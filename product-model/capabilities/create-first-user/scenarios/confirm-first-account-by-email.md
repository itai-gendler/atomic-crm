---
kind: edge
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
- text: The email address must be confirmed before signing in
  kind: condition
  entities:
  - entity: user-account
    effect: reads
    facts:
    - Email
  contexts:
    web:
      place: crm-web::sign-in::first-user-sign-up
- text: The Product asks the Visitor to follow the link sent by email to confirm the account
  kind: product
  actor: visitor
  entities: []
  contexts:
    web:
      place: crm-web::sign-in::first-user-sign-up
references:
- kind: code
  role: implementation
  target: src/components/atomic-crm/login/ConfirmationRequired.tsx#ConfirmationRequired
- kind: code
  role: implementation
  target: src/components/atomic-crm/login/SignupPage.tsx#SignupPage
---

# Confirm the first account by email

## Trigger

The CRM is connected to a backend that requires email confirmation.

## Outcome

The account exists; the Visitor signs in after confirming it through the emailed link.
