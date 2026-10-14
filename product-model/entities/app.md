---
references:
- kind: code
  role: implementation
  target: internal/api/apps.go#AppInfo
- kind: code
  role: implementation
  target: internal/apps/index.go
---

# App

A theme or a plugin the index lists, which the App center and `kite apps` show and install by name.

## Information kept

- **Kind** — theme or plugin
- **Name** — the name it is installed by
- **Description** — what it is
- **Made by** — official, or a community author
- **Versions** — its versions, each with release notes and the archive's sha256
- **Needs Kite** — the Kite versions each version works with
- **Loads from** — the other sites it has readers' browsers load from
- **Code on pages** — how many pieces of code it puts on pages
- **Build hooks** — what it runs while the site is built
- **Yanked** — whether a version was withdrawn
- **No longer listed** — whether, and why, the index took it off
- **Installed version** — the version the site has, and whether a newer one works with this Kite
