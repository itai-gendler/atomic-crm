---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses Change password on their profile
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: crm-web::workspace::profile
- text: The Product emails a password reset link to the User's address
  kind: product
  actor: user
  entities:
  - entity: user-account
    effect: reads
    facts:
    - Email
  contexts:
    web:
      place: crm-web::workspace::profile
- text: The Visitor follows the link and enters a new password twice
  kind: actor
  actor: visitor
  entities: []
  contexts:
    web:
      place: crm-web::sign-in::set-password
- text: The Product saves the new password
  kind: product
  actor: visitor
  entities:
  - entity: user-account
    effect: changes
    facts:
    - Password
  contexts:
    web:
      place: crm-web::sign-in::set-password
references:
- kind: code
  role: implementation
  target: supabase/functions/update_password/index.ts
- kind: code
  role: implementation
  target: src/components/atomic-crm/settings/ProfilePage.tsx#ProfilePage
---

# Change password from the profile

## Trigger

A signed-in User wants a new password.

## Outcome

The password is changed; the person signs in with it from then on.
