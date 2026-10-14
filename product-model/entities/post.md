---
relations:
- entity: file
  verb: keeps
  cardinality: one-to-many
- entity: term
  verb: carries
  cardinality: many-to-many
references:
- kind: code
  role: implementation
  target: internal/content/content.go#Content
- kind: code
  role: implementation
  target: internal/content/contenttype.go#builtinTypes
- kind: code
  role: implementation
  target: internal/store/file/codec.go
---

# Post

A dated piece of writing, kept as a folder (a bundle) under content/posts/ that holds its Markdown and its files. A Hugo-style single file is read as a post too. Posts are what the feed carries.

## Information kept

- **Id** — the id Kite keeps it by for its whole life, whatever its address or where its file lives
- **Title** — its heading
- **Slug** — the last part of its address, derived from the title unless set; it may hold a path
- **Text** — its Markdown body
- **Description** — its summary, shown in lists, search results and the feed
- **Cover** — the picture lists and share cards show, or none at all (No cover)
- **Pinned** — whether a theme keeps it at the top of lists
- **Categories** — the categories it is in
- **Tags** — its tags
- **Publish time** — when it was or will be published; a time in the future holds it back
- **Template** — a page template the active theme offers, chosen instead of the default
- **Aliases** — former addresses that send a browser on to it
- **Last saved** — when it was last saved
- **Deleted at** — when it went to the trash

## States

### Draft

Not on the site, unless the site is served with drafts for a local preview. A draft saves itself as the owner writes.

### Published

On the site once its publish time has come; a publish time in the future holds it back until then. Saved only when the owner saves.

### Scheduled

Waiting for its publish time, which it must have, and on the site once that time has passed.

### Archived

Kept, and not on the site.

### In the trash

Deleted: kept on disk with everything it owns so it can be restored, and not on the site. It keeps the status it had.
