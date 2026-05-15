# Procurement Agent Skills

Universal, portable procurement skills repository for a personal AI procurement agent.

This repository contains structured procurement skills, reusable methodologies, output formats and company profiles for use across different employers, industries and procurement contexts.

## Purpose

The goal of this repository is to create a reusable skill library for a procurement agent that can support:

- RFQ / RFP preparation
- Supplier quotation comparison
- TCO analysis
- Supplier negotiation preparation
- Category strategy
- Supplier scorecards
- Contract and commercial term review
- Compliance checks
- Management reporting

## Core principle

The agent is intentionally employer-independent.

Company-specific knowledge must be stored in `company-profiles/`, while universal procurement logic must stay in `skills/` and `global/`.

This makes the agent portable when changing employer or industry.

## Repository structure

```text
procurement-agent-skills/
├── README.md
├── skills.yaml
├── global/
│   ├── SYSTEM_PRINCIPLES.md
│   ├── OUTPUT_FORMATS.md
│   ├── SAFETY_RULES.md
│   └── PROCUREMENT_TERMS.md
├── company-profiles/
│   ├── template-company-profile.md
│   └── current-employer-profile.md
└── skills/
    ├── rfq-rfp/
    │   └── SKILL.md
    ├── quotation-comparison/
    │   └── SKILL.md
    ├── tco-analysis/
    │   └── SKILL.md
    ├── negotiation-brief/
    │   └── SKILL.md
    ├── category-strategy/
    │   └── SKILL.md
    └── management-reporting/
        └── SKILL.md
```

## Skill philosophy

Every skill must:

1. Define when it should be used.
2. List required inputs.
3. Describe the analysis process.
4. Define the output format.
5. Separate facts, assumptions, risks and recommendations.
6. Be reusable across companies.
7. Avoid confidential employer-specific assumptions unless provided through a company profile.

## Recommended first use cases

Start with these workflows:

1. Compare supplier offers.
2. Prepare RFQ emails and supplier response matrices.
3. Calculate total cost impact.
4. Prepare negotiation brief.
5. Create management-ready procurement summary.
