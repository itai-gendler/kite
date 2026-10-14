---
references:
- kind: code
  role: implementation
  target: internal/api/themes.go
- kind: code
  role: implementation
  target: internal/site/themes.go
---

# Theme

A theme the site can be built with: the built-in one, or a folder in themes/.

## Information kept

- **Name** — its folder's name, which the site names to use it
- **Version** — its version
- **Author** — who made it
- **Built in** — whether it is the theme compiled into Kite
- **In use** — whether the site is built with it
- **Problem** — why it cannot be used, when it cannot
- **Screenshot** — how it looks
- **Settings it declares** — the settings form it brings in theme.yaml
- **Page templates** — the templates an author may choose for an item
- **Menus it draws** — the menus it offers to fill in
- **Loads from** — the other sites its pages have a reader's browser load from
- **Installed from the index** — what kite.lock records for one that came from the index: version, index, archive and a digest of its files
- **Changed by hand** — whether its files changed since it was installed from the index
