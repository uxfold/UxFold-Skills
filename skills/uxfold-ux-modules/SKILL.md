---
name: uxfold-ux-modules
description: Route UX questions to selected modules of the szilu ux-designer skill. Use when designing or reviewing UI and the project has ux-designer installed, or when the user names a topic such as forms, tables, accessibility, onboarding, or search. Works with any coding agent.
license: MIT
metadata:
  origin: uxfold
  version: "1.0"
  wraps: https://github.com/szilu/ux-designer-skill
---

# UX designer modules

The full [szilu/ux-designer-skill](https://github.com/szilu/ux-designer-skill) is large on purpose. This project may only have ticked some modules.

1. Read `docs/ux-modules.json` if it exists. That file lists the module ids the designer enabled.
2. If the file is missing, treat the full set as enabled.
3. Load only the matching files under the installed `ux-designer/references/` folder.
4. Follow that skill’s review and build workflows. Do not copy the reference text into chat.

## Module ids

See `ux-designer-modules.json` in this pack for the picker list. Ids match the upstream file names without the number prefix where possible.

If the user asks for a topic that is not enabled, say which module would cover it and offer to turn it on. Do not load disabled modules on your own.
