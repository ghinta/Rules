---
name: React and TypeScript Development Rules
globs:
  - "**/*.ts"
  - "**/*.tsx"
  - "**/tsconfig*.json"
  - "**/package.json"
alwaysApply: false
description: React and TypeScript development, technology evaluation, security, accessibility, and quality standards.
---

# React and TypeScript Development Rules

## Standards & Tooling

- MUST follow the project's supported versions, configured tooling, and established conventions.
- MUST follow currently applicable React, TypeScript, and web standards compatible with the project.
- MUST preserve strict type checking; MUST NOT use `any` or broad suppressions merely to bypass errors.
- MUST validate untrusted data at runtime where required; static types are not runtime validation.
- SHOULD prefer maintained solutions and existing abstractions over unnecessary dependencies.

## Architecture & Technology

- MUST follow the established architecture while remaining open to justified improvements.
- MUST evaluate the architecture and technology stack before substantial or cross-cutting changes.
- SHOULD consider maintained alternatives for rendering, routing, state management, data fetching, API integration, and build tooling when beneficial.
- MUST assess compatibility, performance, security, complexity, migration effort, and long-term maintainability before recommending architectural changes.
- MUST present justified alternatives and trade-offs rather than automatically preserving existing technology choices.
- MUST NOT introduce major technology migrations without explicit approval.

## Components, State & Effects

- MUST follow React's Rules of Hooks, keep rendering pure, and treat props and state as immutable.
- MUST handle side effects through appropriate React mechanisms and clean up external resources.
- SHOULD keep components focused, state local where practical, and avoid duplicated or unnecessary derived state.
- SHOULD distinguish UI state from server state and reuse appropriate synchronization and caching mechanisms.
- MUST prevent stale asynchronous results from corrupting state where race conditions are possible.
- SHOULD favor clear, maintainable components over premature abstractions or memoization.

## Data, Security & Accessibility

- MUST handle relevant loading, empty, success, and error states in asynchronous user interfaces.
- MUST enforce authentication and authorization on the server; client-side checks are not access control.
- MUST treat external data as untrusted, render it safely, and sanitize HTML when necessary.
- MUST NOT expose secrets or privileged credentials in browser-delivered code.
- MUST preserve established authentication, CSRF, and secure-transport protections.
- MUST provide accessible interfaces with semantic markup, keyboard support, accessible names, and appropriate focus behavior.

## Quality, Performance & Testing

- MUST handle errors explicitly and MUST NOT silently ignore failed operations.
- MUST add or update tests when observable behavior changes.
- SHOULD test user-visible behavior, important edge cases, and accessibility-relevant interactions.
- SHOULD optimize based on evidence or clear scaling requirements, not speculative micro-optimizations.
- SHOULD avoid unbounded rendering or data transfer; use suitable pagination, virtualization, or filtering when necessary.
- MUST use the project's established testing and quality-assurance tools.
