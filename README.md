# Ciloo

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
> **Not from the company, and here with a question?** You are welcome here — we would rather be the
> front line and point you the right way than have a good report go nowhere. What this repository
> can answer is narrow, though, so it is worth knowing who you are actually looking for:
>
> - **A question about how the API works, an account, billing, or a bug in the service** — that is
>   the company's own support, not us. We profile this API; we do not operate it and cannot see
>   your account.
> - **A bug in an open-source project we only catalog** — file it on that project's own repository.
>   This has happened with a real and correct bug report that reached us instead of the people who
>   could fix it, which helped nobody.
> - **Anything about this listing itself** — the description, the tags, the rating, a missing or
>   wrong artifact — is ours. Open an issue here.
> - **Not sure, or something general about API Evangelist or APIs.io** — open an issue on the
>   [APIs.io Inbox](https://github.com/api-search/inbox) and we will route it.
>
> **This repository contains no software, and we will never ask you to download anything.** There is
> no build, release, installer, or binary here — only text and machine-readable API descriptions, so
> there is nothing here that can be "corrupt" or need "repairing". Any issue, comment, or email
> claiming otherwise and offering a download link is not from us and is hostile. Do not follow the
> link; it is a lure. Report it to GitHub and, if you like, tell us at
> [info@apievangelist.com](mailto:info@apievangelist.com) so we can take it down.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

Ciloo is a Rotterdam-headquartered global platform for branded products and promotional merchandise. Enterprises run a branded Ciloo store — business cards, apparel, stationery, signage, corporate gifts and sales collateral — and every order placed in it is produced on demand by a vetted production partner near the recipient, which Ciloo positions as cutting cost, waste and shipping distance while keeping brand control central. The platform is used by manufacturing, medical-device, professional- services and franchise organisations, and integrates with digital asset management (Frontify, Bynder, Canto, Aprimo, Papirfly, Brandfolder, Marvia), procurement and ERP (SAP Ariba, S/4HANA, Proactis, Proqura, Exact), SSO, and WooCommerce. Ciloo documents two APIs on its own knowledge centre at api.cilooprint.com: a per-brand-store Cart API secured with OAuth 1.0a, and a bidirectional Printer API integration that pushes orders to production partners and receives production and shipping status callbacks in return.

**Areas:** Company · Printing · Branded Merchandise · Promotional Products · Print on Demand · E-Commerce · Digital Asset Management · Procurement · Fulfillment · Marketing

## Ciloo on APIs.io

Everything profiled for Ciloo is published on APIs.io rather than in this repository. Start at the provider page — **[apis.io/providers/ciloo/](https://apis.io/providers/ciloo/)** — or go straight to one of the APIs or properties below.

### APIs (4)

- [Ciloo Cart API](https://apis.io/apis/ciloo/ciloo-cart-api/) — OAuth 1.0a (HMAC-SHA1) REST API on the ciloo/v1 namespace of a Ciloo brand store. Read, add, update and remove cart items; mint per-customer OAuth…
- [Ciloo Printer API Integration](https://apis.io/apis/ciloo/ciloo-printer-api/) — Bidirectional order integration between Ciloo and its production partners. Ciloo POSTs a print order — items, print components with artwork paths and…
- [Ciloo Authentication API](https://apis.io/apis/ciloo/ciloo-authentication-api/) — OAuth key provisioning and auto-login token issuance.
- [Ciloo Customers API](https://apis.io/apis/ciloo/ciloo-customers-api/) — Customer lifecycle via the WooCommerce REST API v3 namespace, as documented by Ciloo.

### Published properties

Each property below is a page on APIs.io carrying the machine-readable artifact and what it says.

#### AsyncAPI (1)

Event-driven and webhook contracts.

- [Ciloo Printer Webhooks](https://apis.io/asyncapis/ciloo/ciloo-printer-webhooks/)

#### MCP servers (1)

Model Context Protocol servers that expose the API to agents.

- [ciloo](https://apis.io/servers/ciloo/ciloo/)

#### Collections (1)

Postman and Open Collection request collections.

- [Ciloo Cart API](https://apis.io/collections/ciloo/open-ciloo-cart-api/)

#### Overlays (1)

OpenAPI overlays, including conversational phrasing for each operation.

- [Ciloo Cart Api Overlay](https://apis.io/overlays/ciloo/ciloo-cart-api-overlay/)

#### Security (2)

Authentication, trust centre, and vulnerability disclosure.

- [Ciloo Authentication](https://apis.io/security/ciloo/ciloo-authentication/)
- [Ciloo Domain Security](https://apis.io/security/ciloo/ciloo-domain-security/)

#### Plans and pricing (1)

Published plans, tiers and prices.

- [Ciloo Plans Pricing](https://apis.io/plans/ciloo/ciloo-plans-pricing/)

#### Rate limits (1)

Published request limits.

- [Ciloo Rate Limits](https://apis.io/rate-limits/ciloo/ciloo-rate-limits/)

## Where to find this API

Links to the company's own pages. This repository publishes no copy of their specifications — the canonical document is theirs and lives at the URLs below.

- [Website](https://ciloo.com/)
- [Documentation](https://api.cilooprint.com/)
- [Getting started](https://api.cilooprint.com/ciloo-cart-api-documentation/#authentication-setup)
- [API reference](https://api.cilooprint.com/ciloo-cart-api-documentation/#api-endpoints-reference)
- [Support](https://support.ciloo.com/hc/en-us)
- [Blog](https://ciloo.com/blog/)
- [Terms of service](https://ciloo.com/terms-conditions/)
- [Privacy policy](https://ciloo.com/privacy-policy/)

## API Evangelist rating

**Kin Score 30.2** — thin · rubric 0.24.0 · scored 2026-10-17

| Facet | Score |
|---|---|
| Discoverability | 71.4 |
| Contract quality | 21.8 |
| Contract governance | 4.5 |
| Operational transparency | 7.9 |
| Developer ergonomics | 55.4 |
| Access clarity | 21.1 |

**Agent readiness 29.0** — agent-ready

| Agent-readiness dimension | Result |
|---|---|
| Spec Presence | yes |
| Agentic Access | — |
| Reversibility Documented | — |
| MCP Server | — |
| Auth Clarity | bearer (partial credit) |
| Idempotency | — |
| Error Semantics | derived (partial credit) |
| OpenAPI Examples | verified |
| Rate Limit Signal | documented (partial credit) |
| Event Surface Described | yes |
| Agent Skills | derived (partial credit) |
| Well Known Catalog | — |
| Consent Identity | — |
| Agent Card | — |
| Dry Run Mode | — |
| Delegated Identity | — |
| Protected Resource Metadata | — |
| Dynamic Client Registration | — |
| Agentic Commerce | — |

**Regulatory alignment 24.5** — Horizontal (data, software, accessibility, platform)

The rubric is published at [github.com/api-evangelist/kin-score](https://github.com/api-evangelist/kin-score). The per-check breakdown behind these numbers — which checks were earned, partial or missed — along with score history and how this provider compares to its peers, is available at [apis.io/providers/ciloo/](https://apis.io/providers/ciloo/).

## How this profile is made

API Evangelist profiles a company's public API surface the way a developer would find it: the website, developer portal and documentation, the specifications it publishes, its public repositories, and its pricing, status and changelog pages. From that it derives the properties above — contracts split per API, workflows, schemas, collections, governance rules, plans and rate limits — and scores them against the published [Kin Score rubric](https://github.com/api-evangelist/kin-score).

The artifacts are published on [APIs.io](https://apis.io), not in this repository. This repository is the public record for Ciloo: the place to say something is wrong, missing or out of date, and to ask for a re-score or a removal.

## Open an issue

- **Something about this listing** — a wrong description, a missing API, a stale artifact or a question about the rating: [open an issue on this repository](https://github.com/api-evangelist/ciloo/issues/new).
- **A new API, or one that is not in the catalog yet** — [submit it on APIs.io](https://apis.io/add/).
- **Anything else** — [the APIs.io inbox](https://github.com/api-search/inbox/issues/new) or [info@apievangelist.com](mailto:info@apievangelist.com).
