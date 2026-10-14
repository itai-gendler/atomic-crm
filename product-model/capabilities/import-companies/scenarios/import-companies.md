---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses Import CSV on the companies page and picks a file
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: crm-web::workspace::data-import
- text: The Product creates a company per row named in it, matching its sector to a configured sector, while reporting progress
  kind: product
  actor: user
  entities:
  - entity: company
    effect: creates
    facts:
    - Name
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
    - Revenue
    - Tax identifier
    - Account manager
    - Added on
  - entity: configuration
    effect: reads
    facts:
    - Company sectors
  contexts:
    web:
      place: crm-web::workspace::data-import
references:
- kind: code
  role: implementation
  target: src/components/atomic-crm/dataImport/useCompanyImport.ts
- kind: doc
  role: intent
  target: doc/src/content/docs/users/import-data.mdx
---

# Import companies from CSV

## Trigger

A User brings companies from another tool.

## Outcome

The companies are in the CRM.

## Edge cases

- A row without a name fails and is counted among the errors.
- A sector matching no configured sector is left empty.
