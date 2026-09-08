# 008 — Knoxville rebrand, JSON-driven property cards

- **Date:** 2025-12-18
- **Commits:** `fc10a91` (refactor(home): rebrand metadata to Knoxville, cards from JSON), `621ae9f` (docs(home): rewrite hero copy and property card text), `aee212d`/`8d0a993` (price badge styling)

## Context

The site's metadata still carried Nashville placeholder content — a fake address, phone, office hours, wrong geo coordinates — while the actual properties are in Knoxville. The home page also hardcoded one property's card in HTML.

## Decision

Rewrite titles, descriptions, keywords, OG/Twitter, and JSON-LD from Nashville to Knoxville with real property facts; drop the fake address/phone/office-hours metadata. Convert the home page's property cards into a Mavo-templated card bound to the `propertyCard` list in `blunova-home.json`, so adding a listing means editing JSON, not HTML.

## Alternatives

- **Keep per-page hardcoded cards** — rejected: drift between pages (already visible in the 2024 history).
- **Generate cards from the per-property JSON files** — rejected for the home page: Mavo binds one storage per app; cross-file aggregation isn't supported, so a dedicated `propertyCard` list on the home app is the pragmatic model.

## Consequences

- Listing additions/edits on the home page are content changes (`blunova-home.json`) the owner can make in Mavo.
- Property facts are now stored in two places (home JSON cards + per-property JSON/meta), which the December sprint had to keep correcting (e.g. Chimney Ridge bed/bath counts in `a7d5051`, `f0e3652`) — a standing sync burden documented in AGENTS.md.
- One later Mavo save (`11ca0b36`→rewritten) accidentally dropped the `image`/`link` fields from the cards, showing the fragility of editor-driven saves against hand-shaped schemas.
