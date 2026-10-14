---
kind: primary
routes:
  web: Web
steps:
- text: The Admin switches Admin off for another user and saves
  kind: actor
  actor: admin
  entities:
  - entity: user
    effect: reads
    facts: []
  contexts:
    web:
      place: crm-web::administration::user
- text: The Product removes the Admin role from the user account
  kind: product
  actor: admin
  entities:
  - entity: user-account
    effect: changes
    facts:
    - Admin
  contexts:
    web:
      place: crm-web::administration::user
references:
- kind: code
  role: implementation
  target: src/components/atomic-crm/sales/SalesInputs.tsx#SalesInputs
- kind: code
  role: implementation
  target: supabase/functions/users/index.ts
---

# Revoke the Admin role

## Trigger

A user no longer needs to manage the team and settings.

## Outcome

The person is a User without the Admin role.

## Edge cases

- An Admin's own Admin switch is read-only.
