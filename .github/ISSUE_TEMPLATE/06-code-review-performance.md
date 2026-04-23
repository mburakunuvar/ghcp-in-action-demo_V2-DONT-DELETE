---
name: "Issue 6 — Code Review and Performance"
about: "AI-powered code review of the live deployed app; findings become new issues"
title: "Code Review and Performance"
labels: "copilot-cli"
---

## Task
Perform a code review of the full application (targeting the live deployed app):

1. **Code quality review** — focus on best practices, error handling, accessibility
2. **Performance review** — focus on asset optimization, render-blocking resources, caching

The findings from each review should be filed as four new GitHub issues using `gh issue create`:
- Fix: missing alt attributes and semantic HTML
- Fix: render-blocking CSS and missing meta tags
- Write and run unit tests for the application
- Deploy latest version to Azure (trigger the existing workflow with `gh workflow run "Azure Static Web Apps CI/CD"`)

After filing the issues, generate a `suggested_improvements.md` report in the repo root summarizing all findings and recommendations from the review.

## Assigned to
Copilot CLI — review the codebase, file the issues, generate the report.

## Note
This step happens after Azure Deployment (#5). The reviews target the live deployed app.

## Completion
Once the issues are created, the report is generated, and changes are committed and pushed, close this issue:

```bash
gh issue close 6 --repo <owner/repo>
```
