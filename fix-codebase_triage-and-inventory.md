# fix-codebase_triage-and-inventory.md

Use this prompt before allowing an agent to modify a codebase.

## Goal

Build a reliable map of the repository, identify risks, and determine the safest repair order.

## Instructions for the agent

You are not allowed to edit files yet.

Inspect the repository and produce a structured triage report.

## Required inventory

Identify:

- Programming languages
- Package managers
- Frameworks
- Application entrypoints
- Build system
- Test framework
- CI/CD configuration
- Docker or deployment files
- Database schema and migrations
- API routes
- Background jobs
- Frontend routes/components
- Configuration files
- Secret handling
- Generated files
- Dead or suspicious files

## Commands to try

Run applicable commands and capture results:

```bash
git status
git log --oneline --decorate -20
find . -maxdepth 3 -type f | sort
```

For JavaScript/TypeScript:

```bash
npm ci
npm run lint
npm run typecheck
npm test
npm run build
```

For Python:

```bash
python -m venv .venv
pip install -r requirements.txt
ruff check .
mypy .
pytest
```

For Go:

```bash
go test ./...
go vet ./...
```

For Rust:

```bash
cargo fmt --check
cargo clippy -- -D warnings
cargo test
```

## Suspicious pattern search

Search for:

```text
TODO
FIXME
HACK
XXX
placeholder
mock
temporary
@ts-ignore
@ts-expect-error
eslint-disable
type: ignore
noqa
any
password
secret
token
api_key
PRIVATE KEY
dangerouslySetInnerHTML
eval
exec(
innerHTML
raw SQL
```

## Output format

```md
# Codebase Triage Report

## Stack detected

## Repository map

## Commands run

| Command | Result | Notes |
|---|---|---|

## Critical risks

## Suspicious generated-code patterns

## Broken quality gates

## Missing documentation

## Top prioritized findings

| ID | Severity | Category | Summary | Files |
|---|---|---|---|---|

## Recommended repair sequence

## Do-not-touch-yet areas

Areas that need product clarification or careful migration.
```

## Constraint

Do not refactor anything during triage.
