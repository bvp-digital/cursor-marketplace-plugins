---
name: jira-general
description: Explains when to use which Jira project and enforces English for ticket content. Use when project context is unclear or when creating tickets.
---

# Jira Project Selection

Always apply this when creating or updating Jira tickets.

## Project Overview and Mapping

- Read the project list from the plugin config: `config/projects.json` in the jira-team-workflows plugin directory, or `.cursor/jira-team-workflows-config.json` in the workspace if present.
- Use the `projects` array to build the project overview (key, name, website) and to know which project to use for which product. If no config is found, ask the user which Jira project applies.

Example structure: each project has `key`, `name`, `website` (or null), and optionally `componentsRequired` and `components` for component rules.

## Rules

- Ensure project context is clear before creating a ticket.
- If context is ambiguous, ask which project this is for.
- All ticket content must be written in English.
- UI labels may stay in German when they are part of the product.
