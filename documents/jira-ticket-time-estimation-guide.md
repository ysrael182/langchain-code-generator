# Time Estimate — Guide

The **Time estimate** field supports numeric values or deferred placeholders.

## Allowed values

| Value | When to use |
|-------|-------------|
| `0` | Placeholder; team has not sized the work yet |
| `To be defined` | Scope unclear or depends on discovery |
| `1`–`8` (typical) | Small to medium implementation tasks (hours or story points per team convention) |

## Heuristics (single developer, familiar stack)

| Task type | Typical estimate |
|-----------|------------------|
| Single static HTML/CSS page (new) | 2–4 |
| Add JavaScript validation to existing form | 1–2 |
| New page + basic styling + validation | 3–5 |
| Integrate with backend API (first endpoint) | 5–8 |
| Refactor or bug fix with known root cause | 1–3 |

## Rules

1. If the user does **not** provide an estimate, infer one only when scope is **clear** (e.g. greenfield login page with HTML/JS).
2. If scope is vague, output `To be defined` or `0` — do not guess aggressively.
3. If the user **does** provide an estimate, preserve it in the output unless it is clearly inconsistent with scope (then note the assumption in the description).
4. Treat estimates as **relative sizing**, not contractual deadlines, unless the team defines otherwise.

## Example — login page

**Input:** Create a login page with HTML and JavaScript, responsive.

**Reasonable estimate:** `3` — one new page, inline CSS, basic validation, no backend.

**Output field:**
```
Time estimate: 3
```
