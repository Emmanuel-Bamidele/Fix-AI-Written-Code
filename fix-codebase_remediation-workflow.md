# fix-codebase_remediation-workflow.md

Use this prompt to guide the actual repair process after triage.

## Goal

Fix the codebase safely through small, reviewable changes.

## Agent instructions

Work one finding at a time.

Do not combine unrelated repairs.

## Workflow

### 1. Select a finding

Choose the highest-priority finding that can be safely fixed now.

### 2. Reproduce or prove the issue

Before editing, provide:

- Command that fails
- Test that fails
- Code evidence
- Security reasoning
- Runtime reproduction

### 3. Create a minimal patch

The patch should:

- Fix the finding
- Add or update tests
- Avoid unrelated formatting
- Avoid broad rewrites
- Avoid new dependencies unless justified

### 4. Run checks

Run relevant checks:

```bash
make check
```

Or the project-specific equivalent.

If no unified command exists, run lint, typecheck, test, and build separately.

### 5. Summarize

Provide:

- What changed
- Why it changed
- Files modified
- Tests added
- Commands run
- Remaining risks

## Patch discipline

Avoid:

- Giant diffs
- Opportunistic refactors
- Silent behavior changes
- Dependency churn
- Formatting unrelated files
- Suppressing new errors
- Deleting tests without replacement

## Required output after each fix

```md
# Remediation Summary

## Finding fixed

## Evidence before fix

## Change made

## Tests added

## Commands run

## Files changed

## Residual risk

## Suggested next finding
```
