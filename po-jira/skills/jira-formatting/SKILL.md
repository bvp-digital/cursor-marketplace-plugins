---
name: jira-formatting
description: Provides examples for formatting Jira tickets using both Markdown and Atlassian Document Format (ADF). Use this skill when creating or updating tickets that require rich text formatting.
---

# Jira Formatting Rules

When interacting with the Jira API via the `mcp-atlassian` server, the format depends on the field being updated.

## Description Field

- Use standard Markdown when supported.
- If Markdown tables render as plain text, use Jira Wiki Markup for tables.

### Table Example

```text
|| Parameter || Description || Example ||
| source | The platform | APP |
| status | Event state | true |
```

### Panel Example

```text
{panel:bgColor=#deebff}
h5. General info for implementation
Library, documentation, API, or technical context
{panel}
```

## Acceptance Criteria Field

The Acceptance Criteria field (ID from plugin config `acceptanceCriteriaFieldId`; default `customfield_10092`) must be provided in Atlassian Document Format (ADF) JSON.

### Minimal ADF Document

```json
{
  "version": 1,
  "type": "doc",
  "content": []
}
```

### Bullet List Example

```json
{
  "type": "bulletList",
  "content": [
    {
      "type": "listItem",
      "content": [
        {
          "type": "paragraph",
          "content": [
            { "type": "text", "text": "Criteria 1 works as expected." }
          ]
        }
      ]
    }
  ]
}
```
