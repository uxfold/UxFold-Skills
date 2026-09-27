---
name: uxfold-handoff
description: Package a developer handoff from the live prototype. Use when the user says handoff, visual explainer, write the PR, give this to engineering, or ship notes. Works with any coding agent.
license: MIT
metadata:
  origin: uxfold
  version: "1.0"
---

# Developer handoff

Write `docs/handoff.md`. If the user also asked for a GitHub PR, use that file as the PR body.

## Collect

1. What changed — files, tokens, new vs reused components
2. States designed — default, hover, disabled, loading, empty, error
3. What was explicitly out of scope
4. How to run the preview and any test command from `AGENTS.md`
5. Accessibility notes if the web-design-guidelines skill ran
6. Copy notes if a writing skill ran

## Screenshots

If Playwright CLI is available, snapshot each changed route and link the images from `docs/handoff.md`. If it is not available, list the routes and say screenshots were skipped.

## Do not

- Do not invent backend contracts the prototype does not have. Mark them as assumptions.
- Do not tell engineering to “just make it pixel perfect” without the token file path and the component names.
- Do not paste the whole codebase. Link paths.

## `docs/handoff.md` shape

```md
# Handoff

## Intent
## What changed
## Components (reused / new)
## Tokens touched
## States
## Assumptions
## Out of scope
## How to run
## How to verify
```
