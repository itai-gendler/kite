---
kind: primary
routes:
  cli: Command line
steps:
- text: The Owner names the Hexo site and an empty folder
  kind: actor
  actor: owner
  entities: []
  contexts:
    cli:
      place: cli
- text: The Product creates the project with the title, address, language, author and time zone the Hexo
    configuration gives, and the deploy workflow
  kind: product
  actor: owner
  entities:
  - {entity: site-settings, effect: changes, facts: [Title, Description, Address, Language, Author, Time
        zone, Update services]}
  contexts:
    cli:
      place: cli
- text: The Product turns each Hexo post into a post kept as a folder holding the files of its asset folder,
    each page into a page, and every other source file into one of the site's own static files
  kind: product
  actor: owner
  entities:
  - {entity: post, effect: creates, to: Published, facts: [Id, Title, Slug, Text, Description, Cover,
      Categories, Tags, Publish time, Aliases]}
  - {entity: page, effect: creates, to: Published, facts: [Id, Title, Slug, Text, Publish time, Aliases]}
  - {entity: file, effect: creates, facts: [Name, Link, Size], with: post}
  contexts:
    cli:
      place: cli
- text: The Product lists what it imported and the items that hold Hexo tags it left as written
  kind: product
  actor: owner
  entities: []
  contexts:
    cli:
      place: cli
references:
- kind: code
  role: implementation
  target: internal/importer/hexo/hexo.go
---

# Import a Hexo site into a new project

## Trigger

The Owner runs kite import hexo ../old-blog blog.

## Outcome

The new project holds the Hexo content, with every old address kept as an alias.

## Edge cases

- Hexo drafts and posts with published: false become drafts.
- Nested categories are flattened, dates are read in the site's time zone, and a picture a Hexo theme names becomes the cover.
- asset_img, asset_link and asset_path tags become Markdown; folders starting with _ are left out.
