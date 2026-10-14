---
appliesTo:
- type: entity
  id: theme
  effect: removes
  contexts:
  - place: studio
permits:
- actors: [owner]
  when:
  - {entity: studio-server, fact: Changes allowed, is: true}
  - {fact: Built in, is: false}
  - {fact: In use, is: false}
references:
- kind: code
  role: implementation
  target: internal/api/themes.go#handleRemoveTheme
- kind: code
  role: implementation
  target: internal/cli/theme_cmd.go#newThemeRemoveCmd
---

# Only the owner removes a theme, never the built-in one or the one in use

The theme compiled into Kite cannot be removed, and the theme the site uses stays until the site switches to another; otherwise the owner removes a theme where the server allows changes.
