---
availability:
- place: studio::signed-in
- place: cli
domain: theme
references:
- kind: code
  role: implementation
  target: internal/api/settings.go#usableTheme
- kind: code
  role: implementation
  target: internal/cli/theme_cmd.go#newThemeUseCmd
---

# Use a theme

Switch the site to an installed theme: Use on the Theme page, Use and save in a theme's settings, or `kite theme use`. The settings kept for the previous theme stay in kite.yaml, and the new one goes on using those it shares.
