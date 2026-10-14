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
      place: studio::signed-in::plugins
- text: It holds no manifest, or what it holds does not load
  kind: condition
  actor: owner
  entities: []
  contexts:
    studio:
      place: studio::signed-in::plugins
- text: The Product refuses it and installs nothing
  kind: product
  actor: owner
  entities: []
  contexts:
    studio:
      place: studio::signed-in::plugins
references:
- kind: code
  role: implementation
  target: internal/api/plugins.go#handleInstallPlugin
---

# Upload something that is not a usable plugin

## Trigger

The archive is not a plugin this site can load.

## Outcome

Nothing is installed.
