# fix-codebase_correctness.md

Use this prompt to make the codebase behaviorally correct.

## Goal

Find and fix bugs, invalid assumptions, broken edge cases, incorrect async behavior, bad error handling, and data integrity problems.

## Agent instructions

Review the code for correctness before style.

Prioritize defects that cause:

- Wrong user-visible behavior
- Runtime crashes
- Data corruption
- Silent failures
- Incorrect state transitions
- Missing edge-case handling
- Broken async/concurrency behavior

## Common issues to find

### Happy-path-only code

Look for code that assumes:

- Records always exist
- Arrays are never empty
- API calls always succeed
- JSON always has the expected shape
- Dates are always valid
- Environment variables are always set
- Permissions were already checked elsewhere

### Bad async behavior

Look for:

- Missing `await`
- `map(async ...)` without `Promise.all`
- Detached promises without error handling
- Race conditions
- Unsafe shared mutable state
- Retrying non-idempotent operations
- Unbounded parallelism

### Bad error handling

Look for:

- Empty `catch` blocks
- `console.log` instead of structured logging
- Returning fake success after failure
- Throwing strings
- Leaking internal errors to users
- Catching too broadly
- Swallowing database or payment errors

### Bad validation

Look for:

- Superficial checks
- Type assertions instead of validation
- Missing runtime validation at boundaries
- Trusting client-provided IDs
- Trusting request headers
- Trusting third-party responses

## Required fixes

For each correctness issue:

1. Add or identify a failing test.
2. Fix the smallest unit of behavior.
3. Add validation or explicit error handling.
4. Verify the fix.
5. Avoid unrelated cleanup.

## Review checklist

- [ ] Public inputs are validated.
- [ ] Nullable values are handled.
- [ ] Empty states are handled.
- [ ] Invalid states are impossible or detected.
- [ ] Async operations are awaited.
- [ ] Detached work has error handling.
- [ ] External calls have timeout handling.
- [ ] State transitions are tested.
- [ ] Business rules live in one place.
- [ ] Date, timezone, and currency logic is correct.
- [ ] Errors are meaningful.
- [ ] Silent fallbacks are removed.
- [ ] Regression tests exist.

## Output format

```md
# Correctness Repair Summary

## Issues found

## Fixes made

## Tests added

## Commands run

## Remaining correctness risks
```
