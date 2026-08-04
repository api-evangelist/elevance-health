# Elevance Health (elevance-health)

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

Elevance Health (formerly Anthem) is a Fortune 500 health benefits company that serves members through Blue Cross and Blue Shield affiliated health plans across multiple states. The company offers medical, pharmacy, dental, vision, and other specialty insurance and exposes a set of CMS Interoperability and Patient Access FHIR APIs to enable members, providers, and partner payers to securely exchange coverage, clinical, claims, provider directory, and formulary data.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/elevance-health/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/elevance-health/refs/heads/main/apis.yml)

## Scope

- **Type:** Index
- **Position:** Consuming
- **Access:** 3rd-Party

## Tags

- Fortune 500
- Healthcare
- Health Insurance
- FHIR
- Interoperability

## Timestamps

- **Created:** 2026-03-21
- **Modified:** 2026-04-28

## APIs

### Elevance Health Patient Access API

The Patient Access API enables Anthem and Elevance Health members to securely access and exchange their medical, pharmacy, dental, and vision claims and clinical data through third-party applications. Built on the HL7 FHIR R4 specification and aligned with the CARIN Consumer Directed Payer Data Exchange Implementation Guide, the API supports up to five years of historical claims and clinical data.

- **Human URL:** [https://www.anthem.com/developers](https://www.anthem.com/developers)
- **Base URL:** `https://patient360.anthem.com/P360Member/fhir`

#### Tags

- FHIR
- Healthcare
- Health Insurance
- Patient Access
- Interoperability

#### Properties

- [Documentation](https://patient360c.anthem.com/P360Member/fhir/documentation)
- [Developer Portal](https://www.anthem.com/developers)
- [Postman Collection](collections/elevance-health.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/elevance-health.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Elevance Health Provider Directory API

The Provider Directory API exposes Elevance Health network provider information including practitioners, practitioner roles, organizations, locations, and insurance plans. The API conforms to the HL7 FHIR R4 specification and the DaVinci PDEX Plan Net Implementation Guide and does not require authentication for public directory data.

- **Human URL:** [https://www.anthem.com/developers](https://www.anthem.com/developers)

#### Tags

- FHIR
- Provider Directory
- Healthcare
- Interoperability

#### Properties

- [Documentation](https://www.anthem.com/developers)
- [Postman Collection](collections/elevance-health.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/elevance-health.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Elevance Health Formulary API

The Formulary API publishes Elevance Health drug coverage information including covered drug lists, tier placement, prior authorization requirements, and step therapy rules. The API conforms to the HL7 FHIR R4 specification and the DaVinci PDEX US Drug Formulary Implementation Guide.

- **Human URL:** [https://www.anthem.com/developers](https://www.anthem.com/developers)

#### Tags

- FHIR
- Formulary
- Pharmacy
- Healthcare
- Interoperability

#### Properties

- [Documentation](https://www.anthem.com/developers)
- [Postman Collection](collections/elevance-health.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/elevance-health.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Elevance Health Payer to Payer API

The Payer to Payer API enables Elevance Health to exchange member coverage and clinical data with other health plans when members move between payers, supporting the CMS Interoperability and Prior Authorization rule. The API is built on the HL7 FHIR R4 specification.

- **Human URL:** [https://www.anthem.com/developers](https://www.anthem.com/developers)

#### Tags

- FHIR
- Payer to Payer
- Healthcare
- Interoperability

#### Properties

- [Documentation](https://www.anthem.com/developers)
- [Postman Collection](collections/elevance-health.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/elevance-health.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

## Common Properties

- [LinkedIn](https://www.linkedin.com/company/elevance-health)
- [Website](https://www.elevancehealth.com)
- [Developer Portal](https://www.anthem.com/developers)
- [Documentation](https://patient360c.anthem.com/P360Member/fhir/documentation)
- [Sign Up](https://www.anthem.com/developers/request-anthem-io)

## Maintainers

**FN:** API Evangelist
**Email:** info@apievangelist.com
