---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses Edit company and changes its details
  kind: actor
  actor: user
  entities:
  - entity: company
    effect: reads
    facts: []
  contexts:
    web:
      place: crm-web::workspace::company
- text: The Product saves the company and shows its page
  kind: product
  actor: user
  entities:
  - entity: company
    effect: changes
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
  contexts:
    web:
      place: crm-web::workspace::company
references:
- kind: code
  role: implementation
  target: src/components/atomic-crm/companies/CompanyEdit.tsx#CompanyEdit
---

# Edit a company

## Trigger

A company's details change.

## Outcome

The company page shows the new details.
