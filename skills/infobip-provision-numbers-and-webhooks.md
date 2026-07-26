---
name: Provision a number and wire up its webhooks
description: Search, purchase and configure an Infobip number, then attach the SMS/MMS/voice inbound configuration
  and webhook endpoints that route traffic back to you.
api: openapi/infobip-numbers-openapi.json
operations:
- get-available-numbers
- purchase-number
- list-owned-numbers
- create-new-configuration
- create-mms-configuration
- create-voice-setup-on-number
- update-owned-number
provider: Infobip
generated: '2026-07-25'
method: generated
source: Grounded in operationIds verified in openapi/infobip-numbers-openapi.json plus conventions/infobip-conventions.yml,
  errors/infobip-error-codes.yml and rate-limits/infobip-rate-limits.yml
---

# Provision a number and wire up its webhooks

Search, purchase and configure an Infobip number, then attach the SMS/MMS/voice inbound configuration and webhook endpoints that route traffic back to you.

## Ground rules for every Infobip call

- Base URL: `https://api.infobip.com` (an account may also be issued a personalized `https://{subdomain}.api.infobip.com` host shown in the web portal — either works).
- Auth header: `Authorization: App {API_KEY}`. Basic auth is only for the API-key-management endpoints. Every endpoint additionally requires at least one API scope (see `scopes/infobip-scopes.yml`).
- There is **no idempotency key**. Never blind-retry a send on a timeout or 5xx — re-read the outcome with the reports/logs operation for the returned `bulkId`/`messageId` first (`conventions/infobip-conventions.yml`).
- On `429` back off exponentially and honour `Retry-After`. Per-operation limits are published in the spec as `x-throttling-info` and collected in `rate-limits/infobip-rate-limits.yml`.
- HTTP errors use the Infobip `requestError.serviceException {messageId, text, validationErrors}` envelope (not RFC 9457) — see `errors/infobip-problem-types.yml`.
- A `200` does **not** mean delivered. Message outcome lives in the `status {groupId, groupName, id, name}` and `error {groupId, groupName, id, name, permanent}` objects; resolve them against `errors/infobip-error-codes.yml`. `permanent: true` means a retry can never succeed.
- Listing endpoints page with `page`/`size` (max 100) and return `{page, size, totalPages, totalResults}`; newer endpoints support `cursor`/`useCursor`.

## Steps
1. **Search inventory** — `get-available-numbers` (`GET /numbers/1/numbers/available`) filtered by `country`, `capabilities` and `type`. Keep the `numberKey`.
2. **Purchase** — `purchase-number` (`POST /numbers/1/numbers`). This is a billable, non-idempotent write: if the call times out, call `list-owned-numbers` (`GET /numbers/1/numbers`) and check before retrying.
3. **Configure inbound SMS** — `create-new-configuration` (`POST /numbers/2/numbers/{numberKey}/sms`) with the keyword/`notifyUrl` routing you want; `list-configurations-for-number` and `modify-sms-configurations` manage it afterwards.
4. **Configure MMS and voice** — `create-mms-configuration` (`POST /numbers/2/numbers/{numberKey}/mms`) and `create-voice-setup-on-number` (`POST /numbers/2/numbers/{numberKey}/voice`); `update-cnam` sets the caller name where supported.
5. **Verify the endpoint before you rely on it.** The Subscriptions Management API exposes a test-connection-to-webhook operation, and every callback Infobip can send is catalogued in `asyncapi/infobip-webhooks.yml`. Secure the endpoint with a bearer token, basic auth or a message signature, and dedupe on the payload's event identifier — Infobip retries.
6. **Release** — `cancel-number` (`DELETE /numbers/1/numbers/{numberKey}`) stops the recurring charge.
