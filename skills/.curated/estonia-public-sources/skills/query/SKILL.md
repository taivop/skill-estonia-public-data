---
name: query
description: >
  Query Estonian official public sources — registries, statistics, permits, procurement, budgets, legal acts, and more.
  Use when: user asks about Estonian government data, public registries, official statistics, permits, tenders,
  legal acts, business register, building register, land registry, environmental permits, official notices,
  or any Estonian public-sector dataset.
  Keywords (ET): äriregister, ehitisregister, maaregister, kinnistusraamat, riigihanked, keskkonnaload,
  ametlikud teadaanded, riigiteataja, riigikogu, riigieelarve, statistikaamet, maksu- ja tolliamet,
  terviseamet, sotsiaalkindlustusamet, keskkonnaamet, maa-amet, ruumiamet, KOTKAS, PRIA, haigekassa.
  Keywords (EN): business register, building register, land register, procurement, environmental permits,
  official notices, parliament, state budget, statistics, tax board, health board, social insurance,
  environmental agency, land board, spatial data.
---

# Estonian Public Sources Query

You have access to 133 official Estonian public source skills. Use them to answer the user's question with evidence from official sources.

## User query

$ARGUMENTS

## Routing workflow

1. Read the source map at `${CLAUDE_SKILL_DIR}/../../SOURCE_MAP.md` to find the right source(s) for the query.
2. Open the matching source skill at `${CLAUDE_SKILL_DIR}/../../sources/<source-name>/SKILL.md`.
3. Execute the source workflow: follow the endpoint, retrieval method, and quality checks defined in that source skill.
4. If the source requires human interaction (login, captcha, UI export), guide the user through the exact steps, then continue analysis from the files/data they provide.

## Retrieval preferences

- Prefer `curl`/`wget` on direct URLs over browser navigation.
- If the source has an API, use it with concrete request examples from the source skill.
- Only fall back to browser/UI navigation when the data is truly UI-only.

## Output requirements

- Always cite the exact source URL where data was retrieved.
- Include retrieval timestamp.
- Preserve original field names from the source.
- Separate facts from interpretation.
