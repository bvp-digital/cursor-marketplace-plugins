---
name: jira-attach-file
description: Workflow for handling file and image attachments on Jira tickets. Use when attachments are relevant for a task, story, or bug.
---

# Jira Attachment Workflow

Images and files can be attached only if they are available to the agent as a local file path.

## When A File Path Is Available

1. Attach via `jira_update_issue` using the `attachments` parameter.
2. Verify first that the file exists and is readable.

## When No File Path Is Available

### Option A: Share Link

If the user provides a share link, the agent can:

- insert the link into the ticket description
- ask the user for a local file path if an actual attachment is required

### Option B: Placeholder And Manual Upload

- Add a placeholder such as `(Screenshot to be attached)`.
- Ask the user to open Jira and attach the file manually.

## Summary

| Situation | Action |
|-----------|--------|
| Local path provided | Attach via `jira_update_issue` |
| Share link only | Insert link or ask for local path |
| No path and no link | Placeholder plus manual upload |
