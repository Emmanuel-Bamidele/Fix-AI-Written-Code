# fix-codebase_architecture.md

Use this prompt to repair architectural drift and inconsistent patterns.

## Goal

Make the codebase understandable, cohesive, and safe to evolve.

## Agent instructions

Do not start with a rewrite. First identify boundaries and duplicate patterns.

## Detect architectural drift

Look for:

- Multiple auth systems
- Multiple API clients
- Multiple config loaders
- Multiple logging systems
- Multiple validation approaches
- Business logic in controllers or UI components
- Database access scattered everywhere
- Circular dependencies
- Duplicated domain models
- Dead abstractions
- Over-generalized managers
- Large files with mixed responsibilities

## Preferred structure

A typical maintainable backend boundary:

```text
transport/controllers
application/services
domain
persistence/repositories
integrations/adapters
```

A typical frontend boundary:

```text
routes/pages
features
components
hooks
api
state
utils
```

Adapt this to the project. Do not force a structure that does not fit.

## Consolidation rules

For each duplicated pattern:

1. Identify all implementations.
2. Pick the safest existing implementation.
3. Write tests around expected behavior.
4. Migrate callers gradually.
5. Delete replaced code.
6. Document the chosen pattern.

## What to delete

Delete only when safe:

- Unused files
- Unused helpers
- Dead routes
- Placeholder adapters
- One-implementation interfaces with no test value
- Fake abstraction layers
- Stale mocks
- Duplicate config
- Old generated code

## Required output

```md
# Architecture Repair Report

## Current architecture

## Detected drift

## Duplicate patterns

## Proposed target architecture

## Safe incremental migration plan

## Files safe to delete

## Files requiring product/domain review
```

## Constraint

Do not combine architectural changes with unrelated security or bug fixes unless required.
