---
kind: primary
routes:
  web: Web
steps:
- text: The Visitor enters their email on the forgot-password page
  kind: actor
  actor: visitor
  entities: []
  contexts:
    web:
      place: crm-web::sign-in::forgot-password
- text: The Product emails a password reset link to that address and returns to sign-in with a notice
  kind: product
  actor: visitor
  entities:
  - entity: user-account
    effect: reads
    facts:
    - Email
  contexts:
    web:
      place: crm-web::sign-in::forgot-password
- text: The Visitor follows the link and enters a new password twice
  kind: actor
  actor: visitor
  entities: []
  contexts:
    web:
      place: crm-web::sign-in::set-password
- text: The Product saves the new password and signs the person in
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
  target: src/components/supabase/forgot-password-page.tsx
- kind: code
  role: implementation
  target: src/components/supabase/set-password-page.tsx#SetPasswordPage
---

# Reset a forgotten password

## Trigger

A Visitor has forgotten their password.

## Outcome

The person signs in with the new password.

## Edge cases

- The notice reads the same whether or not the address belongs to a user, so it never tells who is registered.
