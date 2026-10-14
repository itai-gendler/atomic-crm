---
entities:
- entity: user-account
  shows:
  - First name
  - Last name
  - Email
  - Admin
  collects:
  - First name
  - Last name
  - Email
  - Admin
entryPoints:
- crm-web: /sales/:id
---

# User

One account, edited by an Admin.
