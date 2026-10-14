---
appliesTo:
- type: capability
  id: create-first-user
- type: capability
  id: sign-in
references:
- kind: code
  role: implementation
  target: supabase/schemas/02_functions.sql#handle_new_user
- kind: code
  role: implementation
  target: src/components/atomic-crm/login/SignupPage.tsx#SignupPage
---

# The CRM's first user is an Admin and sign-up closes after it

The first account created, by sign-up or by a first single sign-on, holds the Admin role. Once any user exists, sign-up sends visitors to the sign-in page and later accounts start without the Admin role.
