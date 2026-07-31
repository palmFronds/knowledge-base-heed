# 02 — Product and Architecture

## Integration surface

A single CDN-hosted JavaScript file, loaded via one script tag. No npm package, no build step, no backend dependency, no changes to the partner's codebase. Removable by deleting one line.

The choice is a compliance argument before it is an engineering one. An npm package requires a dependency-security review and a partner-side deployment cycle every time Heed ships. In a licensed environment where any change to the operator's UI is potentially a compliance event, a one-line integration surface is what makes the first "yes" achievable on a pilot timeline rather than a quarterly one.

## Five layers

**Signal capture.** Standard browser event listeners — `touchstart`, `touchend`, `blur`, `scroll`, `popstate` — attach to operator-specified selectors. Four signal types: dwell/idle, field blur without completion, scroll reversal above a delta threshold, and back-navigation intent on an incomplete flow. Each emits `{ type, targetSelector, bbox, timestamp }`. Geometry and timing only: no field values, no cookies, no `localStorage` reads, no document content.

Listener attachment survives SPA route changes through a `MutationObserver` on `document.body` gated on `window.location.pathname` having changed, with a `popstate` listener running in parallel as belt-and-braces. Instrumented elements are tracked in a `WeakSet` so re-attachment is idempotent. This works on React, Next.js, Angular, and server-rendered stacks without modification.

**Inference.** A two-layer feedforward network — four inputs, four hidden with ReLU, four softmax outputs — running entirely in the browser on `brain.js`, roughly 30kb gzipped, sub-millisecond forward pass. Input vector is `[normalizedDwell, blurFlag, normalizedReversalCount, backFlag]`, all in `[0,1]`. Output classes are `confusion`, `price_doubt`, `trust_gap`, `flow_friction`, each with a confidence score. Weights are trained offline in Node and stored in the partner config as `net.toJSON()` output.

Client-side is not an optimisation. The intervention window is the hesitation itself, and a server round-trip at real-world tail latency is slower than the moment it would need to catch. The tradeoff is deliberate: the model must be small enough to run in a browser, which forces something fast and interpretable rather than maximally sophisticated.

**Response.** A single transparent overlay `div` injected into `document.body` at init: `position:fixed; inset:0; pointer-events:none; z-index:2147483647`. Response elements render inside it with `pointer-events:auto`, positioned from the signal's bounding rect through `clampToViewport()` (which accounts for iOS safe-area insets). The host DOM is otherwise untouched — no class mutations, no style changes, no event suppression on partner elements.

Response types: `tooltip`, `nudge_copy`, `discount_offer`, `social_proof`. A `discount_offer` CTA fires a `postMessage` to the host window carrying the partner's configured payload. Heed never fulfils a reward.

**Config.** One JSON file per partner on CDN, fetched once at session start, never re-fetched mid-session. It holds selector targets, confidence threshold (default 0.65), model weights, response copy, active routes, completion selector, and the weight-push endpoint. This file is the contract with the partner. Partners do not edit it during pilots — Heed operates it on their behalf, translating their inputs into config. The production dashboard is a UI on this exact schema, not a re-architecture.

**Logging.** Every signal, inference, and response is logged as `{ ts, sessionId, partnerId, event, data }` with event types `signal_detected`, `inference_run`, `response_fired`, `response_dismissed`, `flow_complete`, `flow_abandoned`. Currently console-only. The schema is designed not to change when persistence is activated, so pilot logs and stored logs stay comparable.

## Absolute architectural rules

These are how the code is built, not policies bolted on afterward. A partner's security team can verify them by reading the source, which is itself part of the pitch.

- No PII leaves the browser. Payloads carry geometry and timestamps only.
- The only outbound call after config load is a single session-end POST containing the updated weight array. Not events, not behavioral data. Any other `fetch()` in the SDK is a bug.
- The partner DOM is untouched except for the one overlay div.
- Inference runs client-side only. No inference endpoint, no server-side model.
- Weights are per-partner and stored in that partner's config. Partner A's signal never influences Partner B's. There is no shared model and no federated learning.

## Current build state

`heed-harness`, one repo, four branches. `CONTRACT.md` defines seven locked `data-heed` selectors that must not be modified across branches.

**Branch 1 — `feat/demo-platform`:** complete, gate passed.

**Branch 2 — `feat/heed-sdk`:** complete. All six phases, milestone v1.0. 88/88 Vitest unit tests and 6/6 Playwright end-to-end tests passing. Verified on a real mobile device with the full signal chain confirmed live in both directions: scroll reversal → `price_doubt` → `discount_offer`, and touch hesitation → `confusion` → `tooltip`.

**`linkedin-demo` branch (milestone v1.1, "CRM Blind Spot Demo"):** in active development. A two-lane HUD showing a steelmanned CRM event stream beside Heed's raw behavioral capture across a single hand-driven session. Beat 4 is framed as absence-detection — a timeout on a missing completion event — not as a latency claim. Beat 5, where the net classifies the raw cluster and the Heed overlay renders, is mandatory as the close, and its input must wire to the full hesitation cluster across screens rather than a single terminal signal. A persistent disclosure states that the CRM lane is a competent reconstruction rather than a live third-party product.

*Open decision:* the demo currently runs a crypto wallet swap with CRM vocabulary locked to `swap_started` / `swap_completed`. Given the migration of capital from DeFi protocols into regulated stablecoin rails, a swap demo may date itself. The screens map almost unchanged onto a stablecoin funding flow; the cost of relabelling is event naming and copy, not architecture, though `CONTRACT.md` constrains selector movement.

**Branches 3 and 4 — `feat/agents`, `feat/eval`:** not started, gated behind demo completion.

## Deliberately not built

No dashboard, no auth, no database, no inference endpoint, no cross-partner aggregation, no federated learning, no SDK auto-update, no analytics pipeline, no A/B testing framework inside the SDK.

The last one matters: pilot materials have previously promised a "strict A/B testing framework." What actually exists is that the partner splits their own traffic and Heed is enabled on one arm. Do not describe an A/B capability as a Heed feature.

## Reliability

The file executes asynchronously and does not cause layout shift, block the main thread, or delay content rendering. Inference is entirely client-side, so on CDN failure, latency spikes, or dropped connections the script degrades silently — no response renders and the host UI is left unobstructed.
