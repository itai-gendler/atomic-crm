---
appliesTo:
- type: capability-scenario
  id: add-contact-note
- type: capability
  id: change-contact-status
references:
- kind: code
  role: implementation
  target: src/components/atomic-crm/notes/NoteCreate.tsx#NoteCreate
---

# A contact note gives its contact the note's status

A new note starts with the contact's current status; whatever status it is saved with becomes the contact's status.
