# 06 — Commercial and Pilot Structure

## Sales posture — standing instruction

Sales-first. No MVP expansion until partners explicitly ask for product. Sandler-style: two discovery calls, let the prospect define the solution, then circle back. Passive product research runs in parallel, but no new build is pulled without pipeline demand.

**Discovery has to make the objection speakable, not defer it.** The two objections that decide these deals — build-versus-buy and first-customer risk — are raised on the prospect's schedule if they are not raised on Heed's. Once stated, they are a position the prospect has committed to, and the deal is being argued rather than sold. Both belong in the discovery script; the handling is in `01-positioning.md` §10, which owns objection language.

**Diagnostic for a soft close:** if the prospect's decision criteria are new information when the deferral arrives, the close was soft, however the call felt.

## Pilot shape — two phases

Settled 8 Aug 2026. Supersedes the single-phase two-to-four-week engagement; see `09-retired-positions.md` §17.

Scoped to **registration → KYC → first funded action** and nothing else, in both phases (`01-positioning.md` §7). "Across the onboarding journey" is broader than the wedge and is not the scope — correct it wherever it appears.

**Phase 1 — three to four weeks. Collection only.** Event listeners attached across the wedge. No inference runs. Nothing renders and the user experience does not change. Ends in a written read on where sessions stall and what precedes it.

**Phase 2 — conditional, entered by agreement.** Intent classification in-session, emitted as a signal into the partner's own stack, which the partner acts on with tooling they already run. Heed does not render, does not touch the user, and does not originate the response (`09-retired-positions.md` §18). Commercial framing is co-design. Phase 2 is not assumed by Phase 1 and is not sold during Phase 1.

Phase 1 does not end in a recommendation to buy Phase 2. It ends in a read the partner owns and can act on with or without Heed, which is exactly what makes it a scoping input to their own build-versus-buy decision rather than a purchase step (`01-positioning.md` §10). A Phase 1 that converts nobody and produces a read the partner uses is a success by design, not a failure to close.

**Deployment target — the partner elects at scoping.** Decided 8 Aug 2026: case-by-case, not a fixed rule.

State the tradeoff rather than letting the partner discover it. Staging carries no real sessions, so a staging Phase 1 reads synthetic or internal traffic and is worth substantially less. Production carries real sessions and is a larger internal approval. Phase 1 changes nothing in either environment, which is the only reason production is electable at all. Let the partner weigh it: a partner who elects staging and receives a thin read made an informed choice, and a partner told "production or nothing" has been handed a reason to defer.

**Phase 1 also carries two contractual items that are not obvious from its size.** A retention policy for the session-end aggregate, because Phase 1 requires a store and the store is new (`02-product-and-architecture.md`). And, if Phase 2 is contemplated, the partner's RG-suppression warranty — a negotiated term, surfaced during Phase 1 scoping rather than at Phase 2 signature (`05-regulatory-posture.md`).

## What Heed needs from a partner

**Phase 1.** A thirty-minute walkthrough of the flow, to identify the screens inside the wedge and write selector targeting against the partner's actual DOM. The script tag. Agreement up front on what the written read will cover, so there is no dispute at the end about what was promised.

No backend access, no database access, no code changes beyond the script tag. **No response copy, no compliance sign-off on copy, and no staging environment for response testing** — those were inputs to the retired single-phase pilot, and Phase 1 has no response layer to test.

**Phase 2.** Not scoped here. What it requires depends on which of the partner's own tools consumes the signal, and that is a co-design question answered after Phase 1. Do not describe Phase 2 inputs to a prospect during Phase 1.

## What a partner receives

**Phase 1 — one written read.** Where sessions stall inside the wedge, and what preceded the stall. Screen-level signal density against completion outcome, signal-type co-occurrence, and frequency. It is theirs to keep and is useful to them whether or not Phase 2 happens.

What it does not contain: a conversion delta, a lift figure, or a causal claim. Phase 1 has no intervention arm, so nothing in it supports "this caused that." **Say *precedes*. Never *causes*, and never *appears to cause*** — the hedge reads as causation to anyone analytically literate, which is who receives this document.

What it contains depends on the Phase 1 payload, which is not fully specified. Session-level sequence is not recoverable from aggregate data at all. Duration and magnitude are recoverable only if the payload carries summary statistics rather than bare counts — see the open question in `09-retired-positions.md` before promising anything about how long a user paused.

**Phase 2.** A weight corpus trained on their specific flow, theirs to keep, and a signal log. **Not an intervention log with a decision trace** — Heed no longer fires the intervention, so there is no Heed-side record of a response.

## Pilot KPIs

**Phase 1 has no conversion KPI**, because it changes nothing. It is measured on whether the read identified a stall point the partner had not already found, engineering hours on the partner's side — target being the script tag and nothing else — and compliance review overhead.

**Phase 2 carries the conversion KPIs.** Abandonment reduction at the identified screens. Completion rate through the wedge. Time-to-first-funding. Plus total engineering hours on both sides: a pilot that proves the product works but costs more engineering time than it saves is not yet a sellable product.

## Measurement — say this precisely

**Heed does not contain an A/B testing framework and must not be described as providing one**, in either phase. Prior pilot material promised a "strict A/B testing framework" as a Heed capability. It is not one.

Phase 1 has no arms and measures no lift. It is observation.

**Phase 2 lift is measured in the partner's stack, not in Heed's**, because the partner's tooling fires the response. This is a real consequence of the emit-into-their-stack architecture and it costs something: Heed can no longer compute an independent before-and-after the way the retired rendering shape could. Attribution now depends on the partner's own instrumentation and on their willingness to share the result. Do not promise a before-and-after Heed cannot itself produce.

### Attribution becomes joint — anticipate this, do not discover it

**When the operator renders the response, the lift is jointly attributable and there is no clean way to separate the contributions.** Heed supplied the signal; the operator's team wrote the copy, chose the treatment, and picked the moment. A good signal paired with bad copy produces no lift. A mediocre signal paired with excellent copy produces some. Nothing in the architecture distinguishes them, and under emit-only nothing ever will.

**This is a renewal problem, not a pilot problem, and the distinction matters.** During a pilot both sides want the number to be good and nobody interrogates the split. At renewal, the operator is deciding whether a recurring platform fee is worth it, and *"our team wrote the messaging that actually moved it"* is available to them, true, and unanswerable. The flat per-month platform fee is the right basis partly because of this — a performance-based fee would put Heed in an argument it cannot win with evidence it does not have.

**Raise it during Phase 2 scoping, in writing, before there is a number to disagree about.** Agree in advance what both sides will treat as evidence: which arms are being compared, what counts as a Heed-signalled session, and that the delta is a joint result of signal plus response. The version of this conversation that happens after a good quarter is a negotiation; the version that happens before it is a design decision, and it costs nothing.

Do not overcorrect into disclaiming credit. The honest frame is that Heed makes an intervention possible that could not otherwise have happened at all — the operator's copy had nothing to fire on before, which is the whole argument (`01-positioning.md`).

## Pricing

**Phase 1 is free. Phase 2 is a flat per-month platform fee.** Founder decisions, 8 Aug 2026.

**Why Phase 1 is free — say it this way and not another way.** It is a scoping instrument, not a discount. Phase 1 exists to produce the input a prospect needs for their own build-versus-buy decision, and charging for it would make it a purchase — which is precisely what loses to comparative deferral (`01-positioning.md` §10). A priced diagnostic has to be justified against every other use of the budget. A free one has to be justified against nothing.

Do not present it as a trial, an introductory rate, a discount, a waived fee, or a limited-time offer. Every one of those framings implies a price that is being suppressed, invites the question of what it will cost later, and converts a scoping instrument back into a purchase decision. **It is free because it is scoping, and it stays free after there is a case study.**

**GAP — the Phase 2 figure.** The *basis* is decided: a flat per-month platform fee. Not per-seat, not per-tracked-user, not performance-based. The *amount* is not. **Quote no Phase 2 number.** The retired $3–5K per engagement was a fixed fee for a two-to-four-week engagement and does not convert to a monthly platform fee by any arithmetic — do not divide it, do not annualise it (`09-retired-positions.md` §15, §17). The deck script's $5–8K/month figure remains withdrawn and is not a starting point.

**What the flat monthly basis rules out.** The post-pilot options previously under consideration included a performance agreement tied to incremental first-deposit conversion delta. A flat platform fee is not that — and since Heed can no longer compute an independent before-and-after (see Measurement above), a performance basis would have been unmeasurable by Heed regardless. That option is closed, not deferred.

## A tighter pilot shape — recorded, not adopted

A 4 Aug 2026 GTM research document (`sources/2026-08-04-gtm-case-studies.md`) argues the pilot above is directionally right but loose, on the evidence of how comparable categories broke through buyer education. The pattern it identifies across Darktrace, Sift, Featurespace, Feedzai, and Forter: none of them argued the prospect out of their existing mental model, all of them gave the prospect a fast, low-risk way to watch the new model catch something the old one missed, on the prospect's own data, in a fixed window, with the vendor absorbing the risk of being wrong.

Three concrete changes followed from that. **Two are now adopted; one remains blocked.**

- **A fixed window with a named deliverable — ADOPTED 8 Aug 2026.** Darktrace ran a free 30-day proof of value with a promised report of real findings, rather than an open-ended pilot. Phase 1 is the Heed version: a fixed three-to-four-week window, free or nominal, ending in a written read. Note what was *not* adopted from the Darktrace analog — the original proposal here was "a report of observed hesitation events **and estimated recovered conversions against baseline**." The second half is a lift estimate, Phase 1 has no intervention arm, and it does not go in the deliverable.
- **"Alongside, not instead of."** Featurespace and Feedzai both defused the compliance objection by positioning explicitly as supplementing existing rule-based infrastructure rather than replacing it. Canon already carries the architecture for this — no PII, no execution logic, removable in one line — but not the sentence, and not for product and growth stakeholders rather than compliance.
- **Outcome risk carried by Heed.** Forter made a chargeback guarantee the sales motion rather than a footnote. **Blocked**: any downside guarantee is a commercial commitment Heed has not adopted. It cannot be offered, or implied in a prospect conversation, until explicitly decided.
- **An observation-only first phase producing a written read — ADOPTED 8 Aug 2026**, as Phase 1 above. Raised out of the Jackpot.com deferral, resolved the same week. Do not call it "read-only"; see `09-retired-positions.md` §17.

**The conclusion this section drew is retired. Its reasoning is not** (`09-retired-positions.md` §19).

The reasoning — *a guaranteed deliverable is a build commitment made to a prospect before the pipeline has asked for it* — was correct, and the two-phase decision overrides it knowingly rather than disproving it. Its prediction came true inside the same week: Phase 1 requires a payload change to the SDK that no partner asked for, and that build now sits with a co-founder who did not sell it (`07-company-team-and-status.md`).

So keep the test. Every time a deliverable is promised, *"what does this commit us to building, and did anyone ask for it?"* still has to be answered out loud. The answer is now permitted to be "yes, and we are doing it anyway." It is not permitted to go unasked.

## Post-pilot commercials

Following validated lift, a transparent performance-aligned model. Options under consideration: a tiered SaaS structure on monthly tracked users, or a direct performance agreement tied to incremental first-deposit conversion delta maintained by the software.

Do not commit to a specific post-pilot structure in application or prospect materials until a partner asks.

## Framing discipline in all commercial material

**Outcomes first, mechanics second.** Lead with measurable lift in first-deposit conversion. Product mechanics — the net, the emission, the config — are the answer to the second question, not the top-line description. *("The overlay" stood here until 9 Aug 2026 and is not a mechanic Heed has.)*

**Every number needs a spoken defense.** A figure you cannot justify out loud in a meeting is worse than no figure. Confidence-flag every estimate and know which are hard data, which are triangulated, and which are guesses.

**Never assert a prospect's drop-off numbers.** Frame findings as where Heed would expect to create value. Asserting drop-off puts the prospect in the position of defending their funnel, and invites a rebuttal you cannot check.

**Do not offer flexibility on commitments the prospect has not asked for.** This has been a recurring pattern in live calls.
