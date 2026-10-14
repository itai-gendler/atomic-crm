---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses Import CSV on the deals page and picks a file
  kind: actor
  actor: user
  entities:
  - entity: deal
    effect: reads
    facts: []
  contexts:
    web:
      place: crm-web::workspace::data-import
- text: The Product creates the companies the rows name that do not exist yet
  kind: product
  actor: user
  entities:
  - entity: company
    effect: creates
    facts:
    - Name
    - Account manager
    - Added on
  contexts:
    web:
      place: crm-web::workspace::data-import
- text: The Product creates an active deal per row with its company, matching its category and stage, and placing it below the deals already in its stage
  kind: product
  actor: user
  entities:
  - entity: deal
    effect: creates
    to: Active
    facts:
    - Name
    - Description
    - Company
    - Contacts
    - Category
    - Budget
    - Expected closing date
    - Stage
    - Position
    - Account manager
    - Created at
  - entity: configuration
    effect: reads
    facts:
    - Deal stages
    - Deal categories
  - entity: company
    effect: reads
    facts: []
  contexts:
    web:
      place: crm-web::workspace::data-import
references:
- kind: code
  role: implementation
  target: src/components/atomic-crm/dataImport/useDealImport.ts
- kind: doc
  role: intent
  target: doc/src/content/docs/users/import-data.mdx
---

# Import deals from CSV

## Trigger

A User brings a pipeline from another tool.

## Outcome

The deals are on the board in their stages.

## Edge cases

- A row without a name fails and is counted among the errors.
- An empty or unknown stage falls back to the first stage of the pipeline.
