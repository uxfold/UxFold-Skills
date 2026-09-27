---
name: uxfold-moscow
description: Scope work with Must Should Could Will-not. Use for MVP, roadmap, what to build first, scope cuts, or when the user says MoSCoW. Works with any coding agent.
license: MIT
metadata:
  origin: uxfold
  version: "1.0"
---

# MoSCoW

Write or update `docs/scope.md`.

## Buckets

- Must — the product fails without this in the current slice
- Should — important, but the slice still works if it slips
- Could — nice if cheap
- Will not (this slice) — parked on purpose, with a one-line reason

## Rules

- Every item needs a reason. “Nice to have” is not a reason.
- Tie Must items to the Pareto jobs from uxfold-principles when that skill is installed.
- Parkinson still applies — a long Must list is a failed slice. Cut until a designer can ship it in one sitting.
- Will-not is a decision, not a graveyard. Revisit only when the user reopens scope.

## `docs/scope.md` shape

| Item | Bucket | Reason | Depends on |
| --- | --- | --- | --- |
