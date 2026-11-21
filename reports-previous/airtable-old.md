# Airtable – Previous assessment (without the skill)

*Made with Claude in free-form conversation before the skill existed. Transcribed from the original rendered report; content unchanged.*

## Summary overview

|Item|Status|
|-|-|
|AI model training|Explicitly prohibited|
|Data residency|Enterprise Scale only|
|DPA available|Yes — must be executed|
|SCCs (GDPR)|EU + UK SCCs included|
|AI input/output retention|Enterprise: zero — Free/Team: 30 days|
|Breach notification|72 hours per DPA|

## Risk assessment

**Low — AI model training — explicitly prohibited**
AI Terms §5: Airtable will not use, or permit Third-Party AI Providers to use, Input, Output, or Customer Data to train generative AI models. Unconditional — no plan-tier carve-out.

**Low — Input/Output retention — zero for Enterprise or Business**
If on Enterprise Scale or Business: subprocessors cannot log, save, or retain Input/Output. Free/Team plans allow 30-day retention for safety/compliance moderation — confirm your plan tier.

**Medium — AI subprocessors — 8 third-party providers globally**
AWS, Google, IBM, OpenAI, Parallel Web, Reducto, Sampark, Vercel. Enterprise Scale customers with BAA/Health exhibit are excluded from some. Business/Enterprise admins can opt out individual providers via admin panel.

**Medium — Data residency — Enterprise Scale plan only**
EU and AU regions available, but only for Enterprise Scale. Base metadata, user/auth data, and Airtable analytics always remain in US regardless of region. Some extensions send data to third-party servers outside chosen region.

**Medium — Broad content licence in ToS §2.4**
ToS grants Airtable "irrevocable, transferable, sublicensable... right to access, use, copy, store, modify" Your Content for service provision and "any other purpose consistent with the Privacy Policy." The DPA, once executed, constrains this for personal data — but the ToS licence is broad for non-personal data.

**Medium — Usage data — free to use without restriction**
ToS §2.5: Airtable can use usage/analytics data freely for product development, analytics, and business purposes. Usage Data is explicitly excluded from the definition of Your Content, so DPA protections don't apply.

**High — DPA must be executed — it's not automatic**
The DPA is not self-executing. It requires a signed copy via airtable.com/dpaform. Without execution, GDPR Article 28 processor obligations and AI training prohibitions in the DPA context are unenforceable. The AI Terms training prohibition exists independently, but the DPA is essential for full data protection coverage.

**Medium — Liability cap — 12 months fees only**
ToS §14: aggregate liability capped at fees paid in the prior 12 months. Typical for SaaS; worth noting for risk acceptance if sensitive data is stored.

**Info — Sub-processor change notice — 10 business days only**
DPA §5.2: Airtable provides minimum 10 business days notice of new AI subprocessors, with a 10 business day objection window. Short lead time for procurement/legal review cycles.

## AI subprocessors (in-product AI only)

|Provider|Role|Location|
|-|-|-|
|Amazon Web Services|AI model provider|Global|
|Google LLC|AI model provider|Global|
|OpenAI LLC|AI model provider|USA|
|IBM|AI model provider|USA|
|Parallel Web Systems|AI-powered internet search|USA — excl. Enterprise+BAA|
|Reducto Inc|AI-powered data extraction|USA — excl. Enterprise+BAA|
|Sampark Inc|Integration auth layer / AI agents|USA — excl. Enterprise+BAA|
|Vercel Inc|AI web prototype generation|USA — excl. Enterprise+BAA|

## Recommended actions

1. **Execute the DPA immediately** visit airtable.com/dpaform. Without this, GDPR Article 28 obligations are not contractually binding.
2. **Confirm your plan tier** — Enterprise Scale or Business plan gets zero AI input/output retention and admin-level AI provider opt-out controls. Free/Team does not.
3. **Review AI provider opt-outs** in the admin panel — Enterprise Scale and Business admins can disable individual Third-Party AI Providers. Audit which are enabled for your workspaces.
4. **Enable data residency** if EU data is stored — available on Enterprise Scale only. Note: base metadata, user/auth data, and some extensions will always remain US-based regardless.
5. **Subscribe to subprocessor change notifications** — 10 business days notice is a short window. Subscribe via the form on airtable.com/company/subprocessors so your legal/procurement team can review changes in time.
6. **Assess the broad ToS content licence** with your legal team — the irrevocable, sublicensable licence in §2.4 is constrained by the DPA for personal data, but non-personal business data in Airtable (e.g. process data, workflow data) falls under the broader ToS terms.

