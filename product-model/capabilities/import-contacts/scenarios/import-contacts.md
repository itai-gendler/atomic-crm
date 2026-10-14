---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses Import CSV on the contacts page and picks a file
  kind: actor
  actor: user
  entities:
  - entity: contact
    effect: reads
    facts: []
  contexts:
    web:
      place: crm-web::workspace::data-import
- text: The Product closes the dialog and creates the companies and tags the rows name that do not exist yet
  kind: product
  actor: user
  entities:
  - entity: company
    effect: creates
    facts:
    - Name
    - Account manager
    - Added on
  - entity: tag
    effect: creates
    facts:
    - Name
    - Color
  contexts:
    web:
      place: crm-web::workspace::data-import
- text: The Product creates a contact per row at its company with its tags, while reporting progress
  kind: product
  actor: user
  entities:
  - entity: contact
    effect: creates
    facts:
    - First name
    - Last name
    - Gender
    - Title
    - Company
    - Email addresses
    - Phone numbers
    - LinkedIn URL
    - Background
    - Has newsletter
    - Account manager
    - Avatar
    - First seen
    - Last seen
    - Tags
  - entity: company
    effect: reads
    facts: []
  - entity: tag
    effect: reads
    facts: []
  contexts:
    web:
      place: crm-web::workspace::data-import
- text: The Product reports how many records were imported and how many failed
  kind: product
  actor: user
  entities: []
  contexts:
    web:
      place: crm-web::workspace::data-import
references:
- kind: code
  role: implementation
  target: src/components/atomic-crm/contacts/useContactImport.tsx
- kind: code
  role: implementation
  target: src/components/atomic-crm/dataImport/DataImportDialog.tsx
- kind: doc
  role: intent
  target: doc/src/content/docs/users/import-data.mdx
---

# Import contacts from CSV

## Trigger

A User brings contacts from another tool.

## Outcome

The contacts are in the CRM, linked to their companies and tags.

## Edge cases

- Columns the CRM does not know are ignored and missing ones are left empty.
- A sample file shows the expected columns.
- The User can stop the import from the progress notice; records already imported stay.
