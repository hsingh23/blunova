# 002 — Mavo as the CMS, GitHub as storage

- **Date:** 2024-08-19
- **Commits:** `504c37b` (feat: Add Mavo.js for dynamic content editing and uploading images)

## Context

The site owner needed to update copy, photos, and listings without editing HTML or asking a developer. There is no server, so a traditional admin panel was not an option.

## Decision

Load Mavo (CSS + JS from `get.mavo.io`) on every page and declare `mv-app` + `mv-storage="https://github.com/hsingh23/blunova"` on the page root. Editors open the live site, authenticate with GitHub, edit in place, and Mavo commits the changes (JSON files, uploaded images) back to the repository.

## Alternatives

- **Headless CMS (Contentful, Sanity)** — rejected: requires JS rendering or a build step to inject content into static HTML.
- **Netlify/Decap CMS admin** — rejected: ties the site to a specific host and adds an admin surface to maintain.
- **Manual PRs from the owner** — rejected: too slow for content tweaks (prices, descriptions, photos).

## Consequences

- Content lives in versioned `blunova-*.json` files alongside the HTML; history of every content edit is in git.
- Much of the 2024-08 history consists of Mavo auto-save commits ("Updated blunova-home.json"), including three commits that were accidentally empty.
- The site depends on Mavo staying available from its CDN and on the owner's GitHub token permissions.
- A companion guide (`Mavo Editability Guide.md`) was later added so both humans and LLMs can extend the bindings correctly.
