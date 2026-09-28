# UxFold skills pack

Drop-in files for UxFold Lab New Project. Written so any coding agent can use them — Claude Code, Codex, OpenCode, Cursor, Gemini CLI, Grok, or whatever the designer already pays for.

## What you copy where

| This folder | Goes into the new project as |
| --- | --- |
| `templates/AGENTS.md` | `AGENTS.md` at the repo root (source of truth) |
| `templates/CLAUDE.md` | `CLAUDE.md` at the repo root (one-line pointer so Claude Code reads the same rules) |
| `skills/*` that the designer ticked | `.agents/skills/<name>/` and `.claude/skills/<name>/` (same files, two discovery paths) |
| `skills-catalogue.json` | replace the file at the UxFold Lab repo root (drives the picker) |
| `ux-designer-modules.json` | used when the designer ticks **ux-designer** and then picks topics |
| `kkd-leaf-skills.json` | search index only — never the default tick list |

Third-party skills are **not** copied into this pack. The catalogue `install` line tells Lab (or the designer) how to fetch them.

## KKD rows in the picker

All three KKD repos, their plugins, their flow skills, and every leaf skill are **optional add-only**.

- `default: off` on every KKD row
- `visibility: search-only` — do not put them in the default New Project tick list
- Load `kkd-leaf-skills.json` (or the inclusive / practice splits) into the **search index only**
- When the designer types, match `name`, `description`, `group`, `parent`, `copiesFrom`, `tags`
- Show the matches as ticks. Install only what they tick. A pack tick does not silently tick its children.

Search hints: `kkd`, `kkd-flow`, `kkd-inc`, `kkd-prac`, `grill`, `inclusive`, `a11y`, `tokens`, `critique`.

## Agent-agnostic rules (every house skill follows these)

- Talk to “the agent”, never one vendor.
- If a tool is missing (Figma MCP, Playwright CLI, a plugin), say what is missing and stop or degrade. Do not pretend.
- Facts that are always true live in `AGENTS.md`. Procedures live in skills.
- Write project docs into `docs/`, not only into chat.
