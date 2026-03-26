---
name: election-results-data
description: Retrieve election outcome datasets and National Electoral Committee decision records from valimised.ee, with legal-reference linking to Riigi Teataja.
---

# Election Results and VVK Decisions

## Use when
- You need election results/open-data files.
- You need National Electoral Committee (VVK) decision records and legal references.

## Avoid when
- You need parliamentary voting behavior (use Riigikogu sources).

## Inputs
- Election type/year.
- Whether to include VVK decision records.

## Outputs
- Harmonized election dataset and/or VVK decision record list with legal links.

## Access reality statement
- Access type: `download files` + `UI copy-only`.
- Verified on 2026-02-24.
- Election open-data pages provide downloadable files; VVK decisions are presented as list/navigation pages.

## Primary endpoints
- Election open data: https://www.valimised.ee/en/archive/open-data-estonian-elections
- Elections archive (ET): https://www.valimised.ee/et/toimunud-valimiste-arhiiv
- Election open data (ET): https://www.valimised.ee/et/valimiste-arhiiv/valimiste-avaandmed
- VVK decisions page: https://www.valimised.ee/et/korraldajad/vabariigi-valimiskomisjon/otsused
- Riigi Teataja VVK decision query: https://www.riigiteataja.ee/algteksti_tulemused.html?doli=otsus&valj1=Vabariigi+Valimiskomisjon&kuvaKoik=true&sorteeri=kuupaev&kasvav=false

## Retrieval workflow (reproducible)
1. For election outcomes, open open-data/archive pages and download machine-readable files for requested elections.
2. Record election type, year, geography coding, and file version/date.
3. For governance decisions, open VVK decisions page and collect decision links, titles, and dates.
4. Cross-reference legal publication records with the Riigi Teataja filtered decision query.
5. Return separate datasets for `results` and `vvk_decisions`, with explicit provenance.

## Request/query contract
- No auth required.
- Election data extraction is file-based from published archive/open-data pages.
- VVK decisions are list pages; fields are parsed from HTML anchors and surrounding metadata.
- Riigi Teataja filtered query parameters are visible in URL (`doli`, `valj1`, `sorteeri`, `kasvav`).

## Output schema expectations
- `dataset_type` (`results` or `vvk_decisions`)
- `source_page_url`
- `election_type`
- `election_year`
- `record_title`
- `record_date`
- `record_url`
- `legal_reference_url` (when applicable)

## Limits and caveats
- Navigation and labels are often Estonian-first.
- Historic election files can differ in schema and territorial units.
- Decision pages may prioritize human-readable summaries over structured tables.

## Verification hooks
- Open-data page includes downloadable files (observed multiple direct file links).
- VVK decisions page includes direct link to the Riigi Teataja filtered query for VVK decisions.
