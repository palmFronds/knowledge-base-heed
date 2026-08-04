# 04 — Competitive Landscape

The right answer to "don't we already have something like this?" is that operators own excellent tools in five adjacent categories and none of them can do this — not because of a feature gap a future release closes, but because of a structural mismatch between what each category's architecture was built to do and what in-session substrate inference requires.

Argue mechanism, never speed.

## CRM and lifecycle platforms

*Optimove, Fast Track, Braze, Iterable.*

**Mechanism.** Ingest events, update a stored customer profile — recency, frequency, monetary value, lifecycle stage, segment membership. Campaigns trigger off rules evaluated against that stored profile, or off an event completing. The architecture assumes the event you care about has already happened and been recorded before any decision logic runs.

**Why it structurally cannot do this.** A CRM has no concept of "a user is mid-action and has not yet decided." Its unit of work is a completed, logged event, not an in-progress interaction state. There is no webhook for "user is currently hesitating," so an eleven-second pause before a button press is invisible regardless of how fast the pipeline is. What the CRM sends next is a win-back campaign, which is a different and much lower-converting intervention than a message shown during the hesitation itself.

**Do not claim these tools are slow.** Optimove has genuine real-time triggering. The claim is that real-time triggering on an empty input is still nothing to fire on.

## Product analytics

*Mixpanel, FullStory, Amplitude, PostHog.*

**Mechanism.** Instrument a page to capture a rich event stream — clicks, page views, form interactions, and in FullStory's case full session replay — and store it for analysts to query after the fact. "Real-time" here means a human can see an event within seconds, not that the platform acts.

**Why it structurally cannot do this.** Built around a human-in-the-loop workflow: capture broadly, let a person look later, let that person decide what to build. There is no intent-classification layer and no response-firing mechanism in the product at all. A PM who spots a drop-off at the fee screen still has to brief an engineer, ship a fix, and wait weeks — which is the lag Heed removes.

Note on session replay specifically: capturing everything a user does, potentially including form content and full-page visuals, is a *heavier* privacy footprint than Heed's, not a lighter one. State this carefully — the specific claim about any named vendor's current practice should be checked against their public statements before appearing in a deck.

## Experimentation and feature flagging

*LaunchDarkly, Statsig.*

**Mechanism.** Evaluate pre-defined rules or randomised assignment at page load or a code checkpoint to decide which pre-built variant a user sees. The job is treatment assignment among human-authored options, using targeting rules configured in advance.

**Why it structurally cannot do this.** There is no behavioral-inference substrate at all. A feature flag evaluates static attributes — user ID, cohort, random bucket — that exist before the session starts. It answers "which version of this screen does this user get," never "is this user, right now, about to leave."

## Customer data platforms

*Segment, Tealium, mParticle.*

**Mechanism.** Identity resolution across devices and touchpoints, plus event orchestration routing a unified stream to downstream tools. Profile-centric and pipeline-based: data flows through server-side routing before reaching any destination.

**Why it structurally cannot do this.** The entire value proposition is a persistent cross-tool profile, which is architecturally the opposite of an ephemeral, minimal-data, single-session signal. Backend routing latency makes in-session response impossible by design. A CDP could theoretically run inference on the events flowing through it, but doing so requires exactly the persistent cross-source profile-building that creates the privacy exposure Heed's architecture avoids.

## Fraud, risk, and RG scoring

*Mindway AI, Neccton.*

**Mechanism.** Evaluate a user or transaction against historical models — prior transaction patterns, device and network fingerprinting, known fraud rings, accumulated play history. Statistical power comes from history.

**Why it structurally cannot do this.** An inherent cold-start problem sits exactly where Heed is strongest. A first-time depositor has no transaction history, no play pattern, often minimal device history — which is precisely the population where historical models are weakest and abandonment is highest. These systems also do not predict abandonment at all: a low fraud score says nothing about whether a legitimate user is about to give up on a confusing form. "Is this person a risk" and "is this person about to leave" are different questions answered by different data.

**The named vertical analogs.** Mindway AI (an Aarhus University spinout) and Neccton's Mentor run behavioral monitoring inside licensed gambling operators — deposit velocity, bet size, session length, micro-signal patterns — to flag problem-gambling risk before a player self-identifies. This is the closest thing to Heed operating in the same industry on the same class of signal, and it is the one place in this file where the mechanism argument has to be made carefully rather than structurally.

It still holds, and it holds on cold start specifically: every input those systems use is accumulated play history, which a user who has not yet made a first deposit does not have. They answer "is this established player at risk." Heed answers "is this new user about to leave." The populations barely overlap.

They matter for two reasons that are not competitive. They are existence proof that licensed operators will buy behavioral inference and carry it through compliance review — the objection Heed spends most of its time on. And they scaled by treating tightening RG mandates as a distribution channel rather than an obstacle. Whether Heed should lead the same way is an open decision, not a settled position — see `09-retired-positions.md`.

**Named but unassessed.** OptiKPI and Talon.One surface in adjacent-vendor discussion. Neither has been worked through on mechanism, so neither belongs in a pitch yet. `08-claims-register.md` prohibits claims about a specific competitor's architecture; a name is not a mechanism claim, and these are currently only names.

## Human concierge

*Betting Hero.*

**Mechanism.** Paid human representatives in physical venues, walking users through registration and first deposit by hand.

**Why it matters more than the others.** It is not a competitor to argue against; it is evidence for the argument. Operators with complete stacks concluded their software could not reach the hesitation moment and bought humans instead. And because it requires a retail venue in a legal state, it is unavailable to the entire set of operators Heed targets first.

## The one-line summary

Those systems explain what already happened, or route what already happened, or score what already happened. Heed observes what is happening — and the reason none of them can is that the thing it observes was never an event in their schema.
