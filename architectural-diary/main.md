# Architectural Diary — Blunova Properties site

> All commit hashes below reference the current (message-rewritten) history. The project spans three active periods: a July 2024 bootstrap, an August 2024 Mavo CMS build-out, and a December 2025 content/SEO/rebrand sprint.

## Timeline

### Era 1 — Bootstrap (2024-07-07)

`433ae72` created the site as a self-contained static multipage website (index, about, contact, properties hub, one property detail page) with embedded CSS, Montserrat/Playfair Display fonts, and stock imagery. No framework, no build tooling — that constraint has never changed. See [001-static-site-bootstrap](decisions/001-static-site-bootstrap.md).

### Era 2 — Mavo CMS build-out (2024-08-16 → 2024-08-24)

The defining week of the project. `504c37b` introduced Mavo so the site owner could edit content in the browser. A burst of ~90 commits followed, most of them Mavo auto-saves ("Updated blunova-*.json") interleaved with hand-written HTML work:

- Storage format experiments settled on JSON over YAML (`16ac117`, [003-mavo-json-storage](decisions/003-mavo-json-storage.md)).
- A shadow-DOM web-components rebuild of Cherry Grove was attempted and immediately reverted (`93b14a3` → `18906e8`, [004-web-components-reverted](decisions/004-web-components-reverted.md)).
- Property pages were multiplied out — Cherry Grove, Creekhead Cove, Chimney (later Chimney Ridge), Luttrell — each with a unique Mavo app and JSON file (`63886fb`, `0ee06f8`, [005-per-page-mavo-apps](decisions/005-per-page-mavo-apps.md)).
- The contact page moved to Mavo plus a hosted `form-wrapper` form service (`5500118`, [006-contact-form](decisions/006-contact-form.md)).
- A fullscreen/lightbox gallery pattern emerged and was hardened after Mavo rendering (`63886fb`, later perfected in Era 3, [007-lightbox-gallery](decisions/007-lightbox-gallery.md)).
- Real photography replaced stock/Unsplash images in several upload commits.

### Era 3 — Content, rebrand, SEO, and honesty pass (2025-12-18 → 2025-12-19)

A two-day, ~36-commit sprint that professionalized the site:

- Rebranded all metadata from Nashville placeholders to the real Knoxville market and made home-page property cards data-driven from `blunova-home.json` (`fc10a91`, [008-knoxville-rebrand](decisions/008-knoxville-rebrand.md)).
- Rolled the Luttrell-style upgrades (lightbox gallery, categorized amenities, corrected facts) across all four listings (`33ed24c`, [007-lightbox-gallery](decisions/007-lightbox-gallery.md)).
- Fixed real breakage: image directories containing `#` produced un-loadable gallery URLs (`9550f1a`).
- Added a client-side spam filter for SEO-scam contact submissions (`d3c7e0b`, [006-contact-form](decisions/006-contact-form.md)).
- Added `sitemap.xml` and tightened per-page structured data (`dd3662d`, [009-seo-hardening](decisions/009-seo-hardening.md)).
- Removed the fake phone number and address and standardized on email-only contact, then stripped office hours and social links (`9d1a5dd`, `b7f83fa`, `222657d`, [010-email-only-contact](decisions/010-email-only-contact.md)).

## Post-history note (2026-09)

Commit messages for 108 of 112 commits were improved via a messages-only history rewrite (trees and diffs unchanged). Local branch `backup/pre-docs-20260908` preserves the pre-rewrite chain.

## Decisions index

| # | Decision | Key commits |
| --- | --- | --- |
| 001 | Static HTML site, no build system | `433ae72` |
| 002 | Mavo as the CMS, GitHub as storage | `504c37b` |
| 003 | JSON (not YAML) for Mavo storage | `16ac117` |
| 004 | Web components tried, reverted | `93b14a3`, `18906e8` |
| 005 | One Mavo app + JSON file per page | `63886fb`, `0ee06f8` |
| 006 | Hosted form-wrapper + client-side spam filter | `5500118`, `d3c7e0b` |
| 007 | Custom lightbox gallery on every listing | `33ed24c`, `9550f1a` |
| 008 | Knoxville rebrand, JSON-driven property cards | `fc10a91` |
| 009 | SEO hardening: sitemap, JSON-LD, OG | `dd3662d` |
| 010 | Email-only contact, footer cleanup | `9d1a5dd`, `222657d` |
