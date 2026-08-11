# CLAUDE.md — Operating instructions for the Heed knowledge base

Read this before touching any file in this set.

## What this is

The canonical files in `canonical/` describe Heed as of 30 July 2026. This is not a document archive — it is the single source of truth from which applications, decks, prospect reports, and outbound are generated. If a fact is not in here, it has not been checked. If it is in here and wrong, everything downstream is wrong.

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

### Raw source — calls, transcripts, notes

Transcripts do not go in the inbox. They go in `sources/`, which is gitignored and never committed. The convention travels with the repo; the content does not.

Two acts, nothing else.

**Save the file** in whatever form it arrived — a Fireflies or Otter export, a Zoom `.vtt`, a `.docx`, a paragraph typed from memory. Any extension, no conversion, no cleanup, no header. Name it `YYYY-MM-DD-account.ext`:

```
sources/2026-08-03-pascal.vtt
sources/2026-08-03-banxa-notes.txt
```

That filename is the entire required metadata. Contact, channel, and status are either already inside the file or are Claude's job at sweep.

**Then one line in `INBOX.md`** — a pointer, never the transcript body:

```
2026-08-03  Call: Pascal — sources/2026-08-03-pascal.vtt
2026-08-03  Call: Pascal — growth lead, they run Braze, funnel is weeks — sources/2026-08-03-pascal.vtt
```

Both are complete entries. The gist is optional and earns its ten seconds for one reason: the transcript is not committed and the inbox line is. If the file is ever lost, the gist is what survives.

**A transcript is provenance, never a citation.** Canon must stand without it. No claim in `08-claims-register.md` may have "see the transcript" as its spoken defense.

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

### Sweeping a transcript

Claude reads the file, extracts atomic facts, routes each to its owning file, deletes the inbox line, and stamps the top of the transcript: `swept 2026-08-05 → 03, 08`. No stamp means unswept. Transcripts are kept indefinitely; sweeping never deletes one.

**A call that changes nothing is a normal outcome.** Stamp it `swept 2026-08-05 → no change` and stop. No changelog entry. Do not manufacture a fact to justify the read.

**Never lift phrasing.** Extract the fact, rewrite it in canon's voice. A transcript is a verbatim record of Heed speaking under time pressure, which is the exact condition under which the retired latency argument has already come back three times — `09-retired-positions.md` §1. The transcript pile is the highest-density source of retired language in the corpus.

**Attribute what a prospect asserted, and enter it at 🔴.** A prospect describing their own stack, funnel, or numbers is one uncorroborated interested party. Under the register's legend that is 🔴, not 🟡 — 🟡 means triangulated. It lifts to 🟡 only when a second independent source says the same thing, and two operators saying the same thing about the market is exactly that. Check for that lift on every sweep; it is the cheapest confidence upgrade available. Write "Pascal's growth lead says their funnel runs weeks," never "Pascal's funnel runs weeks."

**A prospect contradicting canon is Class 4, not Class 2.** One assertion from an interested party does not correct a checked fact, however mechanical the swap looks.

**A transcript fact enters `08-claims-register.md` only if Heed would say it out loud to a third party.** Everything else lives in its owning file with an inline attribution. The register is the pre-flight check for external artifacts; a call log inside it destroys that.

**Ceilings key off who is speaking, not off the call.** Counsel does not raise a regulatory claim above the ceilings already set in `05-regulatory-posture.md` and `08-claims-register.md` — research, never clearance.

**Drop-off numbers are governed by provenance, not by subject matter.** Carve-out decided 8 Aug 2026.

**A figure a prospect asserted** — on a call, in an email, in a deck they showed you — never becomes a Heed claim and never appears in a report written for that prospect. Repeating their number back reads as "we know your funnel," which is the posture `03-market-and-icp.md` and `06-commercial-and-pilot-structure.md` forbid.

**Data Heed measured itself, under agreement, on that partner's own funnel** is different and is permitted in a report to that partner. That is what a Phase 1 written read is (`06-commercial-and-pilot-structure.md`), and it is the only source for the abandonment-cost denominator (`09-retired-positions.md`).

The two never mix inside one sentence, and measured data stays with the partner it was measured on — it does not become a market claim, a benchmark, or a number quoted to a second prospect without its own decision. Named-partner facts also inherit the confidentiality question already flagged in `07-company-team-and-status.md` and `09-retired-positions.md`.

**Heed's own words on the call are facts too.** If the rep argued speed, claimed a pilot, quoted a price, or promised a deliverable, surface it. A quoted price is Class 3 while pricing is unresolved — see `06-commercial-and-pilot-structure.md`. A recurring delivery pattern belongs in `07-company-team-and-status.md` under known personal patterns.

**Names stay in the transcript.** Canon uses role-at-company — "Pascal's growth lead" — because canon is what external artifacts are generated from, and a name in canon leaks into a deck. The exception is when the name is the operative fact: `03-market-and-icp.md` names the Novig contact because the decline and the do-not-re-approach window attach to that person, not to the company.

**Follow-ups are not knowledge.** Next steps and reminders go in Apollo. This set holds what is true.

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
- **Pipeline roster** appears in `03-market-and-icp.md`, `07-company-team-and-status.md`, and `08-claims-register.md`. `03` owns per-account status and tiering, `07` owns the traction narrative, `08` owns whether the roster may be stated out loud and to whom. A call that moves an account changes all three. Change them together, always.

When a fact changes, check whether it appears in more than one file before editing. If it does and it should not, collapse it and note the collapse.

Raw source in `sources/` is not canon. It is never quoted and never counted as a file in this table.

## What else lives in this repo — the direction-of-dependency test

Decided 9 Aug 2026. Not everything generated in this project belongs here, and "case-by-case" is not a rule unless the case is written down. One test, applied to any non-canonical document:

**Which way does the dependency run?**

- **Canon depends on it → in-repo, under `artifacts/`.** If a canonical file cites the document as the answer to a question canon raises, the document is load-bearing for canon and has to be versioned beside it. `artifacts/retention-policy.md` is the first: `05-regulatory-posture.md` points at it for what is stored and for how long, so `05` is incomplete without it. **It stays.**
- **It is generated from canon → outside the repo.** Decks, one-pagers, pilot briefs, prospect reports, site copy, sequence copy. Canon does not cite them; they consume canon. Keeping them here creates a second place where a claim lives and a second place for it to go stale, which is the failure this whole set exists to prevent.

**The test in one line: if deleting the document would leave a canonical file with an unanswered question, it lives here. If deleting it would only mean regenerating it, it does not.**

Applied to what exists today: `artifacts/retention-policy.md` is in. `refactor/website-copy.md` is out — it is site copy, canon does not depend on it, and it should live wherever the site does.

Two things this test does not license. A document in `artifacts/` is still not canon: it does not appear in the ownership table, it is not a source of truth, and where it and a canonical file disagree the canonical file wins. And an in-repo document is not exempt from the blast-radius rule — when canon changes underneath it, name it stale like any other artifact.

## `refactor/` — correcting an external artifact against canon

A third directory, with one job: hold a live external artifact still while it is checked against canon. Files land here temporarily; they are not canon and they are not `artifacts/`.

**`refactor/` is gitignored, like `sources/`.** The convention travels with the repo; the content does not. Both the source and its `_mod` output stay local — the direction-of-dependency test above already ruled that canon does not depend on them, and committing them would create the second place for a claim to go stale that the test exists to prevent. The `_mod` file is delivered to wherever the artifact actually lives, not versioned here.

**Any file in `refactor/` is read-only input.** Generate `{name}_mod.{ext}` alongside it. Never edit the original. The original is the record of what was actually shipped, and the diff between the two is the whole value of the exercise.

**Preserve the source's structure and approximate length, section by section.** This is a correctness pass, not a rewrite. A section that was three lines comes back three lines. Headings, order, and shape stay unless canon requires otherwise. The output has to be droppable into whatever produced the original — a mod file half the length of its source is a new artifact wearing the old one's name, and someone has to rebuild the page around it.

**Where a canon-required correction cannot fit the source's length, note the delta inline** rather than overflowing silently. A one-line claim that needs three lines to state honestly is information about the artifact: it means the original was compressed past what canon supports, and that is worth surfacing rather than absorbing.

**Where canon is silent on something the source asserts, leave it and flag it.** Absence of canon is neither permission to invent nor grounds to delete. A domain name, a video, a design choice, a phrase nobody has ruled on — it stays, and it goes in the report. Deleting it because it is unverified would strip the artifact of everything canon has not yet reached, which is most of what makes it a page rather than a claims list.

**Report at the end**, in three parts: sections where length was preserved by substituting canon-supported material, sections where a delta was unavoidable, and everything canon neither supports nor forbids.

Call outcomes have no file of their own and do not get one. Account status goes to `03-market-and-icp.md`, a pricing reaction to `06-commercial-and-pilot-structure.md`, a competitor mechanism claim to `04-competitive-landscape.md`, a compliance objection to `05-regulatory-posture.md`. If something from a call fits nowhere, that is a `**GAP:**`, not a tenth canonical file.

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

Facts sourced from a call carry the call date inline — "as of the 3 Aug 2026 call." An operator's stack, funnel shape, and roadmap move faster than regulation: Underdog's March 2026 layoffs changed its account profile inside a quarter. The inline date is the decay signal. No separate rule.

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

**Do not read transcripts while producing an artifact.** Transcripts are read at sweep and nowhere else. Anything worth using is already in canon; if it is not there, it did not survive the sweep, and that was a decision. Treating `sources/` as a searchable second canon is how this set acquires a shadow copy of itself.

---

## Session end

One line, when anything changed: append to `CHANGELOG.md` as `YYYY-MM-DD · class · file · what changed · what it invalidates`. That is the whole ritual. If the changelog entry feels like work, the change was probably Class 3 and deserved it.

A transcript sweep logs one line per canonical file changed, with the transcript path inside the "what changed" field so provenance survives the file itself.

```
2026-08-05 · 1 · canonical/03-market-and-icp.md · Pascal moved from cold target to active conversation after the 3 Aug call (sources/2026-08-03-pascal.vtt). Braze confirmed, funnel-in-weeks attributed to their growth lead. · Invalidates: nothing
```
