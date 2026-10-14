---
references:
- kind: code
  role: implementation
  target: internal/api/plugins.go
- kind: code
  role: implementation
  target: internal/plugin/plugin.go
---

# Plugin

A plugin in plugins/: code it adds to pages, and WebAssembly it runs while the site is built.

## Information kept

- **Id** — its folder's name
- **Name** — its name
- **Version** — its version
- **Settings** — the values of the settings it declares, kept in kite.yaml under plugins.settings, and kept there while it is off
- **Adds code to pages** — the code it puts on pages, and on which
- **Loads from** — the other sites its code loads from
- **Build hooks** — what it runs while the site is built
- **Problem** — why it cannot be used, when it cannot
- **Installed from the index** — what kite.lock records for one that came from the index
- **Agreed to do** — what it was installed to do — code, sites and hooks — as kite.lock records it
- **Changed by hand** — whether its files changed since it was installed from the index

## States

### Off

Installed and doing nothing; listed nowhere in plugins.enabled.

### On

Listed in plugins.enabled, in the order it runs in.
