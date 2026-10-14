---
domain: contacts
availability:
- place: crm-web::workspace
references:
- kind: code
  role: implementation
  target: src/components/atomic-crm/contacts/useContactImport.tsx
---

# Import contacts

Load contacts from a CSV file in the background, matching companies and tags by name and creating the missing ones.
