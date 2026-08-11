# 08 — Claims Register

Every claim usable in an application, deck, or prospect conversation, with a confidence flag and the defense to be spoken out loud. 🟢 hard data · 🟡 triangulated · 🔴 estimate

## Product claims

🟢 **SDK v1.0 shipped, 88/88 Vitest and 6/6 Playwright passing.** Defense: run the suite.

⚠️ 🟢 **Full signal chain verified on a real mobile device, both directions** — scroll reversal → `price_doubt` → `discount_offer`, touch hesitation → `confusion` → `tooltip`. **Both chains end in a rendered response, and the render call sites were removed 8 Aug 2026** (`09-retired-positions.md` §18, `02-product-and-architecture.md`). The claim is true of what was built and describes a terminus that no longer exists in the source. Still usable as evidence that capture-and-classify works end to end on a real device; do not present the response half as current product. **The 88/88 and 6/6 counts above fall with the removed tests — quote neither number until the new suite is green**, then restate both together.

🟢 **Single script tag, no SDK dependency, no backend, removable in one line.** Defense: show the integration line.

🟢 **The partner DOM is untouched — the SDK inserts no element into the page and renders nothing, ever.** No exception clause, as of 9 Aug 2026: render call sites and the overlay div are both removed from the source, not disabled by configuration. Defense: a security team reads the source and finds no DOM insertion at all. This is architectural, and saying it as a configuration fact ("nothing renders in your setup") gives away the whole strength of it.

🟢 **No PII leaves the browser.** Defense: the source is readable, a security team can verify it. No field values, no credentials, no document content, no cookies, no `localStorage`.

⚠️ **"The only outbound call after config load is a session-end weight POST."** **False as written since 8 Aug 2026.** The call is still single and still fires at session end, but it now carries per-session behavioral aggregates alongside the weight array (`09-retired-positions.md` §20). Restate as: one outbound call, at session end, carrying updated weights and per-session aggregate counts — never raw events, and never during the session.

**Keep "no PII" and "no personal data" strictly apart when saying either.** A session-keyed aggregate is personal data under `05-regulatory-posture.md`'s own test — data becomes personal *"the moment it can reasonably be tied to a session, account, or device."* Claiming the second while defending the first is retired position `09-retired-positions.md` §10, and it is the claim a partner's privacy counsel catches first.

🟡 **Sub-30kb gzipped.** Defense: measure the bundle before quoting it. Earlier materials quote both <30kb and <15kb for different builds — quote the shipping number, not the target.

🔴 **10–15% lift in first-deposit conversion.** This is a target, not a result, and appears in pilot material as an estimate. **Do not state it as an achieved outcome.** There is no partner data. If it appears anywhere, it must be visibly framed as the pilot's hypothesis.

🔴 **Synthetic scripted users show measurable uplift.** Internal validation only, not partner data, no external baseline. Usable as "we have started validating beyond judgment calls," not as evidence of lift.

## Market claims

🟢 **Betting Hero exists and is paid by major sportsbooks for in-person activation.** Defense: public company, public client relationships, plus first-hand intel from a former operator.

🟢 **Underdog closed its sportsbook in December 2025, withdrew its Missouri application, and launched a federally licensed prediction exchange in July 2026.** Defense: publicly reported.

🟢 **87 operators hold active Brazilian licenses as of Q3 2026; CPF validation is mandatory and SPA Ordinance 722/2024 requires biometric Face Match at onboarding.** Defense: SECAP portal is public. When quoting market size, state *operators* — not brands.

🔴 **Roughly 180–200 federally authorised brands in Brazil, plus state-level licensing above that.** Single source — LATAM B2B veteran, 3 Aug 2026 call. Different unit from licensed operators; operators may hold multiple brands. Do not conflate with the 87-operator figure. Say "brands" when using this number.

🟢 **GENIUS Act implementation — OCC proposed rule 2 March 2026, FinCEN/OFAC joint NPRM 8 April 2026, regime operational January 2027.** Defense: regulator publications. Verify currency before use; this is moving.

🟡 **DeFi TVL fell roughly 37% in H1 2026, from ~$114.5B to ~$71.8B, while stablecoin circulation crossed $314B.** Defense: cite the source and the date, and note TVL methodology varies by tracker.

🟡 **Novig reportedly valued near $500M with over $5B cumulative volume.** Defense: reported figure, not confirmed by the company. Say "reportedly."

🟡 **Affiliate link effectiveness for driving sign-ups is declining.** Defense: industry reporting, directional rather than quantified.

🔴 **A 2025 deposit tax in Colombia contracted the market roughly 25%; operators responded with an untargeted ~20% bonus because they could not identify which players had left over the tax.** Single source — a LATAM B2B veteran recalling figures on the 3 Aug 2026 call, not citing them. Corroborate before external use. Strong as an illustration of deposit-step friction; do not present it as researched.

🔴 **Market sizing figures of any kind.** No defensible TAM figure currently exists in the document set. Do not put one in an application without building it from operator count times realistic contract value, with the arithmetic sayable out loud.

## Competitive claims

🟢 **CRM platforms have no event for user hesitation.** Defense: schema argument, verifiable against any CRM's public event documentation.

🟢 **Optimove and comparable platforms have genuine real-time triggering.** Say this proactively. Conceding it is what makes the input-model argument credible.

🟡 **Session replay tools carry a heavier privacy footprint than Heed.** Defense: architectural comparison. Do not attach it to a named vendor without checking that vendor's current public statements.

🔴 **Mindway AI scaled from roughly 100,000 monitored players per month in 2021 to over 9 million by 2025, across 39 countries and 64 jurisdictions.** Single source: a GTM research document citing iGaming trade press, 4 Aug 2026. Not independently checked. Useful as evidence that licensed operators adopt behavioral inference at scale; verify before it appears in a deck.

🟢 **Heed's category is intelligent behavioral intervention.** Defense: founder decision, 4 Aug 2026. Describes intervention on behavioral substrate without asserting speed as the differentiator. Do not substitute "real-time behavioral response infrastructure" or "behavioral control layer" — both are retired (`09-retired-positions.md` §16).

🔴 **Any claim about a specific competitor's internal architecture or roadmap.** Not held. Do not make. This now explicitly includes OptiKPI and Talon.One, which are named in internal material without any mechanism work behind them.

🔴 **Behavioral inference is an established category, proven in fraud, AML, and account-security tooling — Heed applies it at a new point in the funnel.** Used as the category de-risking half of the "we'd rather not be first" counter (`01-positioning.md` §10). Founder assertion, not checked. Defense as written is thin: the only instances actually verified in this set are Mindway AI and Neccton in licensed gambling, and the Mindway scale figures are themselves 🔴. Lifts to 🟡 once two publicly documented non-gambling examples are named and dated. Until then, argue it with Mindway and Neccton, which are at least in the prospect's own industry.

## Regulatory claims

🟡 **Heed is most accurately classified as a data processor.** Defense: architectural intention. **Never state as a settled legal conclusion** — it depends on actual DPA language and production data flows.

🟡 **Behavioral scoring is profiling and this is unavoidable.** Defense: definitional under GDPR-family law.

🟡 **Heed sits outside GDPR Article 22 because the significant decision is the operator's.** Defense: the operator's pre-configured rule stands between signal and effect. Needs case-by-case review per partner config.

🔴 **Any specific licensing threshold, fee, effective date, or supplier-certification requirement.** All of these need jurisdiction-specific counsel. Present as research, never as clearance.

❌ **"Behavioral data is outside personal-data scope and outside your DPAs entirely."** This claim appears in prior pilot material and is wrong. Retract it wherever it survives.

## Company claims

🟢 **Active conversations with the CEO of PrizePicks, Head of Partner Integrations at Banxa, and ProphetX.** Jackpot.com reached discovery and deferred to early 2027 on 8 Aug 2026 and may no longer be counted as active. Defense: state three, not four. The older four-name version appears in submitted applications and in the deck — correct it before either is used again.

🟢 **Category-level pipeline phrasing, where naming is not permitted:** "active conversations with licensed operators across DFS and on-ramps." No names, no stage, no count implied beyond what the sentence says. This is the only approved way to reference the pipeline to a prospect, and it exists because no prospect is named to another prospect. The naming confidentiality question flagged in `07-company-team-and-status.md` and `09-retired-positions.md` §12 is unresolved and applies to every document naming a partner.

🟢 **85 qualified accounts in outbound across two Apollo lists.**

🟢 **Pre-incorporation, counsel engaged, Delaware C-corp path identified.**

🟢 **Phase 1 is free.** Defense: founder decision 8 Aug 2026. It is a scoping instrument, not a discount — say it that way and never as a trial, introductory rate, or waived fee (`06-commercial-and-pilot-structure.md`).

⚠️ **Phase 2 pricing — basis decided, figure not.** A flat per-month platform fee. **No amount may be quoted.** The retired $3–5K per engagement was a fixed fee on a two-to-four-week engagement and does not convert to a monthly fee by any arithmetic (`09-retired-positions.md` §15, §17). The $5–8K/month deck figure remains withdrawn and is not a starting point.

🟢 **Phase 1 is collection only. Event listeners across the wedge, no inference, nothing rendered, no change to the user experience.** Three to four weeks, ending in a written read on where sessions stall and what precedes it. Defense: founder decision 8 Aug 2026, and the architecture is readable — there is no inference call and no response path in a Phase 1 build.

**Do not say "read-only."** It is an engineering term of art meaning read access to systems, which invites the question *read access to what* when the answer is nothing. The second reason it was wrong — that it was not literally true while the overlay div was injected at init — lapsed on 9 Aug 2026 when the div was removed. The first reason stands alone and is sufficient. The ⚠️ that stood against this phrasing on 8 Aug was raised against a pilot structure that has since been adopted; the structure is now real and the phrasing is still wrong, for a different reason (`09-retired-positions.md` §17). Approved instead: **infrastructure that senses and reports** (`05-regulatory-posture.md`).

**What the Phase 1 written read may contain.** Payload decided 8 Aug 2026 — per selector, per signal type: count, mean, p50, p90, max (`02-product-and-architecture.md`).

🟢 **Supported: duration and magnitude, per screen.** p90 and max recover it. *"At your Confirm step the 90th-percentile dwell is eleven seconds"* is a defensible sentence, and it is the first time canon has been able to evidence `01-positioning.md` §3's primary category — the aborted and partial physical actions the file calls the ground to fight on. Defense: it is a measured statistic on the partner's own funnel, permitted under the provenance carve-out in `CLAUDE.md`.

🟢 **Supported: per-screen signal density and frequency, by signal type.** Which screens carry the most hesitation signal, and of which kind.

🟢 **Supported: outcome comparison, between buckets.** Resolved 8 Aug 2026 — the aggregate is stratified into completed and abandoned. *"Non-completing sessions carried a p90 dwell of nineteen seconds at the fee row, against six for completing sessions"* is a defensible sentence. Defense: measured on the partner's own funnel under agreement (`CLAUDE.md` provenance carve-out), stated as a comparison between two populations, never as a cause.

🟢 **Supported: signal-type co-occurrence, within a bucket.**

❌ **Not supported at any payload dimensionality: session-level sequence.** No ordering, no timestamps, no session records. *"They blurred the document field, then scrolled back to the fee row, then left"* cannot be said and cannot be softened into being sayable.

❌ **Not supported anywhere, in any phase: an abandoned tap.** Resolved 9 Aug 2026 — the four signal types in `02-product-and-architecture.md` are complete and none of them is an abort. This is not a Phase 1 limitation and not a gap to be built; it was a description in `01-positioning.md` §3 of a behavior Heed does not observe, and that prose is corrected. **A long touch is sayable — it is a dwell on a touch target. An abort is not.** Do not write "users hold the button and don't press it" into a read, a deck, or a call.

⚠️ **Every duration figure is provisional until the histogram bins are set.** Percentiles do not merge across sessions, so p50 and p90 are read from a merged histogram whose bin edges are undecided (`02-product-and-architecture.md`). The bins set the resolution of every duration claim. Separately and obviously: no Phase 1 has run, so **there is no actual figure yet** — the 🟢 above is a claim about what the read may contain, not a number in hand.

⚠️ **Field focus with no entry — count only. No duration figure is quotable.** Blur-without-completion is a count. Whether focus *duration* is captured depends on whether dwell is measured on focused fields, which `02-product-and-architecture.md` does not specify. **Blocked pending Anthony's confirmation.** Until he confirms, no number derived from field-focus duration reaches any artifact: say that sessions leave the field without entering, never how long they sat in it.

**And in every phrasing: precedes. Never causes, never appears to cause.** Phase 1 has no intervention arm and supports no causal claim of any kind, at any hedge level.

❌ **"Pilots underway with Banxa, Jackpot.com, and PrizePicks."** False. They are conversations. Appears in the expanded regulatory report and must be corrected before that document is attached to anything.

❌ **"Design partner commitments secured across DeFi and CeFi platforms."** False. Appears in `Product_Posture.md`. Nothing is signed.

❌ **Any revenue, signed pilot, or LOI claim.** None exist.

## The rule

If a claim is not in this register, it has not been checked. Either check it and add it, or do not make it.
