---
kind: validation
routes:
  studio: Studio
steps:
- text: The Owner uploads an archive
  kind: actor
  actor: owner
  entities: []
  contexts:
    studio:
      place: studio::signed-in::themes
- text: It holds no manifest, says it cannot be built into a static site, has a name that cannot name
    a folder, or takes the built-in one's name
  kind: condition
  actor: owner
  entities: []
  contexts:
    studio:
      place: studio::signed-in::themes
- text: The Product refuses it and installs nothing
  kind: product
  actor: owner
  entities: []
  contexts:
    studio:
      place: studio::signed-in::themes
references:
- kind: code
  role: implementation
  target: internal/api/themes.go#handleInstallTheme
---

# Upload something that is not a usable theme

## Trigger

The archive is not a theme this site can use.

## Outcome

Nothing is installed; the Theme page says why.
