# Agent instructions

This file is the source of truth for every coding agent that opens this repo.

## Product

- Code is the design file. Do not invent a parallel design tool.
- Prefer existing components and CSS variables (tokens). Do not add a one-off hex, font size, or radius if a token exists.
- If a value is hardcoded, offer to move it into the tokens file rather than editing it in one place.
- After a UI change the preview must still compile.

## Stack

Fill these in when the project is created:

- Framework:
- UI library:
- Tokens file:
- Preview command:

## Do / do not

- Do reuse a component that already exists.
- Do design empty, loading, error, and disabled states when you add a new view.
- Do not drag-reposition elements in a visual editor unless the user explicitly asked for UxFold Pro pixel polish.
- Do not copy or duplicate nodes that come from a list or `.map()` loop unless the user said “this one only” or “all of them”.
- Do not add a new dependency when the platform, the UI library, or this repo already does the job.

## Skills

Project skills live in `.agents/skills/` (and a copy in `.claude/skills/` for Claude Code). Load a skill when the user ask matches its description. If a skill names a tool you do not have, say so and continue with the parts you can do.
