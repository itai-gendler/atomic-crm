---
references:
- kind: code
  role: implementation
  target: supabase/schemas/01_tables.sql
- kind: code
  role: implementation
  target: src/components/atomic-crm/notes/NoteInputs.tsx
---

# Contact note

A note written on a contact: what happened, when, and the contact's status at that moment, with optional attachments. Notes also arrive from captured emails.

## Information kept

- **Text** — the note text, in Markdown
- **Date** — when the note was taken
- **Status** — the contact status recorded with the note
- **Attachments** — files attached to the note
- **Author** — the user who added the note
