# Bendigo and Adelaide Bank (bendigo-and-adelaide-bank)

Bendigo and Adelaide Bank Limited (ASX:BEN) is one of Australia's largest retail banks, formed by the 2007 merger of the community-focused Bendigo Bank and the wholesale-strong Adelaide Bank, and headquartered in Bendigo, Victoria. The group serves millions of customers through the Bendigo Bank, Adelaide Bank, Rural Bank, and Up (neobank) brands, with a distinctive Community Bank branch-franchise model. As an authorised deposit-taking institution and accredited Consumer Data Right (CDR) data holder, the bank exposes public, unauthenticated Product Reference Data (PRD) APIs conforming to the Australian Consumer Data Standards, alongside the authenticated CDR consumer data-sharing surface governed by the ACCC/DSB rules.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/bendigo-and-adelaide-bank/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/bendigo-and-adelaide-bank/refs/heads/main/apis.yml)

## Tags

- Financial
- Banks
- Open Banking
- CDR
- Consumer Data Right
- Consumer Banking
- Australia
- Product Reference Data

## Timestamps

- **Created:** 2026-07-20
- **Modified:** 2026-07-20

## APIs

### Bendigo and Adelaide Bank CDR Product Reference Data API

Public, unauthenticated Consumer Data Right Product Reference Data API for the Bendigo Bank brand, exposing GET /banking/products and GET /banking/products/{productId} per the Australian Consumer Data Standards. Confirmed live returning HTTP 200 at x-v 4 with 50 published retail and business banking products (verified 2026-07-20).

- **Human URL:** [https://www.bendigoadelaide.com.au/banking-products-api/](https://www.bendigoadelaide.com.au/banking-products-api/)
- **Base URL:** `https://api.cdr.bendigobank.com.au/cds-au/v1`

#### Tags

- CDR
- Open Banking
- Product Reference Data
- Banking

#### Properties

- [Documentation](https://www.bendigoadelaide.com.au/banking-products-api/)
- [API Reference](https://consumerdatastandardsaustralia.github.io/standards/#get-products)
- [OpenAPI](openapi/bendigo-and-adelaide-bank-cds-banking-products-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)

### Up Banking CDR Product Reference Data API

Public CDR Product Reference Data API for Up, the digital neobank owned by Bendigo and Adelaide Bank, conforming to the shared Australian Consumer Data Standards. Confirmed live returning HTTP 200 for GET /banking/products (verified 2026-07-20). Up separately publishes its own authenticated personal-banking developer API at api.up.com.au/api/v1.

- **Human URL:** [https://up.com.au/](https://up.com.au/)
- **Base URL:** `https://api.up.com.au/cds-au/v1`

#### Tags

- CDR
- Open Banking
- Product Reference Data
- Neobank

#### Properties

- [Documentation](https://up.com.au/)
- [API Reference](https://consumerdatastandardsaustralia.github.io/standards/#get-products)
- [OpenAPI](openapi/bendigo-and-adelaide-bank-cds-banking-products-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)

### Adelaide Bank CDR Product Reference Data API

Consumer Data Right Product Reference Data API for the Adelaide Bank brand, following the standard Consumer Data Standards path at the documented CDR host. UNVERIFIED — the host resolved but did not return HTTP 200 for GET /banking/products on the standard path/version during probing on 2026-07-20; endpoint listed with the standard CDS path, not an invented host.

- **Human URL:** [https://www.bendigoadelaide.com.au/banking-products-api/](https://www.bendigoadelaide.com.au/banking-products-api/)
- **Base URL:** `https://api.cdr.adelaidebank.com.au/cds-au/v1`

#### Tags

- CDR
- Open Banking
- Product Reference Data
- Banking

#### Properties

- [Documentation](https://www.bendigoadelaide.com.au/banking-products-api/)
- [API Reference](https://consumerdatastandardsaustralia.github.io/standards/#get-products)
- [OpenAPI](openapi/bendigo-and-adelaide-bank-cds-banking-products-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)

## Common Properties

- [Website](https://www.bendigobank.com.au/)
- [Corporate Website](https://www.bendigoadelaide.com.au/)
- [Developer Portal](https://www.bendigoadelaide.com.au/banking-products-api/)
- [Documentation](https://www.bendigoadelaide.com.au/banking-products-api/)
- [API Standards](https://consumerdatastandardsaustralia.github.io/standards/)
- [Terms of Service](https://www.bendigobank.com.au/legal/terms-and-conditions/)
- [Privacy Policy](https://www.bendigobank.com.au/privacy/)
- [Support](https://www.bendigobank.com.au/contact-us/)
- [Investor Relations](https://www.bendigoadelaide.com.au/investor-centre/)
- [Blog](https://www.bendigoadelaide.com.au/media-centre/)

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com
