# Suggested Changes — Guide

The **Suggested changes** section connects the JIRA ticket to actionable work in the local project referenced by **Project URL**.

## Purpose

Help the assignee start implementation immediately by showing:

- Which files to create or modify
- Full or partial code aligned with the ticket description and acceptance criteria
- Paths rooted in the provided project folder

## When Project URL is provided

1. Treat the path as a **local directory** on the developer machine.
2. List files that exist or should exist (e.g. `login.html`, `styles.css`, `app.js`).
3. For an **empty project folder**, propose new files with complete starter content.
4. For an **existing project**, read or infer structure and propose minimal changes.

## Output structure

```markdown
## Suggested changes

Apply the following changes to `/path/to/project/login.html`

<full HTML file content>

---

Apply the following changes to `/path/to/project/app.js`

<full JS file content or diff>
```

## Rules

| Rule | Detail |
|------|--------|
| **Path accuracy** | Every file path must be under the Project URL from the input. |
| **Intro line** | Start each file block with: `Apply the following changes to \`<path>\`` |
| **Greenfield** | Provide complete file contents (DOCTYPE, structure, styles, scripts as needed). |
| **Match stack** | If user asks for HTML + JavaScript, do not suggest React unless specified. |
| **Meet AC** | Code should satisfy listed acceptance criteria (responsive, validation, etc.). |
| **No secrets** | Do not embed real API keys or passwords in examples. |
| **Simulated backend** | For login without backend, use `console.log`, `alert`, or commented `fetch()` placeholder. |

## Responsive login page — implementation notes

When acceptance criteria include **responsive**:

- Include `<meta name="viewport" content="width=device-width, initial-scale=1.0">`
- Use flexible widths (`max-width`, `%`, `box-sizing: border-box`)
- Center card layout with flexbox on `body`
- Avoid fixed pixel widths that break on small screens

When description asks for **JavaScript validation**:

- Prevent default form submit
- Validate email format and password length
- Show inline error messages per field
- Provide user feedback on successful validation

## Empty project behavior

If the project folder exists but has no files:

- Create `login.html` as a single-file solution (HTML + CSS + JS) unless the repo convention suggests separate files.
- State in the ticket description that this is a new file in an empty project.

## Missing Project URL

If no project path is given, output:

```
Suggested changes: Project URL required to generate file-level suggestions.
```
