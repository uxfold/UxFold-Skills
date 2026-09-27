---
name: uxfold-principles
description: Apply UxFold product-design principles when building or reviewing screens. Use for new screens, redesigns, critiques, trust, scope, heuristics, patterns, desirability, feasibility, or scalability. Works with any coding agent.
license: MIT
metadata:
  origin: uxfold
  version: "1.0"
---

# UxFold principles

Run these as tests, not essays. Load a reference file only when that test needs detail.

- Enterprise vs consumer patterns — `references/pattern-catalogues.md`
- Heuristic score sheet — `references/heuristics.md`

Read `AGENTS.md` for product type. If it says enterprise, use the enterprise catalogue. If it says consumer, growth, or marketing, use the consumer catalogue. If unclear, ask once.

## 1. Aesthetic-usability (does this look finished enough to trust)

Fail the screen if any of these are true:

- Mixed radii, type sizes, or colours that are not tokens
- No empty / loading / error treatment on a data view
- Weak hierarchy (everything the same weight)
- Misaligned groups, cramped tap targets, leftover placeholder copy

Fix the visual system first. Users forgive small usability gaps on a screen that looks cared for. They do not forgive a screen that looks unfinished.

## 2. Pareto (the 20 percent)

Before adding UI, name the one or two jobs that carry most of the value. Build those. Put the rest through the MoSCoW skill (or a Must / Should / Could / Won’t list if that skill is not installed).

## 3. Heuristics

If the user asked for a review or the screen is a new flow, score it with `references/heuristics.md`. Output a table — heuristic, severity (blocker / major / minor), where, fix. Do not write a lecture.

## 4. Parkinson (do not fill the time)

If the ask is broad (“a dashboard”, “settings”, “admin”), propose a time-boxed slice — one primary action, one supporting list — and wait. Do not invent twelve widgets to look complete.

## 5. Pattern catalogue

Match the product type to `references/pattern-catalogues.md` and reuse those patterns. Do not dress an enterprise table like a consumer onboarding, or the reverse.

## 6. Desirability, feasibility, scalability

For any non-trivial feature, write three lines into the reply or into `docs/handoff.md`:

- Desirable — whose job is this, and what does success look like for them?
- Feasible — do we already have the component, the data, and the permission model?
- Scalable — what breaks at 10× users, 10× rows, or a second language?

## 7. Scale angles (product, not infra theatre)

Call out only what the current screen needs — pagination vs a short list, search vs browse, roles, string length, empty catalogues, light/dark tokens, list performance. Skip the rest.
