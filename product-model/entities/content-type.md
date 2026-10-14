---
relations:
- entity: declared-content
  verb: holds
  cardinality: one-to-many
references:
- kind: code
  role: implementation
  target: internal/content/contenttype.go#Type
- kind: code
  role: implementation
  target: internal/content/contenttype.go#Declare
- kind: doc
  role: intent
  target: docs/reference.md
  title: Content types
---

# Content type

A kind of content a site declares of its own in kite.yaml under content.types, beside posts and pages — such as a portfolio's projects or a reading list's books. It is configured in the file, not in the studio, and the studio lists it beside posts and pages with a form drawn from its fields.

## Information kept

- **Kind** — its name, lowercase letters, digits, - and _
- **Label** — what the studio calls it
- **Folder** — its folder under content/, which is also its listing's address
- **Route** — the address pattern of its items, the folder and the slug unless set
- **Layout** — a folder per item (bundle) or a file per item (single)
- **Order** — by date, newest first, or by weight, smallest first
- **In the feed** — whether its items count as posts in the feed
- **Taxonomies** — the taxonomies its items carry
- **Fields** — the fields its items keep, drawn as a form the way a theme's settings are
