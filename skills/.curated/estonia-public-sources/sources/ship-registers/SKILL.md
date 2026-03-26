---
name: ship-registers
description: Use official Estonian ship register sources for vessel registration and maritime registry governance context.
---

# Ship Registers

## Use when
- You need official vessel registration context.
- You need ship-register fields for compliance/governance analysis.

## Avoid when
- You need port infrastructure records only.

## Inputs
- Vessel identifier, register type, and period.

## Outputs
- Structured vessel register extract and status fields.

## Primary endpoints
- Ship register (Ministry of Justice): https://www.just.ee/en/legal-services/ship-register
- Estonian ship registers info: https://www.transpordiamet.ee/en/vehicle-ship-airplane/ships/estonian-ship-registers

## Workflow
1. Determine relevant ship register type.
2. Extract available vessel registration fields.
3. Normalize vessel and status identifiers.
4. Return structured dataset with provenance.

## Human setup (when needed)
- If register browsing/export is manual-only, guide user through the process and continue from supplied results.

## Quality checks
- Keep register type explicit in outputs.
- Separate active registration from historical/inactive states.

## Access reality
- Public access type: UI page with direct downloadable files.
- Verification run: 2026-02-24.
- https://www.transpordiamet.ee/en/vehicle-ship-airplane/ships/estonian-ship-registers (HTTP 200, text/html;, file links detected: 12)

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
