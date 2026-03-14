---
name: jira-bug
description: Workflow for reporting bugs in Jira. Checks for duplicates, ensures bug content is ready for dev, then creates the ticket.
---

# Jira Bug Reporting Workflow

This skill guides the agent through the process of reporting a bug in Jira and avoiding duplicates.

## Workflow

### 1. Determine Target Project

Ask the user which project the bug belongs to, or infer it when the context is clear.

### 2. Search For Duplicates

Before creating any ticket, search for existing issues in the target project.

- Tool: `jira_search`
- JQL: `project = PROJECT_KEY AND (summary ~ "KEYWORD" OR description ~ "KEYWORD") ORDER BY created DESC`

### 3. Present Findings

- If duplicates are found, list the top 3 relevant tickets and ask whether one matches the issue.
- If no duplicates are found, continue to the ready-for-dev check.

### 4. Ensure Bug Is Ready For Dev

Mandatory fields:

- Steps to reproduce as a numbered list
- Expected behaviour
- Observed behaviour
- Environment: dev, stage, or prod
- Platform: App, Web, or CMS

Optional fields:

- Device or browser

### 5. Create The Bug Ticket

Only proceed if the user confirms it is a new issue or explicitly wants a new ticket despite duplicates, and the bug is ready for dev.

Constraints:

- Follow `ticket-creation` and `jira-mcp-allowlist`
- Use `ticket-auditor` to validate content
- Put Acceptance Criteria in the custom field when they are needed
- Set the correct component when required
