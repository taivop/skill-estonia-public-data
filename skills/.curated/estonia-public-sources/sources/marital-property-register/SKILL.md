---
name: marital-property-register
description: Use e-marital property register public service context for official lookup workflows and registry evidence extraction.
---

# Marital Property Register

## Use when
- You need official marital property register workflow/context.
- You need structured extraction from publicly available registry outputs.

## Avoid when
- You need private records not publicly accessible.

## Inputs
- Query purpose, allowed identifiers, and legal context.

## Outputs
- Structured register outputs and access constraints metadata.

## Primary endpoints
- Register search: https://abieluvararegister.rik.ee/
- Register statistics: https://abieluvararegister.rik.ee/Statistika
- Service info: https://www.rik.ee/en/other-services/e-marital-property-register

## Workflow
1. Determine what output is publicly available.
2. Execute lookup flow within allowed scope.
3. Extract structured fields and legal references.
4. Return output with access limitations.

## Human setup (when needed)
- If lookup needs authentication/role rights, walk user through the required steps and continue from resulting data.

## Quality checks
- Clearly label public vs restricted data boundaries.
- Preserve official registry references.

## Access reality
- Public access type: Public webpage/document extraction.
- Verification run: 2026-02-24.
- https://www.rik.ee/en/other-services/e-marital-property-register (HTTP 200, text/html;, file links detected: 0)

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
