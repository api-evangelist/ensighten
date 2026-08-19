---
name: ensighten-publish-a-space
description: >-
  Publish an Ensighten Manage space so its committed tag deployments go live on
  the customer's website, then poll until the publish completes. Use when asked
  to "publish", "push live", "deploy tags" or "release" an Ensighten space.
api: Ensighten Manage API
base_url: https://manage-api.ensighten.com
operations:
  - getManageSpaces
  - getManageSpacesId
  - putManageSpacesIdPublish
  - patchManageSpacesIdPublish
  - getManageSpacesIdPublishPublishid
generated: '2026-08-13'
method: generated
source: openapi/ensighten-manage-api-openapi.yml
---

# Publish an Ensighten Manage space

Publishing pushes tag JavaScript onto the customer's **live public website**. Treat it
as a production deployment, not a data write.

## Before you start

- Authenticate with `X-API-Key: ens_...`. Every request is HTTPS-only and authenticated.
- This flow is **rate limited to 5 publishes per hour, per account**. Check
  `X-Rate-Limit-Remaining` on the response before attempting a second publish.
- There is **no idempotency key**. If a publish request times out, do NOT blindly retry —
  poll for status first (step 4), or you will publish twice against your hourly ceiling.

## 1. Find the space

`getManageSpaces` — `GET /manage/spaces?name={name}`

Optional filters: `name`, `publishPath`, `page`, `per_page` (default 10, max 50).

> A `404` here means **no space matched**, not an error. Treat it as an empty result and
> stop — do not retry.

## 2. Confirm what will go live

`getManageSpacesId` — `GET /manage/spaces/{id}`

Read `mandatedConditions`, `mandatedDeployments` and `lastPublished`. Only deployments in a
`*_committed` status will be included; `*_uncommitted` ones will not. If a deployment needs
to be included, commit it first with the `ensighten-manage-a-deployment` skill.

## 3. Publish

Full publish — `putManageSpacesIdPublish` — `PUT /manage/spaces/{id}/publish`

Selective publish — `patchManageSpacesIdPublish` — `PATCH /manage/spaces/{id}/publish`,
sending only the deployments you intend to release.

Prefer the **selective** form whenever the request names specific deployments; it limits the
blast radius to what was asked for.

Responses:

- `200` — accepted; the body carries the publish identifier to poll.
- `412 Precondition Failed` — a precondition is unmet (full publish only). Read the
  `description` field, resolve it, and try again. Do not retry unchanged.
- `400 Bad Request` — malformed selection (selective publish only).
- `429` — hourly ceiling reached. Read `X-Rate-Limit-Reset` for the seconds remaining and
  wait; do not spin.

## 4. Poll to completion

`getManageSpacesIdPublishPublishid` — `GET /manage/spaces/{id}/publish/{publishId}`

There is **no webhook or callback** in this API. Poll this endpoint until it reports
completion. Back off between polls; publishing is asynchronous and takes time to propagate.

For a Git-enabled space you can also follow the commit with
`getManageSpacesIdCommitCommitid` — `GET /manage/spaces/{id}/commit/{commitId}` — which
returns `{spaceId, commitId, complete, success}`.

## Errors

All errors share one envelope:

```json
{ "code": 412, "message": "Precondition Failed", "description": "..." }
```

The `description` field is the only place the actual cause appears — always surface it.
See `errors/ensighten-problem-types.yml`.

## Do not

- Do not publish without being asked to. It changes a live website.
- Do not retry a non-GET after a timeout without polling first — there is no de-duplication.
- Do not treat a `404` from step 1 as a failure.
