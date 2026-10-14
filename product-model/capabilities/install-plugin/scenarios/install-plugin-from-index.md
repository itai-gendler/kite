---
kind: alternative
routes:
  studio: Studio
steps:
- text: The Owner chooses Install on a listing in the App center
  kind: actor
  actor: owner
  entities:
  - {entity: app, effect: reads, facts: [Name, Loads from, Code on pages, Build hooks, Made by]}
  contexts:
    studio:
      place: studio::signed-in::app-center
- text: The Owner reads what it does to the site and confirms
  kind: actor
  actor: owner
  entities: []
  contexts:
    studio:
      place: studio::signed-in::app-center
- text: The Product fetches and checks the archive, installs the plugin switched off and records in kite.lock
    what it was installed to do
  kind: product
  actor: owner
  entities:
  - {entity: plugin, effect: creates, to: 'Off', facts: [Id, Name, Version, Adds code to pages, Loads
        from, Build hooks, Installed from the index, Agreed to do]}
  contexts:
    studio:
      place: studio::signed-in::app-center
references:
- kind: code
  role: implementation
  target: internal/api/apps.go#handleInstallApp
---

# Install a plugin from the index

## Trigger

The Owner found a plugin in the index.

## Outcome

The plugin is installed, off; the studio points to Plugins to turn it on.
