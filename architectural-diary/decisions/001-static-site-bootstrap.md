# 001 — Static HTML site, no build system

- **Date:** 2024-07-07
- **Commits:** `433ae72` (feat: add initial static site for BluNova Properties), `3afeba83` (feat: add Cherry Grove listing page), `097a8df` (fix links)

## Context

Blunova Properties needed a web presence for its rental homes with zero budget for infrastructure or maintenance. The site would be updated infrequently by a single developer.

## Decision

Build a purely static, multi-page website: one HTML file per page with embedded CSS, fonts and icons from CDNs, and no build system, bundler, or package manager at all.

## Alternatives

- **WordPress / hosted site builder** — rejected: hosting cost, maintenance, and update overhead.
- **Static site generator (Hugo, Astro, Next)** — rejected: a build step would later conflict with Mavo's model of editing the deployed HTML directly; also more tooling than needed for ~8 pages.
- **SPA framework** — rejected: worse SEO for a listings site and unnecessary complexity.

## Consequences

- Deploying is just pushing to `main` (GitHub Pages); nothing can break in a build because there is none.
- CSS is duplicated across pages, so style changes must be replicated by hand — accepted for a site this size.
- The codebase stayed approachable enough that a client-side CMS (Mavo, decision 002) could be layered on later without refactoring.
