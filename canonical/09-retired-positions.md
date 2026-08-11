# 09 — Retired Positions

Fourteen contradictions found across `Product_Posture.md`, `Product_Spec.md`, `Pilot_Specs.txt`, the Pilot Brief PDF, the Regulatory Report, and the Ember report, plus one frame retired during canon consolidation. Each is resolved here. Superseded documents are kept for traceability but never quoted.

---

## 1. Latency as the differentiator — RETIRED

**Old:** "Heed fills the latency gap between user hesitation and operator response." Also "CRM engines respond five to thirty minutes after a player has gone cold."

**Why it lost:** Optimove, Braze, and Fast Track have genuine real-time triggering. Anyone who has evaluated them dismantles a speed claim in one sentence and the differentiator collapses with it.

**Replacement:** Input model. An event-driven pipeline can be infinitely fast and still have nothing to fire on, because a pause is not an event it was built to receive. Argue absence of input, never timing of output.

**This is the most frequently recurring drift in the entire document set.** It has reverted at least three times under compression, including in live outbound. Watch for any sentence about *when* something fires.

---

## 2. Two-axis frame as the core structure — RETIRED

**Old:** The core argument was framed as two independent axes — input model (semantic events versus behavioral substrate) and response window (retroactive versus in-session) — with Heed positioned as "the only occupant of substrate-capture plus in-session response."

**Why it lost:** A 2×2 hands the incumbent a legitimate quadrant. Presenting response-window as a co-equal axis lets Optimove and comparable CRMs claim parity on one full axis — "they're real-time" — which reads as half a conceded differentiator before the pitch starts. Retroactivity is not an independent property; it is a consequence of the input model. If the only observable things are named events, discovery can only happen after the fact, because the pipeline was never built to accept the unnamed behavior as input in the first place. The lag is a property of what the pipeline can accept, not of pipeline speed.

**Replacement:** One axis only — the input model, event versus behavioral substrate. See `01-positioning.md`. Any framing that hands the incumbent a fast/slow axis to stand on has reverted to this position.

**Recurrence log.** 3 Aug 2026 — the spoken opening on the LATAM call ran on "response window" and "not afterwards, but while it's actually going on" (`07-company-team-and-status.md`). 4 Aug 2026 — a GTM research document arrived framed end to end on "real-time behavioral inference vs. retroactive/rule-based tooling," and additionally led on rule-absence, which is demoted at §3. Two independent reversions in two days, one spoken and one written. This position is not holding on its own.

---

## 3. Rule-absence as the differentiator — DEMOTED

**Old:** "This is not a faster rule engine. The differentiator is the absence of rules entirely."

**Why it was demoted:** It is true and it is a good second-order point, but it is not the primary axis. A rule-based system with substrate input would still be closer to Heed than a non-rule-based system with only semantic events. The input model is the deeper claim.

**Replacement:** Lead with substrate versus semantic. Use rule-absence as supporting detail.

---

## 4. "Consumer DeFi" as the primary vertical — RETIRED

**Old:** `Product_Posture.md` positions DeFi and early-stage CeFi as the wedge. Counsel was told the DeFi pivot happened *because* the space is "very unregulated in the US."

**Why it lost:** DeFi TVL fell roughly 37% in H1 2026 while stablecoin circulation crossed $314B — capital relocated into the regulated perimeter. More fundamentally, the stated rationale inverted the product: Heed's differentiator is that compliance constraints *are* the product, which makes an unregulated market the worst possible home for it.

**Replacement:** Regulated money flows. Prediction exchanges first, licensed DFS second, regulated on-ramps and stablecoin rails third, Brazil fourth, ADW and lottery couriers fifth.

---

## 5. Cross-partner data aggregation as the moat — RETIRED

**Old:** `Product_Posture.md`: "Signal data aggregated across design partners generates a behavioral dataset that does not exist anywhere else. This dataset is the compounding moat."

**Why it lost:** It directly contradicts the architectural rule that per-partner weights never mix, and it would plausibly convert Heed from processor to joint controller, triggering a much heavier compliance burden and a much harder conversation with every partner's legal team.

**Replacement:** The moat is the operator-control architecture itself — expensive to retrofit and easy to get wrong if a CRM or CDP vendor tries to bolt real-time inference onto a profile store. Cross-partner training is prohibited and would require its own legal review before any engineering work.

---

## 6. Host UI mutation at full scale — RETIRED

**Old:** `Product_Posture.md`: "Parallax can push targeted mutations to host UI elements directly: swap copy, reorder elements, surface a simplified view."

**Why it lost:** Contradicts the absolute rule that the partner DOM is untouched except for the overlay div. In a licensed environment, any mutation of the operator's UI is either undocumented (audit exposure) or requires its own compliance review per change (destroying the speed advantage).

**Replacement:** Overlay only, permanently. Not a v0 limitation. — **This replacement has itself been retired at §18.** Heed renders nothing at all: render call sites and the overlay div are both removed, and the SDK inserts no element into the partner's page. The original position stays retired for the original reason, and the rule it protected is now absolute rather than narrow.

---

## 7. Sandboxed iframe integration — RETIRED

**Old:** `Product_Posture.md`: "Single script tag injects a full-viewport iframe... all communication via `postMessage` only."

**Why it lost:** Superseded by the shipping implementation, which injects a transparent overlay div into `document.body`. `postMessage` survives, but only as the `discount_offer` CTA handoff to the host window.

**Replacement:** Overlay div, as built and tested. — **Superseded at §18.** The div is removed along with the render call sites, and the `postMessage` handoff is gone with the rest of the response layer. Iframe integration stays retired regardless, and doubly so: it was retired once for not matching the build and again for describing a rendering product.

---

## 8. Static mapping table for v0 inference — RETIRED

**Old:** `Product_Posture.md`: "A static mapping table, not a model."

**Why it lost:** Contradicts `Pilot_Specs.txt` and the shipping build, both of which specify a 2-layer feedforward net and explicitly reject a lookup table on the grounds that a table is a rule by another name.

**Replacement:** 4 → 4 (ReLU) → 4 (softmax) on `brain.js`, weights trained offline in Node, stored per partner.

---

## 9. Product name — RESOLVED

**Old:** Parallax, throughout `Product_Posture.md`, `Product_Spec.md`, `Pilot_Specs.txt`, and as the internal codename in the regulatory report.

**Replacement:** Heed. Parallax appears only as a historical codename in engineering context, never externally.

---

## 10. "Outside personal data scope entirely" — RETIRED AND WRONG

**Old:** Pilot Brief: no PII leaves the browser, "keeping Heed outside the scope of personal data definitions and outside your existing data processing agreements entirely."

**Why it lost:** The regulatory report in the same document set says the opposite — behavioral interaction data becomes personal data whenever it can reasonably be tied to a session or device, and the compliance posture assumes this applies rather than arguing around it.

**Replacement:** Minimisation narrows the operator's lawful-basis analysis; it does not remove Heed from scope. A partner's privacy counsel will catch the stronger claim immediately.

---

## 11. A/B testing framework as a Heed capability — RETIRED

**Old:** Pilot Brief promises "a strict A/B Testing Framework" with traffic split evenly between control and intervention.

**Why it lost:** `CLAUDE.md` lists "no A/B testing framework" under what not to build, and none exists.

**Replacement:** The partner splits their own traffic and enables Heed on one arm. Describe it that way.

---

## 12. Pilot status of named partners — CORRECTED

**Old:** Regulatory report: "Pilots are underway with Banxa, Jackpot.com, and PrizePicks."

**Why it lost:** They are conversations. Nothing is signed, no code is deployed at any of them. The same report's Appendix A separately flags that naming them externally needs a confidentiality check.

**Replacement:** "Active conversations with." Correct this before the report is attached to anything.

---

## 13. Design partner commitments — CORRECTED

**Old:** `Product_Posture.md` Current State: "Design partner commitments secured across DeFi and CeFi platforms."

**Replacement:** None secured. Zero signed.

---

## 14. Mid-session monetisation — OUT OF SCOPE

**Position:** Bonus deployment on loss events is deprioritised for UKGC and RG tail risk. The pilot scope is registration through first funded action only.

**The drift:** The Ember report offered "bonus deployment based on intent" pointed at a run of consecutive losses as use case 2, and a live LinkedIn message named bonus deployment as the example response.

**Resolved 4 Aug 2026:** Remove bonus-on-loss from the Ember template and from any licensed-prospect material. Where an example is needed, a unit explainer or a conversion breakdown makes the same point without teaching the habit.

**Reframed 9 Aug 2026.** This previously read "default example responses," which described a Heed response catalogue. Heed has none (§18) — it emits a signal and the operator's tooling decides everything after. These are examples of **what an operator might choose to fire**, offered to make a point about scope, and they should be spoken that way: *"an operator might show a unit explainer"*, never *"we show a unit explainer."* The distinction is the whole regulatory position and it collapses in exactly this kind of throwaway example.

---

## 15. Pilot pricing — RESOLVED

**Old:** Deck script said $5–8K/month pilot tier. One-pager said $3–5K per engagement. Both were in circulation.

**Why the monthly figure lost:** Founder decision 4 Aug 2026 — fixed fee per engagement matches the pilot shape (two-to-four weeks, stated scope) and avoids implying an open-ended monthly commitment.

**Current:** **$3–5K per engagement** for the pilot. Withdraw the deck script's $5–8K/month everywhere it appears. See `06-commercial-and-pilot-structure.md` and `01-positioning.md` §8.

---

## 16. Category name — SUPERSEDED

**Old:** "A behavioral control layer" — listed under approved language in `01-positioning.md` as of 29 Jul 2026.

**Why it lost:** Founder decision 4 Aug 2026. "Control layer" implied authority over regulated outcomes that sits with the operator, not Heed. The GTM research document's alternative — "real-time behavioral response infrastructure" — was never adopted; it is built on banned language (speed as differentiator) and is retired alongside this entry.

**Replacement:** **Intelligent behavioral intervention.** Category name only — the input-model argument and approved/banned language rules in `01-positioning.md` §11 are unchanged.

**Challenged and retained, 8 Aug 2026.** The emit architecture (§18) removed Heed from the intervention, raising the obvious objection that a company which does not intervene should not have "intervention" in its category name. The name is kept, defended as *the intelligence layer of an intervention system*, with a rehearsable sentence in `01-positioning.md` §11.

**Anticipate the next challenge instead of meeting it fresh.** Three names have now been tested and two were retired for the same class of defect — asserting something Heed does not do. "Behavioral control layer" implied authority over regulated outcomes that sits with the operator. "Real-time behavioral response infrastructure" asserted both speed as the differentiator and Heed responding. The surviving name is in the same family and survives because it is *defended*, not because it is self-evidently accurate.

So when a fourth challenge arrives — and on this record it will — the question to ask is not "is this name right." It is **"does the defense still hold under the architecture we have now."** If it does, answer with the prepared sentence and move on. If it does not, the replacement must describe what Heed does, not what the system Heed is part of does. That is the test all three names have been judged against, and it is the only one that has held.

**9 Aug 2026 — emit-only confirmed, and the defense is now load-bearing rather than incidental.** The name is not re-decided here. What changed is that emit-only was promoted from an architectural fact to a positioning asset led with in the compliance conversation (`01-positioning.md` §9), which means the pitch now says *"Heed never shows your users anything"* early and out loud. A prospect who hears that and then hears the category name has been handed the contradiction rather than having to find it.

**The name therefore no longer survives on its own; it survives on one sentence.** That sentence is in `01-positioning.md` §11 and it has to be delivered, not remembered. Three consequences worth writing down:

- **This is the third name held against the same class of challenge** — asserting something Heed does not do. Two failed it. This one passes only because the defense reframes Heed as a layer within a system rather than the actor.
- **The defense has a dependency.** It rests on the operator's intervention being real and Heed's signal being what makes it possible. It does not survive an architecture in which Heed's output is one input among many that the operator would have acted on anyway.
- **Do not re-open this casually.** Three names in three weeks is already a cost — a category that keeps changing reads as a company that does not know what it is. Re-open it only if the defense fails, and record the failure here before choosing a replacement.

---

## 17. Single-phase pilot ending in a rendered intervention — RETIRED

**Old:** A two-to-four-week co-design engagement in four weekly steps — co-design and compliance sign-off on response copy, script tag to staging with overlay response testing, live deployment to a controlled segment, then conversion delta review. Priced at $3–5K per engagement. Recorded in `06-commercial-and-pilot-structure.md` until 8 Aug 2026.

**Why it lost:** it front-loaded every cost of being first into the first purchase. Compliance sign-off on response copy, a staging environment, and live exposure to real users were all required before the prospect had seen a single piece of evidence from their own funnel. Against comparative deferral — the objection class that lost Jackpot.com (`01-positioning.md` §10) — that shape gives a roadmap-constrained prospect nothing to say yes to that is smaller than a full deployment decision.

**Replacement:** two phases. Phase 1 is three to four weeks, collection only, no inference, nothing rendered, no change to the user experience, free or nominal, ending in a written read on where sessions stall and what precedes it. Phase 2 is conditional and entered by agreement. See `06-commercial-and-pilot-structure.md`.

**This resolves the open question raised 8 Aug 2026** ("does the engagement have a read-only first phase?"). It does — but **"read-only" is retired along with the old shape and is not the phrase.** It is an engineering term of art meaning read access to systems, which invites a security reviewer to ask read access *to what*, when the answer is nothing. The second reason it was wrong — that it was not literally true while the overlay div was injected at init — lapsed on 9 Aug 2026 when the div was removed. The first reason is sufficient on its own and the phrase stays retired. The approved phrasing is `05-regulatory-posture.md`'s own: **infrastructure that senses and reports.**

---

## 18. Heed renders the response — RETIRED

**Old:** Heed's SDK renders the operator's pre-approved response into a transparent overlay div, using copy the operator's compliance team authored. `05-regulatory-posture.md`: *"Heed's SDK renders the response… That handoff is the entire regulatory position."* Response types `tooltip`, `nudge_copy`, `discount_offer`, `social_proof`, with a `discount_offer` CTA passing acceptance back by `postMessage`.

**Why it lost:** founder decision, 8 Aug 2026. Rendering put Heed inside the operator's user experience to execute a decision that was never Heed's, and it carried the entire dark-patterns and promotional-marketing exposure in `05-regulatory-posture.md` for no differentiating benefit. Every hard compliance question in the set attached to the render, not to the signal.

**Replacement:** Heed emits a signal into the operator's stack; the operator acts on it with tooling they already run. Heed does not render, does not touch the user, and does not originate the response. This is an architectural statement, not an analogy — **do not describe it as "plugging in like a CRM,"** which is banned language (`01-positioning.md` §11, "another CRM").

`01-positioning.md` §9's compliance sentence — *"Heed identifies friction. The operator determines whether and how to assist the customer"* — survives unchanged and becomes literally true rather than architecturally guaranteed. Keep it exactly as written.

**Live instances still in circulation.** `02-product-and-architecture.md` still describes the response layer, the overlay div injected at init, `response copy` in the config schema, and `response_fired` / `response_dismissed` in the log schema. `05-regulatory-posture.md` still runs its dark-patterns and marketing sections on rendering. Both files need their own pass and have not had one, because two questions must be decided first: whether the overlay div is deleted from the SDK rather than shipped inert, and what emit-into-their-stack does to the processor classification. See open questions below.

---

## 19. "No named deliverable before the pipeline asks" — CONCLUSION RETIRED, REASONING RETAINED

**Old:** `06-commercial-and-pilot-structure.md` declined the fixed-window named-deliverable pattern on the grounds that *"a guaranteed deliverable is a build commitment made to a prospect before the pipeline has asked for it,"* weighed against the standing sales-first instruction that no build is pulled without pipeline demand.

**Why the conclusion lost:** founder decision, 8 Aug 2026. Phase 1's written read is adopted as the deliverable because the objection it answers — comparative deferral — cannot be answered by anything the prospect has to buy first.

**Why the reasoning is kept:** because it was right, and it was proved right within the week. Phase 1 requires a payload change to the SDK that no partner asked for, and the build sits with a co-founder who did not sell it. This is a constraint the decision **knowingly overrides**, not one found to be mistaken. The test survives: every promised deliverable must answer *"what does this commit us to building, and did anyone ask?"* out loud. "Yes, and we are doing it anyway" is now an acceptable answer. Silence is not.

---

## 20. "Not events, not behavioral data" as an absolute rule — NARROWED

**Old:** `02-product-and-architecture.md`, under Absolute architectural rules: *"The only outbound call after config load is a single session-end POST containing the updated weight array. Not events, not behavioral data. Any other `fetch()` in the SDK is a bug."*

**Why it lost:** Phase 1's written read requires behavioral signal to reach Heed. Founder decision 8 Aug 2026 chose the narrowest path that produces a deliverable — extend the existing session-end POST to carry **per-session aggregates, not raw events**. A full events pipeline is a fallback if the deliverable proves too thin, not the plan. Both options are zero partner effort; aggregates were chosen on internal build cost and regulatory exposure.

**Replacement, clause by clause.** *A single session-end POST* — unchanged. *Not events* — unchanged, aggregates are not events. *Any other `fetch()` is a bug* — unchanged. **Only "not behavioral data" falls**, and it falls because aggregated counts of behavioral signals are behavioral data even when derived. The transport rule narrows; the content rule breaks. Do not describe the outbound payload as "geometry and timing only" — that remains true of what is captured in the browser and is no longer true of what leaves it.

**Consequence for `08-claims-register.md`.** The 🟢 no-PII claim splits: *no PII leaves the browser* survives; *the only outbound call is a session-end weight POST* is now false as written. And a session-keyed aggregate is personal data under `05-regulatory-posture.md`'s own posture — *"the moment it can reasonably be tied to a session, account, or device."* Keep "no PII" and "no personal data" strictly apart. Conflating them is retired position §10, and it is the one a partner's privacy counsel catches first.

---

## 21. "Touch-hold-release without completing the tap" as an observed behavior — CORRECTED

**Old:** `01-positioning.md` §3 led its primary category with *"touch-hold-release without completing the tap,"* presented as a named behavior Heed detects, and §10 repeated it as *"holds a tap without releasing it."* It was the most vivid example in the positioning and it had been in canon since 29 Jul 2026.

**Why it lost:** it was never true. `02-product-and-architecture.md` lists four signal types — dwell/idle, field blur without completion, scroll reversal above a delta threshold, back-navigation on an incomplete flow — and **that list is complete** (founder confirmation, 9 Aug 2026). An aborted tap is not among them, and it is not separable from a dwell on a touch target. The prose described a capability the product does not have.

**Replacement:** *a finger resting on a button without pressing it.* A dwell, accurately described, and no less vivid.

**A long touch is sayable. An abort is not.** Barred in `08-claims-register.md`.

**The demo does not overclaim.** The LinkedIn demo's touch signal is a dwell, and the chain recorded as verified in `08-claims-register.md` — touch hesitation → `confusion` → `tooltip` — is a dwell chain. The reconciliation question raised on 8 Aug is answered the other way round from how it was framed: the documented signal types were right and the positioning was wrong.

**The demo's separate defect stands.** `02-product-and-architecture.md` records Beat 5, *"where the net classifies the raw cluster and the Heed overlay renders,"* as **mandatory as the close** — and the render call sites are gone (§18). Its required closing beat shows a capability the product no longer has. That is a rendering problem, not a signal problem.

**What this one is really about.** The abort description survived eleven days and three full canon passes, including two that specifically audited the render architecture, because it was vivid and nobody checked it against the signal-type list. It was not introduced by drift — it was wrong when written. **The lesson is not about taps: a claim that sounds like a product detail should be checked against `02-product-and-architecture.md` the first time it is written, not the fourth time it is quoted.**

---

## Open questions

Class 4 items — conflicting sources Claude cannot resolve alone. See `CLAUDE.md` for the flag procedure.

*Closed 8 Aug 2026, first batch: the read-only first phase (→ §17) and the abandonment-cost denominator (below). Seven items opened, then all seven closed by the second decision batch the same day — RG suppression (contractual, `05-regulatory-posture.md`), overlay div (ship inert, `02-product-and-architecture.md`), processor classification (processor, Phase 1 only, `05`), category name (retained and defended, §16), payload dimensionality (count/mean/p50/p90/max per selector per signal type), Phase 1 pricing (free), Phase 2 pricing basis (flat per-month platform fee, figure open), deployment target (partner elects at scoping), and ephemerality (requalified, `01-positioning.md` §5 and `04-competitive-landscape.md`).*

*A third batch on 8 Aug 2026 closed the session-record question (stratified aggregate), the overlay gating question (call sites removed), and drafted the retention policy. Four items remain open; two are new.*

**CLOSED — session record versus running total.** Resolved to a **stratified aggregate**: the same five statistics per selector per signal type, held in two buckets, completed and abandoned. No session persists. This recovers outcome conditioning and signal-type co-occurrence while staying inside the aggregate bound, and it is not a step toward the raw-events fallback at §20. It carries one live design item — percentiles do not merge, so durations must travel as a fixed-bin histogram and the bin edges are unchosen (`02-product-and-architecture.md`).

**CLOSED — what "inert" means for the overlay.** Call sites removed, not config-gated. "Heed does not render" is an architectural claim. The div itself is left in place and is now vestigial; whether it goes too is the one piece still open (`02-product-and-architecture.md`).

**CLOSED — is the demo's touch signal an abort or a dwell?** A dwell. The four signal types are complete and the positioning prose was wrong; see §21. The demo does not overclaim on signal. Its Beat 5 render defect is unaffected and stands.

**What is the Phase 1 store, and where does it sit?** Retention is drafted (`artifacts/retention-policy.md`) and carries eight fields marked for founder decision. What the store is and where it is hosted are still open, and data residency remains an open counsel question in `05-regulatory-posture.md`. A partner will ask before Phase 1 starts rather than after.

**What is the Phase 2 emission transport?** Webhook, a client-side handoff into a partner SDK already on the page, or a queue. It decides whether Heed-authored inference transits Heed's servers, which is live in the unresolved Phase 2 processor question (`05-regulatory-posture.md`).

**Does `response copy` come out of the config schema?** Raised 10 Aug 2026. The overlay div and the dead log-schema event types were removed on exactly one argument: dead code makes an architectural claim look configurational to a reviewer reading the source. **The `response copy` field survived that pass** and is still in the per-partner config schema, populated in no shipping config (`02-product-and-architecture.md`). It is the same defect in the one artifact a compliance reviewer is most likely to be handed — the config file is described in `05-regulatory-posture.md` as the concrete thing compliance inspects. A reviewer who finds a response-copy field on a product that says it never renders has been given the configurational reading for free. This is not flagged as a contradiction between sources; it is a decided rule with one instance left unapplied, and applying it is a schema change nobody has authorised.

**CLOSED — the vestigial overlay div and the dead log-schema events.** Both removed, 9 Aug 2026, on one reason: dead code is what makes an architectural claim look configurational to a reviewer reading the source. `02-product-and-architecture.md`'s absolute rule now reads *"the partner DOM is untouched"* with no exception clause.

**Plus one figure, deliberately unset:** the Phase 2 monthly amount. Basis decided (flat per-month platform fee), amount not. No number may be quoted (`06-commercial-and-pilot-structure.md`).

**CLOSED — the abandonment-cost denominator.** Previously a GAP: no verified figure existed to anchor against, and a comparative-deferral prospect had no magnitude to score Heed with. **Resolved 8 Aug 2026 — Phase 1's written read is the source, and it is the only one.** The denominator is built from measured stall density against completion outcome on a real partner funnel, not from published rates or a constructed TAM. This interlocks with the provenance carve-out in `CLAUDE.md`: measurement Heed performed under agreement on a partner's own funnel may be used in a report to that partner, which is what makes the read possible at all. Until the first Phase 1 completes, **there is still no denominator** — the source is identified, not populated. `08-claims-register.md`'s prohibition on market-sizing figures stands unchanged, and nothing here licenses inventing one in the meantime.

**A note on the pace of 8 Aug 2026.** Two decision batches in one day retired four positions, rewrote the pilot, changed the architecture, and moved the regulatory posture. That is faster than this set is designed to absorb, and the risk is not that a decision was wrong — it is that a downstream artifact still speaks the retired version to a prospect. Every canonical file was passed over; no external artifact was. Check `CHANGELOG.md` before regenerating anything.
