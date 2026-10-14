---
references:
- kind: code
  role: implementation
  target: internal/config/config.go
- kind: code
  role: implementation
  target: internal/api/settings.go#checkMenu
- kind: doc
  role: intent
  target: docs/reference.md
  title: Themes
---

# Menu link

A link in one of the site's menus — the links a theme draws, such as across its header — kept in kite.yaml apart from any theme, so another theme finds them where they were.

## Information kept

- **Menu** — the menu it is in, such as main
- **Name** — what it says
- **Address** — where it leads: a path from the site's root, published under the site's base path, or a full address
- **Links under it** — the links of the submenu it heads, to the depth the theme draws
