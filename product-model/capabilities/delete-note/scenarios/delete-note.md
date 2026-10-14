---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses Delete note on a deal's note
  kind: actor
  actor: user
  entities:
  - entity: deal-note
    effect: reads
    facts:
    - Text
  - entity: deal
    effect: reads
    facts: []
  contexts:
    web:
      place: crm-web::workspace::deal
- text: The Product removes the note, offering Undo for a few seconds
  kind: product
  actor: user
  entities:
  - entity: deal-note
    effect: removes
  contexts:
    web:
      place: crm-web::workspace::deal
references:
- kind: code
  role: implementation
  target: src/components/atomic-crm/notes/Note.tsx#Note
---

# Delete a note

## Trigger

A note was added by mistake.

## Outcome

The note and its attachments are gone.

## Edge cases

- A contact's notes are deleted the same way on the contact's page.
