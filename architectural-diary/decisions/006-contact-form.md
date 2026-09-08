# 006 — Hosted form-wrapper + client-side spam filter

- **Date:** 2024-08-19 and 2025-12-18
- **Commits:** `5500118` (feat: make contact page Mavo-editable and expand property data), `d3c7e0b` (feat(contact): block SEO-scam spam submissions on contact form)

## Context

The contact page originally used a plain GET form and a Cloudflare-protected mailto. In 2024 it was rebuilt as a Mavo-editable page; a submission backend was still needed, and by late 2025 the form was receiving automated SEO-scam pitches ("pay per click", "Google's 1st page", ...).

## Decision

1. Use a hosted form service via a `<form-wrapper data-form-id="[formId]">` element loaded from `web.celeritytechconsulting.com/form-wrapper.js` — no backend of our own, no form secrets in the repo.
2. Block scam submissions client-side: a capture-phase submit listener checks the message field against a keyword list and calls `preventDefault`/`stopImmediatePropagation` before form-wrapper can send.

## Alternatives

- **Formspree/Netlify Forms** — available, but the hosted wrapper was already in place from the 2024 rebuild.
- **Server-side filtering / captcha** — impossible (no server) and heavier than needed for keyword spam.

## Consequences

- The form works with zero infrastructure; the repo contains no API keys.
- Spam filtering is trivially bypassable by a determined bot (client-side only) — accepted trade-off, reviewed again if volume grows.
- The `data-form-id` is still the placeholder `[formId]`, so the live form's ID must be configured in the markup when the endpoint changes (a gotcha noted in AGENTS.md).
