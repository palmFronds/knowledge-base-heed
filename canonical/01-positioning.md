# Heed — Canonical Positioning

**Status:** Canonical. This file is authoritative on positioning, competitive framing, and approved language.
**Last reviewed:** 2026-07-29
**Owner:** Dheeraj

**Supersedes entirely:**
- `Product_Posture.md` (Parallax-era). Retired in full — retired positioning, retired ICP, and an architecture description (sandboxed iframe / postMessage) that does not match what shipped.
- The positioning and competitive sections of both regulatory reports (§4, §5, §7 in each).
- The "The Problem" and "What Heed Does" sections of the Pilot Brief.

**Does not supersede:**
- The regulatory reports' legal analysis (§1, §2, §3, §9) — still current, still needs counsel review per Appendix A.
- `Product_Spec.md` / `Pilot_Specs.txt` engineering detail — these need their own consolidation, separately, into one spec.

**Unresolved and blocking:** pricing. See §8.

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

**Primary — aborted and partial physical actions.** Touch-hold-release without completing the tap. A cursor settling on Confirm for eleven seconds. Scroll reversal back to the fee row and then back down. Field focus with no entry. These are not absences: they are positive, present, continuously-structured behaviors that the browser emits and that no analytics ontology has a name for. There is no timeout that catches them, because nothing is pending — nothing started. This is the ground to fight on.

**Secondary — genuine absences.** `swap_started` fires; `swap_completed` never does. A competent CRM team **can** detect this with a timeout, and a sharp prospect will say so. What it requires is having predicted in advance which absence matters and how long to wait, which is the pre-declaration problem again rather than an impossibility. Use this as a supporting beat. Never as the headline.

## 4. Retired framings — do not use

**Latency / speed.** "Faster than competitors," "we act in the moment they act minutes later," "we fill the latency gap." This is a straw man. Optimove's real-time triggering is real, and any prospect who has been sold by them will know it. The correct argument is that an event-driven pipeline can be infinitely fast and still have nothing to act on when a user pauses or reverses scroll.

*Live instances still in circulation:* Regulatory Report §7 ("fills the latency gap between user hesitation and operator response") and the Pilot Brief's problem statement ("fires five to thirty minutes after a player has gone cold"). Both must be rewritten before the next prospect touchpoint. A prospect who read the brief will bring the retired version into the call.

**"The absence of rules entirely."** Currently in the Pilot Brief. It is not true and it is cheap to knock down — the config layer is thresholds and per-intent response mappings, which are rules, authored in advance, by the operator.

The precise and stronger version: **detection is rule-free; response is deliberately and entirely rule-based.** The response side is pre-declared on purpose, because pre-approved operator-authored copy is exactly what makes the product approvable by a compliance team. Conflating the two halves concedes a point that should never be available.

**Demo beat discipline.** Any copy that references *when* something fired rather than *what it could observe* has reverted to the latency straw man. This applies to HUD labels, deck copy, and LinkedIn artifact captions.

## 5. Competitive framing

The kill line differs by category, and knowing which axis is load-bearing per objection is what keeps the frame stable under pressure.

| Category | Examples | The claim that separates us |
|---|---|---|
| CRM / lifecycle | Optimove, Fast Track, Braze, Iterable | Input model. There is no event for a behavior nobody named, and no event for a user who hasn't done anything. Their real-time capability is real and irrelevant to this. |
| CDP | Segment, Tealium, mParticle | Input model, plus architecture: the value proposition is a persistent cross-tool profile, which is the opposite of an ephemeral single-session signal. |
| Product analytics (event-based) | Mixpanel, Amplitude, PostHog | Input model, plus no classification layer and no response mechanism — a human reads a chart and briefs an engineer. |
| **Session replay** | **FullStory, Hotjar** | **Input model does NOT separate us.** See below. |
| Experimentation / flags | LaunchDarkly, Statsig | No behavioral substrate at all. Static targeting rules evaluated at page load, resolved before the session begins. |
| Fraud / risk / RG scoring | — | Cold-start. A first-time depositor has no history, which is exactly the population these models are weakest on and exactly where onboarding abandonment is highest. Also answers a different question entirely. |

**The FullStory carve-out — hold this in reserve.** Session replay *does* capture raw substrate. It is the one category where the input-model claim does not separate us, and leading with "we see raw behavior" in front of an operator who owns FullStory gets "we already have that." Against session replay the separating claim is entirely on the action side: capture is for retrospective human review, with no intent classification and no in-session response path, and with a materially heavier privacy footprint than Heed's geometry-and-timing-only payloads. Do not open with this; deploy it when replay comes up.

## 6. Supporting evidence

**Betting Hero.** A paid human-concierge activation vendor used by major sportsbooks. Operators running full analytics and CRM stacks concluded their own software could not intervene at the hesitation moment and started paying humans to stand in bars instead. This indicts the incumbent stack using the incumbents' own customers' spending as proof, which is why it lands harder than any feature comparison. Operator-side intel via Scott Miller (former Betting Hero, since departed) on the reg→FTD friction lane.

## 7. ICP and wedge

**Wedge:** the registration → KYC → first funded action lane, specifically. Highest abandonment, lowest regulatory sensitivity (no wagering or promotional logic in scope), cleanest before/after measurement because a completed first funded action is binary.

**Deprioritized:** mid-session monetization triggering. Carries UKGC/RG regulatory tail risk and puts the product on the wrong side of the safety-vs-monetization line during the period when its thresholds are least proven.

**Verticals:** iGaming (Tier 1 ICP), DeFi on-ramps (parallel), prediction markets (emerging third).

**Regulatory tiering changes the pitch.** UKGC/MGA-licensed operators respond to the compliance-native framing; offshore operators do not weight it the same way. Match the framing to the operator's own regulatory bar rather than leading with compliance universally.

## 8. Pricing — UNRESOLVED

Two figures are currently in circulation and they contradict each other:

- Deck script: **$5–8K / month**, pilot tier
- One-pager: **$3–5K per engagement**

These are not reconcilable as-written — one is a recurring rate and one is a fixed scope. Any prospect who sees both documents will notice. **Resolve to a single number and structure, record it here, then correct both source documents.** This is blocking on the next prospect touchpoint, not on the next fundraise.

## 9. Architectural constraints referenced by positioning

Stated here only because the positioning depends on them being true. Full treatment lives in the regulatory report.

Heed produces a signal and a confidence score; the operator's pre-approved configuration decides whether and how to respond, using copy the operator's own compliance team authored. Heed never captures document contents, credentials, or sensitive field values; never modifies a regulated decision; never generates or prices an offer autonomously; and never overrides a responsible-gambling control under any partner configuration. RG suppression always wins over Heed's own signal, with no configuration path to disable that.

The load-bearing sentence for compliance reviewers: *"Heed identifies friction. The operator determines whether and how to assist the customer."*

## 10. Objection handling

**"We already have real-time — Optimove does this."**
Concede the speed point immediately; it is true and defending against it costs credibility. Then reframe to input: a pipeline can be infinitely fast and still have nothing to act on when a user pauses, holds a tap without releasing it, or scrolls back to re-read a fee row. Ask which event in their schema fires on that.

**"Then why can't Optimove just add a hesitation listener?"**
Mechanically they can — a client-side script emitting `user_hesitated` is not hard. Be honest about this. What it requires is deciding what hesitation *means*, per screen, in advance, as a threshold — which reintroduces the pre-declaration problem and lands them back in the discovery loop they were trying to exit. Note clearly: this is a *why-they-haven't* answer, not a moat. Do not present it as one.

**"So what's the actual moat?"**
Not the insight. The learned per-partner weights accumulated against a specific flow, and a client-side inference architecture that an existing CRM or CDP cannot retrofit without giving up the persistent cross-source profile that makes their product recognizable to their own customers.

**"We already have FullStory."**
See §5 carve-out. Move to the action axis, not the input axis.

**"This is behavioral manipulation / dark patterns."**
The rendering mechanism carries no manufactured urgency, no fake countdowns, no pre-selected options, no asymmetric decline path. Response copy is authored and approved by the operator's own compliance function, not by Heed. Scope is onboarding and first funding, not wagering.

## 11. Approved and banned language

**Use:** behavioral substrate; input model; pre-declared vocabulary; observes behavior rather than named events; behavioral control layer; signal, not decision; operator retains authority over every regulated outcome.

**Avoid:** faster than / real-time as the differentiator; latency gap; no rules at all; AI decision engine; another CRM; personalization engine; anything asserting *when* a signal fired as the point of comparison.

**Top-line framing rule:** lead with operator outcomes (measurable lift in FTD conversion), and keep product mechanics out of top-line descriptions in both prospect-facing and investor-facing material. Mechanics are the second question, never the first sentence.

**Every figure needs a spoken-out-loud rationale**, not just a citation. Confidence-flag anything triangulated: 🟢 hard data, 🟡 triangulated estimate, 🔴 assumption.

---

## Change log

| Date | Change |
|---|---|
| 2026-07-29 | Created. Collapsed the two-axis frame to one axis with retroactivity as consequence. Split invisible-behavior claim into primary (aborted/partial actions) and secondary (genuine absences). Added FullStory carve-out. Corrected the "no rules" claim. Retired `Product_Posture.md`. Flagged pricing as blocking. |
