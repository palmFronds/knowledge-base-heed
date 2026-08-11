# 05 — Regulatory Posture

Nothing here is legal advice. Every citation reflects research as of mid-2026 and needs independent verification by qualified counsel before external use.

## The central line

The regulatory challenge is not behavioral analytics. It is ensuring behavioral inference never becomes autonomous decision-making with legal or financial effect. The moment a system decides to suppress an offer, block a deposit, or author what a message says, it stops being a sensing layer and becomes a decision-maker — and that is where compliance burden, licensing exposure, and liability all live.

Heed produces a signal and a confidence score and emits it into the operator's stack. Everything after that is the operator's — their tooling, their rules, their copy, their contact with the customer. **That handoff is still the entire regulatory position, and since 8 Aug 2026 it happens one step earlier than it used to** (`09-retired-positions.md` §18). Heed does not render, does not contact a user, and does not execute a decision.

## Classification

**Data processor under GDPR, UK GDPR, and US state privacy law — scoped to Phase 1.** Position taken 8 Aug 2026, and the scoping is the substance: the analysis below is written to Phase 1 and **does not extend to Phase 2 by inheritance.** This remains an architectural intention, not a tested legal conclusion; whether it holds for any specific partner depends on actual DPA language and production data flows.

### Phase 1 — the processor argument, and it is the strongest version Heed will ever have

Phase 1 processes on the operator's instruction for the operator's stated purpose. It runs no inference, creates no new attribute about a person, renders nothing, and returns an aggregate to the party that asked for it. The operator specifies the selectors; Heed supplies listeners and returns statistics. Obligations are defined by DPA rather than by controller-level duties.

**Does defining hesitation determine a purpose rather than follow an instruction?** This is the sharpest available challenge and it is thin for Phase 1. Heed sets the dwell threshold and the scroll-reversal delta that decide what counts as a signal, and the operator does not make that determination. The answer is that this determines *means*, not *purpose*. The purpose is the operator's — understand where onboarding stalls. The threshold is a technical implementation detail of the kind a processor is permitted to choose: a non-essential means, not an essential one. Heed does not decide what categories of data are collected in principle, how long anything is kept, or who may see it.

**Say it while it is true.** With no inference running, Heed is closer to a measurement instrument than to a decision system, and this argument will never be easier to make than it is in Phase 1.

**The persistent-profile exposure.** Heed's output becomes durable inside the operator's store while Heed retains nothing beyond the aggregate. This does not convert Heed to a controller — a processor returning output that the controller then persists is ordinary processing, and the persistence decision is the controller's. It does change what may be *said* about it: Heed's minimisation is a fact about Heed, not a fact about the data's life. See the requalified ephemerality claim in `01-positioning.md` §5 and `04-competitive-landscape.md`.

### Phase 2 — does not inherit, and is not resolved

**State the Phase 1 classification only. Do not extend it, and do not let a reviewer assume it carries.**

Phase 2 differs where it matters. It runs inference and creates a **new personal-data attribute** — an intent classification with a confidence score — using a model, per-partner weights, and a definition of intent that are all Heed's. That is materially closer to determining essential means than a dwell threshold is, and it raises a joint-controllership question Phase 1 does not raise. Emission then places Heed-authored inference into the operator's profile store as a durable attribute about an identified person, on a data flow that did not exist under the retired architecture.

**Open question, requiring counsel:** whether Heed remains a processor in Phase 2, and whether the emission transport decides it. A classification computed in the browser and handed to a partner SDK already on the page is a different fact pattern from one that transits Heed's servers, and that transport is itself undecided (`02-product-and-architecture.md`). Do not answer this in a call. "Phase 1 is processor-scoped and Phase 2 needs its own analysis" is a credible answer; a confident extension is not.

**Behavioral profiling system.** Unavoidable and not contested. Scoring a user's likelihood of abandoning is profiling under every relevant framework. Profiling triggers disclosure obligations, not prohibition. The strategy is not to dodge the label but to stay decisively on the correct side of the profiling-versus-automated-decision-making line.

**Gaming supplier / technology vendor**, potentially, depending on jurisdiction and on exactly what the software touches. A vendor that only observes UI interaction and returns a confidence score sits materially lighter than one generating or storing essential regulatory records. Malta's MGA requires a B2B critical gaming supply license for vendors handling essential regulatory records; Heed has a reasonable basis to sit outside that definition but this must be confirmed with Malta-qualified counsel, not assumed.

**Infrastructure**, as commercial framing. A vendor described as infrastructure that senses and reports moves through procurement, security review, and compliance sign-off far faster than one described as an AI system that intervenes with users, even where the technology is identical.

## Correction to a claim in earlier materials

Prior pilot material asserted that because no PII leaves the browser, Heed sits **outside the scope of personal data definitions and outside the partner's DPAs entirely.** That is wrong and it contradicts the regulatory analysis in the same document set.

Behavioral interaction data becomes personal data under essentially every relevant framework the moment it can reasonably be tied to a session, account, or device — without a name or email attached. The correct posture assumes this applies rather than arguing around it. Data minimisation narrows the lawful-basis analysis an operator has to perform; it does not remove Heed from scope. A partner's privacy counsel will catch the stronger claim immediately, and it costs more credibility than the claim was ever worth.

## Must never — architectural, not configurable

Capture document contents. Capture a password or credential. Record the value of any sensitive text field. Modify a regulated decision — KYC outcome, AML flag, wagering limit, deposit approval. Generate or price an offer autonomously. Override a responsible-gambling control, under any configuration, for any partner.

A single accidental instance surfaced in a partner audit converts Heed's classification from signal-only infrastructure to a system touching regulated outcomes, with no clean way back once a compliance team's trust is gone.

## Responsible gambling

RG regulation has moved toward *encouraging* behavioral analytics — UKGC customer-interaction rules require operators to monitor a defined set of behavioral indicators, and affordability checks escalate at defined loss thresholds. Ontario's AGCO standards require accessible deposit and time limits, self-exclusions honoured for at least six months, and no incentives or promotional contact to self-excluded players.

The load-bearing distinction: **analytics intended to improve player safety and analytics intended to increase monetisation are the same technology pointed in opposite directions**, and regulators, partners, and press will not treat them as equivalent just because the signal math is identical.

### Suppression is contractual — changed 8 Aug 2026

**Retired.** This file previously stated: *"users on any self-exclusion or vulnerability register are invisible to the response layer regardless of confidence score, with no configuration option to disable that override."* `01-positioning.md` §9 carried the matching promise: *"RG suppression always wins over Heed's own signal, with no configuration path to disable that."* Both described a Heed-side response layer that no longer fires (`09-retired-positions.md` §18). Heed cannot enforce a suppression it has no mechanism to apply. **Neither sentence may be repeated.**

**What Heed claims now.** Heed emits a signal describing observed interaction. It holds no register, receives no exclusion status, and takes no action toward any user. It cannot suppress, because there is nothing on Heed's side to suppress.

**What the partner warrants.** That self-exclusion, vulnerability-register, and jurisdiction-specific RG controls are applied on their side — downstream of Heed's signal and upstream of any customer contact. Jurisdiction-specific RG policy remains enforced per partner per jurisdiction; it is now enforced *by* the partner.

**Where it is written.** In the agreement, as a partner warranty rather than a Heed representation. And in the pilot brief, stated plainly rather than left to the contract. A compliance reviewer who hears the old promise on a call and then discovers the transfer of responsibility in the paperwork is the worst version of this conversation, and it is avoidable by saying it first.

**The residual failure mode, stated rather than written around.** Heed emits a hesitation signal on a session belonging to a self-excluded player; the operator's CRM consumes it and fires promotional copy at that player. This is a live possibility. Heed cannot prevent it. The warranty allocates responsibility for it — it does not eliminate it. Do not soften this: promotional contact with a self-excluded player is the conduct the UKGC and AGCO treat most severely, and it is the first question a competent reviewer will ask. Answer it before it is asked.

### Design consequences — requirements, not preferences

Three conditions on the emission layer, which exist so the transfer of responsibility is auditable rather than a disclaimer.

1. **Emission carries an operator-auditable acknowledgment.** Every emitted signal is logged with an acknowledgment from the receiving system, so a downstream suppression failure is attributable to a specific signal at a specific time rather than unfalsifiable after the fact. Without it neither party can reconstruct whether a signal was emitted, received, or acted on, and the warranty is unenforceable in both directions.
2. **The emitted object is legible to a rule engine.** Signal type, selector, and confidence as separate fields — **never a single blended score.** The partner's RG controls have to be able to condition on what was observed and where. A blended score cannot be gated by a rule that needs to know whether the user was hesitating over a fee row or a document upload.
3. **The suppression warranty and the partner's RG integration are Phase 2 preconditions**, surfaced during Phase 1 scoping rather than at Phase 2 signature. Phase 1 emits nothing and needs neither. Discovering at signature that the partner has no rule engine able to consume a gated signal is a late and expensive discovery. See `06-commercial-and-pilot-structure.md`.

Audit logs remain immutable. An RG inquiry needs to reconstruct what a specific user was shown and why, months later — and under the emit architecture Heed can reconstruct only what it emitted, which is exactly why point 1 is a requirement and not a nicety.

## Dark patterns

**This exposure has moved.** Under the retired render architecture Heed showed things to users and therefore sat closer to dark-pattern scrutiny than almost any other infrastructure vendor. Heed now shows nothing. Dark patterns are a property of what a user is presented with, and Heed presents nothing to anyone — no manufactured urgency, no countdowns or artificial scarcity, no hidden or pre-selected choices, no forced friction making declining harder than accepting, because there is no surface on which any of those could exist. The exposure transfers to the operator, who authors and renders whatever their tooling does with the signal.

**As of 9 Aug 2026 this is true of the source and not only of every shipping configuration** — the render call sites and the overlay div are both removed (`02-product-and-architecture.md`). The qualification that stood here, that the div still shipped inert and so "Heed does not render" was a configuration fact rather than an architectural one, is withdrawn. Say the strong version; it is now the accurate one.

One qualification survives, and a reviewer will find it on their own.

**Heed still identifies the moment of hesitation** — the moment at which an intervention is most effective and most questionable. Producing the signal that makes a well-timed intervention possible is not the same as delivering one, but it is not nothing, and the honest framing is that Heed's exposure is now about what it enables rather than what it does. The FTC's 2024 rule was vacated on procedural grounds in 2025, but the conduct remains enforceable under general Section 5 authority, and California, Colorado, and Connecticut privacy law each treat dark patterns as invalidating consent obtained through them.

## Marketing and promotions

Bonuses, promotions, cashback, and deposit incentives are regulated marketing activity in every relevant jurisdiction. UK LCCP social responsibility provisions tightened in January 2026 with a 10x cap on bonus wagering requirements and a ban on mixed-product promotions.

Heed never calculates an offer's value, determines eligibility, generates promotional messaging, or fires an offer. Under the emit architecture there is no `discount_offer` response and no `postMessage` handoff at all — the partner's own tooling does whatever it does with the signal.

**This is still the constraint most likely to be broken by careless framing, and the architecture change makes the careless version easier rather than harder.** "We fire the bonus" was always wrong. **"We tell your CRM when to fire the bonus" is the new version of the same sentence** and lands identically with a licensed operator's compliance team: you originate the inducement. Heed reports an observation; the operator decides that an observation warrants an offer. Keep the copy-ownership clause attached every time.

## KYC and AML

Heed never touches identity documents, verification outcomes, sanctions screening, or AML risk scoring. Its value in the KYC flow is entirely about the experience of getting through it — is the user confused by a field, stuck on an upload — never about the outcome of it.

## Procurement expectations

**Legal** wants a signed DPA, privacy documentation, a subprocessor list, and a retention policy. Maintain these as standing, always-current documents rather than per-deal artifacts; this is the single fastest way to shorten legal review. **The retention policy is now load-bearing rather than formal** — Phase 1 requires a store for the session-end aggregate. **Drafted 8 Aug 2026 at `artifacts/retention-policy.md`, and it is not usable yet:** eight fields carry founder decisions, the sharpest being whether the transmitted aggregate carries a session identifier, which decides whether it is personal data on arrival. Where the store sits remains open and interacts with the data-residency question below. A partner will ask before Phase 1 starts, not after. The agreement also now carries a **partner RG-suppression warranty** rather than a Heed representation; that is a negotiated term, so surface it at scoping.

**Security** wants a SOC 2 roadmap or report, penetration test results, encryption approach, RBAC, and audit logging. A roadmap with committed dates is typically sufficient at pilot stage, but a live pilot without a credible SOC 2 path is a common stalling point.

**Engineering** wants SDK documentation, event schema, architecture diagrams, latency guarantees, and a kill switch. The script-tag model answers most of this by itself.

**Compliance** wants RG exclusion handling, an intervention-approval workflow, jurisdiction-level controls, and explicit confirmation the operator owns all business logic. This review most directly tests the signal-not-decision architecture, and the per-partner config file is what gives it something concrete to inspect.

## Open questions requiring jurisdiction-specific counsel

Supplier licensing thresholds. GDPR Article 22 and UK Articles 22A–22D applicability to any specific partner configuration. Consent requirements for behavioral profiling, which vary by US state and are actively moving. Cross-operator model training, which is currently prohibited architecturally and would need its own review before any engineering work. Data residency. Gaming supplier certification, distinct from licensing. Whether the SDK itself needs independent review as part of an operator's RG program. State-by-state supplier registration in the US.

None of these should be represented as settled to a partner, investor, or regulator.
