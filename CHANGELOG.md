# CHANGELOG

Format: `YYYY-MM-DD · class · file · what changed · what it invalidates`

Classes: 1 append · 2 correct · 3 supersede · 4 flag

---

2026-07-30 · 3 · ALL · Initial canon established. Fourteen contradictions across prior document set resolved; see `09-retired-positions.md`. Invalidates: `Product_Posture.md`, `Product_Spec.md`, `Pilot_Specs.txt`, Pilot Brief PDF, expanded Regulatory Report as positioning sources.

2026-07-31 · — · canonical/01-positioning.md · Renamed from canonical/POSITIONING.md to conform to numbered-filename convention. Content unchanged. · Invalidates: nothing (path only)

2026-07-31 · 1 · canonical/02-product-and-architecture.md · Bulk-populated from inbox: integration surface, five-layer architecture, absolute architectural rules, current build state across four branches, deliberately-not-built list, reliability posture. · Invalidates: nothing (first population)

2026-07-31 · 1 · canonical/03-market-and-icp.md · Bulk-populated from inbox: qualifying filter, Tiers 1–5 with named accounts and statuses, channel plays, disqualified sweepstakes category, sequencing, outbound learnings. · Invalidates: nothing (first population)

2026-07-31 · 1 · canonical/04-competitive-landscape.md · Bulk-populated from inbox: mechanism-level breakdown of CRM/lifecycle, product analytics, experimentation, CDP, fraud/RG scoring, and human concierge categories. · Invalidates: nothing (first population)

2026-07-31 · 1 · canonical/05-regulatory-posture.md · Bulk-populated from inbox: classification, must-never architectural rules, RG posture, dark patterns, marketing/promotions, KYC/AML, procurement expectations, open counsel questions. · Invalidates: nothing (first population)

2026-07-31 · 1 · canonical/06-commercial-and-pilot-structure.md · Bulk-populated from inbox: sales posture, pilot shape and weekly structure, partner inputs/outputs, KPIs, unresolved pricing, post-pilot commercial options, framing discipline. · Invalidates: nothing (first population)

2026-07-31 · 1 · canonical/07-company-team-and-status.md · Bulk-populated from inbox: team, entity/visa structure, funding status, accelerator applications, traction narrative, tooling, personal patterns to correct. · Invalidates: nothing (first population)

2026-07-31 · 1 · canonical/08-claims-register.md · Bulk-populated from inbox: full claims register with confidence flags across product, market, competitive, regulatory, and company claims. · Invalidates: nothing (first population)

2026-07-31 · 1 · canonical/09-retired-positions.md · Bulk-populated from inbox: 14 pre-existing retired/demoted/corrected positions plus open-questions scaffold. · Invalidates: nothing (first population)

2026-08-10 · 1 · .gitignore, CLAUDE.md · `refactor/` gitignored alongside `sources/` — convention travels, content does not. Founder decision. Implements the direction-of-dependency test decided 9 Aug: canon does not depend on an artifact held there, so versioning it would create the second stale home the test exists to prevent. The `_mod` output is delivered to wherever the artifact lives. · Invalidates: nothing

2026-08-10 · 4 · canonical/09-retired-positions.md · Open question raised: the `response copy` field is still in the per-partner config schema after the 9 Aug dead-code pass that removed the overlay div and the dead log events on the same argument. The config file is what compliance inspects, so it is the worst place for the one surviving instance. Schema change not authorised. · Invalidates: nothing yet — but any security or compliance review that walks the config schema

2026-08-10 · 2 · canonical/05-regulatory-posture.md · Dark-patterns section finished against the 9 Aug overlay removal. "The overlay div still ships inert" withdrawn — it was directly contradicting `08-claims-register.md`'s 🟢 partner-DOM claim and telling the reader to say the weaker version. Two qualifications become one. · Invalidates: any compliance answer that hedged "Heed does not render" as a configuration fact

2026-08-10 · 2 · canonical/08-claims-register.md, canonical/09-retired-positions.md · The "do not say read-only" rule carried two reasons; the second (the div is injected at init) lapsed 9 Aug. Recorded as lapsed rather than deleted — the phrase stays retired on the first reason, which is sufficient. · Invalidates: nothing

2026-08-10 · 2 · canonical/06-commercial-and-pilot-structure.md · "The net, the overlay, the config" corrected to "the net, the emission, the config" in the outcomes-first rule. Last surviving instance of the overlay named as a Heed mechanic in canon. · Invalidates: nothing

2026-08-09 · 3 · canonical/02-product-and-architecture.md · Overlay div and the dead `response_fired`/`response_dismissed` event types removed. The absolute rule now reads "the partner DOM is untouched" with no exception clause — the SDK inserts no element into the page at all. Reason: dead code makes an architectural claim look configurational to a reviewer reading the source. · Invalidates: website copy, LinkedIn demo, any security answer describing an overlay

2026-08-09 · 1 · canonical/08-claims-register.md · New 🟢 — the partner DOM is untouched, no exception clause, architectural not configurational. · Invalidates: nothing

2026-08-09 · 2 · canonical/09-retired-positions.md · §14 reframed: "default example responses" was a Heed response catalogue; restated as examples of what an operator might fire. §6 and §7 annotations updated for full overlay removal. Overlay and dead-schema open items closed. · Invalidates: Ember template phrasing

2026-08-09 · 3 · CLAUDE.md · `refactor/` convention written in — read-only input, generate `{name}_mod.{ext}`, preserve structure and approximate length, note deltas inline, leave and flag what canon is silent on, report in three parts. · Invalidates: nothing

2026-08-09 · 1 · refactor/website-copy_mod.md · Corrected pass over live site copy against the 29-defect audit. ICP moved to licensed operators, demo rebuilt on the first-deposit fee row, gap loop redrawn terminating in the operator's rule engine, emit-only led with, two-tier roadmap replaced by Phase 1 free / Phase 2 by agreement. Original untouched. · Invalidates: nothing (the live site is already stale; this is the fix)

2026-08-09 · 2 · canonical/01-positioning.md · §3 and §10 corrected — "touch-hold-release without completing the tap" removed as a named observed behavior and replaced with "a finger resting on a button without pressing it." The four signal types in `02` are complete; the prose was wrong, not the product. · Invalidates: LinkedIn demo labelling, website copy ("dead taps"), any deck or call script using the abort example

2026-08-09 · 3 · canonical/01-positioning.md · Emit-only promoted from architecture to argument. "Heed never shows your users anything" added as the compliance conversation's shortest path. Event-parity register banned — the signal shares shape with their events so a rule engine can route it, and is never described as one of them. §4 rule-absence, §5 product-analytics row, and §10 dark-patterns objection rewritten off the retired render. · Invalidates: call script, deck, one-pager, website copy, Apollo sequence copy

2026-08-09 · 1 · canonical/06-commercial-and-pilot-structure.md · Joint attribution recorded as a renewal-conversation problem — when the operator renders, lift cannot be split, and the terms of evidence should be agreed during Phase 2 scoping rather than after a good quarter. Supports the flat-fee basis. · Invalidates: nothing external yet

2026-08-09 · 2 · canonical/04-competitive-landscape.md · CRM and product-analytics sections corrected — both argued a response mechanism Heed no longer has. Separation restated as delivery (dashboard versus rule engine), not firing. · Invalidates: deck competitive slide

2026-08-09 · 2 · canonical/02-product-and-architecture.md · Overlay rule tightened to call-sites-removed. LinkedIn demo Beat 5 recorded as requiring a rebuild — it renders an overlay that no longer exists; replacement close is the signal landing in the operator's lane. · Invalidates: LinkedIn demo

2026-08-09 · 3 · canonical/09-retired-positions.md · §21 added — the abort description corrected, with the note that it survived eleven days and three passes because it was never checked against the signal-type list. §6 and §7 annotated where their replacements have themselves been retired. §16 records that the category defense is now load-bearing and that this is the third name held against the same class of challenge. · Invalidates: nothing

2026-08-09 · 3 · CLAUDE.md · Direction-of-dependency test written in: canon depends on it → `artifacts/`; generated from canon → outside the repo. `artifacts/retention-policy.md` stays; `refactor/website-copy.md` goes. · Invalidates: nothing

2026-08-08 · 3 · canonical/02-product-and-architecture.md · Session-end aggregate stratified into completed and abandoned buckets, unblocking outcome comparison and co-occurrence while retaining no session. Percentile-mergeability defect recorded — durations must travel as a fixed-bin histogram, bin edges open. Overlay render call sites removed rather than config-gated, making "Heed does not render" architectural; test-count fallout recorded. · Invalidates: any quoted test count until the suite is green

2026-08-08 · 2 · canonical/08-claims-register.md · Outcome comparison and co-occurrence promoted to 🟢. Abandoned tap recorded ❌ as unevidenceable. Field-focus duration ⚠️ blocked pending Anthony. Duration figures marked provisional pending histogram bins. Test counts and verified-chain claim barred from quotation pending suite rebuild. · Invalidates: nothing new

2026-08-08 · 4 · canonical/09-retired-positions.md · Session-record and overlay-gating questions closed. Aborted tap opened as scoped-not-built, with the demo exposure stated for the first time — the LinkedIn demo runs on a signal Phase 1 cannot measure, and its mandatory Beat 5 renders an overlay that no longer exists. Reconciliation flagged: `02`'s four signal types versus the demo's verified touch chain. · Invalidates: LinkedIn demo, any artifact built on it

2026-08-08 · 1 · artifacts/retention-policy.md · Drafted against the Phase 1 architecture. Eight fields marked for founder decision; the session-identifier question decides whether the transmitted aggregate is personal data on arrival. First generated artifact kept in this repo — convention flagged, not settled. · Invalidates: nothing (new document)

2026-08-08 · 3 · canonical/05-regulatory-posture.md · RG suppression moved from architectural guarantee to partner warranty — both prior promises quoted and retired, residual failure mode (emit on a self-excluded player, operator's CRM fires promotional copy) stated plainly, three emission requirements recorded as canon. Classification set to processor scoped to Phase 1, with the purpose-vs-means challenge answered, the persistent-profile exposure addressed, and Phase 2 stated separately as not inheriting and unresolved. Dark-patterns exposure transferred to the operator with two qualifications. Marketing section updated — "we tell your CRM when to fire the bonus" named as the new form of the old error. · Invalidates: expanded regulatory report, pilot brief, any compliance answer given before 8 Aug

2026-08-08 · 3 · canonical/02-product-and-architecture.md · Response layer replaced by Emission (signal type, selector, confidence as separate fields; acknowledgment logged). Overlay ships inert, stated as "the render path exists and is not exercised." Session-end aggregate specified — count, mean, p50, p90, max per selector per signal type. "No database" recorded as fallen. Client-side rationale rewritten off latency onto data minimisation. · Invalidates: any security or engineering answer describing a response layer

2026-08-08 · 3 · canonical/06-commercial-and-pilot-structure.md · Phase 1 free, with the scoping-instrument rationale and a ban on trial/discount framing. Phase 2 basis set to flat per-month platform fee, figure open. Deployment target elected by the partner at scoping. Retention policy and RG warranty added as Phase 1 scoping items. Performance-based post-pilot option closed rather than deferred. · Invalidates: deck, one-pager, any quoted price

2026-08-08 · 3 · canonical/01-positioning.md · §9 rewritten onto emit-into-stack with RG as contractual. §5 CDP row and FullStory carve-out requalified — "ephemeral in our hands," and the geometry-and-timing payload phrasing corrected. §11 category name retained with a rehearsable one-sentence defense. · Invalidates: call script, deck, one-pager

2026-08-08 · 2 · canonical/04-competitive-landscape.md · CDP section requalified on ephemerality; the backend-routing-latency argument removed as a speed claim contradicting this file's own instruction. · Invalidates: nothing external

2026-08-08 · 2 · canonical/08-claims-register.md · Phase 1 free 🟢; Phase 2 figure ⚠️ unquotable. Phase 1 deliverable bounds rewritten on the decided payload — duration and per-screen density 🟢, sequence ❌, outcome comparison and co-occurrence ⚠️ pending the session-record question. · Invalidates: nothing not already listed

2026-08-08 · 3 · canonical/09-retired-positions.md · §16 category name challenged and retained, with the three-name pattern recorded so the next challenge is anticipated. Seven open questions closed; four opened. · Invalidates: nothing

2026-08-08 · 3 · canonical/06-commercial-and-pilot-structure.md · Pilot rebuilt on two phases. Phase 1: 3–4 weeks, collection only, no inference, nothing rendered, free or nominal, ending in a written read. Phase 2: conditional, emits a signal into the operator's stack. Partner inputs drop response copy and staging; deliverables drop the conversion delta and the intervention log; KPIs split, with no conversion KPI in Phase 1; measurement records that Heed can no longer compute an independent before-and-after. Fixed-window named deliverable adopted; its blocking conclusion retired with the reasoning kept live. · Invalidates: pilot brief, deck, one-pager, Ember template, regulatory report, any quoted price

2026-08-08 · 3 · canonical/09-retired-positions.md · Four retirements. §17 single-phase rendering pilot (resolves the 8 Aug read-only question; "read-only" retired as the phrase). §18 Heed renders the response — replaced by emit-into-the-operator's-stack; `02` and `05` flagged as still carrying it. §19 the no-named-deliverable conclusion retired, reasoning retained with its prediction recorded as correct. §20 "not behavioral data" narrowed for the Phase 1 aggregate payload. Denominator GAP closed against Phase 1's written read. Seven open questions opened. · Invalidates: all six downstream artifacts

2026-08-08 · 2 · canonical/08-claims-register.md · No-PII claim split — "no PII leaves the browser" survives 🟢, "only outbound call is a weight POST" flagged false. Verified-signal-chain claim ⚠️ as describing a retired terminus. Price entry ⚠️ with no quotable figure in either phase. Read-only entry replaced by a 🟢 Phase 1 claim plus a ⚠️ 🔴 bounding what the written read may contain. · Invalidates: deck, one-pager, any artifact quoting a pilot price

2026-08-08 · 3 · canonical/01-positioning.md · §10 cost-of-first counter rewritten onto Phase 1. §11 in-session rule added with five banned constructions and two compliant examples. · Invalidates: Apollo sequence copy, call script, deck script, pilot brief

2026-08-08 · 1 · canonical/07-company-team-and-status.md · Delivery capacity set at two concurrent Phase 1 engagements as the prepared bandwidth answer. Decision authority recorded as unilateral, with personal-commitment and co-founder-build exposure stated. · Invalidates: nothing

2026-08-08 · 3 · CLAUDE.md · Drop-off rule re-cut on provenance: prospect-asserted figures still barred; data Heed measured under agreement on a partner's own funnel permitted in a report to that partner. Permits the Phase 1 deliverable and the denominator. · Invalidates: nothing

2026-08-08 · 1 · canonical/01-positioning.md · §10 gained four objection entries from the Jackpot.com deferral: the feature read, build-vs-buy pre-emption, "we'd rather not be first" with its two-part counter, and comparative deferral named as an objection class distinct from thesis and capability objections. §11 bans the feature register and approves "a coverage gap in the event stream." · Invalidates: nothing (additive)

2026-08-08 · 3 · canonical/01-positioning.md · §11 top-line framing rule gained a named carve-out: absence of integration effort is stated unprompted in compliance- and roadmap-sensitive calls, because absence of effort is itself the operator outcome. Narrows a non-negotiable ("never lead with mechanics") rather than retiring it, so no `09` entry. · Invalidates: Apollo sequence copy and call script if either withholds the no-integration line until asked

2026-08-08 · 2 · canonical/03-market-and-icp.md · Jackpot.com moved from active Tier 5 conversation to deferred to early 2027 (inbound email, 8 Aug 2026, post-discovery) with the three stated criteria recorded. Thesis not challenged. · Invalidates: any artifact stating four active conversations

2026-08-08 · 1 · canonical/06-commercial-and-pilot-structure.md · Sales posture gained the discovery rule that build-vs-buy and first-customer risk must be made speakable in discovery, plus the soft-close diagnostic. A read-only first phase producing a coverage-gap report recorded in the unadopted-options section with the conflict against the current Week 2/Week 3 shape stated. · Invalidates: nothing (nothing adopted)

2026-08-08 · 2 · canonical/07-company-team-and-status.md · Traction pipeline corrected to three active plus one deferred. Known personal patterns gained the asynchronous soft close — criteria that are new information when the deferral arrives mean discovery did not surface them. · Invalidates: submitted accelerator applications and deck stating four active conversations

2026-08-08 · 2 · canonical/08-claims-register.md · Company claims corrected to three active conversations; approved category-level pipeline phrasing added for confidentiality-constrained contexts; category de-risking claim added at 🔴 with its lift condition; ⚠️ added on the read-only-first-phase claim, which is banned from prospect conversation pending resolution. · Invalidates: deck, one-pager, submitted applications — pipeline count

2026-08-08 · 4 · canonical/09-retired-positions.md · Two open questions: whether the engagement has a read-only first phase delivering a coverage-gap report (conflicts with the adopted pilot shape and with the not-adopted named-deliverable pattern in `06`), and a GAP on the missing abandonment-cost denominator. · Invalidates: use of "read-only" or any promised report in prospect conversation until resolved

2026-08-04 · 1 · canonical/04-competitive-landscape.md · Mindway AI and Neccton named in the fraud/risk/RG section from the GTM case-study document (sources/2026-08-04-gtm-case-studies.md) — closest vertical analogs, cold-start argument holds against them, and they are existence proof that licensed operators buy behavioral inference. OptiKPI and Talon.One recorded as names without mechanism. · Invalidates: nothing

2026-08-04 · 1 · canonical/06-commercial-and-pilot-structure.md · Tighter pilot shape recorded as an unadopted option — fixed window with named deliverable, "alongside not instead of" framing, outcome risk carried by Heed. The guarantee is blocked behind unresolved pricing. · Invalidates: nothing (nothing adopted)

2026-08-04 · 1 · canonical/08-claims-register.md · Mindway scale figures added at 🔴, single-source. OptiKPI/Talon.One folded into the existing competitor-architecture prohibition. ⚠️ added on the contested category name. · Invalidates: nothing

2026-08-04 · 4 · canonical/09-retired-positions.md · Two open questions from the GTM document: which category name is current ("behavioral control layer" per 01 versus "real-time behavioral response infrastructure"), and whether RG becomes the growth lever. Recurrence log added to §2 — the retired axis reverted twice in two days, once spoken and once written. · Invalidates: any external use of a category name until resolved

2026-08-04 · 3 · canonical/01-positioning.md · Category set to **intelligent behavioral intervention** (supersedes "behavioral control layer"). Pricing resolved to **$3–5K per engagement**. Wedge clarified: pre-first-bet VIP capture in scope; post-funding retention out. · Invalidates: deck script ($5–8K/month), any artifact using old category names

2026-08-04 · 3 · canonical/06-commercial-and-pilot-structure.md · Pilot pricing settled at **$3–5K per engagement**; deck script monthly figure withdrawn. · Invalidates: deck script

2026-08-04 · 2 · canonical/03-market-and-icp.md · Brazil: 87 operators and ~180–200 brands recorded as different units. VIP asymmetry scoped — pre-first-bet capture in wedge, post-funding retention not. · Invalidates: nothing

2026-08-04 · 2 · canonical/07-company-team-and-status.md · Levi Bosshart confirmed as collaborator, not co-founder. · Invalidates: any application listing him as co-founder

2026-08-04 · 3 · canonical/08-claims-register.md · Category, pricing, and Brazil unit claims updated. Contested ⚠️ flags cleared. · Invalidates: deck, one-pager if category or pricing wrong

2026-08-04 · 3 · canonical/09-retired-positions.md · Resolved Aug 3–4 open questions: category (§16), pricing (§15), bonus-on-loss template (§14). RG-first and VIP-scope questions closed — conversion-first holds, wedge unchanged with pre-first-bet VIP nuance. · Invalidates: deck script, Ember template use case 2, any artifact with old category or pricing

2026-08-03 · 1 · canonical/03-market-and-icp.md · New "LATAM beyond Brazil" section from the 3 Aug Seccatore call (sources/2026-08-03-nicolas.md) — Argentina/Peru/Chile/Colombia structure, VIP asymmetry, the "keep it simple" objection, all attributed and 🔴. Brazil intro path added to Tier 4 barriers. One outbound learning added: ask for a critique, not interest. · Invalidates: nothing

2026-08-03 · 1 · canonical/07-company-team-and-status.md · Nicolas Seccatore added as a source (not advisor). Two delivery patterns added: the spoken pitch still opens on retired response-window language, and a sweepstakes operator was cited aloud as a worked example and described as one "we were working with." · Invalidates: nothing

2026-08-03 · 1 · canonical/08-claims-register.md · Colombia deposit-tax contraction added at 🔴, single-source. ⚠️ added on the Brazilian operator count pending reconciliation. · Invalidates: nothing

2026-08-03 · 4 · canonical/09-retired-positions.md · Two open questions raised by the 3 Aug call (sources/2026-08-03-nicolas.md): Brazilian operator-vs-brand count unreconciled against the 🟢 SECAP figure, and whether VIP identification enters scope. Neither resolved. · Invalidates: any external use of a Brazilian operator or brand count until resolved

2026-07-31 · 3 · canonical/09-retired-positions.md · Two-axis frame (input model + response window as co-equal axes) retired as item 2, superseded by the one-axis frame already established in `01-positioning.md`. Why it lost: a 2×2 concedes a legitimate quadrant to CRMs with genuine real-time triggering. · Invalidates: any deck, one-pager, or outbound copy using two-axis language ("Axis one is...", "Axis two is...", "the only occupant of substrate-capture plus in-session response").
