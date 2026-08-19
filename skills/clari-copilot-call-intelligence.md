---
name: clari-copilot-call-intelligence
description: Pull conversation intelligence out of Clari Copilot — list calls, fetch call details with transcript, summary topics, action items and competitor sentiments, and read coaching scorecards.
api: Clari Copilot REST API
base_url: https://rest-api.copilot.clari.com
spec: openapi/clari-copilot-api-openapi.yml
operations:
  - GET /calls
  - GET /call-details
  - GET /users
  - GET /topics
  - GET /v2/topics
  - GET /scorecard
  - GET /scorecard-template
  - POST /create-call
generated: '2026-08-13'
method: generated
source: openapi/clari-copilot-api-openapi.yml, data-model/clari-data-model.yml, conventions/clari-conventions.yml
---

# Read Clari Copilot conversation intelligence

Copilot is a separate API from the Clari Revenue API — different host, different auth, different error envelope, different pagination. Carry nothing over from one to the other.

## Auth

Send **both** headers on every request. Either one alone returns `401`.

```
X-Api-Key: <key>
X-Api-Password: <password>
```

Keys are in Workspace Settings > Integrations > Clari Copilot API.

The Copilot spec assigns **no `operationId`** to any operation, so the path is the stable identifier — refer to operations by method and path.

## Rate limits (published, but not signalled)

- 10 requests/second.
- 100,000 requests/week, week starting Sunday 00:00 GMT.

No `Retry-After`, no `X-RateLimit-*`. Throttle client-side to 10/s and track your own weekly count.

## List calls

```
GET /calls
```

Returns `CallsResponse` — a `calls[]` array plus a `pagination` object. Follow `nextPage` to page through. (Note: the Revenue API paginates with `paginationToken`; Copilot does not.)

Each `Call` carries `id`, `source_id`, calendar identity (`icaluid`, `calendar_id`, `recurring_event_id`), `status`, `type`, `disposition`, `metrics`, and participant arrays — `users` (`CallUser`), `externalParticipants` and `joinedParticipants`.

If a call has no recording, check `bot_not_join_reason` before assuming a data gap — it enumerates why the recording bot did not join.

## Fetch the deep call payload

```
GET /call-details
```

Returns `CallDetailsResponse` wrapping `CallDetails`, which is where the intelligence lives:

- `ExternalTranscript` — with `external_speakers[]` and `ext_conversation_turns[]`
- `SummaryTopics`
- `SummaryActionItems`
- `CompetitorSentiments`

`404` means the call id is unknown or not in this workspace.

**Worth knowing:** raw transcript retrieval was removed from Clari's MCP server for Claude in August 2026 because the protocol could not return the content as intended. This REST route still returns it. If you need transcripts programmatically, this operation — not MCP — is the supported path.

## Topics

```
GET /topics
GET /v2/topics
```

Two generations are live simultaneously. Clari does not state which is canonical or whether `/topics` retires. Prefer `/v2/topics` for new work and pin whichever you choose.

## Scorecards

```
GET /scorecard
GET /scorecard-template
```

A `Scorecard` belongs to a `Call` via `call_id` and to a `ScoreCardTemplate` via `template_id`, and carries `questions_score[]`. To interpret scores you need the template — fetch both.

## Users

```
GET /users
```

Returns `UsersResponse`. `User.manager_id` is self-referencing, so this is also the org chart — walk `manager_id` to build the reporting hierarchy.

## Create a call

```
POST /create-call
```

Returns `CreateCallResponse` with `call_id`. There is no idempotency key on this API either — a replayed create can produce a duplicate call record.

## Errors

Copilot's envelope is `{errorMessage}`, not the Revenue API's `{statusCode, reasonPhrase, message, errors[]}` and not RFC 9457. Most operations declare `400` and `500` with an **empty response schema**, so do not expect a typed body. Example, observed live:

```
401 {"errorMessage":"Credentials not provided!, see documentation: https://api-doc.copilot.clari.com"}
```
