# 004 — Web components tried, reverted

- **Date:** 2024-07-07 (committed in that era's branch of history; landed with the 2024-07-07 commits `93b14a3` and `18906e8`)

## Context

Mid-build, Cherry Grove's page was rebuilt with custom elements (`<app-header>`, `<property-hero>`, `<property-details>`, `<image-gallery>`) using shadow DOM and slots, moving the fullscreen viewer into an `ImageGallery` component and dropping the page-level gtag script.

## Decision

Revert the entire web-components rebuild (`18906e8`) and restore the plain-HTML Mavo-annotated page.

## Alternatives

- **Keep the component version** — rejected: shadow DOM fights Mavo's attribute-based editing (content inside shadow trees is not editable/saved by Mavo), and duplicating the pattern across four property pages would multiply the maintenance cost.
- **Componentize only the gallery** — rejected as not worth a mixed architecture for one widget.

## Consequences

- The codebase's architecture rule was reaffirmed: plain HTML + Mavo attributes, duplicated per page, beats abstraction that breaks in-browser editing.
- The custom lightbox (decision 007) is therefore copy-pasted JS on each property page — accepted duplication.
- The revert intentionally lost the gtag removal, so analytics stayed on all pages.
