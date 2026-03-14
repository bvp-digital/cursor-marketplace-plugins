---
name: jira-figma
description: Use Figma MCP when the user shares a Figma link to enrich Jira tickets with design context. Use when creating or updating tickets that reference a design.
---

# Jira and Figma

When the user provides a Figma link and the Figma MCP (cloud) is available, use it to improve ticket quality.

## When to use

- User shares a Figma URL (e.g. file, frame, or node link) in the context of a Story or Task.
- You need design context for acceptance criteria or a "Design context" snippet in the ticket.

## How to use

1. Resolve the Figma link (file key, node ID if present) using the Figma MCP tools available in your environment (e.g. get file, get node, or equivalent read-only calls).
2. Fetch design context: file name, page names, frame/screen names, and relevant component names.
3. Summarise in PO-friendly language (no low-level implementation detail).
4. Suggest a short "Design context" paragraph or 1–2 acceptance criteria for the ticket; include the Figma link in the ticket description.

## Constraints

- Use only read-style Figma tools (get file, get node, list frames/components). Do not create or update any design content.
- If no design exists, follow the planning workflow: ask whether a Design Briefing ticket should be created; do not invent design details.
