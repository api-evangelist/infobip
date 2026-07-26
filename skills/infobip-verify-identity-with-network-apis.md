---
name: Verify identity with CAMARA network APIs
description: Use the Infobip CAMARA implementation to verify a phone number against the mobile network,
  check for a recent SIM swap, verify device location, and run a KYC match.
api: openapi/infobip-camara-openapi.json
operations:
- authorize-number-verify
- verify-number
- verify-number-v2
- sim-swap-check
- sim-swap-retrieve-date
- verify-device-location
- know-your-customer-match
provider: Infobip
generated: '2026-07-25'
method: generated
source: Grounded in operationIds verified in openapi/infobip-camara-openapi.json plus conventions/infobip-conventions.yml,
  errors/infobip-error-codes.yml and rate-limits/infobip-rate-limits.yml
---

# Verify identity with CAMARA network APIs

Use the Infobip CAMARA implementation to verify a phone number against the mobile network, check for a recent SIM swap, verify device location, and run a KYC match.

## Ground rules for every Infobip call

- Base URL: `https://api.infobip.com` (an account may also be issued a personalized `https://{subdomain}.api.infobip.com` host shown in the web portal — either works).
- Auth header: `Authorization: App {API_KEY}`. Basic auth is only for the API-key-management endpoints. Every endpoint additionally requires at least one API scope (see `scopes/infobip-scopes.yml`).
- There is **no idempotency key**. Never blind-retry a send on a timeout or 5xx — re-read the outcome with the reports/logs operation for the returned `bulkId`/`messageId` first (`conventions/infobip-conventions.yml`).
- On `429` back off exponentially and honour `Retry-After`. Per-operation limits are published in the spec as `x-throttling-info` and collected in `rate-limits/infobip-rate-limits.yml`.
- HTTP errors use the Infobip `requestError.serviceException {messageId, text, validationErrors}` envelope (not RFC 9457) — see `errors/infobip-problem-types.yml`.
- A `200` does **not** mean delivered. Message outcome lives in the `status {groupId, groupName, id, name}` and `error {groupId, groupName, id, name, permanent}` objects; resolve them against `errors/infobip-error-codes.yml`. `permanent: true` means a retry can never succeed.
- Listing endpoints page with `page`/`size` (max 100) and return `{page, size, totalPages, totalResults}`; newer endpoints support `cursor`/`useCursor`.

## Steps
These are CAMARA-conformant network APIs, so they follow CAMARA conventions rather than the classic Infobip ones: send the `x-correlator` header and expect it echoed back for tracing.

1. **Number verification (silent, network-based)** — `authorize-number-verify` (`GET /camara/number-verification/v0/authorize`) starts the device authorization over the mobile data connection, then `verify-number` (`POST /camara/number-verification/v0/verify`) confirms the number. The v2 surface (`verify-number-v2`, `create-dcql-request`, `get-device-phone-number`) is the SIM-based flow.
2. **SIM swap** — `sim-swap-check` (`POST /camara/sim-swap/v0/check`) answers "has this SIM changed within N hours"; `sim-swap-retrieve-date` (`POST /camara/sim-swap/v0/retrieve-date`) returns the actual last-swap timestamp. Run this **before** you trust an OTP delivered to that number.
3. **Device location** — `verify-device-location` (`POST /camara/location/v0/verify`) checks a device against a coordinate + radius; it verifies, it does not return a position.
4. **KYC match** — `know-your-customer-match` (`POST /camara/kyc-match/v0.3/match`) compares the identity attributes you hold against the operator's record and returns per-attribute match results.
5. **Coverage is per operator.** A negative or unavailable result is normal in markets where the operator does not expose the capability — treat "not supported" as a distinct branch from "does not match", and never fail the user closed on it alone.
