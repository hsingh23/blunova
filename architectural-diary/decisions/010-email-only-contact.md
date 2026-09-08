# 010 — Email-only contact, footer cleanup

- **Date:** 2025-12-19
- **Commits:** `9d1a5dd` (fix: remove placeholder phone/address and standardize on email contact), `b7f83fa` (style: polish quick-contact email link and remove office hours card), `222657d` (fix: Remove social links from multiple pages for a cleaner footer design), `10f6308` (style: normalize formatting of new email links and JSON)

## Context

The site displayed a placeholder phone number, a fictitious Nashville street address, office hours, and social-media links that either pointed nowhere ("#") or to profiles the business did not maintain. For a real business, fake contact data is a trust and liability problem.

## Decision

Remove all of it and standardize on a single contact channel: email (info@blunovainc.com / the address configured in `blunova-contact.json`). Phone card, "Call Now" quick action, address lines, office-hours card, and the social-links footer blocks (plus their CSS and `sameAs` JSON-LD) were deleted across all eight pages; mailto links were styled inside the quick-contact card.

## Alternatives

- **Publish real phone/hours** — not chosen at the time (owner preferred email-first contact); the decision is easily reversible by re-adding the blocks.
- **Keep social links with real profiles** — rejected: no maintained profiles existed.

## Consequences

- The footer is cleaner and nothing on the site is untrue; the JSON-LD `sameAs` arrays were removed to match.
- Contact conversion funnels entirely through email and the form-wrapper form (decision 006).
- Dead nav links to not-yet-existing pages (apply, FAQ, tenant portal, etc.) remain in markup as placeholders — documented in AGENTS.md as intentional future slots.
