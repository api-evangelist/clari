---
name: clari-copilot-crm-sync
description: Keep accounts, contacts and deals in sync with Clari Copilot using its CRM CRUD endpoints, addressing every record by the customer's own CRM id.
api: Clari Copilot REST API
base_url: https://rest-api.copilot.clari.com
spec: openapi/clari-copilot-api-openapi.yml
operations:
  - POST /create-account
  - GET /get-account
  - PUT /update-account
  - DELETE /delete-account
  - POST /create-contact
  - GET /get-contact
  - PUT /update-contact
  - DELETE /delete-contact
  - POST /create-deal
  - GET /get-deal
  - PUT /update-deal
  - DELETE /delete-deal
generated: '2026-08-13'
method: generated
source: openapi/clari-copilot-api-openapi.yml, data-model/clari-data-model.yml, conventions/clari-conventions.yml
---

# Sync CRM objects with Clari Copilot

Copilot exposes verb-in-path CRUD over three CRM objects. The endpoints are synchronous — unlike the Revenue API, nothing here is a job.

## The one thing to get right: `crm_id`

Accounts, contacts and deals are addressed by **`crm_id` — the id from the customer's own CRM**, not a Clari-issued identifier. The create-shape schemas are literally named `AccountWithoutId`, `ContactWithoutId` and `DealWithoutId`; the id-bearing variants add `crm_id`.

There is no Clari-native account or deal id in the public contract. If you do not have the source CRM id, you cannot address the record.

## Auth

Both headers, every request:

```
X-Api-Key: <key>
X-Api-Password: <password>
```

## Accounts

```
POST   /create-account     body: AccountWithoutId
GET    /get-account        -> Account
PUT    /update-account     body: Account
DELETE /delete-account
```

`Account` carries `crm_id` and `custom_fields[]` (`CustomField`).

## Contacts

```
POST   /create-contact     body: ContactWithoutId
GET    /get-contact        -> Contact
PUT    /update-contact
DELETE /delete-contact
```

`Contact.account_crm_id` links the contact to its account. Create or confirm the account first, or you will attach contacts to an account that does not exist in Copilot.

## Deals

```
POST   /create-deal        body: DealWithoutId
GET    /get-deal           -> Deal
PUT    /update-deal
DELETE /delete-deal
```

`Deal` links out twice — `account_crm_id` to the account and `owner_crm_id` to the owning user — and carries two history arrays as first-class fields:

- `stage_change_history[]` (`StageChangeHistory`)
- `close_date_change_history[]` (`CloseDateChangeHistory`)

Deal slippage is modelled **inside the deal object**. There is no separate history resource to query, and no audit endpoint on this API. If you need slippage analysis, read these arrays.

Plus `custom_fields[]`.

## Recommended write order

1. Account (`POST /create-account`)
2. Contacts (`POST /create-contact` with `account_crm_id`)
3. Deals (`POST /create-deal` with `account_crm_id` and `owner_crm_id`)

Users are read-only on this API (`GET /users`) — resolve `owner_crm_id` against that list rather than creating users.

## Retry discipline

There is **no `Idempotency-Key` header**. A replayed `POST /create-*` after an unknown outcome can duplicate the record. Because every object is keyed on `crm_id`, the safe pattern is read-before-write:

```
GET /get-account   -> 404 ? create : update
```

`404` is the documented "not found" status on all three `get-*` and all three `delete-*` operations, so it is a reliable existence check.

## Errors

Envelope is `{errorMessage}`. `400` and `500` are declared with an empty schema on these operations, so do not rely on a typed error body. See `errors/clari-problem-types.yml`.
