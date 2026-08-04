# Infobip (infobip)

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
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

Infobip is a global communications platform as a service (CPaaS) provider headquartered in Vodnjan, Croatia, and is Croatia's largest technology company. It sells programmable messaging, voice, video, email and customer engagement APIs on top of direct connections into mobile network operators worldwide, sitting in the aggregator layer of the telecom value chain: it buys and resells carrier connectivity, and it is the developer-facing surface that most businesses actually integrate with rather than the carriers themselves. Its API posture is openly self-serve — a free-trial account, a documentation hub at infobip.com/docs/api, first-party SDKs in six languages, a public Postman workspace, remote MCP servers, and an unauthenticated OpenAPI 3.1 endpoint at https://api.infobip.com/platform/1/openapi that returns the complete specification for all public endpoints and webhooks, plus per-product specifications for 46 products. On the network-API side Infobip is a GSMA Open Gateway participant certified for SIM Swap and Number Verification (September 2025) and an Aduna channel partner, and it publishes callable CAMARA endpoints — Number Verification, SIM Swap, Device Location Verification and KYC Match — though CAMARA access itself is sales-gated behind a contact form even while the specification is public.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/infobip/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/infobip/refs/heads/main/apis.yml)

## Telecom posture

Infobip sits on the API-native half of the telecom split. It is an aggregator, not an operator: it buys carrier connectivity and resells it as programmable APIs, and it out-publishes most of its own suppliers. The developer surface is genuinely self-serve — free-trial signup, public documentation, first-party SDKs, a public Postman workspace, remote MCP servers, and, unusually, the complete OpenAPI 3.1 definition served anonymously from a live endpoint.

- **Downloadable OpenAPI:** `GET https://api.infobip.com/platform/1/openapi` returns the whole platform specification (OpenAPI 3.1.0, version 3.210.0, 652 paths, 102 webhooks). `GET /platform/1/openapi/available-products` lists 46 products and `GET /platform/1/openapi/{product}` returns a specification per product. All 47 documents are harvested verbatim into [`openapi/`](openapi/).

- **CAMARA:** real and callable, not a press release. Nine `/camara/*` endpoints are published — Number Verification (network-based v0 and SIM-based v2, including DCQL and device-phone-number), SIM Swap (check and retrieve-date), Device Location Verification, and KYC Match v0.3. Commercial access is still sales-gated: Infobip's own product description opens with "Contact us and get started with CAMARA."

- **GSMA Open Gateway:** participant, certified for SIM Swap and Number Verification (announced 2025-09-16). Also an announced Aduna (Ericsson/carrier JV) channel partner since February 2025, so it reaches network APIs both directly and through the JV.

- **TM Forum / 3GPP:** no TM Forum Open API conformance certification found, and no NEF/SCEF, network-slicing or edge/MEC surface — expected for a channel rather than an operator.

- **Auth:** API key (`Authorization: App <key>`, scoped and revocable), HTTP Basic, an IBSSO session token, and OAuth2 client-credentials at `https://api.infobip.com/auth/1/oauth2/token`. **No CIBA** appears anywhere in the specification and no OIDC discovery document is served — the aggregator absorbs CAMARA's OIDC/CIBA authorization and re-fronts it as an API key.

- **Events:** 102 webhooks carried natively in the OpenAPI 3.1 `webhooks` object, with a dedicated Subscriptions Management product for subscriptions, security settings and certificates. No AsyncAPI is published.

## Tags

- Telecommunications
- Croatia
- CPaaS
- Messaging
- SMS
- Voice
- RCS
- WhatsApp
- Email
- Network APIs
- CAMARA
- Open Gateway
- Identity Verification
- SIM Swap
- Number Verification
- Omnichannel
- Aggregator
- Customer Engagement

## Timestamps

- **Created:** 2026-07-25
- **Modified:** 2026-07-25

## APIs (46)

### Infobip 2FA API

Infobip's Two Factor Authentication API for OTP (One Time Passcode) delivery and verification. OTPs can be delivered over SMS, Voice or Email. Learn more about the workflow and setup. You can use SDKs and other available tools to help you with integration. — 14 operation path(s) and 0 webhook(s) in Infobip's published OpenAPI.

- **Human URL:** [https://www.infobip.com/docs/api/platform/2fa](https://www.infobip.com/docs/api/platform/2fa)
- **Base URL:** `https://api.infobip.com`

#### Tags

- 2FA
- Platform

#### Properties

- [OpenAPI](openapi/infobip-2fa-openapi.json) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Documentation](https://www.infobip.com/docs/api/platform/2fa)
- [API Reference](https://www.infobip.com/docs/api/platform/2fa)

### Infobip Account management API

Manage your Infobip account details, such as individual users and api keys. — 13 operation path(s) and 0 webhook(s) in Infobip's published OpenAPI.

- **Human URL:** [https://www.infobip.com/docs/api/platform/account-management](https://www.infobip.com/docs/api/platform/account-management)
- **Base URL:** `https://api.infobip.com`

#### Tags

- Account management
- Platform

#### Properties

- [OpenAPI](openapi/infobip-account-management-openapi.json) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Documentation](https://www.infobip.com/docs/api/platform/account-management)
- [API Reference](https://www.infobip.com/docs/api/platform/account-management)

### Infobip AI Assistants API

Infobip AI assistant is a retrieval-augmented generation (RAG) solution that performs tasks based on documents and instructions you specify. This means the AI draws answers directly from your documents, resulting in more accurate and relevant responses. — 2 operation path(s) and 0 webhook(s) in Infobip's published OpenAPI.

- **Human URL:** [https://www.infobip.com/docs/api/ai-hub/ai-assistants](https://www.infobip.com/docs/api/ai-hub/ai-assistants)
- **Base URL:** `https://api.infobip.com`

#### Tags

- AI Assistants
- Ai Hub

#### Properties

- [OpenAPI](openapi/infobip-ai-assistants-openapi.json) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Documentation](https://www.infobip.com/docs/api/ai-hub/ai-assistants)
- [API Reference](https://www.infobip.com/docs/api/ai-hub/ai-assistants)

### Infobip Answers API

Answers is the Infobip fully-encompassed chatbot building platform that enables you to build, test, and deploy highly customized chatbots of different types. Multiple channels are supported on Answers like WhatsApp, Facebook Messenger, Live Chat, Apple Business Chat, Viber, Google Business Messaging and other. — 3 operation path(s) and 1 webhook(s) in Infobip's published OpenAPI.

- **Human URL:** [https://www.infobip.com/docs/api/customer-engagement/answers](https://www.infobip.com/docs/api/customer-engagement/answers)
- **Base URL:** `https://api.infobip.com`

#### Tags

- Answers
- Customer Engagement

#### Properties

- [OpenAPI](openapi/infobip-answers-openapi.json) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Documentation](https://www.infobip.com/docs/api/customer-engagement/answers)
- [API Reference](https://www.infobip.com/docs/api/customer-engagement/answers)

### Infobip Apple Messages for Business API

Use Apple Messages for Business to contact customers in real time. Through the Messages app on iOS, macOS, watchOS, and iPadOS, Apple Messages for Business makes it easy for customers to communicate with businesses. — 4 operation path(s) and 2 webhook(s) in Infobip's published OpenAPI.

- **Human URL:** [https://www.infobip.com/docs/api/channels/apple-mfb](https://www.infobip.com/docs/api/channels/apple-mfb)
- **Base URL:** `https://api.infobip.com`

#### Tags

- Apple Messages for Business
- Channels

#### Properties

- [OpenAPI](openapi/infobip-apple-mfb-openapi.json) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Documentation](https://www.infobip.com/docs/api/channels/apple-mfb)
- [API Reference](https://www.infobip.com/docs/api/channels/apple-mfb)

### Infobip Application and Entity Management API

Applications and Entities are designed to be flexible and modular to give you the opportunity to define your business environment, use cases, applications, customers, assets, etc. on the Infobip platform, so you don't have to manage the complexity of a CPaaS execution. Applications and Entities share some similarities. — 6 operation path(s) and 0 webhook(s) in Infobip's published OpenAPI.

- **Human URL:** [https://www.infobip.com/docs/api/platform/application-entity](https://www.infobip.com/docs/api/platform/application-entity)
- **Base URL:** `https://api.infobip.com`

#### Tags

- Application and Entity Management
- Platform

#### Properties

- [OpenAPI](openapi/infobip-application-entity-openapi.json) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Documentation](https://www.infobip.com/docs/api/platform/application-entity)
- [API Reference](https://www.infobip.com/docs/api/platform/application-entity)

### Infobip Billing Usage API

The Billing Usage API gives you programmatic access to the same billing data behind your monthly invoices. Query costs on demand, integrate results into your own systems, and build automated reporting pipelines. — 1 operation path(s) and 1 webhook(s) in Infobip's published OpenAPI.

- **Human URL:** [https://www.infobip.com/docs/api/platform/billing-usage-api](https://www.infobip.com/docs/api/platform/billing-usage-api)
- **Base URL:** `https://api.infobip.com`

#### Tags

- Billing Usage
- Platform

#### Properties

- [OpenAPI](openapi/infobip-billing-usage-api-openapi.json) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Documentation](https://www.infobip.com/docs/api/platform/billing-usage-api)
- [API Reference](https://www.infobip.com/docs/api/platform/billing-usage-api)

### Infobip Biometrics API

Represents a set of services used for biometric authentication and identity proofing of the end user. — 5 operation path(s) and 4 webhook(s) in Infobip's published OpenAPI.

- **Human URL:** [https://www.infobip.com/docs/api/connectivity/biometrics](https://www.infobip.com/docs/api/connectivity/biometrics)
- **Base URL:** `https://api.infobip.com`

#### Tags

- Biometrics
- Connectivity

#### Properties

- [OpenAPI](openapi/infobip-biometrics-openapi.json) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Documentation](https://www.infobip.com/docs/api/connectivity/biometrics)
- [API Reference](https://www.infobip.com/docs/api/connectivity/biometrics)

### Infobip Blocklist API

Phone numbers and email addresses (referred to as destinations) that no longer want to be contacted are stored inside a Blocklist (also known as Do Not Contact List) This platform feature is used to make sure that no communication is sent to recipients who have opted out of your communication campaigns. — 1 operation path(s) and 1 webhook(s) in Infobip's published OpenAPI.

- **Human URL:** [https://www.infobip.com/docs/api/platform/blocklist](https://www.infobip.com/docs/api/platform/blocklist)
- **Base URL:** `https://api.infobip.com`

#### Tags

- Blocklist
- Platform

#### Properties

- [OpenAPI](openapi/infobip-blocklist-openapi.json) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Documentation](https://www.infobip.com/docs/api/platform/blocklist)
- [API Reference](https://www.infobip.com/docs/api/platform/blocklist)

### Infobip CAMARA API

Contact us and get started with CAMARA. Please fill out the form, and our experts will contact you shortly. CAMARA represents a set of services that we offer in cooperation with the mobile network operators. — 9 operation path(s) and 0 webhook(s) in Infobip's published OpenAPI.

- **Human URL:** [https://www.infobip.com/docs/api/connectivity/camara](https://www.infobip.com/docs/api/connectivity/camara)
- **Base URL:** `https://api.infobip.com`

#### Tags

- CAMARA
- Connectivity

#### Properties

- [OpenAPI](openapi/infobip-camara-openapi.json) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Documentation](https://www.infobip.com/docs/api/connectivity/camara)
- [API Reference](https://www.infobip.com/docs/api/connectivity/camara)

### Infobip Catalogs API

Create and manage your catalogs to use with other Infobip solutions. Catalogs are similar to databases, you can store and retrieve data sets. Concepts explained Catalog - a set of records. Each record can be for a product or service. Item - a record within a catalog. An item could be a product or service. — 7 operation path(s) and 0 webhook(s) in Infobip's published OpenAPI.

- **Human URL:** [https://www.infobip.com/docs/api/platform/catalogs-api](https://www.infobip.com/docs/api/platform/catalogs-api)
- **Base URL:** `https://api.infobip.com`

#### Tags

- Catalogs
- Platform

#### Properties

- [OpenAPI](openapi/infobip-catalogs-api-openapi.json) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Documentation](https://www.infobip.com/docs/api/platform/catalogs-api)
- [API Reference](https://www.infobip.com/docs/api/platform/catalogs-api)

### Infobip Common Assets API

Reuse assets created on Infobip SaaS products in order to recreate configuration more easily on a single or across multiple accounts. Export or share Moments flows, Answers chatbots or other SaaS assets from your account and import it on another one. This feature is in Early access stage. — 4 operation path(s) and 2 webhook(s) in Infobip's published OpenAPI.

- **Human URL:** [https://www.infobip.com/docs/api/customer-engagement/common-assets](https://www.infobip.com/docs/api/customer-engagement/common-assets)
- **Base URL:** `https://api.infobip.com`

#### Tags

- Common Assets
- Customer Engagement

#### Properties

- [OpenAPI](openapi/infobip-common-assets-openapi.json) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Documentation](https://www.infobip.com/docs/api/customer-engagement/common-assets)
- [API Reference](https://www.infobip.com/docs/api/customer-engagement/common-assets)

### Infobip Conversations API

Conversations is a solution that allows Enterprises to engage in conversations with their customers over multiple channels. The solution is available either as a web-based cloud platform web interface or over HTTP API for 2-way messaging over SMS, WhatsApp, Viber, and Facebook messenger. — 75 operation path(s) and 0 webhook(s) in Infobip's published OpenAPI.

- **Human URL:** [https://www.infobip.com/docs/api/customer-engagement/conversations](https://www.infobip.com/docs/api/customer-engagement/conversations)
- **Base URL:** `https://api.infobip.com`

#### Tags

- Conversations
- Customer Engagement

#### Properties

- [OpenAPI](openapi/infobip-conversations-openapi.json) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Documentation](https://www.infobip.com/docs/api/customer-engagement/conversations)
- [API Reference](https://www.infobip.com/docs/api/customer-engagement/conversations)

### Infobip Email API

Infobip Email is a cloud-based, all-in-one communication solution suited for both transactional and marketing email message delivery. It allows users to create rich, personalized, and responsive emails using API. — 35 operation path(s) and 4 webhook(s) in Infobip's published OpenAPI.

- **Human URL:** [https://www.infobip.com/docs/api/channels/email](https://www.infobip.com/docs/api/channels/email)
- **Base URL:** `https://api.infobip.com`

#### Tags

- Email
- Channels

#### Properties

- [OpenAPI](openapi/infobip-email-openapi.json) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Documentation](https://www.infobip.com/docs/api/channels/email)
- [API Reference](https://www.infobip.com/docs/api/channels/email)

### Infobip Instagram Direct Messages API

Instagram DMs are an in-app messaging feature that enables your business to be reachable by your customers over one of the most popular social media platforms. To utilize Instagram DMs in combination with other channels, check out Messages API. — 3 operation path(s) and 2 webhook(s) in Infobip's published OpenAPI.

- **Human URL:** [https://www.infobip.com/docs/api/channels/instagram](https://www.infobip.com/docs/api/channels/instagram)
- **Base URL:** `https://api.infobip.com`

#### Tags

- Instagram Direct Messages
- Channels

#### Properties

- [OpenAPI](openapi/infobip-instagram-openapi.json) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Documentation](https://www.infobip.com/docs/api/channels/instagram)
- [API Reference](https://www.infobip.com/docs/api/channels/instagram)

### Infobip Kakao Talk API

Kakao Talk holds immense value in the Korean market due to its widespread adoption, versatile features, and seamless integration into various aspects of daily life. In South Korea, Kakao Talk has become an integral part of communication. — 12 operation path(s) and 4 webhook(s) in Infobip's published OpenAPI.

- **Human URL:** [https://www.infobip.com/docs/api/channels/kakao](https://www.infobip.com/docs/api/channels/kakao)
- **Base URL:** `https://api.infobip.com`

#### Tags

- Kakao Talk
- Channels

#### Properties

- [OpenAPI](openapi/infobip-kakao-openapi.json) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Documentation](https://www.infobip.com/docs/api/channels/kakao)
- [API Reference](https://www.infobip.com/docs/api/channels/kakao)

### Infobip Knowledge Base API

Knowledge Base is a centralized content management system for creating, organizing, and retrieving articles, attachments, and structured content. Content is organized into categories, folders, and a hierarchical content tree. — 18 operation path(s) and 0 webhook(s) in Infobip's published OpenAPI.

- **Human URL:** [https://www.infobip.com/docs/api/customer-engagement/knowledge-base](https://www.infobip.com/docs/api/customer-engagement/knowledge-base)
- **Base URL:** `https://api.infobip.com`

#### Tags

- Knowledge Base
- Customer Engagement

#### Properties

- [OpenAPI](openapi/infobip-knowledge-base-openapi.json) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Documentation](https://www.infobip.com/docs/api/customer-engagement/knowledge-base)
- [API Reference](https://www.infobip.com/docs/api/customer-engagement/knowledge-base)

### Infobip LINE API

Disrupt the Southeast Asian market with LINE messaging. Send timely notifications and reminders to your customers, through pre-approved templates, so they can take prompt action and never miss out on communications. To utilize LINE in combination with other channels, check out Messages API. — 2 operation path(s) and 1 webhook(s) in Infobip's published OpenAPI.

- **Human URL:** [https://www.infobip.com/docs/api/channels/line](https://www.infobip.com/docs/api/channels/line)
- **Base URL:** `https://api.infobip.com`

#### Tags

- LINE
- Channels

#### Properties

- [OpenAPI](openapi/infobip-line-openapi.json) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Documentation](https://www.infobip.com/docs/api/channels/line)
- [API Reference](https://www.infobip.com/docs/api/channels/line)

### Infobip Live Chat API

Infobip Live Chat product offers real-time chat communication with customer on your website or in through your mobile app. More information about the product you can find at Live Chat product documentation. — 1 operation path(s) and 1 webhook(s) in Infobip's published OpenAPI.

- **Human URL:** [https://www.infobip.com/docs/api/channels/live-chat](https://www.infobip.com/docs/api/channels/live-chat)
- **Base URL:** `https://api.infobip.com`

#### Tags

- Live Chat
- Channels

#### Properties

- [OpenAPI](openapi/infobip-live-chat-openapi.json) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Documentation](https://www.infobip.com/docs/api/channels/live-chat)
- [API Reference](https://www.infobip.com/docs/api/channels/live-chat)

### Infobip Messages API API

The Messages API integrates multiple messaging channels into one interface. Instead of using a separate API for each messaging channel, use only one API for multiple channels and message types. — 5 operation path(s) and 3 webhook(s) in Infobip's published OpenAPI.

- **Human URL:** [https://www.infobip.com/docs/api/platform/messages-api](https://www.infobip.com/docs/api/platform/messages-api)
- **Base URL:** `https://api.infobip.com`

#### Tags

- Messages API
- Platform

#### Properties

- [OpenAPI](openapi/infobip-messages-api-openapi.json) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Documentation](https://www.infobip.com/docs/api/platform/messages-api)
- [API Reference](https://www.infobip.com/docs/api/platform/messages-api)

### Infobip Messenger API

Grow your business with conversations on Messenger. To utilize Messenger in combination with other channels, check out Messages API. — 11 operation path(s) and 5 webhook(s) in Infobip's published OpenAPI.

- **Human URL:** [https://www.infobip.com/docs/api/channels/messenger](https://www.infobip.com/docs/api/channels/messenger)
- **Base URL:** `https://api.infobip.com`

#### Tags

- Messenger
- Channels

#### Properties

- [OpenAPI](openapi/infobip-messenger-openapi.json) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Documentation](https://www.infobip.com/docs/api/channels/messenger)
- [API Reference](https://www.infobip.com/docs/api/channels/messenger)

### Infobip Metrics API

Metrics API is a way to access aggregated traffic information. By integrating this API, you can retrieve analytics related to your communications and build your own reporting facilities. — 2 operation path(s) and 1 webhook(s) in Infobip's published OpenAPI.

- **Human URL:** [https://www.infobip.com/docs/api/platform/metrics-api](https://www.infobip.com/docs/api/platform/metrics-api)
- **Base URL:** `https://api.infobip.com`

#### Tags

- Metrics
- Platform

#### Properties

- [OpenAPI](openapi/infobip-metrics-api-openapi.json) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Documentation](https://www.infobip.com/docs/api/platform/metrics-api)
- [API Reference](https://www.infobip.com/docs/api/platform/metrics-api)

### Infobip MMS API

Infobip MMS API allows you to send and receive MMS messages and receive delivery reports on your endpoint in real time. You can send messages up to 1600 characters in length together with multimedia content including images and videos. To utilize MMS in combination with other channels, check out Messages API. — 8 operation path(s) and 4 webhook(s) in Infobip's published OpenAPI.

- **Human URL:** [https://www.infobip.com/docs/api/channels/mms](https://www.infobip.com/docs/api/channels/mms)
- **Base URL:** `https://api.infobip.com`

#### Tags

- MMS
- Channels

#### Properties

- [OpenAPI](openapi/infobip-mms-openapi.json) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Documentation](https://www.infobip.com/docs/api/channels/mms)
- [API Reference](https://www.infobip.com/docs/api/channels/mms)

### Infobip Mobile push and in-app messaging API

Mobile push and in-app messaging is a set of API requests to send mobile push and in-app messages, receive data about an application with a mobile SDK​, and receive statistics and reports about push messages​. — 16 operation path(s) and 1 webhook(s) in Infobip's published OpenAPI.

- **Human URL:** [https://www.infobip.com/docs/api/channels/mobile-app-messaging](https://www.infobip.com/docs/api/channels/mobile-app-messaging)
- **Base URL:** `https://api.infobip.com`

#### Tags

- Mobile push and in-app messaging
- Channels

#### Properties

- [OpenAPI](openapi/infobip-mobile-app-messaging-openapi.json) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Documentation](https://www.infobip.com/docs/api/channels/mobile-app-messaging)
- [API Reference](https://www.infobip.com/docs/api/channels/mobile-app-messaging)

### Infobip Mobile Identity API

Contact us and get started with Mobile Identity. Please fill out the form, and our experts will contact you shortly. — 8 operation path(s) and 3 webhook(s) in Infobip's published OpenAPI.

- **Human URL:** [https://www.infobip.com/docs/api/connectivity/mobile-identity](https://www.infobip.com/docs/api/connectivity/mobile-identity)
- **Base URL:** `https://api.infobip.com`

#### Tags

- Mobile Identity
- Connectivity

#### Properties

- [OpenAPI](openapi/infobip-mobile-identity-openapi.json) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Documentation](https://www.infobip.com/docs/api/connectivity/mobile-identity)
- [API Reference](https://www.infobip.com/docs/api/connectivity/mobile-identity)

### Infobip Moments API

Use Moments to set up and manage automated messaging campaigns with your customers by building conversation workflows. — 7 operation path(s) and 0 webhook(s) in Infobip's published OpenAPI.

- **Human URL:** [https://www.infobip.com/docs/api/customer-engagement/moments](https://www.infobip.com/docs/api/customer-engagement/moments)
- **Base URL:** `https://api.infobip.com`

#### Tags

- Moments
- Customer Engagement

#### Properties

- [OpenAPI](openapi/infobip-moments-openapi.json) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Documentation](https://www.infobip.com/docs/api/customer-engagement/moments)
- [API Reference](https://www.infobip.com/docs/api/customer-engagement/moments)

### Infobip Number Activation State API

Number Activation State are reports with end user numbers that had a change in their activation status. Those would be usually numbers that become deactivated, however sometimes they would also have information about temporary suspensions or re-activations. Number state information is provided by our suppliers. — 2 operation path(s) and 0 webhook(s) in Infobip's published OpenAPI.

- **Human URL:** [https://www.infobip.com/docs/api/connectivity/number-activation-state](https://www.infobip.com/docs/api/connectivity/number-activation-state)
- **Base URL:** `https://api.infobip.com`

#### Tags

- Number Activation State
- Connectivity

#### Properties

- [OpenAPI](openapi/infobip-number-activation-state-openapi.json) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Documentation](https://www.infobip.com/docs/api/connectivity/number-activation-state)
- [API Reference](https://www.infobip.com/docs/api/connectivity/number-activation-state)

### Infobip Number lookup API

Number Lookup is a product that draws information from Home Location Register which is a database that contains important information about every mobile subscriber of a specific mobile network. — 3 operation path(s) and 0 webhook(s) in Infobip's published OpenAPI.

- **Human URL:** [https://www.infobip.com/docs/api/connectivity/number-lookup](https://www.infobip.com/docs/api/connectivity/number-lookup)
- **Base URL:** `https://api.infobip.com`

#### Tags

- Number lookup
- Connectivity

#### Properties

- [OpenAPI](openapi/infobip-number-lookup-openapi.json) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Documentation](https://www.infobip.com/docs/api/connectivity/number-lookup)
- [API Reference](https://www.infobip.com/docs/api/connectivity/number-lookup)

### Infobip Numbers API

Numbers are essential for two way communication and your branding. Buy and manage your numbers to send and receive messages and voice calls. — 47 operation path(s) and 7 webhook(s) in Infobip's published OpenAPI.

- **Human URL:** [https://www.infobip.com/docs/api/platform/numbers](https://www.infobip.com/docs/api/platform/numbers)
- **Base URL:** `https://api.infobip.com`

#### Tags

- Numbers
- Platform

#### Properties

- [OpenAPI](openapi/infobip-numbers-openapi.json) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Documentation](https://www.infobip.com/docs/api/platform/numbers)
- [API Reference](https://www.infobip.com/docs/api/platform/numbers)

### Infobip OMNI Failover API

Send messages over WhatsApp, Viber, Voice, VKontakte, Line and other channels with a failover to SMS or any other channel of your choice. — 5 operation path(s) and 3 webhook(s) in Infobip's published OpenAPI.

- **Human URL:** [https://www.infobip.com/docs/api/channels/omni-failover](https://www.infobip.com/docs/api/channels/omni-failover)
- **Base URL:** `https://api.infobip.com`

#### Tags

- OMNI Failover
- Channels

#### Properties

- [OpenAPI](openapi/infobip-omni-failover-openapi.json) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Documentation](https://www.infobip.com/docs/api/channels/omni-failover)
- [API Reference](https://www.infobip.com/docs/api/channels/omni-failover)

### Infobip Open Channel API

Open Channel enables your system to exchange messages with Infobip SaaS products through the Infobip public API. Inbound messages are sent through the Infobip API to the Open Channel destination that is registered on the Infobip platform. The messages are sent to a SaaS product, like a chatbot. — 1 operation path(s) and 1 webhook(s) in Infobip's published OpenAPI.

- **Human URL:** [https://www.infobip.com/docs/api/channels/open-channel](https://www.infobip.com/docs/api/channels/open-channel)
- **Base URL:** `https://api.infobip.com`

#### Tags

- Open Channel
- Channels

#### Properties

- [OpenAPI](openapi/infobip-open-channel-openapi.json) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Documentation](https://www.infobip.com/docs/api/channels/open-channel)
- [API Reference](https://www.infobip.com/docs/api/channels/open-channel)

### Infobip OpenAPI Specification API

OpenAPI is an industry-standard specification for defining REST APIs. It allows you to generate client libraries, automate API testing, and streamline integration workflows. Infobip OpenAPI specification is publicly available as a complete OpenAPI specification with all Infobip products. — 3 operation path(s) and 0 webhook(s) in Infobip's published OpenAPI.

- **Human URL:** [https://www.infobip.com/docs/api/tools/openapi](https://www.infobip.com/docs/api/tools/openapi)
- **Base URL:** `https://api.infobip.com`

#### Tags

- OpenAPI
- Tools

#### Properties

- [OpenAPI](openapi/infobip-openapi-openapi.json) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Documentation](https://www.infobip.com/docs/api/tools/openapi)
- [API Reference](https://www.infobip.com/docs/api/tools/openapi)

### Infobip People API

Build rich profiles for each person to create audience segments for more precise targeting. Manage duplicates and import your data over API. Events reflect actions that end users take on your website or in your mobile application. Events API is a robust way to send those events to Infobip. — 37 operation path(s) and 0 webhook(s) in Infobip's published OpenAPI.

- **Human URL:** [https://www.infobip.com/docs/api/customer-engagement/people](https://www.infobip.com/docs/api/customer-engagement/people)
- **Base URL:** `https://api.infobip.com`

#### Tags

- People
- Customer Engagement

#### Properties

- [OpenAPI](openapi/infobip-people-openapi.json) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Documentation](https://www.infobip.com/docs/api/customer-engagement/people)
- [API Reference](https://www.infobip.com/docs/api/customer-engagement/people)

### Infobip RCS API

Rich Communication Services (RCS) is a new, visually appealing messaging channel that offers rich functionalities to enable more engaging customer journeys. RCS is sometimes referred to as the “SMS 2.0”. — 23 operation path(s) and 11 webhook(s) in Infobip's published OpenAPI.

- **Human URL:** [https://www.infobip.com/docs/api/channels/rcs](https://www.infobip.com/docs/api/channels/rcs)
- **Base URL:** `https://api.infobip.com`

#### Tags

- RCS
- Channels

#### Properties

- [OpenAPI](openapi/infobip-rcs-openapi.json) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Documentation](https://www.infobip.com/docs/api/channels/rcs)
- [API Reference](https://www.infobip.com/docs/api/channels/rcs)

### Infobip Resources API

The Resources API is a set of endpoints designed to manage and request communication resources, such as alphanumeric senders and numbers. Automate resource registration, validation, and provisioning to reduce manual workload. — 10 operation path(s) and 2 webhook(s) in Infobip's published OpenAPI.

- **Human URL:** [https://www.infobip.com/docs/api/platform/resources](https://www.infobip.com/docs/api/platform/resources)
- **Base URL:** `https://api.infobip.com`

#### Tags

- Resources
- Platform

#### Properties

- [OpenAPI](openapi/infobip-resources-openapi.json) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Documentation](https://www.infobip.com/docs/api/platform/resources)
- [API Reference](https://www.infobip.com/docs/api/platform/resources)

### Infobip Sending Strategy Management API

Sending Strategy represents one type of configuration for your sending resources. This configuration in its simplest form allows you to set manipulation for your senders on a country level for a specific channel (SMS/MMS) on an Entity or Application-Entity level (read more about Entity and Application here). — 2 operation path(s) and 0 webhook(s) in Infobip's published OpenAPI.

- **Human URL:** [https://www.infobip.com/docs/api/platform/sending-strategy](https://www.infobip.com/docs/api/platform/sending-strategy)
- **Base URL:** `https://api.infobip.com`

#### Tags

- Sending Strategy Management
- Platform

#### Properties

- [OpenAPI](openapi/infobip-sending-strategy-openapi.json) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Documentation](https://www.infobip.com/docs/api/platform/sending-strategy)
- [API Reference](https://www.infobip.com/docs/api/platform/sending-strategy)

### Infobip Signals API

Signals is a solution for detecting and blocking artificially generated traffic. Each mobile device has a unique identifier assigned to it. It's called a Mobile Station International Subscriber Directory Number. Use this API to create a list of trusted MSISDNs and add/remove numbers from it. — 2 operation path(s) and 0 webhook(s) in Infobip's published OpenAPI.

- **Human URL:** [https://www.infobip.com/docs/api/platform/signals](https://www.infobip.com/docs/api/platform/signals)
- **Base URL:** `https://api.infobip.com`

#### Tags

- Signals
- Platform

#### Properties

- [OpenAPI](openapi/infobip-signals-openapi.json) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Documentation](https://www.infobip.com/docs/api/platform/signals)
- [API Reference](https://www.infobip.com/docs/api/platform/signals)

### Infobip SMS API

SMS (Short Message Service) is the most extensive messaging service available in terms of reach and coverage. A SMS can be sent to and from any mobile device in the world and does not necessarily require a data connection. — 14 operation path(s) and 4 webhook(s) in Infobip's published OpenAPI.

- **Human URL:** [https://www.infobip.com/docs/api/channels/sms](https://www.infobip.com/docs/api/channels/sms)
- **Base URL:** `https://api.infobip.com`

#### Tags

- SMS
- Channels

#### Properties

- [OpenAPI](openapi/infobip-sms-openapi.json) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Documentation](https://www.infobip.com/docs/api/channels/sms)
- [API Reference](https://www.infobip.com/docs/api/channels/sms)

### Infobip Subscriptions Management API

Subscriptions are a way to manage notifications sent to your webhooks by Infobip. It is a useful feature if you want to narrow down the list of events to be notified about or specify different webhooks for different use cases. It will also allow you to set up authentication settings for your endpoint. — 11 operation path(s) and 0 webhook(s) in Infobip's published OpenAPI.

- **Human URL:** [https://www.infobip.com/docs/api/platform/subscriptions-api](https://www.infobip.com/docs/api/platform/subscriptions-api)
- **Base URL:** `https://api.infobip.com`

#### Tags

- Subscriptions Management
- Platform

#### Properties

- [OpenAPI](openapi/infobip-subscriptions-api-openapi.json) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Documentation](https://www.infobip.com/docs/api/platform/subscriptions-api)
- [API Reference](https://www.infobip.com/docs/api/platform/subscriptions-api)

### Infobip TikTok API

TikTok Business Messaging enables one-to-one conversations between TikTok users and your TikTok Business Account. With Infobip, you can receive inbound messages through webhooks, reply to users using the API, send events, and track delivery and seen status. — 4 operation path(s) and 3 webhook(s) in Infobip's published OpenAPI.

- **Human URL:** [https://www.infobip.com/docs/api/channels/tiktok](https://www.infobip.com/docs/api/channels/tiktok)
- **Base URL:** `https://api.infobip.com`

#### Tags

- TikTok
- Channels

#### Properties

- [OpenAPI](openapi/infobip-tiktok-openapi.json) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Documentation](https://www.infobip.com/docs/api/channels/tiktok)
- [API Reference](https://www.infobip.com/docs/api/channels/tiktok)

### Infobip Viber API

Viber offers businesses a dynamic duo of tools - Viber Business Messages and Viber Bots. These solutions are designed to revolutionize customer engagement and communication strategies, providing businesses with a direct and effective means of connecting with their audience. — 12 operation path(s) and 5 webhook(s) in Infobip's published OpenAPI.

- **Human URL:** [https://www.infobip.com/docs/api/channels/viber](https://www.infobip.com/docs/api/channels/viber)
- **Base URL:** `https://api.infobip.com`

#### Tags

- Viber
- Channels

#### Properties

- [OpenAPI](openapi/infobip-viber-openapi.json) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Documentation](https://www.infobip.com/docs/api/channels/viber)
- [API Reference](https://www.infobip.com/docs/api/channels/viber)

### Infobip Vocalize API

Infobip Vocalize API allows you to integrate AI Gamification features into your application. — 9 operation path(s) and 0 webhook(s) in Infobip's published OpenAPI.

- **Human URL:** [https://www.infobip.com/docs/api/customer-engagement/vocalize](https://www.infobip.com/docs/api/customer-engagement/vocalize)
- **Base URL:** `https://api.infobip.com`

#### Tags

- Vocalize
- Customer Engagement

#### Properties

- [OpenAPI](openapi/infobip-vocalize-openapi.json) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Documentation](https://www.infobip.com/docs/api/customer-engagement/vocalize)
- [API Reference](https://www.infobip.com/docs/api/customer-engagement/vocalize)

### Infobip Voice API

Infobip Voice API allows you to engage into voice communication with your customer using the Voice API features. With Calls API, you can use our granular APIs to create any inbound or outbound voice and video scenario you require. — 113 operation path(s) and 16 webhook(s) in Infobip's published OpenAPI.

- **Human URL:** [https://www.infobip.com/docs/api/channels/voice](https://www.infobip.com/docs/api/channels/voice)
- **Base URL:** `https://api.infobip.com`

#### Tags

- Voice
- Channels

#### Properties

- [OpenAPI](openapi/infobip-voice-openapi.json) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Documentation](https://www.infobip.com/docs/api/channels/voice)
- [API Reference](https://www.infobip.com/docs/api/channels/voice)

### Infobip WebRTC API

Infobip WebRTC provide a simplified and secure way of real-time audio and video communication over the web and inside mobile applications. It's powered by Web Real-Time Communication (WebRTC) technology, the leading real-time communication standard built into more than a billion devices. — 22 operation path(s) and 1 webhook(s) in Infobip's published OpenAPI.

- **Human URL:** [https://www.infobip.com/docs/api/channels/webrtc-calls](https://www.infobip.com/docs/api/channels/webrtc-calls)
- **Base URL:** `https://api.infobip.com`

#### Tags

- WebRTC
- Channels

#### Properties

- [OpenAPI](openapi/infobip-webrtc-calls-openapi.json) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Documentation](https://www.infobip.com/docs/api/channels/webrtc-calls)
- [API Reference](https://www.infobip.com/docs/api/channels/webrtc-calls)

### Infobip WhatsApp API

With 2 billion users, WhatsApp is the most used application worldwide. It enables you to reach more customers, sharing important and timely notifications, as well as provide real-time customer support. Infobip is an official WhatsApp Business solution provider. — 52 operation path(s) and 7 webhook(s) in Infobip's published OpenAPI.

- **Human URL:** [https://www.infobip.com/docs/api/channels/whatsapp](https://www.infobip.com/docs/api/channels/whatsapp)
- **Base URL:** `https://api.infobip.com`

#### Tags

- WhatsApp
- Channels

#### Properties

- [OpenAPI](openapi/infobip-whatsapp-openapi.json) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Documentation](https://www.infobip.com/docs/api/channels/whatsapp)
- [API Reference](https://www.infobip.com/docs/api/channels/whatsapp)

### Infobip Zalo API

Zalo offers businesses a dynamic tool - Zalo Notification Service. This solution is designed to revolutionize customer engagement and communication strategies, providing businesses with a direct and effective means of connecting with their audience. — 8 operation path(s) and 2 webhook(s) in Infobip's published OpenAPI.

- **Human URL:** [https://www.infobip.com/docs/api/channels/zalo](https://www.infobip.com/docs/api/channels/zalo)
- **Base URL:** `https://api.infobip.com`

#### Tags

- Zalo
- Channels

#### Properties

- [OpenAPI](openapi/infobip-zalo-openapi.json) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Documentation](https://www.infobip.com/docs/api/channels/zalo)
- [API Reference](https://www.infobip.com/docs/api/channels/zalo)

## Common Properties

- [Website](https://www.infobip.com/)
- [Documentation](https://www.infobip.com/docs)
- [APIReference](https://www.infobip.com/docs/api)
- [OpenAPI](openapi/infobip-platform-full-openapi.json)
- [OpenAPIEndpoint](https://api.infobip.com/platform/1/openapi)
- [Authentication](https://www.infobip.com/docs/essentials/api-essentials/api-authorization)
- [SDK](https://www.infobip.com/docs/sdk)
- [Postman](https://www.postman.com/infobip/infobip-api)
- [MCP](https://www.infobip.com/docs/mcp)
- [GitHubOrganization](https://github.com/infobip)
- [SignUp](https://www.infobip.com/signup)
- [Pricing](https://www.infobip.com/pricing)
- [StatusPage](https://status.infobip.com/)
- [ChangeLog](https://www.infobip.com/docs/release-notes)
- [Blog](https://www.infobip.com/blog)
- [BlogRSS](https://www.infobip.com/blog/feed)
- [LinkedIn](https://www.linkedin.com/company/infobip)
- [Support](https://www.infobip.com/contact)

## Maintainers

- Kin Lane — kin@apievangelist.com
