---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses Log out
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: crm-web::workspace
- text: The Product ends the session and forgets the data cached on this device
  kind: product
  actor: user
  entities: []
  contexts:
    web:
      place: crm-web::workspace
references:
- kind: code
  role: implementation
  target: src/components/atomic-crm/providers/supabase/authProvider.ts#getAuthProvider
- kind: code
  role: implementation
  target: src/components/atomic-crm/root/CRM.tsx#CRM
---

# Sign out

## Trigger

A signed-in User is done with the CRM.

## Outcome

The person is signed out and sees the sign-in page.
