# Claude SDLC Kit

A reusable, stack-agnostic SDLC quality framework for Claude Code projects. Drop it into any project and get a full AI-powered development team out of the box.

---

## What is this?

This kit gives you a full team of AI agents that automatically review your work after every task — so you get senior-level quality checks without needing a team.

One agent (the **Architect**) acts as the orchestrator. After every task, it reads what changed and decides which specialists to call. You never have to think about it.

---

## The team

| Skill | Role | Source |
|---|---|---|
| `/architect` | Orchestrator — decides which skills to run after every task | This repo |
| `/verify` | QA — confirms the change actually works | Built-in |
| `/ux` | UX Designer — reviews any user-visible change | Built-in |
| `/swe` | Backend Engineer — reviews routes, logic, data models | Built-in |
| `/security-review` | Security Auditor — auth, payments, user data, schema | Built-in |
| `/test` | Test Engineer — writes and validates tests | This repo |
| `/performance` | Performance Engineer — catches costly or slow patterns | This repo |
| `/simplify` | Code Health — cleans up over-edited files | Built-in |
| `/review` | Release Manager — pre-deployment sign-off | Built-in |
| `/pm` | Project & Product Manager — milestones, timeline, priorities | This repo |

**Built-in** = already available in Claude Code, no setup needed.
**This repo** = installed by following the steps below.

---

## How to install in any project (step by step)

> **You need:** VS Code + the Claude Code extension installed and open.

### Step 1 — Open your project in VS Code

Open the folder of the project you want to add the SDLC kit to.

### Step 2 — Open the terminal inside VS Code

Press **Ctrl + `** (the backtick key, top-left of your keyboard, under Escape).

A terminal panel will open at the bottom of VS Code.

### Step 3 — Run this command

Copy and paste the line below into the terminal, then press **Enter**:

```
git clone https://github.com/Davidmerzel/SDLC_KIT.git _sdlc_tmp; Copy-Item -Recurse _sdlc_tmp\.claude .\; Remove-Item -Recurse -Force _sdlc_tmp
```

This will:
- Download the kit from GitHub
- Copy the `.claude/commands/` folder into your project
- Delete the temporary download

### Step 4 — Add the standing instructions to your CLAUDE.md

Open (or create) a file called `CLAUDE.md` in the root of your project.

At the very top, paste the following block:

```
## Standing instructions

After completing any implementation task, ALWAYS run `/architect`. It reads what changed and selects only the relevant skills from the 9 available — then shows what it chose and why it skipped the rest.

Available skills the architect orchestrates:

| Skill | Role |
|---|---|
| `/verify` | QA — does it work |
| `/ux` | UX Designer — any user-visible change |
| `/swe` | Backend Engineer — routes, data models, logic |
| `/security-review` | Security gate — auth, payments, user data, schema |
| `/test` | Test Engineer — backend logic, API endpoints, critical flows |
| `/performance` | Performance Engineer — API calls, queries, parallelism |
| `/simplify` | Code Health — over-edited or patchy files |
| `/review` | Release Manager — batch push to production |
| `/pm` | Project & Product Manager — milestones, timeline, priorities |

Never run all 9 by default. `/architect` decides. Individual skills can still be called directly on demand.
```

### Step 5 — Tell Claude to activate the kit

In the Claude Code chat, type:

> *"The SDLC kit is in place. Please read CLAUDE.md and adapt the commands to this project's stack."*

Claude will read the project context and tailor each command to your specific technology. You are done.

---

## How it works day-to-day

- You describe what you want to build or fix.
- Claude implements it.
- Claude automatically runs `/architect`, which reads what changed and calls only the relevant agents.
- You see a transparent report: what was checked, what was skipped, and why.
- You never have to remember which skill to run.

---

## Calling skills directly

You can always call any skill manually by typing it in the Claude chat:

- `/pm` — get a project status and priority check at any time
- `/simplify` — clean up a specific file
- `/review` — request a pre-deployment review

---

## Design principles

- **Stack-agnostic** — no technology names in the commands. Claude reads the project and adapts.
- **No review fatigue** — the Architect runs only the skills the specific change warrants.
- **Transparent decisions** — the Architect always explains what it ran and what it skipped, and why.
- **Solo-developer friendly** — designed for one person with no-code or low-code experience who wants senior-team quality output.
