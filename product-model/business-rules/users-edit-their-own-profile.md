---
appliesTo:
- type: entity
  id: user-account
  effect: changes
  facts:
  - First name
  - Last name
  - Email
  - Secondary emails
  - Avatar
permits:
- actors:
  - admin
- related:
  - verb: holds
    entity: user
references:
- kind: code
  role: implementation
  target: supabase/functions/users/index.ts
---

# A User changes only their own profile; an Admin changes anyone's

Name, email, secondary emails and avatar of an account are changed by its holder or by an Admin.
