# fix-codebase_frontend.md

Use this prompt to repair frontend quality, correctness, accessibility, security, and performance.

## Goal

Make the frontend reliable, accessible, secure, and maintainable.

## Agent instructions

Inspect components, routing, state, data fetching, forms, styling, accessibility, and rendering performance.

## Common frontend issues

Find:

- Oversized components
- Duplicated state
- Server state copied unnecessarily into local state
- Missing loading states
- Missing empty states
- Missing error states
- Weak form validation
- Unsafe HTML rendering
- Broken auth state handling
- API calls scattered across components
- Inconsistent styling
- Accessibility failures
- Large lists without virtualization
- Re-render loops
- Large bundles
- Unoptimized images

## Accessibility checklist

- [ ] Buttons are real buttons.
- [ ] Links are real links.
- [ ] Inputs have labels.
- [ ] Errors are associated with fields.
- [ ] Keyboard navigation works.
- [ ] Focus states exist.
- [ ] Dialogs manage focus.
- [ ] Color contrast is acceptable.
- [ ] Icons have accessible labels where needed.
- [ ] Page titles are meaningful.

## Security checklist

- [ ] Avoid unsafe HTML rendering.
- [ ] Sanitize rich text.
- [ ] Validate URLs before rendering links.
- [ ] Do not expose secrets in frontend code.
- [ ] Do not trust client-side authorization.
- [ ] Handle auth expiration safely.

## Performance checklist

- [ ] Large lists are paginated or virtualized.
- [ ] Expensive derived values are memoized where needed.
- [ ] Data fetching avoids waterfalls.
- [ ] Bundle size is measured.
- [ ] Images are optimized.
- [ ] Components do not re-render unnecessarily.

## Required output

```md
# Frontend Repair Summary

## Components inspected

## Correctness issues

## Accessibility issues

## Security issues

## Performance issues

## Fixes made

## Tests added

## Remaining frontend risks
```
