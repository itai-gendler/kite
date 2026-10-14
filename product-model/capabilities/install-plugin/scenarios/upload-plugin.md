---
kind: primary
routes:
  studio: Studio
steps:
- text: The Owner drops a plugin's zip archive on the Plugins screen
  kind: actor
  actor: owner
  entities:
  - {entity: plugin, effect: reads, facts: []}
  contexts:
    studio:
      place: studio::signed-in::plugins
- text: The Product checks it as a site loading it would and puts it in plugins/, switched off
  kind: product
  actor: owner
  entities:
  - {entity: plugin, effect: creates, to: 'Off', facts: [Id, Name, Version, Adds code to pages, Loads
        from, Build hooks]}
  contexts:
    studio:
      place: studio::signed-in::plugins
references:
- kind: code
  role: implementation
  target: internal/api/plugins.go#handleInstallPlugin
---

# Upload a plugin archive

## Trigger

The Owner has a plugin as a zip archive.

## Outcome

The plugin is installed and does nothing until it is switched on.
