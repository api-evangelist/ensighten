---
name: ensighten-provision-users-scim
description: >-
  Provision, update and deprovision Ensighten Manage users and groups — either
  through the native Users/Roles endpoints or through the standards-based SCIM
  2.0 surface. Use when asked to add/remove a user, change someone's roles, or
  wire Ensighten to an identity provider.
api: Ensighten Manage API
base_url: https://manage-api.ensighten.com
operations:
  - postManageUsersSearch
  - getManageUsersId
  - postManageUsers
  - putManageUsersId
  - deleteManageUsersId
  - postManageRolesSearch
  - postScim2Users
  - getScim2Users
  - getScim2UsersId
  - putScim2UsersId
  - patchScim2UsersId
  - deleteScim2UsersId
  - getScim2Groups
  - getScim2GroupsId
  - putScim2GroupsId
  - patchScim2GroupsId
generated: '2026-08-13'
method: generated
source: openapi/ensighten-manage-api-openapi.yml
---

# Provision Ensighten Manage users

Ensighten exposes **two** user surfaces. Pick deliberately.

| Surface | Use when |
|---|---|
| `/manage/users`, `/manage/roles` | Ad-hoc administration, or when you need to set Manage-specific fields like `multiFactorAuth` and `sendNotification`. |
| `/scim2/Users`, `/scim2/Groups` | An identity provider is the source of truth. This is a real SCIM 2.0 (RFC 7643/7644) implementation — use it for IdP-driven lifecycle. |

Authorization is **role-based**. There are no OAuth scopes; your API Key's assigned Roles
decide what you can do. A `403` means the Role is insufficient.

## Native surface

### Find roles first

`postManageRolesSearch` — `POST /manage/roles/search`

You need role **ids** to create a user. Fetch them before creating anyone.

### Find a user

`postManageUsersSearch` — `POST /manage/users/search`
`getManageUsersId` — `GET /manage/users/{id}`

> `404` from the search means **no users matched** — an empty result, not an error.

### Create

`postManageUsers` — `POST /manage/users` → `201`

Fields: `username` (unique, ≤255 chars, may not contain `<`, `>`, `:`, `~`, `+` or spaces),
`firstName`, `lastName` (alphanumerics, spaces and hyphens only), `email`, `roleIds`
(array of integer role ids), `multiFactorAuth` (`enable` / `disable`, defaults `disable`),
`sendNotification` (boolean, defaults `false`), `isActive` (defaults `true`).

Set `sendNotification: true` only when the person should receive a welcome email now.

### Update / remove

`putManageUsersId` — `PUT /manage/users/{id}` → `204`
`deleteManageUsersId` — `DELETE /manage/users/{id}` → `204`

To deactivate rather than delete, `PUT` with `isActive: false`. Prefer deactivation unless
removal was explicitly requested — a delete cannot be undone through this API.

## SCIM 2.0 surface

Standard RFC 7644 verbs, unversioned under `/scim2`:

- `postScim2Users` — `POST /scim2/Users` → `201`
- `getScim2Users` — `GET /scim2/Users` (search)
- `getScim2UsersId` — `GET /scim2/Users/{id}`
- `putScim2UsersId` — `PUT /scim2/Users/{id}` (full replace)
- `patchScim2UsersId` — `PATCH /scim2/Users/{id}` (partial, SCIM PATCH ops)
- `deleteScim2UsersId` — `DELETE /scim2/Users/{id}` → `204`
- `getScim2Groups` / `getScim2GroupsId` — group read
- `putScim2GroupsId` — replace group membership
- `patchScim2GroupsId` — incrementally add/remove members

Use `PATCH` for membership changes. `PUT` on a group **replaces** the whole membership
list, so a `PUT` built from a partial view will silently remove everyone you omitted.

## Errors

`{code, message, description}` on every failure. Common cases: `400` invalid field format
(check the username and name character restrictions above), `403` insufficient Role,
`404` user does not exist.

## Do not

- Do not delete when deactivation was meant.
- Do not `PUT` a SCIM group unless you intend to replace its entire membership.
- Do not retry a create after a timeout without searching first — there is no idempotency key.
