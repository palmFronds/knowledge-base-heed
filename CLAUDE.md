# CLAUDE.md — Operating instructions for the Heed knowledge base

Read this before touching any file in this set.

## What this is

Ten canonical files describing Heed as of 30 July 2026. This is not a document archive — it is the single source of truth from which applications, decks, prospect reports, and outbound are generated. If a fact is not in here, it has not been checked. If it is in here and wrong, everything downstream is wrong.

## The governing constraint

**This knowledge base must be cheaper to update than to work around.** The failure mode is not inaccuracy — it is ceremony. A maintenance protocol heavy enough that Dheeraj sends a message instead of updating a file produces a KB that is quietly stale by September, at which point the real knowledge lives in chat threads again and this set actively misleads.

Every rule below is written to keep the cost of capture near zero and push the cost of curation into batches.

---

## Capture — near-zero friction

New facts land in `INBOX.md`. Append-only, no format, no thinking required. A line, a paste, a half-sentence. Nobody promotes anything at capture time.

```
2026-08-03  Pascal call — they use Braze, not Optimove. Growth lead is [name].
2026-08-03  PrizePicks went quiet after CEO intro, 3 wks no reply
2026-08-04  Brazil license count now 91? saw a number somewhere, unverified
```

That is the whole capture protocol. Uncertainty is welcome in the inbox — "unverified" is a valid entry and better than a fact that never gets written down.

## Curation — batched, deliberate

Sweep the inbox on demand or roughly weekly. For each item, classify it into one of four change types. **The class determines the ceremony, and most items are class 1.**

### Class 1 — Append
A new fact that conflicts with nothing. New target account, new call outcome, a test count going up.

Claude does this without asking. Write it into the owning file, delete the inbox line, note it in `CHANGELOG.md`. No discussion.

### Class 2 — Correct
An existing fact was wrong or has gone stale. A date, a headcount, a valuation, a bundle size.

Claude does this without asking **when the correction is mechanical** — a number replacing a number, a date replacing a date, from a source Dheeraj supplied. Fix in place, log it, move on. If a "correction" changes what the fact *means* or what it implies strategically, it is Class 3, not Class 2.

### Class 3 — Supersede
A position changed. The old version was reasonable and is now wrong.

This is the one with real ceremony, and it is the reason the set works. Never delete the old position. Move it to `09-retired-positions.md` with three things: what it said, why it lost, and what replaced it. Update the canonical file. Log it.

The "why it lost" is not optional and is not a formality — it is the only thing that stops a retired argument returning six months later when someone reconstructs the reasoning that originally produced it. The latency argument has already come back three times.

### Class 4 — Flag
Two sources disagree and Claude cannot tell which is right.

**Claude never resolves this alone.** Add it to the open-questions block at the bottom of `09-retired-positions.md`, mark the affected claim in `08-claims-register.md` with a ⚠️, and surface it. Averaging two conflicting positions into one smooth sentence is the single most destructive thing that can happen to this set — it produces text that reads confidently and is nobody's actual position.

---

## Fact ownership — one home per fact

The set currently carries deliberate redundancy, and redundancy is where drift starts. Each fact class has exactly one owning file. Other files reference it; they do not restate it.

| Fact class | Owner |
|---|---|
| The core argument, one-axis frame, why-now | `01-positioning.md` |
| Build state, test counts, architecture, what's not built | `02-product-and-architecture.md` |
| Named accounts, tiering, outbound learnings | `03-market-and-icp.md` |
| Competitor mechanism claims | `04-competitive-landscape.md` |
| Legal classification, constraints, open legal questions | `05-regulatory-posture.md` |
| Pricing, pilot structure, KPIs, commercial framing | `06-commercial-and-pilot-structure.md` |
| Team, entity, visa, applications, traction narrative | `07-company-team-and-status.md` |
| Every externally-usable claim + confidence flag | `08-claims-register.md` |
| Dead positions and why they died | `09-retired-positions.md` |

All canonical files live in `canonical/` under these numbered names. Two known overlaps, resolved:

- **Traction** appears in `07-company-team-and-status.md` and `08-claims-register.md`. `07` owns the narrative version. `08` owns the boundary of what may be said out loud. Change both together, always.
- **Pricing** appears in `06-commercial-and-pilot-structure.md` and `09-retired-positions.md`. `06` owns it. `09` only records that it is unresolved and points at `06`.

When a fact changes, check whether it appears in more than one file before editing. If it does and it should not, collapse it and note the collapse.

---

## Blast radius — what a change invalidates

A canon change silently invalidates downstream artifacts. After any Class 2, 3, or 4 change, state which of these are now stale:

- Pitch deck and deck script
- One-pager
- Expanded regulatory report
- Pilot brief
- Ember-style prospect reports (template)
- Apollo sequence copy
- Live accelerator applications already submitted

Known high-radius items: **pricing** invalidates deck + one-pager. **Positioning** invalidates all six. **Pilot status** invalidates the regulatory report and any submitted application.

Do not silently fix the downstream artifacts. Name them and let Dheeraj decide what gets regenerated.

---

## Verification decay

Regulatory and market facts rot faster than product facts. Anything in `05-regulatory-posture.md` or the market claims in `08-claims-register.md` older than 90 days drops from 🟢 to 🟡 automatically and needs re-checking before external use. Product claims in `02-product-and-architecture.md` do not decay — they are verifiable by running the test suite.

Specifically watch: GENIUS implementation dates, Brazil license counts, competitor valuations, prediction-market legal status by state, and sweepstakes enforcement.

---

## Knowledge out — which files for which artifact

Mobility runs both directions. Producing anything from this set:

| Output | Read |
|---|---|
| Accelerator application | `01-positioning.md`, `07-company-team-and-status.md`, `08-claims-register.md` |
| Investor deck or memo | `01-positioning.md`, `03-market-and-icp.md`, `04-competitive-landscape.md`, `08-claims-register.md` |
| Cold outreach / sequence copy | `01-positioning.md`, `03-market-and-icp.md`, `04-competitive-landscape.md` |
| Prospect walkthrough report | `01-positioning.md`, `04-competitive-landscape.md`, `05-regulatory-posture.md`, `06-commercial-and-pilot-structure.md` |
| Compliance questionnaire / security review | `02-product-and-architecture.md`, `05-regulatory-posture.md` |
| Pilot scoping conversation | `02-product-and-architecture.md`, `06-commercial-and-pilot-structure.md` |
| Anything at all with a number in it | `08-claims-register.md`, always |

`08-claims-register.md` is non-optional for any external artifact. If a claim is not in the register, it has not been checked — either check it and add it, or cut it.

---

## Non-negotiables when writing from this set

**Never argue speed.** The differentiator is the input model. Any sentence about *when* something fires rather than *what could be observed* has reverted to a retired position.

**Never claim a signed pilot, LOI, revenue, or design partner commitment.** There are none. Four named conversations, nothing more.

**Never claim behavioral data sits outside personal-data scope.** It is personal data the moment it can be tied to a session or device.

**Never claim cross-partner training as a moat.** Per-partner weight isolation is an architectural rule.

**Never lead with mechanics.** Operator outcomes first. Architecture answers the second question.

**Never assert a prospect's drop-off numbers.** Frame as where Heed would expect to create value.

**Keep the copy-ownership clause attached to any intervention claim.** "We fire the response" alone becomes "you originate the inducement" by the time it reaches a compliance team.

**Every number needs a spoken defense**, not a citation. If it cannot be justified out loud in a meeting, it does not go in an artifact.

---

## Interaction rules for Claude

**Batch questions.** Do not interrupt per-item during an inbox sweep. Process everything, then surface all Class 3 and Class 4 items together in one list. Interruption is what makes maintenance feel expensive.

**Act on Class 1 and mechanical Class 2 without asking.** Asking permission to update a test count is friction with no upside.

**Never smooth over a conflict.** When two things disagree, both survive until Dheeraj adjudicates.

**Never invent to fill a gap.** Write `**GAP:**` inline and add it to open questions.

**When asked to produce an external artifact, check `08-claims-register.md` before writing, not after.** Retrofitting confidence flags onto finished copy is how unsupported numbers survive.

**If a request would require breaking a non-negotiable, say so before drafting** rather than drafting a compliant version and mentioning the conflict at the end.

---

## Session end

One line, when anything changed: append to `CHANGELOG.md` as `YYYY-MM-DD · class · file · what changed · what it invalidates`. That is the whole ritual. If the changelog entry feels like work, the change was probably Class 3 and deserved it.
