---
entities:
- entity: menu-link
  shows:
  - Name
  - Address
  - Links under it
  - Menu
  collects:
  - Name
  - Address
  - Links under it
- entity: theme
  shows:
  - Menus it draws
- entity: post
  shows:
  - Title
- entity: page
  shows:
  - Title
references:
- kind: code
  role: implementation
  target: web/src/features/settings/menus/index.tsx
---

# Menus

The links each menu the theme draws holds, to the depth the theme draws it, with pages and posts picked by their titles; menus the theme does not draw are kept and shown apart.
