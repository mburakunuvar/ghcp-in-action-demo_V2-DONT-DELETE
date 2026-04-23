---
name: "Issue 1 — Azure Static Web App Setup"
about: "Pre-demo setup: deploy blank pages to Azure Static Web Apps"
title: "Azure Static Web App Setup (Pre-demo)"
labels: "pre-demo"
---

## Task
Set up the Azure Static Web App before the live demo begins. This gets the blank pages deployed to Azure so the live URL is accessible from the start of the demo.

### Steps
1. Go to the [Azure Portal](https://portal.azure.com) and create a new **Static Web App**
2. Connect it to this GitHub repository (select the `main` branch)
3. Set `app_location` to `/` and leave `output_location` blank
4. Copy the **deployment token** from the Azure Portal
5. In this repository, go to **Settings → Secrets and variables → Actions**
6. Add a new secret named `AZURE_STATIC_WEB_APPS_API_TOKEN` and paste the token
7. Go to the **Actions** tab in this repository, select the **Azure Static Web Apps CI/CD** workflow, and click **Run workflow** to manually trigger the deployment
8. Verify the live URL is accessible before going on stage

> ✅ Once this issue is complete, the app is live and the live demo can begin at **Issue #2**.

## Note
This issue is done **before** the live demo — not during. Close it once the live URL is confirmed working.
