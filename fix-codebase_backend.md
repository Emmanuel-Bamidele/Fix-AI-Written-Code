# fix-codebase_backend.md

Use this prompt to repair backend security, correctness, data safety, jobs, and APIs.

## Goal

Make backend behavior safe, predictable, and observable.

## Agent instructions

Inspect routes, services, database access, jobs, integrations, auth, validation, and error handling.

## Backend risk areas

- Authentication
- Authorization
- Request validation
- Database transactions
- External API calls
- Webhooks
- Background jobs
- Rate limiting
- Error handling
- Logging
- Data serialization
- Caching
- Multi-tenant scoping

## Required checks

- Every protected route authenticates.
- Every object access authorizes.
- Every request validates input.
- Every external call has timeout handling.
- Every webhook verifies signature.
- Every sensitive mutation has audit logging.
- Jobs are idempotent.
- Retries are bounded.
- Database writes are transactional when needed.
- Errors are mapped to safe responses.
- Internal details are not leaked to clients.

## Rate limiting targets

Review:

- Login
- Signup
- Password reset
- Invite creation
- Email sending
- File upload
- Expensive search/query endpoints
- Payment/webhook endpoints where appropriate

## Required output

```md
# Backend Repair Summary

## Routes inspected

## Service-layer issues

## Auth/authz issues

## Data safety issues

## Job issues

## Integration issues

## Fixes made

## Tests added

## Remaining backend risks
```
