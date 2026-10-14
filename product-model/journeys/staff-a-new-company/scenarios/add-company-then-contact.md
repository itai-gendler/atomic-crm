---
kind: primary
result: achieved
routes:
  web: Web
steps:
- text: The User enters the new company's details and chooses Create Company
  kind: actor
  capability: create-company
  actor: user
  entities:
  - entity: company
    effect: reads
    facts: []
  contexts:
    web:
      place: crm-web::workspace::new-company
- text: The Product creates the company
  kind: product
  capability: create-company
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
  capability: create-company
  actor: user
  entities:
  - entity: company
    effect: reads
    facts:
    - Name
  contexts:
    web:
      place: crm-web::workspace::company
- text: The User chooses Add contact on the company's contacts tab and completes the contact
  kind: actor
  capability: create-contact
  actor: user
  entities:
  - entity: company
    effect: reads
    facts: []
  - entity: contact
    effect: reads
    facts: []
  contexts:
    web:
      place: crm-web::workspace::new-contact
- text: The Product creates the contact at the company
  kind: product
  capability: create-contact
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
  contexts:
    web:
      place: crm-web::workspace::new-contact
---

# Create a company, then add a contact at it

## Trigger

The team starts working with a new organisation.

## Outcome

The company and its first contact are in the CRM.
