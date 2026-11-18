---
name: saas-ai-due-diligence
description: >-
  Assess a SaaS vendor's data-protection, security, and AI-governance posture
  from the vendor's own documents (DPA, Terms of Service, privacy policy, AI
  policy, subprocessor list, trust center) and produce a standardized
  procurement-decision report with a per-criterion and overall traffic-light
  verdict. Use this whenever the user wants to evaluate, vet, review, or run
  due diligence on a SaaS tool, AI vendor, or third-party application before
  adoption — including phrasings like "is this vendor safe to use", "check this
  DPA", "review this tool's privacy terms", "does this SaaS train on our data",
  or "assess this AI product". Trigger even when the user just uploads vendor
  documents and asks what to make of them.
---

# SaaS AI Due Diligence

Evaluate a SaaS vendor against seven fixed criteria and produce a standardized
report. The report's value is an honest, source-anchored verdict a busy decision
maker can act on — never a rubber stamp and never invented reassurance.

## Scope (state this, don't drift from it)

- Assess **the vendor and its product** — not the customer's use case.
- The primary interest protected is the customer's **business data and trade
  secrets**; personal data is the subset that GDPR governs.
- This is a **decision-support tool, not legal advice**.
- General purpose — not industry specific.

## Step 1 — Ask the report language AND format FIRST

Before anything else, ask both:

> Report language / Raportin kieli: **(1) Suomi  (2) English**
> Report format / Raportin muoto: **(A) Markdown  (B) ASCII (plain text)**

The whole skill runs identically regardless — only the output language, the fixed
template text, and the rendering change. Criteria, thresholds, and logic are
language- and format-neutral. Use the fixed FI/EN term pairs in the Glossary so
the two language versions never drift apart.

**Format:** Markdown renders cleanly in chat and documents (tables, headings);
ASCII (the plain-text boxed layout shown in the templates) survives copy-paste
into any system where formatting breaks. Same content either way. The templates
below are shown in ASCII; for Markdown, render Page 1 criteria as a table and each
appendix block as a short heading + labeled lines.

**Quotes are never translated.** The `Lainaus` / `Quote` field always keeps the
document's original wording (usually English), even in a Finnish report.
Translating a quote would break the verbatim anchoring that keeps the report
honest (see Anti-hallucination rules).

## Step 2 — Confirm the input documents

Ask the user to provide what they have. The DPA is the single most important
document — it alone carries several criteria, and its absence collapses the
reliability of the whole assessment.

| Document | Covers |
|---|---|
| DPA (Data Processing Agreement) + subprocessor annex | C1, C2, C3, C4 |
| Terms of Service | C1, C2 |
| Privacy policy | C2 |
| AI policy / product documentation | C1, C5, C6 |
| Subprocessor list (if not in the DPA) | C4, C6 |
| Trust center page (screenshot / export / URL) | C7 |

A trust-center screenshot is sufficient evidence for C7. Certificates being
behind a "Request access" gate is **not** a gap — it is standard industry
practice.

Do not block on missing documents. Note what is missing and proceed — a missing
document simply drives the relevant criteria to Yellow ("could not verify") and
generates a "to obtain" item.

## Step 3 — Evaluate each criterion

For each of C1–C7, find the relevant wording in the provided documents and assign
a traffic-light state using the acceptance thresholds below. The core discipline:
**documents are not binary and do not use standard language.** "We do not use
customer data to train our models" and "Customer Content may be processed to
improve our services" mean opposite things while sharing no keywords. Read for
meaning against the threshold, not for a keyword match.

### Traffic-light logic (every criterion)

- 🟢 **Green** — requirement met in clear, unambiguous wording. The user can rely
  on it.
- 🟡 **Yellow** — mentioned vaguely / partially / conditionally, OR not found at
  all. The user cannot rely on it as-is; demand clarification.
- 🔴 **Red** — the document proves the requirement is NOT met.

The Yellow/Red distinction matters: "the vendor does the wrong thing" (Red) and
"we can't tell" (Yellow) are different, and only the latter produces a
"to obtain a document" recommendation.

### Assess the strictest applicable tier, then flag tier differences in bold

Protections often depend on the plan: a DPA, no-training commitment, or data-
residency option may apply only to Business/Enterprise tiers, while Free/Pro/Team
users get weaker terms. Do not ask which tier the user is on. **Always assess
against the strictest (usually the consumer/default) tier** — the weakest terms a
customer could be subject to — so the verdict is never falsely reassuring. Then,
wherever a higher tier changes the outcome, say so explicitly **in bold** in the
Finding and in the recommendation, e.g. "**On Business/Enterprise the DPA prohibits
this, so C1 would be Yellow rather than Red.**" This gives the reader both the
safe-default verdict and the path to improve it, without a tier question up front.

## The seven criteria and acceptance thresholds

### C1 — No training on customer data
**Requirement:** The vendor does not use customer data (prompts, uploaded files,
generated content) to train or develop its own or third-party AI models.
- 🟢 Unconditional no-training commitment **AND** no mention of aggregated/
  anonymized data being used for analytics or any secondary purpose.
- 🟡 Tier-conditional ("Enterprise only") · carve-out for aggregated/de-identified
  data used for **analytics/service improvement** (not training) · vague language ·
  silence · "training" and "improving" blurred together. **Any** mention of
  aggregated-data analytics use drops to Yellow even if model training is
  separately prohibited. A broad but standard service-provision content license
  ("to provide, maintain, improve, or optimize the Services") that is NOT model
  training also lands here — not Red.
- 🔴 The critical trigger: customer data — or data derived from it — is or may be
  used to **train or develop AI models** (the vendor's or a third party's). This
  includes: training that is **on by default with an opt-out** (training happens
  unless the customer acts → Red, because it happens by default); a broad license
  specifically to develop/train models; and **training on de-identified/aggregated
  data derived from customer data** (analytics on such data is Yellow, but training
  on it is still training → Red). Ordinary service-improvement language that is not
  training is not enough for Red.
- **Note when a verdict rests on a standard clause.** A broad service-provision
  license is common SaaS boilerplate, not an unusual red flag. When a Yellow (or
  Red) rests on such a standard clause, say so in the Finding ("this is a typical
  SaaS content license") so the reader can weigh it correctly and isn't misled
  into treating routine wording as an alarm. This principle applies to every
  criterion, not just C1.
- **Cross-check:** the no-training commitment must extend to every model provider
  found in C6.

### C2 — Retention and deletion
**Requirement:** A defined retention period and a deletion (or return) mechanism
on contract termination.
- 🟢 Explicit deletion commitment on termination **AND** a concrete deadline.
- 🟡 No deadline · deletion only on request · backups excluded or unaddressed ·
  vague ("as long as necessary") · silence.
- 🔴 Right to retain indefinitely; no deletion commitment.
- **Cross-check:** the deletion obligation must extend to subprocessors (C4, GDPR
  Art. 28(4)).

### C3 — Data location and jurisdiction
**Requirement:** Data stored and processed in the EU/EEA, with no exposure to
non-EU jurisdictional access.
- 🟢 Explicit EU/EEA commitment **AND** no jurisdictional back door (e.g. EU-owned
  entity or an EU data-residency guarantee).
- 🟡 EU location but parent company outside the EU (e.g. US-owned → US CLOUD Act
  exposure even with EU hosting) · transfers permitted under SCCs/adequacy ·
  partially defined (support/logs/backups elsewhere) · vague ("global
  infrastructure") · silence.
- 🔴 Data outside EU/EEA with no valid mechanism; unrestricted transfer right.
- **Always record** the vendor's ownership and headquarters jurisdiction — this
  determines CLOUD Act exposure and is otherwise invisible.
- **Cross-check:** depends on C6 — a non-EU model provider takes data out of the
  jurisdiction with each model call, even if the vendor itself is in the EU.

### C4 — Subprocessor list
**Requirement:** A complete subprocessor list plus a change-notification process.
- 🟢 Complete list (names, role, location) **AND** advance-notification process
  with a right to object.
- 🟡 List without a notification process · notification without a right to object
  · incomplete list (location/role missing) · vague ("trusted partners") · silence.
- 🔴 Right to use subprocessors without disclosure or notice.
- **Structural hub:** feeds C3 (jurisdiction), C6 (model providers), C2 (deletion
  down the chain). A gap here weakens the reliability of those criteria.

### C5 — AI risk classification
**Requirement:** The product's AI functionality is classified under the EU AI Act
and the resulting obligations are handled.
- 🟢 Risk class explicitly identified **AND** the class's obligations handled/
  documented.
- 🟡 Class not stated · classification unclear/contestable · high-risk without any
  conformity evidence · silence.
- 🔴 Prohibited use case; clearly high-risk with no evidence whatsoever.
- **Note:** high risk ≠ Red. This measures identification and management of
  obligations, not the risk level itself. The customer's use context can raise the
  class — record this in prose.
- **Cross-check:** depends on C6.

### C6 — AI models and providers (an inventory criterion)
**Requirement:** All AI models the product uses, and their providers, identified.
- 🟢 Complete inventory: every model + provider named (e.g. Azure OpenAI, AWS
  Bedrock, Anthropic, self-hosted), GPAI-vs-native clear, provider location ideally
  given.
- 🟡 Partial disclosure · provider named but model/role unclear · GPAI-vs-native
  open · contradictory documentation · silence despite evident AI functionality.
- 🔴 Data sent to undisclosed third-party models AND explicit refusal to disclose;
  or active denial of AI use contrary to fact.
- **Analytical center:** its output (the list of models + providers) feeds C1, C3,
  C4, C5. Red is rarer here than elsewhere — expected for an inventory criterion.
  Record the models/providers found as a short list; that list is C6's real output,
  more valuable than the color alone.
- **Proactive request:** if the subprocessor list (C4) is mentioned but its
  contents are not visible, request the full list explicitly — it resolves C4 AND
  C6 at once (model providers are subprocessors and should appear on it). When a
  single document would lift two or more criteria, say so in the recommendation
  so the user knows which one file to chase first.

### C7 — Certifications
**Requirement:** Valid independent audits (ISO 27001, SOC 2, ISO 42001).
- 🟢 At least one relevant, valid, in-scope certification, verifiable OR reliably
  listed (trust center with type + dates, even if the file is gated). Strongest:
  ISO 27001 + SOC 2 Type II (+ ISO 42001 for an AI product).
- 🟡 SOC 2 Type I only · mention without verifiability · scope narrow/unclear ·
  validity unclear · "compliant/aligned" without certification (self-assessment).
- 🔴 No independent certification at all; expired or out-of-scope certificates.
- **Note:** a badge ≠ a verified certificate. GDPR/CCPA/DPF "compliant" badges are
  self-declarations and do not count toward the verdict. Being behind a gate is not
  a gap.
- **Cross-check:** a reliability multiplier for the other criteria — an audit that
  covers them strengthens the contractual promises in C2/C3/C4.

## Overall verdict

Derive the overall traffic light directly from the criteria states — no weighting,
no arbitrary thresholds, and no numeric counter:

- 🟢 all criteria Green
- 🟡 at least one Yellow, no Red
- 🔴 at least one Red

Show the overall verdict as a single traffic light (e.g. `🔴 RED`). Do not add a
tally like "2 confirmed · 1 gap · 4 could not verify" or a "criteria assessable:
n/7" figure — the per-criterion colors already show the distribution at a glance,
and a count of files or colors tends to mislead (it conflates "we lacked a
document" with "the terms are weak"). The recommendations carry what is missing or
weak; the colors carry the balance. Colors + recommendations are the whole story.

## Anti-hallucination rules (critical — this is what keeps the report honest)

- **Anchor every verdict directly to a quote.** No source, no verdict.
- **When information is absent, leave the fields empty (—). Never fill them with
  inferred content.** An empty Source + Quote means the criterion is 🟡
  "could not verify" by definition.
- **Quotes are verbatim and in the original language.** A long quote may be
  trimmed with `[…]`, but never paraphrased and never translated — either would
  destroy the anchoring. This holds in the Finnish report too.
- **The report speaks only about the vendor and the documents — never about
  itself.** Never reference the skill's own thresholds, rules, colors-as-rules, or
  the process of assessing ("the critical trigger we set", "this is Red per our
  calibration", "the threshold for Green is…", "as this skill defines it"). State
  the finding as a fact about the vendor and cite the document: not "this is Red
  because our rule says default-on training is Red", but "training is on by default
  and requires the customer to opt out." The reader must never see the machinery.
  Comparisons to other vendors assessed in other sessions also do not belong in a
  report — each report stands alone.

## Report structure

Two layers. Page 1 is the decision layer (fits on one page, scannable). The
appendix is the evidence layer (1–2 pages). Use the templates below verbatim,
translating only the labels per the chosen language.

### Page 1 template (English shown; use the FI labels from the Glossary for Suomi)

```
SaaS AI Due Diligence Report
Vendor: [name]  |  Assessment date: [date]

OVERALL ASSESSMENT:  [🟢/🟡/🔴] [GREEN/YELLOW/RED]

Scope: This assessment covers the vendor based on the documents provided, not the
customer's use case. Assessed against the strictest (default) tier; tier
differences are flagged in bold below. Not legal advice.

CRITERIA
#    Criterion                        Color   Finding (one line)
C1   No training on customer data     [ ]     [...]
C2   Retention and deletion           [ ]     [...]
C3   Data location and jurisdiction   [ ]     [...]
C4   Subprocessor list                [ ]     [...]
C5   AI risk classification           [ ]     [...]
C6   AI models and providers          [ ]     [...]
C7   Certifications                   [ ]     [...]

RECOMMENDATIONS (before the procurement decision)
• [criterion]: [what to obtain / negotiate]   (one line per Yellow/Red)

Notices: The EU AI Act applies in phases — verify current obligations. As a
deployer you may have your own AI Act obligations; assess your use case separately.
```

### Appendix block template (one per criterion)

```
──────────────────────────────────────────────
C[n] — [Criterion name]                     [🟢/🟡/🔴]
──────────────────────────────────────────────
Source:     [document + section, or —]
Quote:      [verbatim, original language, or —]
Finding:    [how the wording was read against the requirement]
To obtain:  [Yellow/Red only: what to obtain or negotiate]
```

Appendix "To obtain" lines and the Page-1 recommendations are one-to-one. Green
blocks have no "To obtain" line.

## Standard notices (append to every report)

- **Deployer responsibility:** The EU AI Act places obligations on the deployer
  too. Even a compliant product can be deployed in a way that creates obligations
  for your organization or raises the use case's risk class. Assess your intended
  use separately.
- **Not legal advice.**
- **The EU AI Act applies in phases** — obligations and application dates must be
  verified against a current source.

## Glossary (fixed FI/EN pairs — use consistently)

| Suomi | English |
|---|---|
| SaaS AI Due Diligence -arvio | SaaS AI Due Diligence Report |
| Kokonaisarvio | Overall assessment |
| Vahvistettu / Puute / Ei voitu vahvistaa | Confirmed / Gap / Could not verify |
| Vihreä / Keltainen / Punainen | Green / Yellow / Red |
| Rajaus | Scope |
| Dokumenttien kattavuus | Document coverage |
| Suositukset | Recommendations |
| Lähde / Lainaus / Tulkinta / Hankittava | Source / Quote / Finding / To obtain |
| Kriteerit | Criteria |
| C1 Ei koulutuskäyttöä | C1 No training on customer data |
| C2 Säilytys ja poisto | C2 Retention and deletion |
| C3 Datan sijainti ja jurisdiktio | C3 Data location and jurisdiction |
| C4 Alikäsittelijälista | C4 Subprocessor list |
| C5 AI-riskiluokka | C5 AI risk classification |
| C6 AI-mallit ja tarjoajat | C6 AI models and providers |
| C7 Sertifioinnit | C7 Certifications |
| Käyttöönottaja (deployer) | Deployer |
| Ei oikeudellinen lausunto | Not legal advice |
