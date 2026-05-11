# Fix AI-Written Code

> Copy-paste prompts for fixing, securing, testing, and productionizing code written by AI coding agents.

AI coding agents can generate code quickly, but they can also leave behind hidden bugs, weak security, fake tests, inconsistent architecture, dependency bloat, broken CI, unsafe migrations, and production risks.

**Fix AI-Written Code** is a practical prompt pack for developers who want to clean up, audit, harden, and productionize codebases created or heavily modified by AI coding agents.

Use these prompts with tools like Codex, Claude Code, Cursor, Copilot, Devin-style agents, or any coding agent that can inspect and edit a repository.

---

## Why this exists

AI coding agents are great at generating code fast.

But fast code is not always safe code.

Agent-written code often has problems like:

- Happy-path-only logic
- Missing authorization checks
- Weak input validation
- Fake or shallow tests
- Unused dependencies
- Duplicated implementations
- Inconsistent architecture
- Security vulnerabilities
- Unsafe database migrations
- Missing observability
- Broken CI/CD
- Silent error handling
- Runtime crashes hidden behind broad `try/catch` blocks

This repo gives you structured prompts and checklists that tell your coding agent how to audit and repair those problems like a serious engineer.

---

## What this repo contains

This repository is a collection of Markdown prompt files.

Each file focuses on a specific part of codebase repair.

```text
prompts/
  fix-codebase_master-prompt.md
  fix-codebase_triage-and-inventory.md
  fix-codebase_correctness.md
  fix-codebase_security.md
  fix-codebase_dependencies.md
  fix-codebase_performance.md
  fix-codebase_architecture.md
  fix-codebase_data-and-migrations.md
  fix-codebase_api-contracts.md
  fix-codebase_tests.md
  fix-codebase_ci-cd.md
  fix-codebase_observability.md
  fix-codebase_frontend.md
  fix-codebase_backend.md
  fix-codebase_infrastructure.md
  fix-codebase_agentic-failure-patterns.md
  fix-codebase_remediation-workflow.md
  fix-codebase_definition-of-done.md

templates/
  issue-template.md
  pull-request-template.md

QUICKSTART.md
README.md
