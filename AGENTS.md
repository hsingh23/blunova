# AGENTS.md — working guide for the Blunova Properties site

Static, no-build website for Blunova Properties (Knoxville, TN rentals), live at https://blunovainc.com/. There is no package manager, no bundler, no CI. Everything is hand-written HTML with embedded CSS, plus Mavo for in-browser editing.

## Commands

```bash
# Serve locally (any static server works)
python3 -m http.server 8000   # then open http://localhost:8000

# Git
git pull --ff-only origin main
git push origin main

# Verify a page's HTML after edits (no linters are configured)
npx prettier --check index.html        # formatting convention is Prettier-style, ~2-space indent
```

There are no tests, no linters, and no build step in the repo. Verification is visual: serve the folder and click through the eight pages (home, about, contact, properties hub, four property pages).

## Architecture map

- **Rendering**: static HTML, one file per page. CSS is embedded per page in `<style>` blocks (styles are duplicated across pages — a change usually must be replicated by hand).
- **Content editing**: [Mavo](https://mavo.io) is loaded from `get.mavo.io` on every page. Each page declares an `mv-app` (e.g. `blunova-home`) and `mv-storage="https://github.com/hsingh23/blunova"`. Editors authenticate with GitHub in the browser; saves commit JSON files (`blunova-*.json`) to `main`. The JSON files ARE the content database — HTML binds to them via `property` / `mv-list` / `mv-list-item` attributes (see `Mavo Editability Guide.md`).
- **Per-page Mavo apps**: `blunova-home`, `blunovaAbout-bup3s7` (about), `blunova-contact`, `blunova-cherryGrove`, `blunova-chimney`, `blunova-creekhead`, `blunova-luttrel`. Each app must stay unique or Mavo saves collide.
- **Contact form**: `contact.html` uses a `<form-wrapper data-form-id="[formId]">` element powered by a hosted script (`web.celeritytechconsulting.com/form-wrapper.js`) — no backend of our own.
- **Gallery**: custom lightbox JS duplicated on each property page (prev/next, counter, Escape/arrows, touch swipe, scroll lock).
- **SEO/Analytics**: JSON-LD + OG/Twitter meta per page; `sitemap.xml` at root; Google Analytics gtag on all pages (ID in `config.yml`).

## Conventions

- Commit messages: conventional commits (`type:`, `type(scope):`), imperative subject ≤72 chars, body explaining what/why. (Older history was largely Mavo auto-save messages like "Updated blunova-home.json".)
- Formatting is Prettier-style HTML (multi-line attributes, 2-space indent). Match the surrounding file.
- Property facts (beds/baths, names) live in BOTH the page meta/JSON-LD and the `blunova-*.json` content — keep them in sync.
- No secrets. The GA measurement ID and the public form endpoint are configuration, not secrets.

## Gotchas

- **Never rename or merge `blunova-*.json` files casually** — they are the Mavo storage for live pages; the HTML binds by app name and property keys.
- **Footer/nav links to `apply.html`, `faq.html`, `maintenance.html`, `tenant-portal.html`, `privacy-policy.html`, `terms-of-service.html`, `fair-housing.html` do not exist in the repo** — they are placeholders/dead links. Also watch for `href="[link]"` (unbound Mavo placeholder) in markup.
- **`apple-touch-icon.png` / `favicon-32x32.png` / `favicon-16x16.png` are referenced in `index.html` but missing** from the repo.
- **The about page's Mavo app (`blunovaAbout-bup3s7`) has no tracked JSON file** — its saves may create one; check before rebinding.
- A web-components rebuild of Cherry Grove was tried and reverted (2024); the codebase intentionally stays plain HTML + Mavo.
- The 2024→2025 history contains three intentionally empty commits (Mavo saves that produced no diff).

## Verify your changes

1. Serve locally and open every page you touched plus the home page.
2. Open the page's JSON file and confirm property keys still match `property="..."` attributes in the HTML (Mavo binding).
3. `grep -n "[link]" <page>.html` to catch unbound Mavo placeholders.
4. Push to `main` only; the site deploys from `main` on GitHub Pages.

## Pointers

- Full commit-by-commit history: `CHANGELOG.md`
- Narrative history and decisions: `architectural-diary/main.md` and `architectural-diary/decisions/`
