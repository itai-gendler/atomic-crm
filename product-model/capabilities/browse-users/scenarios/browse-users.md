---
kind: primary
routes:
  web: Web
steps:
- text: The Admin opens Users
  kind: actor
  actor: admin
  entities:
  - entity: user
    effect: reads
    facts: []
  contexts:
    web:
      place: crm-web::administration::users
- text: The Product lists every user account by first name, with Admin and Disabled badges
  kind: product
  actor: admin
  entities:
  - entity: user-account
    effect: reads
    facts:
    - First name
    - Last name
    - Email
    - Admin
  contexts:
    web:
      place: crm-web::administration::users
- text: The Admin searches by name
  kind: actor
  actor: admin
  entities:
  - entity: user-account
    effect: reads
    facts:
    - First name
    - Last name
  contexts:
    web:
      place: crm-web::administration::users
references:
- kind: code
  role: implementation
  target: src/components/atomic-crm/sales/SalesList.tsx#SalesList
---

# Browse users

## Trigger

An Admin looks after the team's accounts.

## Outcome

The Admin sees the matching users.

## Edge cases

- A User without the Admin role is denied the Users page.
