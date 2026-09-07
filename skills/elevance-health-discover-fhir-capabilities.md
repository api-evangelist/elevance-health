---
name: elevance-health-discover-fhir-capabilities
description: Read what an Elevance Health FHIR endpoint actually supports before calling it — resource types, interactions, search parameters and OAuth endpoints — from the server's own contract.
api: elevance-health:elevance-health-conformance-api
operations:
  - getCapabilityStatement
generated: '2026-09-07'
method: generated
source: openapi/elevance-health-conformance-api-openapi.yml, verified against the live contract at https://patient360.anthem.com/P360Member/api/fhir/metadata (HTTP 200, 2026-09-07)
---

# Discover what an Elevance Health FHIR endpoint supports

Do this first, every time. Elevance Health publishes no OpenAPI. Its contracts are FHIR
CapabilityStatements that each server publishes about itself, and they are the only authoritative
description of what a given base URL will do. They also differ substantially between surfaces —
one is FHIR DSTU2 and read/write, the others are FHIR R4 and read-only.

## Steps

1. **Pick the right base URL.** There is no routing endpoint; you must choose.

   | Surface | Base URL | FHIR |
   |---|---|---|
   | Patient Access (production) | `https://totalview.healthos.elevancehealth.com/resources/registered/{Brand}/api/v1/fhir` | R4 |
   | Provider Directory | `https://totalview.healthos.elevancehealth.com/resources/unregistered/api/v1/fhir/cms_mandate/mcd/` | R4 |
   | Formulary | `https://totalview.healthos.elevancehealth.com/resources/unregistered/api/v1/fhir/cms_mandate/frmlry` | R4 |
   | Patient360 (legacy) | `https://patient360.anthem.com/P360Member/api/fhir` | DSTU2 |

   `{Brand}` is one of thirteen values — `AnthemBlueCross`, `AnthemBlueCrossBlueShield`,
   `Amerigroup`, `BlueMedicareAdvantage`, `ClearHealthAlliance`, `DellChildrenHealthPlan`,
   `HealthyBlue`, `HealthyBlueBlueChoice`, `HealthyBlueNC`, `SimplyHealthCare`, `Summit`,
   `Unicare`, `Wellpoint`. Use the brand that issued the member's plan.

2. **Call `getCapabilityStatement`** — `GET {base}/metadata` with `Accept: application/fhir+json`.
   No authentication is required for this call on the Provider Directory and Patient360 bases.

3. **Read `fhirVersion` first.** `4.0.1` means R4; `1.0.2` means DSTU2 and a different resource
   vocabulary (`MedicationOrder` not `MedicationRequest`, `DiagnosticOrder` not `ServiceRequest`).
   Do not carry an R4 query shape onto the DSTU2 base.

4. **Enumerate what you may do.** For each `rest[].resource[]`, read `type` and `interaction[].code`.
   `search-type`, `read` and `vread` are reads. If `create`, `update` or `delete` is absent, the
   surface is read-only and a write is a 405, not a permissions problem.

5. **Take your query parameters from the contract, not from a guess.** Each resource declares its
   own `searchParam[]`. Parameters outside that list are rejected, not ignored. `_id` and
   `_lastUpdated` are available on every resource.

6. **Read the OAuth endpoints from the same place.** On DSTU2 they are in the
   `oauth-uris` extension under `rest.security`. On every surface they are also at
   `{base}/.well-known/smart-configuration`, which additionally gives you the scope list and the
   PKCE methods.

## What to expect

- The Provider Directory `/metadata` answers anonymously and returns 8 resources, 25 interactions.
- The Patient360 `/metadata` answers anonymously and returns 32 resources, 161 interactions, 16
  system operations. It is ~190KB; request `Accept: application/fhir+json` and stream it.
- The registered Patient Access tenants may time out on `/metadata` anonymously. The same content
  is available from the documentation feed at
  `https://totalview.healthos.elevancehealth.com/api/v1/fhir/docs`.
- Formulary `/metadata` returns **403** with an empty body until your application is registered.
  This is expected and is not an error in your request.

## Rules

- Never assume a resource exists because it exists in FHIR. Check the contract. The Patient360
  server does **not** support `ExplanationOfBenefit`, despite it being the natural CARIN resource
  for claims — use `Claim` there instead.
- The contract is the schema. Do not invent field names; every resource is a standard HL7 FHIR
  resource whose fields are defined at `https://hl7.org/fhir/R4/<resource>.html`. Elevance's own
  extensions are documented in `conformance/elevance-health-fhir-extensions.json`.
