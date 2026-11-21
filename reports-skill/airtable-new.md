# SaaS AI Due Diligence Report

*Produced with the saas-ai-due-diligence skill. Content unchanged from the original; Markdown formatting restored.*

**Vendor:** Formagrid Inc, dba Airtable | **Assessment date:** 18 Sep 2026

**OVERALL ASSESSMENT: 🟡 YELLOW**

**Scope:** covers the vendor based on the documents provided, not your use case. Assessed against the strictest (default) tier; tier differences flagged in bold. Not legal advice.

## Criteria

| # | Criterion | Color | Finding (one line) |
|---|---|---|---|
| C1 | No training on customer data | 🟡 | Unconditional no-training commitment covering all third-party providers, but Privacy Policy reserves aggregated/de-identified data for analytics & "service improvement". |
| C2 | Retention and deletion | 🟡 | Delete-or-anonymize on termination, but only on written request, no concrete deadline, backups deferred to unspecified internal retention. |
| C3 | Data location and jurisdiction | 🟡 | US-owned; default stores all data in US under EU SCCs (valid mechanism). EU/AU residency exists only on Enterprise Scale — and metadata + auth data always stay in US. |
| C4 | Subprocessor list | 🟢 | Complete list (names/purpose/location), 10-day advance notice, right to object with a termination remedy. |
| C5 | AI risk classification | 🟡 | No EU AI Act risk class stated; only generic "comply with applicable AI laws" language. |
| C6 | AI models and providers | 🟡 | Full provider inventory with locations, but specific models and per-feature routing not disclosed. |
| C7 | Certifications | 🟢 | SOC 2 Type II, ISO 27001:2022, ISO 27701:2019, HIPAA, TX-RAMP L2. No ISO 42001. |

## Recommendations (before the procurement decision)

- **C1:** Confirm in the order form/MSA that the AI Terms §5 no-training commitment governs, and get written confirmation that Content is excluded from the Privacy Policy's aggregated/de-identified analytics use (as Usage Data already is).
- **C2:** Negotiate a concrete post-termination deletion deadline (e.g. 30/90 days) and a defined backup-purge window; the default defers to undocumented internal retention.
- **C3:** If EU residency matters, budget for Enterprise Scale and accept that base metadata, scripts, and authentication data (password hashes, OAuth tokens) remain in the US regardless; assess US CLOUD Act exposure independently of hosting region.
- **C5:** Request Airtable's EU AI Act risk classification for Airtable AI plus any transparency/conformity documentation.
- **C6:** Request per-feature model routing (which provider/model serves which Airtable AI feature) — one document sharpens C6 and confirms C1's no-training coverage across every provider.

**Notices:** The EU AI Act applies in phases — verify current obligations. As a deployer you may have your own AI Act obligations; assess your use case separately.

---

## Appendix — Evidence

### C1 — No training on customer data 🟡

**Source:** Airtable AI Terms §5; Privacy Policy §2.b
**Quote:** "Airtable will not use, or permit the Third-Party AI Providers or others to use, Input, Output, or any other Customer Data to train generative artificial intelligence models." — and — "Aggregated or De-Identified Data. This includes use of aggregated or de-identified information for a wide variety of statistical, analytical, and service improvement purposes."
**Finding:** The no-training commitment is unconditional, applies on every plan, and extends to the third-party model providers — unusually strong. What holds it below Green is the separate, standing right to use aggregated/de-identified data for analytics and "service improvement". This is typical SaaS boilerplate, not model training, but it is a secondary use of data derived from Content and cannot be relied on as absent. ToS §2.5 helpfully excludes "Your Content" from Usage Data.
**To obtain:** Written confirmation that Content is out of scope of the aggregated/de-identified use, ideally in the order form.

### C2 — Retention and deletion 🟡

**Source:** DPA §12 (Destruction of Personal Data)
**Quote:** "Upon termination of the Agreement and written request from Customer, Airtable will delete or anonymize Customer Personal Data, unless prohibited by Applicable Law. Notwithstanding the foregoing, nothing will oblige Airtable to delete or anonymize Customer Personal Data from files created for security, backup and business continuity purposes sooner than required by Airtable's data retention processes."
**Finding:** A real deletion/return mechanism exists, and it extends down the subprocessor chain (DPA §5.1). But three things keep it off Green: deletion is triggered only by a written request (not automatic), no concrete deadline is stated, and backups are carved out by reference to unspecified internal retention timelines. The Enterprise Scale data-residency page is firmer ("Airtable will delete all in-product data from Airtable's systems... upon termination") but still gives no deadline.
**To obtain:** A concrete deletion SLA and backup-purge window in the contract.

### C3 — Data location and jurisdiction 🟡

**Source:** DPA Exhibit A (importer); DPA §9.2 (EU SCCs); Data residency page
**Quote:** "Name: Formagrid Inc dba Airtable Address: 1 Front Street, Fl 28, San Francisco, CA 94111" — and — "Airtable offers data residency in the United States (default), Europe, and Australia." — and — "Regardless of your chosen data region, the following data is stored in US-based data centers: Base metadata... User and authentication data (Usernames, password hashes, OAuth token data, etc.)..."
**Finding:** Airtable is US-owned and US-headquartered, so US CLOUD Act reach applies to data in its possession regardless of where it is hosted. On the default tier all Customer data sits in the US; transfers from the EEA/UK/Switzerland run on the EU SCCs (Module 2/3, Irish governing law) — a valid mechanism, which is what keeps this off Red. On Enterprise Scale, data residency (EU/AU) covers in-base data, attachments, and revision history — but base metadata, scripts, and authentication data (including password hashes and OAuth tokens) remain in US data centers even with residency enabled.
**To obtain:** Decide whether Enterprise Scale residency is required; document the residual US metadata/auth footprint and CLOUD Act exposure.

### C4 — Subprocessor list 🟢

**Source:** Subprocessor list (25 Aug 2026); DPA §5.2, §5.3
**Quote:** "Airtable will provide Customers with at least ten (10) days' written notice of new sub-processors before authorizing such sub-processor(s) to Process Customer Personal Data..." — and — "Customer may object to Airtable's use of a new sub-processor on reasonable grounds relating to the protection of Customer Personal Data by notifying Airtable... within ten (10) business days..."
**Finding:** Complete published list with entity, purpose, and country for core infrastructure, AI, and other subprocessors. Advance-notice process and a genuine right to object exist, backed by a termination remedy if Airtable cannot avoid the objected-to subprocessor (§5.3). Meets the requirement in full.

### C5 — AI risk classification 🟡

**Source:** Airtable AI Terms §10 (Governance, Compliance, Responsible AI)
**Quote:** "Airtable will comply with all laws and regulations applicable to its integration and use of AI within the Services, including applicable laws and regulations regarding the responsible and ethical deployment of AI capabilities."
**Finding:** No EU AI Act risk class is stated and no conformity/transparency documentation is referenced — only a general commitment to comply with applicable AI law plus internal evaluation/testing. As a general-purpose generative productivity feature, Airtable AI most likely falls under limited-risk (transparency) rather than high-risk obligations, but the vendor does not say so. Your own deployment context could raise the class.
**To obtain:** Airtable's stated AI Act risk classification and any transparency/conformity evidence.

### C6 — AI models and providers 🟡

**Source:** Subprocessor list — In-Product AI Subprocessors; AI Terms §1, footnote
**Quote:** "Amazon Web Services (AI model provider — Global); Anthropic, PBC (USA); Google LLC (Global); IBM (USA); OpenAI, LLC (USA)" plus Castle Global (moderation), Parallel Web Systems, Reducto, Vercel.
**Finding:** Provider inventory is complete and located — the real output of this criterion. Every model provider is a third-party GPAI vendor; Airtable runs no native model. What holds it below Green: the specific models are not named and per-feature routing (which feature calls which provider) is not disclosed. Note the "Global"/USA locations directly feed C3 — each AI call can move data out of your chosen region.
**To obtain:** Per-feature model/provider routing map.

### C7 — Certifications 🟢

**Source:** Compliance & Certifications page; DPA §10 (Audits)
**Quote:** "SOC 2 Type 2 ... ISO/IEC 27001:2022 ... ISO/IEC 27701:2019 ... HIPAA ... TX-RAMP Level 2."
**Finding:** A strong, current stack: SOC 2 Type II plus ISO 27001:2022 (ISMS) and ISO 27701:2019 (privacy information management), reinforced by HIPAA and TX-RAMP Level 2. SOC 2 sitting behind an account-manager request is standard practice, not a gap. The one absence worth noting is ISO 42001 (AI management system), which would be the natural next certification for a product shipping generative AI. These audits act as a reliability multiplier for the contractual promises in C2–C4.

---

**Standard notices:** (1) Deployer responsibility — even a compliant product can create AI Act obligations for you depending on how your teams use Airtable AI; assess your intended use separately. (2) The EU AI Act applies in phases — verify obligations and dates against a current source. (3) Not legal advice.
