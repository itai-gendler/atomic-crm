---
kind: primary
routes:
  web: Web
steps:
- text: The Admin switches Disabled on for another user and saves
  kind: actor
  actor: admin
  entities:
  - entity: user
    effect: reads
    facts: []
  contexts:
    web:
      place: crm-web::administration::user
- text: The Product disables the user account and blocks its sign-in
  kind: product
  actor: admin
  entities:
  - entity: user-account
    effect: changes
    from: Active
    to: Disabled
    facts: []
  contexts:
    web:
      place: crm-web::administration::user
references:
- kind: code
  role: implementation
  target: supabase/functions/users/index.ts
- kind: code
  role: implementation
  target: src/components/atomic-crm/sales/SalesInputs.tsx#SalesInputs
---

# Disable a user

## Trigger

A member leaves the sales team.

## Outcome

The person can no longer sign in; their contacts, deals and notes stay in the CRM.

## Edge cases

- An Admin's own Disabled switch is read-only.
