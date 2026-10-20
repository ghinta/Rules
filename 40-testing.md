---
name: Testing and Verification Rules
alwaysApply: true
description: Framework-agnostic, risk-based testing and verification across application code, APIs, infrastructure, and integrations.
---

# Testing and Verification Rules

## Strategy & Scope

- MUST choose test types and verification depth according to change risk, affected contracts, and potential failure modes.
- SHOULD use focused tests for isolated logic, integration or contract tests for system boundaries, and end-to-end tests for critical user journeys.
- MUST add or update tests when observable behavior changes, unless impractical; MUST state the reason when tests are omitted.
- MUST use the repository's established testing and quality tools unless a change is explicitly justified.

## Behavior & Regression

- SHOULD test stable public behavior, invariants, state transitions, and observable effects rather than private implementation details.
- MUST add a regression test for a corrected defect when practical; SHOULD verify that it fails before the fix and passes afterward.
- SHOULD cover relevant success, boundary, invalid or empty input, permissions, repetition, failure, concurrency, and compatibility scenarios according to risk.
- MUST NOT rely on snapshots or broad assertions that conceal unintended behavior changes.
- SHOULD keep assertions specific, test names descriptive, and failures diagnosable.

## Reliability & Isolation

- MUST keep automated tests deterministic, order-independent, and free from leaked state or resources.
- MUST control time, randomness, environment, locale, and external dependencies when they affect results.
- MUST NOT use arbitrary sleeps or unconditional retries to conceal flaky tests; SHOULD use explicit synchronization, bounded polling, or deterministic substitutes.
- MUST treat flaky tests as defects and investigate their underlying causes.
- SHOULD mock external boundaries when useful, but prefer integration tests over mocks that duplicate implementation details.
- MUST verify the fidelity of test doubles when contract drift could hide defects.

## Test Data & Coverage

- SHOULD use minimal, purpose-specific fixtures and synthetic or appropriately anonymized sensitive data.
- MUST NOT use real secrets or unnecessary personal data in tests.
- MUST prioritize critical behavior, security boundaries, complex logic, and regression-prone areas over arbitrary coverage targets.
- SHOULD treat coverage metrics as diagnostic signals, not evidence of correctness by themselves.
- MUST NOT add meaningless assertions solely to increase coverage.

## Maintenance & Verification

- MUST update tests when intended contracts change; MUST NOT weaken or delete valid tests merely to accommodate failing code.
- SHOULD remove obsolete tests when their intended behavior is deliberately removed.
- SHOULD run focused tests first, then affected integration tests, applicable static checks, and broader suites proportionate to the change.
- MUST investigate relevant test failures and review the resulting changes.
- MUST report which checks ran, their outcomes, and any checks that could not be performed; MUST NOT claim unexecuted checks passed.
