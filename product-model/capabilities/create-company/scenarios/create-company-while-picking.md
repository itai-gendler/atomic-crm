---
kind: primary
routes:
  web: Web
steps:
- text: The User types a company name that does not exist in a contact's company field and chooses to create it
  kind: actor
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
- text: The Product creates the company with that name and selects it for the contact
  kind: product
  actor: user
  entities:
  - entity: company
    effect: creates
    facts:
    - Name
    - Account manager
    - Added on
  - entity: contact
    effect: reads
    facts: []
  contexts:
    web:
      place: crm-web::workspace::new-contact
references:
- kind: code
  role: implementation
  target: src/components/atomic-crm/companies/AutocompleteCompanyInput.tsx
---

# Create a company while picking one

## Trigger

A new contact works at a company not yet in the CRM.

## Outcome

The company exists and is filled in on the contact being entered.
