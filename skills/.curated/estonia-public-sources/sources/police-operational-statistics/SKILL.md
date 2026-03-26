---
name: police-operational-statistics
description: Query Police and Border Guard Board public publications for operational statistics context, annual reporting, and incident-related indicators.
---

# Police Operational Statistics

## Use when
- You need official police operational statistics context.
- You need annual publication-based indicators from PPA sources.

## Avoid when
- You need court-level procedural outcomes.

## Inputs
- Topic scope (crime, border, response), period, and region.

## Outputs
- Extracted police operational indicators with source citations.

## Primary endpoints
- Statistics page (ET): https://www.politsei.ee/et/juhised/statistika
- Police and Border Guard Board portal: https://www.politsei.ee/en

## Workflow
1. Locate relevant statistics/news/report publication within official PPA pages.
2. Extract comparable indicators and periods.
3. Normalize category labels and definitions.
4. Return structured table plus source notes.

## Human setup (when needed)
- If statistics are published only via downloadable reports or press releases, guide user through retrieval and continue from provided files.

## Quality checks
- Keep indicator definitions tied to each source.
- Do not infer missing values; mark unknowns explicitly.

## Limitations
- A dedicated public API/statistics endpoint may not be exposed from the main entry page; use official published reports/pages as evidence sources.

## Access reality
- Public access type: UI page with direct downloadable files.
- Verification run: 2026-02-24.
- https://www.politsei.ee/en (HTTP 200, text/html, file links detected: 1)

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
