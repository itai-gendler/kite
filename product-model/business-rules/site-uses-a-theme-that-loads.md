---
appliesTo:
- type: capability
  id: use-theme
  contexts:
  - place: studio::signed-in
  - place: cli
references:
- kind: code
  role: implementation
  target: internal/api/settings.go#usableTheme
---

# The site switches only to an installed theme that loads

A theme listed with a problem cannot be used until it is fixed.
