---
entities:
- entity: app
  shows:
  - Kind
  - Name
  - Description
  - Made by
  - Versions
  - Needs Kite
  - Loads from
  - Code on pages
  - Build hooks
  - Yanked
  - No longer listed
  - Installed version
references:
- kind: code
  role: implementation
  target: web/src/features/apps/index.tsx
- kind: code
  role: implementation
  target: web/src/features/apps/app-sheet.tsx
- kind: code
  role: implementation
  target: web/src/features/apps/dialogs.tsx
---

# App center

The themes and plugins the index lists, searched by word and by who makes them, with what each loads, injects and runs, which are installed, and which have a newer version.
