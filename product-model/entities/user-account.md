---
domain: users
references:
- kind: code
  role: implementation
  target: supabase/schemas/01_tables.sql
- kind: code
  role: implementation
  target: supabase/functions/users/index.ts
- kind: code
  role: implementation
  target: supabase/schemas/02_functions.sql#handle_new_user
---

# User account

The account of one member of the sales team: who they are, how they sign in and whether they hold the Admin role. Users are created, edited and disabled, never deleted.

## Information kept

- **First name** — the person's first name
- **Last name** — the person's last name
- **Email** — the address the person signs in with and receives password and invitation emails at; unique among users
- **Secondary emails** — up to ten further addresses the person sends email from, used to recognise them as the sender of captured emails
- **Avatar** — the person's picture
- **Admin** — whether the person holds the Admin role
- **Password** — the secret the person signs in with when password sign-in is enabled

## States

### Active

The person can sign in and is offered as an account manager.

### Disabled

The person can no longer sign in, is no longer offered as an account manager, and emails they send are not captured.
