# Ensighten

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

Ensighten is an enterprise tag management, data governance, and client-side website security platform. It gives digital, marketing, and privacy teams centralized control over the third-party tags, scripts, and vendor code that run on their web and mobile properties, enforcing consent and privacy rules (GDPR, CCPA) at the point of data collection. The platform combines server- and client-side tag management, malicious-script and data-leakage detection (client-side security), and consent management. Ensighten was acquired by CHEQ (CHEQ AI Technologies Ltd.) and is now delivered as part of CHEQ's Control & Compliance / Go-to-Market Security suite; the ensighten.com domain 301-redirects to cheq.ai. This company profile was surfaced as an Insight Partners portfolio lead and enriched by the API Evangelist pipeline. Ensighten does publish a public REST contract: the Ensighten Manage API, documented as an API Blueprint at manageexternalapi.docs.apiary.io and served in production from manage-api.ensighten.com. It covers 66 operations across Spaces, Publish Paths, Deployments, Conditions, Data Definitions, Event Definitions, Labels, Users, Roles, SCIM 2.0 user/group provisioning, Git-enabled spaces, and TDN jobs. Authentication is either an X-API-Key API key or an OAuth 2.0 Resource Owner Password Credentials bearer token from /auth/token.

**Areas:** Company · Cybersecurity · Tag Management · Data Governance · Client-Side Security · Consent Management · Privacy Compliance · Marketing Technology

## Ensighten on APIs.io

Everything profiled for Ensighten is published on APIs.io rather than in this repository. Start at the provider page — **[apis.io/providers/ensighten/](https://apis.io/providers/ensighten/)** — or go straight to one of the APIs or properties below.

### APIs (13)

- [Ensighten Authentication API](https://apis.io/apis/ensighten/ensighten-authentication-api/) — Requests using a username and password for authentication follow the Resource Owner Password Flow of the OAuth 2.0 specification. API Request Once a token…
- [Ensighten Conditions API](https://apis.io/apis/ensighten/ensighten-conditions-api/) — CRUD operations with Conditions. Important Condition specific fields Field Description Valid Values id The condition id name The name of the condition A…
- [Ensighten Data Definitions API](https://apis.io/apis/ensighten/ensighten-data-definitions-api/) — CRUD operations with Data Definitions. Data Definitions specific fields Field Required Description Valid Values name Y The name of the definition A name up…
- [Ensighten Deployments API](https://apis.io/apis/ensighten/ensighten-deployments-api/) — CRUD operations with Deployments. Important Deployment specific fields Field Description Valid Values id The deployment id name The name of the deployment A…
- [Ensighten Event Definitions API](https://apis.io/apis/ensighten/ensighten-event-definitions-api/) — CRUD operations with Event Definitions. Event Definition specific fields Field Description Valid Values name The name of the definition A name up to 255…
- [Ensighten GIT API](https://apis.io/apis/ensighten/ensighten-git-api/) — Operations specific to Git enabled spaces. Git specific fields Field Description Valid Values commitId Commit ID A SHA-1 hash, 40 characters long
- [Ensighten Labels API](https://apis.io/apis/ensighten/ensighten-labels-api/) — CRUD operations with Labels. Label specific fields Field Description Valid Values key The key of the label A string up to 128 characters. Should only…
- [Ensighten Publish Paths API](https://apis.io/apis/ensighten/ensighten-publish-paths-api/) — CRUD operations with Publish Paths. For further details or guidance on configuring Publish Path settings, please consult our Help Center article available…
- [Ensighten Roles API](https://apis.io/apis/ensighten/ensighten-roles-api/) — CRUD operations with Roles. Role specific fields Field Description Valid Values name Unique identifier for the role Up to 255 characters; Role name should…
- [Ensighten SCIM 2.0 API](https://apis.io/apis/ensighten/ensighten-scim-2-0-api/) — SCIM2 (System for Cross-domain Identity Management) is a specification that automates user and group identity provisioning across cloud-based applications…
- [Ensighten Spaces API](https://apis.io/apis/ensighten/ensighten-spaces-api/) — CRUD operations with Spaces. Space specific fields Field Required Description Valid Values name Y The name of the space A name up to 255 characters…
- [Ensighten TDN API](https://apis.io/apis/ensighten/ensighten-tdn-api/) — Retrieve TDN job information JSON Schema Conforms to JSON schema draft v4 specifications { "$schema": "http://json-schema.org/draft-04/schema#",…
- [Ensighten Users API](https://apis.io/apis/ensighten/ensighten-users-api/) — CRUD operations with Users. User specific fields Field Description Valid Values username Unique identifier for the user Up to 255 characters; cannot include…

### Published properties

Each property below is a page on APIs.io carrying the machine-readable artifact and what it says.

#### Overlays (1)

OpenAPI overlays, including conversational phrasing for each operation.

- [Ensighten Manage Api Overlay](https://apis.io/overlays/ensighten/ensighten-manage-api-overlay/)

#### Security (3)

Authentication, trust centre, and vulnerability disclosure.

- [Ensighten Authentication](https://apis.io/security/ensighten/ensighten-authentication/)
- [Ensighten Domain Security](https://apis.io/security/ensighten/ensighten-domain-security/)
- [Ensighten Trust Center](https://apis.io/security/ensighten/ensighten-trust-center/)

#### Plans and pricing (1)

Published plans, tiers and prices.

- [Ensighten Plans Pricing](https://apis.io/plans/ensighten/ensighten-plans-pricing/)

#### Rate limits (1)

Published request limits.

- [Ensighten Rate Limits](https://apis.io/rate-limits/ensighten/ensighten-rate-limits/)

## Where to find this API

Links to the company's own pages. This repository publishes no copy of their specifications — the canonical document is theirs and lives at the URLs below.

- [Website](https://cheq.ai/ensighten/)
- [Documentation](https://manageexternalapi.docs.apiary.io/)
- [Getting started](https://help.ensighten.com/hc/en-us/sections/22957479812369)
- [API reference](https://manageexternalapi.docs.apiary.io/)
- [Support](https://help.ensighten.com/hc/en-us)
- [Blog](https://cheq.ai/blog/)
- [Compliance](https://cheq.ai/trust/)
- [Trust centre](https://cheq.ai/trust/)
- [Terms of service](https://cheq.ai/cheq-terms-of-service/)
- [Privacy policy](https://cheq.ai/website-privacy-policy/)
- [GitHub](https://github.com/Ensighten)

## API Evangelist rating

**Kin Score 41.5** — developing · rubric 0.25.0 · scored 2026-10-23

| Facet | Score |
|---|---|
| Discoverability | 73.2 |
| Contract quality | 18.6 |
| Contract governance | 18.2 |
| Operational transparency | 47.4 |
| Developer ergonomics | 55.4 |
| Access clarity | 43.4 |

**Agent readiness 27.3** — agent-aware

| Agent-readiness dimension | Result |
|---|---|
| Spec Presence | yes |
| Agentic Access | — |
| Reversibility Documented | — |
| MCP Server | — |
| Auth Clarity | bearer (partial credit) |
| Idempotency | — |
| Error Semantics | documented (partial credit) |
| OpenAPI Examples | verified |
| Rate Limit Signal | documented (partial credit) |
| Event Surface Described | — |
| Agent Skills | derived (partial credit) |
| Well Known Catalog | — |
| Consent Identity | — |
| Agent Card | — |
| Dry Run Mode | — |
| Delegated Identity | — |
| Protected Resource Metadata | — |
| Dynamic Client Registration | — |
| Agentic Commerce | — |
| Pagination Ratio | na |
| Operation Distinctiveness | mostly |

**Regulatory alignment 29.4** — Horizontal (data, software, accessibility, platform)

The rubric is published at [github.com/api-evangelist/kin-score](https://github.com/api-evangelist/kin-score). The per-check breakdown behind these numbers — which checks were earned, partial or missed — along with score history and how this provider compares to its peers, is available at [apis.io/providers/ensighten/](https://apis.io/providers/ensighten/).

## How this profile is made

API Evangelist profiles a company's public API surface the way a developer would find it: the website, developer portal and documentation, the specifications it publishes, its public repositories, and its pricing, status and changelog pages. From that it derives the properties above — contracts split per API, workflows, schemas, collections, governance rules, plans and rate limits — and scores them against the published [Kin Score rubric](https://github.com/api-evangelist/kin-score).

The artifacts are published on [APIs.io](https://apis.io), not in this repository. This repository is the public record for Ensighten: the place to say something is wrong, missing or out of date, and to ask for a re-score or a removal.

## Open an issue

- **Something about this listing** — a wrong description, a missing API, a stale artifact or a question about the rating: [open an issue on this repository](https://github.com/api-evangelist/ensighten/issues/new).
- **A new API, or one that is not in the catalog yet** — [submit it on APIs.io](https://apis.io/add/).
- **Anything else** — [the APIs.io inbox](https://github.com/api-search/inbox/issues/new) or [info@apievangelist.com](mailto:info@apievangelist.com).
