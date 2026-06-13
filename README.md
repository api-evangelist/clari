# Clari (clari)

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
