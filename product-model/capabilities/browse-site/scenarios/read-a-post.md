---
kind: primary
routes:
  site: Site
steps:
- text: The Reader opens the address of a published post
  kind: actor
  actor: reader
  entities:
  - {entity: post, effect: reads, facts: []}
  contexts:
    site:
      place: site
- text: The Product serves the post as a build would have written it
  kind: product
  actor: reader
  entities:
  - {entity: post, effect: reads, facts: [Title, Text, Description, Cover, Categories, Tags, Publish time]}
  contexts:
    site:
      place: site
references:
- kind: code
  role: implementation
  target: internal/serve/router.go#router
---

# Read a published post

## Trigger

A reader follows a link to a post.

## Outcome

The reader sees the post.
