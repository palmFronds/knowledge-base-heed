# 08 — Claims Register

Every claim usable in an application, deck, or prospect conversation, with a confidence flag and the defense to be spoken out loud. 🟢 hard data · 🟡 triangulated · 🔴 estimate

## Product claims

🟢 **SDK v1.0 shipped, 88/88 Vitest and 6/6 Playwright passing.** Defense: run the suite.

🟢 **Full signal chain verified on a real mobile device, both directions** — scroll reversal → `price_doubt` → `discount_offer`, touch hesitation → `confusion` → `tooltip`. Defense: demonstrate it live.

🟢 **Single script tag, no SDK dependency, no backend, removable in one line.** Defense: show the integration line.

🟢 **No PII leaves the browser; the only outbound call after config load is a session-end weight POST.** Defense: the source is readable, a security team can verify it.

🟡 **Sub-30kb gzipped.** Defense: measure the bundle before quoting it. Earlier materials quote both <30kb and <15kb for different builds — quote the shipping number, not the target.

🔴 **10–15% lift in first-deposit conversion.** This is a target, not a result, and appears in pilot material as an estimate. **Do not state it as an achieved outcome.** There is no partner data. If it appears anywhere, it must be visibly framed as the pilot's hypothesis.

🔴 **Synthetic scripted users show measurable uplift.** Internal validation only, not partner data, no external baseline. Usable as "we have started validating beyond judgment calls," not as evidence of lift.

## Market claims

🟢 **Betting Hero exists and is paid by major sportsbooks for in-person activation.** Defense: public company, public client relationships, plus first-hand intel from a former operator.

🟢 **Underdog closed its sportsbook in December 2025, withdrew its Missouri application, and launched a federally licensed prediction exchange in July 2026.** Defense: publicly reported.

🟢 **87 operators hold active Brazilian licenses as of Q3 2026; CPF validation is mandatory and SPA Ordinance 722/2024 requires biometric Face Match at onboarding.** Defense: SECAP portal is public.

🟢 **GENIUS Act implementation — OCC proposed rule 2 March 2026, FinCEN/OFAC joint NPRM 8 April 2026, regime operational January 2027.** Defense: regulator publications. Verify currency before use; this is moving.

🟡 **DeFi TVL fell roughly 37% in H1 2026, from ~$114.5B to ~$71.8B, while stablecoin circulation crossed $314B.** Defense: cite the source and the date, and note TVL methodology varies by tracker.

🟡 **Novig reportedly valued near $500M with over $5B cumulative volume.** Defense: reported figure, not confirmed by the company. Say "reportedly."

🟡 **Affiliate link effectiveness for driving sign-ups is declining.** Defense: industry reporting, directional rather than quantified.

🔴 **Market sizing figures of any kind.** No defensible TAM figure currently exists in the document set. Do not put one in an application without building it from operator count times realistic contract value, with the arithmetic sayable out loud.

## Competitive claims

🟢 **CRM platforms have no event for user hesitation.** Defense: schema argument, verifiable against any CRM's public event documentation.

🟢 **Optimove and comparable platforms have genuine real-time triggering.** Say this proactively. Conceding it is what makes the input-model argument credible.

🟡 **Session replay tools carry a heavier privacy footprint than Heed.** Defense: architectural comparison. Do not attach it to a named vendor without checking that vendor's current public statements.

🔴 **Any claim about a specific competitor's internal architecture or roadmap.** Not held. Do not make.

## Regulatory claims

🟡 **Heed is most accurately classified as a data processor.** Defense: architectural intention. **Never state as a settled legal conclusion** — it depends on actual DPA language and production data flows.

🟡 **Behavioral scoring is profiling and this is unavoidable.** Defense: definitional under GDPR-family law.

🟡 **Heed sits outside GDPR Article 22 because the significant decision is the operator's.** Defense: the operator's pre-configured rule stands between signal and effect. Needs case-by-case review per partner config.

🔴 **Any specific licensing threshold, fee, effective date, or supplier-certification requirement.** All of these need jurisdiction-specific counsel. Present as research, never as clearance.

❌ **"Behavioral data is outside personal-data scope and outside your DPAs entirely."** This claim appears in prior pilot material and is wrong. Retract it wherever it survives.

## Company claims

🟢 **Active conversations with the CEO of PrizePicks, Head of Partner Integrations at Banxa, Strategy & Data at Jackpot.com, and ProphetX.**

🟢 **85 qualified accounts in outbound across two Apollo lists.**

🟢 **Pre-incorporation, counsel engaged, Delaware C-corp path identified.**

❌ **"Pilots underway with Banxa, Jackpot.com, and PrizePicks."** False. They are conversations. Appears in the expanded regulatory report and must be corrected before that document is attached to anything.

❌ **"Design partner commitments secured across DeFi and CeFi platforms."** False. Appears in `Product_Posture.md`. Nothing is signed.

❌ **Any revenue, signed pilot, or LOI claim.** None exist.

## The rule

If a claim is not in this register, it has not been checked. Either check it and add it, or do not make it.
