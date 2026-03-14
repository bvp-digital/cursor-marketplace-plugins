---
name: jira-split-story
description: Splits a Jira story into two or more tickets. Requires the source story ID and explicit user guidance for how scope and acceptance criteria should be divided.
---

# Jira Split Story Workflow

Trigger: `/split` or an explicit request to split a story.

## Prerequisites

- Source story ID
- User explanation of which functionality belongs in which resulting ticket

## Process

1. Load the source story with `jira_get_issue`.
2. Extract the original description and all Acceptance Criteria from the Acceptance Criteria field (ID from plugin config: `config/projects.json` or `.cursor/jira-team-workflows-config.json`, key `acceptanceCriteriaFieldId`; default `customfield_10092`).
3. Ask the user how the functionality and Acceptance Criteria should be split.
4. Draft the resulting stories.
5. Validate coverage so every original Acceptance Criterion appears in at least one resulting story.
6. Run `ticket-auditor` on each resulting story.
7. Present the plan and ask for confirmation before creation.

## Constraints

- Follow `ticket-creation` and `jira-mcp-allowlist`
- Acceptance Criteria belong in the field ID given in the plugin config (`acceptanceCriteriaFieldId`)
- Never guess where functionality should go
- Do not update the original story unless the user explicitly asks
