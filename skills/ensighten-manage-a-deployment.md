---
name: ensighten-manage-a-deployment
description: >-
  Find, create, edit and move an Ensighten tag deployment through its lifecycle
  — enable, disable, commit, uncommit, undelete, archive, unarchive — and merge
  one between spaces. Use when asked to add, change, turn on/off, commit or
  promote a tag in Ensighten Manage.
api: Ensighten Manage API
base_url: https://manage-api.ensighten.com
operations:
  - getManageDeployments
  - postManageDeploymentsSearch
  - getManageSpacesSpaceidDeploymentsId
  - postManageSpacesSpaceidDeployments
  - putManageSpacesSpaceidDeploymentsId
  - deleteManageSpacesSpaceidDeploymentsId
  - putManageSpacesSpaceidDeploymentsIdAction
  - putManageSpacesDeploymentsBatchAction
  - putManageSpacesSpaceidDeploymentsIdMergeTargetspaceid
generated: '2026-08-13'
method: generated
source: openapi/ensighten-manage-api-openapi.yml
---

# Manage an Ensighten tag deployment

A deployment is a unit of tag code that runs on the customer's pages. Its `status` is a
pair: a lifecycle state (`enabled`, `disabled`, `deleted`, `archived`) crossed with a
publish state (`uncommitted`, `committed`, `published`) — e.g. `enabled_committed`.

**Editing a deployment does not make it live.** It must be committed, and then its space
must be published (see `ensighten-publish-a-space`).

## Find it

`getManageDeployments` — `GET /manage/deployments`

Filters: `name`, `spaceId`, `status`, `code`, `sinceCreated`, `untilCreated`,
`sinceUpdated`, `untilUpdated`, `page`, `per_page`.

`code` searches the tag body itself — the fastest way to answer "which tag contains this
vendor snippet?".

For richer criteria use `postManageDeploymentsSearch` — `POST /manage/deployments/search`
with a JSON criteria body.

> A `404` from either means **no deployments matched**. It is an empty result, not an error.

## Read one

`getManageSpacesSpaceidDeploymentsId` — `GET /manage/spaces/{spaceId}/deployments/{id}`

Check `status`, `previousStatus`, `lastPublishedStatus` and `lastAction` before changing
anything — they tell you what state machine transition is actually legal next.

## Create

`postManageSpacesSpaceidDeployments` — `POST /manage/spaces/{spaceId}/deployments`

Key fields: `name` (≤255 chars), `code` (the tag JavaScript), `executionTime`
(`immediate`, `dom_parsed`, `dom_loaded`), `comments`, `labels`.

**No idempotency.** A retried create makes a second deployment. If a create times out,
search by `name` before retrying.

## Edit / delete

- `putManageSpacesSpaceidDeploymentsId` — `PUT /manage/spaces/{spaceId}/deployments/{id}` → `204`
- `deleteManageSpacesSpaceidDeploymentsId` — `DELETE /manage/spaces/{spaceId}/deployments/{id}` → `204`

A delete is a lifecycle transition to `deleted_*`, and is reversible with the `undelete`
action below — but only until the space is republished.

## Change state

`putManageSpacesSpaceidDeploymentsIdAction` —
`PUT /manage/spaces/{spaceId}/deployments/{id}/{action}`

`action` is one of: `enable`, `disable`, `commit`, `uncommit`, `undelete`, `archive`,
`unarchive`.

Batch form: `putManageSpacesDeploymentsBatchAction` —
`PUT /manage/spaces/deployments/batch/{action}` for commit / uncommit across many
deployments at once.

## Promote between spaces

`putManageSpacesSpaceidDeploymentsIdMergeTargetspaceid` —
`PUT /manage/spaces/{spaceId}/deployments/{id}/merge/{targetSpaceId}` → `204`

This is how a tag moves from a stage space to a prod space. Confirm the target space id
before calling — the operation reports `204` with no body, so there is nothing to inspect
afterwards except by re-reading the target.

## Errors

`{code, message, description}` on every failure. `403` means the Role assigned to your
user or API Key lacks the permission — authorization here is role-based, not scope-based.

## Do not

- Do not assume an edit is live. Commit, then publish the space.
- Do not blind-retry any POST/PUT/DELETE — there is no idempotency key.
- Do not treat search `404` as a failure.
