# SaaS AI Due Diligence Report

*Produced with the saas-ai-due-diligence skill. Content unchanged from the original; Markdown formatting restored.*

**Vendor:** Lovable (Lovable Labs Incorporated / Lovable Labs Sweden AB) | **Assessment date:** 22 September 2026

**OVERALL ASSESSMENT: 🔴 RED / 🟡 Yellow for business/enterprise**

**Scope:** This assessment covers the vendor based on the documents provided, not your use case. Assessed against the strictest (default) tier; tier differences are flagged in bold. Not legal advice.

| # | Criterion | Color | Finding (one line) |
|---|---|---|---|
| C1 | No training on customer data | 🔴 | Training on Customer Content is on by default with an opt-out on all consumer plans. DPA prohibits it for Business/Enterprise. |
| C2 | Retention and deletion | 🟡 | Deletion on account closure or request, but no firm deletion deadline and backups persist; B/E adds a 30-day instruction window, then discretionary. |
| C3 | Data location and jurisdiction | 🔴 | US-owned contracting entity (CLOUD Act) + ToS disclaims any regional processing guarantee = unrestricted transfer right; data flows to US. |
| C4 | Subprocessor list | 🟡 | Full list published (names/role/location), but change-notification + objection right exist only under the DPA (Business/Enterprise). |
| C5 | AI risk classification | 🟡 | No EU AI Act risk classification of the product in any document; responsibility pushed to the customer/deployer. |
| C6 | AI models and providers | 🟡 | Providers named (Anthropic, OpenAI, Google, OpenRouter, ElevenLabs, AWS Bedrock); specific models/roles unspecified, OpenRouter routing leaves the set open. |
| C7 | Certifications | 🟢 | ISO 27001:2022 + SOC 2 Type II on the trust center, reports on request; DPA contractually commits to maintaining both. |

## Recommendations (before the procurement decision)

- **C1:** Opt out of model training immediately in account settings for every workspace (default is opt-in). For anything non-trivial, move to Business/Enterprise where the DPA prohibits training on Customer Personal Data — and get written confirmation the prohibition covers all Customer Content (not just personal data), plus reconciliation of the DPA's internal contradiction (§9 lists ML training/tuning as a permitted Service Data purpose; §10.3 says Service Data is not used for AI/ML training).
- **C2:** Negotiate a firm deletion deadline (concrete number of days from termination and from a deletion request), covering backups, and remove the "at its discretion" language so deletion is an obligation, not an option.
- **C3:** Obtain a written EU/EEA data-residency commitment; confirm which model/infra providers can be pinned to EU regions (GCP-EU, Supabase-EU, Bedrock-EU) or disabled. Note the contracting/importing entity is Lovable Labs Incorporated, Boston MA (US) → CLOUD Act exposure regardless of tier.
- **C4:** Consumer/Pro users get no change-notification or objection right — move to Business/Enterprise for the DPA's 20-business-day objection right, or secure a written notification commitment.
- **C5:** Request Lovable's own EU AI Act classification of the product; separately classify your intended deployment (you are a deployer). One document from Lovable resolves this.
- **C6:** Request the specific model list per provider and confirm OpenRouter's downstream routing set — routing can send prompts to models beyond those named. This one request also tightens C1 (the no-training promise must bind every provider) and C3 (each US provider is an EU exit point).

**Notices:** The EU AI Act applies in phases — verify current obligations against a current source. As a deployer you may have your own AI Act obligations; assess your use case separately.

---

## Appendix — Evidence

### C1 — No training on customer data 🔴

**Source:** Privacy Policy §5 (AI Model Training); Terms of Service (Rights in Customer Data); DPA §10.
**Quote:** "We use Customer Content and Usage Data — which may include Personal Data — to train, develop, fine-tune, and improve our AI models […] You can opt out of model training at any time in your account settings, on any plan, at no cost." And ToS: "We may use your Customer Data to develop and train artificial intelligence and machine learning models. You may tell us at any time that you do not want your Customer Data used for model training […] we will honor that request for prospective use." And DPA §10.1: "Lovable shall not use any Customer Personal Data for the purpose of training, retraining, fine-tuning, or otherwise developing any Artificial Intelligence (AI) or Machine Learning (ML) models."
**Finding:** On every consumer/default plan, training happens unless the customer acts — training is enabled by default with an opt-out, and the opt-out is prospective only ("It does not retract content from training datasets assembled, or models trained, before you opted out"). On Business/Enterprise the DPA prohibits training on Customer Personal Data, which lifts this off Red — but not to Green, because (a) the DPA prohibition names only Customer Personal Data, not all Customer Content, and (b) DPA §9 lists "training or tuning proprietary machine-learning models used to deliver the Services" as a permitted Service Data (de-identified) purpose, directly contradicting §10.3's statement that Service Data "is not used for AI/ML training." Training on de-identified data derived from customer data is still training.
**To obtain:** Written no-training commitment covering all Customer Content on your tier; reconciliation of DPA §9 vs §10.3; confirmation the commitment binds every model provider in C6.

### C2 — Retention and deletion 🟡

**Source:** Privacy Policy (Data Retention); DPA §11; DPA Annex 1 (Retention and erasure).
**Quote:** "Your account and Customer Content — kept while your account is open, then deleted or de-identified after it closes or after a verified deletion request, unless the law requires us to keep it longer." And DPA §11.2: "Within thirty (30) calendar days after the termination of the Agreement the Customer may instruct Lovable, in writing, to return or delete all Customer Personal Data […] If no such instruction is received within thirty (30) calendar days, Lovable may, at its discretion, permanently delete or irreversibly anonymize."
**Finding:** A deletion mechanism exists on both tiers, but there is no committed deletion deadline: consumer deletion is tied to account closure or a verified request with no timeframe, and backups persist ("Deleted data may persist in backups for a limited time"). The DPA gives a 30-day instruction window, after which deletion is discretionary ("may, at its discretion"), and Lovable may bill for export/deletion exceeding two person-hours. Subprocessor deletion is addressed by DPA §7 (equivalent obligations imposed by contract).
**To obtain:** A firm deletion SLA (days) covering primary and backup copies, with deletion as an obligation rather than at Lovable's discretion.

### C3 — Data location and jurisdiction 🔴

**Source:** ToS (Use of Infrastructure and AI Providers); Privacy Policy (International Data Transfers); DPA §1 / Annex 1 (data importer); subprocessor list.
**Quote:** "we do not guarantee that data transmitted through the Platform or the AI Gateway will be processed or stored in any particular country or region. By using the Services, you consent to these transfers, processing, and storage." And Privacy Policy: "We and our service providers process Personal Data in a number of countries, including the United States." And DPA: data importer "Lovable Labs Incorporated, [1 Lincoln St, Boston, MA 02111], Role: Processor."
**Finding:** Two entities exist — Lovable Labs Sweden AB (Stockholm) is the privacy controller/EU establishment, but Lovable Labs Incorporated (Boston, MA, USA) is the ToS contracting party and the DPA data importer, creating US CLOUD Act exposure on every tier. The ToS grants an effectively unrestricted transfer right (no guarantee of any region + consent to transfers). SCCs/UK IDTA/Swiss addendum are in place as transfer mechanisms for personal data, but they do not cure the unrestricted-transfer language or the US-importer exposure, and the AI model providers (C6) are predominantly US-based, so customer prompts leave the EEA with each model call. On Business/Enterprise the DPA constrains transfers to SCC modules and adds a government-request redirect clause, which would move this to Yellow — still not Green, as there is no EU-residency guarantee and the importer remains US.
**To obtain:** Written EU/EEA residency option and confirmation of EU-region pinning for model and infrastructure providers; ownership/CLOUD Act risk sign-off.

### C4 — Subprocessor list 🟡

**Source:** Trust center subprocessor list (provided); DPA §7; Privacy Policy (Who Receives Your Personal Data).
**Quote:** DPA §7.1: "Lovable shall inform the Customer of any intended changes concerning the addition or replacement of other processors through updating the sub-processor list available at lovable.dev/subprocessors […] This list is updated at least annually." Privacy Policy: "Our current sub-processor list, including each provider's location and purpose, is at trust.lovable.dev."
**Finding:** The published list is substantially complete — names, purpose/role, and location for ~30 subprocessors (a handful vague on location: Cloudflare "Global," TanStack "N/A"). The change-notification process and the 20-business-day right to object (with termination + prepaid-fee refund as the remedy) exist only in the DPA, i.e. Business/Enterprise. Consumer/Pro users get the published list but no notification or objection right. On Business/Enterprise, C4 would be Green.
**To obtain:** For non-DPA tiers, a written advance-notification and objection commitment; or move to Business/Enterprise.

### C5 — AI risk classification 🟡

**Source:** — (no EU AI Act classification present in any provided document).
**Quote:** —
**Finding:** No document classifies Lovable's AI functionality under the EU AI Act or states the resulting obligations. The ToS instead shifts responsibility to the user ("agree not to rely on it for critical or high-risk functions … without appropriate safeguards") and the DPA states Lovable "does not engage in automated decision-making with legal or similarly significant effects." As an AI code/app-generation assistant the product itself most plausibly sits in the limited-risk (transparency) band, but this is not stated — and your deployment could raise the class depending on what you build with it.
**To obtain:** Lovable's stated AI Act classification of the product; a separate classification of your own intended use.

### C6 — AI models and providers 🟡

**Source:** Trust center subprocessor list; ToS (Definitions — Third-Party AI Provider); Privacy Policy §8.
**Quote:** ToS: "'Third-Party AI Provider(s)' means external providers of artificial intelligence models … (for example, OpenAI, Google, or Anthropic)." Subprocessor list: "Anthropic (Claude) — US … OpenAI — US … Google Gemini — US … OpenRouter — LLM inference routing — US … ElevenLabs — US … Amazon Web Services — Services: S3, SES, Bedrock — US."
**Finding:** Providers are named with locations and roles — the real output of this criterion: Anthropic, OpenAI, Google Gemini, AWS Bedrock, ElevenLabs (audio), routed via OpenRouter, plus Lovable-operated proprietary models. Specific model names/versions and the model-to-function mapping are not given, and OpenRouter's routing means the actual downstream model set is open-ended. All named inference providers are US-based (feeds C3). GPAI-vs-native is clear (third-party foundation models + some Lovable-operated models).
**To obtain:** Model-level inventory per provider and OpenRouter's downstream allow-list; confirmation each is bound by the C1 no-training commitment.

### C7 — Certifications 🟢

**Source:** Trust center (provided screenshot); DPA §5.
**Quote:** Trust center lists "ISO 27001:2022," "SOC 2 Type II" (and SOC 2 Type I, AIUC-1), with Certifications resources (SOC 2 Type I/II, Bridge Letter) gated. DPA §5: "Lovable shall maintain SOC 2 Type II and ISO 27001 accreditations for the duration of the term of the Agreement."
**Finding:** Two strong, in-scope, independent certifications — ISO 27001:2022 and SOC 2 Type II — are listed on the trust center with reports available on request (gating is standard, not a gap), and the DPA turns them into a contractual maintenance obligation for Business/Enterprise. The "GDPR" item is a self-declared badge and does not count toward the verdict. ISO 42001 (AI management system) is not present; adding it would be the natural strengthening step for an AI product. AIUC-1 is an AI-specific trust attestation — a useful supplement but not a substitute for the above.
**To obtain:** — (Green)

---

**Standard notices:** This is decision-support, not legal advice. The EU AI Act applies in phases — verify current obligations against a live source. As a deployer, even a compliant product can create obligations for your organisation depending on how you use it; assess your intended use separately.
