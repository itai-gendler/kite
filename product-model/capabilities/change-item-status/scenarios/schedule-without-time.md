---
kind: validation
routes:
  studio: Studio
steps:
- text: The Owner chooses Scheduled for a post with no publish time, and saves
  kind: actor
  actor: owner
  entities:
  - {entity: post, effect: reads, facts: []}
  contexts:
    studio:
      place: studio::signed-in::editor
- text: The Product refuses the save, as a scheduled item needs a publish time
  kind: product
  actor: owner
  entities:
  - {entity: post, effect: reads, facts: [Publish time]}
  contexts:
    studio:
      place: studio::signed-in::editor
references:
- kind: code
  role: implementation
  target: internal/content/content.go#Validate
---

# Schedule without a publish time

## Trigger

The Owner schedules a post and leaves the time empty.

## Outcome

Nothing is saved; the post keeps its stored status until a time is chosen.
