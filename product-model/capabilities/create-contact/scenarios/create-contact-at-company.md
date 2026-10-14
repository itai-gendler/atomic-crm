---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses Add contact on a company's contacts tab
  kind: actor
  actor: user
  entities:
  - entity: company
    effect: reads
    facts:
    - Name
  - entity: contact
    effect: reads
    facts: []
  contexts:
    web:
      place: crm-web::workspace::company
- text: The Product opens a new contact form with that company filled in
  kind: product
  actor: user
  entities:
  - entity: company
    effect: reads
    facts:
    - Name
  - entity: contact
    effect: reads
    facts: []
  contexts:
    web:
      place: crm-web::workspace::new-contact
- text: The User completes the contact's details
  kind: actor
  actor: user
  entities:
  - entity: contact
    effect: reads
    facts: []
  contexts:
    web:
      place: crm-web::workspace::new-contact
- text: The Product creates the contact at that company
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
  contexts:
    web:
      place: crm-web::workspace::new-contact
references:
- kind: code
  role: implementation
  target: src/components/atomic-crm/companies/CompanyShow.tsx#CompanyShow
---

# Add a contact from a company

## Trigger

A User adds someone working at a company already in the CRM.

## Outcome

The contact exists and is listed on the company.
