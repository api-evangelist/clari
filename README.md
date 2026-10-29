# Clari

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

Clari is an enterprise revenue orchestration platform that publishes three machine surfaces. The Clari Revenue API v5 (api.clari.com/v4) is an asynchronous, job-based export and ingest surface — queue a forecast, activity or audit export, poll until the job reads DONE, then download the results — plus a partner Ingestion API for pushing third-party data into Clari accounts and opportunities. The Clari Copilot REST API (rest-api.copilot.clari.com) is a synchronous conversation-intelligence and CRM surface covering calls, transcripts, AI summaries, action items, competitor sentiment, coaching scorecards, and CRUD over accounts, contacts and deals keyed on the customer's own CRM id. Clari also runs a first-party remote MCP server at mcp.clari.com/mcp, OAuth protected via Okta and listed natively in the Claude connector directory, which exposes live Clari + Salesloft revenue context to AI agents. Both HTTP APIs authenticate with header API keys, support no idempotency keys, and return no rate-limit headers.

**Areas:** Revenue Operations · Forecasting · Pipeline Management · Sales Intelligence · Activity Intelligence · Deal Insights · CRM · Conversation Intelligence · B2B · Enterprise · MCP · Agents

## Clari on APIs.io

Everything profiled for Clari is published on APIs.io rather than in this repository. Start at the provider page — **[apis.io/providers/clari/](https://apis.io/providers/clari/)** — or go straight to one of the APIs or properties below.

### APIs (16)

- [Clari MCP Server](https://apis.io/apis/clari/clari-mcp-server/) — Clari's first-party remote Model Context Protocol server. It exposes live Clari + Salesloft revenue context — accounts, deals, people, calls and…
- [Clari Activity API](https://apis.io/apis/clari/clari-activity-api-api/) — The Activity API API from Clari — 1 operation(s) for activity api.
- [Clari Administrative API](https://apis.io/apis/clari/clari-administrative-api-api/) — The Administrative API API from Clari — 1 operation(s) for administrative api.
- [Clari Audit API](https://apis.io/apis/clari/clari-audit-api-api/) — The Audit API API from Clari — 2 operation(s) for audit api.
- [Clari Bulk Export Framework API](https://apis.io/apis/clari/clari-bulk-export-framework-api/) — The Bulk Export Framework API from Clari — 3 operation(s) for bulk export framework.
- [Clari Bulk Ingest Job Status API](https://apis.io/apis/clari/clari-bulk-ingest-job-status-api-api/) — The Bulk Ingest Job Status API API from Clari — 1 operation(s) for bulk ingest job status api.
- [Clari Forecast API](https://apis.io/apis/clari/clari-forecast-api-api/) — The Forecast API API from Clari — 1 operation(s) for forecast api.
- [Clari Ingestion API](https://apis.io/apis/clari/clari-ingestion-api-api/) — The Ingestion API API from Clari — 3 operation(s) for ingestion api.
- [Clari Opportunity API](https://apis.io/apis/clari/clari-opportunity-api-api/) — The Opportunity API API from Clari — 1 operation(s) for opportunity api.
- [Clari Account API](https://apis.io/apis/clari/clari-account-api/) — Accounts in CRM
- [Clari Call API](https://apis.io/apis/clari/clari-call-api/) — Calls in Copilot
- [Clari Contact API](https://apis.io/apis/clari/clari-contact-api/) — Contacts in CRM
- [Clari Deal API](https://apis.io/apis/clari/clari-deal-api/) — Deals in CRM
- [Clari Scorecard API](https://apis.io/apis/clari/clari-scorecard-api/) — Scorecards in Copilot
- [Clari Topics API](https://apis.io/apis/clari/clari-topics-api/) — Topics in Copilot
- [Clari User API](https://apis.io/apis/clari/clari-user-api/) — Users in Copilot

### Published properties

Each property below is a page on APIs.io carrying the machine-readable artifact and what it says.

#### GraphQL (1)

GraphQL schemas.

- [Moved to /providers/clari/](https://apis.io/graphqls/clari/clari-graphql/)

#### MCP servers (1)

Model Context Protocol servers that expose the API to agents.

- [Clari MCP Server](https://apis.io/servers/clari/clari-mcp-server/)

#### Agentic access (1)

Which operations an agent can call, which act, and which need a human in the loop.

- [Clari Agentic Access](https://apis.io/agentic-access/clari/clari-agentic-access/)

#### JSON Schema (3)

The data models the API reads and writes.

- [ClariExportJob](https://apis.io/schemas/clari/clari-export-job/)
- [ClariForecastExportRequest](https://apis.io/schemas/clari/clari-forecast-export-request/)
- [ClariIngestionRequest](https://apis.io/schemas/clari/clari-ingestion-request/)

#### JSON-LD (1)

Linked-data contexts for the provider's vocabulary.

- [Clari Context](https://apis.io/jsonld/clari/clari-context/)

#### Vocabulary (1)

The provider's domain terms, defined.

- [Clari Vocabulary](https://apis.io/vocabularies/clari/clari-vocabulary/)

#### Examples (3)

Example requests and responses.

- [Clari Activity Export Example](https://apis.io/examples/clari/clari-activity-export-example/)
- [Clari Forecast Export Example](https://apis.io/examples/clari/clari-forecast-export-example/)
- [Clari Job Status Example](https://apis.io/examples/clari/clari-job-status-example/)

#### Collections (10)

Postman and Open Collection request collections.

- [Clari API Reference Activity API API](https://apis.io/collections/clari/open-clari-activity-api-api/)
- [Clari API Reference Activity API Administrative API API](https://apis.io/collections/clari/open-clari-administrative-api-api/)
- [Clari API Reference Activity API Audit API API](https://apis.io/collections/clari/open-clari-audit-api-api/)
- [Clari API Reference Activity API Bulk Export Framework API](https://apis.io/collections/clari/open-clari-bulk-export-framework-api/)
- [Clari API Reference Activity API Bulk Ingest Job Status API API](https://apis.io/collections/clari/open-clari-bulk-ingest-job-status-api-api/)
- [rest-api](https://apis.io/collections/clari/open-clari-copilot-api/)
- [Clari API Reference Activity API Export API](https://apis.io/collections/clari/open-clari-export-api/)
- [Clari API Reference Activity API Forecast API API](https://apis.io/collections/clari/open-clari-forecast-api-api/)
- [Clari API Reference Activity API Ingestion API API](https://apis.io/collections/clari/open-clari-ingestion-api-api/)
- [Clari API Reference Activity API Opportunity API API](https://apis.io/collections/clari/open-clari-opportunity-api-api/)

#### Overlays (10)

OpenAPI overlays, including conversational phrasing for each operation.

- [Clari Activity Api Api Overlay](https://apis.io/overlays/clari/clari-activity-api-api-overlay/)
- [Clari Administrative Api Api Overlay](https://apis.io/overlays/clari/clari-administrative-api-api-overlay/)
- [Clari Audit Api Api Overlay](https://apis.io/overlays/clari/clari-audit-api-api-overlay/)
- [Clari Bulk Export Framework Api Overlay](https://apis.io/overlays/clari/clari-bulk-export-framework-api-overlay/)
- [Clari Bulk Ingest Job Status Api Api Overlay](https://apis.io/overlays/clari/clari-bulk-ingest-job-status-api-api-overlay/)
- [Clari Copilot Api Overlay](https://apis.io/overlays/clari/clari-copilot-api-overlay/)
- [Clari Export Api Overlay](https://apis.io/overlays/clari/clari-export-api-overlay/)
- [Clari Forecast Api Api Overlay](https://apis.io/overlays/clari/clari-forecast-api-api-overlay/)
- [Clari Ingestion Api Api Overlay](https://apis.io/overlays/clari/clari-ingestion-api-api-overlay/)
- [Clari Opportunity Api Api Overlay](https://apis.io/overlays/clari/clari-opportunity-api-api-overlay/)

#### Governance rules (1)

Spectral rulesets for the provider's contracts.

- [Clari — jsonschema rules](https://apis.io/rules/clari/clari-jsonschema-spectral-rules/)

#### Security (4)

Authentication, trust centre, and vulnerability disclosure.

- [Clari Authentication](https://apis.io/security/clari/clari-authentication/)
- [Clari Domain Security](https://apis.io/security/clari/clari-domain-security/)
- [Clari Trust Center](https://apis.io/security/clari/clari-trust-center/)
- [Clari Vulnerability Disclosure](https://apis.io/security/clari/clari-vulnerability-disclosure/)

#### OAuth scopes (1)

The permissions the API asks for.

- [Clari Scopes](https://apis.io/scopes/clari/clari-scopes/)

#### Plans and pricing (1)

Published plans, tiers and prices.

- [Clari Plans Pricing](https://apis.io/plans/clari/clari-plans-pricing/)

#### Rate limits (1)

Published request limits.

- [Clari Rate Limits](https://apis.io/rate-limits/clari/clari-rate-limits/)

#### FinOps (1)

What the API costs to run, by operation.

- [Clari Finops](https://apis.io/finops/clari/clari-finops/)

## Where to find this API

Links to the company's own pages. This repository publishes no copy of their specifications — the canonical document is theirs and lives at the URLs below.

- [Website](https://www.clari.com/)
- [Documentation](https://developer.clari.com/)
- [Getting started](https://community.clari.com/product-q-a-6/how-to-use-copilot-apis-2258)
- [API reference](https://developer.clari.com/documentation/external_spec)
- [Pricing](https://www.clari.com/pricing/)
- [Support](https://clari.my.site.com/customer/s/get-support)
- [Blog](https://www.clari.com/blog/)
- [Privacy policy](https://www.clari.com/privacy/)
- [Status](https://clari.statuspage.io/)

## API Evangelist rating

**Kin Score 59.1** — strong · rubric 0.25.0 · scored 2026-10-23

| Facet | Score |
|---|---|
| Discoverability | 69.2 |
| Contract quality | 66.0 |
| Contract governance | 28.0 |
| Operational transparency | 78.9 |
| Developer ergonomics | 57.7 |
| Access clarity | 36.8 |

**Agent readiness 56.9** — agent-ready (gated down from agent-native)

| Agent-readiness dimension | Result |
|---|---|
| Spec Presence | yes |
| Agentic Access | derived (partial credit) |
| Reversibility Documented | documented (partial credit) |
| MCP Server | verified |
| Auth Clarity | served (partial credit) |
| Idempotency | — |
| Error Semantics | verified |
| OpenAPI Examples | verified |
| Rate Limit Signal | documented (partial credit) |
| Event Surface Described | — |
| Agent Skills | derived (partial credit) |
| Well Known Catalog | — |
| Consent Identity | — |
| Agent Card | — |
| Dry Run Mode | — |
| Delegated Identity | served (partial credit) |
| Protected Resource Metadata | verified |
| Dynamic Client Registration | yes |
| Agentic Commerce | — |
| Pagination Ratio | — |
| Operation Distinctiveness | distinct |

**Regulatory alignment 41.2** — Horizontal (data, software, accessibility, platform)

The rubric is published at [github.com/api-evangelist/kin-score](https://github.com/api-evangelist/kin-score). The per-check breakdown behind these numbers — which checks were earned, partial or missed — along with score history and how this provider compares to its peers, is available at [apis.io/providers/clari/](https://apis.io/providers/clari/).

## How this profile is made

API Evangelist profiles a company's public API surface the way a developer would find it: the website, developer portal and documentation, the specifications it publishes, its public repositories, and its pricing, status and changelog pages. From that it derives the properties above — contracts split per API, workflows, schemas, collections, governance rules, plans and rate limits — and scores them against the published [Kin Score rubric](https://github.com/api-evangelist/kin-score).

The artifacts are published on [APIs.io](https://apis.io), not in this repository. This repository is the public record for Clari: the place to say something is wrong, missing or out of date, and to ask for a re-score or a removal.

## Open an issue

- **Something about this listing** — a wrong description, a missing API, a stale artifact or a question about the rating: [open an issue on this repository](https://github.com/api-evangelist/clari/issues/new).
- **A new API, or one that is not in the catalog yet** — [submit it on APIs.io](https://apis.io/add/).
- **Anything else** — [the APIs.io inbox](https://github.com/api-search/inbox/issues/new) or [info@apievangelist.com](mailto:info@apievangelist.com).
