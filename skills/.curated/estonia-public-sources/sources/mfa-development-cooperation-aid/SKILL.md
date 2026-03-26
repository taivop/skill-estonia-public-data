---
name: mfa-development-cooperation-aid
description: Retrieve Ministry of Foreign Affairs development cooperation and humanitarian aid strategy/report records from official page documents.
---

# MFA Development Cooperation and Humanitarian Aid

## Use when
- You need official strategy, evaluation, and report records for Estonia’s development cooperation and humanitarian aid.

## Avoid when
- You need beneficiary-level microdata not published on MFA pages.

## Inputs
- Period/year.
- Document type (`strategy`, `report`, `evaluation`, `annex`).

## Outputs
- Structured list of downloadable records with titles, dates, and URLs.

## Access reality statement
- Access type: `download files`.
- Verified on 2026-02-24.
- Page provides direct PDF links and keyword-filter navigation.

## Primary endpoints
- Development cooperation database: https://akta.mfa.ee/index.php?language=eng
- Main page: https://www.vm.ee/en/activity/development-cooperation-and-humanitarian-aid
- Example report: https://vm.ee/sites/default/files/documents/2025-07/RKK_Estonias-Development-Cooperation-Report.pdf
- Example strategy file: https://www.vm.ee/sites/default/files/documents/2024-04/AKHA%20strateegia%202024-2030%20inglise%20keeles.pdf

## Retrieval workflow (reproducible)
1. Open main page and collect linked files under `/sites/default/files/documents/...`.
2. Classify files by type (strategy, review, report, indicator annex).
3. Extract date/year from filename and nearby page context.
4. Capture relevant keyword-filter links when topic filtering is needed.
5. Return normalized document records with absolute URLs.

## Request/query contract
- No auth required.
- Files are directly downloadable via HTTPS links.
- No documented API; extraction is document-link based.

## Output schema expectations
- `source_page_url`
- `document_title`
- `document_url`
- `document_type`
- `publication_year_or_date`
- `language`
- `notes`

## Limits and caveats
- Document naming is mixed (English/Estonian and varying filename conventions).
- Page may combine policy and informational files with different update cycles.

## Verification hooks
- Main page includes downloadable files such as:
  - `RKK_Estonias-Development-Cooperation-Report.pdf`
  - `AKHA strateegia 2024-2030 ... .pdf`
  - `Evaluating Results ... indicators.pdf`
