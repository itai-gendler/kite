---
references:
- kind: code
  role: implementation
  target: internal/content/content.go#Content
- kind: code
  role: implementation
  target: internal/content/contenttype.go#Type
---

# Declared content

An item of a content type the site declares, kept in that type's folder, given an address, a place in its listing, and a feed entry when its type asks for one.

## Information kept

- **Id** — the id Kite keeps it by for its whole life
- **Title** — its heading
- **Slug** — the last part of its address
- **Text** — its Markdown body
- **Fields** — the values of the fields its type declares
- **Weight** — its place in a listing ordered by weight
- **Terms** — the terms of the taxonomies its type names
- **Publish time** — when it was or will be published; a time in the future holds it back
- **Template** — a page template the active theme offers for its type
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
