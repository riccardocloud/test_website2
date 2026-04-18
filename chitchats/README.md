# Chit-Chats Podcast — Landing Page

A static landing page for **Chit-Chats**, a long-form interview podcast by Riccardo Murciano. Built as a single HTML file with external CSS — zero build step, zero dependencies, deploys to GitHub Pages in minutes.

## Repository structure

```
.
├── index.html              ← entry point
├── styles.css              ← all styles
├── assets/
│   ├── guests/             ← guest photos (jpg/webp, 1:1)
│   ├── covers/             ← episode cover images (optional override)
│   ├── logos/              ← company logos (svg preferred)
│   └── favicon.svg
├── CNAME                   ← (optional) custom domain
└── README.md
```

## Deploy to GitHub Pages — 5 minutes

1. **Create the repo.** On github.com click **New repository**. Name it e.g. `chit-chats-site`. Keep it public.
2. **Upload files.** Drag the contents of this folder into the repo (GitHub web UI → *Add file → Upload files → Commit*).
3. **Enable Pages.** Repo → **Settings → Pages** → *Source*: `Deploy from a branch` → *Branch*: `main` / `/ (root)` → **Save**.
4. **Wait ~1 minute.** GitHub emails you the URL: `https://<you>.github.io/chit-chats-site/`.
5. **Done.** Every push to `main` redeploys automatically.

## Custom domain (optional)

To serve at `podcast.riccardocloud.com`:

1. In your DNS provider, add a CNAME record: `podcast` → `<you>.github.io`.
2. Edit the `CNAME` file at repo root — put `podcast.riccardocloud.com` (one line, no protocol).
3. Repo → **Settings → Pages → Custom domain** → paste the same string → **Save**. Tick *Enforce HTTPS* once it becomes available (~10 min).

To serve at `riccardocloud.com/podcast` instead, host the repo inside the main site repo under a `/podcast` subfolder, or use a reverse proxy — see GitHub Pages docs for subpath routing.

## Replace placeholders with real assets

All guest portraits currently render as **initial monograms** via CSS (no image files needed to ship). To swap in real photos:

1. Drop square images (minimum 600×600, WebP or JPG) into `assets/guests/` named by slug: `peter-grafe.jpg`, `david-wood.jpg`, etc. Slugs are listed in `index.html` under each `<article data-slug="…">`.
2. The CSS auto-swaps the monogram for the image — nothing else to edit.

Similarly: `assets/logos/<org-slug>.svg` replaces text-set company names in the logo strip, and `assets/covers/<ep-slug>.jpg` can override the generated episode cover on the featured-episode hero.

## Maintenance — add a new episode

Open `index.html`, find the `<!-- EPISODES -->` block, copy any `<article class="ep-card">` and update the fields. Mark `data-featured="true"` on the newest one to bump it to the hero.

That's it.
