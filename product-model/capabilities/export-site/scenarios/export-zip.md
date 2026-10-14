---
kind: primary
routes:
  studio: Studio
steps:
- text: The Owner chooses Export zip on the Deploy screen
  kind: actor
  actor: owner
  entities:
  - {entity: site-settings, effect: reads, facts: [Address]}
  contexts:
    studio:
      place: studio::signed-in::deploy
- text: The Product builds the site as a deployment gets it, leaving out every item that is not public
  kind: product
  actor: owner
  entities:
  - {entity: post, effect: reads, facts: [Title, Slug, Text, Publish time]}
  - {entity: page, effect: reads, facts: [Title, Slug, Text, Publish time]}
  - {entity: site-settings, effect: reads, facts: [Address, Theme in use, Theme settings]}
  contexts:
    studio:
      place: studio::signed-in::deploy
- text: The Product answers with the site at the top of a zip named after the site's host and the time
  kind: product
  actor: owner
  entities: []
  contexts:
    studio:
      place: studio::signed-in::deploy
references:
- kind: code
  role: implementation
  target: internal/api/export.go#exportName
- kind: code
  role: implementation
  target: internal/serve/server.go#export
---

# Export the site as a zip

## Trigger

The Owner wants to upload the site to a host themselves.

## Outcome

A zip of the static site is downloaded: unpacked, its files are the site. Drafts, archived and trashed items and items whose time has not come are not in it, even from a server that shows drafts.

## Edge cases

- While the site's address is still on this computer, the Deploy screen says feeds, the sitemap and shared links will point here, and offers to change it.
- A scheduled post appears once its time has come and the site is exported again.
