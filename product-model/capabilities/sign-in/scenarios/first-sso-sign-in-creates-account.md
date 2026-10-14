---
kind: primary
routes:
  web: Web
steps:
- text: The Visitor signs in with Google Workplace for the first time
  kind: actor
  actor: visitor
  entities: []
  contexts:
    web:
      place: crm-web::sign-in::sign-in-page
- text: The Product creates a user account from the name and email the identity provider returns
  kind: product
  actor: visitor
  entities:
  - entity: user-account
    effect: creates
    to: Active
    facts:
    - First name
    - Last name
    - Email
    - Admin
  contexts:
    web:
      place: crm-web::sign-in::sign-in-page
- text: The Product signs the person in
  kind: product
  actor: visitor
  entities: []
  contexts:
    web:
      place: crm-web::sign-in::sign-in-page
references:
- kind: code
  role: implementation
  target: supabase/schemas/02_functions.sql#handle_new_user
- kind: code
  role: implementation
  target: supabase/migrations/20260128165057_sso_handling.sql
---

# A first single sign-on creates the user account

## Trigger

A member of the configured Workspace domain signs in with no user account yet.

## Outcome

A user account exists for them, with the Admin role only if it is the CRM's first, and they are signed in.
