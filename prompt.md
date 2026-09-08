# One-shot recreation prompt — Blunova Properties rental website

Use the prompt below to recreate this website from scratch in one session. It mirrors the actual build order of the repository (July 2024 → December 2025). Hashes reference the current (message-rewritten) history; see `CHANGELOG.md` for details.

---

Build a production-ready marketing and listings website for **Blunova Properties**, a provider of premium rental homes (single-family houses and small apartment buildings) in **Knoxville, Tennessee**. The site must be 100% static (no build system, no bundler, no package manager), editable in the browser by a non-developer, and deployed on GitHub Pages under the custom domain **https://blunovainc.com/**.

## Hard constraints (the stack)

- Hand-written HTML files, one per page, CSS embedded in per-page `<style>` blocks. No framework, no SSG, no build step.
- **Mavo** (CSS `mavo.min.css` + JS `mavo.min.js` from `https://get.mavo.io/`) as the client-side CMS; every page is a Mavo app with `mv-storage="https://github.com/hsingh23/blunova"` (saves commit JSON to the repo).
- Fonts from Google Fonts: **Montserrat** (300–700, body/UI) and **Playfair Display** (400–700, headings).
- Icons: **Font Awesome 6.4.0** from cdnjs.
- Contact form via hosted `<form-wrapper data-form-id="[formId]">` element + script from `https://web.celeritytechconsulting.com/form-wrapper.js`. No backend of our own; no API keys in the repo.
- Google Analytics (gtag) on every page; the measurement ID lives in `config.yml` (`gtag:`). This is the only "environment" value — there are no other env vars or secrets.
- Formatting convention: Prettier-style HTML (multi-line attributes, 2-space indent).

## Design / UI-UX decisions (follow exactly)

- **Palette**: deep navy foundation (`#0f2744`, `#1a365d`, `#2c5282`), light neutrals (`#f7fafc`, `#e2e8f0`, `#718096`), white cards, green success accents (`#48bb78`), orange CTAs (`#ed8936` hover `#dd6b20`). Generous use of `linear-gradient` overlays on heroes and section bands.
- **Hero**: full-width background image (`heroImage`) with a gradient scrim, a small badge above the title (`heroBadge`), Playfair Display headline, supporting paragraph, CTA button.
- **Property cards** (home page): Mavo-templated card list (`mv-list`, fields: `image`, `title`, `location`, `description`, `link`) — never hardcode a card.
- **Property page hero stats**: beds/baths/sqft row; price displayed as a **centered gradient pill badge** with the location line beneath.
- **Gallery**: card grid with hover overlay + zoom icon; clicking opens a full **lightbox** — overlay, prev/next buttons, image counter, Escape/arrow-key navigation, touch swipe, body scroll-lock. Implemented as embedded vanilla JS per page, bound after Mavo renders (the gallery list comes from the JSON `pictures` array).
- **Amenities**: "What this place offers" section, `amenities-grid` of category cards (`amenities-category h3` + `amenities-list`) — categories, not a flat list.
- **Testimonials**: guest review cards on property pages; Airbnb room booking links under "Book room on Airbnb".
- **Footer**: navy, Quick Links + About + Contact Us columns, email-only contact (info@blunovainc.com). No social links, no phone, no office hours, no street address.
- **Contact page**: quick-contact card with styled inline mailto links (white bold, subtle bottom border, hover underline/ring), then the hosted form; spam filter script below.
- Sticky header with logo `logo.png`; site-wide `og-image.jpg` (1200×630).

## Data model (Mavo JSON files at repo root — these ARE the content database)

One JSON file per page app; flat schemas, keys matching the `property="..."` attributes exactly:

- `blunova-home.json` — `heroBadge`, `heroTitle`, `heroDescription`, `trustBadges`, `features`, `sectionContent` (tinymce-editable), `propertyCard[]` (`image`, `title`, `location`, `description`, `link`), `testimonials`, `ctaTitle`, `ctaDescription`, `ctaButtonText`, `links[]`, `footer`, `link`
- `blunova-contact.json` — `heroBadge`, `heroTitle`, `heroDescription`, `contactInfo`, `formId`, `faqItem[]`, `links[]`, `link`
- Per-property files: `blunova-cherryGrove.json`, `blunova-chimney.json`, `blunova-creekhead.json`, `blunova-luttrel.json` (single-l typo intentional, keep it) — each with `heroImage`, `property-hero-content`, `property-details` (Quick Facts), `gallery-desc`, `pictures[]` (gallery)
- App names: `blunova-home`, `blunovaAbout-bup3s7` (about page), `blunova-contact`, `blunova-cherryGrove`, `blunova-chimney`, `blunova-creekhead`, `blunova-luttrel`. One app per page, never shared (shared apps overwrite each other's saves).

## Pages

1. `index.html` — home (hero, trust badges, features, property cards, testimonials, CTA)
2. `about.html` — company story
3. `contact.html` — contact info + form + spam filter
4. `properties.html` — all-listings hub
5. `properties/cherry-grove.html`, `properties/creekhead.html`, `properties/chimney.html` (Chimney Ridge), `properties/luttrell.html`
6. `sitemap.xml` — 8 URLs, home priority 1.00 daily, property pages 0.80 weekly, about/contact 0.60 monthly

## SEO requirements

Per-page unique title/description/keywords with Knoxville local intent ("houses for rent Knoxville TN", property names: Cherry Grove, Creekhead Cove, Chimney Ridge, Luttrell & 3rd); canonical URLs on blunovainc.com; full OG + Twitter card meta; multiple JSON-LD blocks per page (RealEstateListing/Residence with `amenityFeature`, ItemList on the hub, breadcrumbs); `<link rel="preload">` for the page's Mavo JSON; real photography (no stock), URL-safe directory names (never `#` or spaces).

## Phased build order (mirrors the real history)

1. **Bootstrap** (era of `433ae72`): plain static multipage site with embedded CSS; nav/footer skeletons; one sample listing page.
2. **Mavo integration** (era of `504c37b`): add Mavo to every page, GitHub storage, author the JSON files, add "Mavo Editability Guide" documenting `property`/`mv-list`/`mv-list-item` → JSON mapping. Expect iteration on the storage schema (nested → flat; YAML → JSON: standardize on flat JSON, `16ac117`).
3. **Listings build-out** (era of `63886fb`, `0ee06f8`): duplicate the listing template to all four properties with unique Mavo apps; fullscreen gallery that survives Mavo re-render; real photo uploads with descriptive, URL-safe filenames.
4. **(Deliberate detour)** Rebuild one page with shadow-DOM web components (`93b14a3`), then revert (`18906e8`) — plain HTML + Mavo wins because shadow DOM is not Mavo-editable. Skip this in recreation, but keep the lesson: no abstraction layers that break in-browser editing.
5. **Contact** (era of `5500118`): Mavo-editable contact page, hosted form-wrapper, remove old mailto/Cloudflare remnants.
6. **Rebrand + polish sprint** (era of `fc10a91` → `222657d`): rewrite all metadata Nashville→Knoxville with real facts; JSON-driven home cards; roll the Luttrell lightbox/amenities pattern to all listings; fix `#`-in-path image directories (`9550f1a`); add the contact-form spam keyword filter (`d3c7e0b`); add `sitemap.xml`; strip fake phone/address/hours/social links for email-only contact.
7. **Docs**: README, AGENTS.md, CHANGELOG, this prompt, architectural diary.

## Acceptance criteria

- `python3 -m http.server` on the repo root serves a fully working site; every page loads with images, fonts, icons, gallery, and analytics.
- Logging into Mavo on any page and saving produces a JSON diff in the repo for that page's app only.
- Adding a new listing requires only: new JSON file + new page with its own `mv-app`, a `propertyCard` entry, and a `sitemap.xml` line.
- No build tools, no secrets, no fake contact data, no broken image URLs, no `[link]` placeholders in shipped nav.
- Lighthouse-friendly basics: unique titles/descriptions, canonical, OG/Twitter, JSON-LD, sitemap.
