# Infobip

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **Not from the company, and here with a question?** You are welcome here — we would rather be the
> front line and point you the right way than have a good report go nowhere. What this repository
> can answer is narrow, though, so it is worth knowing who you are actually looking for:
>
> - **A question about how the API works, an account, billing, or a bug in the service** — that is
>   the company's own support, not us. We profile this API; we do not operate it and cannot see
>   your account.
> - **A bug in an open-source project we only catalog** — file it on that project's own repository.
>   This has happened with a real and correct bug report that reached us instead of the people who
>   could fix it, which helped nobody.
> - **Anything about this listing itself** — the description, the tags, the rating, a missing or
>   wrong artifact — is ours. Open an issue here.
> - **Not sure, or something general about API Evangelist or APIs.io** — open an issue on the
>   [APIs.io Inbox](https://github.com/api-search/inbox) and we will route it.
>
> **This repository contains no software, and we will never ask you to download anything.** There is
> no build, release, installer, or binary here — only text and machine-readable API descriptions, so
> there is nothing here that can be "corrupt" or need "repairing". Any issue, comment, or email
> claiming otherwise and offering a download link is not from us and is hostile. Do not follow the
> link; it is a lure. Report it to GitHub and, if you like, tell us at
> [info@apievangelist.com](mailto:info@apievangelist.com) so we can take it down.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

Infobip is a global communications platform as a service (CPaaS) provider headquartered in Vodnjan, Croatia, and is Croatia's largest technology company. It sells programmable messaging, voice, video, email and customer engagement APIs on top of direct connections into mobile network operators worldwide, sitting in the aggregator layer of the telecom value chain: it buys and resells carrier connectivity, and it is the developer-facing surface that most businesses actually integrate with rather than the carriers themselves. Its API posture is openly self-serve — a free-trial account, a documentation hub at infobip.com/docs/api, first-party SDKs in six languages, a public Postman workspace, remote MCP servers, and an unauthenticated OpenAPI 3.1 endpoint at https://api.infobip.com/platform/1/openapi that returns the complete specification for all public endpoints and webhooks, plus per-product specifications for 46 products. On the network-API side Infobip is a GSMA Open Gateway participant certified for SIM Swap and Number Verification (September 2025) and an Aduna channel partner, and it publishes callable CAMARA endpoints — Number Verification, SIM Swap, Device Location Verification and KYC Match — though CAMARA access itself is sales-gated behind a contact form even while the specification is public.

**Areas:** Telecommunications · Croatia · CPaaS · Messaging · SMS · Voice · RCS · WhatsApp · Email · Network APIs · CAMARA · Open Gateway

## Infobip on APIs.io

Everything profiled for Infobip is published on APIs.io rather than in this repository. Start at the provider page — **[apis.io/providers/infobip/](https://apis.io/providers/infobip/)** — or go straight to one of the APIs or properties below.

### APIs (6)

- [Infobip AI Hub API](https://apis.io/apis/infobip/infobip-ai-hub-api/) — AI-powered tools and services to help you create smarter and more personalized customer experiences.
- [Infobip Channels API](https://apis.io/apis/infobip/infobip-channels-api/) — Create a perfect customer experience by using the channels your customer already use and love.
- [Infobip Connectivity API](https://apis.io/apis/infobip/infobip-connectivity-api/) — Powerful infrastructure and tools that connect you to the world.
- [Infobip Customer Engagement API](https://apis.io/apis/infobip/infobip-customer-engagement-api/) — Complete solutions that will help you drive better outcomes for your customers and business across the entire customer journey.
- [Infobip Platform API](https://apis.io/apis/infobip/infobip-platform-api/) — Modular tools to scale and automate your business.
- [Infobip Tools API](https://apis.io/apis/infobip/infobip-tools-api/) — Developer utilities to help you integrate and work with Infobip APIs more efficiently.

### Published properties

Each property below is a page on APIs.io carrying the machine-readable artifact and what it says.

#### AsyncAPI (2)

Event-driven and webhook contracts.

- [Infobip Webhooks](https://apis.io/asyncapis/infobip/infobip-webhooks/)
- [Infobip platform webhooks](https://apis.io/asyncapis/infobip/infobip-webhooks-asyncapi/)

#### Event channels (102)

Individual events and webhooks the provider emits.

- [brand-auth-2fa-update-notification](https://apis.io/channels/infobip/brand-auth-2fa-update-notification/)
- [brand-registration-status-change-notification](https://apis.io/channels/infobip/brand-registration-status-change-notification/)
- [brand-vet-notification](https://apis.io/channels/infobip/brand-vet-notification/)
- [call-link-status-webhook](https://apis.io/channels/infobip/call-link-status-webhook/)
- [calls-event-webhook](https://apis.io/channels/infobip/calls-event-webhook/)
- [campaign-ai-builder-notification](https://apis.io/channels/infobip/campaign-ai-builder-notification/)
- [campaign-ai-feedback-notification](https://apis.io/channels/infobip/campaign-ai-feedback-notification/)
- [campaign-network-status-notification](https://apis.io/channels/infobip/campaign-network-status-notification/)
- [campaign-status-change-notification](https://apis.io/channels/infobip/campaign-status-change-notification/)
- [cdp-event-webhook](https://apis.io/channels/infobip/cdp-event-webhook/)
- [conversation-event-webhook](https://apis.io/channels/infobip/conversation-event-webhook/)
- [deprecated-receive-voice-delivery-reports](https://apis.io/channels/infobip/deprecated-receive-voice-delivery-reports/)
- [dial-callback](https://apis.io/channels/infobip/dial-callback/)
- [fetch-markup-language](https://apis.io/channels/infobip/fetch-markup-language/)
- [inbound-events-receive-inbound-rcs-events](https://apis.io/channels/infobip/inbound-events-receive-inbound-rcs-events/)
- [receive-advanced-silent-mobile-verification-result](https://apis.io/channels/infobip/receive-advanced-silent-mobile-verification-result/)
- [receive-aggregate-data-result](https://apis.io/channels/infobip/receive-aggregate-data-result/)
- [receive-billing-usage-result](https://apis.io/channels/infobip/receive-billing-usage-result/)
- [receive-blocklist-event](https://apis.io/channels/infobip/receive-blocklist-event/)
- [receive-capability-check-result](https://apis.io/channels/infobip/receive-capability-check-result/)
- [receive-email-delivery-reports](https://apis.io/channels/infobip/receive-email-delivery-reports/)
- [receive-email-platform-events](https://apis.io/channels/infobip/receive-email-platform-events/)
- [receive-email-tracking-reports](https://apis.io/channels/infobip/receive-email-tracking-reports/)
- [receive-enrollment-session-results](https://apis.io/channels/infobip/receive-enrollment-session-results/)
- [receive-extraction-session-results](https://apis.io/channels/infobip/receive-extraction-session-results/)
- …and 77 more published on APIs.io

#### MCP servers (1)

Model Context Protocol servers that expose the API to agents.

- [infobip-mcp.yml](https://apis.io/servers/infobip/infobip-mcp-yml/)

#### Agentic access (1)

Which operations an agent can call, which act, and which need a human in the loop.

- [Infobip Agentic Access](https://apis.io/agentic-access/infobip/infobip-agentic-access/)

#### JSON Schema (30)

The data models the API reads and writes.

- [OmniAdvancedRequest](https://apis.io/schemas/infobip/infobip-04790a6ae08cb63186016b6e4b8eb1c003a31d6a3227220686470a5721dc2d02-omni-advanced-request/)
- [ArticleDetailResponse](https://apis.io/schemas/infobip/infobip-09ef6171198229ad9a73a413d2271afa3ba31b9abbd6cd8a0cc9563fd721f1ed-article-detail-response/)
- [TollFreeUnifiedNumberCampaignApiModel](https://apis.io/schemas/infobip/infobip-2700ea5ecfd0574f21019319e90eb63416ede8263eab67e466c718c51cd1a77a-toll-free-unified-number-campaign-api-model/)
- [QueryAiAssistantApiResponse](https://apis.io/schemas/infobip/infobip-2a53d681c9399f766b0cfff54e0469d04419b36fc1603e6db03e69cc8ad55f34-query-ai-assistant-api-response/)
- [RetrieveContextApiResponse](https://apis.io/schemas/infobip/infobip-2a53d681c9399f766b0cfff54e0469d04419b36fc1603e6db03e69cc8ad55f34-retrieve-context-api-response/)
- [RetrieveContextRequest](https://apis.io/schemas/infobip/infobip-2a53d681c9399f766b0cfff54e0469d04419b36fc1603e6db03e69cc8ad55f34-retrieve-context-request/)
- [SimpleAiAssistantQuery](https://apis.io/schemas/infobip/infobip-2a53d681c9399f766b0cfff54e0469d04419b36fc1603e6db03e69cc8ad55f34-simple-ai-assistant-query/)
- [SendMimeRequestSchema](https://apis.io/schemas/infobip/infobip-34438aa163eb13a2a06ad96ae98170e41cc2ee8902e8b7655aba73ceb0bb23f1-send-mime-request-schema/)
- [SendRequestSchema](https://apis.io/schemas/infobip/infobip-34438aa163eb13a2a06ad96ae98170e41cc2ee8902e8b7655aba73ceb0bb23f1-send-request-schema/)
- [CallLog](https://apis.io/schemas/infobip/infobip-431fb79b0e816230968e14ba1e1c6fadb75cfde9cb3c381f4217b2777f48153f-call-log/)
- [MoConfigurationRequest](https://apis.io/schemas/infobip/infobip-7c77a2c703ce12a601f120565936de62cf48d1baf9232d5411f82fc339353553-mo-configuration-request/)
- [EnrollmentSessionRequest](https://apis.io/schemas/infobip/infobip-8a19359d3a412667abbd2d38733e247b91417d2a845ae41758328736ea0ecce9-enrollment-session-request/)
- [ExtractionSessionRequest](https://apis.io/schemas/infobip/infobip-8a19359d3a412667abbd2d38733e247b91417d2a845ae41758328736ea0ecce9-extraction-session-request/)
- [VerificationSessionRequest](https://apis.io/schemas/infobip/infobip-8a19359d3a412667abbd2d38733e247b91417d2a845ae41758328736ea0ecce9-verification-session-request/)
- [IamPersonV2](https://apis.io/schemas/infobip/infobip-a8ed60f1ed4abc0dfe4d5460edd3205f89585f2cd4b436e4d83a1231d28c264c-iam-person-v2/)
- [RecordingMetadataApiModel](https://apis.io/schemas/infobip/infobip-b979cda441a7c661201042835d7dc18eaec3fa68a2905164912469051f8b8866-recording-metadata-api-model/)
- [CreateApiKeyRequest](https://apis.io/schemas/infobip/infobip-bb8af9c2d2d4d677e25555100e31662e23d86ede8b5d73bbf4974b4decdd08d7-create-api-key-request/)
- [UpdateApiKeyRequest](https://apis.io/schemas/infobip/infobip-bb8af9c2d2d4d677e25555100e31662e23d86ede8b5d73bbf4974b4decdd08d7-update-api-key-request/)
- [Message](https://apis.io/schemas/infobip/infobip-c3b21d2ffef2552e10577daa67c904ac80618665b001ef386a4faefc515e78f3-message/)
- [SmsOrVoiceMessage](https://apis.io/schemas/infobip/infobip-c3b21d2ffef2552e10577daa67c904ac80618665b001ef386a4faefc515e78f3-sms-or-voice-message/)
- [CreateRcsSenderApiRequest](https://apis.io/schemas/infobip/infobip-c4d4776b979fea48176211c392051aca0dae21d75b7a9ca349c8f2eb95a84913-create-rcs-sender-api-request/)
- [RcsSender](https://apis.io/schemas/infobip/infobip-c4d4776b979fea48176211c392051aca0dae21d75b7a9ca349c8f2eb95a84913-rcs-sender/)
- [CamaraKycMatchRequestDto](https://apis.io/schemas/infobip/infobip-c4fb96364cd87b1d1d15720880c5153ef26f58342e4ec03b9d5896f2251f17ae-camara-kyc-match-request-dto/)
- [CamaraKycMatchResponseDto](https://apis.io/schemas/infobip/infobip-c4fb96364cd87b1d1d15720880c5153ef26f58342e4ec03b9d5896f2251f17ae-camara-kyc-match-response-dto/)
- [SmvVerifyAdvancedRequestDto](https://apis.io/schemas/infobip/infobip-c4fb96364cd87b1d1d15720880c5153ef26f58342e4ec03b9d5896f2251f17ae-smv-verify-advanced-request-dto/)
- …and 5 more published on APIs.io

#### JSON-LD (1)

Linked-data contexts for the provider's vocabulary.

- [Infobip Context](https://apis.io/jsonld/infobip/infobip-context/)

#### Collections (93)

Postman and Open Collection request collections.

- [Infobip OpenAPI Specification](https://apis.io/collections/infobip/open-infobip-2fa/)
- [Infobip OpenAPI Specification](https://apis.io/collections/infobip/open-infobip-account-management/)
- [Infobip OpenAPI Specification](https://apis.io/collections/infobip/open-infobip-ai-assistants/)
- [Infobip OpenAPI Specification](https://apis.io/collections/infobip/open-infobip-answers/)
- [Infobip OpenAPI Specification](https://apis.io/collections/infobip/open-infobip-apple-mfb/)
- [Infobip OpenAPI Specification](https://apis.io/collections/infobip/open-infobip-application-entity/)
- [Infobip OpenAPI Specification](https://apis.io/collections/infobip/open-infobip-billing-usage-api/)
- [Infobip OpenAPI Specification](https://apis.io/collections/infobip/open-infobip-biometrics/)
- [Infobip OpenAPI Specification](https://apis.io/collections/infobip/open-infobip-blocklist/)
- [Infobip OpenAPI Specification](https://apis.io/collections/infobip/open-infobip-camara/)
- [Infobip OpenAPI Specification](https://apis.io/collections/infobip/open-infobip-catalogs-api/)
- [Infobip OpenAPI Specification](https://apis.io/collections/infobip/open-infobip-common-assets/)
- [Infobip OpenAPI Specification](https://apis.io/collections/infobip/open-infobip-conversations/)
- [Infobip OpenAPI Specification](https://apis.io/collections/infobip/open-infobip-email/)
- [Infobip OpenAPI Specification](https://apis.io/collections/infobip/open-infobip-instagram/)
- [Infobip OpenAPI Specification](https://apis.io/collections/infobip/open-infobip-kakao/)
- [Infobip OpenAPI Specification](https://apis.io/collections/infobip/open-infobip-knowledge-base/)
- [Infobip OpenAPI Specification](https://apis.io/collections/infobip/open-infobip-line/)
- [Infobip OpenAPI Specification](https://apis.io/collections/infobip/open-infobip-live-chat/)
- [Infobip OpenAPI Specification](https://apis.io/collections/infobip/open-infobip-messages-api/)
- [Infobip OpenAPI Specification](https://apis.io/collections/infobip/open-infobip-messenger/)
- [Infobip OpenAPI Specification](https://apis.io/collections/infobip/open-infobip-metrics-api/)
- [Infobip OpenAPI Specification](https://apis.io/collections/infobip/open-infobip-mms/)
- [Infobip OpenAPI Specification](https://apis.io/collections/infobip/open-infobip-mobile-app-messaging/)
- [Infobip OpenAPI Specification](https://apis.io/collections/infobip/open-infobip-mobile-identity/)
- …and 68 more published on APIs.io

#### Overlays (53)

OpenAPI overlays, including conversational phrasing for each operation.

- [Infobip 2Fa Overlay](https://apis.io/overlays/infobip/infobip-2fa-overlay/)
- [Infobip Account Management Overlay](https://apis.io/overlays/infobip/infobip-account-management-overlay/)
- [Infobip Ai Assistants Overlay](https://apis.io/overlays/infobip/infobip-ai-assistants-overlay/)
- [Infobip Ai Hub Api Phrasing Overlay](https://apis.io/overlays/infobip/infobip-ai-hub-api-phrasing-overlay/)
- [Infobip Answers Overlay](https://apis.io/overlays/infobip/infobip-answers-overlay/)
- [Infobip Apple Mfb Overlay](https://apis.io/overlays/infobip/infobip-apple-mfb-overlay/)
- [Infobip Application Entity Overlay](https://apis.io/overlays/infobip/infobip-application-entity-overlay/)
- [Infobip Billing Usage Api Overlay](https://apis.io/overlays/infobip/infobip-billing-usage-api-overlay/)
- [Infobip Biometrics Overlay](https://apis.io/overlays/infobip/infobip-biometrics-overlay/)
- [Infobip Blocklist Overlay](https://apis.io/overlays/infobip/infobip-blocklist-overlay/)
- [Infobip Camara Overlay](https://apis.io/overlays/infobip/infobip-camara-overlay/)
- [Infobip Catalogs Api Overlay](https://apis.io/overlays/infobip/infobip-catalogs-api-overlay/)
- [Infobip Channels Api Phrasing Overlay](https://apis.io/overlays/infobip/infobip-channels-api-phrasing-overlay/)
- [Infobip Common Assets Overlay](https://apis.io/overlays/infobip/infobip-common-assets-overlay/)
- [Infobip Connectivity Api Phrasing Overlay](https://apis.io/overlays/infobip/infobip-connectivity-api-phrasing-overlay/)
- [Infobip Conversations Overlay](https://apis.io/overlays/infobip/infobip-conversations-overlay/)
- [Infobip Customer Engagement Api Phrasing Overlay](https://apis.io/overlays/infobip/infobip-customer-engagement-api-phrasing-overlay/)
- [Infobip Email Overlay](https://apis.io/overlays/infobip/infobip-email-overlay/)
- [Infobip Instagram Overlay](https://apis.io/overlays/infobip/infobip-instagram-overlay/)
- [Infobip Kakao Overlay](https://apis.io/overlays/infobip/infobip-kakao-overlay/)
- [Infobip Knowledge Base Overlay](https://apis.io/overlays/infobip/infobip-knowledge-base-overlay/)
- [Infobip Line Overlay](https://apis.io/overlays/infobip/infobip-line-overlay/)
- [Infobip Live Chat Overlay](https://apis.io/overlays/infobip/infobip-live-chat-overlay/)
- [Infobip Messages Api Overlay](https://apis.io/overlays/infobip/infobip-messages-api-overlay/)
- [Infobip Messenger Overlay](https://apis.io/overlays/infobip/infobip-messenger-overlay/)
- …and 28 more published on APIs.io

#### Governance rules (1)

Spectral rulesets for the provider's contracts.

- [Infobip API Rules](https://apis.io/rules/infobip/infobip-rules/)

#### Security (4)

Authentication, trust centre, and vulnerability disclosure.

- [Infobip Authentication](https://apis.io/security/infobip/infobip-authentication/)
- [Infobip Domain Security](https://apis.io/security/infobip/infobip-domain-security/)
- [Infobip Trust Center](https://apis.io/security/infobip/infobip-trust-center/)
- [Infobip Vulnerability Disclosure](https://apis.io/security/infobip/infobip-vulnerability-disclosure/)

#### OAuth scopes (1)

The permissions the API asks for.

- [Infobip Scopes](https://apis.io/scopes/infobip/infobip-scopes/)

#### Plans and pricing (1)

Published plans, tiers and prices.

- [Infobip Plans Pricing](https://apis.io/plans/infobip/infobip-plans-pricing/)

#### Rate limits (1)

Published request limits.

- [Infobip Rate Limits](https://apis.io/rate-limits/infobip/infobip-rate-limits/)

## Where to find this API

Links to the company's own pages. This repository publishes no copy of their specifications — the canonical document is theirs and lives at the URLs below.

- [Website](https://www.infobip.com/)
- [Documentation](https://www.infobip.com/docs)
- [Getting started](https://www.infobip.com/docs/essentials/getting-started)
- [API reference](https://www.infobip.com/docs/api)
- [Pricing](https://www.infobip.com/pricing)
- [Sign up](https://www.infobip.com/signup)
- [Support](https://www.infobip.com/contact)
- [Changelog](https://www.infobip.com/docs/release-notes)
- [Blog](https://www.infobip.com/blog)
- [Security](https://www.infobip.com/security-trust-center/cvd-policy)
- [Compliance](https://www.infobip.com/certificates)
- [Terms of service](https://www.infobip.com/policies/service-terms-conditions)
- [Privacy policy](https://www.infobip.com/policies/privacy-notice)
- [GitHub](https://github.com/infobip)
- [Status](https://status.infobip.com/)

## API Evangelist rating

**Kin Score 84.9** — exemplar · rubric 0.25.0 · scored 2026-10-23

| Facet | Score |
|---|---|
| Discoverability | 83.3 |
| Contract quality | 72.1 |
| Contract governance | 35.6 |
| Operational transparency | 68.4 |
| Developer ergonomics | 68.5 |
| Access clarity | 92.1 |

**Agent readiness 61.3** — agent-ready (gated down from agent-native)

| Agent-readiness dimension | Result |
|---|---|
| Spec Presence | yes |
| Agentic Access | derived (partial credit) |
| Reversibility Documented | verified |
| MCP Server | verified |
| Auth Clarity | served (partial credit) |
| Idempotency | — |
| Error Semantics | verified |
| OpenAPI Examples | verified |
| Rate Limit Signal | derived (partial credit) |
| Event Surface Described | yes |
| Agent Skills | derived (partial credit) |
| Well Known Catalog | — |
| Consent Identity | — |
| Agent Card | — |
| Dry Run Mode | — |
| Delegated Identity | served (partial credit) |
| Protected Resource Metadata | verified |
| Dynamic Client Registration | yes |
| Agentic Commerce | — |
| Pagination Ratio | partial |
| Operation Distinctiveness | — |

**Regulatory alignment 72.5** — Telecommunications

The rubric is published at [github.com/api-evangelist/kin-score](https://github.com/api-evangelist/kin-score). The per-check breakdown behind these numbers — which checks were earned, partial or missed — along with score history and how this provider compares to its peers, is available at [apis.io/providers/infobip/](https://apis.io/providers/infobip/).

## How this profile is made

API Evangelist profiles a company's public API surface the way a developer would find it: the website, developer portal and documentation, the specifications it publishes, its public repositories, and its pricing, status and changelog pages. From that it derives the properties above — contracts split per API, workflows, schemas, collections, governance rules, plans and rate limits — and scores them against the published [Kin Score rubric](https://github.com/api-evangelist/kin-score).

The artifacts are published on [APIs.io](https://apis.io), not in this repository. This repository is the public record for Infobip: the place to say something is wrong, missing or out of date, and to ask for a re-score or a removal.

## Open an issue

- **Something about this listing** — a wrong description, a missing API, a stale artifact or a question about the rating: [open an issue on this repository](https://github.com/api-evangelist/infobip/issues/new).
- **A new API, or one that is not in the catalog yet** — [submit it on APIs.io](https://apis.io/add/).
- **Anything else** — [the APIs.io inbox](https://github.com/api-search/inbox/issues/new) or [info@apievangelist.com](mailto:info@apievangelist.com).
