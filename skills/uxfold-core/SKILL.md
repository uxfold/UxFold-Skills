---
name: uxfold-core
description: House rules for any UxFold Lab project. Use when starting work, scaffolding a screen, editing UI, or when the user mentions tokens, Tune, components, preview, or handoff. Applies to every coding agent.
license: MIT
metadata:
  origin: uxfold
  version: "1.1"
---

# UxFold core

Read `AGENTS.md` first. This skill is the short procedure on top.

## Before you edit UI

1. Find the tokens file named in `AGENTS.md`. Prefer CSS variables over hardcoded values.
2. Find an existing component that already does this job. Reuse it.
3. If the user selected an element in Lab, scope the change to that element unless they said the token or component should update everywhere.

## While you edit

- Never add, edit, copy or remove `data-uxf-id` attributes. UxFold Lab manages them. Leave them exactly where they are when you change markup, and never strip them with a search-and-replace or `sed`.
- Keep the change small. One intent per edit.
- Do not introduce a second visual language (new radius scale, new typeface, new primary colour) unless the user asked to restyle the system.
- If you add UI, add the states that UI needs — empty, loading, error, disabled — or write why they are out of scope in `docs/handoff.md`.

## After you edit

- Confirm the preview still compiles.
- If Playwright CLI is installed, snapshot the changed route. If it is not installed, skip and say so in one line.
- Do not claim done until the file you intended to change is the file that changed.

## Missing tools

If the user asks for Figma, browser QA, or a plugin you cannot see, name the missing tool and the install hint from `skills-catalogue.json`. Then do the parts that do not need it.
