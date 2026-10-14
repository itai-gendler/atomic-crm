---
kind: primary
routes:
  web: Web
steps:
- text: The Visitor enters a first name, last name, email and password
  kind: actor
  actor: visitor
  entities: []
  contexts:
    web:
      place: crm-web::sign-in::first-user-sign-up
- text: The Product creates the first user account with the Admin role
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
    - Password
    - Admin
  - entity: admin
    effect: reads
    facts: []
  contexts:
    web:
      place: crm-web::sign-in::first-user-sign-up
- text: The Product signs the new Admin in and confirms the initial user was created
  kind: product
  actor: visitor
  entities:
  - entity: admin
    effect: reads
    facts: []
  - entity: user
    effect: reads
    facts: []
  contexts:
    web:
      place: crm-web::sign-in::first-user-sign-up
references:
- kind: code
  role: implementation
  target: src/components/atomic-crm/login/SignupPage.tsx#SignupPage
- kind: code
  role: implementation
  target: supabase/schemas/02_functions.sql#handle_new_user
---

# Create the first user and enter the CRM

## Trigger

A Visitor opens the CRM before anyone has set it up.

## Outcome

The first user account exists with the Admin role and its holder is signed in, on the contacts page.
