# Portfolio site

A plain-text artist site built for GitHub Pages. Every page is a Markdown file you can edit directly on github.com — save, wait a minute, it's live.

```
_config.yml          ← your name, photo path, footer links, menu
index.md             ← landing page (your photo + optional line of text)
about.md             ← About
upcoming.md          ← Upcoming gigs
archive.md           ← Past gigs + set recordings
assets/images/me.jpg ← your photo (replace this file)
assets/fonts/        ← Source Serif 4 (already included)
assets/css/style.css ← look & feel
CNAME                ← your custom domain
```

---

## 1. Put it on GitHub

1. On github.com, click **+ → New repository**.
   - Name it `yourusername.github.io` (replace with your actual username). Any name works, but this one is the simplest.
   - Set it to **Public**, then **Create repository**.
2. On the new repo page, click **uploading an existing file**, drag in *everything* inside this folder (including the `_layouts` and `assets` folders), and click **Commit changes**.
   - Files starting with a dot (`.gitignore`) may be hidden on your computer — that one is optional, skip it if you can't see it.

## 2. Personalise it

Edit files right on github.com: open a file, click the ✏️ pencil, change it, **Commit changes**.

1. **`_config.yml`** — set `title` (your name), `url` (your domain), and the footer `links`.
2. **`CNAME`** — replace `yourdomain.com` with your real domain, e.g. `janedoe.com` (just the domain, nothing else).
3. **Your photo** — open `assets/images`, click **Add file → Upload files**, upload your photo named **`me.jpg`** (it replaces the placeholder). Using a different name or `.png`? Update `landing_photo` in `_config.yml` to match.
   - Tip: resize it to about 2000px on the long side first, so it loads fast on phones.

## 3. Turn on GitHub Pages

1. Repo → **Settings → Pages**.
2. Under **Build and deployment**, Source: **Deploy from a branch**. Branch: **main**, folder **/ (root)** → **Save**.
3. Wait 1–2 minutes. The **Actions** tab shows a green tick when the site is built.

## 4. Connect your domain

At your domain registrar (Namecheap, GoDaddy, Porkbun, Cloudflare, etc.), open the DNS settings and add:

| Type  | Host / Name | Value |
|-------|-------------|-------|
| A     | `@`         | `185.199.108.153` |
| A     | `@`         | `185.199.109.153` |
| A     | `@`         | `185.199.110.153` |
| A     | `@`         | `185.199.111.153` |
| CNAME | `www`       | `yourusername.github.io` |

Remove any other existing `A` records on `@` (often a registrar "parking" page) — they'll conflict.

Then back in **Settings → Pages**:
1. Under **Custom domain**, enter your domain and **Save**. It should match what's in `CNAME`.
2. Once the DNS check passes (minutes to a few hours), tick **Enforce HTTPS**.

Optional but recommended: in your GitHub profile **Settings → Pages**, **verify** the domain so nobody else can claim it on GitHub.

> These IP addresses are GitHub's published ones at the time of writing; GitHub's "Managing a custom domain" docs have the current list.

---

## Everyday editing

**Add a gig** — edit `upcoming.md`:

```markdown
### Fri 24 Oct 2026 — Venue Name, Toronto
Doors 9pm · with Other Artist · [Tickets](https://link)
```

**Gig's over** — cut that block from `upcoming.md` and paste it into `archive.md` under the right year.

**Add a set recording** — under the gig in `archive.md`, either paste a plain link:

```markdown
[Listen to the set](https://soundcloud.com/...)
```

…or an embedded player: on SoundCloud / YouTube / Bandcamp click **Share → Embed**, copy the `<iframe …>` code, and paste it on its own line. It resizes for phones automatically.

**Markdown cheatsheet**

| You type | You get |
|---|---|
| `*italic*` | *italic* |
| `**bold**` | **bold** |
| `[text](https://url)` | a link |
| `## Heading` | a section heading |
| `- item` | a bullet list |
| `---` | a thin divider line |
| blank line | new paragraph |

**Add a new page** — create e.g. `press.md`:

```markdown
---
layout: default
title: Press
permalink: /press/
---

Your text here.
```

…then add it to `nav` in `_config.yml`:

```yaml
  - title: Press
    url: /press/
```

**Change colours** — top of `assets/css/style.css`, the `--ink` and `--paper` values. The site follows the visitor's dark mode automatically; delete the `@media (prefers-color-scheme: dark)` block if you'd rather it always be light.

---

## Preview on your computer (optional)

Not required — editing on github.com is enough. If you want to preview before publishing, install Ruby, then in this folder:

```
bundle install
bundle exec jekyll serve
```

and open http://localhost:4000.

---

Font: Source Serif 4 by Adobe, SIL Open Font License — free to self-host.
