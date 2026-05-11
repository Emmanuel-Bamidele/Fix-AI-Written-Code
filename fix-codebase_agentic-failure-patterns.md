# fix-codebase_agentic-failure-patterns.md

Use this prompt to specifically detect failures common in AI-agent-written code.

## Goal

Find defects caused by agents producing plausible but inconsistent, incomplete, insecure, or overconfident code.

## Agent instructions

Review the codebase with skepticism. Look for signs that code was generated without full context.

## Common patterns

### Conflicting implementations

Look for multiple versions of:

- Auth/session handling
- API clients
- Config loaders
- Validation helpers
- Logger setup
- Error classes
- Database access wrappers
- Date formatting
- Permission checks
- State management

Fix by choosing one pattern and migrating gradually.

### Fabricated APIs

Agents may call functions that do not exist or use libraries incorrectly.

Check:

- Third-party method names
- Parameter order
- Return types
- Async/sync behavior
- Version compatibility
- Deprecated APIs

### Fake robustness

Look for:

- `try/catch` blocks that hide errors
- Fallbacks to empty arrays
- Defaults that hide missing config
- Comments claiming validation without validation
- Tests that mock away all risk

### Type suppression

Search for:

- `any`
- `unknown as`
- `@ts-ignore`
- `@ts-expect-error`
- `eslint-disable`
- `type: ignore`
- `noqa`

Each suppression must be removed or justified.

### Placeholder behavior

Search for:

- `TODO`
- `FIXME`
- `mock`
- `placeholder`
- `temporary`
- `not implemented`
- `return true`
- `return []`
- `return null`

### Inconsistent vocabulary

Find cases where the same concept has different names:

- tenant / organization / workspace / account
- user / member / owner
- state / status / phase
- project / app / service
- permission / role / policy

Create a glossary and align names gradually.

## Required output

```md
# Agentic Failure Pattern Review

## Conflicting implementations

## Fabricated or suspicious API usage

## Fake robustness

## Type suppressions

## Placeholder behavior

## Inconsistent vocabulary

## Recommended cleanup sequence
```

## Constraint

Do not rewrite everything. Convert agentic chaos into small reviewable repairs.
