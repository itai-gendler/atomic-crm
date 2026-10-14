---
references:
- kind: code
  role: implementation
  target: supabase/schemas/01_tables.sql
- kind: code
  role: implementation
  target: src/components/atomic-crm/notes/NoteInputs.tsx
---

# Deal note

A note written on a deal, with optional attachments.

## Information kept

- **Text** — the note text, in Markdown
- **Date** — when the note was taken
- **Attachments** — files attached to the note
- **Author** — the user who added the note
