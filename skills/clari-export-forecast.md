---
name: clari-export-forecast
description: Export a Clari forecast tab as a file using the asynchronous three-step bulk export flow — queue the job, poll until DONE, then download the results.
api: Clari Revenue API
base_url: https://api.clari.com/v4
spec: openapi/clari-forecast-api-api-openapi.yml
operations:
  - externalFcwExport
  - jobStatus
  - externalExportDownload
  - updateJob
generated: '2026-08-13'
method: generated
source: openapi/clari-forecast-api-api-openapi.yml, openapi/clari-bulk-export-framework-api-openapi.yml, conventions/clari-conventions.yml, errors/clari-problem-types.yml
---

# Export a Clari forecast

Forecast data does not leave Clari through a synchronous read. There is no `GET /forecast`. The only route is a three-step asynchronous export.

## Before you start

- **You need a `forecastId`, and no API returns it.** Clari's own documentation says to open the Forecast Tab in the browser and read the id out of the URL. If no Forecast Tab is configured for the data you want, a human has to configure one with their CSM first. Do not guess an id.
- Auth is the `apikey` request header. The token is created in Account Settings > API Token and is shown exactly once.
- If the token's user is deactivated in Clari, every token they created is revoked and this flow starts returning 401 with no other warning.

## Step 1 — queue the export

```
POST /export/forecast/{forecastId}
apikey: <token>
Content-Type: application/json
```

Body fields come from the spec: `timePeriod`, `scopeId`, `typesToExport`, `includeHistorical`, `currency`, `exportFormat` (JSON or CSV).

Returns `200` with a job id.

**Handle these before treating the call as failed:**

- `400` — the job could not be queued. Read the message. The most common cause is **quota exhaustion, not a malformed body** — Clari reports a spent monthly export quota as a 400, not a 429. Call `GET /admin/limits` (operationId `limits`) to confirm before retrying.
- `401` — the user behind the token has no permission for this forecast. This is an authorization failure scoped to the forecast, not a bad token.
- `500` — retry with backoff.

**Do not blind-retry a 5xx or a timeout.** Clari supports no `Idempotency-Key` header on any operation, so a replayed POST may queue a second job against the same quota. On an unknown outcome, call `GET /export/jobs` (operationId `externalFcwExport`) and look for the job you may already have created.

## Step 2 — poll for completion

```
GET /export/jobs/{jobId}
apikey: <token>
```

Poll periodically until `status` is `DONE`. There is no webhook, no callback and no event stream — Clari's spec explicitly instructs clients to poll.

- `403` — invalid permissions to view this job. The token's user cannot see it.
- `400` — the job status could not be retrieved.

Clari publishes **no `Retry-After` and no rate-limit headers**, so choose your own polling interval and back off exponentially. A concurrency limit applies at the organization level; see `rate-limits/clari-rate-limits.yml`.

To modify a queued job, use `PATCH /export/jobs/{jobId}` (operationId `updateJob`).

## Step 3 — download the results

```
GET /export/jobs/{jobId}/results
apikey: <token>
```

Returns the exported payload. `400` here means the job id was not passed correctly or the job has no retrievable output.

## Reading the output

Clari's guides on interpreting the file (linked from the spec description):

- Forecasting Building Blocks — https://clari.my.site.com/customer/s/article/Forecast-Building-Blocks
- How to Read the Forecast Export — https://clari.my.site.com/customer/s/article/How-to-Read-the-Forecast-Export
- How to Read the Export API Output — https://clari.my.site.com/customer/s/article/How-to-Read-Claris-Export-API-Output

## Error envelope

Revenue API errors are proprietary JSON, not RFC 9457: `{statusCode, reasonPhrase, message, errors[]}`. See `errors/clari-problem-types.yml`.
