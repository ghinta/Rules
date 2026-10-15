---
name: Architecture and Design Rules
alwaysApply: false
description: Apply when introducing or changing modules, services, APIs, persistence boundaries, cross-cutting concerns, dependencies, or architectural structure.
---

# Architecture and Design Rules

## Preserve architectural intent

- MUST inspect existing architecture documentation, ADRs, module boundaries, and dependency direction before introducing a new architectural pattern.
- MUST preserve established architectural boundaries unless the task explicitly requires changing them.
- SHOULD align new code with the dominant local pattern rather than introducing a second competing pattern.
- MUST document or clearly report a material architectural deviation.
- SHOULD introduce the c4 model to show or display the current architecture

## Modularity

- SHOULD design modules around cohesive responsibilities and explicit boundaries.
- SHOULD minimize coupling between modules and maximize cohesion within a module.
- MUST avoid circular dependencies.
- SHOULD depend on stable contracts rather than implementation details across architectural boundaries.
- SHOULD keep domain and business rules independent from transport, UI, persistence, and infrastructure concerns where the existing architecture supports that separation.
- SHOULD isolate integration-specific behavior at system boundaries.

## Dependency direction

- MUST preserve the repository's intended dependency direction.
- SHOULD keep lower-level domain or core code from depending on delivery mechanisms such as HTTP, CLI, UI, or database adapters unless the project deliberately uses that architecture.
- MUST NOT introduce a service locator, hidden global dependency, or mutable singleton to avoid explicit dependency wiring.
- SHOULD inject boundary dependencies when substitution, testing, or lifecycle control is required.

## Interfaces and contracts

- MUST make cross-module and external contracts explicit.
- MUST preserve API, event, schema, and persistence compatibility unless a breaking change is explicitly required.
- SHOULD prefer narrow interfaces over broad "manager", "utility", or "god object" abstractions.
- MUST define failure behavior for external interfaces, not only successful behavior.
- SHOULD validate assumptions at boundaries rather than deep inside unrelated implementation code.

## Data and state

- MUST identify ownership of mutable data when introducing new persistence or shared state.
- MUST preserve transactional invariants for operations that must succeed or fail together.
- MUST avoid duplicated sources of truth unless synchronization rules are explicit.
- SHOULD derive values instead of storing redundant state when derivation is reliable and inexpensive.
- MUST consider migration, rollback, and compatibility for persistent schema changes.

## Distributed and external systems

When calling another process, service, queue, database, or external API:

- MUST define timeouts.
- MUST handle expected transient and permanent failures.
- SHOULD use bounded retries only for operations that are safe to retry.
- MUST consider duplicate execution before retrying writes.
- SHOULD use idempotency mechanisms for externally repeated write operations when appropriate.
- MUST NOT assume exactly-once execution across network boundaries.
- SHOULD degrade or fail predictably rather than hang indefinitely.

## Configuration

- SHOULD externalize environment-specific configuration.
- MUST NOT use configuration flags to bypass fundamental authorization or security controls.
- SHOULD keep configuration typed, validated, and documented where supported.
- MUST provide safe defaults when a default is appropriate.

## Observability

- SHOULD expose enough structured diagnostics to operate and debug the system.
- SHOULD make failures observable at the boundary where they can be acted upon.
- MUST NOT use logging as a substitute for error handling.
- MUST follow security and privacy rules for logs, traces, and metrics.

## Architecture changes

A material architecture change SHOULD include the project's normal architecture-decision mechanism when one exists, especially for:

- new infrastructure or platform technology
- new persistence technology
- new inter-service communication pattern
- new cross-cutting security mechanism
- new shared framework or foundational dependency
- a deliberate exception to an established architecture rule

## Anti-patterns

MUST NOT introduce without a demonstrated need:

- god classes or god modules
- circular dependencies
- mutable global state
- generic abstractions with no concrete reuse
- deep inheritance hierarchies for ordinary business logic
- duplicated business rules across layers
- hidden network or database calls in apparently pure helpers
- framework-specific types leaking through unrelated domain boundaries
- broad "utils" modules used as dumping grounds
- new distributed services solely to avoid modularizing an existing application

## Design preference

When multiple designs satisfy the requirements, SHOULD prefer the design that:

1. changes fewer concepts
2. has clearer ownership
3. has fewer runtime dependencies
4. is easier to test
5. fails more predictably
6. is easier for another engineer to understand
7. matches the existing architecture
