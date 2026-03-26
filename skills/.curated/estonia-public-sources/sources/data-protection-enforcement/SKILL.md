---
name: data-protection-enforcement
description: Query Data Protection Inspectorate public materials for enforcement, guidance, and privacy-governance operational context.
---

# Data Protection Enforcement Context

## Use when
- You need public privacy enforcement or guidance context.
- You need operational data-protection oversight references.

## Avoid when
- You need private complaint details not publicly disclosed.

## Inputs
- Topic, controller/sector, timeframe.

## Outputs
- Public enforcement/guidance references with metadata.

## Primary endpoints
- Precepts and enforcement (ET): https://www.aki.ee/et/inspektsioon/ettekirjutused
- AKI homepage: https://www.aki.ee/en

## Workflow
1. Locate relevant enforcement/guidance sections.
2. Extract entries by date/topic.
3. Normalize titles, dates, and links.
4. Return oversight-context dataset.

## Human setup (when needed)
- If site navigation is not directly machine-queryable, walk the user through exact clicks and continue from shared URLs/files.

## Quality checks
- Distinguish guidance from sanctions/enforcement actions.
- Preserve original publication wording and dates.

## Access reality
- Public access type: UI page with direct downloadable files.
- Verification run: 2026-02-24.
- https://www.aki.ee/en (HTTP 200, text/html;, file links detected: 1)

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
