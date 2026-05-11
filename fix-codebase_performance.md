# fix-codebase_performance.md

Use this prompt to find and fix performance problems with evidence.

## Goal

Improve performance without guessing or creating risky rewrites.

## Agent instructions

Measure before optimizing. If measurement is not possible, explain the limitation and use code evidence.

## Areas to inspect

- Database queries
- API latency
- External service calls
- Startup time
- Memory usage
- CPU-heavy loops
- Serialization
- Frontend rendering
- Bundle size
- Asset loading
- Background jobs
- Caching behavior

## Common performance issues

Find:

- N+1 database queries
- Unbounded `findAll` / `findMany`
- Missing pagination
- Missing indexes
- Repeated expensive computation
- Unbounded parallelism
- Synchronous blocking in request paths
- Large JSON payloads
- Re-render loops
- Unvirtualized large lists
- Large bundles
- Unoptimized images
- External calls without timeouts
- Cache without invalidation

## Database checks

Look for queries that need:

- `LIMIT`
- Pagination
- Indexes
- Selective columns
- Joins/includes instead of loops
- Transactions
- Batching

## Frontend checks

Look for:

- Heavy components
- Repeated derived calculations
- Context updates causing full-tree re-render
- Large lists without virtualization
- Waterfall requests
- Unnecessary client-side data fetching
- Images without dimensions or optimization

## Required output

```md
# Performance Review

## Baseline

## Hot paths inspected

## Findings

| ID | Impact | Evidence | Proposed fix |
|---|---|---|---|

## Fixes made

## Benchmarks or measurements

## Remaining risks
```

## Fix rules

- Prefer bounded queries.
- Prefer pagination.
- Prefer indexes backed by observed query patterns.
- Prefer batching over uncontrolled parallelism.
- Do not add caching without invalidation rules.
- Do not trade correctness for speed.
