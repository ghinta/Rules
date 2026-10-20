---
name: Git and Collaboration Rules
alwaysApply: true
description: Lightweight Git workflow with worktrees, issues, Kanban, PRs/MRs, documentation, architecture, releases, and CI/CD.
---

# Git and Collaboration Rules

## Repository navigation

- MUST keep `README.md` as the central entry point: purpose, setup, development, testing, and links to the board, issues, documentation, CI/CD, and releases.
- MUST make current scope, ownership, progress, and blockers discoverable without insider knowledge.
- SHOULD document the workflow and Definition of Done in `CONTRIBUTING.md` or another obvious location.
- MUST follow existing repository conventions rather than introduce competing tools or processes.

## Issues and Kanban

- SHOULD track non-trivial work in actionable issues with context, clear goals, and acceptance criteria.
- SHOULD use priorities, assignees, labels, milestones, and dependencies when useful.
- MUST keep board states accurate (e.g. Backlog → Ready → In Progress → Review → Done) and highlight blockers.
- MUST link related issues, PRs/MRs, and relevant decisions; MUST NOT mark work done before the agreed Definition of Done is met.
- SHOULD break large work into independently reviewable tasks.

## Branches and worktrees

- SHOULD use a dedicated, clearly named branch per independent change or issue.
- SHOULD prefer Git worktrees for parallel tasks instead of repeated branch switching or stashing.
- MUST preserve uncommitted changes and worktree isolation; MUST NOT discard or modify another task's work without approval.
- MUST NOT rewrite shared history, force-push shared branches, or move published tags without explicit approval.

## Commits and PRs/MRs

- MUST keep commits focused, descriptive, and consistent with repository conventions.
- SHOULD deliver changes through PRs/MRs rather than directly to long-living branches.
- MUST link issues and explain scope, rationale, actual verification, risks, and breaking changes.
- MUST respect reviews, required CI checks, branch protection, and merge strategy.
- MUST NOT claim tests, reviews, approvals, or updates that did not occur.
- SHOULD update the related issues and board as work progresses and after merge.

## Documentation and architecture

- MUST maintain a discoverable `docs/` directory for durable technical and operational documentation, linked from `README.md`.
- SHOULD document architecture using C4 diagrams at the levels useful for the project (context, containers, components), keeping diagrams aligned with implementation.
- MUST record significant architectural decisions and their rationale as Architecture Decision Records (ADRs), preferably under `docs/architecture/adr/`.
- MUST update affected documentation and diagrams when interfaces, deployment, or architecture change; SHOULD avoid documentation without ongoing value.

## Changelog, versions, and tags

- MUST maintain `CHANGELOG.md` for meaningful user-facing changes, fixes, and breaking changes, following the repository's release convention.
- MUST document upgrade or migration steps for breaking changes where applicable.
- MUST follow the project's versioning scheme and use traceable release tags; SHOULD prefer annotated or signed tags where supported.
- MUST keep tags, release notes, changelog, and published version metadata consistent; MUST NOT silently overwrite existing releases.

## CI/CD and delivery

- MUST keep CI/CD configuration version-controlled, discoverable, and aligned with the documented build and release workflow.
- MUST preserve required automated checks (tests, linting, builds, security/policy checks where configured) for PRs/MRs and releases.
- MUST NOT bypass failing checks or protections merely to merge or deploy.
- SHOULD automate reproducible builds, tagged releases, and deployment promotion using the project's approved pipeline.
- MUST make build, review, release, and deployment status distinguishable so the board does not imply a delivery stage that has not occurred.

## Workflow hygiene

- MUST NOT commit secrets, credentials, or unrelated generated artifacts.
- SHOULD keep processes minimal and avoid duplicating policies already defined in security, testing, or IaC rules.
- MUST report unavailable tracker, CI, or board updates instead of inventing their completion.
