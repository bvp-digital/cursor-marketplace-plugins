---
name: jira-userstory
description: Checks if a Jira ticket is ready for dev. Supports the PO in creating Stories and Tasks by asking questions, proposing concrete text, and iterating until ready. For bugs, use jira-bug.
---

# Jira User Story And Task Ready For Dev Check

Always apply this check when creating or updating Stories or Tasks. Support the PO by evaluating tickets against the Definition of Ready and guiding them to add missing information until the ticket is ready. For bugs, use `jira-bug`.

## DoR Checklist

### INVEST Criteria

| Criterion | Meaning | Check Question |
|-----------|---------|----------------|
| **Independent** | No dependencies on other tasks | Can the ticket be implemented on its own based on the description? |
| **Valuable** | Clear benefit | Is the business or user value evident? |
| **Estimable** | Can be estimated | Is the scope clear enough to estimate? |
| **Small** | Small enough | Does the description suggest one focused scope? |
| **Testable** | Verifiable | Are acceptance criteria and minimal QA steps defined? |

### Context Criteria

- Target audience
- Goal
- Technical requirements only if they are certain and necessary

## Workflow

### Assessment

1. Load the existing ticket.
2. Go through the checklist.
3. Output a structured assessment with concrete improvement suggestions.

### Creation

When the PO wants to create a Story or Task, guide them until all criteria pass.

#### Story Questions

- Who is this for?
- What should the user be able to do?
- Why does this matter?

Optional if helpful:

- Data source
- Design
- Specific testing info
- Scope
- Dependencies
- QA testing steps
- Technical context only if certainly correct and crucial

#### Task Questions

- What is the outcome of this task?
- What are the steps to complete it?
- Is this one focused task, or should it be split?
- Does this depend on other tickets or work?
- How do we know when it is done?
- What minimal QA steps should be followed?
- Any technical constraints or environments to mention?

#### Propose Concrete Text

- **Story**: Use user story format plus acceptance criteria
- **Task**: Use objective, numbered steps, completion criteria, and dependencies

#### Iterate Until Ready

After each user response, reassess. If not ready, ask the next missing question or propose the next concrete addition. If ready, confirm and proceed.
