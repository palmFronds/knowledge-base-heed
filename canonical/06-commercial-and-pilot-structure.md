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

## Pricing — UNRESOLVED, resolve before the next prospect touchpoint

Two figures currently exist across live materials:

- Deck script: **$5–8K per month**, pilot tier
- One-pager: **$3–5K per engagement**

These are not reconcilable as a monthly rate versus a fixed fee for the same thing, and any prospect who sees both documents will notice. This must be settled before either document goes to another prospect, an accelerator, or an investor.

Considerations for settling it: a four-week engagement at $5–8K/month prices roughly the same as $5–8K per engagement, so the simplest resolution is a fixed pilot fee with a stated scope, and a separate post-pilot commercial model. It also avoids implying an open-ended monthly commitment during a fixed-length pilot.

## Post-pilot commercials

Following validated lift, a transparent performance-aligned model. Options under consideration: a tiered SaaS structure on monthly tracked users, or a direct performance agreement tied to incremental first-deposit conversion delta maintained by the software.

Do not commit to a specific structure in application or prospect materials until the pilot pricing above is resolved.

## Framing discipline in all commercial material

**Outcomes first, mechanics second.** Lead with measurable lift in first-deposit conversion. Product mechanics — the net, the overlay, the config — are the answer to the second question, not the top-line description.

**Every number needs a spoken defense.** A figure you cannot justify out loud in a meeting is worse than no figure. Confidence-flag every estimate and know which are hard data, which are triangulated, and which are guesses.

**Never assert a prospect's drop-off numbers.** Frame findings as where Heed would expect to create value. Asserting drop-off puts the prospect in the position of defending their funnel, and invites a rebuttal you cannot check.

**Do not offer flexibility on commitments the prospect has not asked for.** This has been a recurring pattern in live calls.
