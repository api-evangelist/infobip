---
name: Send omnichannel with failover
description: Use the Messages API to send one payload across channels with an ordered failover chain,
  and read a single normalized delivery report.
api: openapi/infobip-messages-api-openapi.json
operations:
- validate-messages-api-message
- send-messages-api-message
- get-messages-api-delivery-reports
- get-messages-api-inbound-messages
- send-messages-api-events
provider: Infobip
generated: '2026-07-25'
method: generated
source: Grounded in operationIds verified in openapi/infobip-messages-api-openapi.json plus conventions/infobip-conventions.yml,
  errors/infobip-error-codes.yml and rate-limits/infobip-rate-limits.yml
---

# Send omnichannel with failover

Use the Messages API to send one payload across channels with an ordered failover chain, and read a single normalized delivery report.

## Ground rules for every Infobip call

- Base URL: `https://api.infobip.com` (an account may also be issued a personalized `https://{subdomain}.api.infobip.com` host shown in the web portal — either works).
- Auth header: `Authorization: App {API_KEY}`. Basic auth is only for the API-key-management endpoints. Every endpoint additionally requires at least one API scope (see `scopes/infobip-scopes.yml`).
- There is **no idempotency key**. Never blind-retry a send on a timeout or 5xx — re-read the outcome with the reports/logs operation for the returned `bulkId`/`messageId` first (`conventions/infobip-conventions.yml`).
- On `429` back off exponentially and honour `Retry-After`. Per-operation limits are published in the spec as `x-throttling-info` and collected in `rate-limits/infobip-rate-limits.yml`.
- HTTP errors use the Infobip `requestError.serviceException {messageId, text, validationErrors}` envelope (not RFC 9457) — see `errors/infobip-problem-types.yml`.
- A `200` does **not** mean delivered. Message outcome lives in the `status {groupId, groupName, id, name}` and `error {groupId, groupName, id, name, permanent}` objects; resolve them against `errors/infobip-error-codes.yml`. `permanent: true` means a retry can never succeed.
- Listing endpoints page with `page`/`size` (max 100) and return `{page, size, totalPages, totalResults}`; newer endpoints support `cursor`/`useCursor`.

## Steps
1. **Validate first** — `validate-messages-api-message` (`POST /messages-api/1/messages/validate`) checks the payload without sending. Cheap insurance against `REJECTED_VALIDATION_FAILED`.
2. **Send** — `send-messages-api-message` (`POST /messages-api/1/messages`). One request carries `messages[].channel` content plus an ordered failover chain, so a WhatsApp attempt can fall back to SMS or Viber without you orchestrating it. The response returns `messageId` per message.
3. **Read one report shape for every channel** — `get-messages-api-delivery-reports` (`GET /messages-api/1/reports`), or the corresponding webhook. Channel-specific `error.name` values still surface, so resolve them against `errors/infobip-error-codes.yml`.
4. **Inbound** — `get-messages-api-inbound-messages` (`GET /messages-api/1/inbound`) pulls replies across channels; `send-messages-api-events` reports read/typing events back.
5. If you need channel-native features the unified payload does not expose (WhatsApp flows, RCS carousels, voice IVR), drop to the channel API and keep the omni-failover chain in `openapi/infobip-omni-failover-openapi.json`.
