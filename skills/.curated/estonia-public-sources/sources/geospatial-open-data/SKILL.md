---
name: geospatial-open-data
description: Use Land and Spatial Board geospatial open data services for maps, cadaster/cadastral parcels, and address-linked analysis in Estonia.
---

# Estonia Geospatial Open Data

## Use when
- You need base maps, cadaster/cadastral parcel context, or map-service layers.
- You need interoperable geospatial services (WMS/WFS/WMTS).
- You need parcel-level lookup or map extraction for a specific cadastral unit/area.

## Avoid when
- You only need non-spatial time series indicators.

## Inputs
- Area of interest (address, municipality, coordinates, polygon).
- Required layer/theme and output format.

## Outputs
- Layer/service URLs.
- Retrieved geospatial dataset or map extract.
- Cadastral unit context when present in selected layers.

## Primary endpoints
- Public services index: https://geoportaal.maaamet.ee/eng/services/public-wms-wfs-p346.html
- Spatial data downloads: https://geoportaal.maaamet.ee/eng/spatial-data-p58.html
- Metadata catalogue: https://metadata.geoportaal.ee/geonetwork/srv/eng/catalog.search#/home
- WMS base maps: https://kaart.maaamet.ee/wms/alus?
- WMS topographic: https://kaart.maaamet.ee/wms/kaart?
- WMS addresses/cadastral: https://kaart.maaamet.ee/wms/aadressid?
- WMS orthophotos: https://kaart.maaamet.ee/wms/fotokaart?
- WFS vectors (ETAK): https://gsavalik.envir.ee/geoserver/etak/ows

## Workflow
1. Open the public services page and select the right layer family.
2. Use GetCapabilities endpoint listed there to discover exact layers.
3. Query layer subset by bbox/filter (including parcel identifiers when available).
4. Export in a reusable format and document CRS/projection.

## Human setup (when needed)
- If a map layer requires manual portal selection, instruct the user exactly which layer to enable and where to copy the service URL.

## Quality checks
- Always report CRS and geometry type.
- Check if layer is authoritative or contextual.

## Access reality
- Public access type: Public webpage/document extraction.
- Verification run: 2026-02-24.
- https://geoportaal.maaamet.ee/eng/services/public-wms-wfs-p346.html (HTTP 200, text/html)
- WMS/WFS endpoints are open OGC services, queryable via GetCapabilities

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
