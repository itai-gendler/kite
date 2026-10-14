---
kind: alternative
routes:
  studio: Studio
steps:
- text: The Visitor runs kite run in an empty folder and, in the browser it opens, gives the site's name
    and their own name, and chooses Create site
  kind: actor
  actor: visitor
  entities: []
  contexts:
    studio:
      place: studio::signed-out::setup
- text: The Product creates the site in the folder, with Explore listed as an update service, and opens
    the studio on this computer with no password
  kind: product
  actor: visitor
  entities:
  - {entity: site-settings, effect: changes, facts: [Title, Address, Language, Author, Update services]}
  - {entity: studio-server, effect: changes, facts: [Waiting for setup]}
  contexts:
    studio:
      place: studio::signed-out::setup
references:
- kind: code
  role: implementation
  target: internal/api/setup.go#createSite
- kind: code
  role: implementation
  target: internal/cli/first_run.go
---

# Create a site in an empty folder

## Trigger

Someone starts writing in a new folder.

## Outcome

The folder is a site, and its studio works in local mode on this computer.
