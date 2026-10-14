---
kind: primary
routes:
  web: Web
steps:
- text: The Visitor follows the invitation link and enters a password twice
  kind: actor
  actor: visitor
  entities: []
  contexts:
    web:
      place: crm-web::sign-in::set-password
- text: The Product saves the password of the invited user account and signs the person in
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
  target: src/components/supabase/set-password-page.tsx#SetPasswordPage
- kind: code
  role: implementation
  target: supabase/templates/invite.html
---

# Set a password from the invitation

## Trigger

A person receives the invitation sent when an Admin created their account.

## Outcome

The person is signed in to the CRM with their new password.
