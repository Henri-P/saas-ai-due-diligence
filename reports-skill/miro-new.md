# SaaS AI Due Diligence Report

*Produced with the saas-ai-due-diligence skill.*

**Vendor:** RealtimeBoard, Inc. dba Miro | **Assessment date:** 18 September 2026

**OVERALL ASSESSMENT: 🔴 RED (On non-enterprise plan) / 🟡 on Enterprise**

**Scope:** This assessment covers the vendor based on the documents provided, not your use case. Assessed against the strictest (default self-serve) tier; tier differences are flagged in bold. Not legal advice.

## Criteria

|#|Criterion|Color|Finding (one line)|
|-|-|-|-|
|C1|No training on customer data|🔴|On non-enterprise plans, AI Input/Output is used to train/fine-tune Miro's models by default unless you object.|
|C2|Retention and deletion|🟡|Deletion on request/termination exists, but no concrete deadline and backups are excluded.|
|C3|Data location and jurisdiction|🟡|US-owned processor, default US processing (CLOUD Act exposure); EU residency is an optional add-on.|
|C4|Subprocessor list|🟢|Complete list with names/role/location, advance-notice option and a right to object.|
|C5|AI risk classification|🟡|No EU AI Act risk class stated in any provided document.|
|C6|AI models and providers|🟢|Full inventory of models, providers and hosting disclosed.|
|C7|Certifications|🟢|ISO 27001 + SOC 2 Type II + ISO 42001, listed with dates.|

## Recommendations (before the procurement decision)

* **C1:** If you proceed on a self-serve/Business plan, you must locate and exercise the opt-out for AI training before rolling out AI features — or negotiate onto the Enterprise Master Cloud Agreement, where training is opt-in (consent-based). Confirm the opt-out mechanism in writing.
* **C2:** Request Miro's current data-deletion timelines/policy (the DPA defers to an unstated schedule) and confirm the backup-retention window.
* **C3:** If EU/EEA data residency matters, confirm the AWS EU data residency offering in the Order, and note that AI calls still route to US model providers regardless (see C6).
* **C5:** Request Miro's EU AI Act positioning for its AI Features, and assess your own deployer obligations for your intended use case.

**Notices:** The EU AI Act applies in phases — verify current obligations against a live source. As a deployer you may have your own AI Act obligations; assess your use case separately.

\---

## Appendix — Evidence

### C1 — No training on customer data 🔴

**Source:** AI Terms (eff. 17 July 2024), §3
**Quote:** "If your use of Miro's Service is not through a subscription to a Miro enterprise plan (e.g. if you are on a free, starter, business, or equivalent plan), and Miro seeks to use your Input and Output for improving its AI Features, including for training or fine tuning underlying models, Miro will provide you with reasonable means to object to such use." … "If you consent (or do not object) to Miro's use of Input and Output to improve the AI Features, you grant Miro a non-exclusive, perpetual, irrevocable, worldwide, royalty-free license to use your Input and Output. Miro will remove direct identifiers when using Input and Output to improve AI Features consistent with industry standards."
**Finding:** On the default self-serve tier (free/starter/business), your AI Inputs and Outputs are used to train and fine-tune Miro's underlying models unless you actively object — training is on by default, which is the core concern here. De-identification ("remove direct identifiers") does not cure this: it is still training on data derived from your content, and the license you grant is perpetual and irrevocable. On the Enterprise Master Cloud Agreement this is opt-in — "Miro will obtain your consent prior to using your Input and Output for improving its AI Features, including for training or fine tuning underlying models" — which would move C1 to 🟡. Note that Miro's AI Features are off unless enabled, so this exposure only materializes once your users turn AI on.
**To obtain:** Written confirmation of the training opt-out procedure for your tier, or migration to the Enterprise agreement; ideally a contractual no-training commitment covering all providers in C6.

### C2 — Retention and deletion 🟡

**Source:** DPA (eff. 17 Sept 2024), §9; Terms of Service §4.4
**Quote:** "Upon Customer's request during the Agreement Subscription Term and/or at termination or expiry of this DPA, Miro shall delete or return to Customer all Customer Personal Data in its possession in accordance with Miro's then-current data deletion timelines and policies \[…] This requirement shall not apply \[…] to Customer Personal Data archived on back-up systems, which data Miro shall isolate and protect from any further processing" — and, from the ToS: "During the Subscription Term or within 30 days thereafter, Customer may export its Customer Content \[…] If Customer elects to proactively delete its account at any time, all associated Customer Content will be deleted permanently and cannot be retrieved."
**Finding:** A deletion/return mechanism exists on termination and a 30-day export window is defined, which is good. But the deletion deadline is not fixed in the contract — it defers to Miro's "then-current data deletion timelines and policies" — and backups are explicitly carved out (isolated rather than deleted on a stated schedule). This is fairly typical SaaS boilerplate, but it means you cannot rely on a specific deletion SLA as written.
**To obtain:** Miro's current data-deletion timeline document (the DPA says it "may be requested by Customer at any time") and the backup retention period.

### C3 — Data location and jurisdiction 🟡

**Source:** DPA §8.1; Privacy Policy §9; Subprocessor List (updated 8 July 2026); ToS §20.2
**Quote:** "Customer Personal Data that Miro processes under the Agreement may be processed in any country in which Miro, its Miro Subsidiaries and Sub-processors maintain facilities to perform the Services \[…] Miro shall not process or transfer Customer Personal Data \[…] outside of EEA, Switzerland or UK, unless it first takes such measures as are necessary to ensure the transfer is in compliance with Data Protection Law." Subprocessor list footnote: "location of storage may be limited to certain jurisdictions if a Miro customer chooses a Miro data residency offering."
**Finding:** Miro is RealtimeBoard, Inc., a US company headquartered in San Francisco, CA, with the ToS governed by California law — so even with EU hosting, data is exposed to US jurisdictional access (CLOUD Act). By default, processing occurs in the US: every subprocessor on the list is US-located, and EU/EEA data residency is available only as an opt-in offering (via AWS: "data residency available for AUS, EU, US, Japan"). Cross-border transfers are covered by valid mechanisms — the EU-US Data Privacy Framework (Miro is certified) plus EU/UK SCCs (Module 2/3, Dutch-law governed) — which keeps this out of Red. The residual risk is jurisdictional exposure, not a missing transfer mechanism. Cross-check (C6): even if you select EU residency, AI features send data to US-based model providers on each call.
**To obtain:** EU data-residency confirmed in the Order if required; clarity on which support/log/backup data stays in-region.

### C4 — Subprocessor list 🟢

**Source:** DPA §3.1–3.4; Subprocessor List (updated 8 July 2026)
**Quote:** "If Miro engages a new or replacement Subprocessor, Miro will: \[…] update the Subprocessor List; impose substantially the same data protection terms \[…] and remain liable to Customer \[…]. If Customer elects to be notified at least ten (10) days prior to Miro engaging a new or replacement Subprocessor, Customer must subscribe to such notifications here \[…] Customer may object \[…] within thirty (30) days after receipt of notice \[…] on reasonable grounds."
**Finding:** A complete, current list (12 subprocessors with names, role and location) is provided, along with flow-down of terms, retained Miro liability, advance-notice and a right to object — all the required elements. Two caveats worth noting rather than downgrading for: notification is opt-in (you must actively subscribe to the notification feed), and if an objection can't be resolved, your remedy is limited to termination. Subscribe to the notification feed on day one so subprocessor changes don't pass silently.

### C5 — AI risk classification 🟡

**Source:** — (no EU AI Act classification found in any provided document; AI Terms §5 and trust center ISO 42001 governance reviewed)
**Quote:** —
**Finding:** None of the provided documents classify Miro's AI Features under the EU AI Act or document the resulting obligations. There is relevant governance — an ISO 42001 (AI management system) certification and AI-governance controls on the trust center, plus an AI Terms clause requiring "adequate human review" for automated decision-making — but governance is not the same as a stated risk class. Miro's AI Features (content/diagram generation, summarization, transcription) are most plausibly limited/minimal-risk, but that is not asserted by the vendor, and your deployment context could raise the classification.
**To obtain:** Miro's EU AI Act positioning for its AI Features; run your own deployer-side AI Act assessment for the intended use case.

### C6 — AI models and providers 🟢

**Source:** Third Party AI Model Providers list (updated 8 July 2026); Subprocessor List; Privacy Policy §5
**Quote:** "the AI features may share limited data with Microsoft in connection with the use of the AI features and to monitor compliance with codes of conduct." (Privacy Policy §5)
**Finding:** Miro provides a complete inventory of models, providers, hosting and licensing. Data goes to US-based providers in all cases:

* Anthropic models — hosted via AWS Bedrock (and under Anthropic Commercial ToS) — US
* Amazon models — AWS Bedrock — US
* OpenAI models — via Microsoft Azure OpenAI and OpenAI LLC — US
* StabilityAI models — AWS Bedrock — US
* Google — Data Discovery (Guard) and AI functionality — US
* Microsoft — accessibility, OCR, AI functionality — US
* ElevenLabs — live captions and transcripts — US
* Self-hosted open models — InSPyReNet (MIT), MobileNetv2 and SSD MobileNetv2 (Apache 2.0), run by Miro via AWS

This list is C6's real deliverable and it feeds C1 (the no-training gap applies across all of these), C3 (all US) and C4.

### C7 — Certifications 🟢

**Source:** Trust center (screenshot); DPA Exhibit 2
**Quote:** Documentation listed: "ISO/IEC 42001:2023 Certificate", "ISO/IEC 27001 Certificate", "SOC 2 Type II Report 2025–2026", "SOC 3 System and Organization Controls Report 2025–2026", "IRAP Attestation Letter".
**Finding:** Miro holds the strongest common combination — ISO/IEC 27001 + SOC 2 Type II + ISO/IEC 42001:2023 (the AI-specific management system standard) — listed with current dates, plus SOC 3, IRAP and UK Cyber Essentials. Several are behind a "Request access" gate, which is standard practice and not a gap; ISO 27001 and SOC 3 are directly downloadable. The GDPR, CCPA, SSPA and DPF badges are self-declarations and don't independently count, but the three real certifications are solid and act as a reliability multiplier for the C2/C3/C4 contractual promises. Obtain the SOC 2 Type II report under NDA and check its scope covers the services and regions you'll use.

