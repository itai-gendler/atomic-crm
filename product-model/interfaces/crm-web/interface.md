---
type: web
actors:
- visitor
- user
- admin
entryPoints:
- web: /
references:
- kind: code
  role: implementation
  target: src/components/atomic-crm/root/CRM.tsx#CRM
- kind: code
  role: implementation
  target: src/App.tsx
---

# CRM web app

The CRM in the browser, laid out for desktop and for phones, where it can be installed to the home screen. Visitors sign in or set the CRM up; signed-in users work their contacts, companies, deals, notes and tasks; Admins also manage users and settings.
