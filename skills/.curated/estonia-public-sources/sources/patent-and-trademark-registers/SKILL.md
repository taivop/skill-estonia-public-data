---
name: patent-and-trademark-registers
description: Use Estonian Patent Office sources for patents, trademarks, and industrial property register context and structured public-record extraction.
---

# Patent and Trademark Registers

## Use when
- You need official industrial property register context.
- You need structured extraction of patent/trademark public records.

## Avoid when
- You need non-official commercial IP datasets.

## Inputs
- IP type, identifier, owner/applicant, and period.

## Outputs
- Structured IP register outputs with official references.

## Primary endpoints
- EPA online search (patents/utility models): https://online.epa.ee/
- EPA trademarks/designs search: http://teenused.epa.ee/
- Patent Office portal: https://www.epa.ee/

## Workflow
1. Locate relevant register/search route for IP type.
2. Extract public fields and status data.
3. Normalize status and classification fields.
4. Return structured dataset with provenance.

## Human setup (when needed)
- If search/export is portal-driven, guide user through lookup and continue from provided outputs.

## Quality checks
- Preserve official application/registration identifiers.
- Keep register status definitions attached.

## Access reality
- Public access type: UI page with direct downloadable files.
- Verification run: 2026-02-24.
- https://www.patendiamet.ee/en (HTTP 200, text/html;, file links detected: 1)

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
