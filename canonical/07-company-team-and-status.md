# 07 — Company, Team, and Status

## Team

**Dheeraj Aaditya** — CEO. Purdue University. Owns positioning, pipeline, operator conversations, and commercial strategy. Indian national on an F1 visa, roughly one year from graduation as of mid-2026.

**Anthony Petrescu** — co-founder. Owns inference architecture and the SDK. Contact surface `apetresc@purdue.edu`.

**Levi Bosshart** — collaborator, not co-founder. Part-time top-of-funnel lead sourcing and CRM. He is an active founder at another company; represent as collaborator on applications and in diligence, not as a co-founder with over 10% equity. The bandwidth question should still have a prepared answer.

**Scott Miller** — former Betting Hero operator, no longer at the company. Yielded operator-side intel on the registration-to-FTD friction lane. Not an advisor; a source.

**Nicolas Seccatore** — LATAM iGaming B2B veteran based in Chile, reached by cold LinkedIn outreach, first call 3 Aug 2026. Supplier-side perspective across Brazil, Argentina, Peru, Chile, and Colombia. Has offered introductions to English-speaking Brazilian operators and a second call. Not an advisor; a source.

## Delivery capacity — the prepared bandwidth answer

**Two concurrent Phase 1 engagements, maximum.** Founder decision, 8 Aug 2026. This is the answer to the bandwidth question flagged above, not a target to beat.

The arithmetic is the team: Dheeraj is part-time by visa necessity, Anthony owns the inference architecture and the SDK alongside everything Phase 1 requires him to build, and Levi is a part-time collaborator who is an active founder elsewhere. A third concurrent engagement is not a stretch — it is a missed deliverable on a fixed three-to-four-week window that was promised in writing.

State the number if asked. Two slots on a fixed window is a constraint that is true, and a prospect who hears a real constraint hears a real company; an evasive answer to a bandwidth question from an operator who runs delivery teams costs more than the constraint does.

## Decision authority

**Dheeraj decides commercial commitments unilaterally.** Recorded 8 Aug 2026 as the operating reality rather than as an aspiration, with its exposure stated rather than left to be discovered:

- **Pre-incorporation, so commitments are personal, not entity-level.** There is no entity to enter a contract (see below), which means a Phase 1 agreed on a call is agreed by Dheeraj individually.
- **Anthony owns the build every Phase 1 depends on.** The inference architecture and the SDK are his, and so is the session-end payload change Phase 1 requires (`09-retired-positions.md` §20). A Phase 1 sold is a co-founder's engineering time committed by someone else.

Neither point argues against the authority. Both are why `06-commercial-and-pilot-structure.md`'s standing instruction — do not offer flexibility on commitments the prospect has not asked for — is load-bearing rather than stylistic, and why the retained reasoning at `09-retired-positions.md` §19 still has to be answered out loud each time.

## Entity status — pre-incorporation

Counsel engaged. Recommended structure: a **Delaware C-corp** with an **Indian LLP or partnership firm** holding Dheeraj's economic interest, so that the shareholding is clean while visa status is unresolved. Co-founders hold shares directly at the US level. Founder vesting is built onto the LLP itself.

The visa constraint operates across three roles. **Shareholder** is resolved by the LLP structure. **Employee** is prohibited by F1 terms — no W2, no salary, though CPT or OPT internship structuring is a possible narrow path. **Director** is potentially available as a nominee directorship and should be confirmed with an immigration attorney; if unavailable, control routes through the LLP nominating a director.

Contracts are entered by the entity, not the individual, with a co-founder signing as representative. A co-founder agreement between the co-founders and the LLP is essential, governed by Delaware law.

Counsel's US rate is $350/hour. An India subsidiary is a future consideration, not a current one, and would require a master services agreement and transfer pricing work when it happens.

**Application handling.** Where a form asks for number of full-time founders and defines founders as holders of over 10% equity with an instruction to enter 0 if not yet incorporated, enter 0 and list co-founders separately. Where a form asks full-time versus part-time, the accurate answer is part-time, because claiming full-time contradicts the visa posture and will not survive a follow-up question. Address the structure proactively in an additional-information field rather than letting it be discovered.

## Funding status

No investment taken. Verbal interest from several angels in the payments ecosystem, sourced through Purdue's venture network, plus early conversation with one VC firm. All interest is contingent on production pilot data. Nothing on paper.

Target: roughly $311K from a private US investor would open founder-parole and other visa paths.

## Accelerator applications

Active or in preparation: Y Combinator, Elbow Grease, gener8tor, a16z Speedrun. Prior applications to Z Fellows, AlchemistX, Draper, Techstars.

**a16z Speedrun specifics.** SR007 closed 17 May 2026 and is running now. SR008 runs late January through April 2027 in San Francisco, applications rolling, with the prior cycle's deadline pattern suggesting roughly late September 2026. Acceptance is under 0.4%. The standard deal is $500K for 10% on an upfront SAFE plus $500K in the next round. Pre-incorporation is explicitly acceptable — a16z has stated it is the sweet spot, and roughly a dozen of the last batch's seventy companies had not quit their jobs when they applied.

**The Speedrun blocker is not traction.** It is that the program requires twelve weeks in person in San Francisco from late January 2027, which lands inside spring semester. Resolve whether that is a leave of absence, a CPT arrangement, or a hard no *before* submitting, because it will be asked in interview and having no answer is worse than any traction gap.

**Recommended timing.** Draft now, submit in September with a signed pilot if one converts. Applications can be updated after submission, so an early submission plus a September update naming a partner is a defensible middle path.

**Disclosure consideration.** A prior YC application may exist. Check before answering any question about prior applications.

## Traction — state exactly this and nothing more

**Product.** SDK v1.0 shipped. 88/88 Vitest unit tests and 6/6 Playwright end-to-end tests passing. Full signal chain verified on a real mobile device. Demo harness complete, CRM blind-spot demo in development.

**Pipeline.** Active conversations with the CEO of PrizePicks, Head of Partner Integrations at Banxa, and ProphetX. Jackpot.com (Strategy & Data) reached discovery and deferred to early 2027 as of 8 Aug 2026 — it is a completed conversation, not an active one, and the traction narrative is now three active plus one deferred rather than four active (`03-market-and-icp.md`). 85 qualified accounts in outbound across iGaming and prediction markets, held in two Apollo lists.

**Revenue.** None. **Signed pilots.** None. **Design partner commitments.** None signed.

Earlier material claiming "design partner commitments secured" and "pilots underway with Banxa, Jackpot.com, and PrizePicks" is inaccurate and must not be repeated. Those are conversations. The regulatory report flags its own confidentiality concern about naming those partners externally at all — confirm before any document naming them leaves the company.

## Tooling

`heed-harness` repo, four branches, `CONTRACT.md` with seven locked selectors. Apollo.io for CRM and sequencing. Vitest and Playwright. `brain.js` for inference, weights trained offline in Node. LinkedIn company page at `linkedin.com/company/heedai/`.

## Known personal patterns to correct

In live calls: opening monologues running too long before the first question, filler phrases clustering under pressure before a close, talking past buying signals instead of letting silence work, and offering flexibility on commitments the prospect did not ask for.

In written outreach: asks that are always meeting-sized rather than answerable in a line, and openers that read as job-seeking rather than founder-to-operator.

**The soft close now shows up asynchronously.** Post-call deferral emails are the same weakness in written form. An objection that arrives after the call is an objection discovery did not make speakable during it — the Jackpot.com deferral of 8 Aug 2026 named three decision criteria that had not surfaced on the call at all. This is the same pattern as talking past buying signals, one step later in the sequence, and it is not visible in the moment because the call itself felt warm.

**In the spoken pitch: the retired frame is still what surfaces first.** On the 3 Aug 2026 LATAM call the opening description — given by Levi — ran on retired response-window language: "not afterwards, but while it's actually going on," "instead of only understanding drop-off after it happens," and "what we call a response window," which is the retired Axis Two verbatim (`09-retired-positions.md` §2). Dheeraj corrected onto the input model in the next turn and did it well, conceding real-time triggering explicitly. But the correction came second, in front of a source who went on to offer introductions. The opening is the part that gets remembered, and it is currently the part carrying retired language.

Also on that call: a sweepstakes operator was cited aloud as a worked example, and described as one "we were working with." `03-market-and-icp.md` explicitly disqualifies the sweepstakes category, and there are no working relationships of any kind. Both halves of that sentence need to stop.
