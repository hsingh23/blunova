# 003 — JSON (not YAML) for Mavo storage

- **Date:** 2024-08-17 → 2024-08-18
- **Commits:** `16ac117` (chore: store Mavo app data as JSON instead of YAML), `b36e2f6` (refactor: flatten Mavo schema, restore GitHub storage), plus a chain of schema-refactor commits (`5d24d54`, `8f8dd41`-era "refactor: Update blunova-home.json structure for links")

## Context

During the August 2024 build-out, Mavo's storage format and schema for the home page churned heavily: nested "detail" objects, duplicate fields, YAML vs JSON output, and a brief period where storage pointed elsewhere than the GitHub repo.

## Decision

Standardize on flat JSON files (`blunova-home.json`, later one per page) as Mavo storage, with `mv-storage` always pointing back at `https://github.com/hsingh23/blunova`. Keep schemas flat — no nested "detail" objects — so the HTML `property` bindings and the JSON keys match one-to-one. Notably, one early decision to model nav links as objects was flattened back to a simple array after it fought the markup.

## Alternatives

- **YAML storage** (Mavo default option) — tried and abandoned: the surrounding tooling (diff review, editors) worked better with JSON.
- **Nested/deep schemas** — tried and abandoned: harder to bind and to hand-edit; flattened in `b36e2f6`.

## Consequences

- Every page's content is a single, human-readable JSON file that doubles as the deployment data source.
- The link-array flattening saga is visible as several near-identical "structure for links" commits — the cost of discovering the right schema by iteration.
- Renaming a JSON file or its keys still silently orphans the page bindings (a standing gotcha documented in AGENTS.md).
