# saas-ai-due-diligence
A Claude skill for assessing SaaS vendors’ data protection and AI governance from their own documents, producing a standardized traffic-light report with quote-anchored findings.

# SaaS AI Due Diligence – Claude Skill

A Claude skill for assessing SaaS vendors' data protection and AI governance from their own documents, producing a standardized traffic-light report with quote-anchored findings.

This repository is an appendix to a bachelor's thesis, *Käyttääkö toimittaja dataamme? Tekoälyavusteinen arviointityökalu SaaS-sovellusten käyttöönottoon* (Haaga-Helia University of Applied Sciences, 2026). Release [`v1.0`](../../tree/v1.0) corresponds to the submitted thesis.

## What the skill does

The skill evaluates a SaaS vendor against seven fixed criteria using the vendor's own documents (DPA, Terms of Service, privacy policy, AI policy, subprocessor list and trust center):

| # | Criterion |
|---|---|
| C1 | No training on customer data |
| C2 | Retention and deletion |
| C3 | Data location and jurisdiction |
| C4 | Subprocessor list |
| C5 | AI risk classification |
| C6 | AI models and providers |
| C7 | Certifications |

Each criterion gets a traffic light (🟢 met, 🟡 unclear or not found, 🔴 not met), and every verdict is anchored to a verbatim quote from the vendor's documents so the reader can verify it. The report has two layers: a one-page summary for decision makers and an evidence appendix per criterion. Reports can be produced in Finnish or English.

## Repository contents

```
├── saas-ai-due-diligence/
│   └── SKILL.md            # The skill itself
├── reports-skill/          # Reports produced with the skill
└── reports-previous/       # Earlier assessments made without the skill (for comparison)
```

The reports in `reports-previous/` were made with Claude through free-form conversation before the skill existed. They are included for the comparison in the thesis (chapter 4) and have been anonymized.

## Using the skill

Download the `saas-ai-due-diligence` folder and add it to Claude as a skill. See Anthropic's [skills repository](https://github.com/anthropics/skills) for more on how skills work. Start by asking Claude to assess a vendor and provide the vendor's documents; the skill asks for the report language and format first.

## Limitations

- The skill assesses the vendor's documents, not whether the vendor actually acts according to them.
- It does not assess the customer's own use case, which can affect the EU AI Act risk class.
- Each report reflects the documents at the time of assessment. Vendor terms change, so reassess when they do.
- The output is produced by a language model and must be reviewed by a human. It is decision support, not legal advice.

## Notes on the reports

- Reports were produced at different times and some with an earlier development version of the skill, so minor structural differences exist.
- Quotes in the reports are taken from the vendors' public documents, and the rights to them belong to the respective vendors. The license below covers the skill and the original text of the reports.

## License

[MIT](LICENSE)
