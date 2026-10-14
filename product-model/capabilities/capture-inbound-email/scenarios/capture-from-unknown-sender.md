---
kind: validation
routes:
  email: Inbound email
steps:
- text: The Inbound email service posts an email
  kind: actor
  actor: inbound-email-service
  entities: []
  contexts:
    email:
      place: inbound-email
- text: The sender is no active user account
  kind: condition
  entities:
  - entity: user-account
    effect: reads
    facts:
    - Email
    - Secondary emails
  contexts:
    email:
      place: inbound-email
- text: The Product refuses the email without asking for a retry and records nothing
  kind: product
  entities: []
  contexts:
    email:
      place: inbound-email
references:
- kind: code
  role: implementation
  target: supabase/functions/postmark/index.ts
- kind: code
  role: implementation
  target: supabase/functions/postmark/addNoteToContact.ts
---

# Email from an unknown or disabled sender is ignored

## Trigger

Someone who is not an active user writes to the inbound address.

## Outcome

No contact, company or note is created.

## Edge cases

- A sender listed as secondary email by two users is refused the same way.
