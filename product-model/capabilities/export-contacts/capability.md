---
domain: contacts
availability:
- place: crm-web::workspace
references:
- kind: code
  role: implementation
  target: src/components/atomic-crm/contacts/ContactList.tsx#ContactList
---

# Export contacts

Download the listed or selected contacts as a CSV file, with company, account manager and tags by name.
