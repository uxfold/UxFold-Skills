---
name: uxfold-ux-modules
description: Route UX questions to selected modules of the szilu ux-designer skill. Use when designing or reviewing UI and the project has ux-designer installed, or when the user names a topic such as forms, tables, accessibility, onboarding, or search. Works with any coding agent.
license: MIT
metadata:
  origin: uxfold
  version: "1.1"
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

## When a request needs a module that is off

Check this before any other step, including reading files or writing code. If the request falls in a module that is not listed in `docs/ux-modules.json` (for example "help me design a data table" when Data tables is off), **stop and do no work yet**. Ask, in these words, naming the module by its topic:

> The <Module> module is off for this project. How do you want to go?
> 1. Turn on <Module> and use it
> 2. Continue with general good practice
> 3. Give me your own direction

Then wait for the answer. Do not start the task while you wait, and do not pick an option for the designer.

- **1** — add the module id to the `modules` list in `docs/ux-modules.json`, add the module's name to the `ux-designer modules:` line in `AGENTS.md`, load that module's file, then do the task with it.
- **2** — do the task with general good practice. Do not load the module and do not change either file.
- **3** — follow the designer's direction instead.

Never load a disabled module on your own.
