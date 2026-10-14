---
references:
- kind: code
  role: implementation
  target: internal/content/contenttype.go#builtinTypes
---

# Page

A standing page of the site such as About, kept as a single Markdown file under content/pages/ and published at its slug from the site's root. Pages carry no tags or categories and are not in the feed.

## Information kept

- **Id** — the id Kite keeps it by for its whole life, whatever its address or where its file lives
- **Title** — its heading
- **Slug** — its address from the site's root; it may hold a path
- **Text** — its Markdown body
- **Description** — its summary
- **Menu weight** — its place among pages in a menu
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
