---
name: food-business-approvals
description: Use Agriculture and Food Board food business approval pages for licensing/approval workflows and official requirement extraction.
---

# Food Business Approvals

## Use when
- You need official approval/licensing process context for food businesses.
- You need structured extraction of approval requirements and statuses.

## Avoid when
- You need consumption or food-price indicators.

## Inputs
- Business type, approval stage, and period.

## Outputs
- Structured approval-process references and requirement fields.

## Primary endpoints
- JVIS public register: https://jvis.agri.ee/jvis/avalik.html
- Approval info: https://pta.agri.ee/en/food/approval-operating-enterprises

## Workflow
1. Determine applicable approval route by business type.
2. Extract requirement and procedural fields.
3. Normalize approval categories and statuses.
4. Return structured process output.

## Human setup (when needed)
- If approvals require interactive service usage, guide user through steps and continue from provided outputs.

## Quality checks
- Preserve official requirement references.
- Keep process stage and responsible authority explicit.

## Access reality
- Public access type: UI page with direct downloadable files.
- Verification run: 2026-02-24.
- https://pta.agri.ee/en/food/approval-operating-enterprises (HTTP 200, text/html;, file links detected: 1)

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
