---
name: competition-authority-decisions
description: Query Competition Authority public materials for decisions, precepts, and competition/market governance enforcement context.
---

# Competition Authority Decisions

## Use when
- You need competition/market regulation enforcement context.
- You need public decisions or precept-related records.

## Avoid when
- You need procurement contract data rather than enforcement outcomes.

## Inputs
- Sector, entity, enforcement topic, date range.

## Outputs
- Decision/precept publication references with links.

## Primary endpoints
- Decisions and precepts (ET): https://www.konkurentsiamet.ee/otsused-ja-ettekirjutused
- Authority homepage: https://www.konkurentsiamet.ee/en

## Workflow
1. Locate decision-related sections/news/publications.
2. Filter by topic/entity/date.
3. Extract metadata and links.
4. Return enforcement-context record set.

## Human setup (when needed)
- Some pages may block automated access. If blocked, instruct user to open the target page in browser and share links/files; continue from provided material.

## Quality checks
- Mark whether each item is a formal decision, precept, or news summary.
- Keep publication dates and entity names exactly.

## Access reality
- Public access type: UI page with direct downloadable files.
- Verification run: 2026-02-24.
- https://www.konkurentsiamet.ee/en (HTTP 200, text/html;, file links detected: 1)

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
