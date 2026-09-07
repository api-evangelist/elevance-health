---
name: elevance-health-retrieve-member-claims
description: Retrieve a consenting Elevance Health member's coverage and claims history over SMART on FHIR, with the consent, paging and error rules that actually apply.
api: elevance-health:elevance-health-claims-api
operations:
  - getCapabilityStatement
  - searchPatient
  - readPatient
  - searchCoverage
  - readCoverage
  - searchClaim
generated: '2026-09-07'
method: generated
source: >-
  openapi/elevance-health-claims-api-openapi.yml, openapi/elevance-health-coverage-api-openapi.yml
  and openapi/elevance-health-patient-api-openapi.yml, verified against the live conformance
  statement at https://patient360.anthem.com/P360Member/api/fhir/metadata and the SMART configuration
  at https://patient360c.anthem.com/P360Member/api/fhir/.well-known/smart-configuration (both HTTP 200, 2026-09-07)
---

# Retrieve a member's coverage and claims

This is member health data. It cannot be reached without an individual member completing an
authorization flow in a browser. There is no unattended path, and you should not attempt to build
one.

## Before you start

- Your application must be registered. Sandbox registration is self-service at
  `https://sbx.totalview.healthos.elevancehealth.com/registration/sandbox/login`. Production
  requires the form at `https://www.anthem.com/developers/request-anthem-io`, a documented security
  risk analysis, and approval that Elevance says can take several weeks.
- Develop against the sandbox first. It carries synthetic data and the same SMART flow.

## Steps

1. **Confirm the contract.** Run `getCapabilityStatement` against your base URL. Follow
   `elevance-health-discover-fhir-capabilities` if you have not already.

2. **Fetch the SMART configuration** at `{base}/.well-known/smart-configuration`. Take
   `authorization_endpoint`, `token_endpoint` and `scopes_supported` from it. Do not hard-code
   these; they differ per surface.

3. **Request only the scopes you will use.** Ask for `patient/Patient.read`,
   `patient/Coverage.read` and `patient/Claim.read` rather than `patient/*.read`. Add
   `offline_access` only if you genuinely need refresh, and `launch/patient` for standalone launch.

4. **Run the authorization code flow with PKCE.** `code_challenge_method=S256`. The member
   authenticates and consents; you receive a token bound to that member's patient context.
   Production Patient Access tokens are valid for **90 days**, after which continued access
   requires renewed member consent — plan for re-consent, not silent refresh forever.

5. **Resolve the patient.** Call `readPatient` (`GET /Patient/{id}`) with the id from the token's
   patient context. Use `searchPatient` only when you have an identifier and no context;
   it accepts `identifier`, `birthdate`, `family` and `given`.

6. **Get coverage.** `searchCoverage` — `GET /Coverage?patient={patientId}` — then `readCoverage`
   for any individual policy you need in full.

7. **Get claims.** `searchClaim` — `GET /Claim?patient={patientId}`.

8. **Page to completion.** Responses are FHIR Bundles. Follow `Bundle.link` where
   `relation` is `next` until it is absent. Do not assume the first Bundle is the whole answer;
   Elevance publishes up to five years of history.

## Which claims resource

This matters and it is easy to get wrong.

- On the **R4 Patient Access** surface, `ExplanationOfBenefit` is the CARIN Blue Button resource
  and is supported — it has 14 search parameters, the richest on the estate.
- On the **DSTU2 Patient360** surface, `ExplanationOfBenefit` is **not supported**. The live
  conformance statement declares 32 resource types and it is not among them. Use `Claim` there.
  Any spec in this repository that shows an `/ExplanationOfBenefit` path against the Patient360
  base is describing an operation the server does not implement; the overlay at
  `overlays/elevance-health-claims-api-overlay.yaml` records this.

## Error handling

- **403, empty body** — your application is not registered for this surface.
- **401** — token missing, expired, or the 90-day consent has lapsed. Re-run consent.
- **405** — you attempted a write. Every CMS surface is read-only.
- **400** — you used a search parameter the resource does not declare. Re-read `searchParam[]`.
- **500** — a proprietary gateway envelope, `{"status_code":500,"status":"failed",...}`, not a FHIR
  OperationOutcome. Retry with your own exponential backoff. There is no `Retry-After` header, no
  published rate limit, and no status page to check.

## Rules

- Retrieve the minimum necessary. This is PHI under HIPAA; scope requests narrowly and do not
  persist more than your stated purpose requires.
- Never retry a write. There is no idempotency mechanism anywhere on this estate — no
  `Idempotency-Key` header, and the DSTU2 server explicitly declares `conditionalCreate` false,
  `conditionalUpdate` false and `conditionalDelete` not-supported.
- Never construct a base URL. Use one of the thirteen published brand bases verbatim.
