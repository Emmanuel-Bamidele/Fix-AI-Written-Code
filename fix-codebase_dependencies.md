# fix-codebase_dependencies.md

Use this prompt to clean up dependency risk, unused packages, duplicate libraries, and supply-chain issues.

## Goal

Make dependencies minimal, justified, current, secure, and reproducible.

## Agent instructions

Audit all package manifests and lockfiles.

Do not upgrade everything blindly. Prefer focused changes.

## Check package managers

Identify:

- `package.json`
- `package-lock.json`
- `pnpm-lock.yaml`
- `yarn.lock`
- `requirements.txt`
- `pyproject.toml`
- `poetry.lock`
- `uv.lock`
- `go.mod`
- `go.sum`
- `Cargo.toml`
- `Cargo.lock`
- Docker base images
- GitHub Actions versions

## Required checks

Run applicable commands:

```bash
npm audit
pnpm audit
yarn audit
npx depcheck
pip-audit
pipdeptree
poetry show --tree
go mod graph
govulncheck ./...
cargo tree
cargo audit
```

## Find unnecessary dependencies

Look for packages used for:

- Trivial helpers
- Date formatting where native APIs work
- Multiple HTTP clients
- Multiple validation libraries
- Multiple logging systems
- Multiple state managers
- Duplicate UI frameworks
- Abandoned packages
- Build tools no longer used

## Review package risk

For each suspicious dependency, consider:

- Maintenance status
- License
- Transitive dependency count
- Install scripts
- Native extensions
- Known vulnerabilities
- Whether standard library can replace it
- Whether the package is used in production or dev only

## Required output

```md
# Dependency Audit

## Package managers detected

## Vulnerabilities

| Package | Severity | Current | Fixed | Action |
|---|---|---:|---:|---|

## Unused dependencies

## Duplicate dependency categories

## Recommended removals

## Recommended upgrades

## Lockfile status

## Commands run
```

## Fix rules

- Remove unused packages.
- Move dev-only packages to dev dependencies.
- Keep lockfiles committed.
- Avoid changing major versions without tests.
- Avoid adding new packages unless clearly justified.
- Document any vulnerability accepted temporarily.
