# Claude SDLC Kit

A reusable, stack-agnostic SDLC quality framework for Claude Code projects. Drop it into any project and get a full AI-powered development team out of the box.

## What's included

| File | Role |
|---|---|
| `.claude/commands/architect.md` | Orchestrator — runs after every task, decides which skills are needed |
| `.claude/commands/test.md` | Test Engineer — writes and validates tests for any stack |
| `.claude/commands/performance.md` | Performance Engineer — catches costly patterns before production |
| `CLAUDE-standing-instructions.md` | Ready-to-paste standing instructions block for CLAUDE.md |

The other 5 skills (`/verify`, `/ux`, `/swe`, `/security-review`, `/simplify`, `/review`) are built into Claude Code — no setup needed.

## Full skill roster

| Skill | Role | Source |
|---|---|---|
| `/architect` | Orchestrator | This repo |
| `/verify` | QA — does it work | Built-in |
| `/ux` | UX Designer | Built-in |
| `/swe` | Backend Engineer | Built-in |
| `/security-review` | Security Auditor | Built-in |
| `/test` | Test Engineer | This repo |
| `/performance` | Performance Engineer | This repo |
| `/simplify` | Code Health | Built-in |
| `/review` | Release Manager | Built-in |
| `/pm` | Project & Product Manager | This repo |

## How to apply to a new project

**Step 1** — Copy the commands folder into the project root:
```
your-project/
  .claude/
    commands/
      architect.md
      test.md
      performance.md
```

**Step 2** — Open the project's `CLAUDE.md` (create one if it doesn't exist) and paste the contents of `CLAUDE-standing-instructions.md` at the top.

**Step 3** — Tell Claude: *"I've added the SDLC kit — please read CLAUDE.md and confirm the architect is active."*

That's it. Claude will adapt each command to the project's stack automatically by reading the project context.

## Design principles

- **Stack-agnostic** — no technology names in the commands. Claude reads the project and adapts.
- **No review fatigue** — `/architect` runs only the skills that the specific change warrants.
- **Transparent decisions** — architect always explains what it ran and what it skipped, and why.
- **Solo-developer friendly** — designed for one person with no-code or low-code experience who wants senior-team quality output.
