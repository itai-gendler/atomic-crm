---
scope: The CRM web app, its database schema and the edge functions behind users, merging, passwords, inbound email and the MCP server.
method: Static inspection of source, schema and documentation; nothing was run.
covered:
  - description: CRM web application screens, data access and configuration
    paths: [src/components/atomic-crm/, src/components/supabase/, src/App.tsx]
  - description: Database tables, views, functions, triggers, policies and search
    paths: [supabase/schemas/]
  - description: Edge functions for users, contact merging, password reset, inbound email and the MCP server
    paths: [supabase/functions/users/, supabase/functions/merge_contacts/, supabase/functions/update_password/, supabase/functions/postmark/, supabase/functions/mcp/, supabase/functions/_shared/]
  - description: Invitation and password recovery email templates
    paths: [supabase/templates/]
exclusions:
  - description: Vendored admin-kit and UI component libraries
    paths: [src/components/admin/, src/components/ui/]
  - description: In-browser demo data provider, sample data and the demo build
    paths: [src/components/atomic-crm/providers/fakerest/, demo/, test-data/]
  - description: Database migrations generated from the declarative schema
    paths: [supabase/migrations/, supabase/seed.sql]
  - description: Documentation site and contributor learnings
    paths: [doc/, docs/]
  - description: Tests, stories and agent tooling
    paths: [e2e/, src/test/, .storybook/, .claude/]
  - description: Build, deployment, registry and development-container tooling
    paths: [scripts/, .github/, .devcontainer/, makefile, registry.json, vite.config.ts, vite.demo.config.ts]
  - description: Storage cleanup of attachments removed from notes
    paths: [supabase/functions/delete_note_attachments/]
unmapped:
  - description: Dashboard deals revenue chart and pipeline widget
    paths: [src/components/atomic-crm/dashboard/DealsChart.tsx, src/components/atomic-crm/dashboard/DealsPipeline.tsx]
  - description: Interface language and light or dark theme selection
    paths: [src/components/atomic-crm/providers/commons/i18nProvider.ts, src/components/atomic-crm/settings/SettingsPageMobile.tsx]
  - description: Mobile layout navigation, refresh and offline cache
    paths: [src/components/atomic-crm/layout/]
  - description: Changelog page
    paths: [src/components/atomic-crm/misc/ChangelogPage.tsx]
  - description: Mobile note detail page
    paths: [src/components/atomic-crm/notes/NoteShowPage.tsx]
  - description: Direct REST data API exposed from the database grants
    paths: [supabase/schemas/06_grants.sql]
  - description: Anonymous usage telemetry ping
    paths: [src/components/atomic-crm/root/CRM.tsx]
limitations: []
---

# Coverage
