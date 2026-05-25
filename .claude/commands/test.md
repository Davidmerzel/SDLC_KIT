# Test

Write and validate tests for any new or changed logic in this project. There may be no existing test suite — build incrementally, one unit at a time.

## Before writing tests

Read the project context (CLAUDE.md if present, or infer from the codebase) to identify:
- The language and runtime (Node.js, Deno, Python, etc.)
- The testing tools already in use (if any)
- Where test files should live (conventions in the project)
- Any deployment constraints that affect how tests can be run

If no testing stack exists, default to the lightest available option for the runtime — no heavy frameworks unless already present.

## Universal test categories

Apply these to every new or changed unit of logic, regardless of stack:

1. **Input validation** — missing, empty, or malformed inputs are rejected with a clear error before any expensive operation runs.
2. **Auth enforcement** — unauthenticated or unauthorised requests are blocked at the boundary.
3. **Error handling** — external failures (APIs, databases, file system) are caught and return a meaningful response, not a crash.
4. **Happy path** — correct input produces the expected output or side effect.
5. **Edge cases** — boundary values, empty results, maximum lengths, concurrent access where relevant.
6. **Isolation** — tests do not share state, do not hit production systems, and leave no residual data.

## How to run

Identify the correct run command for the project's stack and include it explicitly in the report.

## Report

Show: what was tested, which categories were covered, the result of running the tests, and any gaps. If a test fails, fix the root cause (route or test) before reporting done. If the project cannot run tests locally (e.g. serverless-only deployment), produce a manual verification checklist as a substitute.
