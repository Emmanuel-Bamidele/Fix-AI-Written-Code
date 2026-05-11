# Fix AI-Written Code

> Copy-paste prompts for auditing, fixing, securing, testing, and productionizing code written by AI coding agents.

AI coding agents can generate code fast.

They can also leave behind code that looks impressive but is not actually safe, correct, tested, maintainable, or ready for production.

**Fix AI-Written Code** is a practical prompt pack for developers who want to clean up and harden codebases created or heavily modified by AI coding agents.

Use it with Codex, Claude Code, Cursor, GitHub Copilot, Devin-style agents, or any coding assistant that can inspect and edit a repository.

---

## The problem

AI-generated code often works in the demo path, but breaks down when real engineering standards are applied.

Common problems include:

- Hidden bugs
- Missing edge cases
- Weak input validation
- Missing authorization checks
- Cross-tenant data leaks
- Hardcoded secrets
- Unsafe file handling
- SQL, shell, HTML, or template injection risks
- Fake or shallow tests
- Tests that only assert mocks
- Broken CI/CD
- Dependency bloat
- Vulnerable packages
- Unsafe database migrations
- Missing transactions
- Unbounded database queries
- Inconsistent architecture
- Duplicate implementations
- Poor error handling
- Silent failures
- Missing logs, metrics, and health checks
- Code that is hard to review because agents changed too much at once

This repo gives you structured prompts that tell your coding agent how to audit and repair these issues like a serious engineer.

---

## What this repository does

This repository helps you:

1. Audit an entire codebase.
2. Create a prioritized repair backlog.
3. Fix security, correctness, testing, dependency, CI, architecture, and production-readiness issues.
4. Keep changes small and reviewable.
5. Add tests for real behavior.
6. Avoid dangerous fix everything agent patches.
7. Move an AI-generated codebase closer to production quality.

The goal is not just to make the app run.

The goal is to make the codebase safer, cleaner, tested, maintainable, and easier to trust.

---

## Who this is for

This is useful for:

- Developers using AI coding agents
- Founders building products with AI
- Engineers cleaning up vibe-coded apps
- Teams adopting Codex, Claude Code, Cursor, Copilot, or other coding agents
- Code reviewers
- Security reviewers
- DevOps engineers
- Full-stack engineers
- Anyone inheriting a messy AI-generated codebase

If an agent wrote a lot of your code and now you need to make it reliable, this repo is for you.

---

## What this repository is not

This is not a magic button.

It does not guarantee that generated code is secure or production-ready.

It gives your coding agent a structured engineering process.

You still need to review changes, run tests, inspect security-sensitive code, and use human judgment before shipping.

---

## How it works

The safest way to repair an AI-written codebase is not to ask the agent to fix everything in one giant patch.

Instead, use this workflow:

```text
1. Audit the whole codebase.
2. Create a prioritized repair backlog.
3. Fix the highest-priority issue first.
4. Add or update tests.
5. Run relevant checks.
6. Summarize the change.
7. Move to the next issue.
8. Repeat until the codebase meets the definition of done.
```

This keeps changes focused, reviewable, and safer to merge.

---

## Quick example

Instead of saying:

```text
Fix the whole codebase.
```

Say:

```text
Read `prompts/fix-codebase_triage-and-inventory.md`.

Inspect this repository.

Do not modify files yet.

Return a prioritized triage report with:
- security risks
- correctness risks
- test gaps
- dependency risks
- architecture risks
- broken commands
- recommended repair order
```

Then say:

```text
Read `prompts/fix-codebase_master-prompt.md`.

Using the triage report, create a complete repair backlog.

Group findings by Critical, High, Medium, and Low.

Do not edit files yet.
```

Then say:

```text
Read `prompts/fix-codebase_remediation-workflow.md`.

Take the highest-priority unresolved finding.

Fix only that finding.

Add or update tests.

Run relevant checks.

Summarize changed files, test results, and remaining risks.
```

Repeat the last step until the codebase is stable.

---

## Repository structure

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
LICENSE
```

---

## What is covered

### Full codebase triage

File:

```text
prompts/fix-codebase_triage-and-inventory.md
```

Use this first.

It tells the agent to inspect the repository before editing anything.

It covers:

- Repository structure
- Languages and frameworks
- Package managers
- Build system
- Test setup
- CI/CD files
- Docker and deployment files
- Database schema and migrations
- API routes
- Background jobs
- Frontend routes and components
- Suspicious generated-code patterns
- Broken commands
- Missing docs
- Initial risk ranking

---

### Master repair prompt

File:

```text
prompts/fix-codebase_master-prompt.md
```

This is the main senior-engineer prompt.

It tells the agent to:

- Act like a senior/staff-level engineer
- Prioritize security, correctness, and data safety
- Avoid broad rewrites
- Avoid invented requirements
- Avoid hiding failures
- Produce findings before making fixes
- Work through issues by severity
- Add tests for fixes
- Document what changed

Use this after triage to create the full repair backlog.

---

### Correctness and bug fixing

File:

```text
prompts/fix-codebase_correctness.md
```

Covers:

- Runtime crashes
- Broken edge cases
- Missing null checks
- Invalid assumptions
- Incorrect async behavior
- Missing awaits
- Race conditions
- Bad error handling
- Silent failures
- Wrong state transitions
- Bad date/time/currency handling
- Missing validation

Use this when the code works in demos but breaks in real use.

---

### Security hardening

File:

```text
prompts/fix-codebase_security.md
```

Covers:

- Secret leaks
- Authentication bypasses
- Missing authorization
- Cross-tenant data access
- SQL injection
- NoSQL injection
- Shell injection
- XSS
- CSRF
- SSRF
- Unsafe file uploads
- Unsafe redirects
- Insecure webhook handling
- Sensitive logging
- Dependency vulnerabilities
- Missing rate limits

Use this before deploying anything generated by an agent.

---

### Dependency cleanup

File:

```text
prompts/fix-codebase_dependencies.md
```

Covers:

- Unused packages
- Duplicate libraries
- Vulnerable dependencies
- Bloated dependency trees
- Lockfile issues
- Dev dependencies incorrectly installed as production dependencies
- Abandoned packages
- Supply-chain risk
- Docker base image dependency risk

Use this when an agent added packages carelessly or the project feels bloated.

---

### Performance review

File:

```text
prompts/fix-codebase_performance.md
```

Covers:

- N+1 queries
- Unbounded database queries
- Missing pagination
- Missing indexes
- Unbounded parallelism
- Slow API endpoints
- Blocking work in request paths
- Repeated expensive computation
- Large frontend bundles
- Re-render loops
- Unoptimized images
- Slow background jobs
- Cache misuse

Use this after correctness and security are stable.

---

### Architecture repair

File:

```text
prompts/fix-codebase_architecture.md
```

Covers:

- Conflicting implementations
- Multiple auth systems
- Multiple API clients
- Multiple config loaders
- Duplicate domain models
- Circular dependencies
- Business logic in UI components or controllers
- Over-generalized abstractions
- Dead code
- Bad module boundaries
- Inconsistent naming

Use this when multiple agents or contributors pushed the project in different directions.

---

### Data and migration safety

File:

```text
prompts/fix-codebase_data-and-migrations.md
```

Covers:

- Unsafe migrations
- Destructive schema changes
- Missing constraints
- Missing indexes
- Bad cascade behavior
- Missing transactions
- Unsafe backfills
- Decimal precision issues
- Timezone issues
- Soft delete consistency
- Migration rollback planning

Use this before running database changes in production.

---

### API contract validation

File:

```text
prompts/fix-codebase_api-contracts.md
```

Covers:

- Request validation
- Response validation
- Error format consistency
- Query parameter validation
- Path parameter validation
- Webhook payload validation
- Message queue payload validation
- Third-party API response validation
- Pagination correctness
- API documentation drift

Use this when frontend/backend contracts are fragile or unclear.

---

### Test repair

File:

```text
prompts/fix-codebase_tests.md
```

Covers:

- Fake tests
- Shallow tests
- Tests that only check mocks
- Flaky tests
- Missing regression tests
- Missing authorization tests
- Missing integration tests
- Missing API tests
- Tests that depend on local machine state
- Tests that hide real failures

Use this when the test suite passes but does not inspire confidence.

---

### CI/CD repair

File:

```text
prompts/fix-codebase_ci-cd.md
```

Covers:

- Missing CI checks
- Broken workflows
- Missing build validation
- Missing type checks
- Missing lint checks
- Missing test gates
- Missing dependency audits
- Missing secret scans
- Unsafe deployment workflows
- CI that depends on production secrets

Use this to prevent the same problems from coming back.

---

### Observability and operations

File:

```text
prompts/fix-codebase_observability.md
```

Covers:

- Structured logging
- Request IDs
- Error tracking
- Metrics
- Health checks
- Readiness checks
- Background job visibility
- Audit logs
- Alerting
- Runbooks
- Sensitive log redaction

Use this when the app runs but would be hard to debug in production.

---

### Frontend cleanup

File:

```text
prompts/fix-codebase_frontend.md
```

Covers:

- Oversized components
- Duplicated state
- Missing loading states
- Missing empty states
- Missing error states
- Weak form validation
- Accessibility problems
- Unsafe HTML rendering
- Scattered API calls
- Broken auth state
- Large lists without virtualization
- Unoptimized assets
- Bundle size issues

Use this for React, Next.js, Vue, Svelte, Angular, or other frontend codebases.

---

### Backend cleanup

File:

```text
prompts/fix-codebase_backend.md
```

Covers:

- Route validation
- Authentication
- Authorization
- Service-layer design
- Database writes
- Transactions
- Webhooks
- Background jobs
- Rate limiting
- External API timeouts
- Safe error responses
- Sensitive logging
- Multi-tenant data isolation

Use this for API servers, workers, microservices, and backend-heavy applications.

---

### Infrastructure cleanup

File:

```text
prompts/fix-codebase_infrastructure.md
```

Covers:

- Dockerfile safety
- Root containers
- Dev dependencies in production images
- Secrets baked into images
- Missing health checks
- Unsafe cloud permissions
- Public buckets
- Exposed databases
- Missing backups
- Missing rollback plan
- Deployment safety

Use this before shipping agent-generated infrastructure or deployment code.

---

### Agentic failure patterns

File:

```text
prompts/fix-codebase_agentic-failure-patterns.md
```

Covers problems that are especially common in AI-generated code:

- Plausible but wrong library usage
- Fabricated APIs
- Conflicting implementations
- Overbroad exception handling
- Type suppressions
- Placeholder behavior
- Fake robustness
- Inconsistent vocabulary
- Repeated helper functions
- Comments that claim safety without real checks

Use this when the code looks right but feels suspicious.

---

### Remediation workflow

File:

```text
prompts/fix-codebase_remediation-workflow.md
```

Covers how to fix issues safely.

It tells the agent to:

- Work one finding at a time
- Reproduce or prove the issue first
- Make the smallest safe fix
- Add tests
- Run checks
- Summarize files changed
- Avoid unrelated refactors

Use this when you are ready to let the agent modify the codebase.

---

### Definition of done

File:

```text
prompts/fix-codebase_definition-of-done.md
```

Covers final acceptance criteria.

It checks:

- Build
- Tests
- Lint
- Type checks
- Security
- Correctness
- Data safety
- Maintainability
- Performance
- Operations
- CI/CD
- Documentation

Use this before considering the cleanup finished.

---

## Recommended workflow

For most projects, use this sequence:

```text
1. Triage and inventory
2. Master repair backlog
3. Security review
4. Critical security fixes
5. Data-safety fixes
6. Correctness fixes
7. Test repair
8. Dependency cleanup
9. CI/CD repair
10. API contract review
11. Backend or frontend focused cleanup
12. Architecture cleanup
13. Performance review
14. Observability review
15. Definition of done
```

---

## The full-codebase repair loop

This repo is designed for full-codebase repair.

The reason it recommends fixing one issue at a time is safety.

Use this repeated loop:

```text
Read `prompts/fix-codebase_remediation-workflow.md`.

Take the next highest-priority unresolved finding from the repair backlog.

Fix only that finding.

Add or update tests.

Run relevant checks.

Update the finding status.

Recommend the next finding to fix.
```

Repeat until:

```text
- all Critical findings are fixed
- all High findings are fixed
- Medium findings are fixed or accepted with explanation
- Low findings are fixed or moved to future cleanup
- tests pass
- build passes
- CI passes
- security risks are addressed
- the definition of done is satisfied
```

---

## Severity guide

Use this severity model:

| Severity | Meaning |
|---|---|
| Critical | Secret exposure, auth bypass, data loss, remote code execution, destructive migration, production outage risk |
| High | Broken authorization, incorrect business logic, runtime crashes, major build or test failure |
| Medium | Performance bottleneck, architecture drift, flaky tests, weak error handling |
| Low | Formatting, naming, minor cleanup, documentation gaps |

Fix in this order:

```text
Critical -> High -> Medium -> Low
```

---

## Good prompts

Use specific prompts like:

```text
Inspect first. Do not edit files.
```

```text
Create a repair backlog. Do not edit files yet.
```

```text
Fix only the highest-priority unresolved finding.
```

```text
Add a regression test.
```

```text
Run relevant checks and report failures honestly.
```

```text
Do not refactor unrelated code.
```

---

## Bad prompts

Avoid vague prompts like:

```text
Fix the whole app.
```

```text
Make this production ready.
```

```text
Clean up everything.
```

```text
Refactor the codebase.
```

```text
Make all tests pass however you can.
```

These prompts are too broad and can produce unsafe changes.

---

## Suggested usage with agents

### Codex / ChatGPT-style coding agent

Paste the prompt file contents or reference the file path if the agent can read the repository.

```text
Read `prompts/fix-codebase_triage-and-inventory.md`.
Inspect this repository.
Do not modify files yet.
Return a prioritized triage report.
```

### Claude Code

Ask Claude Code to read the relevant prompt file before acting.

```text
Read `prompts/fix-codebase_master-prompt.md`.
Create a repair backlog.
Do not edit files yet.
```

### Cursor

Open the prompt file, reference it in chat, and ask Cursor to follow it.

```text
Follow `prompts/fix-codebase_security.md`.
Review security risks.
Do not modify files yet.
```

### GitHub Copilot

Use the prompt files as manual instructions in Copilot Chat or copy relevant sections into your request.

---

## Templates included

The repository includes templates for tracking and reviewing fixes.

```text
templates/issue-template.md
templates/pull-request-template.md
```

Use them to turn agent findings into reviewable engineering work.

---

## Best practices when using this repo

When using these prompts, tell your agent:

- Do not invent product requirements.
- Do not hide failing tests.
- Do not remove behavior silently.
- Do not suppress type errors without explanation.
- Do not add dependencies without justification.
- Do not make broad rewrites before triage.
- Do not mix security fixes with cosmetic refactors.
- Do not claim success unless commands passed.
- Do not delete tests just because they fail.
- Do not trust comments without verifying code behavior.
- Always provide evidence for findings.
- Always add regression tests for bug fixes.
- Always keep patches small and reviewable.

---

## Supported project types

These prompts are language-agnostic.

They can be adapted for:

- JavaScript
- TypeScript
- Python
- Go
- Rust
- Java
- C#
- Ruby
- PHP
- React
- Next.js
- Vue
- Svelte
- Angular
- Node.js
- Django
- FastAPI
- Rails
- Laravel
- Spring
- Docker
- Kubernetes
- Terraform
- Serverless apps

The prompts are not tied to one stack.

---

## Recommended companion repository

For codebases where you want standing rules that agents should always follow, use:

```text
AI-Agent-Coding-Rules
```

That repository is for placing persistent instructions inside a codebase.

This repository is for auditing and repairing an existing codebase.

They work well together:

```text
AI-Agent-Coding-Rules      -> rules agents should always follow
Fix-AI-Written-Code        -> prompts for auditing and repairing codebases
```

---

## Suggested repository description

```text
Copy-paste prompts for fixing, securing, testing, and productionizing code written by AI coding agents.
```

---

## Suggested tagline

```text
Turn chaotic AI-generated code into production-grade software.
```

---

## Suggested GitHub topics

```text
ai
ai-agents
coding-agents
ai-code-review
code-review
code-audit
codebase-audit
security
security-hardening
software-engineering
prompt-engineering
developer-tools
technical-debt
testing
ci-cd
devsecops
```

---

## Contributing

Contributions are welcome.

Good contributions include:

- New repair prompts
- Better checklists
- Language-specific variants
- Framework-specific variants
- Security-specific improvements
- Real-world examples
- Better CI/CD templates
- Better issue and PR templates
- Improved wording for agent compatibility

Please keep prompts practical, specific, and easy to copy into coding agents.

---

## Future ideas

Useful future additions:

```text
prompts/language-specific/fix-typescript.md
prompts/language-specific/fix-python.md
prompts/language-specific/fix-go.md
prompts/framework-specific/fix-nextjs.md
prompts/framework-specific/fix-fastapi.md
prompts/framework-specific/fix-django.md
prompts/framework-specific/fix-rails.md
prompts/security/fix-authz.md
prompts/security/fix-secrets.md
prompts/security/fix-webhooks.md
examples/before-after.md
examples/real-agent-session.md
```

---

## Disclaimer

These prompts are tools for improving software quality, not a guarantee of correctness or security.

Always review generated changes carefully.

For production systems, especially those handling money, health data, personal data, authentication, infrastructure, or sensitive user information, use human review, security review, testing, staged deployment, monitoring, and rollback plans.

---

## Final note

AI coding agents are powerful.

But generated code should not be treated as automatically trustworthy.

Use agents to move faster.

Use engineering discipline to make the result safe.

**Fix AI-Written Code** helps bridge that gap.
