# Bendigo and Adelaide Bank (bendigo-and-adelaide-bank)

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

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
