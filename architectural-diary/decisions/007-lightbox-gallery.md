# 007 — Custom lightbox gallery on every listing

- **Date:** 2024-08-19 → 2025-12-18
- **Commits:** `63886fb`/`0ee06f8` (fullscreen viewer per page), `fcbbd6a` (feat(properties): add lightbox gallery to Luttrell page), `33ed24c` (feat(properties): add lightbox galleries, amenities, Knoxville SEO), `9550f1a` (fix(properties): rename Luttrell image dirs to fix gallery URLs)

## Context

Property pages need photo galleries. The first implementation was simple click-to-fullscreen; it broke when Mavo re-rendered the DOM, and had no navigation. Photography filenames/dirnames contained characters like `#` that broke URL resolution.

## Decision

Implement a self-contained lightbox (vanilla JS embedded per page): card-grid gallery with hover overlays and a zoom icon, overlay viewer with prev/next buttons, image counter, Escape/arrow-key support, touch swipe, and body scroll-lock. Bind it after Mavo render. Name image directories without URL-unsafe characters (`628-1` instead of `628 #1`).

## Alternatives

- **Lightbox library (GLightbox, PhotoSwipe)** — viable, but adds a dependency beside Mavo and less control over styling; not chosen.
- **Native `<dialog>` fullscreen images** — simpler but no counter/swipe polish.
- **The web-component `ImageGallery`** — died with decision 004's revert.

## Consequences

- Every listing page has identical, dependency-free gallery behavior; the December 2025 sprint rolled the final Luttrell version out to all four pages.
- The lightbox JS/CSS is duplicated in each property page — a deliberate consequence of the no-abstraction stance from decision 004.
- The `#`-directory bug (`9550f1a`) is a reminder that content-side filenames must be URL-safe because the JSON drives `<img src>` directly.
