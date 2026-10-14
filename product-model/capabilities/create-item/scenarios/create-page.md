---
kind: alternative
routes:
  studio: Studio
steps:
- text: The Owner chooses New page
  kind: actor
  actor: owner
  entities:
  - {entity: page, effect: reads, facts: []}
  contexts:
    studio:
      place: studio::signed-in::content-list
- text: The Product opens the editor on an unsaved draft
  kind: product
  actor: owner
  entities: []
  contexts:
    studio:
      place: studio::signed-in::editor
- text: The Owner types a title and some text and chooses Save
  kind: actor
  actor: owner
  entities: []
  contexts:
    studio:
      place: studio::signed-in::editor
- text: The Product saves the new page as a draft in its own Markdown under content/pages/
  kind: product
  actor: owner
  entities:
  - {entity: page, effect: creates, to: Draft, facts: [Id, Title, Slug, Text, Last saved]}
  contexts:
    studio:
      place: studio::signed-in::editor
references:
- kind: code
  role: implementation
  target: internal/api/write.go#handleCreate
- kind: code
  role: implementation
  target: internal/content/contenttype.go#builtinTypes
---

# Create a page

## Trigger

The Owner wants a new standing page such as About.

## Outcome

A draft page exists as one Markdown file; it is not on the site.
