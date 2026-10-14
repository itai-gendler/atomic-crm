---
appliesTo:
- type: entity
  id: user-account
  effect: creates
  contexts:
  - place: crm-web::administration
  - place: crm-web::workspace
permits:
- actors:
  - admin
references:
- kind: code
  role: implementation
  target: supabase/functions/users/index.ts
- kind: code
  role: implementation
  target: src/components/atomic-crm/providers/commons/canAccess.ts#canAccess
---

# Only an Admin creates a user

Users are added by an Admin, on the Users page or by importing a JSON file that lists new users. The first account, created before anyone else exists, is the only one created by sign-up.
