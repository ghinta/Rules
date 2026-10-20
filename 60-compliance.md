# Compliance and Governance Rules

These rules guide engineering decisions; they do not replace qualified legal, privacy, security, or regulatory review.

## Requirements & Approvals

- MUST follow applicable documented legal, contractual, regulatory, organizational, and repository requirements.
- MUST preserve required approval, review, audit, retention, and change-control processes.
- MUST surface missing, conflicting, or ambiguous requirements when they materially affect implementation; MUST NOT invent legal obligations, retention periods, or certification levels.
- MUST NOT claim compliance or formal approval without appropriate evidence and authorized review.

## Privacy & Data Governance

- MUST apply purpose limitation and data minimization to personal data, including collection, processing, storage, retention, and transfer.
- MUST follow applicable data classification, retention, deletion, and protection requirements, including storage, transmission, and backups.
- MUST preserve applicable rights-related mechanisms for access, correction, export, restriction, and deletion.
- MUST minimize personal or confidential data in logs, telemetry, URLs, caches, error messages, and test data; SHOULD use synthetic, anonymized, or appropriately pseudonymized test data.
- SHOULD prefer privacy-preserving defaults and avoid unnecessary persistent storage or optional telemetry.
- MUST obtain required approval before introducing third-party trackers, analytics, external AI services, or data processors; MUST keep restricted data within approved systems and transfer paths and explicitly approve new destinations.

## Third-Party Software & Licensing

- SHOULD evaluate new dependencies for necessity, provenance, maintenance, vulnerabilities, licensing, transitive impact, and updateability.
- MUST follow approved dependency and license-review processes.
- MUST preserve applicable copyright notices, license terms, attribution, and source-offer obligations.
- MUST NOT incorporate external code with unknown or incompatible reuse rights.
- SHOULD preserve dependency inventories and SBOMs where established or required.

## Auditability & Change Control

- SHOULD retain necessary security and operational audit events with useful context and minimal sensitive data.
- MUST preserve audit-record integrity, access controls, and documented retention requirements.
- SHOULD keep material changes traceable through relevant issues, reviews, tests, security checks, architecture decisions, and deployment records.
- MUST NOT fabricate compliance evidence or alter records, history, or metadata to conceal unsafe or unauthorized changes.

## Vulnerabilities & Regulated Obligations

- MUST preserve established vulnerability reporting, remediation, disclosure, and security-update processes.
- MUST surface introduced or materially affected security findings; MUST NOT suppress known vulnerabilities without an accepted, documented risk decision.
- SHOULD keep relevant software components maintainable and inventories or evidence current where required.
- MUST follow documented accessibility, records-management, export-control, and sector-specific obligations and verify them at an appropriate level.
- MUST escalate material regulatory or contractual interpretations for qualified review rather than guessing.
