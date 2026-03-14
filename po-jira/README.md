# Jira Team Workflows

Cursor plugin for Jira-focused planning and ticket creation. Use it as the primary way to create and manage Jira tickets.

## For Product Owners

**Primary use:** Create Jira tickets (Stories, Tasks, Bugs) that are ready for dev.

**Main flow:**

1. Describe what you want (feature, task, or bug).
2. The agent gathers details and checks whether a Figma design is relevant.
3. Content is validated with the `ticket-auditor` agent (ready-for-dev check).
4. You review the plan; when satisfied, confirm with **"build"** to create the tickets in Jira.

**Split a story:** Use the `/split` command (or ask to split a story). Provide the story key (e.g. `PROJ-123`) and say which functionality belongs in which ticket.

**Required:** Set these environment variables so the Jira MCP can connect:

- `JIRA_USERNAME` – your Jira user (e.g. email)
- `JIRA_API_TOKEN` – a Jira API token (create in Atlassian account settings)

## Optional: Figma MCP (cloud)

For better ticket quality when designs exist, the plugin can use the Figma MCP (cloud, API-based). When you share a Figma link, the agent can fetch design context (file name, frames, components) and suggest a short "Design context" or acceptance criteria for the ticket.

Set `FIGMA_API_KEY` to your Figma personal access token (Figma Settings > Account > Personal access tokens). If you do not use Figma, remove the `figma` server from the plugin’s `mcpServers` in `.cursor-plugin/plugin.json` to avoid startup errors.

This plugin uses only read-style Figma tools; it does not create or update design content.

## Includes

- Jira rules for planning, ticket standards, MCP safety, and story splitting
- Jira skills for stories, bugs, formatting, attachments, and project selection
- `ticket-auditor` agent
- `/split` command
- `mcp-atlassian` MCP server wiring

## Local path

This plugin is installed locally at:

`~/.cursor/plugins/local/po-jira`

## MCP setup (Jira)

The bundled MCP server uses the shared Jira URL and project filter. Credentials come from environment variables:

- `JIRA_USERNAME`
- `JIRA_API_TOKEN`

If your team uses different credentials per user, each user sets their own values before using the Atlassian MCP server.

The plugin includes an optional `figma` server in its MCP config (Figma cloud/API). Set `FIGMA_API_KEY`; if you do not use Figma, remove the `figma` entry from `mcpServers` in `.cursor-plugin/plugin.json`.

## Customization (other teams / orgs)

**Config:** Projects and component rules are read from the plugin’s plugin config (see below). Projects, component requirements, and the Acceptance Criteria field ID are configurable. The plugin ships with `config/projects.json` containing `acceptanceCriteriaFieldId` and a `projects` array (`key`, `name`, `website?`, `componentsRequired?`, `components?`). For any project with `componentsRequired: true`, tickets must have one of the listed `components`.

- **Override:** Copy `config/projects.json` from the plugin into your workspace as `.cursor/jira-team-workflows-config.json` and edit it. The agent will use this file when present.
- **Jira MCP:** In the plugin’s `.cursor-plugin/plugin.json`, set `JIRA_PROJECTS_FILTER` in the `mcp-jira` server `env` to a comma-separated list of project keys to match your config.

## Notes

- Source rules and skills were copied from the Jira workspace and normalized for plugin use.
- Embedded secrets and machine-specific paths were removed.
- References use plugin-safe skill, rule, command, or agent names.
