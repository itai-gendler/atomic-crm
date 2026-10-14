---
kind: primary
routes:
  web: Web
steps:
- text: The Admin enters a first name, last name and email, and whether the person is Admin
  kind: actor
  actor: admin
  entities: []
  contexts:
    web:
      place: crm-web::administration::new-user
- text: The Product creates the user account
  kind: product
  actor: admin
  entities:
  - entity: user-account
    effect: creates
    to: Active
    facts:
    - First name
    - Last name
    - Email
    - Admin
  contexts:
    web:
      place: crm-web::administration::new-user
- text: The Product emails the person an invitation to set their password and returns to Users
  kind: product
  actor: admin
  entities:
  - entity: user-account
    effect: reads
    facts:
    - Email
  - entity: user
    effect: reads
    facts: []
  contexts:
    web:
      place: crm-web::administration::new-user
references:
- kind: code
  role: implementation
  target: src/components/atomic-crm/sales/SalesCreate.tsx#SalesCreate
- kind: code
  role: implementation
  target: supabase/functions/users/index.ts
---

# Create a user

## Trigger

A new member joins the sales team.

## Outcome

The account exists and its holder has an invitation to set a password.

## Edge cases

- Creating the account already disabled keeps its holder from signing in until an Admin enables it.
