---
agent: 'agent'
description: 'List GitHub issues for this repository with optional filters'
argument-hint: 'Optional: state (open/closed/all), label, or assignee'
---

List the GitHub issues for the current repository using the `gh` CLI.

Run the following command in the terminal:

```bash
gh issue list --state ${input:state:Issue state to filter by — open, closed, or all (default: open)} --limit 50 --json number,title,state,labels,assignees,createdAt
```

If the user provided a label filter, append `--label "${input:label:Label to filter by (optional — leave blank to skip)}"` to the command.
If the user provided an assignee filter, append `--assignee "${input:assignee:GitHub username to filter by (optional — leave blank to skip)}"` to the command.

After running the command, present the results as a Markdown table with these columns:

| # | Title | State | Labels | Assignee | Created |

Rules:
- Sort by most recently created first
- If a field is empty, show `—`
- Highlight any issues that are more than 30 days old with a ⚠️ prefix on the title
- After the table, show a brief summary: total count, how many are open vs closed
