---
name: ministry-document-registries
description: Query Estonia's official ministry and agency document registries (ADR network) for operational records, incoming/outgoing documents, and workflow traceability.
---

# Ministry Document Registries

## Use when
- You need official document-level operational records from ministries/agencies.
- You need a trace of administrative workflow (registration, correspondence, routing).

## Avoid when
- You need enacted legal texts only.

## Inputs
- Institution, date range, document keywords, registry identifiers.

## Outputs
- Registry search results with document metadata and source links.

## System types

There are three distinct document registry systems used by Estonian ministries:

### System A: ADR (adr.rik.ee) — used by most ministries

Software: ADR v1.4.19 (Webmedia/RIT). Server-side rendered. Two search endpoints per registry:

**Quick search (all fields):**
```
POST https://adr.rik.ee/{code}/kiirotsing
Content-Type: application/x-www-form-urlencoded
Body: input=<keyword>&pageNumber=1
```

**Title-only search:**
```
POST https://adr.rik.ee/{code}/otsing
Content-Type: application/x-www-form-urlencoded
Body: title=<keyword>&pageNumber=1
```

Additional `otsing` fields: `regDateBegin` (DD.MM.YYYY), `regDateEnd`, `documentTypes` (checkbox IDs), `party`, `senderRegNr`, `accessRestriction` (Avalik/AK).

Returns HTML with `<table class="data hover">` containing up to 100 rows. Message "kuvatakse esimesed 100" indicates more results exist — refine the query.

Document detail URL: `https://adr.rik.ee/{code}/dokument/{id}`

### System B: HiA.PDR (adr.envir.ee, dok.hm.ee) — Kliimaministeerium and Haridusministeerium

REST JSON API:
```
GET https://{host}/api/v1/documents.json
Params: orgId=<id>&title=<keyword>&offset=0&limit=100&fields=id,title,regNr,regDate,docType
```

Response: `{"recordsFiltered": N, "recordsReturned": M, "data": [...]}`

Organisation IDs available at: `GET https://{host}/api/v1/options/name/organization.json`

Additional search params: `extPerson`, `extOrganization`, `extRegCode`, `responsible`, `regCode`, `regDateStart` (DD.MM.YYYY), `regDateEnd`, `ctId` (document type ID).

### System C: WebDesktop (dok-register.vm.ee, dhsavalik.agri.ee) — Välisministeerium and Regionaal ministry

These systems are UI-driven. No reliable machine-readable search API confirmed. Human-guided extraction required.

---

## Ministry registry index

| Ministry | Code/Host | System | Search URL | Verified results (keyword "kiri") |
|---|---|---|---|---|
| Justiits- ja Digiministeerium | `jm` | ADR | `POST adr.rik.ee/jm/kiirotsing` | >100 |
| Rahandusministeerium | `ram` | ADR | `POST adr.rik.ee/ram/kiirotsing` | >100 |
| Majandus- ja Kommunikatsiooniministeerium | `mkm` | ADR | `POST adr.rik.ee/mkm/kiirotsing` | >100 |
| Sotsiaalministeerium | `som` | ADR | `POST adr.rik.ee/som/kiirotsing` | >100 |
| Kultuuriministeerium | `kum` | ADR | `POST adr.rik.ee/kum/kiirotsing` | >100 |
| Kaitseministeerium | `kaitseministeerium` (also `kmin`) | ADR | `POST adr.rik.ee/kaitseministeerium/kiirotsing` | >100 |
| Siseministeerium | `sisemin` @ adr.siseministeerium.ee | ADR | `POST adr.siseministeerium.ee/sisemin/kiirotsing` | >100 |
| Riigikantselei | `riigikantselei` | ADR | `POST adr.rik.ee/riigikantselei/kiirotsing` | 0 (registry appears empty/restricted) |
| Kliimaministeerium | orgId=68 @ adr.envir.ee | HiA.PDR | `GET adr.envir.ee/api/v1/documents.json?orgId=68&title=...` | 8 669 |
| Haridus- ja Teadusministeerium | orgId=1 @ dok.hm.ee | HiA.PDR | `GET dok.hm.ee/api/v1/documents.json?orgId=1&title=...` | 10 421 |
| Välisministeerium | dok-register.vm.ee | WebDesktop | `https://dok-register.vm.ee/?page=pub_search_dynobj&tid=48314` | UI-only |
| Regionaal- ja Põllumajandusministeerium | dhsavalik.agri.ee | WebDesktop | `https://dhsavalik.agri.ee/` | UI-only |
| Päästeamet | `paa` @ adr.rescue.ee | ADR | `POST adr.rescue.ee/paa/kiirotsing` | >100 |

### Additional HiA.PDR organisations at adr.envir.ee

| Organisation | orgId |
|---|---|
| Kliimaministeerium | 68 |
| Keskkonnaamet | 43 |
| Keskkonnainspektsioon | 53 |
| Keskkonnaagentuur | 58 |
| Maa- ja Ruumiamet | 71 |
| Eesti Loodusmuuseum | 1 |
| Riigilaevastik | 67 |
| Keskkonnaministeeriumi Infotehnoloogiakeskus | 70 |

### Additional HiA.PDR organisations at dok.hm.ee

| Organisation | orgId |
|---|---|
| Haridus- ja Teadusministeerium | 1 |
| Haridus- ja Noorteamet | 136 |
| Eesti Keele Instituut | 172 |
| Keeleamet | 148 |
| Rahvusarhiiv | 53 |
| Eesti Noorsootöö Keskus | 60 |
| Eesti Teadusagentuur SA | 184 |

---

## Workflow

### For ADR registries (System A)

1. Choose the ministry code from the table above.
2. POST to `https://adr.rik.ee/{code}/kiirotsing` with `input=<keyword>&pageNumber=1`.
3. Parse the returned HTML table rows (`<tr><td><a href="/mkm/dokument/ID">`).
4. For each row extract: viit (registration number), date, title, document type, parties.
5. To get document detail or attached files: fetch `https://adr.rik.ee/{code}/dokument/{id}`.
6. If >100 results, use `/otsing` with specific fields (title, date range) to narrow results.

### For HiA.PDR registries (System B)

1. Call `GET https://{host}/api/v1/documents.json?orgId=<id>&title=<keyword>&offset=0&limit=100`.
2. Parse `data[]` array from JSON response; check `recordsFiltered` for total count.
3. Paginate using `offset` parameter (increment by `limit`).
4. To get document detail: fetch `GET https://{host}/api/v1/documents/{id}.json`.

### For WebDesktop registries (System C)

- Navigate to the registry URL in a browser.
- Select document category (e.g. Kirjavahetus, Saabunud dokument).
- Use the on-page search form.
- Share resulting URL or export for machine processing.

---

## Access reality
- Public access type: Server-side HTTP (ADR, HiA.PDR) or UI-only (WebDesktop).
- Verification run: 2026-03-01.
- ADR adr.rik.ee: HTTP 200, server: RIT, content-type: text/html;charset=utf-8.
- HiA.PDR adr.envir.ee: HTTP 200, JSON API confirmed working.
- HiA.PDR dok.hm.ee: HTTP 200, JSON API confirmed working.
- WebDesktop dok-register.vm.ee, dhsavalik.agri.ee: HTTP 200, UI-only confirmed.
- Riigikantselei ADR: HTTP 200 but 0 results for any keyword tested — may be effectively empty.

## Quality checks
- Keep original registry identifiers (viit) unchanged.
- Separate incoming (`Sissetulev kiri`) vs outgoing (`Väljaminev kiri`) records where provided.
- Private individuals appear as initials only (e.g. "H. K.") per Public Information Act.
- ADR shows max 100 results per query; HiA.PDR supports full pagination via `offset`.
- Documents registered since 2009 (ADR) or 2016 (adr.envir.ee HiA.PDR) are available.

## Request contract
- ADR: use POST with `Content-Type: application/x-www-form-urlencoded`.
- HiA.PDR: use GET with query params; response is JSON.
- No authentication required for public records.
- Keyword must be at least 3 characters for ADR quick search.

## Output schema expectations
- ADR HTML table columns: Viit | Reg. kpv | Pealkiri | Dokumendi liik | Teised osapooled
- HiA.PDR JSON fields: `id`, `title`, `regNr`, `regDate`, `docType`, `orgId`, `extOrganization`, `extPerson`, `extRegCode`, `responsible`, `dispatchType`, `accessRestrictedUntil`
- Keep at least: source URL, retrieval timestamp, registration number (viit), registration date, title, document type, parties.

## Limits and caveats
- WebDesktop systems (Välisministeerium, Regionaal- ja Põllumajandusministeerium) are UI-only.
- Restricted documents show only metadata (no file access).
- Paper documents are not in the registries.
- HiA.PDR title search is substring match; ADR quick search covers all fields.
- adr.envir.ee documents before 2016-01-01 are not publicly available due to system migration.

## Verification hooks
- ADR: POST to `/kiirotsing` with `input=kiri` must return HTML containing `<table class="data hover">` with at least one `<tr><td><a href=` row.
- HiA.PDR: GET `/api/v1/documents.json?orgId=68&title=kiri` must return JSON with `recordsFiltered > 0`.
- Confirm `server: RIT` header for ADR rik.ee endpoints.
