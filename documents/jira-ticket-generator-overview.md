# JIRA Ticket Generator — Knowledge Base Overview

This knowledge base defines how an AI assistant converts informal feature requests into structured JIRA tickets. The assistant reads ticket guidelines and examples from this documentation, optionally inspects a local project path, and produces a complete ticket with suggested code changes.

## Purpose

Turn a short product or engineering request into a JIRA-ready ticket that includes:

- Clear title and description
- Time estimate (when possible)
- Testable acceptance criteria
- Assignee (when provided)
- Concrete suggested changes for files in the referenced local project

## Workflow

1. **Receive inputs** from the user (ticket name, description, project URL/path, optional assignee).
2. **Retrieve relevant guidance** from this knowledge base (format rules, examples, estimation heuristics).
3. **Inspect the local project** at the given path to understand existing files, structure, and gaps.
4. **Generate the ticket** following the output schema below.
5. **Propose suggested changes** as file-specific edits or full file contents when creating new files.

## Scope

This generator is intended for:

- Frontend tasks (HTML, CSS, JavaScript)
- Small feature work with a clear local project folder
- Tickets where acceptance criteria can be derived from the description or common best practices

This generator is **not** intended for:

- Vague requests with no project path when code suggestions are required
- Production deployment or infrastructure tickets without additional context
- Legal, HR, or non-technical JIRA work

## Core principles

- **Preserve user intent** — Do not rewrite the ticket name or description unless clarifying ambiguity.
- **Make acceptance criteria testable** — Each criterion should be verifiable by a reviewer or QA.
- **Ground suggestions in the project path** — Suggested changes must reference real files under the provided local path.
- **Prefer complete files for greenfield work** — When a file does not exist, provide a full suggested file rather than a fragment.
- **Prefer targeted diffs for existing files** — When a file exists, describe what to add or change and why.
- **Time estimates are honest** — Use `0` or `To be defined` when scope is unclear; do not invent precision.

## Related documents

| Document | Contents |
|----------|----------|
| `jira-ticket-input-output-schema.md` | Required inputs and output fields |
| `jira-ticket-acceptance-criteria-guide.md` | How to write good acceptance criteria |
| `jira-ticket-time-estimation-guide.md` | How to estimate or defer time |
| `jira-ticket-suggested-changes-guide.md` | Rules for project-based code suggestions |
| `examples/example-01-login-page.md` | Full input → output example |
