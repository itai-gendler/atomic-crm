---
kind: primary
routes:
  web: Web
steps:
- text: The User writes a note on a deal's page, optionally attaching files, and chooses Add this note
  kind: actor
  actor: user
  entities:
  - entity: deal
    effect: reads
    facts:
    - Name
  contexts:
    web:
      place: crm-web::workspace::deal
- text: The Product saves the note on the deal as the User's
  kind: product
  actor: user
  entities:
  - entity: deal-note
    effect: creates
    facts:
    - Text
    - Date
    - Attachments
    - Author
  - entity: deal
    effect: reads
    facts: []
  contexts:
    web:
      place: crm-web::workspace::deal
references:
- kind: code
  role: implementation
  target: src/components/atomic-crm/deals/DealShow.tsx#DealShow
- kind: code
  role: implementation
  target: src/components/atomic-crm/notes/NoteCreate.tsx#NoteCreate
---

# Add a note to a deal

## Trigger

Something happened on a deal.

## Outcome

The note heads the deal's notes.
