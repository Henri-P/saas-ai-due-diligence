# Lovable – Previous assessment (without the skill)

*Made with Claude in free-form conversation before the skill existed. Content unchanged from the original.*

!\[Lovable data flow](lovable-dataflow.png)

This is a solid set of documents — privacy policy, terms of service, and DPA. Let me do a full due diligence analysis across the key risk areas.

Here is the full due diligence analysis across the key risk areas.

\---

## 1\. Model training — your prompts and data

This is the most critical area and the language is genuinely split between the Privacy Policy and the Terms of Service, which creates ambiguity.

**The good news:** The DPA (Section 10) is explicit: *"Lovable shall not use any Customer Personal Data for the purpose of training, retraining, fine-tuning, or otherwise developing any AI or ML models."* This is a strong, clear prohibition — but it only applies to identifiable personal data.

**The catch:** The Terms of Service grant Lovable *"a worldwide, perpetual, royalty-free license to use, copy, modify, process, analyze, and otherwise exploit your Customer Data"* including for *"developing and training artificial intelligence and machine learning models."* The carve-out is: this does not apply to PII. But your prompts, generated code, and project content that isn't personally identifying is fair game for model training by default.

**The opt-out:** You can opt out of model training by contacting privacy@lovable.dev or upgrading to a Business plan. This opt-out is not automatic — you must actively request it.

**Verdict:** Your prompts CAN be used to train Lovable's proprietary models unless you're on a Business/Enterprise plan or have explicitly opted out. Identifiable personal data cannot be. For enterprise use or sensitive IP work, you should request the opt-out in writing.

\---

## 2\. Third-party AI providers — do they train on your data?

When you use the platform (not just the AI Gateway), your prompts are sent to third-party AI providers including OpenAI, Google Gemini, and OpenRouter. Lovable explicitly states: *"We do not control these providers' data practices, and you are responsible for reviewing their policies."*

This is a significant liability transfer. OpenAI's API (as opposed to ChatGPT) does not use inputs for training by default, but you need to verify each provider's current policy independently. OpenRouter routes to many different underlying models, which adds another layer of uncertainty.

**Verdict:** Lovable washes its hands of what happens once data hits the AI providers. If you submit sensitive IP or customer data as prompts, you need to review OpenAI, Google, and OpenRouter's policies separately. This is non-trivial if you're using the platform with proprietary business logic.

\---

## 3\. Data storage and location

* Primary hosting is on **Supabase** infrastructure. Lovable Cloud stores your apps, databases, files, and generated outputs there.
* Lovable is incorporated in Delaware, USA, with an EU entity in Stockholm (Lovable Labs Sweden AB).
* For EEA/UK/Swiss customers, transfers to the US are covered by EU Standard Contractual Clauses (SCCs), the EU-US Data Privacy Framework, and UK/Swiss addenda — all standard and legally sound mechanisms.
* Log data is retained for **90 days**.
* Customer data is deleted within **30 days** of account termination (backups may persist up to 90 days).
* Anonymized/aggregated data can be retained **indefinitely**.

**Verdict:** Data location is primarily US-based (via Supabase). The international transfer mechanisms are in order for EU/UK compliance. If your organization has strict data residency requirements, you'd need to confirm Supabase's specific region options with Lovable directly, as the documents don't specify.

\---

## 4\. "Service Data" — the grey zone

Both the Privacy Policy and the DPA define "Service Data" as telemetry, logs, usage metrics, and operational data. This is classified as data Lovable owns and processes as an **independent controller** — not subject to DPA restrictions.

The DPA (Section 9) explicitly allows Service Data to be used for *"training or tuning proprietary machine-learning models used to deliver the Services."* This is the key distinction: your identifiable Customer Personal Data cannot be used for training, but aggregated/de-identified usage patterns derived from your activity can be — and you cannot opt out of this as long as you're a customer.

\---

## 5\. Key risks summary

**High concern:**

* Prompts and Customer Data (non-PII) used for model training by default — opt-out required, not opt-in.
* No control over what third-party AI providers (OpenAI, Google, OpenRouter) do with your data once it passes through.
* Perpetual, royalty-free license on Customer Data (excluding PII) survives termination.

**Medium concern:**

* "Service Data" (de-identified usage, telemetry) can be used for ML training indefinitely with no opt-out right.
* Liability cap is limited to 12 months of fees paid — relatively standard but worth noting.
* Supabase data residency not specified — could matter for strict compliance requirements.

**Low concern / well-handled:**

* International transfer mechanisms (SCCs, DPF) are properly implemented.
* DPA explicitly prohibits PII use for model training.
* SOC 2 Type II and ISO 27001 accreditations maintained.
* 72-hour breach notification commitment.
* Sub-processor change notification (10–20 business days depending on which document you read — slight inconsistency there).

\---

## 6\. What to request from Lovable before signing

If you're doing this for a business evaluation, I'd recommend:

1. **Written confirmation of the training opt-out** for your account, or a Business plan DPA that includes it by default.
2. **Their current sub-processor list** from trust.lovable.dev (mentioned but not included here) — particularly which specific OpenAI/Google/OpenRouter agreements are in place.
3. **Confirmation of Supabase data region** if you have EU data residency requirements.
4. **Clarification on the 10 vs 20 business days** sub-processor notice period — the Privacy Policy says 10, the DPA says 20. Minor but worth aligning.
5. Their **SOC 2 Type II report** (available under NDA per the DPA, Section 5).

