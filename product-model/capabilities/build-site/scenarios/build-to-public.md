---
kind: primary
routes:
  cli: Command line
steps:
- text: The Owner runs kite build
  kind: actor
  actor: owner
  entities: []
  contexts:
    cli:
      place: cli
- text: The Product writes every public page, the feed, the sitemap and kite-build.json into the output
    folder, replacing what an earlier build wrote there
  kind: product
  actor: owner
  entities:
  - {entity: post, effect: reads, facts: [Title, Slug, Text, Publish time]}
  - {entity: page, effect: reads, facts: [Title, Slug, Text, Publish time]}
  - {entity: site-settings, effect: reads, facts: [Address, Theme in use, Build stamp]}
  contexts:
    cli:
      place: cli
- text: The Product reports what it wrote and when the next scheduled item falls due
  kind: product
  actor: owner
  entities: []
  contexts:
    cli:
      place: cli
references:
- kind: code
  role: implementation
  target: internal/cli/build_cmd.go#printBuild
---

# Build into public/

## Trigger

The Owner, or the deploy workflow, builds the site.

## Outcome

The static site is in the output folder; a scheduled post reaches it only with a build after its time.

## Edge cases

- With no site address, the feed and the sitemap can only give relative links, and the build warns.
