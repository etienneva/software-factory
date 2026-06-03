# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Purpose

This is a **Software Factory** — a reference repository of agents, prompts, templates, and standards used to bootstrap and run AI-assisted software projects. It is not an application; it contains no build system, tests, or runnable code.

## Repository Structure

```
agents/       — AI agent persona definitions (Product, CTO, Backend, Frontend, QA, DevOps-Security)
prompts/      — Reusable prompt scripts for key activities (create-project, generate-mvp, debug, etc.)
standards/    — Non-negotiable rules applied to all projects spawned from this factory
templates/    — Fillable documents used to kick off or document a project
```

## Project Lifecycle

Every project generated from this factory follows this cycle (defined in `standards/workflow.md`):

**Brief → Product → Architecture → Backlog → Dev → QA → Deploy → Monitor**

1. Fill `templates/project-brief.md`
2. Run the `prompts/create-project.md` prompt to generate `product.md`, `architecture.md`, `roadmap.md`, `backlog.md`, `database.md`, `api.md`, and first GitHub issues
3. Each backlog task → feature branch → PR → review → merge develop → merge main

## Default Tech Stack (`standards/tech-stack.md`)

Any deviation must be justified in the target project's `architecture.md`.

| Layer | Technology |
|---|---|
| Frontend | Next.js, React, TypeScript, Tailwind |
| Backend / DB | Supabase, PostgreSQL |
| Auth | Supabase Auth |
| Payments | Stripe |
| Deploy | Vercel |
| Monitoring | Sentry |
| Analytics | PostHog |
| Unit tests | Vitest |
| E2E tests | Playwright |
| CI/CD | GitHub Actions |

## Architecture Principles (`standards/architecture.md`)

- Frontend: display and user interactions only — no critical business logic.
- Backend (Supabase): owns all business logic, permissions, and validations.
- External services must always be encapsulated; never depend directly on a single vendor.
- Avoid premature microservices and over-engineering.

## Git Flow (`standards/git-flow.md`)

- `main` — production only; direct commits forbidden.
- `develop` — integration branch.
- `feature/*` — one branch per issue/task.
- `hotfix/*` — urgent production fixes only.
- Every PR must document: objective, changes, impacts, tests performed. No merge without review.

## Agent Roles

Each agent file in `agents/` defines a specialized AI persona with a fixed response format:

- **Product** — transforms a brief into MVP, user stories, backlog, and KPIs.
- **CTO** — owns architecture, technical decisions (ADRs), and tech debt management.
- **Backend** — data model, API, migrations, security, robustness.
- **Frontend** — UI components, responsive design, UX flows, accessibility (mobile-first).
- **QA** — test plans, regression, acceptance validation, Go/No-Go recommendation.
- **DevOps-Security** — CI/CD pipeline, secrets management, monitoring, production checklist.

When acting as one of these agents, follow the response format defined in the relevant `agents/*.md` file.

## Definition of Done (`standards/definition-of-done.md`)

A PR cannot be merged unless all of the following are true:
- Acceptance criteria validated by Product Agent
- Code compiles without error and meets coding standards
- Unit and functional tests pass, critical scenarios covered
- Documentation updated, significant decisions recorded
- Permissions verified, no secrets exposed
- Feature is deployable with no major regressions

## Coding Standards (`standards/coding-standards.md`)

- `camelCase` for variables and functions; `PascalCase` for components.
- One file = one responsibility.
- Prefer small functions with a single responsibility.
- Comment only non-obvious logic or important trade-offs — never the obvious.
- Refactor on the second significant duplication.

## Project Templates

| Template | Use case |
|---|---|
| `template-saas-next-supabase.md` | Standard SaaS product |
| `template-ai-app.md` | AI assistant, document analysis, agentic workflows |
| `template-internal-tool.md` | Back-office, CRM, reporting tools |

When bootstrapping a new project, copy the matching template as the starting point for `architecture.md`.
