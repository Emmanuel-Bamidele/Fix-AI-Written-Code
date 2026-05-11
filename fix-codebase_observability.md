# fix-codebase_observability.md

Use this prompt to make the application diagnosable in production.

## Goal

Add or repair logging, metrics, tracing, health checks, audit logs, and operational visibility.

## Agent instructions

Focus on user-impacting flows, critical jobs, and sensitive actions.

## Required observability areas

- Structured logs
- Request IDs
- Error tracking
- Metrics
- Health checks
- Readiness checks
- Background job visibility
- Audit logs
- Deployment logs
- Alerts
- Runbooks

## Logging review

Good logs include:

- Event name
- Request ID
- User or tenant ID when safe
- Resource ID
- Operation result
- Error object
- Duration for slow operations

Bad logs include:

- Full tokens
- Passwords
- Cookies
- Raw sensitive request bodies
- Full payment details
- Excessive personal data

## Metrics to consider

- Request count
- Request latency
- Error rate
- Job success/failure count
- Queue depth
- External API latency
- Database query latency
- Login failure count
- Rate limit count
- Payment/webhook processing failures

## Health checks

Separate:

- Liveness: process is alive.
- Readiness: service can handle traffic.

Readiness can check:

- Database connection
- Queue connection
- Required migrations
- Critical dependency availability

## Required output

```md
# Observability Repair

## Current observability

## Missing logs

## Missing metrics

## Missing health checks

## Sensitive logging risks

## Fixes made

## Recommended alerts

## Runbook gaps
```
