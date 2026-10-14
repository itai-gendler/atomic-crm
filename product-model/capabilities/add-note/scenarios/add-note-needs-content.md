---
kind: validation
routes:
  web: Web
steps:
- text: The User chooses Add this note with no text and no attachment
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: crm-web::workspace::contact
- text: The Product says a note or an attachment is required and saves nothing
  kind: product
  actor: user
  entities: []
  contexts:
    web:
      place: crm-web::workspace::contact
references:
- kind: code
  role: implementation
  target: src/components/atomic-crm/notes/NoteInputs.tsx#NoteInputs
---

# A note needs text or an attachment

## Trigger

A User submits an empty note.

## Outcome

No note is added.
