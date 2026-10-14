---
kind: primary
routes:
  web: Web
steps:
- text: The User enters the company's name and details and chooses Create Company
  kind: actor
  actor: user
  entities:
  - entity: company
    effect: reads
    facts: []
  contexts:
    web:
      place: crm-web::workspace::new-company
- text: The Product creates the company, managed by the chosen user, with a logo from its website when none was given
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
      place: crm-web::workspace::new-company
- text: The Product opens the new company's page
  kind: product
  actor: user
  entities:
  - entity: company
    effect: reads
    facts:
    - Name
  contexts:
    web:
      place: crm-web::workspace::company
references:
- kind: code
  role: implementation
  target: src/components/atomic-crm/companies/CompanyCreate.tsx#CompanyCreate
- kind: code
  role: implementation
  target: supabase/schemas/02_functions.sql#handle_company_saved
---

# Create a company

## Trigger

The team starts working with a new organisation.

## Outcome

The company exists and the User is on its page.
