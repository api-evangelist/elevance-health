# Elevance Health

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

Elevance Health (formerly Anthem) is a Fortune 500 health benefits company serving members through Blue Cross and Blue Shield affiliated health plans across multiple states, offering medical, pharmacy, dental, vision and specialty insurance. Its entire public API surface is HL7 FHIR, published to satisfy the CMS Interoperability and Patient Access Final Rule: a member-consented Patient Access API (FHIR R4, CARIN Blue Button, SMART on FHIR), a read-only Provider Directory API (Da Vinci PDEX Plan Net) whose CapabilityStatement is readable with no credentials, a Formulary API (Da Vinci PDEX US Drug Formulary), and a legacy Patient360 FHIR DSTU2 endpoint running CareEvolution HIEBus. There is no OpenAPI, no SDK and no pricing — the contracts are the FHIR CapabilityStatements the servers publish about themselves. Elevance has committed in its own endpoint support document to shipping Payer-to-Payer, Prior Authorization and Provider Access APIs by 1 January 2027 under CMS-0057-F; none of the three exists today.

**Areas:** Fortune 500 · Healthcare · Health Insurance · FHIR · Interoperability · CMS Interoperability · SMART on FHIR · Da Vinci PDEX · CARIN Blue Button · Payers · Provider Directory · Formulary

## Elevance Health on APIs.io

Everything profiled for Elevance Health is published on APIs.io rather than in this repository. Start at the provider page — **[apis.io/providers/elevance-health/](https://apis.io/providers/elevance-health/)** — or go straight to one of the APIs or properties below.

### APIs (8)

- [Elevance Health Patient Access API](https://apis.io/apis/elevance-health/patient-access/) — The Patient Access API gives Elevance Health members, through an application they authorize, up to five years of their medical, pharmacy, dental and vision…
- [Elevance Health Provider Directory API](https://apis.io/apis/elevance-health/provider-directory/) — The Provider Directory API exposes which practitioners and organizations are in-network for a given Elevance Health insurance plan. HL7 FHIR R4 conforming…
- [Elevance Health Formulary API](https://apis.io/apis/elevance-health/formulary/) — The Formulary API publishes drug coverage for Elevance-affiliated Medicare, Medicaid and CHIP plans — covered drug lists, tier placement, pharmacy type and…
- [Elevance Health Claims API](https://apis.io/apis/elevance-health/elevance-health-claims-api/) — The Claims API from Elevance Health — 3 operation(s) for claims.
- [Elevance Health Conformance API](https://apis.io/apis/elevance-health/elevance-health-conformance-api/) — The Conformance API from Elevance Health — 1 operation(s) for conformance.
- [Elevance Health Coverage API](https://apis.io/apis/elevance-health/elevance-health-coverage-api/) — The Coverage API from Elevance Health — 2 operation(s) for coverage.
- [Elevance Health Patient API](https://apis.io/apis/elevance-health/elevance-health-patient-api/) — The Patient API from Elevance Health — 2 operation(s) for patient.
- [Elevance Health Provider Directory API](https://apis.io/apis/elevance-health/elevance-health-provider-directory-api/) — The Provider Directory API from Elevance Health — 2 operation(s) for provider directory.

### Published properties

Each property below is a page on APIs.io carrying the machine-readable artifact and what it says.

#### MCP servers (1)

Model Context Protocol servers that expose the API to agents.

- [elevance-health-mcp.yml](https://apis.io/servers/elevance-health/elevance-health-mcp-yml/)

#### Agentic access (1)

Which operations an agent can call, which act, and which need a human in the loop.

- [Elevance Health Agentic Access](https://apis.io/agentic-access/elevance-health/elevance-health-agentic-access/)

#### Collections (6)

Postman and Open Collection request collections.

- [Elevance Health Patient Access FHIR API](https://apis.io/collections/elevance-health/open-elevance-health/)
- [Elevance Health Patient Access FHIR Claims API](https://apis.io/collections/elevance-health/open-elevance-health-claims-api/)
- [Elevance Health Patient Access FHIR Claims Conformance API](https://apis.io/collections/elevance-health/open-elevance-health-conformance-api/)
- [Elevance Health Patient Access FHIR Claims Coverage API](https://apis.io/collections/elevance-health/open-elevance-health-coverage-api/)
- [Elevance Health Access FHIR Claims Patient API](https://apis.io/collections/elevance-health/open-elevance-health-patient-api/)
- [Elevance Health Patient Access FHIR Claims Provider Directory API](https://apis.io/collections/elevance-health/open-elevance-health-provider-directory-api/)

#### Overlays (5)

OpenAPI overlays, including conversational phrasing for each operation.

- [Elevance Health Claims Api Overlay](https://apis.io/overlays/elevance-health/elevance-health-claims-api-overlay/)
- [Elevance Health Conformance Api Overlay](https://apis.io/overlays/elevance-health/elevance-health-conformance-api-overlay/)
- [Elevance Health Coverage Api Overlay](https://apis.io/overlays/elevance-health/elevance-health-coverage-api-overlay/)
- [Elevance Health Patient Api Overlay](https://apis.io/overlays/elevance-health/elevance-health-patient-api-overlay/)
- [Elevance Health Provider Directory Api Overlay](https://apis.io/overlays/elevance-health/elevance-health-provider-directory-api-overlay/)

#### Security (2)

Authentication, trust centre, and vulnerability disclosure.

- [Elevance Health Authentication](https://apis.io/security/elevance-health/elevance-health-authentication/)
- [Elevance Health Domain Security](https://apis.io/security/elevance-health/elevance-health-domain-security/)

#### OAuth scopes (1)

The permissions the API asks for.

- [Elevance Health Scopes](https://apis.io/scopes/elevance-health/elevance-health-scopes/)

#### Plans and pricing (1)

Published plans, tiers and prices.

- [Elevance Health Plans Pricing](https://apis.io/plans/elevance-health/elevance-health-plans-pricing/)

#### Rate limits (1)

Published request limits.

- [Elevance Health Rate Limits](https://apis.io/rate-limits/elevance-health/elevance-health-rate-limits/)

#### FinOps (1)

What the API costs to run, by operation.

- [Elevance Health Finops](https://apis.io/finops/elevance-health/elevance-health-finops/)

## Where to find this API

Links to the company's own pages. This repository publishes no copy of their specifications — the canonical document is theirs and lives at the URLs below.

- [Website](https://www.elevancehealth.com)
- [Documentation](https://patient360c.anthem.com/P360Member/fhir/documentation)
- [Getting started](https://www.anthem.com/developers)
- [API reference](https://www.anthem.com/content/dam/digital/developers-portal/Anthem-IOProviderDirectoryAndFormulary-API-Documentation.pdf)
- [Sign up](https://www.anthem.com/developers/request-anthem-io)
- [Support](https://www.anthem.com/contact-us)
- [Blog](https://www.anthem.com/blog)
- [Terms of service](https://www.anthem.com/terms-of-use)
- [Privacy policy](https://www.elevancehealth.com/privacy-policy)
- [GitHub](https://github.com/openanthem)

## API Evangelist rating

**Kin Score 44.3** — developing · rubric 0.25.0 · scored 2026-10-23

| Facet | Score |
|---|---|
| Discoverability | 66.1 |
| Contract quality | 51.3 |
| Contract governance | 18.2 |
| Operational transparency | 18.4 |
| Developer ergonomics | 51.8 |
| Access clarity | 22.4 |

**Agent readiness 38.4** — agent-ready

| Agent-readiness dimension | Result |
|---|---|
| Spec Presence | yes |
| Agentic Access | derived (partial credit) |
| Reversibility Documented | na |
| MCP Server | — |
| Auth Clarity | served (partial credit) |
| Idempotency | na |
| Error Semantics | documented (partial credit) |
| OpenAPI Examples | — |
| Rate Limit Signal | documented (partial credit) |
| Event Surface Described | — |
| Agent Skills | derived (partial credit) |
| Well Known Catalog | — |
| Consent Identity | — |
| Agent Card | — |
| Dry Run Mode | na |
| Delegated Identity | served (partial credit) |
| Protected Resource Metadata | — |
| Dynamic Client Registration | — |
| Agentic Commerce | — |
| Pagination Ratio | na |
| Operation Distinctiveness | distinct |

**Regulatory alignment 48.4** — Health

The rubric is published at [github.com/api-evangelist/kin-score](https://github.com/api-evangelist/kin-score). The per-check breakdown behind these numbers — which checks were earned, partial or missed — along with score history and how this provider compares to its peers, is available at [apis.io/providers/elevance-health/](https://apis.io/providers/elevance-health/).

## How this profile is made

API Evangelist profiles a company's public API surface the way a developer would find it: the website, developer portal and documentation, the specifications it publishes, its public repositories, and its pricing, status and changelog pages. From that it derives the properties above — contracts split per API, workflows, schemas, collections, governance rules, plans and rate limits — and scores them against the published [Kin Score rubric](https://github.com/api-evangelist/kin-score).

The artifacts are published on [APIs.io](https://apis.io), not in this repository. This repository is the public record for Elevance Health: the place to say something is wrong, missing or out of date, and to ask for a re-score or a removal.

## Open an issue

- **Something about this listing** — a wrong description, a missing API, a stale artifact or a question about the rating: [open an issue on this repository](https://github.com/api-evangelist/elevance-health/issues/new).
- **A new API, or one that is not in the catalog yet** — [submit it on APIs.io](https://apis.io/add/).
- **Anything else** — [the APIs.io inbox](https://github.com/api-search/inbox/issues/new) or [info@apievangelist.com](mailto:info@apievangelist.com).
