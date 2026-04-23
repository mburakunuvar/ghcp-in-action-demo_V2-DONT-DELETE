---
name: "Issue 5 — Azure Deployment"
about: "Verify and trigger deployment after home, primitives & APE are done"
title: "Azure Deployment"
labels: "agent-mode"
---

## Task
The application is already deployed to Azure Static Web Apps and a CI/CD workflow is in place (`.github/workflows/azure-static-web-apps.yml`).

> ⚠️ **Important**: The workflow only triggers on `workflow_dispatch` — **not on push**. Do NOT push to remote expecting a deployment. Trigger it manually with:
> ```bash
> gh workflow run "Azure Static Web Apps CI/CD"
> ```

For this step:
1. Confirm Issues #2 (Home Page), #3 (Primitives Page), and #4 (APE Page) are closed
2. Verify the latest changes are live at the deployed URL
3. If anything needs to be re-triggered, trigger the workflow manually using the command above

> ⚠️ **Prerequisite**: Issues #2, #3, and #4 must be closed before deployment. Code Review and Performance (Issue #6) happens after this step.

## Assigned to
Agent Mode in IDE (VS Code) — prompt: *"Issues 2, 3, and 4 are resolved. Verify the app is deployed and the live site reflects all the latest changes. Trigger a re-deployment if needed."*

## Pre-flight requirement
The presenter must have already completed Issue #1 (Azure Static Web App Setup) before the demo:
- Azure Static Web App created and connected to this repository
- `AZURE_STATIC_WEB_APPS_API_TOKEN` added to the repository secrets

## Completion
Once deployment is verified and the live site is confirmed working, close this issue:

```bash
gh issue close 5 --repo <owner/repo>
```
