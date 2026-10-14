---
domain: contacts
relations:
- entity: contact-note
  verb: has
  cardinality: one-to-many
- entity: task
  verb: has
  cardinality: one-to-many
- entity: tag
  verb: is-tagged-with
  cardinality: many-to-many
references:
- kind: code
  role: implementation
  target: supabase/schemas/01_tables.sql
- kind: code
  role: implementation
  target: supabase/schemas/03_views.sql
- kind: code
  role: implementation
  target: src/components/atomic-crm/contacts/ContactInputs.tsx
- kind: code
  role: implementation
  target: src/components/atomic-crm/types.ts
---

# Contact

A person the team is in touch with, usually working at a company, with their notes, tasks and tags.

## Information kept

- **First name** — the contact's first name
- **Last name** — the contact's last name
- **Gender** — how to refer to the contact: He/Him, She/Her or They/Them
- **Title** — the contact's job title
- **Company** — the company the contact works at
- **Email addresses** — the contact's email addresses, each Work, Home or Other
- **Phone numbers** — the contact's phone numbers, each Work, Home or Other
- **LinkedIn URL** — the contact's LinkedIn profile
- **Background** — background info: bio, how the team met them
- **Has newsletter** — whether the contact receives the newsletter
- **Account manager** — the user who follows the contact
- **Status** — one of the configured note statuses, such as Cold, Warm, Hot or In Contract
- **Tags** — the tags put on the contact
- **Avatar** — the contact's picture, taken from their email address when none is given
- **First seen** — when the contact was added
- **Last seen** — the contact's last activity
- **Pending tasks** — how many of the contact's tasks are not done
