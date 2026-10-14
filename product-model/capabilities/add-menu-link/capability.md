---
availability:
- place: studio::signed-in
domain: menus
references:
- kind: code
  role: implementation
  target: web/src/features/settings/menus/index.tsx
- kind: code
  role: implementation
  target: internal/api/settings.go#checkMenu
---

# Add a menu link

Add a link to a menu the theme draws — written, or a page or post picked by its title — on the Menus screen, and save.
