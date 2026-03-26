# Estonian Public Sources Skill

Use this repository to get evidence-based answers from official Estonian public sources about how government works, what decisions were made, who was involved, and what changed over time.

## Usage

After installing the plugin, use the explicit slash command to query Estonian public sources:

```
/estonia-public-sources:query millised keskkonnaload on Tallinnale väljastatud?
```

```
/estonia-public-sources:query procurement contracts for IT services in 2025
```

```
/estonia-public-sources:query äriregistri andmed ettevõtte X kohta
```

The slash command routes your question to the right official source among 133 available datasets and executes the retrieval workflow.

The plugin may also activate automatically when Claude detects a relevant question, but the slash command is the most reliable way to ensure it is used.

## What You Get

- Fast routing to the right official source for policy, law, spending, operations, registries, and oversight questions.
- Reusable source-specific workflows that produce structured, citation-ready outputs.
- Human-guided fallback steps when a source requires manual export, login, or anti-bot interaction.

## Project Goal

Cover, via reusable source skills, any information that can be found from public and official Estonian sources about:

- How government operates now.
- How government has operated historically.
- Context data needed to interpret government operations.

Sources include both APIs/datasets and official websites/registries.

## Structure

```text
.
├── AGENTS.md
├── SKILL.md
├── SOURCE_MAP.md
├── README.md
├── skills/
│   └── query/
│       └── SKILL.md        ← slash command entry point
└── sources/
    ├── <source-skill-slug-1>/
    │   └── SKILL.md
    ├── <source-skill-slug-2>/
    │   └── SKILL.md
    └── ...
```

## Rules

- The root `SKILL.md` is the router skill.
- `SOURCE_MAP.md` is the fast lookup map for selecting the right source.
- Each source skill lives in its own folder under `sources/`.
- Each source folder has its own `SKILL.md`.
- Any source-specific scripts/examples stay inside that source folder.

## Source Index

- `sources/abis-governance`
- `sources/agricultural-subsidies-pria`
- `sources/aircraft-register`
- `sources/animal-disease-control`
- `sources/animal-keeper-registering`
- `sources/aviation-occurrence-reporting`
- `sources/aviation-safety-reports`
- `sources/bank-of-statistics`
- `sources/border-management-operations`
- `sources/business-register-open-data`
- `sources/civil-service-pay-governance`
- `sources/communicable-disease-bulletins`
- `sources/competition-authority-decisions`
- `sources/construction-register`
- `sources/consumer-technical-regulator-decisions`
- `sources/court-information-system`
- `sources/court-proceedings-data`
- `sources/court-system-statistics`
- `sources/crime-policy-statistics`
- `sources/criminal-records-database`
- `sources/cultural-heritage-register`
- `sources/cyber-incidents-cert-ee`
- `sources/data-protection-enforcement`
- `sources/defence-policy-budget-documents`
- `sources/defence-public-opinion-surveys`
- `sources/digital-government-studies`
- `sources/drone-operator-registration`
- `sources/e-file-statistics`
- `sources/e-notary`
- `sources/e-residency-dashboard`
- `sources/e-ship-register-rik`
- `sources/economic-activities-register-mtr`
- `sources/education-data`
- `sources/election-results-data`
- `sources/energy-data`
- `sources/environmental-charge-statistics`
- `sources/environmental-data`
- `sources/environmental-permit-decisions`
- `sources/estonia-2035-action-plan`
- `sources/etis-research-information-system`
- `sources/eu-funded-projects`
- `sources/fairway-dues`
- `sources/financial-supervision-decisions`
- `sources/food-business-approvals`
- `sources/food-supervision`
- `sources/forest-register`
- `sources/geospatial-open-data`
- `sources/government-action-programme`
- `sources/government-journal-records`
- `sources/government-office-document-register`
- `sources/government-session-agendas`
- `sources/health-insurance-fund-reports`
- `sources/health-statistics`
- `sources/health-supervision-decisions`
- `sources/health-welfare-open-data`
- `sources/healthcare-professionals-register`
- `sources/internal-security-annual-reviews`
- `sources/kultuurkapital-grants-data`
- `sources/labour-inspectorate-enforcement`
- `sources/labour-inspectorate-statistics`
- `sources/land-register-kinnistusraamat`
- `sources/language-law-supervision`
- `sources/legal-acts-data`
- `sources/legislation-workflow-eis`
- `sources/lobby-meetings`
- `sources/local-council-volis`
- `sources/local-government-finance-benchmarks`
- `sources/marital-property-register`
- `sources/maritime-economy-statistics`
- `sources/medicines-agency-statistics`
- `sources/medicines-register`
- `sources/mfa-development-cooperation-aid`
- `sources/mfa-sanctions`
- `sources/migration-management`
- `sources/ministry-document-registries`
- `sources/muis-open-data`
- `sources/national-archives-governance-records`
- `sources/official-notices`
- `sources/officials-interest-declarations`
- `sources/ombudsman-opinions`
- `sources/open-data`
- `sources/party-funding-data`
- `sources/patent-and-trademark-registers`
- `sources/planning-decisions`
- `sources/plant-protection-supervision`
- `sources/police-operational-statistics`
- `sources/political-party-membership`
- `sources/president-decisions-decrees`
- `sources/prison-annual-reviews`
- `sources/procurement-data`
- `sources/procurement-review`
- `sources/procurement-state-supervision`
- `sources/prosecution-statistics`
- `sources/public-consultations-feed`
- `sources/public-consultations-osale`
- `sources/public-finance-data`
- `sources/public-sector-it-systems-riha`
- `sources/public-sector-statistics-fin`
- `sources/rescue-incident-data`
- `sources/riigikogu-agendas`
- `sources/riigikogu-draft-laws`
- `sources/riigikogu-open-data`
- `sources/riigikogu-stenograms`
- `sources/riigiteataja-draft-acts`
- `sources/ship-registers`
- `sources/social-insurance-statistics`
- `sources/state-aid-register`
- `sources/state-assets-register`
- `sources/state-audit-reports`
- `sources/state-ownership-data`
- `sources/state-port-register`
- `sources/state-services-catalog`
- `sources/statistics-api`
- `sources/strategic-development-documents-registry`
- `sources/succession-register`
- `sources/supreme-court-judgments`
- `sources/tallinn-council-documents`
- `sources/tallinn-legal-acts-register`
- `sources/tallinn-open-data`
- `sources/tartu-document-register`
- `sources/tartu-open-data`
- `sources/tartu-webaktid`
- `sources/tax-customs-data`
- `sources/tax-public-inquiries`
- `sources/tourism-information-system-dataset`
- `sources/transport-traffic-data`
- `sources/unemployment-statistics`
- `sources/vaccination-statistics`
- `sources/vehicle-background-check`
- `sources/vital-statistics-procedures`
- `sources/weather-data`
- `sources/work-dispute-committee`
- `sources/x-road-usage-statistics`
