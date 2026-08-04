# 06 — Commercial and Pilot Structure

## Sales posture — standing instruction

Sales-first. No MVP expansion until partners explicitly ask for product. Sandler-style: two discovery calls, let the prospect define the solution, then circle back. Passive product research runs in parallel, but no new build is pulled without pipeline demand.

## Pilot shape

A two-to-four-week co-design engagement, scoped to registration through first funded action and nothing else.

**Week 1 — co-design.** A thirty-minute working session walking the partner's onboarding flow together to identify the two or three screens with the highest drop-off and the most likely hesitation signal. Compliance sign-off on response copy.

**Week 2 — integration.** Script tag deployed to staging, selector targeting written against the partner's actual DOM, overlay response testing.

**Week 3 — live.** Deployment to a controlled segment with real-time inference logging.

**Week 4 — analysis.** Conversion delta review, metric analysis, weight corpus handover.

## What Heed needs from a partner

A staging environment URL. A thirty-minute flow walkthrough. Draft copy for each response type, written into slots and character limits Heed provides, with the actual words supplied and approved by the partner's own compliance team. Agreement up front on the single metric both sides are measuring, so there is no dispute at the end about what "worked" means.

No backend access, no database access, no code changes beyond the script tag.

## What a partner receives

A before-and-after on the agreed metric, a full intervention log with decision trace, and a weight corpus trained on their specific flow which is theirs to keep.

## Pilot KPIs

Abandonment reduction at the targeted screens. Completion rate through the funnel. Time-to-first-funding. Integration effort on the partner's engineering side. Compliance review overhead. Total engineering hours on both sides — a pilot that proves the product works but costs more engineering time than it saves is not yet a sellable product.

## Measurement — say this precisely

The partner splits their own traffic; Heed is enabled on one arm. **Heed does not contain an A/B testing framework and must not be described as providing one.** Prior pilot material promised a "strict A/B testing framework" as a Heed capability. It is not one.

## Pricing

**$3–5K per engagement** for the two-to-four-week pilot — fixed fee, stated scope, not a monthly rate. Settled 4 Aug 2026. The deck script's $5–8K/month figure is withdrawn; see `09-retired-positions.md` §15.

Post-pilot commercial structure remains under consideration and is not part of this number.

## A tighter pilot shape — recorded, not adopted

A 4 Aug 2026 GTM research document (`sources/2026-08-04-gtm-case-studies.md`) argues the pilot above is directionally right but loose, on the evidence of how comparable categories broke through buyer education. The pattern it identifies across Darktrace, Sift, Featurespace, Feedzai, and Forter: none of them argued the prospect out of their existing mental model, all of them gave the prospect a fast, low-risk way to watch the new model catch something the old one missed, on the prospect's own data, in a fixed window, with the vendor absorbing the risk of being wrong.

Three concrete changes follow from that, none of them adopted:

- **A fixed window with a named deliverable.** Darktrace ran a free 30-day proof of value with a promised report of real findings, rather than an open-ended pilot. The Heed analog is a report of observed hesitation events and estimated recovered conversions against baseline, promised up front.
- **"Alongside, not instead of."** Featurespace and Feedzai both defused the compliance objection by positioning explicitly as supplementing existing rule-based infrastructure rather than replacing it. Canon already carries the architecture for this — no PII, no execution logic, removable in one line — but not the sentence, and not for product and growth stakeholders rather than compliance.
- **Outcome risk carried by Heed.** Forter made a chargeback guarantee the sales motion rather than a footnote. **Blocked**: any downside guarantee is a commercial commitment Heed has not adopted. It cannot be offered, or implied in a prospect conversation, until explicitly decided.

Weigh this against the sales posture at the top of this file. Sales-first with no MVP expansion until partners ask is a deliberate constraint, and a guaranteed deliverable is a build commitment made to a prospect before the pipeline has asked for it.

## Post-pilot commercials

Following validated lift, a transparent performance-aligned model. Options under consideration: a tiered SaaS structure on monthly tracked users, or a direct performance agreement tied to incremental first-deposit conversion delta maintained by the software.

Do not commit to a specific post-pilot structure in application or prospect materials until a partner asks.

## Framing discipline in all commercial material

**Outcomes first, mechanics second.** Lead with measurable lift in first-deposit conversion. Product mechanics — the net, the overlay, the config — are the answer to the second question, not the top-line description.

**Every number needs a spoken defense.** A figure you cannot justify out loud in a meeting is worse than no figure. Confidence-flag every estimate and know which are hard data, which are triangulated, and which are guesses.

**Never assert a prospect's drop-off numbers.** Frame findings as where Heed would expect to create value. Asserting drop-off puts the prospect in the position of defending their funnel, and invites a rebuttal you cannot check.

**Do not offer flexibility on commitments the prospect has not asked for.** This has been a recurring pattern in live calls.
