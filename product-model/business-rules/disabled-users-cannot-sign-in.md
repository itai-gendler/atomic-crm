---
appliesTo:
- type: capability
  id: sign-in
- type: capability
  id: disable-user
- type: capability
  id: create-contact
references:
- kind: code
  role: implementation
  target: supabase/functions/users/index.ts
- kind: code
  role: implementation
  target: src/components/atomic-crm/contacts/ContactInputs.tsx#ContactInputs
---

# A disabled user cannot sign in

Disabling an account blocks its sign-in until an Admin enables it again; disabled users are also no longer offered as account managers.
