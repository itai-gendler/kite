---
availability:
- place: studio::signed-in
- place: cli
references:
- kind: code
  role: implementation
  target: internal/api/themes.go#handleInstallTheme
- kind: code
  role: implementation
  target: internal/api/apps.go#handleInstallApp
- kind: code
  role: implementation
  target: internal/cli/theme_cmd.go#newThemeAddCmd
---

# Install a theme

Add a theme to themes/: from its zip archive on the Theme page, by name from the index in the App center, or with `kite theme add <name[@version]|archive|folder>`. It is checked the way a site checks a theme it loads, and the site keeps its theme until the owner switches. A theme from the index is recorded in kite.lock with where it came from.
