# Architect 2.0: product decisions and evaluation map

## Reference review (official product pages, checked September 2026)

This is a focused review of the interaction patterns relevant to Architect, not a feature-for-feature comparison. These products evolve quickly; links below point to their current public product or documentation pages.

| Product | Distinctive strength and reason users choose it | Pattern Architect should learn from |
|---|---|---|
| [Replit Agent](https://replit.com/products/agent) | Prompt-to-app in a browser workspace, with preview, integrations, testing, and deployment. It also supports continuing work from imported repositories and broader framework choices. | Keep setup and preview close to the build conversation. Make progress observable and make deployment a natural continuation of building. |
| [Lovable](https://lovable.dev/guides/how-to-publish-a-web-app) | Fast app creation aimed at reducing the gap between an idea and a shareable app; its publishing guidance emphasizes GitHub-backed changes and staging/production separation. | Treat publishing as a user decision with a stable live version and reversible changes, not as an invisible side effect. |
| [Vercel v0](https://v0.dev/docs/github) | UI-oriented generation connected to a production path; its Git integration uses branches and commits and supports pull-request review before merge. | Make the proposed change reviewable and protect the production branch while iterating. |
| [Cursor Agent](https://prod.cursor.com/help/ai-features/agent) | A codebase-first developer workflow: search and edit multiple files, run commands, and present changes in a diff while the developer remains in the loop. | Developers need to see touched files, command/check outcomes, and review diffs as part of the same task. |
| [OpenAI Codex](https://openai.com/codex/) | Delegated engineering tasks across codebases, with parallel work environments, review-ready changes, and longer-running work. | When work becomes autonomous, preserve isolation, inspectable results, and human control over what ships. |

### Product opportunity for Architect

The market already teaches users to prompt, preview, connect a repo, and deploy. Architect should differentiate through a **shared decision trail** that works for a first-time builder and an experienced engineer: state assumptions, agree on a small slice, show the running behavior, expose the source/check evidence, then explain release blockers. The demo's two modes are a first expression of that idea. The assignment prototype does not implement the underlying AI runtime or integrations, so it should be presented as a UX proposal with honest boundaries.

### Research limits

This review uses public product pages and official documentation, not hands-on usability testing or a full screen-by-screen audit of every listed platform. A later product discovery pass should test the core journeys with novice builders and developers, especially repository import, change review, and deployment readiness.

## Product premise

People who want software often begin with a job to be done, while developers often begin with an existing codebase and constraints. Architect should let both start where they are and converge on the same reviewable artifact: a scoped change with a preview, checks, and a clear path to ship.

This prototype expresses that premise as one project workspace rather than separate “no-code” and “developer” products. Guided mode explains the next decision. Developer mode exposes files and checks. The user can switch modes without losing project context.

## Why these choices belong

- **Scope before generation:** Non-technical users need help turning a broad idea into a small, testable first release. A plan that can be edited and approved makes the system's assumptions visible.
- **Preview beside the conversation:** People can validate the result while discussing changes. The leave request/manager review sample demonstrates one complete role-based workflow.
- **Source and checks in the same workspace:** Developers need to inspect what changed and whether core behavior passes before shipping. The sample code and checks are explicitly labeled as illustrative.
- **Import and GitHub as an explicit flow:** Existing projects are valuable starting points. Users should inspect the detected stack and branch before granting access or changing code.
- **Deployment readiness, not a magic button:** A database, authentication, and secrets affect whether an app is safe to ship. Showing missing prerequisites models responsible release decisions.
- **Agent permissions before action:** Agent capability should be understandable in terms of task, allowed tools, and human approval. New agents begin as drafts; the demo does not claim to execute them.
- **Browser-only demo sign-in:** Authentication is part of the requested end-to-end journey. A local demo session illustrates the entry point while clearly stating that it is not real account security.

## Intended end-to-end journeys

### Start from an idea

Sign in → describe a user problem → name the project → inspect the brief → approve a first scope → build → try the preview as each role → iterate → inspect files/checks → review integrations and deployment readiness.

### Continue existing code

Sign in → connect GitHub → select a repository and branch → review detected framework/setup and permissions → import read-only → inspect the project summary and preview → request a scoped change → review diff/checks → commit or open a PR → deploy.

The second journey is represented with a simulated repository and import review. Repository permissions, code access, branch operations, commits, and deployment are not connected.

## Audience coverage

| Need | Non-technical builder | Developer | Prototype evidence |
|---|---|---|---|
| Get started | Idea prompt and editable scope | Repository import entry point | Sign-in, project brief, GitHub screens |
| Understand output | Role-based clickable preview | File view and scripted checks | Leave workflow, Files, Checks |
| Make a change | Natural language follow-up | Change review and project settings | Chat iteration, diff entry, settings |
| Use agents | Plain-language task and guarded actions | Framework choice and tool visibility | Agent list, draft creation, test trace |
| Ship safely | Readiness checklist and plain-language blockers | Data/secrets view, logs, rollback affordance | Data and Deployments screens |

## Important limits and next build steps

This is a static interaction prototype, not a production application. It has no backend, secure authentication, real AI/model provider, generated source tree, test runner, GitHub OAuth/app, database, or hosting integration. Browser storage is per-device and can be edited by the user.

If continuing beyond the assignment demo, build in this order:

1. Server-backed identity, workspace membership, and project persistence.
2. Real project import using a narrowly scoped GitHub App installation and read-only first pass.
3. A job runner that generates changes in an isolated environment, runs checks, and streams observable progress.
4. Reviewable diffs and explicit commit/PR actions.
5. Preview deployments with secret management, permission boundaries, logs, and rollback.
6. Agent runtime with framework adapters, tool scopes, budgets, test cases, and human approval for consequential actions.

## Assignment coverage

Authentication, homepage, chat, preview, agents, build progress, GitHub, generated-app deployment, integrations, history, settings, and guided/developer modes have prototype screens or flows. The externally hosted take-home and submission record remain separate tasks: deploy this static repo, then enter both its live URL and GitHub URL in the assignment Submit tab.
