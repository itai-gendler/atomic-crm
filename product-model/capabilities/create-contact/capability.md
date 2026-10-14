---
domain: contacts
availability:
- place: crm-web::workspace
references:
- kind: code
  role: implementation
  target: src/components/atomic-crm/contacts/ContactCreate.tsx#ContactCreate
---

# Create contact

Add a person the team is in touch with. The creator is the default account manager; a contact's picture is fetched from its email address when none is given.
