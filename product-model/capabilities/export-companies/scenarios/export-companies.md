---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses Export on the company list
  kind: actor
  actor: user
  entities:
  - entity: company
    effect: reads
    facts: []
  contexts:
    web:
      place: crm-web::workspace::companies
- text: The Product downloads a CSV of the listed companies
  kind: product
  actor: user
  entities:
  - entity: company
    effect: reads
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
    - Number of contacts
    - Number of deals
  contexts:
    web:
      place: crm-web::workspace::companies
references:
- kind: code
  role: implementation
  target: src/components/atomic-crm/companies/CompanyList.tsx#CompanyList
---

# Export companies to CSV

## Trigger

A User needs the companies outside the CRM.

## Outcome

The User has a companies CSV file.
