---
name: Send an SMS and confirm delivery
description: Send SMS through the Infobip SMS API, receive the delivery report, and resolve the status/error
  codes into a real delivery outcome.
api: openapi/infobip-sms-openapi.json
operations:
- send-sms-messages
- get-outbound-sms-message-delivery-reports-v3
- get-outbound-sms-message-logs-v3
- get-inbound-sms-messages
- preview-sms-message
provider: Infobip
generated: '2026-07-25'
method: generated
source: Grounded in operationIds verified in openapi/infobip-sms-openapi.json plus conventions/infobip-conventions.yml,
  errors/infobip-error-codes.yml and rate-limits/infobip-rate-limits.yml
---

# Send an SMS and confirm delivery

Send SMS through the Infobip SMS API, receive the delivery report, and resolve the status/error codes into a real delivery outcome.

## Ground rules for every Infobip call

- Base URL: `https://api.infobip.com` (an account may also be issued a personalized `https://{subdomain}.api.infobip.com` host shown in the web portal — either works).
- Auth header: `Authorization: App {API_KEY}`. Basic auth is only for the API-key-management endpoints. Every endpoint additionally requires at least one API scope (see `scopes/infobip-scopes.yml`).
- There is **no idempotency key**. Never blind-retry a send on a timeout or 5xx — re-read the outcome with the reports/logs operation for the returned `bulkId`/`messageId` first (`conventions/infobip-conventions.yml`).
- On `429` back off exponentially and honour `Retry-After`. Per-operation limits are published in the spec as `x-throttling-info` and collected in `rate-limits/infobip-rate-limits.yml`.
- HTTP errors use the Infobip `requestError.serviceException {messageId, text, validationErrors}` envelope (not RFC 9457) — see `errors/infobip-problem-types.yml`.
- A `200` does **not** mean delivered. Message outcome lives in the `status {groupId, groupName, id, name}` and `error {groupId, groupName, id, name, permanent}` objects; resolve them against `errors/infobip-error-codes.yml`. `permanent: true` means a retry can never succeed.
- Listing endpoints page with `page`/`size` (max 100) and return `{page, size, totalPages, totalResults}`; newer endpoints support `cursor`/`useCursor`.

## Steps
1. **(Optional) Preview the message** — `preview-sms-message` (`POST /sms/1/preview`) tells you how the text will be split into segments and which character set/transliteration applies before you spend money on it.
2. **Send** — `send-sms-messages` (`POST /sms/3/messages`). Put each recipient in `messages[].destinations[]`, the sender in `messages[].sender`, and set `messages[].webhooks.delivery.url` if you want a delivery-report callback instead of polling. The response returns `bulkId` and a `messages[]` array with one `messageId` + `status` per destination.
3. **Do not re-send on a timeout.** There is no idempotency key. If the call fails without a response, call `get-outbound-sms-message-logs-v3` (`GET /sms/3/logs`) filtered by your `bulkId` to see whether the send actually landed.
4. **Read the outcome.** Either consume the `receive-outbound-sms-message-reports-v3` webhook, or poll `get-outbound-sms-message-delivery-reports-v3` (`GET /sms/3/reports?bulkId=...`). Reports are consumed once when polled — a report returned to you will not be returned again.
5. **Interpret it.** `status.groupName` of `DELIVERED` is success; `PENDING` means still in flight; `UNDELIVERABLE`, `EXPIRED` and `REJECTED` are failures, and the `error` object names why (for example `EC_ABSENT_SUBSCRIBER`, `REJECTED_NOT_ENOUGH_CREDITS`). Only retry when `error.permanent` is `false`.
6. **Inbound replies** arrive on the `receive-inbound-sms-messages` webhook, or can be pulled with `get-inbound-sms-messages` (`GET /sms/1/inbox/reports`).

Scheduling: `get-scheduled-sms-messages`, `reschedule-sms-messages`, `get-scheduled-sms-messages-status` and `update-scheduled-sms-messages-status` operate on a whole `bulkId`.
