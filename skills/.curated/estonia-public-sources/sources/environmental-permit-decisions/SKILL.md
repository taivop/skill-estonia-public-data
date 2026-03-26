---
name: environmental-permit-decisions
description: Query KOTKAS environmental decision system for permits, approvals, and environmental administrative decisions.
---

# Environmental Permit Decisions (KOTKAS)

## Use when
- You need permit/approval decision records in environmental domain.
- You need operational permit lifecycle tracking.

## Avoid when
- You need only environmental indicators without permit process context.

## Inputs
- Permit type, area/entity, date range, authority.

## Outputs
- Permit decision records with status chronology.

## Primary endpoints
- Permit registry (public): https://kotkas.envir.ee/permits/public_index
- Document registry (public): https://kotkas.envir.ee/permits/public_document_index
- Applications registry (public): https://kotkas.envir.ee/permits/public_application_index

## Workflow
1. Search for permit cases by type and geography.
2. Extract decision dates, statuses, and case identifiers.
3. Link associated documents where available.
4. Return permit lifecycle dataset.

## Human setup (when needed)
- If detailed records require UI navigation/login context, guide user through exact search and record-opening steps, then continue from shared URLs/exports.

## Quality checks
- Preserve case/permit identifiers.
- Separate application, review, and final-decision stages.

## Access reality
- Public access type: Public webpage/document extraction.
- Verification run: 2026-02-24.
- https://kotkas.envir.ee/permits/public_index (HTTP 200, text/html)

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
