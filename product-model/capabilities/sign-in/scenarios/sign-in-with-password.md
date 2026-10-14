---
kind: primary
routes:
  web: Web
steps:
- text: The Visitor enters their email and password
  kind: actor
  actor: visitor
  entities: []
  contexts:
    web:
      place: crm-web::sign-in::sign-in-page
- text: The Product checks them against an active user account and signs the person in
  kind: product
  actor: visitor
  entities:
  - entity: user-account
    effect: reads
    facts:
    - Email
    - Password
  contexts:
    web:
      place: crm-web::sign-in::sign-in-page
references:
- kind: code
  role: implementation
  target: src/components/atomic-crm/login/LoginPage.tsx#LoginPage
- kind: code
  role: implementation
  target: src/components/atomic-crm/providers/supabase/authProvider.ts#getAuthProvider
---

# Sign in with email and password

## Trigger

A Visitor wants to use the CRM.

## Outcome

The person is signed in and lands on the dashboard, or on the page they were trying to reach.
