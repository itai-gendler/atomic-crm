---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses Import from JSON and uploads a file
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: crm-web::workspace::json-import
- text: The Product creates the file's companies
  kind: product
  actor: user
  entities:
  - entity: company
    effect: creates
    facts:
    - Name
    - Logo
    - Sector
    - Size
    - Website
    - LinkedIn URL
    - Phone number
    - Address
    - City
    - Zip code
    - State
    - Country
    - Description
    - Context links
    - Revenue
    - Tax identifier
    - Account manager
    - Added on
  contexts:
    web:
      place: crm-web::workspace::json-import
- text: The Product creates the file's contacts at their companies, creating the tags they name
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
  - entity: tag
    effect: creates
    facts:
    - Name
    - Color
  contexts:
    web:
      place: crm-web::workspace::json-import
- text: The Product creates the file's notes and tasks on their contacts
  kind: product
  actor: user
  entities:
  - entity: contact-note
    effect: creates
    facts:
    - Text
    - Date
    - Attachments
    - Author
  - entity: task
    effect: creates
    to: Pending
    facts:
    - Description
    - Type
    - Due date
    - Contact
    - Owner
  - entity: contact
    effect: reads
    facts: []
  contexts:
    web:
      place: crm-web::workspace::json-import
- text: The Product shows how many records of each kind were imported and lists those that failed
  kind: product
  actor: user
  entities: []
  contexts:
    web:
      place: crm-web::workspace::json-import
references:
- kind: code
  role: implementation
  target: src/components/atomic-crm/misc/ImportPage.tsx
- kind: code
  role: implementation
  target: src/components/atomic-crm/misc/useImportFromJson.ts
- kind: doc
  role: intent
  target: doc/src/content/docs/users/import-data.mdx
---

# Import data from a JSON file

## Trigger

A team moves its data from another CRM.

## Outcome

The data is in the CRM, linked as in the file.

## Edge cases

- A sample file shows the expected format.
- Users of the file already in the CRM, matched by email, are reused.
