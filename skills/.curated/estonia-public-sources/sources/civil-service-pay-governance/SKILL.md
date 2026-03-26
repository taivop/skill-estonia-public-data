---
name: civil-service-pay-governance
description: Retrieve civil-service pay governance records from Ministry of Finance, including guidance documents, salary disclosure templates, and related legal/policy materials.
---

# Civil Service Pay Governance

## Use when
- You need official public-sector pay-system governance material.
- You need templates/guidance and annual disclosure files related to civil-service pay.

## Avoid when
- You need only aggregated public-sector statistics tables (use public-sector statistics skill).

## Inputs
- Topic (`guidance`, `salary-disclosure`, `methodology`, `legal-context`).
- Year.

## Outputs
- Source-linked list of governance documents and data templates.

## Access reality statement
- Access type: `download files`.
- Verified on 2026-02-24.
- Page provides direct PDF/XLSX downloads.

## Primary endpoints
- Salary data (public sector statistics): https://www.fin.ee/riigihaldus-ja-avalik-teenistus-kinnisvara/riigihaldus/avaliku-sektori-statistika#ametnike-palgaandmed
- Pay governance page: https://www.fin.ee/riigihaldus-ja-avalik-teenistus-kinnisvara/avalik-teenistus/palgakorraldus

## Retrieval workflow (reproducible)
1. Open pay-governance page.
2. Collect all linked files under `/sites/default/files/documents/...`.
3. Classify each record by purpose (methodology handbook, memo, disclosure guide, template).
4. Extract year/date from filename and nearby text.
5. Return sorted record list with absolute URLs.

## Request/query contract
- No auth required.
- File retrieval is direct over HTTPS.
- There is no documented API; extraction is from published file links.

## Output schema expectations
- `source_page_url`
- `document_title`
- `document_url`
- `file_format`
- `publication_or_version_year`
- `document_category`
- `notes`

## Limits and caveats
- Titles can be abbreviated and may require filename parsing for year/version.
- Governance documents may reference frameworks published on other pages.

## Verification hooks
- Page contains files such as `Ametnike palkade avalikustamise juhend_2026.pdf` and `01.04.2026 põhipalgad vorm.xlsx`.
- Methodological documents are available (e.g., `ametikohtade hindamise kasiraamat_2018.pdf`).
