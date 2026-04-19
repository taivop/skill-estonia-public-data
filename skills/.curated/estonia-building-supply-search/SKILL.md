---
name: estonia-building-supply-search
description: Search Estonian building supply stores (Bauhof, Ehituse ABC, Decora, K-Rauta, Bauhaus, Depo) for products, prices, and stock. USE WHEN user asks to find products at Estonian building stores, compare prices across them, or check availability.
metadata:
  distribution:
    tier: curated
    publish_anthropic: true
    plugin_name: estonia-building-supply-search
    plugin_version: 0.1.0
    plugin_author: Taivo Marketplace
---

Run `curl` searches across stores in parallel. By default, filter out out-of-stock items.

## Bauhof — Magento GraphQL

```bash
curl -s -X POST "https://www.bauhof.ee/api/magento/customQuery" \
  -H "Content-Type: application/json" \
  -d '{"query":"query{products(search:\"SEARCH_TERM\",pageSize:10){items{sku name stock_status price_range{minimum_price{final_price{value currency}regular_price{value currency}}}url_key}total_count}}","queryVariables":{}}'
```

Product URL: `https://www.bauhof.ee/{url_key}`. Stock: `stock_status` (`IN_STOCK` / `OUT_OF_STOCK`). Price: `final_price.value`.

## Ehituse ABC — Klevu Search

```bash
curl -s -X POST "https://eucs32v2.ksearchnet.com/cs/v2/search" \
  -H "Content-Type: application/json" \
  -d '{"context":{"apiKeys":["klevu-168180264665813326"]},"recordQueries":[{"id":"productSearch","typeOfRequest":"SEARCH","settings":{"query":{"term":"SEARCH_TERM"},"typeOfRecords":["KLEVU_PRODUCT"],"limit":10,"sort":"RELEVANCE"}}]}'
```

Product URL: `url`. Stock: `inStock` (`yes`/`no`). Price: `salePrice`. Results in `queryResults[0].records`.

## Decora — Klevu Search

```bash
curl -s -X POST "https://decoracsv2.ksearchnet.com/cs/v2/search" \
  -H "Content-Type: application/json" \
  -d '{"context":{"apiKeys":["klevu-159479682665411675"]},"recordQueries":[{"id":"productSearch","typeOfRequest":"SEARCH","settings":{"query":{"term":"SEARCH_TERM"},"typeOfRecords":["KLEVU_PRODUCT"],"limit":10,"sort":"RELEVANCE"}}]}'
```

Same response format as Ehituse ABC. Extra fields: `stock_availability` (store locations), `volume_l`, `shortDesc`, `usage_indoor_outdoor`.

## K-Rauta — LupaSearch

```bash
curl -s -X POST "https://api.lupasearch.com/v1/query/j9gky3z0nx3z" \
  -H "Content-Type: application/json" \
  -d '{"searchText":"SEARCH_TERM","limit":10}'
```

Returns name, price, URL, product code, brand, categories, images. Results in top-level array. Stock: items with `tags: []` are out of stock; in-stock items have tags like `"in-warehouse"`, `"online-only"`, or `"new-product"`.

## Bauhaus — Magento REST (2-step)

Step 1 — search (returns product IDs):
```bash
curl -s "https://secure.qs-m2web.bauhaus.ee/rest/V1/search?searchCriteria[pageSize]=10&searchCriteria[requestName]=quick_search_container&searchCriteria[filterGroups][0][filters][0][field]=search_term&searchCriteria[filterGroups][0][filters][0][value]=SEARCH_TERM"
```

Step 2 — get details (entity IDs from step 1):
```bash
curl -s "https://secure.qs-m2web.bauhaus.ee/rest/V1/products-render-info?searchCriteria[filterGroups][0][filters][0][field]=entity_id&searchCriteria[filterGroups][0][filters][0][value]=ID1,ID2,ID3&searchCriteria[filterGroups][0][filters][0][condition_type]=in&storeId=13&currencyCode=EUR"
```

Returns name (from image label), price, image URLs. No stock status, no product URL slug, no description.

## Depo — GraphQL

```bash
curl -s 'https://online.depo.ee/graphql' \
  -H 'Content-Type: application/json' \
  -d '{"query":"{ products(searchString: \"SEARCH_TERM\", start: 0, rows: 10) { edges { node { id name primaryBarcode specificationBrand prices { yellow { priceWithVat unit } orange { priceWithVat priceQuantity unit } } stockItems { locationAddress quantity } } } } }"}'
```

Name, brand, barcode, per-store stock quantities (1 Estonian store: Tallinn Veskiposti). Two price tiers: `yellow` (retail), `orange` (bulk/loyalty with `priceQuantity` threshold). Prices include 24% VAT.
