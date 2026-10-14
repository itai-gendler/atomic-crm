---
appliesTo:
- type: capability
  id: delete-note
- type: capability
  id: delete-task
- type: capability
  id: delete-contact
- type: capability
  id: delete-company
- type: capability
  id: delete-deal
- type: capability
  id: delete-tag
references:
- kind: code
  role: implementation
  target: src/components/admin/delete-button.tsx#DeleteButton
- kind: code
  role: implementation
  target: src/components/atomic-crm/notes/Note.tsx#Note
---

# A deletion can be undone for a few seconds

Deleting a note, task, contact, company, deal or tag shows an Undo notice; the deletion happens when the notice closes. Merging contacts cannot be undone.
