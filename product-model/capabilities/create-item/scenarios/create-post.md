---
kind: primary
routes:
  studio: Studio
steps:
- text: The Owner chooses New post
  kind: actor
  actor: owner
  entities:
  - {entity: post, effect: reads, facts: []}
  contexts:
    studio:
      place: studio::signed-in::content-list
- text: The Product opens the editor on an unsaved draft in the default category
  kind: product
  actor: owner
  entities: []
  contexts:
    studio:
      place: studio::signed-in::editor
- text: The Owner types a title and the opening of the text
  kind: actor
  actor: owner
  entities: []
  contexts:
    studio:
      place: studio::signed-in::editor
- text: The Product saves the new post as a draft in the default category, its slug taken from the title
  kind: product
  actor: owner
  entities:
  - {entity: post, effect: creates, to: Draft, facts: [Id, Title, Slug, Text, Categories, Last saved]}
  contexts:
    studio:
      place: studio::signed-in::editor
- text: The editor moves to the post's own address and goes on with it
  kind: condition
  actor: owner
  entities:
  - {entity: post, effect: reads, facts: []}
  contexts:
    studio:
      place: studio::signed-in::editor
references:
- kind: code
  role: implementation
  target: internal/api/write.go#handleCreate
- kind: code
  role: implementation
  target: web/src/hooks/useItem.ts#autosaves
---

# Create a post

## Trigger

The Owner wants to write a new post.

## Outcome

A draft post exists in its own folder under content/posts/, in the default category; it is not on the site.

## Edge cases

- With the default category set to empty, the post starts in no category; left out, it starts in Uncategorized in the site's language.
- A new item with nothing typed in it is not saved on its own; leaving one that has something saves it on the way out.
- What is typed and not saved yet is kept in the browser, and offered back when the item opens again.
