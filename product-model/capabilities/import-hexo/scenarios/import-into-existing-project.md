---
kind: alternative
routes:
  cli: Command line
steps:
- text: The Owner names the Hexo site and an existing Kite project
  kind: actor
  actor: owner
  entities: []
  contexts:
    cli:
      place: cli
- text: The Product adds the posts and pages to the project, giving a number to a slug it already uses
  kind: product
  actor: owner
  entities:
  - {entity: post, effect: creates, to: Published, facts: [Id, Title, Slug, Text, Categories, Tags, Publish
        time, Aliases]}
  - {entity: page, effect: reads, facts: []}
  contexts:
    cli:
      place: cli
references:
- kind: code
  role: implementation
  target: internal/importer/hexo/hexo.go
---

# Import a Hexo site into a Kite project

## Trigger

The Owner merges an old Hexo blog into a Kite site.

## Outcome

The project holds both, with no address taken twice.
