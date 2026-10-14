---
domain: contacts
availability:
- place: crm-web::workspace
references:
- kind: code
  role: implementation
  target: src/components/atomic-crm/contacts/BulkTagButton.tsx#BulkTagButton
---

# Remove tag from contact

Take a tag off a contact, or off every selected contact when they all have it.
