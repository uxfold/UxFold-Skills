---
name: uxfold-figma-push
description: Push live screens to Figma as frames or components. Use when the user says push this screen to Figma, send frames to Figma, sync this flow to the design system, or make a Figma file from this project. Works with any agent that can call Figma MCP. Degrade if Figma is not connected.
license: MIT
metadata:
  origin: uxfold
  version: "1.0"
---

# Push screens to Figma

This skill is the interviewer and the mapping policy. Official Figma skills (`figma-use`, `figma-generate-design`, `figma-generate-library`, `figma-code-connect`, `figma-create-new-file`) are the hands. Do not rewrite those.

If Figma MCP (or the equivalent Figma connection) is not available, print the connect steps the user needs for their agent and stop. Do not invent a `.fig` file.

Speak as “the agent”. This is not Claude-only.

## Gate 0 — ask what is missing

Ask only the questions the user did not already answer.

1. Target — existing Figma file URL, or create a new file?
2. Mode — pick one:
   - **A. Frames only** — one frame per route and state. Fast. No components.
   - **B. New local components** — detect repeats, create components in this file, instance the rest.
   - **C. Published team library** — use a published library and Code Connect when it exists.
   - **D. Existing local components** — reuse components that already live in the target file, even if they were never published to a team library.
3. Breakpoints — desktop only, or desktop + tablet + mobile?
4. Scope — current selection, current route, or every route on the canvas?
5. Naming — match the route, or match names already in the Figma file?

Do not start mode C if there is no linked published library. Offer D or B instead.

Mode D is the common case. A file full of unpublished local components is still a design system for this file. Search that file first. Only create a new component when nothing in the file is close enough.

## Gate 1 — repeat detection

Do this before drawing. Any agent that skips it will draw ten buttons instead of one component.

Scan the selected screens and the source:

- Same component file imported in many places → one Figma component.
- Same primitive with only the label different (primary button, icon button) → one component plus a text property.
- Same layout mapped over a list → one component. Ask “this row only, or all of them?”
- Two different files that only look the same → ask. Do not silently merge.

Then confirm, if the user did not already pick a mode:

> I found these repeats — Primary button × 18, Icon button × 11, List row × 9, Card × 6.
> A frames only, B new local components, C published library, or D reuse local components already in the Figma file?

## Gate 2 — mapping (modes B, C, D)

Build a table before write-back.

| Code | Figma candidate | Action |
| --- | --- | --- |
| Exact Code Connect match | that component | instance it, never redraw |
| Same name in the file (mode D) | local component | instance it after the user nods if the match is fuzzy |
| Published library match (mode C) | library component | instance it |
| Close but not equal (padding, radius, type size differ) | — | stop and tell the user |
| No match | — | mode B create local, tag `UNMAPPED` |

On a mismatch offer exactly three choices:

1. Use the existing Figma component and accept the visual drift
2. Make a local variant named after this project (example `Primary / Lab`)
3. Leave this node as a raw frame

Never “almost” swap a primary button.

## Write rules

- Prefer instances over rectangles.
- Bind colour, type, and space to variables when they exist. No raw hex if a variable is there.
- Auto layout. No free x/y unless the user asked for pixel-exact prototype polish.
- One frame = one route + one breakpoint + one state. Hover and error are sibling frames or variants, not extra layers hidden on the happy frame.
- Do not publish to a team library unless the user said publish. Local stays local.
- After write, list what was instanced, what was created, and what was left as frames. If you can screenshot the Figma page and the live preview, do that and list diffs.

## Official skills to call

Use whatever equivalent the current agent has:

- create file → `figma-create-new-file`
- draw / instance / variables → `figma-use`
- whole screen from code + library → `figma-generate-design`
- library from codebase → `figma-generate-library`
- code ↔ Figma names → `figma-code-connect`

This skill decides mode, mapping, and when to stop. Those skills move pixels.
