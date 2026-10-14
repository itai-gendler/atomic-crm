---
kind: primary
routes:
  web: Web
steps:
- text: The Admin changes a user's first name, last name or email and saves
  kind: actor
  actor: admin
  entities:
  - entity: user
    effect: reads
    facts: []
  contexts:
    web:
      place: crm-web::administration::user
- text: The Product saves the user account and returns to Users
  kind: product
  actor: admin
  entities:
  - entity: user-account
    effect: changes
    facts:
    - First name
    - Last name
    - Email
  - entity: user
    effect: reads
    facts: []
  contexts:
    web:
      place: crm-web::administration::user
references:
- kind: code
  role: implementation
  target: src/components/atomic-crm/sales/SalesEdit.tsx#SalesEdit
- kind: code
  role: implementation
  target: supabase/functions/users/index.ts
---

# Edit a user

## Trigger

A member's name or address changes.

## Outcome

The account carries the new details; a new email is the person's new sign-in.
