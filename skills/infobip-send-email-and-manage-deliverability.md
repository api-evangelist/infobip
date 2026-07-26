---
name: Send email and manage deliverability
description: Send transactional email through the Infobip Email API and keep the sending domain, suppression
  list and IP pools healthy.
api: openapi/infobip-email-openapi.json
operations:
- send-email-messages-api
- send-fully-featured-email
- get-outbound-email-message-delivery-reports
- get-email-message-logs
- add-domain
- verify-domain
- get-suppressions
- add-suppressions
- validate-email-addresses
provider: Infobip
generated: '2026-07-25'
method: generated
source: Grounded in operationIds verified in openapi/infobip-email-openapi.json plus conventions/infobip-conventions.yml,
  errors/infobip-error-codes.yml and rate-limits/infobip-rate-limits.yml
---

# Send email and manage deliverability

Send transactional email through the Infobip Email API and keep the sending domain, suppression list and IP pools healthy.

## Ground rules for every Infobip call

- Base URL: `https://api.infobip.com` (an account may also be issued a personalized `https://{subdomain}.api.infobip.com` host shown in the web portal — either works).
- Auth header: `Authorization: App {API_KEY}`. Basic auth is only for the API-key-management endpoints. Every endpoint additionally requires at least one API scope (see `scopes/infobip-scopes.yml`).
- There is **no idempotency key**. Never blind-retry a send on a timeout or 5xx — re-read the outcome with the reports/logs operation for the returned `bulkId`/`messageId` first (`conventions/infobip-conventions.yml`).
- On `429` back off exponentially and honour `Retry-After`. Per-operation limits are published in the spec as `x-throttling-info` and collected in `rate-limits/infobip-rate-limits.yml`.
- HTTP errors use the Infobip `requestError.serviceException {messageId, text, validationErrors}` envelope (not RFC 9457) — see `errors/infobip-problem-types.yml`.
- A `200` does **not** mean delivered. Message outcome lives in the `status {groupId, groupName, id, name}` and `error {groupId, groupName, id, name, permanent}` objects; resolve them against `errors/infobip-error-codes.yml`. `permanent: true` means a retry can never succeed.
- Listing endpoints page with `page`/`size` (max 100) and return `{page, size, totalPages, totalResults}`; newer endpoints support `cursor`/`useCursor`.

## Steps
1. **Set the sending domain up first** — `add-domain` (`POST /email/1/domains`), publish the returned DNS records, then `verify-domain` (`POST /email/1/domains/{domainName}/verify`). `update-tracking-events` controls open/click tracking per domain. Sending from an unverified domain is the most common cause of `EC_DOMAIN_CONFIGURATION_ERROR` / `EC_DMARC_POLICY_ISSUE`.
2. **(Optional) Validate recipients** — `validate-email-addresses` (`POST /email/2/validation`) for one address, `request-validations` for a batch. This is cheaper than bouncing.
3. **Send** — `send-email-messages-api` (`POST /email/4/messages`) is the current structured surface; `send-fully-featured-email` (`POST /email/3/send`) is the multipart form variant and `send-mime-email` (`POST /email/4/mime`) takes a raw MIME document. Keep the returned `bulkId` and per-message `messageId`.
4. **Track outcome** — `get-outbound-email-message-delivery-reports` (`GET /email/4/reports`) or `get-email-message-logs` (`GET /email/4/logs`), or consume the `receive-email-delivery-reports`, `receive-email-tracking-reports` and `receive-email-platform-events` webhooks. Platform-event payloads carry an `eventId` documented for deduplication — dedupe on it, because webhook delivery is retried.
5. **Respect suppressions** — `get-suppressions` / `add-suppressions` / `delete-suppressions` (`/email/1/suppressions`). Unsubscribes, complaints and hard bounces land here; sending to a suppressed address is dropped, not delivered.
6. **At volume, manage IPs** — `get-all-ips`, `commission-ip`, `create-ip-pool`, `assign-ip-to-pool` and `assign-pool-to-domain` control which IP pool a domain sends from.
