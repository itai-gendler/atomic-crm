---
kind: validation
routes:
  web: Web
steps:
- text: The Visitor opens the sign-up page
  kind: actor
  actor: visitor
  entities: []
  contexts:
    web:
      place: crm-web::sign-in::first-user-sign-up
- text: The CRM already has a user
  kind: condition
  entities:
  - entity: user-account
    effect: reads
    facts: []
  - entity: user
    effect: reads
    facts: []
  contexts:
    web:
      place: crm-web::sign-in::first-user-sign-up
- text: The Product sends the Visitor to the sign-in page
  kind: product
  actor: visitor
  entities: []
  contexts:
    web:
      place: crm-web::sign-in::sign-in-page
references:
- kind: code
  role: implementation
  target: src/components/atomic-crm/login/SignupPage.tsx#SignupPage
- kind: code
  role: implementation
  target: src/components/atomic-crm/login/StartPage.tsx#StartPage
---

# Sign-up is closed once a user exists

## Trigger

A Visitor opens the sign-up page of a CRM that is already set up.

## Outcome

No account is created; the Visitor is on the sign-in page.
