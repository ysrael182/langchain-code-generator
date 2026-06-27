# JIRA Ticket — Input and Output Schema

## Inputs (from user / form props)

| Field | Required | Type | Description |
|-------|----------|------|-------------|
| **Ticket name** | Yes | string | Short title for the JIRA issue. Example: `Create a login page` |
| **Description** | Yes | string | What the user wants built or changed. Can include tech stack hints. |
| **Project URL** | Yes* | string (local path) | Absolute or workspace-relative path to the local project folder. Example: `/Users/israel.caceres/Documents/lanchain-course/login_page` |
| **Assigned to** | No | string | Person or team responsible. Example: `Israel`. Omit or leave blank if unknown. |

\* Required when **suggested changes** are expected. If no project path is given, the ticket may still be generated but suggested changes should state that a project path is needed.

### Input example

```
Ticket name: Create a login page
Description: I want a login page. Implement a login page with JavaScript and HTML.
Project URL: /Users/israel.caceres/Documents/lanchain-course/login_page
Assigned to: Israel
```

Additional acceptance criteria may appear in the description or be inferred by the assistant. If the user provides explicit acceptance criteria in the description, carry them forward into the output unchanged when possible.

---

## Outputs (generated JIRA ticket)

| Field | Required | Type | Description |
|-------|----------|------|-------------|
| **Ticket name** | Yes | string | Same as input unless a minor clarity fix is needed (e.g. typo: `Createa` → `Create a`). |
| **Description** | Yes | string | Expanded or cleaned description. Keep user wording; add structure only if it improves clarity. |
| **Time estimate** | Yes | number or string | Story points or hours. Use a number when scope is clear (e.g. `3`). Use `0` or `To be defined` when scope is unknown. |
| **Acceptance criteria** | Yes | list or string | Testable conditions for done. At least one criterion required. |
| **Assigned to** | No | string | From input, or `To be defined` if not provided. |
| **Suggested changes** | Yes* | string (markdown) | File paths and proposed code under the project URL. |

\* Required when a **Project URL** is provided and the task involves implementation.

### Output format (markdown template)

```markdown
## Ticket name
Create a login page

## Description
I want a login page. Implement a login page with JavaScript and HTML.

## Time estimate
3

## Acceptance criteria
- The login page should be responsive
- The page includes email and password fields with client-side validation
- Form submission is handled without full page reload

## Assigned to
Israel

## Suggested changes

Apply the following changes to `/Users/israel.caceres/Documents/lanchain-course/login_page/login.html`

<file content or diff here>
```

---

## Field rules

### Ticket name
- Keep concise (under ~80 characters).
- Use imperative or feature naming: `Create a login page`, `Add password reset flow`.
- Fix obvious typos only.

### Description
- Restate the user goal in 1–3 sentences.
- Mention technologies when the user specified them (HTML, JavaScript, React, etc.).
- Do not add requirements the user did not imply unless they are standard for the task type (e.g. basic validation on a login form).

### Time estimate
- **Small, well-defined UI task (single page, static HTML/JS):** typically `2`–`5` (hours or story points per team convention).
- **Unknown scope:** `To be defined` or `0`.
- Document assumption in description if estimate is approximate.

### Acceptance criteria
- Bullet list preferred.
- Each item starts with an observable outcome: "The …", "User can …", "Page …".
- Include responsive/layout criteria when relevant for UI work.
- Include validation, accessibility, or error-handling criteria when implied by the task.

### Assigned to
- Copy from input when present.
- Use `To be defined` when absent.

### Suggested changes
- Always prefix with: `Apply the following changes to <absolute-or-project-relative-file-path>`.
- One section per file.
- For new files in an empty project, provide the **full file content**.
- For existing files, show the **complete updated file** or a clearly labeled patch.
- Paths must live under the provided **Project URL**.
