---
name: Browse Bendigo/Up banking products (CDR PRD)
description: List and compare Bendigo and Adelaide Bank retail and business banking products via the public, unauthenticated CDR Product Reference Data API, then fetch full detail for a chosen product.
api: openapi/bendigo-and-adelaide-bank-cds-banking-products-openapi.yml
operations: [listBankingProducts, getBankingProductDetail]
---

# Browse Bendigo and Adelaide Bank products (CDR Product Reference Data)

This skill uses the **public, unauthenticated** CDR Product Reference Data API. No credentials,
OAuth, or CDR accreditation are required for these two operations.

## Base URL
- Bendigo Bank: `https://api.cdr.bendigobank.com.au/cds-au/v1`
- Up: `https://api.up.com.au/cds-au/v1`

## Required conventions
- Always send the version header **`x-v: 4`** (positive integer). The server echoes the served
  version in the `x-v` response header. An unsupported version returns **406**
  (`urn:au-cds:error:cds:header:unsupported-version`).
- Optionally send `x-fapi-interaction-id` (a UUID) for request correlation.

## Steps

1. **List products** — call `listBankingProducts`:
   `GET /banking/products` with `x-v: 4`.
   Useful filters: `product-category` (e.g. `TRANS_AND_SAVINGS_ACCOUNTS`, `TERM_DEPOSITS`,
   `RESIDENTIAL_MORTGAGES`, `CRED_AND_CHRG_CARDS`), `brand`, `effective` (`CURRENT`/`FUTURE`/`ALL`),
   `updated-since` (ISO date-time). Paginate with `page` and `page-size` (default 25, max 1000);
   read `meta.totalRecords` / `meta.totalPages` and follow `links.next`.
   - Invalid `page-size` → **400** (`...field:invalid-page-size`); page past the end → **422**
     (`...field:invalid-page`).

2. **Pick a product** — take a `productId` from the `data.products[]` array.

3. **Get product detail** — call `getBankingProductDetail`:
   `GET /banking/products/{productId}` with `x-v: 4`.
   The response includes `fees`, `depositRates`, `lendingRates`, `features`, `eligibility`,
   `constraints`, and `bundles`. A missing/withdrawn product returns **404**
   (`urn:au-cds:error:cds:resource:unavailable` or `...resource:invalid`).

## Error handling
All errors return `application/json` shaped as `ResponseErrorListV2`:
`{ "errors": [ { "code": "<CDS URN>", "title": "...", "detail": "..." } ] }`.
See `errors/bendigo-and-adelaide-bank-problem-types.yml` for the full code list. Do not retry
4xx errors without changing the request; retry 5xx with backoff.

## Notes
- These operations are read-only and safe for autonomous agents.
- Anything beyond product reference data (accounts, transactions, payees, balances) requires the
  authenticated CDR data-sharing surface (FAPI 1.0 Advanced + MTLS, accredited data recipients only)
  — see `authentication/bendigo-and-adelaide-bank-authentication.yml`.
