---
name: consumer-technical-regulator-decisions
description: Query Consumer Protection and Technical Regulatory Authority public materials for supervision and enforcement decision context.
---

# Consumer/Technical Regulator Decisions

## Use when
- You need TTJA supervision/enforcement publication context.
- You need sector-regulation operational outcome references.

## Avoid when
- You need unrelated market stats without regulatory context.

## Inputs
- Sector/topic, entity, and date range.

## Outputs
- Decision-related publication references and metadata.

## Primary endpoints
- Consumer disputes decisions: https://jvis.ttja.ee/modules/tarbijavaidluskomisjoni-otsused/avalik
- TTJA homepage: https://ttja.ee/en

## Workflow
1. Identify decision/enforcement-related sections.
2. Extract relevant entries and links.
3. Normalize topic/date/entity fields.
4. Return structured regulatory-context table.

## Human setup (when needed)
- If direct scraping is blocked by site structure, guide user through browsing/filtering and continue from provided links/files.

## Quality checks
- Label items by type (decision, warning, guidance, news).
- Keep source links and publication dates exact.

## Access reality
- Public access type: UI page with direct downloadable files.
- Verification run: 2026-02-24.
- https://ttja.ee/en (HTTP 200, text/html;, file links detected: 1)

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
