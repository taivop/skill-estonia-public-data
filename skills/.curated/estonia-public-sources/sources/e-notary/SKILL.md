---
name: e-notary
description: Use RIK e-notary service context for notarial workflow guidance and structured extraction of publicly accessible process information.
---

# E-Notary

## Use when
- You need official notarial e-service process context.
- You need structured extraction of public e-notary workflow outputs.

## Avoid when
- You need confidential notarial records.

## Inputs
- Service type, procedural stage, and period.

## Outputs
- Structured e-notary process/output references.

## Primary endpoints
- Chamber of Notaries portal: https://notar.ee
- E-notary service info: https://www.rik.ee/en/other-services/e-notary

## Workflow
1. Identify relevant e-notary service route.
2. Extract process requirements and available outputs.
3. Normalize service/stage terminology.
4. Return structured process map and references.

## Human setup (when needed)
- If interaction requires authenticated service usage, guide user through required steps and continue from provided results.

## Quality checks
- Separate process guidance from official output artifacts.
- Preserve legal references and fees where listed.

## Access reality
- Public access type: Public webpage/document extraction.
- Verification run: 2026-02-24.
- https://www.rik.ee/en/other-services/e-notary (HTTP 200, text/html;, file links detected: 0)

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
