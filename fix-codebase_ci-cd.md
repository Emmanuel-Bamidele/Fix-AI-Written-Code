# fix-codebase_ci-cd.md

Use this prompt to repair CI/CD quality gates.

## Goal

Make quality checks automatic, deterministic, and difficult to bypass.

## Agent instructions

Inspect CI configuration and local scripts. Align local and CI commands.

## Required CI checks

At minimum, CI should run:

- Clean dependency install from lockfile
- Formatting check
- Lint
- Type check where applicable
- Unit tests
- Integration tests where feasible
- Build
- Secret scan
- Dependency audit
- Container scan if containers are built

## GitHub Actions baseline

Adapt this to the repository:

```yaml
name: quality

on:
  pull_request:
  push:
    branches: [main]

jobs:
  check:
    runs-on: ubuntu-latest

    steps:
      - uses: actions/checkout@v4

      - name: Install dependencies
        run: npm ci

      - name: Format check
        run: npm run format:check

      - name: Lint
        run: npm run lint

      - name: Type check
        run: npm run typecheck

      - name: Test
        run: npm test

      - name: Build
        run: npm run build
```

## CI review checklist

- [ ] CI runs on pull requests.
- [ ] CI runs on main branch.
- [ ] CI uses lockfiles.
- [ ] CI does not require production secrets.
- [ ] CI does not deploy from untrusted forks.
- [ ] CI blocks merges on critical failures.
- [ ] CI commands match documented local commands.
- [ ] Security checks exist.
- [ ] Dependency cache is safe.
- [ ] Deployment requires passing checks.

## Required output

```md
# CI/CD Repair Summary

## Current workflows

## Missing gates

## Broken gates

## Security risks

## Changes made

## Commands validated

## Remaining CI/CD improvements
```
