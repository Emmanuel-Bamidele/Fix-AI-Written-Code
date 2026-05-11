# fix-codebase_security.md

Use this prompt to harden authentication, authorization, input handling, secrets, dependencies, and data exposure.

## Goal

Find and fix security vulnerabilities before cosmetic or architectural cleanup.

## Agent instructions

Treat all external input as hostile.

Review:

- HTTP requests
- Query parameters
- Path parameters
- Headers
- Cookies
- Webhooks
- File uploads
- URLs
- CLI input
- Environment variables
- Database records from untrusted flows
- Third-party API responses

## Priority order

1. Secret exposure
2. Authentication bypass
3. Authorization flaws
4. Injection
5. Unsafe file handling
6. SSRF
7. XSS
8. CSRF
9. Insecure deserialization
10. Sensitive logging
11. Vulnerable dependencies
12. Missing rate limits

## Secret scanning

Run applicable tools:

```bash
gitleaks detect --source .
trufflehog filesystem .
```

Also search manually:

```bash
grep -R "password\|secret\|token\|api_key\|PRIVATE KEY\|BEGIN RSA\|AKIA\|ghp_\|sk-" .
```

If secrets are found:

- Remove them.
- Add `.env.example` with fake values.
- Ensure `.env` is ignored.
- Recommend rotating exposed secrets.
- Do not print full secret values in output.

## Authentication review

Check:

- Protected routes require authentication.
- Auth middleware cannot be skipped.
- Session/token expiration is enforced.
- JWT signatures are verified.
- JWT algorithms are restricted.
- OAuth state is validated.
- Redirect targets are validated.
- Passwords are hashed safely.
- Reset tokens are time-limited and single-use.

## Authorization review

For every read/write/delete/export/share action:

- Verify object-level authorization.
- Ensure tenant/org/workspace scoping.
- Do not trust client-provided owner IDs.
- Avoid leaking whether another user's object exists.
- Add negative tests.

## Injection review

Search for:

- Raw SQL string interpolation
- Shell command string construction
- `eval`
- Dynamic imports from user input
- Template injection
- Unsafe HTML insertion
- Unsafe regex construction
- NoSQL query injection

Fix with:

- Parameterized queries
- `execFile` instead of shell strings
- Allowlists
- Escaping/sanitization
- Runtime validation

## File upload review

Validate:

- File size
- MIME type
- Magic bytes
- Extension
- Storage path
- Filename normalization
- Path traversal prevention
- Public/private storage settings

## SSRF review

For user-controlled URLs:

- Require `https`
- Use host allowlists
- Block private IPs and metadata service IPs
- Revalidate redirects
- Limit response size
- Set timeouts

## XSS review

Check:

- `dangerouslySetInnerHTML`
- `innerHTML`
- Markdown rendering
- Rich text rendering
- User-controlled URLs
- Inline scripts
- Missing CSP

## Sensitive logging

Remove or redact:

- Cookies
- Authorization headers
- Passwords
- API keys
- Tokens
- Payment details
- Sensitive personal data
- Full request bodies for sensitive endpoints

## Required tests

Add negative tests for:

- Accessing another user's resource
- Unauthenticated access
- Invalid token/session
- Malicious input
- Invalid webhook signature
- Upload traversal attempt
- Unsafe redirect attempt

## Output format

```md
# Security Hardening Summary

## Critical vulnerabilities

## Fixes applied

## Secrets found

Do not include full values.

## Authorization tests added

## Security scans run

## Remaining security risks
```
