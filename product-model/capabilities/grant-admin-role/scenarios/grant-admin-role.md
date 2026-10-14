---
kind: primary
routes:
  web: Web
steps:
- text: The Admin switches Admin on for another user and saves
  kind: actor
  actor: admin
  entities:
  - entity: user
    effect: reads
    facts: []
  contexts:
    web:
      place: crm-web::administration::user
- text: The Product gives the user account the Admin role
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

# Grant the Admin role

## Trigger

A user is to manage the team and settings.

## Outcome

The person holds the Admin role from their next page load.
