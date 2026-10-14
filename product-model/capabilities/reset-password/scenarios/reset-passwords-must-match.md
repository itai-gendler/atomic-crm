---
kind: validation
routes:
  web: Web
steps:
- text: The Visitor enters two different passwords on the set-password page
  kind: actor
  actor: visitor
  entities: []
  contexts:
    web:
      place: crm-web::sign-in::set-password
- text: The Product reports that the passwords do not match and saves nothing
  kind: product
  actor: visitor
  entities: []
  contexts:
    web:
      place: crm-web::sign-in::set-password
references:
- kind: code
  role: implementation
  target: src/components/supabase/set-password-page.tsx#SetPasswordPage
---

# Mismatched passwords are refused

## Trigger

A Visitor mistypes the confirmation of a new password.

## Outcome

The password is unchanged.
