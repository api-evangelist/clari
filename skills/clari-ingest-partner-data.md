---
name: clari-ingest-partner-data
description: Push partner or third-party revenue data into Clari accounts and opportunities using the Ingestion API, including registering custom picklist fields and handling the 428 precondition and all-or-nothing batch semantics.
api: Clari Revenue API
base_url: https://api.clari.com/v4
spec: openapi/clari-ingestion-api-api-openapi.yml
operations:
  - ingestIncremental
  - ingestBulk
  - ingestJobStatus
  - ingestAddPicklist
  - ingestGetPicklist
generated: '2026-08-13'
method: generated
source: openapi/clari-ingestion-api-api-openapi.yml, openapi/clari-bulk-ingest-job-status-api-api-openapi.yml, conventions/clari-conventions.yml, errors/clari-problem-types.yml
---

# Ingest partner data into Clari

The Ingestion API is for integration partners — platforms and revenue tools building a direct data integration so their data surfaces in Clari's Accounts and Opportunities views for mutual customers.

## Auth

- `apikey` header — the standard Clari API token.
- `partnerkey` header — additionally required on partner/ingest endpoints. It appears seven times in the published spec. Sending only `apikey` is not enough here.

## Register the schema first

This is the step that trips agents. A record referencing a custom field that Clari does not know about does not fail with a 400 — it fails with **`428 Precondition Required`**, and 428 is not retryable as-is.

```
GET  /ingest/schema/{entity}/field    (ingestGetPicklist)
POST /ingest/schema/{entity}/field    (ingestAddPicklist)
```

`{entity}` is the target object type (for example `account`, `opportunity`).

1. `GET` the registered fields for the entity.
2. For any custom field or picklist value your payload uses that is not already registered, `POST` it.
3. Only then send records.

`ingestAddPicklist` returns `400` when "the provided field type is not valid or supported".

## Incremental ingest

```
POST /ingest/entity/{entity}    (ingestIncremental)
apikey: <token>
partnerkey: <partner key>
```

- Maximum **100 records per request**.
- `403` — "data ingestion has disabled". This is a tenant configuration state, not a transient error. Do not retry; escalate.
- `428` — a precondition is unmet. Go back to schema registration.
- `429` — rate limit. The documented ceiling is 100 requests/second per token.

## Bulk ingest

```
POST /ingest/bulk/entity/{entity}    (ingestBulk)
```

- Maximum file size **10MB**.
- Returns `202` with a job id.
- **All-or-nothing validation.** Clari's own words: "If records fail validation, the entire batch is rejected and has to be retried after fixing the errors." That makes a *known-failed* batch safe to replay after correction.
- `400` — "input is not in right format".

## Poll the ingest job

```
GET /ingest/job/{jobId}    (ingestJobStatus)
```

Returns `200` when complete or `202` while still running. Errors are retrievable from the results once the job finishes. `404` means the job id is unknown.

## Retry discipline

Clari publishes **no `Idempotency-Key` header** on any operation. A POST whose outcome you do not know is not safe to replay:

- For **bulk** ingest, poll `GET /ingest/job/{jobId}` with the id you were given before sending anything again. If you never received an id, you have no way to check — treat a replay as potentially duplicating records.
- For **incremental** ingest, there is no job to poll at all. Design the caller so the same batch can be reconciled downstream, or keep batches small enough that a duplicate is cheap to correct.

On `429`, back off exponentially. Clari returns **no `Retry-After` and no `X-RateLimit-*` headers**, so there is no budget signal to read — `GET /admin/limits` is the only programmatic view of your consumption.
