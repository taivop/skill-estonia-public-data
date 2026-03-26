---
name: construction-register
description: Use Estonia construction register (EHR) public data views for permits, building records, and construction-related operational events.
---

# Estonia Construction Register (EHR)

## Use when
- You need building permit/construction operation records.
- You need location/project-level construction administrative data.

## Avoid when
- You need only aggregated construction statistics.

## Inputs
- Address/parcel, municipality, permit type, date range.

## Outputs
- Construction-register records with permit/status metadata.

## Primary endpoints
- EHR app: https://livekluster.ehr.ee/ui/ehr/v1
- EHR redirect: https://www.ehr.ee (redirects to above)

## Workflow
1. Locate relevant EHR public search area.
2. Apply location/permit/date filters.
3. Extract permit/project records and status fields.
4. Return standardized construction operations dataset.

## Human setup (when needed)
- If EHR requires interactive map/form navigation, walk user through exact search steps and ask them to share resulting URLs or exported files.

## Quality checks
- Keep unique register IDs and address references.
- Distinguish planned, approved, and completed states.

## Access reality
- Public access type: UI page with direct downloadable files.
- Verification run: 2026-02-24.
- https://livekluster.ehr.ee/ui/ehr/v1 (JavaScript SPA, requires browser rendering)

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
