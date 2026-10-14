---
kind: primary
routes:
  web: Web
steps:
- text: The Visitor chooses to sign in with Google Workplace
  kind: actor
  actor: visitor
  entities: []
  contexts:
    web:
      place: crm-web::sign-in::sign-in-page
- text: The Visitor signs in at their identity provider
  kind: actor
  actor: visitor
  entities: []
  contexts:
    web:
      place: crm-web::sign-in::sign-in-page
- text: The Product signs in the person whose user account matches the returned email
  kind: product
  actor: visitor
  entities:
  - entity: user-account
    effect: reads
    facts:
    - Email
  contexts:
    web:
      place: crm-web::sign-in::sign-in-page
references:
- kind: code
  role: implementation
  target: src/components/atomic-crm/login/SSOAuthButton.tsx#SSOAuthButton
- kind: code
  role: implementation
  target: src/components/atomic-crm/providers/supabase/authProvider.ts#getAuthProvider
- kind: doc
  role: intent
  target: doc/src/content/docs/developers/sso.mdx
---

# Sign in with Google Workspace

## Trigger

A Visitor of a CRM configured with a Google Workspace domain signs in.

## Outcome

The person is signed in without a CRM password.
