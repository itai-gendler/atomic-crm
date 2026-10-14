---
appliesTo:
- type: capability
  id: create-user
- type: capability
  id: edit-user
- type: capability
  id: edit-profile
references:
- kind: code
  role: implementation
  target: supabase/functions/users/index.ts
---

# Each email address belongs to at most one user

A main or secondary email already used by another user is refused, and a secondary email cannot repeat the main one. Sender recognition for captured emails relies on it.
