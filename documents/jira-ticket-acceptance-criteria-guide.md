# Acceptance Criteria — Writing Guide

Acceptance criteria define when a ticket is **done**. They must be **specific**, **testable**, and **independent** where possible.

## Format

Use a bullet list. Each criterion should answer: *How would a reviewer verify this?*

**Good:**
- The login page should be responsive on mobile, tablet, and desktop viewports.
- Email field shows an error when the value is empty or invalid.
- Submitting valid credentials shows a success message without reloading the page.

**Bad:**
- Login works well.
- Good UX.
- Code is clean.

## Deriving criteria from the description

| User says | Infer these criteria |
|-----------|----------------------|
| "login page with HTML and JavaScript" | Form with email/password; client-side validation; submit handler without full reload |
| "responsive" | Layout adapts at common breakpoints; no horizontal scroll on mobile |
| "secure login" | Password field masked; no credentials logged to console in production guidance |
| "connect to API" | Document expected API contract; handle loading and error states |

## UI / frontend checklist (use when relevant)

- [ ] Page renders without console errors
- [ ] Layout is responsive (viewport meta tag, flexible widths)
- [ ] Form fields have labels and accessible names
- [ ] Validation messages appear next to invalid fields
- [ ] Primary action (submit) is clearly visible
- [ ] Success and error feedback is shown to the user

## Minimum bar

Every ticket must have **at least one** acceptance criterion. If the user provides one explicitly (e.g. "The login page should be responsive"), **include it verbatim** in the output and add complementary criteria only when they clearly support the described feature.

## Example — login page ticket

**User-provided criterion:**
> The login page should be responsive

**Recommended full set:**
- The login page should be responsive on mobile and desktop screen sizes.
- The page includes labeled email and password inputs.
- Invalid or empty inputs display inline error messages.
- Valid form submission is handled in JavaScript without a full page reload.
