---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses Edit and changes their name, email or secondary emails, then saves
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: crm-web::workspace::profile
- text: The Product saves the User's own account
  kind: product
  actor: user
  entities:
  - entity: user-account
    effect: changes
    facts:
    - First name
    - Last name
    - Email
    - Secondary emails
  contexts:
    web:
      place: crm-web::workspace::profile
references:
- kind: code
  role: implementation
  target: src/components/atomic-crm/settings/ProfilePage.tsx#ProfilePage
- kind: code
  role: implementation
  target: supabase/functions/users/index.ts
---

# Edit one's profile

## Trigger

A User's details change, or they send email from more than one address.

## Outcome

The profile shows the new details; a new email is their new sign-in.
