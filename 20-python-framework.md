
---
name: Python Development Rules
globs:
  - "**/*.py"
  - "**/pyproject.toml"
  - "**/uv.lock"
alwaysApply: false
description: Framework-agnostic Python development, architecture, security, and quality standards.
---

# Python Development Rules

## Standards & Tooling

- MUST follow the project's supported Python version, configured tooling, and established conventions.
- MUST follow currently applicable Python PEPs, official specifications, and maintained best practices.
- SHOULD use `uv` exclusively for Python environments, dependencies, and execution.
- MUST maintain `pyproject.toml` and `uv.lock` for uv-managed projects.
- SHOULD use type annotations, explicit interfaces, and appropriate static analysis.
- SHOULD favor standard-library solutions and established abstractions over unnecessary dependencies.

## Architecture & Technology

- MUST remain framework-agnostic and follow the established architecture and documented framework conventions.
- SHOULD favor simplicity, modularity, maintainability, and clear separation of concerns.
- MUST evaluate the existing architecture and technology stack before substantial or cross-cutting changes.
- SHOULD consider current, maintained alternatives when they offer meaningful improvements in performance, security, maintainability, or developer experience.
- MUST assess compatibility, migration effort, technical debt, and long-term implications before recommending architectural changes.
- MUST present justified alternatives and trade-offs rather than automatically preserving existing technology choices.
- MUST NOT introduce major technology migrations without explicit approval.

## Data & Security

- MUST validate untrusted input and enforce authorization at appropriate trust boundaries.
- MUST use safe database access, transactions, constraints, and schema migrations where applicable.
- MUST protect secrets, enforce secure configuration, and avoid insecure defaults.
- MUST NOT bypass established security mechanisms without a justified, secure alternative.
- SHOULD avoid inefficient queries, unnecessary resource consumption, and premature optimization.
- SHOULD use appropriate data types, including decimal-exact arithmetic and timezone-aware timestamps where required.

## Code Quality & Testing

- MUST handle errors explicitly without silently suppressing unexpected exceptions.
- MUST avoid unsafe operations, mutable default arguments, and unnecessary global state.
- MUST add or update tests when behavior changes.
- SHOULD cover edge cases, validation, authorization, and regression scenarios.
- SHOULD favor readable, focused, and testable code over unnecessary abstractions.
- MUST use the project's established testing and quality assurance tools.
