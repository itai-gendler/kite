---
kind: primary
routes:
  studio: Studio
steps:
- text: The Owner chooses Delete on a tag and confirms
  kind: actor
  actor: owner
  entities:
  - {entity: term, effect: reads, facts: [Name, Count]}
  contexts:
    studio:
      place: studio::signed-in::terms
- text: The Product takes the tag, in every spelling, off every post that carries it
  kind: product
  actor: owner
  entities:
  - {entity: term, effect: removes}
  - {entity: post, effect: changes, facts: [Tags]}
  contexts:
    studio:
      place: studio::signed-in::terms
references:
- kind: code
  role: implementation
  target: internal/api/terms.go#handleRemoveTerm
---

# Delete a tag

## Trigger

The Owner drops a tag.

## Outcome

No post carries the tag any more, and its page is gone from the site once built.
