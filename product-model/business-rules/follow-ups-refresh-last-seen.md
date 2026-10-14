---
appliesTo:
- type: capability
  id: add-note
- type: capability
  id: add-task
- type: capability
  id: capture-inbound-email
references:
- kind: code
  role: implementation
  target: src/components/atomic-crm/notes/NoteCreate.tsx#NoteCreate
- kind: code
  role: implementation
  target: src/components/atomic-crm/tasks/AddTask.tsx#AddTask
- kind: code
  role: implementation
  target: supabase/functions/postmark/addNoteToContact.ts
---

# Adding a note or a task marks the contact as seen now

A contact's last activity moves to the moment a note or task is added to it, by hand or from a captured email.
