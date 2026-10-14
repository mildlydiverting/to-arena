# CLAUDE.md

Guidance for Claude Code when working in this repo.

## First action, always

If the user's task matches a plan under `docs/plan-*.md`, read that plan before anything else — before searching the code, before reading other files, before planning. The plan is the spec; don't improvise around it.

If no plan file matches the task, say so and ask whether to create one before coding.

## How to work in this repo

- **Ask before each commit.** State what you're about to change in two or three sentences and wait for a yes. No surprise edits.
- **Tests before implementation** for anything in `arena.js`. Run both files after every change:
  ```bash
  node tests/import.test.mjs
  node tests/export.test.mjs
  ```
- **Small commits** on the current feature branch. Never commit to `main`. Never push, never merge, never force. Short imperative subject lines. No co-author trailers.
- **Backward compatibility is non-negotiable.** New options must default to current behaviour. Do not rename, reshape, or refactor anything that isn't required by the task on the plan.
- **If the plan doesn't cover it, stop and ask.** Don't invent.

## Project constraints

- **are.na API v3 only** (`https://api.are.na/v3`), always via the existing `ArenaClient` so rate limiting still applies. No direct `fetch` calls against are.na.
- **No build step, no dependencies.** Plain HTML, CSS and JavaScript — same as the rest of the project.
- **Design language is set.** Reuse existing classes: `.row`, `.check`, `.choice`, `.btn`, `.list`, `.toolbar`, `#filter` pattern. No new fonts, palette, or spacing scale. Arial everywhere, matching the latest commit on `main`.
- **British English** in any user-facing strings or new comments.

## Scope rules

- The browser-side export scripts (`cosmos-export.js`, `pinterest-export.js`, `export-kit.js`) and OAuth files (`oauth.*`) are off-limits unless the task names them explicitly.
- "Possible enhancements" sections in plan docs are context, not work. Do not build them.

## When finishing a plan

Run the tests one more time. Give a short summary of what changed, what's covered, and anything still open against the plan.
