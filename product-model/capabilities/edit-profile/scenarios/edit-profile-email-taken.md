---
kind: validation
routes:
  web: Web
steps:
- text: The User enters an email or secondary email another user already has
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: crm-web::workspace::profile
- text: The address belongs to another user account
  kind: condition
  entities:
  - entity: user-account
    effect: reads
    facts:
    - Email
    - Secondary emails
  contexts:
    web:
      place: crm-web::workspace::profile
- text: The Product reports the address as already used and saves nothing
  kind: product
  actor: user
  entities: []
  contexts:
    web:
      place: crm-web::workspace::profile
references:
- kind: code
  role: implementation
  target: supabase/functions/users/index.ts
- kind: code
  role: implementation
  target: supabase/functions/users/secondaryEmails.ts
---

# An email used by another user is refused

## Trigger

A User claims an address that belongs to a teammate.

## Outcome

The profile is unchanged.

## Edge cases

- A secondary email equal to the main email is refused.
- More than ten secondary emails, or one that is not an email address, is refused.
