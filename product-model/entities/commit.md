---
references:
- kind: code
  role: implementation
  target: internal/publish/publish.go#DeliveryState
- kind: code
  role: implementation
  target: internal/publish/publish.go#Result
- kind: code
  role: implementation
  target: internal/publish/git/publisher.go#State
---

# Commit

What one publish records in the site's Git repository, followed from the commit through the push to the site built from it.

## Information kept

- **Message** — its subject: "publish: <title>" for one item, unless a message is given
- **Paths** — exactly the paths it carries
- **Branch** — the branch it is made on and pushed to
- **Remote** — where it is pushed: the branch's upstream, or origin, or the only remote
- **Hash** — its hash; a commit put on top of the remote's new commits gets a new one
- **Host** — the host that deploys it, when it is one the studio knows: GitHub Pages, Vercel or Cloudflare Pages
- **Live address** — where the site built from it is live

## States

### Committed

Made on the branch and not yet on the remote.

### Pushed

On the remote; the site has not been built from it yet, as far as anyone has said.

### Deploying

The host reports a deployment of it under way.

### Live

The site was built from it, or from a later commit that contains it.

### Deploy failed

The host reports that deploying it failed.
