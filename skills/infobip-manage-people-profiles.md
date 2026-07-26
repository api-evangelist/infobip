---
name: Manage customer profiles in People
description: Create, match, upsert and merge person profiles in the Infobip People CDP so messaging and
  journeys resolve to one customer.
api: openapi/infobip-people-openapi.json
operations:
- get-a-single-person-or-a-list-of-people
- create-a-new-person
- partial-person-update
- upsert-persons-partial
- match-people-ids
- merge-persons
- batch-people-create
- set-person-contact-information
provider: Infobip
generated: '2026-07-25'
method: generated
source: Grounded in operationIds verified in openapi/infobip-people-openapi.json plus conventions/infobip-conventions.yml,
  errors/infobip-error-codes.yml and rate-limits/infobip-rate-limits.yml
---

# Manage customer profiles in People

Create, match, upsert and merge person profiles in the Infobip People CDP so messaging and journeys resolve to one customer.

## Ground rules for every Infobip call

- Base URL: `https://api.infobip.com` (an account may also be issued a personalized `https://{subdomain}.api.infobip.com` host shown in the web portal — either works).
- Auth header: `Authorization: App {API_KEY}`. Basic auth is only for the API-key-management endpoints. Every endpoint additionally requires at least one API scope (see `scopes/infobip-scopes.yml`).
- There is **no idempotency key**. Never blind-retry a send on a timeout or 5xx — re-read the outcome with the reports/logs operation for the returned `bulkId`/`messageId` first (`conventions/infobip-conventions.yml`).
- On `429` back off exponentially and honour `Retry-After`. Per-operation limits are published in the spec as `x-throttling-info` and collected in `rate-limits/infobip-rate-limits.yml`.
- HTTP errors use the Infobip `requestError.serviceException {messageId, text, validationErrors}` envelope (not RFC 9457) — see `errors/infobip-problem-types.yml`.
- A `200` does **not** mean delivered. Message outcome lives in the `status {groupId, groupName, id, name}` and `error {groupId, groupName, id, name, permanent}` objects; resolve them against `errors/infobip-error-codes.yml`. `permanent: true` means a retry can never succeed.
- Listing endpoints page with `page`/`size` (max 100) and return `{page, size, totalPages, totalResults}`; newer endpoints support `cursor`/`useCursor`.

## Steps
1. **Look before you create** — `get-a-single-person-or-a-list-of-people` (`GET /people/2/persons`) accepts `identifier` + `type` (for example a phone number or email) so you can resolve an existing profile instead of duplicating it. Listing is paged with `page`/`size` and `includeTotalCount`.
2. **Create** — `create-a-new-person` (`POST /people/2/persons`), or `batch-people-create` (`POST /people/2/persons/batch`) for bulk loads.
3. **Prefer upsert for sync jobs** — `upsert-persons-partial` (`PATCH /people/3/persons/upsert`) or `upsert-persons-full` (`PUT /people/3/persons/upsert`). This is the closest thing the platform has to an idempotent write: repeating the same upsert converges instead of duplicating, which matters because there is no `Idempotency-Key`.
4. **Resolve identities in bulk** — `match-people-ids` (`POST /people/2/persons/match`) takes a list of identities and returns the internal person id for each; duplicate identities collapse to a single profile reference.
5. **Fix duplicates** — `merge-persons` (`POST /people/3/persons/merge`).
6. **Contact channels** are managed separately: `set-person-contact-information`, `add-person-contact-information`, `delete-person-contact-information` on `/people/2/persons/contactInformation`.
7. Throttling here is tight (roughly 5–10 requests/second on the person endpoints) — batch rather than loop, and honour `Retry-After` on `429`.
