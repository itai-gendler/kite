---
kind: alternative
routes:
  site: Site
steps:
- text: The Reader's feed reader fetches rss.xml
  kind: actor
  actor: reader
  entities: []
  contexts:
    site:
      place: site
- text: The Product answers with the newest public posts, newest first, each with its title, address,
    date, description, categories, tags and cover
  kind: product
  actor: reader
  entities:
  - {entity: post, effect: reads, facts: [Id, Title, Slug, Description, Categories, Tags, Cover, Publish
        time]}
  - {entity: site-settings, effect: reads, facts: [Title, Address, Posts in the feed]}
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
  title: Configuration
---

# Follow the feed

## Trigger

A reader subscribes to the site.

## Outcome

The feed carries the newest posts; a post that moves stays one entry, since it is known by its id.

## Edge cases

- Items of a declared kind with feed on count as posts.
- Copies of the feed are written to each feed alias the site lists, for readers subscribed at old addresses.
