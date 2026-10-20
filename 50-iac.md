---
name: Infrastructure as Code Rules
globs:
  - "**/*.tf"
  - "**/*.tfvars"
  - "**/*.tf.json"
  - "**/*.hcl"
  - "**/*.bicep"
  - "**/Dockerfile*"
  - "**/*compose*.yml"
  - "**/*compose*.yaml"
  - "**/.gitlab-ci.yml"
  - "**/.github/workflows/**"
  - "**/Jenkinsfile*"
  - "**/k8s/**"
  - "**/kubernetes/**"
  - "**/helm/**"
  - "**/charts/**"
  - "**/ansible/**"
  - "**/infra/**"
  - "**/infrastructure/**"
alwaysApply: false
description: Technology-agnostic infrastructure, containers, orchestration, CI/CD, supply-chain security, and deployment safety.
---

# Infrastructure as Code Rules

Infrastructure changes MUST be treated as production code and assessed for security, availability, cost, and data-loss risks.

## Standards & Architecture

- MUST follow the repository's approved toolchain, conventions, and deployment strategy.
- MUST keep infrastructure definitions version-controlled, reproducible, and declarative where supported; MUST avoid undocumented configuration drift.
- MUST separate environment-specific configuration from reusable infrastructure logic.
- SHOULD reuse maintained modules and platform patterns; keep abstractions focused, documented, and validated without unnecessary wrappers.
- MUST evaluate the existing technology stack before substantial or cross-cutting changes, considering security, operability, portability, cost, and migration risk.
- MUST present material alternatives and trade-offs; MUST NOT perform major platform migrations without explicit approval.

## Security & Supply Chain

- MUST apply least privilege to identities, workloads, runners, and infrastructure resources; broad permissions require justification.
- MUST restrict network exposure by default; public services, administrative endpoints, and unrestricted ingress/egress require explicit justification.
- MUST preserve encryption, TLS verification, and existing security controls; MUST NOT weaken them to resolve deployment issues.
- MUST NOT commit or embed secrets in code, manifests, images, build artifacts, or logs.
- MUST protect sensitive state, plans, generated configuration, and build outputs; SHOULD prefer short-lived or workload-identity credentials.
- MUST use approved dependency and image sources, preserve version constraints, lockfiles, integrity and provenance controls, and configured security checks.
- SHOULD assess new dependencies, modules, images, and CI actions for maintenance, vulnerabilities, and supply-chain risk.

## Infrastructure State & Changes

- MUST protect infrastructure state with appropriate access controls, encryption, and concurrency protection where supported.
- SHOULD separate state according to ownership, lifecycle, access, and blast radius; MUST minimize sensitive values stored in state.
- MUST follow the project's versioning, formatting, validation, and input/output conventions.
- SHOULD validate important module inputs and explicitly classify sensitive outputs.
- MUST review proposed changes for resource deletion/replacement, privilege expansion, public exposure, and state or data migration before applying.
- MUST NOT use targeted applies, imperative provisioners, or drift-suppression settings as routine shortcuts; exceptions require documented justification.

## Containers & Orchestration

- SHOULD use maintained, minimal, version-controlled base images and multi-stage builds where beneficial.
- MUST exclude secrets and unnecessary files from build contexts; MUST NOT bake credentials into image layers.
- SHOULD run workloads as non-root, minimize capabilities, and remove unnecessary runtime components.
- MUST NOT enable privileged containers, host access, or excessive permissions without an explicit, reviewed requirement.
- MUST follow platform policies for resource requests/limits, identity, secrets, and workload isolation.
- SHOULD configure health checks, network segmentation, and read-only filesystems where supported and appropriate.
- MUST use scoped RBAC and appropriate secret-management mechanisms; MUST NOT store secrets in ordinary configuration resources.

## CI/CD & Deployment

- MUST isolate untrusted contributions from privileged runners, deployment credentials, and protected environments.
- MUST scope deployment permissions to the required actions and environments; SHOULD use approval gates for high-risk production changes.
- SHOULD pin or integrity-control build and deployment inputs; MUST preserve configured artifact and infrastructure security checks.
- MUST NOT bypass policy-as-code, provenance, vulnerability, or deployment safeguards merely to make a pipeline pass.

## Verification & Change Safety

- MUST run relevant available formatting, validation, tests, and security/policy checks for affected infrastructure; MUST report checks that could not run.
- SHOULD inspect rendered configurations and deployment plans, and validate high-risk changes in a non-production environment when practical.
- MUST surface destructive changes, new public exposure, privilege increases, and state/data movement for explicit review.
- SHOULD document rollback or recovery considerations when changes can affect availability or persisted data.
