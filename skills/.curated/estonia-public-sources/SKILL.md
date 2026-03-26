---
name: estonia-government-public-sources
description: "Query 133 Estonian official public sources. Covers äriregister, ehitisregister, kinnistusraamat, maa-amet, statistikaamet, haigekassa, KOTKAS, keskkonnaload, riigihanked, riigiteataja, riigikogu, ametlikud teadaanded, PRIA, and more. Routes to the right source and executes retrieval workflows."
metadata:
  distribution:
    tier: curated
    publish_anthropic: true
    plugin_name: estonia-public-sources
    plugin_version: 1.1.0
    plugin_author: Taivo Marketplace
---

# Estonia Government Public Sources

## Routing workflow
1. Classify the user request (parliament, government operations, justice, business/asset registry, finance, municipal, etc.).
2. Use the high-level index below to narrow to a source family.
3. Open `SOURCE_MAP.md` for precise source-to-question routing.
4. Open the specific `sources/<source-name>/SKILL.md` and execute that workflow.

## High-Level Index
- Core national statistics and macro context:
  `sources/statistics-api`, `sources/bank-of-statistics`, `sources/public-finance-data`, `sources/public-sector-statistics-fin`, `sources/tax-customs-data`
- Parliament, lawmaking, and legal texts:
  `sources/riigikogu-open-data`, `sources/riigikogu-draft-laws`, `sources/legislation-workflow-eis`, `sources/legal-acts-data`
- Government operations and transparency records:
  `sources/ministry-document-registries`, `sources/government-office-document-register`, `sources/government-action-programme`, `sources/estonia-2035-action-plan`, `sources/strategic-development-documents-registry`, `sources/lobby-meetings`, `sources/official-notices`
- Executive and election decision records:
  `sources/president-decisions-decrees`, `sources/election-results-data`
- Oversight, supervision, and enforcement:
  `sources/state-audit-reports`, `sources/ombudsman-opinions`, `sources/financial-supervision-decisions`, `sources/data-protection-enforcement`, `sources/language-law-supervision`, `sources/mfa-sanctions`
- Registries, ownership, and organization context:
  `sources/business-register-open-data`, `sources/land-register-kinnistusraamat`, `sources/economic-activities-register-mtr`, `sources/state-ownership-data`
- Public spending, subsidies, and projects:
  `sources/procurement-data`, `sources/party-funding-data`, `sources/agricultural-subsidies-pria`, `sources/eu-funded-projects`, `sources/kultuurkapital-grants-data`, `sources/mfa-development-cooperation-aid`, `sources/civil-service-pay-governance`
- Procurement oversight and review:
  `sources/procurement-review`, `sources/procurement-state-supervision`
- Justice and internal security operations:
  `sources/court-proceedings-data`, `sources/court-system-statistics`, `sources/prosecution-statistics`, `sources/police-operational-statistics`, `sources/internal-security-annual-reviews`
- Health, welfare, and labor operations:
  `sources/health-statistics`, `sources/health-supervision-decisions`, `sources/social-insurance-statistics`, `sources/unemployment-statistics`
- Spatial, environment, and infrastructure:
  `sources/geospatial-open-data`, `sources/planning-decisions`, `sources/construction-register`, `sources/transport-traffic-data`
- Municipal and local-government sources:
  `sources/local-council-volis`, `sources/tallinn-open-data`, `sources/tallinn-council-documents`, `sources/tartu-document-register`
- Digital-state and service delivery context:
  `sources/public-sector-it-systems-riha`, `sources/state-services-catalog`, `sources/x-road-usage-statistics`, `sources/digital-government-studies`, `sources/e-residency-dashboard`, `sources/tourism-information-system-dataset`
- Justice execution and registry operations:
  `sources/e-file-statistics`, `sources/criminal-records-database`, `sources/prison-annual-reviews`, `sources/crime-policy-statistics`
- Labour, population, and civil procedures:
  `sources/labour-inspectorate-statistics`, `sources/labour-inspectorate-enforcement`, `sources/work-dispute-committee`, `sources/migration-management`, `sources/vital-statistics-procedures`
- Civil and property-rights registries:
  `sources/marital-property-register`, `sources/succession-register`, `sources/vehicle-background-check`, `sources/forest-register`
- Transport, maritime, and aviation registries:
  `sources/aircraft-register`, `sources/ship-registers`, `sources/state-port-register`, `sources/e-ship-register-rik`, `sources/aviation-occurrence-reporting`
- Health financing and medicine-system reporting:
  `sources/health-insurance-fund-reports`, `sources/medicines-agency-statistics`, `sources/animal-keeper-registering`
- Public health surveillance and professional registries:
  `sources/communicable-disease-bulletins`, `sources/vaccination-statistics`, `sources/healthcare-professionals-register`
- Food, plant, and environmental supervision:
  `sources/food-supervision`, `sources/food-business-approvals`, `sources/plant-protection-supervision`, `sources/animal-disease-control`, `sources/environmental-charge-statistics`
- Border and migration governance:
  `sources/border-management-operations`, `sources/migration-management`, `sources/vital-statistics-procedures`
- Maritime, aviation, and transport regulation detail:
  `sources/maritime-economy-statistics`, `sources/fairway-dues`, `sources/drone-operator-registration`, `sources/aviation-safety-reports`
- Civil justice and legal service systems:
  `sources/e-notary`, `sources/court-information-system`, `sources/patent-and-trademark-registers`
- Education, research, and culture systems:
  `sources/education-data`, `sources/etis-research-information-system`, `sources/muis-open-data`
- Defence and security policy context:
  `sources/defence-public-opinion-surveys`, `sources/defence-policy-budget-documents`

## Retrieval preferences

- Prefer `curl`/`wget` on direct URLs over browser navigation.
- If the source has an API, use it directly.
- Only fall back to browser/UI when the data is truly UI-only.
- If a source requires login/captcha/export, guide the user through exact steps, then continue from their provided files.

## Output requirements

- Cite exact source URL where data was retrieved.
- Include retrieval timestamp.
- Preserve original field names from the source.
- Separate facts from interpretation.
