---
name: Run a 2FA PIN verification flow
description: Create a 2FA application and message template, send a PIN over SMS, voice or email, verify
  it, and read the verification status.
api: openapi/infobip-2fa-openapi.json
operations:
- create-2fa-application
- create-2fa-message-template
- send-2fa-pin-code-over-sms
- resend-2fa-pin-code-over-sms
- verify-2fa-phone-number
- get-2fa-verification-status
provider: Infobip
generated: '2026-07-25'
method: generated
source: Grounded in operationIds verified in openapi/infobip-2fa-openapi.json plus conventions/infobip-conventions.yml,
  errors/infobip-error-codes.yml and rate-limits/infobip-rate-limits.yml
---

# Run a 2FA PIN verification flow

Create a 2FA application and message template, send a PIN over SMS, voice or email, verify it, and read the verification status.

## Ground rules for every Infobip call

- Base URL: `https://api.infobip.com` (an account may also be issued a personalized `https://{subdomain}.api.infobip.com` host shown in the web portal — either works).
- Auth header: `Authorization: App {API_KEY}`. Basic auth is only for the API-key-management endpoints. Every endpoint additionally requires at least one API scope (see `scopes/infobip-scopes.yml`).
- There is **no idempotency key**. Never blind-retry a send on a timeout or 5xx — re-read the outcome with the reports/logs operation for the returned `bulkId`/`messageId` first (`conventions/infobip-conventions.yml`).
- On `429` back off exponentially and honour `Retry-After`. Per-operation limits are published in the spec as `x-throttling-info` and collected in `rate-limits/infobip-rate-limits.yml`.
- HTTP errors use the Infobip `requestError.serviceException {messageId, text, validationErrors}` envelope (not RFC 9457) — see `errors/infobip-problem-types.yml`.
- A `200` does **not** mean delivered. Message outcome lives in the `status {groupId, groupName, id, name}` and `error {groupId, groupName, id, name, permanent}` objects; resolve them against `errors/infobip-error-codes.yml`. `permanent: true` means a retry can never succeed.
- Listing endpoints page with `page`/`size` (max 100) and return `{page, size, totalPages, totalResults}`; newer endpoints support `cursor`/`useCursor`.

## Steps
1. **Create the application once** — `create-2fa-application` (`POST /2fa/2/applications`). The `configuration` block sets PIN attempt limits, PIN time-to-live, send-attempt limits and verification expiry. Keep the returned `applicationId`.
2. **Create a message template once** — `create-2fa-message-template` (`POST /2fa/2/applications/{appId}/messages`) with `pinType`, `pinLength`, `messageText` containing the `{{pin}}` placeholder, and `language`. Keep the returned `messageId`. Email flows use `create-2fa-email-message-template` instead.
3. **Send the PIN** — `send-2fa-pin-code-over-sms` (`POST /2fa/2/pin`) with `applicationId`, `messageId` and `to`. Voice and email variants are `send-2fa-pin-code-over-voice` and `send-2fa-pin-code-over-email`. Keep the returned `pinId`.
4. **Resend only through the resend operation** — `resend-2fa-pin-code-over-sms` (`POST /2fa/2/pin/{pinId}/resend`). Do not call the send operation again for the same verification; there is no idempotency key and a second send starts a second PIN.
5. **Verify** — `verify-2fa-phone-number` (`POST /2fa/2/pin/{pinId}/verify`) with the PIN the user typed. The response carries `verified` plus `attemptsRemaining`; a wrong PIN is a successful HTTP call with `verified: false`.
6. **Audit** — `get-2fa-verification-status` (`GET /2fa/2/applications/{appId}/verifications`) filtered by `msisdn` shows sent/verified counts for fraud review.
