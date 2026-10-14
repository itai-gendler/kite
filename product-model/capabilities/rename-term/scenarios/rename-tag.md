---
kind: primary
routes:
  studio: Studio
steps:
- text: The Owner chooses Rename on a tag and enters a new name
  kind: actor
  actor: owner
  entities:
  - {entity: term, effect: reads, facts: [Name, Count, Other ways of writing]}
  contexts:
    studio:
      place: studio::signed-in::terms
- text: The Product writes the new name on every post carrying the term in any of its spellings, in one
    change
  kind: product
  actor: owner
  entities:
  - {entity: term, effect: changes, facts: [Name, Other ways of writing]}
  - {entity: post, effect: changes, facts: [Tags]}
  contexts:
    studio:
      place: studio::signed-in::terms
references:
- kind: code
  role: implementation
  target: internal/api/terms.go#changeTerm
---

# Rename a tag

## Trigger

The Owner wants a tag called differently.

## Outcome

Every post that carried the tag, in the trash too, now carries the new name, and the tag's address follows it.

## Edge cases

- When an item carrying the term changed since the list was read, nothing is changed and the list is refreshed.
- Renaming to a name that already exists merges the two.
