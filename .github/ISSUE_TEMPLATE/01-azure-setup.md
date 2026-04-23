---
name: "Issue 1 — Azure Static Web App Setup"
about: "Pre-demo setup: deploy blank pages to Azure Static Web Apps"
title: "Azure Static Web App Setup (Pre-demo)"
labels: "pre-demo"
---

## Task
Set up the Azure Static Web App before the live demo begins using **CLI commands only** — no Azure Portal access required. Copilot will handle the deployment end-to-end and ask the user for information only when needed.

### Steps (automated via CLI)
1. **Authenticate with Azure** — Run `az login` to sign in. If the user has multiple subscriptions, ask which one to use and set it with `az account set --subscription <id>`.
2. **Create a resource group** (if needed) — Run `az group create --name <name> --location <region>`. Ask the user for a preferred resource group name and Azure region, or suggest defaults (e.g., `rg-static-web-demo`, `westeurope`).
3. **Create the Static Web App** — Run:
   ```bash
   az staticwebapp create \
     --name <app-name> \
     --resource-group <rg-name> \
     --source https://github.com/<owner>/<repo> \
     --branch main \
     --app-location "/" \
     --output-location "" \
     --login-with-github
   ```
   Ask the user for a preferred app name or suggest a default.
4. **Retrieve the deployment token** — Run:
   ```bash
   az staticwebapp secrets list --name <app-name> --resource-group <rg-name> --query "properties.apiKey" -o tsv
   ```
5. **Store the token as a GitHub Actions secret** — Run:
   ```bash
   gh secret set AZURE_STATIC_WEB_APPS_API_TOKEN --body "<token>"
   ```
6. **Trigger the deployment workflow** — Run:
   ```bash
   gh workflow run "Azure Static Web Apps CI/CD" --ref main
   ```
7. **Verify the deployment** — Retrieve the live URL with:
   ```bash
   az staticwebapp show --name <app-name> --resource-group <rg-name> --query "defaultHostname" -o tsv
   ```
   Then confirm the URL is accessible (e.g., `curl -s -o /dev/null -w "%{http_code}" https://<hostname>`).

8. **Update `azure_resource.md`** — After successful deployment, update the `azure_resource.md` file in the repository root with the actual resource details (subscription, resource group, app name, region, live URL, default hostname). Commit and push the change so the deployment info is tracked in the repo.

### What the agent asks the user (only if needed)
- Azure subscription (if multiple exist)
- Preferred resource group name and region (or confirm defaults)
- Preferred Static Web App name (or confirm default)

> ✅ Once this issue is complete, the app is live and the live demo can begin at **Issue #2**.

## Note
This issue is done **before** the live demo — not during. Close it once the live URL is confirmed working.
