# Standing Instructions (paste into any project's CLAUDE.md)

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
