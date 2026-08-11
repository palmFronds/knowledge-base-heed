# Heed — Data Retention Policy

**Status: DRAFT. Not for external use.** Eight fields need a founder decision before this goes to a partner; each is marked **[DECIDE]**. A retention policy with a blank in it is worse than no policy — it tells a reviewer the question has been asked and not answered.

**Scope:** Phase 1 of a Heed engagement. Phase 2 processes data this policy does not describe and needs its own section once the emission transport is chosen (`canonical/02-product-and-architecture.md`).

Derived from `canonical/02-product-and-architecture.md` and `canonical/05-regulatory-posture.md`. If those and this document disagree, they are canon and this is stale.

---

## 1. What is collected

Heed's script attaches browser event listeners to operator-specified selectors inside the registration → KYC → first funded action flow. It observes four signal types: dwell/idle, field blur without completion, scroll reversal above a delta threshold, and back-navigation intent on an incomplete flow.

**Never collected, at any point, by architecture:** field values of any kind, passwords or credentials, document contents, identity-document images, cookies, `localStorage` contents, page text, or screenshots. Heed does not read the DOM's content — it observes interaction geometry and timing.

## 2. What leaves the browser

**One outbound call per session, at session end.** It carries:

- the updated per-partner model weight array;
- a **per-session aggregate** of that session's signals — per selector, per signal type: count, sum, max, and a fixed-bin duration histogram;
- a flag indicating whether the session completed or abandoned the flow.

**Nothing else leaves the browser.** No raw events, no event sequence, no timestamps, no mid-session transmission. Within-session data is held in browser memory and is discarded when the session ends.

**[DECIDE] — does the payload carry a session identifier?** If it does, the aggregate is personal data under GDPR and UK GDPR from the moment it is transmitted, because it can be tied to a session (`canonical/05-regulatory-posture.md`). If it does not, and sessions are pooled on arrival, the transmitted object may sit outside that definition — but the operator cannot then be given a per-session audit trail. This is the single most consequential field in this document and it should be decided with counsel, not by engineering convenience.

## 3. What Heed stores

On receipt, each session's aggregate is merged into one of two running buckets — **completed** and **abandoned** — held per partner, per selector, per signal type. Counts and sums add; histograms add bin-wise; maxima are compared.

**After the merge, the individual session's contribution is not recoverable.** Heed does not store session records, session identifiers, user identifiers, IP addresses, device fingerprints, or any per-person row. The stored object is a statistical distribution over a population of sessions.

**Per-partner isolation is architectural.** One partner's aggregate never mixes with another's, there is no cross-partner model, and no federated learning.

**[DECIDE] — the store itself.** What it is, who hosts it, and in which jurisdiction. Data residency is an open counsel question (`canonical/05-regulatory-posture.md`) and an EU or UK partner will ask before signature. Answer with a named provider and a named region.

**[DECIDE] — is the receiving endpoint a subprocessor relationship?** If the store is hosted by a third party, that party is a subprocessor and belongs on a subprocessor list this document should reference.

## 4. How long it is kept

**[DECIDE] — retention period for the merged aggregate.** Suggested default for discussion, not adopted: **twelve months** from the end of the engagement, which is long enough for the partner to return to the read and short enough to be unremarkable in review. Any period is defensible if it is stated and honoured; none is defensible if it is silent.

**[DECIDE] — retention period for the model weight array.** The weight corpus is trained on the partner's flow and is contractually theirs to keep (`canonical/06-commercial-and-pilot-structure.md`). Whether Heed also retains a copy after the engagement, and for how long, is a commercial question as much as a privacy one.

**[DECIDE] — retention of the written read itself.** The Phase 1 deliverable is a document containing measured statistics about the partner's funnel. How long Heed keeps its own copy, and whether it may be retained after the partner relationship ends, is unresolved and interacts with the provenance rule in `CLAUDE.md`: measured data stays with the partner it was measured on and does not become a benchmark quoted elsewhere.

**Browser-side:** nothing persists. Heed writes no cookie, sets no `localStorage` key, and leaves no client-side state after the session ends.

## 5. Deletion on request

**Partner-initiated deletion.** On written request, Heed deletes that partner's merged aggregate, weight array, and stored copy of the written read. **[DECIDE] — the turnaround commitment.** Suggested for discussion: thirty days. A stated number is expected in procurement; an unstated one reads as unconsidered.

**Individual data-subject requests — the honest answer, and it needs to be given carefully.** Heed cannot delete an individual's data on request, because Heed holds no individual's data to delete. Once a session's aggregate is merged, that session is not identifiable or separable within the bucket.

This is a genuine strength and it is easy to state in a way that sounds like evasion. State it as: *Heed retains nothing attributable to an individual, so there is nothing for Heed to erase; the operator's own erasure obligations are unaffected because Heed's signal never entered their user record during Phase 1.* Do not state it as "we're out of scope" — that is retired position `canonical/09-retired-positions.md` §10 and a privacy counsel will catch it.

**[DECIDE] — if the operator requests deletion of a *specific* session's contribution before merge**, is there a pre-merge window in which that is possible? If the payload carries a session identifier and is queued before merging, there is. If it merges on arrival, there is not. This follows from §2's decision and should be answered with it.

## 6. Deletion at engagement end

**[DECIDE] — the default at Phase 1 close.** Two coherent options and they are not equivalent.

*Delete on close unless the partner asks otherwise.* Cleanest to state, strongest in review, and it means a partner returning six months later starts from nothing.

*Retain for the stated period unless the partner asks for deletion.* More useful if Phase 2 follows, and requires the retention period in §4 to carry the weight.

Whichever is chosen, the written read is the partner's and is theirs to keep regardless. What is being decided is what **Heed** keeps.

If the engagement does not proceed to Phase 2, the script tag is removed by the partner deleting one line, and collection stops at that moment with no further action required from either side.

## 7. Security

Transport is HTTPS. **[DECIDE] — encryption at rest, access control, and audit logging on the store.** Security review expects an encryption approach, RBAC, and audit logging (`canonical/05-regulatory-posture.md`), and a SOC 2 roadmap with committed dates is typically sufficient at pilot stage. None of this exists yet and a live pilot without a credible SOC 2 path is a recorded stalling point.

## 8. What this policy does not cover

**Phase 2.** Intent classification, emission into the partner's stack, and anything the partner's own systems do with an emitted signal are outside this document. Once the signal reaches the partner's stack it is in their systems under their retention policy, and Heed has no visibility into or control over what happens to it there. Say that plainly rather than implying coverage that does not exist.

**What the operator persists.** Heed's minimisation is a fact about Heed. It is not a fact about the data's life once it is handed over.

---

*Draft raised 8 Aug 2026 against the Phase 1 architecture. Review whenever `canonical/02-product-and-architecture.md` or `canonical/05-regulatory-posture.md` changes.*
