---
kind: primary
routes:
  studio: Studio
steps:
- text: The Owner chooses Merge into on a tag and picks the tag to keep
  kind: actor
  actor: owner
  entities:
  - {entity: term, as: merged, effect: reads, facts: [Name, Count]}
  - {entity: term, as: kept, effect: reads, facts: [Name, Count]}
  contexts:
    studio:
      place: studio::signed-in::terms
- text: The Product writes the kept name on every post carrying the merged one
  kind: product
  actor: owner
  entities:
  - {entity: term, as: merged, effect: removes}
  - {entity: term, as: kept, effect: changes, facts: [Count]}
  - {entity: post, effect: changes, facts: [Tags]}
  contexts:
    studio:
      place: studio::signed-in::terms
references:
- kind: code
  role: implementation
  target: internal/api/terms.go#changeTerm
---

# Merge two tags

## Trigger

Two tags mean the same thing.

## Outcome

Only the kept tag remains, carried once by each post that had either.
