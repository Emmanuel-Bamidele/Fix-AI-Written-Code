# fix-codebase_api-contracts.md

Use this prompt to validate API contracts, runtime schemas, webhooks, and integration boundaries.

## Goal

Ensure that every boundary validates input, returns consistent output, and matches real contracts.

## Agent instructions

Static types are not enough. Validate runtime data crossing process or trust boundaries.

## Boundaries to inspect

- HTTP request bodies
- Query parameters
- Path parameters
- Headers
- Cookies
- API responses
- Webhook payloads
- Message queue payloads
- CLI args
- Environment variables
- Third-party API responses
- Cache values
- Local storage
- Database JSON columns

## Required checks

- Request validation exists.
- Response shape is deliberate.
- Errors use a consistent format.
- Pagination is stable.
- Sorting is deterministic.
- Filtering is validated.
- Versioning is documented if needed.
- Webhook signatures are verified.
- Third-party responses are parsed defensively.
- OpenAPI or documentation matches implementation.

## Error format

Prefer a consistent safe error shape:

```json
{
  "error": {
    "code": "VALIDATION_ERROR",
    "message": "Invalid request",
    "details": []
  }
}
```

Do not leak internal stack traces to clients.

## Required output

```md
# API Contract Review

## Endpoints inspected

## Missing validation

## Inconsistent responses

## Unsafe webhooks

## Third-party contract risks

## Fixes made

## Contract tests added
```

## Test requirements

Add tests for:

- Valid request
- Invalid request
- Unauthorized request
- Forbidden cross-tenant request
- Missing required fields
- Invalid enum values
- Pagination edge cases
- Webhook signature failure
