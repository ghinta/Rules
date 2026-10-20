# Python Development Rules

## Standards & Tooling

- MUST follow the project's supported Python version, configured tooling, and established conventions.
- MUST follow currently applicable Python PEPs, official specifications, and maintained best practices.
- MUST use `uv` for Python environments, dependencies, and execution in uv-managed projects.
- MUST maintain `pyproject.toml` and `uv.lock` for uv-managed projects.
- SHOULD use type annotations, explicit interfaces, and appropriate static analysis.
- SHOULD favor standard-library solutions and established abstractions over unnecessary dependencies.

## Architecture & Technology

- MUST remain framework-agnostic and follow the established architecture and documented framework conventions.
- SHOULD favor simplicity, modularity, maintainability, and clear separation of concerns.

## Data & Security

- MUST use safe database access, transactions, constraints, and schema migrations where applicable.
- SHOULD avoid inefficient queries, unnecessary resource consumption, and premature optimization.
- SHOULD use appropriate data types, including decimal-exact arithmetic and timezone-aware timestamps where required.

## Code Quality & Testing

- MUST handle errors explicitly without silently suppressing unexpected exceptions.
- MUST avoid unsafe operations, mutable default arguments, and unnecessary global state.
- SHOULD favor readable, focused, and testable code over unnecessary abstractions.
