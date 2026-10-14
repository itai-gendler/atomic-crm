---
kind: primary
routes:
  web: Web
steps:
- text: The Admin uploads a JSON file listing users not yet in the CRM
  kind: actor
  actor: admin
  entities:
  - entity: user
    effect: reads
    facts: []
  contexts:
    web:
      place: crm-web::workspace::json-import
- text: The Product creates a user account without the Admin role for each new user and invites them
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
  - entity: user
    effect: reads
    facts: []
  contexts:
    web:
      place: crm-web::workspace::json-import
references:
- kind: code
  role: implementation
  target: src/components/atomic-crm/misc/useImportFromJson.ts
- kind: code
  role: implementation
  target: supabase/functions/users/index.ts
---

# Import new users from a JSON file

## Trigger

The file to migrate lists the team's sales people.

## Outcome

Each new person has a user account and an invitation.
