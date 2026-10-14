---
kind: validation
routes:
  web: Web
steps:
- text: The Visitor enters an email and password
  kind: actor
  actor: visitor
  entities: []
  contexts:
    web:
      place: crm-web::sign-in::sign-in-page
- text: No active user account matches them
  kind: condition
  entities:
  - entity: user-account
    effect: reads
    facts:
    - Email
    - Password
  contexts:
    web:
      place: crm-web::sign-in::sign-in-page
- text: The Product shows a sign-in error and keeps the Visitor on the sign-in page
  kind: product
  actor: visitor
  entities: []
  contexts:
    web:
      place: crm-web::sign-in::sign-in-page
references:
- kind: code
  role: implementation
  target: src/components/atomic-crm/login/LoginPage.tsx#LoginPage
---

# Wrong credentials are refused

## Trigger

A Visitor mistypes their password, or their account is disabled.

## Outcome

The Visitor stays signed out.

## Edge cases

- A disabled user account is refused the same way as a wrong password.
