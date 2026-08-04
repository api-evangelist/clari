# Clari (clari)

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

Clari is a revenue operations platform that provides a REST API for accessing pipeline data, forecasts, opportunity signals, activity intelligence, and CRM-enriched deal insights. The API enables revenue teams to programmatically export forecast submissions, query activity data (meetings, emails, attachments), and ingest custom entity data into the Clari platform. Clari also offers a Copilot API for accessing conversation intelligence data including call recordings, AI summaries, and coaching insights. The platform serves enterprise B2B organizations including Okta, Adobe, Workday, and Zoom with tools to improve forecast accuracy, accelerate pipeline execution, and unify revenue operations across sales, marketing, and customer success teams.

- **APIs.json**: https://raw.githubusercontent.com/api-evangelist/clari/refs/heads/main/apis.yml
- **Naftiko**: https://github.com/naftiko/fleet?utm_source=api-evangelist&utm_medium=readme&utm_campaign=clari-api-evangelist&utm_content=repo

## Tags

Revenue Operations, Forecasting, Pipeline Management, Sales Intelligence, Activity Intelligence, Deal Insights, CRM, Conversation Intelligence, B2B, Enterprise

## APIs

| Name | Description | Docs |
|------|-------------|------|
| Clari Revenue API | Forecast exports, activity exports, audit events, and data ingestion via async job-based REST API | https://developer.clari.com/documentation/external_spec |
| Clari Copilot API | Conversation intelligence including call recordings, AI summaries, coaching insights, and deal intelligence | https://api-doc.copilot.clari.com/ |

## Plans, Rate Limits, and FinOps

| Resource | File |
|----------|------|
| Plans and Pricing | [plans/clari-plans-pricing.yml](plans/clari-plans-pricing.yml) |
| Rate Limits | [rate-limits/clari-rate-limits.yml](rate-limits/clari-rate-limits.yml) |
| FinOps | [finops/clari-finops.yml](finops/clari-finops.yml) |

**Plans summary:** Clari Core (~$100–$120/user/month), Clari Copilot (~$60–$100/user/month), Groove (bundled). All pricing is custom-quoted with no public pricing page.

**Rate limits summary:** Revenue API allows 3 concurrent export jobs and 1,000 exports/month per organization; data ingestion allows 100 requests/second per API token. Copilot API allows 10 requests/second and 100,000 requests/week per API key.

## Timestamps

- **Created:** 2026-06-13
- **Modified:** 2026-06-13

## Common

| Type | URL |
|------|-----|
| Website | https://www.clari.com/ |
| Documentation | https://developer.clari.com/ |
| GitHub Org | https://github.com/clari |
| LinkedIn | https://www.linkedin.com/company/clari |
| Blog | https://www.clari.com/blog/ |
| Pricing | https://www.clari.com/pricing/ |
| Status Page | https://clari.statuspage.io/ |
| X (Twitter) | https://x.com/clarihq |

## Maintainers

| Name | Email |
|------|-------|
| Kin Lane | kin@apievangelist.com |
