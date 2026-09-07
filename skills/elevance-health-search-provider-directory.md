---
name: elevance-health-search-provider-directory
description: Look up in-network practitioners, organizations, locations and insurance plans in the Elevance Health provider directory — the one surface an unattended agent can legitimately use.
api: elevance-health:elevance-health-provider-directory-api
operations:
  - getCapabilityStatement
  - readPractitioner
  - readOrganization
generated: '2026-09-07'
method: generated
source: >-
  openapi/elevance-health-provider-directory-api-openapi.yml, plus the live Provider Directory
  CapabilityStatement at
  https://totalview.healthos.elevancehealth.com/resources/unregistered/api/v1/fhir/cms_mandate/mcd/metadata
  (HTTP 200, 2026-09-07) and the Interoperability API Endpoint Support Document IO105 v15.0
---

# Search the Elevance Health provider directory

This is the only Elevance Health surface that carries no member PHI and needs no individual's
consent. If you are building an agent against Elevance, this is where it can actually operate.

## Base URL

```
https://totalview.healthos.elevancehealth.com/resources/unregistered/api/v1/fhir/cms_mandate/mcd/
```

FHIR R4 (4.0.1), Da Vinci PDEX Plan Net 1.1.0, US Core STU 3.1.1. Read-only: the contract declares
only `search-type`, `read` and `vread` on all eight resource types.

## Authentication

OAuth 2.0 client credentials. Register at
`https://www.anthem.com/developers/provider-directory-api-request`; Elevance emails you a client id,
a client secret and the token endpoint URL. The token endpoint is **not published** — you cannot
discover it, and you should not guess it.

```
POST <access token endpoint URL>
Content-Type: application/x-www-form-urlencoded
Authorization: Basic <base64 client_id:client_secret>

grant_type=client_credentials
```

Then send `Authorization: Bearer <token>` on every data request.

## Resources and their search parameters

Taken from the live capability statement. Do not use a parameter that is not listed for the
resource; it will be rejected rather than ignored.

| Resource | What it holds | Search parameters |
|---|---|---|
| `InsurancePlan` | The plans themselves | `_id`, `_lastUpdated`, `coverage-area`, `identifier`, `name`, `type` |
| `Practitioner` | Individual clinicians | `_id`, `_lastUpdated`, `name`, `family`, `given` |
| `PractitionerRole` | A clinician's role at an org, in a network | `_id`, `_lastUpdated`, `practitioner`, `organization`, `location`, `service`, `network`, `role`, `specialty` |
| `Organization` | Provider organizations | `_id`, `_lastUpdated`, `name`, `type`, `address` |
| `OrganizationAffiliation` | Org-to-network relationships | `_id`, `_lastUpdated`, `participating-organization`, `primary-organization`, `location`, `service`, `network`, `specialty`, `role` |
| `Location` | Physical sites | `_id`, `_lastUpdated`, `name`, `address`, `address-city`, `address-state`, `address-postalcode` |
| `HealthcareService` | Services offered | `_id`, `_lastUpdated`, `name`, `organization`, `location`, `specialty`, `service-type`, `service-category` |
| `Specimen` | — | `_id`, `_lastUpdated`, and 2 others |

## Steps

1. **Confirm the contract.** `GET {base}metadata` — this answers anonymously, so do it before you
   even have credentials, to check the resource set has not changed.
2. **Get a token** via client credentials, as above.
3. **Start from the plan, not the practitioner.** "In-network" is a property of the relationship,
   not of the clinician. Find the plan with
   `GET {base}InsurancePlan?name={planName}`.
4. **Traverse to participation.** `PractitionerRole` and `OrganizationAffiliation` carry the
   `network` reference that makes a provider in-network for that plan. Query
   `GET {base}PractitionerRole?network={networkRef}&specialty={system}|{code}`.
5. **Expand references in one call.** Use `_include` rather than a second round trip:
   `GET {base}PractitionerRole?network={ref}&_include=PractitionerRole:practitioner&_include=PractitionerRole:location`.
6. **Page to completion** by following `Bundle.link[relation=next]`.
7. **Read individual records** with `readPractitioner` (`GET /Practitioner/{id}`) or
   `readOrganization` (`GET /Organization/{id}`) once you have ids.

## What to expect

- The `/metadata` endpoint is reliably available. The **data plane is not**: on 2026-09-07 a
  `GET {base}InsurancePlan?_count=1` returned HTTP 500 with
  `{"status_code":500,"status":"failed","error":"Internal server error"}` while `/metadata` on the
  same base returned 200. Treat 500 as transient, retry with backoff, and do not conclude your
  query is malformed.
- There is no published rate limit and no `Retry-After` header. Choose your own conservative
  backoff and cache aggressively — directory data changes slowly and `_lastUpdated` lets you fetch
  deltas.

## Rules

- Never write. The surface declares no `create`, `update` or `delete`, and there is no
  idempotency mechanism if it did.
- Do not guess the token endpoint. It is issued privately per application.
- Cache by `_lastUpdated` rather than re-crawling; this is a directory of tens of thousands of
  records behind an API with no published capacity guidance.
