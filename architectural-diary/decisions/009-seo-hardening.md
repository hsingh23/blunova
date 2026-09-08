# 009 — SEO hardening: sitemap, JSON-LD, structured metadata

- **Date:** 2024-08-18 → 2025-12-19
- **Commits:** `dd3662d` (feat: Add sitemap.xml for improved SEO and site indexing), `14dd57f` (fix(properties): correct hero, og/twitter, and JSON-LD image paths), `469278d`/`81c5b3f` (real photography for cards), `10f6308` (formatting normalization), plus the JSON preload commits (`8850095`-era: JSON preload links and metadata structure)

## Context

The site competes for local search ("houses for rent Knoxville TN"). Early metadata was generic or placeholder; images were stock; there was no sitemap; JSON-LD and OG image paths were broken on some pages.

## Decision

Treat SEO as a first-class feature: per-page unique titles/descriptions/keywords with local intent, canonical URLs on `blunovainc.com`, Open Graph + Twitter cards with a real `og-image.jpg`, multiple JSON-LD blocks per page (RealEstateListing/Residence + ItemList + breadcrumbs), `<link rel="preload">` for the Mavo JSON data, and a hand-maintained `sitemap.xml` covering all 8 pages with per-page priorities.

## Alternatives

- **Generate the sitemap in CI** — rejected: no CI exists (decision 001); 8 URLs are manageable by hand.
- **Minimal meta only** — rejected: local rental search is the site's primary acquisition channel.

## Consequences

- Every page addition now requires updating: the page's own meta/JSON-LD, `sitemap.xml`, and (if listed on the home page) a `propertyCard` entry.
- The hand-maintained sitemap can silently go stale if a page is added/renamed.
- Structured-data correctness depends on property facts staying in sync across HTML, meta, and JSON (recurring Chimney Ridge count fixes).
