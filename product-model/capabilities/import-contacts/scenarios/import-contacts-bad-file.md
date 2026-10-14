---
kind: edge
routes:
  web: Web
steps:
- text: The User picks a file that is not a valid CSV
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: crm-web::workspace::data-import
- text: The Product reports that the file could not be imported and creates nothing
  kind: product
  actor: user
  entities: []
  contexts:
    web:
      place: crm-web::workspace::data-import
references:
- kind: code
  role: implementation
  target: src/components/atomic-crm/dataImport/DataImportDialog.tsx
---

# An unreadable file is refused

## Trigger

The chosen file is not CSV.

## Outcome

No contact is created.
