---
availability:
- place: crm-web::sign-in
references:
- kind: code
  role: implementation
  target: src/components/atomic-crm/login/SignupPage.tsx#SignupPage
- kind: doc
  role: intent
  target: doc/src/content/docs/users/user-management.mdx
---

# Create the first user

Set the CRM up by creating its first account. Only offered while the CRM has no user yet; the first account holds the Admin role, and every later user is created by an Admin.
