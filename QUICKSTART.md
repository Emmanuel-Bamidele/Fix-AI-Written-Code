# Quickstart

Use these prompts in sequence.

## 1. First inspection

Paste this into your coding agent:

```text
Read `fix-codebase_triage-and-inventory.md`.
Inspect this repository.
Do not edit files.
Return a prioritized triage report.
```

## 2. Master repair plan

```text
Read `fix-codebase_master-prompt.md`.
Using the triage report, create a repair plan ordered by severity.
Do not edit files yet.
```

## 3. Fix one issue

```text
Read `fix-codebase_remediation-workflow.md`.
Fix the highest-priority finding only.
Add regression tests.
Run relevant checks.
Return a remediation summary.
```

## 4. Security pass

```text
Read `fix-codebase_security.md`.
Perform a security review.
Return findings first.
Do not make changes until findings are listed.
```

## 5. Completion check

```text
Read `fix-codebase_definition-of-done.md`.
Evaluate whether the hardening pass is complete.
Return a final hardening report.
```
