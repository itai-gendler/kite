---
availability:
- place: studio::signed-in
domain: theme
references:
- kind: code
  role: implementation
  target: internal/api/settings.go#checkThemeSetting
- kind: code
  role: implementation
  target: web/src/features/settings/theme/customize.tsx
---

# Change theme settings

Edit the settings the theme declares, section by section beside a live preview of the page each section names, and save them (Customize, then Save). Values are stored under theme.settings in kite.yaml; a setting put back to its default is removed from it.
