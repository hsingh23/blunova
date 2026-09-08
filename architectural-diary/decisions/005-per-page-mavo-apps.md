# 005 — One Mavo app + JSON file per page

- **Date:** 2024-08-18 → 2024-08-19
- **Commits:** `63886fb` (feat: Fix gallery fullscreen after Mavo render; add property pages), `0ee06f8` (fix: Give new property pages unique Mavo apps and working fullscreen), plus the `blunova-*.json` creation commits (`d6a08a36`→`d6a08a3` new: feat: add blunova-luttrel.json property content file, etc.)

## Context

The first cut of the new property pages (Chimney, Creekhead) reused the Cherry Grove Mavo app verbatim, so saves from one page overwrote another page's data, and the fullscreen gallery broke after Mavo re-rendered the DOM.

## Decision

Give every page its own Mavo app name and its own storage file: `blunova-home`/`blunova-home.json`, `blunova-cherryGrove`/`blunova-cherryGrove.json`, `blunova-chimney`, `blunova-creekhead`, `blunova-luttrel` (single-l typo preserved for compatibility), `blunova-contact`, and `blunovaAbout-bup3s7` for the about page. Re-bind gallery JS to work on Mavo-rendered content.

## Alternatives

- **One shared app with a page key** — rejected: Mavo has no router concept; cross-file storage is awkward and error-prone.
- **Home page aggregates everything** — rejected: one giant JSON invites save conflicts between pages.

## Consequences

- Content ownership is unambiguous: to edit Chimney Ridge content, edit/save `blunova-chimney.json` via its page.
- Shared sections (header/footer) are duplicated in each file and each page's HTML.
- The `blunova-luttrel.json` filename typo is frozen in place — renaming it requires updating the luttrell page binding and migrating the file.
- The about page's app has no tracked JSON file yet (see AGENTS.md gotchas).
