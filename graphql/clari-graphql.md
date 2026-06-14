# Clari GraphQL Schema

## Overview

This document describes a conceptual GraphQL schema for the Clari revenue operations platform. Clari provides programmatic access to pipeline data, forecasts, opportunity signals, activity intelligence, and CRM-enriched deal insights. The schema models the core domain objects available through the Clari Revenue API and Copilot API.

Developer documentation is available at https://developer.clari.com/

## Schema Source

This is a conceptual schema derived from the Clari REST API surface area, developer documentation, and the Clari platform domain model. It represents the types, queries, and mutations that a GraphQL layer would expose over the Clari revenue operations platform.

## Types

### Opportunity Types

- **Opportunity** — Core opportunity record linking to CRM data with stage, amount, close date, and owner.
- **OpportunityDetails** — Extended opportunity metadata including source, type, lead source, competitors, and next steps.
- **OpportunityStage** — Stage name, stage order, probability, and whether the stage is closed-won or closed-lost.
- **OpportunityAmount** — Amount, currency, exchange rate, and adjusted amount fields.
- **OpportunityCloseDate** — Original close date, current close date, and number of times the close date has slipped.

### Forecast Types

- **Forecast** — Top-level forecast submission for a user, team, or roll-up for a given period.
- **ForecastDetails** — Granular forecast fields including submitted values, overrides, and timestamps.
- **ForecastCategory** — Named forecast category (Commit, Best Case, Pipeline, Omitted) with color coding.
- **ForecastPeriod** — The time period a forecast covers (quarter, month, custom).
- **ForecastRoll** — Aggregated roll-up forecast across a management hierarchy.
- **ForecastModel** — The forecast model configuration defining categories, weights, and roll-up logic.

### Prediction Types

- **Prediction** — AI-generated prediction for an opportunity or account outcome.
- **PredictionDetails** — Detailed prediction output including confidence intervals and feature attributions.
- **PredictionScore** — Numeric score (0–100) representing likelihood of a predicted outcome.
- **PredictionCategory** — Classification of the prediction (Won, Lost, Push, At Risk).

### Outcome Types

- **Won** — Closed-won opportunity record with final amount and close date.
- **Lost** — Closed-lost opportunity record with loss reason and competitor information.
- **Committed** — Opportunity or roll-up categorized as Commit in the current forecast.
- **BestCase** — Opportunity or roll-up categorized as Best Case in the current forecast.

### Pipeline Types

- **Pipeline** — Aggregate pipeline view for a user, team, or territory for a period.
- **PipelineDetails** — Breakdown of pipeline by stage, category, and movement.
- **PipelineMetrics** — Pipeline coverage ratio, average deal size, velocity, and creation rate.

### Deal Types

- **Deal** — A deal (opportunity) being tracked in Clari with enriched signals and scores.
- **DealDetails** — Full deal context including account, contact, activities, and history.
- **DealScore** — Composite score reflecting deal health across engagement, momentum, and risk dimensions.
- **DealActivity** — Summary of activity (emails, calls, meetings) associated with a deal.
- **DealRisk** — Risk assessment for a deal with contributing factors and severity.
- **RiskFactor** — An individual risk signal (e.g., no activity in 14 days, single-threaded, pricing concern).
- **ForecastRisk** — Risk signals specific to forecast accuracy and submission behavior.

### Account Types

- **Account** — CRM account record with Clari-enriched health and engagement signals.
- **AccountDetails** — Extended account metadata including industry, size, ARR, and renewal date.
- **AccountHealth** — Composite health score for an account based on engagement and relationship signals.
- **AccountScore** — Numeric health score with dimension breakdown (product usage, engagement, risk).

### Contact Types

- **Contact** — Contact associated with an account or opportunity.
- **ContactDetails** — Full contact profile including title, department, seniority, and influence level.
- **ContactActivity** — Summary of activity with a contact across emails, calls, and meetings.

### Activity Types

- **Activity** — An individual activity event (email, call, meeting, attachment).
- **ActivityDetails** — Full activity record including participants, duration, direction, and sentiment.
- **ActivityType** — Enumeration of activity types: EMAIL, CALL, MEETING, ATTACHMENT.
- **Email** — Email activity record with subject, direction, sentiment, and thread context.
- **Call** — Call activity record with duration, direction, recording reference, and transcript summary.
- **Meeting** — Meeting activity record with attendees, duration, agenda, and Copilot insights.

### User Types

- **User** — A Clari user (rep, manager, or admin) with role and team membership.
- **UserDetails** — Full user profile including CRM ID, territory, role, and manager.
- **UserQuota** — Quota assignments for a user by period and product line.
- **UserPerformance** — Attainment, coverage, and activity metrics for a user in a period.

### Team Types

- **Team** — A team hierarchy node (region, segment, pod) with membership and roll-up data.
- **TeamDetails** — Team metadata including manager, members, territory, and segment.
- **TeamPerformance** — Aggregate attainment, pipeline, and activity metrics for a team.

### Goal Types

- **Goal** — A performance goal assigned to a user or team for a period.
- **GoalDetails** — Goal configuration including type, target value, and measurement method.
- **GoalProgress** — Current progress toward a goal with percent attainment and trend.

### Time Period Types

- **Quarter** — A fiscal quarter with start date, end date, and quarter label.
- **QuarterDetails** — Quarter metadata including fiscal year, year label, and whether the quarter is current.
- **Period** — A generic time period (quarter, month, week, custom) used in forecasts and reporting.
- **FiscalYear** — A fiscal year definition with start month, end month, and quarter breakdown.

### Auth and Integration Types

- **APIKey** — An API key credential for accessing the Clari API.
- **Token** — An authentication token with expiry and scope information.
- **Webhook** — A webhook subscription for receiving Clari event notifications.

## Queries

- `opportunity(id: ID!)` — Fetch a single opportunity by ID.
- `opportunities(filter: OpportunityFilter, page: Int, pageSize: Int)` — List opportunities with optional filters.
- `forecast(userId: ID!, periodId: ID!)` — Fetch a forecast submission for a user and period.
- `forecastRoll(teamId: ID!, periodId: ID!)` — Fetch rolled-up forecast for a team.
- `pipeline(userId: ID, teamId: ID, periodId: ID!)` — Fetch pipeline metrics.
- `deal(id: ID!)` — Fetch a deal with enriched signals.
- `deals(filter: DealFilter, page: Int, pageSize: Int)` — List deals.
- `account(id: ID!)` — Fetch an account with health signals.
- `accounts(filter: AccountFilter, page: Int, pageSize: Int)` — List accounts.
- `user(id: ID!)` — Fetch a user profile.
- `users(filter: UserFilter)` — List users.
- `team(id: ID!)` — Fetch a team.
- `teams` — List all teams.
- `activities(filter: ActivityFilter, page: Int, pageSize: Int)` — List activities.
- `quarter(id: ID!)` — Fetch a quarter definition.
- `quarters(fiscalYear: Int)` — List quarters for a fiscal year.
- `prediction(opportunityId: ID!)` — Fetch AI prediction for an opportunity.

## Mutations

- `submitForecast(input: ForecastInput!)` — Submit or update a forecast.
- `updateOpportunityCategory(opportunityId: ID!, category: ForecastCategoryEnum!)` — Change forecast category for an opportunity.
- `createWebhook(input: WebhookInput!)` — Register a webhook subscription.
- `deleteWebhook(id: ID!)` — Remove a webhook subscription.
- `ingestData(input: DataIngestionInput!)` — Ingest custom entity data into Clari.

## References

- Clari Developer Portal: https://developer.clari.com/
- Clari Copilot API: https://api-doc.copilot.clari.com/
- Clari REST API Base URL: https://api.clari.com/v4
