---
kind: validation
routes:
  web: Web
steps:
- text: The Admin enters an email another user already has
  kind: actor
  actor: admin
  entities:
  - entity: user
    effect: reads
    facts: []
  contexts:
    web:
      place: crm-web::administration::user
- text: The email belongs to another user account
  kind: condition
  entities:
  - entity: user-account
    effect: reads
    facts:
    - Email
    - Secondary emails
  contexts:
    web:
      place: crm-web::administration::user
- text: The Product reports the email as already used and saves nothing
  kind: product
  actor: admin
  entities: []
  contexts:
    web:
      place: crm-web::administration::user
references:
- kind: code
  role: implementation
  target: supabase/functions/users/index.ts
---

# An email already in use is refused

## Trigger

An Admin gives a user an address someone else has.

## Outcome

The account is unchanged.
