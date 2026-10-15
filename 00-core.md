---
name: Core Engineering Rules
alwaysApply: true
description: Baseline engineering behavior for all coding, review, refactoring, debugging, and maintenance tasks.
---

# Core Engineering Rules

Use the keywords MUST, MUST NOT, SHOULD, SHOULD NOT, and MAY as requirement levels.

## Work from evidence

- MUST inspect the relevant code, configuration, tests, and repository conventions before changing behavior.
- MUST prefer repository facts over assumptions about frameworks, APIs, commands, file locations, or versions.
- MUST preserve established project conventions unless the task explicitly requires changing them.
- MUST NOT invent files, APIs, configuration keys, command results, test results, or repository behavior.
- MUST state uncertainty when the available evidence is insufficient.

## Change discipline

- MUST make the smallest coherent change that satisfies the requested behavior.
- MUST keep unrelated refactoring out of the change.
- MUST NOT change public APIs, persistence formats, external contracts, or deployment behavior unless required.
- SHOULD preserve backward compatibility when practical.
- MUST identify compatibility or migration impact when a change cannot be backward compatible.
- MUST NOT add a dependency when the existing standard library, framework, or approved project dependencies solve the problem adequately.
- SHOULD remove code made obsolete by the same change when doing so is safe and local.
- MUST NOT perform speculative cleanup or redesign unrelated to the task.

## Simplicity and maintainability

- SHOULD prefer clear, explicit code over clever or compressed code.
- SHOULD prefer cohesive functions, modules, and components with a single clear responsibility.
- SHOULD reuse existing abstractions before introducing new ones.
- MUST NOT create abstractions solely for hypothetical future reuse.
- SHOULD avoid hidden control flow, hidden global state, and surprising side effects.
- MUST use names that communicate domain intent rather than implementation trivia.
- SHOULD write comments primarily to explain constraints, trade-offs, invariants, or why a non-obvious approach exists.
- MUST NOT add comments that merely restate obvious code.

## Correctness

- MUST validate external or untrusted input at an appropriate system boundary.
- MUST preserve important domain invariants.
- MUST handle expected failure modes explicitly.
- MUST NOT silently swallow exceptions or ignore failed operations.
- SHOULD make side-effecting operations idempotent when retries or repeated execution are expected.
- MUST consider concurrency, retries, partial failure, and duplicate execution when modifying code that crosses process or network boundaries.

## Configuration and secrets

- MUST keep environment-specific configuration outside source code where the project architecture supports it.
- MUST NOT commit passwords, tokens, private keys, credentials, or other secrets.
- MUST NOT copy secrets into examples, tests, logs, comments, prompts, generated files, or error messages.
- MUST preserve existing secret-management mechanisms.

## Dependency and version awareness

- MUST respect the versions declared by the repository.
- MUST NOT use framework or language features that are unavailable in those declared versions.
- MUST prefer maintained, documented APIs over deprecated or internal APIs.
- SHOULD prefer the latest LTS versions.
- MUST preserve lockfiles and dependency-management conventions used by the repository.

## Verification

After a code change, the agent SHOULD perform the narrowest relevant verification available:

1. formatter
2. static analysis or linter
3. type checker
4. focused tests
5. broader tests when warranted by the change
6. repository diff review

- MUST use the project's existing tools and commands when they are discoverable.
- MUST NOT claim that a command, test, scan, or build passed unless it was actually executed and the result was observed.
- MUST NOT delete, weaken, skip, or rewrite a valid test merely to make a failing change pass.
- MUST distinguish failures caused by the new change from pre-existing failures when evidence allows.

## Review quality

Before considering a change complete, MUST review the resulting diff for:

- unintended file changes
- dead or duplicated code
- missing tests
- backward-compatibility issues
- security regressions
- accidental secret exposure
- dependency changes
- schema or migration impact
- configuration and deployment impact

## Human control

- MUST preserve repository review, approval, CI, security, and deployment controls.
- MUST NOT bypass branch protections, security checks, policy checks, approval gates, or deployment safeguards.
- MUST surface decisions that materially affect security, privacy, architecture, data, licensing, or production behavior for human review.
