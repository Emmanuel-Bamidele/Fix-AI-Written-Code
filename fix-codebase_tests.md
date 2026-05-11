# fix-codebase_tests.md

Use this prompt to repair weak, fake, flaky, or missing tests.

## Goal

Build a test suite that proves important behavior and prevents regressions.

## Agent instructions

Do not chase vanity coverage. Focus on meaningful risk reduction.

## Identify bad tests

Flag tests that:

- Only check that something renders
- Only check mocks were called
- Mock the function under test
- Duplicate implementation logic
- Have no assertions
- Are skipped without reason
- Are flaky
- Depend on test order
- Depend on local machine state
- Use production services
- Use production credentials
- Hide failures with broad snapshots
- Test private implementation details instead of behavior

## Required test types

Add where appropriate:

- Unit tests for pure domain logic
- Integration tests for database behavior
- API contract tests
- Authorization negative tests
- Regression tests for fixed bugs
- End-to-end tests for critical flows
- Smoke tests for deployment
- Migration tests where feasible

## Regression rule

Every bug fix needs a regression test unless impossible.

If impossible, state why.

## Good test pattern

A good test:

1. Sets up realistic data.
2. Performs a user-visible or system-visible action.
3. Asserts durable behavior.
4. Includes a negative case.
5. Cleans up after itself.

## Required output

```md
# Test Suite Repair

## Current test setup

## Bad tests found

## Missing critical coverage

## Tests added

## Flaky tests fixed

## Commands run

## Remaining gaps
```

## Constraint

Do not delete tests simply because they fail. First determine whether the test or the code is wrong.
