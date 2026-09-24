# Architect — take-home prototype

A dependency-free, browser-first prototype of the Architect 2.0 product flow. It is designed to be easy to run locally and publish as a static site.

## Run locally

Open `index.html` in a browser, or serve this directory with any static file server. For example:

```sh
python3 -m http.server 8000
```

Then visit `http://localhost:8000`.

## Demo path

1. Open **Leave Management** from the dashboard.
2. Review the plan in the conversation and choose **Build it**.
3. Submit a sample leave request, switch to manager view, and approve or decline it.
4. Ask to show remaining leave days to see an iteration and new version.
5. Switch to **Developer** mode to inspect the sample file and scripted checks.
6. Explore Agents, Data & integrations, GitHub, Deployments, and History from the sidebar.

## Prototype boundary

The leave-management preview and its sample request interaction work in the browser. The demo state persists in `localStorage`. AI generation, repository access/import/push, database connection, agent execution, and deployment of the generated app are simulated. The prototype never asks for GitHub credentials or secret values. Deploying this static take-home website is separate from the in-product deployment simulation.

## Publish

This is a static site: publish the repository with Vercel or another static host. No environment variables or external service credentials are required for the prototype.
