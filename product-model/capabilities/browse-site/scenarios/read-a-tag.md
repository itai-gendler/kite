---
kind: alternative
routes:
  site: Site
steps:
- text: The Reader opens the address of a tag
  kind: actor
  actor: reader
  entities:
  - {entity: term, effect: reads, facts: [Address]}
  contexts:
    site:
      place: site
- text: The Product lists the public posts carrying the term in any spelling, newest first, a page at
    a time
  kind: product
  actor: reader
  entities:
  - {entity: term, effect: reads, facts: [Name, Count]}
  - {entity: post, effect: reads, facts: [Title, Description, Publish time, Tags]}
  - {entity: site-settings, effect: reads, facts: [Posts per page]}
  - {entity: page, effect: reads, facts: []}
  contexts:
    site:
      place: site
references:
- kind: code
  role: implementation
  target: internal/render/model.go
- kind: doc
  role: intent
  target: docs/reference.md
  title: Themes
---

# Read the posts of a tag

## Trigger

A reader follows a tag.

## Outcome

The reader sees the posts of the tag, paged as the theme or the site says.
