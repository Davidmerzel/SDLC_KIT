# Performance Review

Review changed code for performance issues. This is not a general optimisation pass — focus only on patterns that cause real problems at scale.

## Before reviewing

Read the project context (CLAUDE.md if present, or infer from the codebase) to identify the stack's specific constraints: database type, hosting limits, external API rate limits, concurrency model, and any known bottlenecks. Apply the checks below through that lens.

## Universal patterns to check

### External API calls
- Are independent calls made in **parallel** where possible, rather than sequentially?
- Are there **redundant calls** — the same endpoint called twice with the same input in one request?
- Is the **response size bounded** before being stored or passed downstream?
- Are **rate limit and failure responses** handled gracefully without cascading failures?

### Database / data access
- **N+1 queries** — a loop that fires one query per iteration. Replace with a single bulk query or JOIN.
- **Missing filters** — queries that scan the full dataset instead of filtering early.
- **Unbounded result sets** — no LIMIT or pagination on tables that grow over time.
- **Missing indexes** — frequently filtered or joined columns without an index.
- **Repeated identical queries** — same query fired multiple times in one request; cache in a local variable.

### Compute and blocking work
- **Synchronous blocking** in an async context — CPU-heavy work that blocks other requests.
- **Large serialisation** — returning or processing very large objects in a hot path.
- Operations that should be **deferred or queued** but are running inline in the request cycle.

### Frontend
- **Fetches on every render** instead of once on mount or on dependency change.
- **Large lists rendered without pagination** or virtualisation.
- **Assets (images, files) loaded without size constraints**.
- **Redundant re-renders** caused by unstable references or missing memoisation.

## Report

List each issue found with: location (file + approximate line), what the problem is, and the recommended fix. Include estimated latency or cost impact where relevant. If nothing is flagged, confirm which patterns were checked and why they pass.
