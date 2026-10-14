---
kind: primary
routes:
  email: Inbound email
steps:
- text: The Inbound email service posts an email a user forwarded to the inbound address only
  kind: actor
  actor: inbound-email-service
  entities:
  - entity: user
    effect: reads
    facts: []
  contexts:
    email:
      place: inbound-email
- text: The Product recognises the sender as an active user account and takes the original correspondent from the forwarded message
  kind: product
  entities:
  - entity: user-account
    effect: reads
    facts:
    - Email
    - Secondary emails
  contexts:
    email:
      place: inbound-email
- text: The Product adds the forwarded subject and body as a note on that correspondent's contact, written by the user
  kind: product
  entities:
  - entity: contact
    effect: reads
    facts:
    - Email addresses
  - entity: contact-note
    effect: creates
    facts:
    - Text
    - Date
    - Attachments
    - Author
  - entity: user
    effect: reads
    facts: []
  contexts:
    email:
      place: inbound-email
references:
- kind: code
  role: implementation
  target: supabase/functions/postmark/index.ts
- kind: code
  role: implementation
  target: supabase/functions/postmark/forwardedParser.ts
---

# Capture a forwarded email

## Trigger

A user forwards a reply they received to the inbound address.

## Outcome

The forwarded email is a note on the correspondent's contact.

## Edge cases

- A forwarded email naming no address other than users' and the inbound address is refused without retry.
