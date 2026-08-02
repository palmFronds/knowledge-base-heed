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

**Replacement:** Overlay only, permanently. Not a v0 limitation.

---

## 7. Sandboxed iframe integration — RETIRED

**Old:** `Product_Posture.md`: "Single script tag injects a full-viewport iframe... all communication via `postMessage` only."

**Why it lost:** Superseded by the shipping implementation, which injects a transparent overlay div into `document.body`. `postMessage` survives, but only as the `discount_offer` CTA handoff to the host window.

**Replacement:** Overlay div, as built and tested.

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

## 14. Mid-session monetisation — OUT OF SCOPE, BUT DRIFTING

**Position:** Bonus deployment on loss events is deprioritised for UKGC and RG tail risk. The pilot scope is registration through first funded action only.

**The drift:** The Ember report offers "bonus deployment based on intent" pointed at a run of consecutive losses as use case 2, and a live LinkedIn message named bonus deployment as the example response. Ember is Bitcoin-native and probably not UKGC-licensed, so it may be survivable there — but the framing is now in written material and contradicts the stated scope.

**Decision needed:** either declare it a deliberate exception for non-licensed operators and document the boundary, or remove it from the template before the next report goes to a licensed prospect. Default to a unit explainer or conversion breakdown as the example response; they make the same point without teaching the habit.

---

## 15. Pricing — UNRESOLVED, NOT RETIRED

Deck script says $5–8K/month pilot tier. One-pager says $3–5K per engagement. Neither has been withdrawn. This is the one open contradiction in the set and must be settled before another prospect sees both documents. See `06-commercial-and-pilot-structure.md`.

---

## Open questions

None currently flagged. Class 4 items (conflicting sources Claude cannot resolve alone) land here as they surface — see `CLAUDE.md` for the flag procedure.
