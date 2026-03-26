---
name: food-supervision
description: Use Agriculture and Food Board food supervision pages for inspection, compliance, and enforcement process context.
---

# Food Supervision

## Use when
- You need official food supervision/inspection context.
- You need structured extraction of food oversight materials.

## Avoid when
- You need food market price statistics.

## Inputs
- Supervision topic, period, and business type scope.

## Outputs
- Structured food supervision references and findings fields.

## Primary endpoints
- JVIS public register: https://jvis.agri.ee/jvis/avalik.html
- Food supervision info: https://pta.agri.ee/en/food/supervision

## Workflow
1. Identify relevant supervision publications/guidance.
2. Extract inspection/compliance-related fields.
3. Normalize supervision taxonomy.
4. Return structured output with citations.

## Human setup (when needed)
- If details are in linked documents, guide user through retrieval and continue from files.

## Quality checks
- Distinguish process guidance from enforcement outcomes.
- Keep source date and publication context.

## Access reality
- Public access type: UI page with direct downloadable files.
- Verification run: 2026-02-24.
- https://pta.agri.ee/en/food/supervision (HTTP 200, text/html;, file links detected: 1)

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
