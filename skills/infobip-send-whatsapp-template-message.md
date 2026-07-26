---
name: Send a WhatsApp template message and handle the session
description: Open a WhatsApp Business conversation with an approved template, then continue within the
  24-hour session using free-form and interactive messages.
api: openapi/infobip-whatsapp-openapi.json
operations:
- send-whatsapp-template-message
- send-whatsapp-text-message
- send-whatsapp-interactive-buttons-message
- send-whatsapp-image-message
- send-whatsapp-interactive-list-message
provider: Infobip
generated: '2026-07-25'
method: generated
source: Grounded in operationIds verified in openapi/infobip-whatsapp-openapi.json plus conventions/infobip-conventions.yml,
  errors/infobip-error-codes.yml and rate-limits/infobip-rate-limits.yml
---

# Send a WhatsApp template message and handle the session

Open a WhatsApp Business conversation with an approved template, then continue within the 24-hour session using free-form and interactive messages.

## Ground rules for every Infobip call

- Base URL: `https://api.infobip.com` (an account may also be issued a personalized `https://{subdomain}.api.infobip.com` host shown in the web portal — either works).
- Auth header: `Authorization: App {API_KEY}`. Basic auth is only for the API-key-management endpoints. Every endpoint additionally requires at least one API scope (see `scopes/infobip-scopes.yml`).
- There is **no idempotency key**. Never blind-retry a send on a timeout or 5xx — re-read the outcome with the reports/logs operation for the returned `bulkId`/`messageId` first (`conventions/infobip-conventions.yml`).
- On `429` back off exponentially and honour `Retry-After`. Per-operation limits are published in the spec as `x-throttling-info` and collected in `rate-limits/infobip-rate-limits.yml`.
- HTTP errors use the Infobip `requestError.serviceException {messageId, text, validationErrors}` envelope (not RFC 9457) — see `errors/infobip-problem-types.yml`.
- A `200` does **not** mean delivered. Message outcome lives in the `status {groupId, groupName, id, name}` and `error {groupId, groupName, id, name, permanent}` objects; resolve them against `errors/infobip-error-codes.yml`. `permanent: true` means a retry can never succeed.
- Listing endpoints page with `page`/`size` (max 100) and return `{page, size, totalPages, totalResults}`; newer endpoints support `cursor`/`useCursor`.

## Steps
1. **Outside a session you must use a template.** Call `send-whatsapp-template-message` (`POST /whatsapp/1/message/template`) with `messages[].content.templateName`, `templateData.body.placeholders[]` and `language`. Templates must already be approved — the WhatsApp spec also exposes template-management operations for creating and checking them.
2. **Capture the identifiers.** The response returns `messages[].messageId` and a `status` object per recipient. Store `messageId` — delivery reports, seen reports and logs all key off it.
3. **Inside the 24-hour customer service window** you may send free-form content: `send-whatsapp-text-message`, `send-whatsapp-image-message`, `send-whatsapp-document-message`, and the interactive family (`send-whatsapp-interactive-buttons-message`, `send-whatsapp-interactive-list-message`, `send-whatsapp-interactive-flow-message`). Outside it, go back to a template.
4. **Consume the events.** `receive-inbound-whatsapp-messages` gives you customer replies (this is what resets the session window), `receive-whatsapp-delivery-reports` gives delivery outcome, `receive-whatsapp-seen-reports` gives read receipts, and `receive-whatsapp-message-template-update-events` tells you when a template's approval status changes.
5. **Failures are channel-specific.** Resolve `error.name` against the WhatsApp/chat families in `errors/infobip-error-codes.yml` before deciding to retry or to fail over to SMS.
