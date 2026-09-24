# Architect 2.0 — take-home prototype

Architect is a workspace that helps a builder move from a user problem to a reviewable, testable application slice. Its core idea is **keep the brief, preview, source review, and release readiness in one loop**. Guided mode keeps the experience approachable; Developer mode exposes files and checks without hiding the underlying trade-offs.

## Run locally

Open `index.html` in a browser, or serve this directory with a static file server:

```sh
python3 -m http.server 8000
```

Visit `http://localhost:8000`. No build step or dependencies are required.

## Recommended demo path

1. Sign in with any name, email, and password (or choose the demo Google button). This is browser-only demo authentication.
2. Open **Leave Management** and review the proposed first version. Choose **Build it** to see the progress flow.
3. In the preview, submit a sample leave request, switch to manager view, and approve or decline it.
4. Ask the builder to show remaining leave days to see an iteration and saved version.
5. Switch to **Developer** mode to inspect the sample file and scripted checks.
6. Explore **Agents** and create a draft, then inspect GitHub import, data configuration, deployment readiness, and project history.

The most complete working slice is the leave preview. Requests, manager decisions, demo sign-in, project briefs, agent drafts, and other workspace state persist in this browser using `localStorage`.

## What is real in this prototype

- Browser-only sign-in and sign-out; credentials are not sent anywhere.
- Interactive sample leave request and manager approval workflow.
- Persistent demo state, project brief creation, and agent draft creation.
- Navigable build, preview, change review, configuration, and deployment screens.

## What is simulated

AI generation, code execution, scripted checks, real authentication, GitHub authorization/import/push, database connections, agent execution, and deployment of the generated app. The deployment screen demonstrates readiness and failure/recovery states; it does not publish the leave app. Do not use this prototype with real credentials or employee data.

## Publish this take-home

This is a static site and can be deployed by importing the GitHub repository into Vercel, Netlify, or another static host. Use the repository root as the site root and leave the build command empty; the entry point is `index.html`. Once deployed, add the live URL and this repository URL in the assignment's Submit tab. No live deployment URL is embedded in this repository yet.

## Product rationale

See [Product decisions and evaluation map](PRODUCT_DECISIONS.md) for the intended audience, design choices, trade-offs, feature coverage, and interview-ready explanation.
