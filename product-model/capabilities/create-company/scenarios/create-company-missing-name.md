---
kind: validation
routes:
  web: Web
steps:
- text: The User chooses Create Company without a name
  kind: actor
  actor: user
  entities:
  - entity: company
    effect: reads
    facts: []
  contexts:
    web:
      place: crm-web::workspace::new-company
- text: The Product marks the name as required and creates nothing
  kind: product
  actor: user
  entities: []
  contexts:
    web:
      place: crm-web::workspace::new-company
references:
- kind: code
  role: implementation
  target: src/components/atomic-crm/companies/CompanyInputs.tsx
---

# A company needs a name

## Trigger

A User forgets the company name.

## Outcome

No company is created.
