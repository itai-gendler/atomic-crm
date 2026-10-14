---
kind: primary
routes:
  web: Web
steps:
- text: The Admin switches Disabled off for a disabled user and saves
  kind: actor
  actor: admin
  entities:
  - entity: user
    effect: reads
    facts: []
  contexts:
    web:
      place: crm-web::administration::user
- text: The Product enables the user account and lifts its sign-in block
  kind: product
  actor: admin
  entities:
  - entity: user-account
    effect: changes
    from: Disabled
    to: Active
    facts: []
  contexts:
    web:
      place: crm-web::administration::user
references:
- kind: code
  role: implementation
  target: supabase/functions/users/index.ts
---

# Enable a user

## Trigger

A disabled member comes back.

## Outcome

The person can sign in again.
