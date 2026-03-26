---
name: healthcare-professionals-register
description: Use Health Board healthcare professionals registration pages for registry-process context and official registration evidence extraction.
---

# Healthcare Professionals Register

## Use when
- You need official registration process context for healthcare professionals.
- You need structured extraction of publicly available registration outputs.

## Avoid when
- You need private personnel records not publicly accessible.

## Inputs
- Profession type, registration scope, and period.

## Outputs
- Structured registration-process/output references.

## Primary endpoints
- Searchable register (MEDRE): https://medre.tehik.ee/home
- Registration info: https://www.terviseamet.ee/en/healthcare/registration-of-health-care-professionals

## Workflow
1. Identify register route and eligibility/output scope.
2. Extract public registration-related fields and references.
3. Normalize profession categories.
4. Return structured output and access caveats.

## Human setup (when needed)
- If lookup/verification requires interactive forms, guide user step-by-step and continue from provided outputs.

## Quality checks
- Separate process guidance from register results.
- Keep official category and status labels unchanged.

## Access reality
- Public access type: UI page with direct downloadable files.
- Verification run: 2026-02-24.
- https://www.terviseamet.ee/en/healthcare/registration-of-health-care-professionals (HTTP 200, text/html;, file links detected: 2)

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
