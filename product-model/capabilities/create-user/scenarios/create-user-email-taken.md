---
kind: validation
routes:
  web: Web
steps:
- text: The Admin enters an email another user already has as main or secondary email
  kind: actor
  actor: admin
  entities:
  - entity: user
    effect: reads
    facts: []
  contexts:
    web:
      place: crm-web::administration::new-user
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
      place: crm-web::administration::new-user
- text: The Product reports the email as already used and creates nothing
  kind: product
  actor: admin
  entities: []
  contexts:
    web:
      place: crm-web::administration::new-user
references:
- kind: code
  role: implementation
  target: supabase/functions/users/index.ts
- kind: code
  role: implementation
  target: src/components/atomic-crm/sales/salesErrorNotification.ts
---

# An email already in use is refused

## Trigger

An Admin creates a user with an address someone already has.

## Outcome

No account is created.
