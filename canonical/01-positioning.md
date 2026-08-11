# Heed — Canonical Positioning

**Status:** Canonical. This file is authoritative on positioning, competitive framing, and approved language.
**Last reviewed:** 2026-08-04
**Owner:** Dheeraj

**Supersedes entirely:**
- `Product_Posture.md` (Parallax-era). Retired in full — retired positioning, retired ICP, and an architecture description (sandboxed iframe / postMessage) that does not match what shipped.
- The positioning and competitive sections of both regulatory reports (§4, §5, §7 in each).
- The "The Problem" and "What Heed Does" sections of the Pilot Brief.

**Does not supersede:**
- The regulatory reports' legal analysis (§1, §2, §3, §9) — still current, still needs counsel review per Appendix A.
- `Product_Spec.md` / `Pilot_Specs.txt` engineering detail — these need their own consolidation, separately, into one spec.

**Category:** intelligent behavioral intervention. See §11.

---

## 1. The claim

Every tool in an operator's stack observes the behaviors that someone already decided to name. Heed observes behavior.

That is the whole differentiator, stated as one thing rather than several. An event is a human-authored abstraction over behavior: somebody decided in advance that a particular occurrence was worth naming, gave it a name, and instrumented it. Everything downstream of that decision — CRM, CDP, warehouse, lifecycle orchestration, experimentation — operates on the resulting vocabulary rather than on the behavior itself. The ceiling is therefore not speed, sophistication, or budget. It is that the vocabulary was written before the session by someone guessing what would matter.

Heed's input is the raw interaction stream: the browser's own timing and geometry, before any naming step. Nothing about a behavior needs to have been anticipated for Heed to see it.

## 2. One axis, not two

Retroactivity is a **consequence** of the input model, not a second independent axis, and it must be presented that way.

If the only observable things are named events, then anything unnamed can only be discovered through aggregate degradation after the fact — a funnel report shows drop-off, someone asks why, an event gets specced, engineering ships it, and the next cohort is measured. The lag is not a property of pipeline latency. It is a property of what the pipeline is able to accept as input.

This matters because framing retroactivity as a co-equal axis hands the incumbent a quadrant. Optimove has genuine real-time triggering; on a speed axis they are at parity, and the prospect gets to conclude it is half a differentiator. Collapsed to one axis, "they're real-time" becomes a concession that does not touch the claim: they are fast at reacting to the things they already decided to watch.

## 3. What is invisible to an event pipeline

Two categories, and they are not equally strong. Lead with the first.

**Primary — stalled and partial physical actions.** A cursor settling on Confirm for eleven seconds. A finger resting on a button without pressing it. Scroll reversal back to the fee row. Field focus with no entry. Back-navigation on a flow that was never finished. These are not absences: they are positive, present, continuously-structured behaviors that the browser emits and that no analytics ontology has a name for. There is no timeout that catches them, because nothing is pending — nothing started. This is the ground to fight on.

**Corrected 9 Aug 2026 — the examples now match what Heed actually observes.** This paragraph previously led with *"touch-hold-release without completing the tap,"* which described an aborted tap as a named behavior Heed detects. It is not one. `02-product-and-architecture.md` lists four signal types — dwell/idle, field blur without completion, scroll reversal above a delta threshold, back-navigation on an incomplete flow — and that list is complete. A long touch is a dwell on a touch target and is observed; the *abort* is not separable from it. **A long touch is sayable. An abort is not.** Every example above maps to one of the four.

**Secondary — genuine absences.** `swap_started` fires; `swap_completed` never does. A competent CRM team **can** detect this with a timeout, and a sharp prospect will say so. What it requires is having predicted in advance which absence matters and how long to wait, which is the pre-declaration problem again rather than an impossibility. Use this as a supporting beat. Never as the headline.

## 4. Retired framings — do not use

**Latency / speed.** "Faster than competitors," "we act in the moment they act minutes later," "we fill the latency gap." This is a straw man. Optimove's real-time triggering is real, and any prospect who has been sold by them will know it. The correct argument is that an event-driven pipeline can be infinitely fast and still have nothing to act on when a user pauses or reverses scroll.

*Live instances still in circulation:* Regulatory Report §7 ("fills the latency gap between user hesitation and operator response") and the Pilot Brief's problem statement ("fires five to thirty minutes after a player has gone cold"). Both must be rewritten before the next prospect touchpoint. A prospect who read the brief will bring the retired version into the call.

**"The absence of rules entirely."** Currently in the Pilot Brief. It is not true and it is cheap to knock down — the config layer is thresholds and per-intent response mappings, which are rules, authored in advance, by the operator.

The precise and stronger version: **detection is rule-free; what happens next is deliberately and entirely rule-based, and the rules are the operator's.** Heed's config layer holds thresholds; everything past the signal runs on the operator's own rule engine, their own copy, their own approvals. That the response side is pre-declared is the point, not a limitation — it is what makes the product approvable by a compliance team. Conflating the two halves concedes a point that should never be available.

*Updated 9 Aug 2026 — this previously read "response is deliberately and entirely rule-based" and described per-intent response mappings inside Heed's config. Heed has no response side (`09-retired-positions.md` §18).*

**Demo beat discipline.** Any copy that references *when* something fired rather than *what it could observe* has reverted to the latency straw man. This applies to HUD labels, deck copy, and LinkedIn artifact captions.

## 5. Competitive framing

The kill line differs by category, and knowing which axis is load-bearing per objection is what keeps the frame stable under pressure.

| Category | Examples | The claim that separates us |
|---|---|---|
| CRM / lifecycle | Optimove, Fast Track, Braze, Iterable | Input model. There is no event for a behavior nobody named, and no event for a user who hasn't done anything. Their real-time capability is real and irrelevant to this. |
| CDP | Segment, Tealium, mParticle | Input model, plus architecture: the value proposition is a persistent cross-tool profile, which is the opposite of a signal Heed computes and does not keep. **Requalified 8 Aug 2026 — say "ephemeral in our hands," never "ephemeral."** After emission Heed retains nothing; what the operator persists in their own store is theirs, and a CDP is a plausible destination for it. The old phrasing ("an ephemeral single-session signal") now overclaims. |
| Product analytics (event-based) | Mixpanel, Amplitude, PostHog | Input model, plus no classification layer and nothing delivered to a system that could act — a human reads a chart and briefs an engineer. **Not "no response mechanism"** — Heed has none either. The separation is that their output terminates in a dashboard and Heed's arrives in the operator's rule engine. |
| **Session replay** | **FullStory, Hotjar** | **Input model does NOT separate us.** See below. |
| Experimentation / flags | LaunchDarkly, Statsig | No behavioral substrate at all. Static targeting rules evaluated at page load, resolved before the session begins. |
| Fraud / risk / RG scoring | — | Cold-start. A first-time depositor has no history, which is exactly the population these models are weakest on and exactly where onboarding abandonment is highest. Also answers a different question entirely. |

**The FullStory carve-out — hold this in reserve.** Session replay *does* capture raw substrate. It is the one category where the input-model claim does not separate us, and leading with "we see raw behavior" in front of an operator who owns FullStory gets "we already have that." Against session replay the separating claim is entirely on the action side: capture is for retrospective review by a human who has to go looking, with no intent classification and nothing delivered to a system that could act on it. Heed classifies and emits. The privacy comparison is materially in Heed's favour and remains so — but **state it as "we capture geometry and timing, and what leaves the page is an aggregate,"** not as "geometry-and-timing-only payloads," which described the retired architecture's outbound call and no longer describes ours (`09-retired-positions.md` §20). Do not open with any of this; deploy it when replay comes up.

## 6. Supporting evidence

**Betting Hero.** A paid human-concierge activation vendor used by major sportsbooks. Operators running full analytics and CRM stacks concluded their own software could not intervene at the hesitation moment and started paying humans to stand in bars instead. This indicts the incumbent stack using the incumbents' own customers' spending as proof, which is why it lands harder than any feature comparison. Operator-side intel via Scott Miller (former Betting Hero, since departed) on the reg→FTD friction lane.

## 7. ICP and wedge

**Wedge:** the registration → KYC → first funded action lane, specifically. Highest abandonment, lowest regulatory sensitivity (no wagering or promotional logic in scope), cleanest before/after measurement because a completed first funded action is binary.

**High-value capture inside the wedge.** Identifying and converting a high-value player — including a rival's VIP — *before their first bet* is inside this window, not a separate product scope. The LATAM intel about operators competing for VIPs pre-bet maps to onboarding friction, not post-funding retention. Post-funding VIP retention, cross-session lifecycle work, and identification after a player has already bet are out of scope.

**Deprioritized:** mid-session monetization triggering. Carries UKGC/RG regulatory tail risk and puts the product on the wrong side of the safety-vs-monetization line during the period when its thresholds are least proven.

**Verticals:** iGaming (Tier 1 ICP), DeFi on-ramps (parallel), prediction markets (emerging third).

**Regulatory tiering changes the pitch.** UKGC/MGA-licensed operators respond to the compliance-native framing; offshore operators do not weight it the same way. Match the framing to the operator's own regulatory bar rather than leading with compliance universally.

## 8. Pricing

**$3–5K per engagement** for the two-to-four-week pilot, fixed fee, stated scope. Not a monthly rate.

The deck script's $5–8K/month figure is withdrawn — see `09-retired-positions.md` §15. Correct the deck script before the next prospect touchpoint.

## 9. Architectural constraints referenced by positioning

Stated here only because the positioning depends on them being true. Full treatment lives in the regulatory report.

Heed produces a signal and a confidence score and emits it into the operator's stack; the operator acts on it with tooling they already run. Heed never captures document contents, credentials, or sensitive field values; never modifies a regulated decision; never generates, prices, or fulfils an offer; and never renders anything to a user.

**Emit-only is an asset. Lead with it.** Confirmed 9 Aug 2026 and promoted out of the architecture section into the argument. Heed emits a signal into the operator's stack; the operator acts on it with tooling they already run. Heed never renders, never shows a user anything, never originates a response.

**"Heed never shows your users anything" is the shortest path through a compliance conversation** — say it early rather than arriving at it under questioning. It closes dark patterns, response-copy approval, RG rendering, promotional-marketing origination, and UI change control in a single sentence, because none of those exposures can attach to a system with no surface. Every one of them used to require its own answer.

**Constraint on how the signal is described.** It must be mechanically consumable by the rule engine the operator already runs — the same shape as the signals they already route, because a signal they cannot ingest is a signal they cannot act on. **But it is never positioned as another CRM event.** The framing is: *an event for something that has never had one. Same shape, unprecedented content.* Any copy that lets it read as one more event type collapses the input-model argument into exactly the objection it exists to answer — "so it's another event in our stream" is the prospect agreeing with a version of the pitch that concedes everything. Shape is an integration fact, stated when integration comes up. Content is the argument, and it leads.

**Responsible gambling is contractual, not architectural.** Changed 8 Aug 2026, and it must be stated accurately because the previous version promised more than Heed can deliver. Heed does not know whether a session belongs to a self-excluded or flagged player and has no mechanism to suppress anything — there is no response layer left to suppress. **The partner warrants suppression on their side.** Heed's signal is one input to a rule engine the partner already operates and already governs. Heed makes no enforcement claim of any kind. The warranty language and the residual failure mode are in `05-regulatory-posture.md`; do not paraphrase them from memory in a call.

The load-bearing sentence for compliance reviewers: *"Heed identifies friction. The operator determines whether and how to assist the customer."* It is now literally true rather than architecturally guaranteed.

## 10. Objection handling

**"We already have real-time — Optimove does this."**
Concede the speed point immediately; it is true and defending against it costs credibility. Then reframe to input: a pipeline can be infinitely fast and still have nothing to act on when a user pauses, rests a finger on a button without pressing it, or scrolls back to re-read a fee row. Ask which event in their schema fires on that.

**"Then why can't Optimove just add a hesitation listener?"**
Mechanically they can — a client-side script emitting `user_hesitated` is not hard. Be honest about this. What it requires is deciding what hesitation *means*, per screen, in advance, as a threshold — which reintroduces the pre-declaration problem and lands them back in the discovery loop they were trying to exit. Note clearly: this is a *why-they-haven't* answer, not a moat. Do not present it as one.

**"So what's the actual moat?"**
Not the insight. The learned per-partner weights accumulated against a specific flow, and a client-side inference architecture that an existing CRM or CDP cannot retrofit without giving up the persistent cross-source profile that makes their product recognizable to their own customers.

**"We already have FullStory."**
See §5 carve-out. Move to the action axis, not the input axis.

**"This is behavioral manipulation / dark patterns."**
**"Heed never shows your users anything."** That is the whole answer and it should be the first sentence, not the recovery. Dark patterns are a property of what a user is presented with; Heed presents nothing, has no surface, and authors no copy. Whatever the operator's tooling does with the signal is authored and approved by the operator's own compliance function. Scope is onboarding and first funding, not wagering. If pressed on what Heed enables rather than what it does, concede the distinction honestly — see `05-regulatory-posture.md`, which does not dodge it.

*Updated 9 Aug 2026 — this previously answered on "the rendering mechanism," which Heed no longer has.*

**"This is a feature, not a product."**
The most damaging read available, because it is not hostile — it sounds like a compliment and it ends the conversation. A feature competes for roadmap slots against everything else the team could build. A coverage gap in the event stream does not, because closing it is instrumented rather than built: there is no backend access, no database access, and no code change beyond the script tag. Answer on that distinction, not on scope or ambition. Any language that describes Heed as something the operator *adds* rather than something the operator *sees* permits the feature read.

**"We could build this ourselves."**
Never argue that the prospect cannot build it — mechanically they can, and disputing it costs the credibility the rest of the conversation runs on. The problem is that an unscoped internal build is free in the prospect's model and therefore beats any priced vendor. The work is to give the build a scope. Raise it in discovery before they do, with a direct question, then run implication: who owns it, what is the estimate, what does it displace on the roadmap, and — if it has been proposed before — why it stalled. Work the prospect has already identified and not completed is the strongest ground available, because the engagement then serves a decision they have already made rather than asking for a new one.

**"We'd rather not be first."**
First-mover framing reads as risk in a regulated environment. This was already a known outbound learning with no counter attached; the counter is two-part and has to be delivered before the prospect raises it, not after. *Category de-risking* — behavioral inference is not a new category. It is established in fraud, AML, and account-security tooling, and Mindway AI and Neccton already run it inside licensed gambling operators and through their compliance reviews (`04-competitive-landscape.md`). Heed applies a known category at a new point in the funnel. *Cost-of-first reduction* — being first now costs almost nothing, because Phase 1 is where the prospect starts and Phase 1 changes nothing. It senses and reports: listeners on the flow, no inference, nothing rendered, no change to the user experience, free or nominal, removable by deleting one line. There is no funnel modification to review and no response copy for their compliance team to approve. The prospect can take the written read, act on it with their own tools, and never enter Phase 2 — and that is the point, not a concession. It is what converts "be our first customer" into "let us show you something about your own funnel" (`06-commercial-and-pilot-structure.md`).

**Comparative deferral — an objection class, not a single line.**
The prospect accepts the thesis, then scores Heed against alternative uses of the same engineering resource. It is distinct from a thesis objection ("does hesitation actually matter") and from a capability objection ("can you really detect it"), and it never touches the input-model argument at all. Signature: warmth on the call, criteria delivered afterwards in writing, deferral measured in quarters. The worked example is Jackpot.com, August 2026 — deferred to early 2027 on internal build feasibility, first-customer risk, and roadmap effort-versus-impact (`03-market-and-icp.md`).

This class is countered in discovery, never in rebuttal. Once the criteria have been stated they are a position the prospect has committed to, and arguing them then costs more than surfacing them would have. The two objections above are its components; both belong in the discovery script.

## 11. Approved and banned language

**Use:** intelligent behavioral intervention; behavioral substrate; input model; pre-declared vocabulary; observes behavior rather than named events; signal, not decision; operator retains authority over every regulated outcome; **a coverage gap in the event stream**; **"Heed never shows your users anything"**; **"an event for something that has never had one."**

**Avoid — the event-parity register.** "Just another event," "one more event type," "an event like any other," "it plugs into your stream," "plugs in like a CRM." All of these are true about the *shape* and fatal to the argument. The signal is shaped like their events so their rule engine can consume it; it is not one of their events, because theirs are the ones somebody named in advance. If a prospect says "so it's another event," that is not agreement — it is the input-model argument collapsing into the objection it exists to answer. Correct it in the moment: *same shape, so you can route it. Different content, because nobody ever named this one.*

**Avoid — the feature register.** Anything that positions Heed as something the operator builds or adds: feature, add-on, module, capability we'd layer in, something to slot into the roadmap. A feature competes for engineering time; a coverage gap does not. Audit call language and outbound copy for this specifically — it is the read a prospect reached for unprompted in August 2026.

**The in-session rule — testable, and it governs every artifact.** Decided 8 Aug 2026, and it exists because the latency framing has reverted at least four times (`09-retired-positions.md` §1, §2).

*In-session* may not appear in a sentence that does not also carry the no-event clause. **Same sentence — not the same paragraph, not the next one.** The clause is the entire reason the timing is not a speed claim: the signal arrives during the session because there was never an event to wait for.

Banned constructions, which are this claim with the clause stripped out: **"in time to act," "while it's still happening," "before they leave," "in the moment," "real-time."** Each asserts *when* rather than *what*, and each hands back the quadrant §2 of the retired-positions file exists to protect.

Compliant, both usable verbatim:
- "Heed classifies intent in-session, on behavior your event schema has no name for."
- "The signal is in-session because there is nothing to wait for — a pause was never named, so there is no event to fire on afterwards either."

**The test:** delete the no-event clause from your sentence. If what remains is still a claim, it was a speed claim wearing a clause. If what remains is incomplete, the sentence is sound.

**Category name:** **intelligent behavioral intervention.** Use this when asked what category Heed occupies. It describes what the product does without asserting speed as the differentiator and without the "control layer" framing, which implied authority Heed does not hold. **Retained 8 Aug 2026** after the emit architecture removed Heed from the intervention itself.

**The challenge will come, so rehearse the answer rather than improvising it.** The challenge is *"you don't intervene — the operator does."* One sentence:

> **"We're the intelligence layer of an intervention system. The operator owns the intervention; we're the reason it can happen at all, because the behavior it responds to was never an event."**

The second clause does the work. It carries the no-event claim, so the answer defends the category and restates the differentiator in the same breath instead of conceding ground and then rebuilding.

Do not soften the name to something Heed unambiguously does on its own. Two prior names were retired for overclaiming and the defense is recorded at `09-retired-positions.md` §16 — read it before conceding this one, because the argument for keeping it is already written down.

**Avoid:** faster than / real-time as the differentiator; latency gap; no rules at all; AI decision engine; another CRM; personalization engine; anything asserting *when* a signal fired as the point of comparison.

**Top-line framing rule:** lead with operator outcomes (measurable lift in FTD conversion), and keep product mechanics out of top-line descriptions in both prospect-facing and investor-facing material. Mechanics are the second question, never the first sentence.

**The one standing exception — integration effort.** State the absence of integration effort unprompted in compliance- and roadmap-sensitive calls: no backend access, no database access, no code change beyond the script tag, removable in one line. This is not a breach of the rule above. Absence of effort *is* the operator outcome, and it is the fact that stops a roadmap-constrained prospect reading Heed as a build. Every other mechanic still waits to be asked about.

**Every figure needs a spoken-out-loud rationale**, not just a citation. Confidence-flag anything triangulated: 🟢 hard data, 🟡 triangulated estimate, 🔴 assumption.

---

## Change log

| Date | Change |
|---|---|
| 2026-07-29 | Created. Collapsed the two-axis frame to one axis with retroactivity as consequence. Split invisible-behavior claim into primary (aborted/partial actions) and secondary (genuine absences). Added FullStory carve-out. Corrected the "no rules" claim. Retired `Product_Posture.md`. Flagged pricing as blocking. |
| 2026-08-04 | Category set to **intelligent behavioral intervention** (supersedes "behavioral control layer"). Pricing resolved to **$3–5K per engagement**. Wedge clarified: pre-first-bet VIP capture is in scope; post-funding retention is not. |
| 2026-08-08 | §10 cost-of-first counter rewritten onto Phase 1 (collection only, free or nominal, changes nothing). §11: the in-session rule added — *in-session* may not appear without the no-event clause in the same sentence, with five banned constructions and two compliant examples. **Pending §9, §5 and the category name:** all three still assume Heed renders, retired at `09` §18. |
| 2026-08-08 | §10: four objection entries added — the feature read, build-vs-buy, "we'd rather not be first," and comparative deferral as an objection class. §11: feature register banned, "coverage gap in the event stream" approved, and a named carve-out to the mechanics-second rule for integration effort. |
