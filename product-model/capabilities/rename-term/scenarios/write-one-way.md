---
kind: alternative
routes:
  studio: Studio
steps:
- text: The Owner chooses Write it one way on a tag written as Go, go and GO
  kind: actor
  actor: owner
  entities:
  - {entity: term, effect: reads, facts: [Name, Other ways of writing]}
  contexts:
    studio:
      place: studio::signed-in::terms
- text: The Product writes the tag the way most posts write it on every post that writes it otherwise
  kind: product
  actor: owner
  entities:
  - {entity: term, effect: changes, facts: [Other ways of writing]}
  - {entity: post, effect: changes, facts: [Tags]}
  contexts:
    studio:
      place: studio::signed-in::terms
references:
- kind: code
  role: implementation
  target: internal/api/terms.go#writesOnly
---

# Write a term one way

## Trigger

A tag is written several ways.

## Outcome

The tag is written one way everywhere.
