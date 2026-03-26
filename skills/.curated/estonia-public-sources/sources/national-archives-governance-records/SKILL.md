---
name: national-archives-governance-records
description: Query National Archives resources for historical governance records, institutional documentation, and long-term operational context.
---

# National Archives Governance Records

## Use when
- You need historical records of government operation.
- You need archival context for longitudinal governance analysis.

## Avoid when
- You need current operational dashboards only.

## Inputs
- Institution/topic, historical period, record type.

## Outputs
- Archival record references with metadata and source links.

## Primary endpoints
- ARKAADER searchable database: https://arkaader.ee/
- Virtual reading room: https://www.ra.ee/vau/index.php/en
- Archives overview: https://www.ra.ee/en/archives/

## Workflow
1. Locate relevant archival collections by institution/topic.
2. Extract collection/item references and date ranges.
3. Capture access metadata and links.
4. Return curated archival reference set.

## Human setup (when needed)
- If archival records require manual search portal navigation, walk user through search steps and continue from shared result links.

## Quality checks
- Preserve archive reference IDs and date spans.
- Distinguish digitized records from catalog-only entries.

## Access reality
- Public access type: Public webpage/document extraction.
- Verification run: 2026-02-24.
- https://www.ra.ee/en/archives/ (HTTP 200, text/html;, file links detected: 0)

## Request contract
- Use the listed primary endpoints as authoritative entry points.
- If API/query parameters are only visible in-browser, preserve exact request URL, params, and headers in output metadata.
- If endpoint is UI-only, document click path and extraction method used.

## Output schema expectations
- Keep at least: source URL, retrieval timestamp, publication/update date (if available), title/record label, and extracted governance-relevant fields.
- Preserve original field names when present in downloadable/API output.

## Limits and caveats
- Confirm whether data is open-download, UI-only, or authenticated before claiming full access.
- Separate narrative/guidance text from measurable records.

## Verification hooks
- Validate endpoint reachability and content type before extraction.
- Validate that each extracted claim is linked to a concrete source URL.
