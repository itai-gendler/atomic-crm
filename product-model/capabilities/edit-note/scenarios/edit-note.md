---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses Edit note on a contact's note, changes it and chooses Update note
  kind: actor
  actor: user
  entities:
  - entity: contact-note
    effect: reads
    facts:
    - Text
    - Date
    - Status
    - Attachments
  - entity: contact
    effect: reads
    facts: []
  contexts:
    web:
      place: crm-web::workspace::contact
- text: The Product saves the note
  kind: product
  actor: user
  entities:
  - entity: contact-note
    effect: changes
    facts:
    - Text
    - Date
    - Status
    - Attachments
  contexts:
    web:
      place: crm-web::workspace::contact
references:
- kind: code
  role: implementation
  target: src/components/atomic-crm/notes/Note.tsx#Note
---

# Edit a note

## Trigger

A note needs correcting.

## Outcome

The note shows the change; attachments removed from it are deleted.

## Edge cases

- A deal's notes are edited the same way on the deal's page.
