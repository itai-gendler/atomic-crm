---
kind: primary
routes:
  web: Web
steps:
- text: The User writes a note on a contact's page, optionally changing its date and status or attaching files
  kind: actor
  actor: user
  entities:
  - entity: contact
    effect: reads
    facts:
    - Status
  contexts:
    web:
      place: crm-web::workspace::contact
- text: The User chooses Add this note
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: crm-web::workspace::contact
- text: The Product saves the note as the User's
  kind: product
  actor: user
  entities:
  - entity: contact-note
    effect: creates
    facts:
    - Text
    - Date
    - Status
    - Attachments
    - Author
  contexts:
    web:
      place: crm-web::workspace::contact
- text: The Product gives the contact the note's status and marks it seen now
  kind: product
  actor: user
  entities:
  - entity: contact
    effect: changes
    facts:
    - Status
    - Last seen
  contexts:
    web:
      place: crm-web::workspace::contact
references:
- kind: code
  role: implementation
  target: src/components/atomic-crm/notes/NoteCreate.tsx#NoteCreate
- kind: code
  role: implementation
  target: supabase/schemas/02_functions.sql#handle_contact_note_created_or_updated
---

# Add a note to a contact

## Trigger

A User has talked to a contact.

## Outcome

The note heads the contact's notes and the contact carries the note's status.
