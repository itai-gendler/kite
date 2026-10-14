---
kind: alternative
routes:
  studio: Studio
steps:
- text: The Owner chooses New project in the list of a content type the site declares
  kind: actor
  actor: owner
  entities:
  - {entity: content-type, effect: reads, facts: [Label]}
  contexts:
    studio:
      place: studio::signed-in::content-list
- text: The Product opens the editor with the fields the content type declares
  kind: product
  actor: owner
  entities:
  - {entity: content-type, effect: reads, facts: [Fields, Taxonomies]}
  contexts:
    studio:
      place: studio::signed-in::editor
- text: The Owner types a title and fills the fields
  kind: actor
  actor: owner
  entities: []
  contexts:
    studio:
      place: studio::signed-in::editor
- text: The Product saves the new declared content as a draft in its type's folder
  kind: product
  actor: owner
  entities:
  - {entity: declared-content, effect: creates, to: Draft, facts: [Id, Title, Slug, Text, Fields, Last
        saved]}
  contexts:
    studio:
      place: studio::signed-in::editor
references:
- kind: code
  role: implementation
  target: internal/api/write.go#handleCreate
- kind: code
  role: implementation
  target: internal/content/contenttype.go#Type
---

# Create an item of a declared kind

## Trigger

The site declares a kind of its own, such as projects.

## Outcome

A draft declared item exists in its type's folder, laid out as the type says.
