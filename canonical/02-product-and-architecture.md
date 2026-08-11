# 02 — Product and Architecture

## Integration surface

A single CDN-hosted JavaScript file, loaded via one script tag. No npm package, no build step, no backend dependency, no changes to the partner's codebase. Removable by deleting one line.

The choice is a compliance argument before it is an engineering one. An npm package requires a dependency-security review and a partner-side deployment cycle every time Heed ships. In a licensed environment where any change to the operator's UI is potentially a compliance event, a one-line integration surface is what makes the first "yes" achievable on a pilot timeline rather than a quarterly one.

## Five layers

**Signal capture.** Standard browser event listeners — `touchstart`, `touchend`, `blur`, `scroll`, `popstate` — attach to operator-specified selectors. Four signal types: dwell/idle, field blur without completion, scroll reversal above a delta threshold, and back-navigation intent on an incomplete flow. Each emits `{ type, targetSelector, bbox, timestamp }`. Geometry and timing only: no field values, no cookies, no `localStorage` reads, no document content.

Listener attachment survives SPA route changes through a `MutationObserver` on `document.body` gated on `window.location.pathname` having changed, with a `popstate` listener running in parallel as belt-and-braces. Instrumented elements are tracked in a `WeakSet` so re-attachment is idempotent. This works on React, Next.js, Angular, and server-rendered stacks without modification.

**Inference.** A two-layer feedforward network — four inputs, four hidden with ReLU, four softmax outputs — running entirely in the browser on `brain.js`, roughly 30kb gzipped, sub-millisecond forward pass. Input vector is `[normalizedDwell, blurFlag, normalizedReversalCount, backFlag]`, all in `[0,1]`. Output classes are `confusion`, `price_doubt`, `trust_gap`, `flow_friction`, each with a confidence score. Weights are trained offline in Node and stored in the partner config as `net.toJSON()` output.

Client-side is not an optimisation, and since 8 Aug 2026 it is no longer a timing argument either. It is what keeps raw behavioral data in the browser: inference runs where the signal is generated, so nothing but a classification ever leaves the page. The tradeoff is deliberate — the model must be small enough to run in a browser, which forces something fast and interpretable rather than maximally sophisticated. **Do not restate this as a latency claim** (`01-positioning.md` §11); the previous version of this paragraph argued server round-trip time and was the last latency argument left standing inside canon.

**Emission.** The classification is emitted into the operator's stack as a structured object; their own tooling decides what to do with it. Heed does not render, does not contact the user, and does not originate the response (`09-retired-positions.md` §18). Phase 2 only — Phase 1 runs no inference and emits nothing.

The emitted object carries **signal type, selector, and confidence as separate fields, never a single blended score**, so the partner's rule engine — including their RG controls — can condition on what was observed and where. Every emission is logged with an acknowledgment from the receiving system, so a downstream failure is attributable to a specific signal rather than unfalsifiable. Both are requirements rather than defaults; `05-regulatory-posture.md` explains why.

**GAP — the emission transport is undecided.** Webhook, a client-side handoff into a partner SDK already loaded on the page, or a queue. This is not only an engineering choice: it decides whether Heed-authored inference transits Heed's servers at all, which is live in the Phase 2 classification question in `05-regulatory-posture.md`.

**The retired response layer — call sites removed.** Decided 8 Aug 2026. The render call sites are deleted from the source, not disabled by configuration. There is no code path from a classification to a rendered element and no config value that could create one. **"Heed does not render" is therefore an architectural claim, not a configuration claim** — which is the standard everything else in this section is held to, and the interim phrasing that hedged it ("the render path exists and is not exercised") is withdrawn.

**The overlay div is removed too.** Decided 9 Aug 2026, for the same reason as the call sites: dead code and an unused element are what make an architectural claim look configurational to a reviewer reading the source. **The SDK inserts nothing into the partner's page.** No div at init, no class mutations, no style changes, no event suppression on partner elements.

**What a security reviewer reading the source will find**, worth pre-empting because it is checkable in ten minutes: no DOM insertion of any kind. No render functions. No handlers for `tooltip`, `nudge_copy`, `discount_offer`, or `social_proof`. No `postMessage` to the host window. A search for element creation returns nothing.

This buys the strongest sentence in the file — **"the partner DOM is untouched,"** with no exception clause after it, which was not sayable while the div shipped.

**Consequence for the test suite.** Removing the call sites removes the tests covering them. The 🟢 88/88 Vitest and 6/6 Playwright counts and the 🟢 verified-both-directions signal chain in `08-claims-register.md` all partly cover the response path: the counts will fall, and the verified chain will describe a terminus that no longer exists. Restate both from the new suite once it is green. **Quote neither number in the meantime** — a test count that drops after being cited is worse than one never cited.

**Config.** One JSON file per partner on CDN, fetched once at session start, never re-fetched mid-session. It holds selector targets, confidence threshold (default 0.65), model weights, active routes, completion selector, and the session-end endpoint. The `response copy` field from the retired render architecture remains in the schema and is populated in no shipping config. This file is the contract with the partner. Partners do not edit it during pilots — Heed operates it on their behalf, translating their inputs into config. The production dashboard is a UI on this exact schema, not a re-architecture.

**Logging.** Every signal and inference is logged as `{ ts, sessionId, partnerId, event, data }` with event types `signal_detected`, `inference_run`, `signal_emitted`, `emission_acknowledged`, `flow_complete`, `flow_abandoned`. `response_fired` and `response_dismissed` are removed from the schema — dead event types read as a disabled feature rather than an absent one. Console-only in the browser; the session-end aggregate below is the only thing that persists anywhere.

## The session-end aggregate — the Phase 1 payload

Decided 8 Aug 2026. **Per selector, per signal type: count, mean, p50, p90, max — held in two buckets, completed and abandoned.** Aggregate only. No session persists, no sequence, no timestamps.

The stratification is what makes the deliverable mean anything. Unstratified, the read carries absolute density and no comparison. Stratified, it carries the sentence the engagement exists to produce: *non-completing sessions carried a p90 dwell of nineteen seconds at the fee row, against six seconds for completing sessions.* Signal-type co-occurrence survives the same way, within a bucket. Bounds in `08-claims-register.md`.

**It stays inside the aggregate rule.** Two buckets rather than one is still an aggregate, still one session-end POST, still nothing retained about any individual session — a session contributes to a bucket and is gone. It is not a step toward the raw-events path recorded as a fallback at `09-retired-positions.md` §20.

**One thing does not work as specified, and it will produce wrong numbers silently.** Percentiles do not merge. Count merges by addition, max by comparison, mean by carrying count and sum — but a bucket's p90 cannot be computed from the p90s of the sessions that fed it. Averaging per-session percentiles yields a number that looks reasonable and is the 90th percentile of nothing.

Only one way out is compatible with retaining no session: **the payload carries a fixed-bin histogram of durations per selector per signal type**, rather than scalar percentiles. Histograms merge by addition; p50 and p90 are read off the merged histogram at the end. The alternative — keeping per-session values so percentiles can be computed later — is a session-level record and is excluded by the decision.

**GAP:** the bin edges are a design choice nobody has made. They set the resolution of every duration claim the read can make, so choose them against the claims the deliverable needs to support rather than as round numbers.

**Payload size stays comfortable.** Four signal types × eight-to-twelve selectors × roughly twelve bins plus count, sum and max is order 10KB of JSON, a couple of KB gzipped — well inside a `sendBeacon` budget, against an existing weight array of about forty floats. The bucket flag adds one field. It becomes material only if the read needs a per-route breakdown on top of per-selector, which multiplies by route count.

## Absolute architectural rules

These are how the code is built, not policies bolted on afterward. A partner's security team can verify them by reading the source, which is itself part of the pitch.

- No PII leaves the browser. No field values, no credentials, no document content, no cookies, no `localStorage`. **Capture is geometry and timing; what leaves the page is an aggregate.** Do not use "geometry and timing only" to describe the outbound payload — that was true of the retired architecture and is not true now (`09-retired-positions.md` §20).
- One outbound call after config load: a single session-end POST carrying the updated weight array and the session aggregate above. Never raw events, never sequence, never timestamps, never anything mid-session. Any other `fetch()` in the SDK is a bug. In Phase 2, emission is a second path and is subject to the same rule — one classification out, nothing else.
- **The partner DOM is untouched.** No exception clause. The SDK inserts no element into the page, and there is no code that could — call sites and overlay both removed, not gated.
- Inference runs client-side only. No inference endpoint, no server-side model.
- Weights are per-partner and stored in that partner's config. Partner A's signal never influences Partner B's. There is no shared model and no federated learning.

## Current build state

`heed-harness`, one repo, four branches. `CONTRACT.md` defines seven locked `data-heed` selectors that must not be modified across branches.

**Branch 1 — `feat/demo-platform`:** complete, gate passed.

**Branch 2 — `feat/heed-sdk`:** complete. All six phases, milestone v1.0. 88/88 Vitest unit tests and 6/6 Playwright end-to-end tests passing. Verified on a real mobile device with the full signal chain confirmed live in both directions: scroll reversal → `price_doubt` → `discount_offer`, and touch hesitation → `confusion` → `tooltip`.

**`linkedin-demo` branch (milestone v1.1, "CRM Blind Spot Demo"):** in active development, **and its closing beat now shows a capability the product does not have.** A two-lane HUD showing a steelmanned CRM event stream beside Heed's raw behavioral capture across a single hand-driven session. Beat 4 is framed as absence-detection — a timeout on a missing completion event — not as a latency claim. A persistent disclosure states that the CRM lane is a competent reconstruction rather than a live third-party product.

**Beat 5 must be rebuilt.** It was specified as the point *"where the net classifies the raw cluster and the Heed overlay renders,"* mandatory as the close — and the render call sites are gone (`09-retired-positions.md` §18). The close is now the classification arriving in the operator's lane as a signal their tooling can route, which is a better ending for the same demo: the CRM lane has been empty the whole time, and Beat 5 is the moment something finally lands in it. Its input must still wire to the full hesitation cluster across screens rather than a single terminal signal.

**The demo's signal is a dwell and does not overclaim** (`09-retired-positions.md` §21). The touch beat is a long touch on a target, not an aborted tap; label it that way.

*Open decision:* the demo currently runs a crypto wallet swap with CRM vocabulary locked to `swap_started` / `swap_completed`. Given the migration of capital from DeFi protocols into regulated stablecoin rails, a swap demo may date itself. The screens map almost unchanged onto a stablecoin funding flow; the cost of relabelling is event naming and copy, not architecture, though `CONTRACT.md` constrains selector movement.

**Branches 3 and 4 — `feat/agents`, `feat/eval`:** not started, gated behind demo completion.

## Deliberately not built

No dashboard, no auth, no inference endpoint, no cross-partner aggregation, no federated learning, no SDK auto-update, no A/B testing framework inside the SDK.

**"No database" has fallen.** Phase 1's written read requires the session-end aggregate to be received, stored, and queried. That is new build with no partner-facing surface, and it is the build no partner asked for that `09-retired-positions.md` §19 predicted. **GAP:** what the store is, where it sits, and what its retention period is are all undecided — and all three are procurement questions before they are engineering ones. A retention policy and a subprocessor list are expected as standing documents (`05-regulatory-posture.md`), and data residency is already an open counsel question there.

The last one matters: pilot materials have previously promised a "strict A/B testing framework." What actually exists is that the partner splits their own traffic and Heed is enabled on one arm. Do not describe an A/B capability as a Heed feature.

## Reliability

The file executes asynchronously and does not cause layout shift, block the main thread, or delay content rendering. Inference is entirely client-side, so on CDN failure or dropped connections the script degrades silently — no signal is emitted, nothing renders, and the host page is unaffected. In Phase 1 the failure mode is a lost session-end POST, which costs one session's contribution to the aggregate and nothing else.
