# Blunova Properties — blunovainc.com

Marketing and listings website for Blunova Properties, a provider of premium single-family and apartment rentals in Knoxville, Tennessee. The site is a fully static, no-build HTML/CSS/JS website made editable in the browser through Mavo, a client-side CMS that stores content as JSON files back into this GitHub repository.

**Live site:** https://blunovainc.com/

## Why this exists

The business needs a fast, SEO-friendly rental listings site that a non-developer can update (copy, photos, amenities, Airbnb room links) without a server, database, or deployment pipeline. Mavo provides in-browser editing on top of the static pages; every save commits a JSON file (e.g. `blunova-home.json`) to this repo, which GitHub Pages serves as the live site.

## Features

- **Four property detail pages** — Cherry Grove, Creekhead Cove, Chimney Ridge, and Luttrell & 3rd — each with a hero, quick facts, categorized amenities ("What this place offers"), a gallery with a full lightbox viewer (keyboard arrows, Escape, touch swipe, image counter), Airbnb room booking links, and guest testimonials.
- **Mavo-powered content editing** — every page is a Mavo app (`mv-app`) with `mv-storage="https://github.com/hsingh23/blunova"`, so content edits in the browser are saved as JSON to this repository. See `Mavo Editability Guide.md`.
- **Home page** with hero, Mavo-templated property cards driven by `blunova-home.json`, and site-wide footer.
- **Contact page** with a hosted form (`form-wrapper` element) and a client-side spam filter that blocks SEO-scam submissions by keyword.
- **SEO hardening** — per-page titles/descriptions/keywords, canonical URLs, Open Graph and Twitter cards, JSON-LD structured data, and `sitemap.xml`.
- **Analytics** — Google Analytics (gtag) on all pages (measurement ID lives in `config.yml`).

## Stack

No build step, no package manager. Dependencies are loaded from CDNs at runtime:

| Piece | Choice | Version |
| --- | --- | --- |
| Pages | Hand-written HTML with embedded CSS | — |
| CMS | Mavo (CSS + JS) | latest, from `get.mavo.io` |
| Fonts | Google Fonts: Montserrat (body) + Playfair Display (headings) | loaded at runtime |
| Icons | Font Awesome | 6.4.0 |
| Hosting | GitHub Pages, custom domain `blunovainc.com` | — |
| Analytics | Google Analytics (gtag) | — |

## Quick start

```bash
git clone git@github.com:hsingh23/blunova.git
cd blunova
open index.html        # or serve the folder: python3 -m http.server
```

Any static file server works; there is nothing to install or build.

To edit content as an editor would: open the live site, log into Mavo via the GitHub prompt (uses `mv-storage` above), edit, and save — Mavo commits the changed JSON back to `main`, and the site updates on the next deploy.

## Repository structure

```
index.html                    Home page (Mavo app: blunova-home)
about.html                    About page (Mavo app: blunovaAbout-bup3s7)
contact.html                  Contact page (Mavo app: blunova-contact) + spam filter
properties.html               All-listings hub page
properties/
  cherry-grove.html           Property pages (Mavo apps: blunova-cherryGrove, ...)
  chimney.html
  creekhead.html
  luttrell.html
  images/, cherry-grove-images/, rooms/   Property photography
images/                       Site-wide images (logo, og-image, hero photos)
blunova-home.json             Mavo storage: home page content
blunova-contact.json          Mavo storage: contact page content
blunova-cherryGrove.json      Mavo storage: per-property content
blunova-chimney.json
blunova-creekhead.json
blunova-luttrel.json
sitemap.xml                   SEO sitemap (8 URLs)
config.yml                    Google Analytics measurement ID (gtag)
Mavo Editability Guide.md     How Mavo attributes map to JSON
```

## History and docs

- `CHANGELOG.md` — every commit in the project's history, newest first.
- `AGENTS.md` — working conventions, architecture map, and gotchas for agents and contributors.
- `architectural-diary/` — narrative history and the key architectural decisions with their commits.
- `prompt.md` — a one-shot prompt that recreates this site from scratch.
