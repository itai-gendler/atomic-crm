---
kind: primary
routes:
  web: Web
steps:
- text: The User opens Companies
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: crm-web::workspace::companies
- text: The Product lists companies with their logo, sector, number of contacts and number of deals
  kind: product
  actor: user
  entities:
  - entity: company
    effect: reads
    facts:
    - Name
    - Logo
    - Sector
    - Size
    - Number of contacts
    - Number of deals
  - entity: contact
    effect: reads
    facts: []
  - entity: deal
    effect: reads
    facts: []
  contexts:
    web:
      place: crm-web::workspace::companies
- text: The User searches by name and picks a size, a sector or Me
  kind: actor
  actor: user
  entities:
  - entity: company
    effect: reads
    facts:
    - Size
    - Sector
    - Account manager
  contexts:
    web:
      place: crm-web::workspace::companies
- text: The Product lists only the matching companies
  kind: product
  actor: user
  entities:
  - entity: company
    effect: reads
    facts:
    - Name
  contexts:
    web:
      place: crm-web::workspace::companies
references:
- kind: code
  role: implementation
  target: src/components/atomic-crm/companies/CompanyList.tsx#CompanyList
- kind: code
  role: implementation
  target: src/components/atomic-crm/companies/CompanyListFilter.tsx#CompanyListFilter
---

# Browse and filter companies

## Trigger

A User looks for an organisation.

## Outcome

The User sees the matching companies.
