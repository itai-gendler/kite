---
entities:
- entity: theme
  shows:
  - Name
  - In use
  - Settings it declares
- entity: site-settings
  shows:
  - Theme settings
  collects:
  - Theme settings
references:
- kind: code
  role: implementation
  target: web/src/features/settings/theme/customize.tsx
- kind: code
  role: implementation
  target: web/src/features/settings/theme/preview-frame.tsx
---

# Theme settings

One theme tried on the whole site: the settings it declares, edited beside a preview of the site drawn with them.
