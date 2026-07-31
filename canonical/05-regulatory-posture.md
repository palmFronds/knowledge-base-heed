# 05 — Regulatory Posture

Nothing here is legal advice. Every citation reflects research as of mid-2026 and needs independent verification by qualified counsel before external use.

## The central line

The regulatory challenge is not behavioral analytics. It is ensuring behavioral inference never becomes autonomous decision-making with legal or financial effect. The moment a system decides to suppress an offer, block a deposit, or author what a message says, it stops being a sensing layer and becomes a decision-maker — and that is where compliance burden, licensing exposure, and liability all live.

Heed produces a signal and a confidence score. The operator's pre-approved configuration decides whether and how to respond. Heed's SDK renders the response, using copy the operator's compliance team wrote and approved. That handoff is the entire regulatory position.

## Classification

**Data processor** under GDPR, UK GDPR, and US state privacy law — processing on the operator's instruction for the operator's stated purpose, obligations defined by DPA rather than controller-level duties. This is an architectural intention, not a tested legal conclusion; whether it holds for any specific partner depends on actual DPA language and production data flows.

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

Absolute constraints: users on any self-exclusion or vulnerability register are invisible to the response layer regardless of confidence score, with no configuration option to disable that override. Jurisdiction-specific RG policy is enforced per partner per jurisdiction. Audit logs are immutable, because an RG inquiry needs to reconstruct what a specific user was shown and why, months later.

## Dark patterns

Because the function is influencing behavior at a moment of hesitation, Heed sits closer to dark-pattern scrutiny than almost any other infrastructure vendor, independent of gaming or fintech law. The FTC's 2024 rule was vacated on procedural grounds in 2025, but the conduct remains enforceable under general Section 5 authority. California, Colorado, and Connecticut privacy law each treat dark patterns as invalidating consent obtained through them.

Response rendering carries no manufactured urgency, no fake countdowns or artificial scarcity, no hidden or pre-selected choices, no forced friction making declining harder than accepting. Because copy is authored by the operator's compliance-reviewed team, Heed's exposure is substantially about the rendering mechanism rather than about copy it does not write.

## Marketing and promotions

Bonuses, promotions, cashback, and deposit incentives are regulated marketing activity in every relevant jurisdiction. UK LCCP social responsibility provisions tightened in January 2026 with a 10x cap on bonus wagering requirements and a ban on mixed-product promotions.

Heed never calculates an offer's value, determines eligibility, or generates promotional messaging. Where a partner configures a `discount_offer` response, Heed fires a pre-approved, pre-priced offer slot and passes acceptance back via `postMessage`. It does not fulfil, price, or originate the reward.

**This is the constraint most likely to be broken by careless framing.** "We fire the bonus" is a sentence that travels, and the version a licensed operator's compliance team hears is "you originate the inducement." Keep the copy-ownership clause attached every time.

## KYC and AML

Heed never touches identity documents, verification outcomes, sanctions screening, or AML risk scoring. Its value in the KYC flow is entirely about the experience of getting through it — is the user confused by a field, stuck on an upload — never about the outcome of it.

## Procurement expectations

**Legal** wants a signed DPA, privacy documentation, a subprocessor list, and a retention policy. Maintain these as standing, always-current documents rather than per-deal artifacts; this is the single fastest way to shorten legal review.

**Security** wants a SOC 2 roadmap or report, penetration test results, encryption approach, RBAC, and audit logging. A roadmap with committed dates is typically sufficient at pilot stage, but a live pilot without a credible SOC 2 path is a common stalling point.

**Engineering** wants SDK documentation, event schema, architecture diagrams, latency guarantees, and a kill switch. The script-tag model answers most of this by itself.

**Compliance** wants RG exclusion handling, an intervention-approval workflow, jurisdiction-level controls, and explicit confirmation the operator owns all business logic. This review most directly tests the signal-not-decision architecture, and the per-partner config file is what gives it something concrete to inspect.

## Open questions requiring jurisdiction-specific counsel

Supplier licensing thresholds. GDPR Article 22 and UK Articles 22A–22D applicability to any specific partner configuration. Consent requirements for behavioral profiling, which vary by US state and are actively moving. Cross-operator model training, which is currently prohibited architecturally and would need its own review before any engineering work. Data residency. Gaming supplier certification, distinct from licensing. Whether the SDK itself needs independent review as part of an operator's RG program. State-by-state supplier registration in the US.

None of these should be represented as settled to a partner, investor, or regulator.
