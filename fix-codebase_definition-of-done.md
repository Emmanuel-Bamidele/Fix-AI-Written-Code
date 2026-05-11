# fix-codebase_definition-of-done.md

Use this prompt to decide whether a codebase hardening pass is complete.

## Goal

Create a strict final checklist for accepting the repair work.

## Build and test

- [ ] Fresh clone can install dependencies.
- [ ] Local setup is documented.
- [ ] App runs locally.
- [ ] Build passes.
- [ ] Tests pass.
- [ ] Lint passes.
- [ ] Type checks pass where applicable.
- [ ] CI enforces the same checks.
- [ ] Lockfiles are committed.

## Security

- [ ] No committed secrets remain.
- [ ] Exposed secrets were rotated or flagged.
- [ ] `.env.example` exists.
- [ ] `.env` is ignored.
- [ ] Auth is enforced on protected routes.
- [ ] Authorization is tested.
- [ ] Cross-tenant access is denied.
- [ ] Inputs are validated.
- [ ] Injection risks are addressed.
- [ ] File upload risks are addressed.
- [ ] Webhooks verify signatures.
- [ ] Sensitive logs are redacted.
- [ ] Critical dependency vulnerabilities are fixed or documented.

## Correctness

- [ ] Critical flows have tests.
- [ ] Known bugs have regression tests.
- [ ] Edge cases are handled.
- [ ] Async behavior is correct.
- [ ] External failures are handled.
- [ ] Transactions are used where needed.
- [ ] Timezone and currency behavior is correct where relevant.
- [ ] Error messages are safe and useful.

## Data

- [ ] Migrations run from an empty database.
- [ ] Migrations run against existing data.
- [ ] Destructive migrations are staged.
- [ ] Constraints match business rules.
- [ ] Indexes support real queries.
- [ ] Backfill plan exists where needed.
- [ ] Rollback plan exists.

## Maintainability

- [ ] Duplicate implementations are consolidated.
- [ ] Dead code is removed.
- [ ] Unused dependencies are removed.
- [ ] Naming is consistent.
- [ ] Architecture boundaries are clear.
- [ ] Config is centralized.
- [ ] Logging is centralized.
- [ ] Validation approach is consistent.
- [ ] README is accurate.

## Performance

- [ ] Obvious N+1 queries are fixed.
- [ ] Unbounded queries are bounded.
- [ ] External calls have timeouts.
- [ ] Large lists are paginated or virtualized.
- [ ] Cache behavior has invalidation rules.
- [ ] Hot paths were measured or reviewed.

## Operations

- [ ] Structured logs exist.
- [ ] Request IDs exist.
- [ ] Health checks exist.
- [ ] Errors are tracked.
- [ ] Critical metrics exist.
- [ ] Alerts are meaningful.
- [ ] Deployment is documented.
- [ ] Rollback is documented.
- [ ] Backups are addressed where needed.

## Final acceptance response

Ask the agent to produce:

```md
# Final Hardening Report

## Summary

## Major risks fixed

## Files changed

## Tests and checks

## Remaining accepted risks

## Recommended future work

## Confidence level

High | Medium | Low

## Why this confidence level?
```
