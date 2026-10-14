---
kind: alternative
routes:
  studio: Studio
steps:
- text: The Owner chooses Scheduled and a publish time in the future for a draft post, and saves
  kind: actor
  actor: owner
  entities:
  - {entity: post, effect: reads, facts: []}
  contexts:
    studio:
      place: studio::signed-in::editor
- text: The Product saves the post as scheduled for that time
  kind: product
  actor: owner
  entities:
  - {entity: post, effect: changes, from: Draft, to: Scheduled, facts: [Publish time, Last saved]}
  contexts:
    studio:
      place: studio::signed-in::editor
references:
- kind: code
  role: implementation
  target: internal/content/content.go#IsPublic
- kind: code
  role: implementation
  target: internal/kitew/workflow.go
---

# Schedule a post

## Trigger

The Owner wants a post to go out later.

## Outcome

The post is on a site Kite serves once its time has passed; a static site shows it once built after that time.

## Edge cases

- The GitHub Pages workflow Kite writes checks every hour whether a scheduled post has fallen due and deploys then; any other host has to build again after the time.
