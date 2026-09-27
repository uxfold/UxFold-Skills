```
╭─────────────────────────────────────────────────────────────╮
│                                                              │
│      ██╗   ██╗██╗  ██╗███████╗ ██████╗ ██╗     ██████╗       │
│      ██║   ██║╚██╗██╔╝██╔════╝██╔═══██╗██║     ██╔══██╗      │
│      ██║   ██║ ╚███╔╝ █████╗  ██║   ██║██║     ██║  ██║      │
│      ██║   ██║ ██╔██╗ ██╔══╝  ██║   ██║██║     ██║  ██║      │
│      ╚██████╔╝██╔╝ ██╗██║     ╚██████╔╝███████╗██████╔╝      │
│       ╚═════╝ ╚═╝  ╚═╝╚═╝      ╚═════╝ ╚══════╝╚═════╝       │
│                                                              │
│              S  K  I  L  L  S                                │
│                                                              │
│         code is the design file                              │
│         one AGENTS.md · any agent                            │
│                                                              │
╯─────────────────────────────────────────────────────────────╯

        ┌─────────┐     ┌─────────┐     ┌─────────┐
        │  Lab    │────│ Skills  │────│  Repo   │
        │  picker │     │  pack   │     │ + agent │
        └─────────┘     └─────────┘     └─────────┘
              │               │               │
              │               │               ▼
              │               │        tokens · screens
              │               │        IA · handoff
              │               │        Figma frames
              ▼               ▼
           tick what      copy what
           you need       the agent
                          should know
```

# UxFold Skills

The instruction pack a new [UxFold Lab](https://github.com/uxfold/UxFold-Lab) project starts with.

This is not a design tool. It is a set of small skill folders and a tick-list. When a designer creates a project in Lab, the agent they already pay for — Claude Code, Codex, OpenCode, Cursor, Gemini, Grok, or anything else that reads skills — already knows how this team designs.

One file is the source of truth: `templates/AGENTS.md`.  
`templates/CLAUDE.md` only points at it, so Claude Code does not get a private set of rules.

---

## House skills

| Skill | What the designer gets |
| --- | --- |
| `uxfold-core` | Tokens first. Reuse components. Preview must still compile. |
| `uxfold-principles` | Trust, Pareto, heuristics, Parkinson, enterprise vs consumer patterns, desirability / feasibility / scale. |
| `uxfold-ia` | Writes `docs/ia.md` and `docs/ia.drawio`. |
| `uxfold-funnel` | TOFU / MOFU / BOFU — or acquire / activate / habit. |
| `uxfold-moscow` | Must / Should / Could / Will-not. |
| `uxfold-handoff` | A note engineering can actually use. |
| `uxfold-figma-push` | Push screens to Figma as frames, new local components, existing local components, or a published library. |
| `uxfold-ux-modules` | Only load the ux-designer topics the designer ticked. |

Default-on in a new project: **core**, **principles**, **handoff**.  
The rest stay off until someone ticks them.

---

## Community skills (optional ticks)

These stay as install commands. Lab does not vendor their code.

- Anthropic `frontend-design` — anti-slop UI
- Taste-skill — art direction
- Vercel web-design-guidelines and writing-guidelines
- content-designer ux-writing
- szilu ux-designer, with a module picker (`ux-designer-modules.json`)
- ponytail — do less, reuse what exists
- image-to-code
- Playwright CLI
- Superpowers and claude-mem (Claude Code plugins)

The full list, with install lines and on/off defaults, lives in `skills-catalogue.json`. That file is what UxFold Lab’s New Project picker reads.

---

## How a new project should look

```
your-project/
  AGENTS.md                 ← facts for every agent
  CLAUDE.md                 ← “read AGENTS.md”
  DESIGN.md                 ← optional style
  docs/
    ia.md
    ia.drawio
    funnel.md
    scope.md
    handoff.md
    ux-modules.json         ← if ux-designer was ticked
  .agents/skills/           ← Codex, OpenCode, others
  .claude/skills/           ← Claude Code (same files)
```

Copy each ticked house skill into **both** skill folders. Same instructions, two discovery paths.

---

## Figma push, in one glance

```
  Gate 0                         Gate 1                    Gate 2
  what is missing?               find the repeats          map, then write
 ┌────────────────────┐       ┌─────────────────┐      ┌─────────────────┐
 │ A  frames only      │       │ 10 buttons  = 1  │      │ instance first   │
 │ B  new local comps  │  ──▶  │ component?       │ ──▶  │ never “almost”   │
 │ C  published library│       │ this row or all? │      │ stop on mismatch │
 │ D  comps already in │       └─────────────────┘      └─────────────────┘
 │    this Figma file  │
 └────────────────────┘
```

D is the usual case. A Figma file full of unpublished local components is still a system for that file. Search it before drawing new ones.

---

## For Lab

See `HOW-TO-USE.md` for where each file goes. The short version:

1. Point Lab’s New Project picker at `skills-catalogue.json`.
2. Copy `templates/AGENTS.md` and `templates/CLAUDE.md` into every scaffolded repo.
3. Copy ticked `skills/uxfold-*` folders into `.agents/skills` and `.claude/skills`.
4. Run the catalogue `install` line only for community skills that were ticked.

Do not overwrite an `AGENTS.md` the designer already wrote.

---

MIT. Built for [UxFold Lab](https://github.com/uxfold/UxFold-Lab).
