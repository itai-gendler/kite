---
references:
- kind: code
  role: implementation
  target: internal/api/media.go#upload
- kind: code
  role: implementation
  target: internal/store/file/writer.go#putMedia
---

# File

A picture or other file added in the studio: kept beside a post in its folder and published with its address, or — for a page, or for something that belongs to no item such as a logo a theme setting names — kept among the site's own uploads in static/uploads/.

## Information kept

- **Name** — its name; one added under a name already taken gets a free one
- **Link** — how the text links it: by name beside a post, from the site's root among the uploads
- **Size** — how large it is
- **Where it is used** — in the text, as the cover, in a field, or not used
- **Location removed** — whether where a photo was taken was taken out of it when it was added
