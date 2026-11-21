# Miro – Previous assessment (without the skill)

*Made with Claude in free-form conversation before the skill existed. Transcribed from the original rendered report; content unchanged.*
*Assessment date: [date]*

## Overview

| Item | Value |
|---|---|
| Vendor | RealtimeBoard Inc. dba Miro |
| Miro role | Data Processor |
| Your role | Data Controller |
| DPA effective | Sep 17, 2024 |
| AI terms effective | Jul 17, 2024 |
| Governing law (ToS) | California, USA |

## Risk assessment by area

**Low — Data transfer mechanisms**
Covered by EU-US DPF certification + EU SCCs (Module 2/3) + UK Addendum + Swiss DPA. Dutch law governs SCCs. Multiple fallback mechanisms if DPF is invalidated.

**Medium — Sub-processor management**
General authorization granted (§3.1). You must actively subscribe to change notifications — not automatic. 30-day objection window. Miro retains final decision on sub-processor use.

**Medium — Audit rights**
Primary reliance on Miro-provided reports and certifications (§7.1). Third-party audits only permitted after confirmed Security Incident or regulator requirement. 30-day notice + Customer bears cost.

**Attention — AI training opt-out (Enterprise)**
Enterprise/MCA customers must give explicit consent before Miro uses Input/Output for model training. Consent is withdrawable. However, this requires active verification — the default position if you don't check your plan type is unclear.

**Attention — AI training opt-out (non-Enterprise)**
Free/Starter/Business plans: Miro may use Input/Output for AI training unless you object. Opt-out is available but not the default. If on these tiers, explicit opt-out action required.

**Medium — Breach notification timeline**
DPA says "without undue delay" — no specific hour SLA defined for customer notification. Supplier DPA (for Miro's own vendors) requires 48 hours, but this stricter standard doesn't flow up to customers.

**Low — GDPR / UK GDPR compliance**
Appropriate legal basis, SCC modules correctly assigned per controller/processor role. DPIA assistance committed. Data subject rights cooperation confirmed.

**Medium — Liability limitations**
Liability capped at fees paid in prior 12 months. Consequential/indirect damages excluded. AI infringement claims explicitly excluded from Miro's indemnification obligations.

**Medium — Prohibited data**
GDPR special category data, PHI/HIPAA, PCI DSS, government IDs explicitly prohibited. Customer is solely responsible for ensuring users don't submit prohibited data. No technical enforcement by Miro.

**Low — Data deletion**
On request or termination. 30-day export window post-termination. Written deletion confirmation available on request. Back-up copies isolated and not further processed.

## AI features — key positions

**What Miro can do with your AI inputs/outputs**
- Use to provide the service (always)
- Improve AI features / fine-tune models (consent-gated on Enterprise)
- Assigns you perpetual royalty-free licence if consent given
- Removes "direct identifiers" before training use
- Outputs may be identical across customers — no exclusivity

**What Miro won't warrant for AI outputs**
- Accuracy, completeness or fitness for purpose
- That output doesn't incorporate third-party content
- IP non-infringement of outputs
- AI IP claims excluded from Miro indemnity
- Customer solely responsible for input content

## Action items for your organisation

- **Confirm your plan tier.** AI training consent/opt-out mechanism differs significantly between Enterprise (MCA) and all other plans. Verify whether you are under a Master Cloud Agreement.
- **Subscribe to sub-processor change notifications.** This is not automatic — you must opt in at the URL in §3.3. Without this, you forfeit your 30-day objection window.
- **Review the live sub-processor list.** Check miro.com/static/legal/Miro-Current-Subprocessors-List.pdf and assess any sub-processors in high-risk jurisdictions or sensitive data functions.
- **Communicate prohibited data rules to users.** Miro places full responsibility on Customer to prevent GDPR special categories, PHI, PCI, and government ID data from being submitted. Consider a policy and user guidance.
- **Request SOC 2 Type II report.** Exhibit 2 references the Security Policy but contains no specific technical controls inline. Request the current SOC 2 report and ISO 27001 cert from your account team (typically under NDA).
- **Clarify breach notification SLA.** "Without undue delay" is vague. Negotiate a specific timeline (72 hours is the GDPR standard) in a supplemental agreement or via your enterprise terms if on MCA.
