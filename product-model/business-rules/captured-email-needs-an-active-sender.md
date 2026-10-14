---
appliesTo:
- type: capability
  id: capture-inbound-email
- type: capability
  id: disable-user
references:
- kind: code
  role: implementation
  target: supabase/functions/postmark/addNoteToContact.ts
---

# Only email sent by an active user is captured

The sender must match exactly one active user by main or secondary email; the note is written as that user.
