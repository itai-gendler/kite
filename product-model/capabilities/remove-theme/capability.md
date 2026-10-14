---
availability:
- place: studio::signed-in
- place: cli
domain: theme
references:
- kind: code
  role: implementation
  target: internal/api/themes.go#handleRemoveTheme
- kind: code
  role: implementation
  target: internal/cli/theme_cmd.go#newThemeRemoveCmd
---

# Remove a theme

Delete an installed theme's folder (Remove, or `kite theme remove`) — never the built-in theme, and never the one in use. The deletion reaches the repository with the next publish.
