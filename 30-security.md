---
name: Secure Development Rules
alwaysApply: true
description: Framework-agnostic security baseline aligned with NIST SSDF, OWASP, and OpenSSF practices.
---

# Secure Development Rules

Security MUST be enforced by default at the appropriate trust boundary. Existing protections MUST NOT be weakened for convenience; exceptions require documented justification and approval.

## Trust boundaries and input

- MUST treat externally controlled data (requests, files, URLs, storage, databases, environment, services, and AI/tool outputs) as untrusted unless a trust boundary explicitly guarantees otherwise.
- MUST validate type, structure, allowed values, and relevant size or resource limits at trust boundaries; SHOULD prefer allow-lists for constrained domains.
- MUST use context-appropriate output encoding rather than relying on generic sanitization.
- MUST enforce file-upload size/type limits, constrain user-controlled paths and filenames, and avoid unsafe deserialization.

## Authentication and authorization

- MUST enforce authentication and resource-level authorization at a trusted enforcement point (e.g., server, service, or native backend); UI checks alone are insufficient.
- MUST deny access by default and verify ownership, tenant, role, and privilege claims for each protected operation; MUST NOT trust client-provided claims.
- MUST apply least privilege to users, services, processes, credentials, and application capabilities.
- MUST preserve required re-authentication or step-up controls for sensitive operations.
- SHOULD centralize reusable authorization policies when appropriate.

## Injection and external interactions

- MUST use parameterized database APIs and prevent injection into SQL, shells, templates, interpreters, or executable expressions.
- SHOULD prefer structured process APIs over shell commands; MUST NOT execute untrusted input as code.
- MUST protect outbound requests against SSRF when untrusted input can influence destinations.

## Secrets and sensitive data

- MUST NOT hardcode, commit, or expose secrets in client code, logs, metrics, traces, snapshots, screenshots, errors, prompts, examples, or documentation.
- MUST minimize credential privileges and scope; SHOULD use short-lived or managed credentials where supported.
- MUST treat exposed credentials as compromised and surface the need for rotation.
- MUST minimize sensitive-data collection, processing, transmission, storage, and retention; SHOULD follow the project's data classification policy.
- MUST authorize access before disclosing sensitive data and protect it at rest and in transit using approved controls.

## Cryptography and transport

- MUST use established, maintained cryptographic libraries, appropriate password hashing, and secure randomness.
- MUST NOT invent cryptographic schemes, store plaintext passwords, or use reversible encoding or generic hashing as password protection.
- SHOULD use authenticated encryption when confidentiality and integrity are both required.
- MUST preserve TLS certificate and hostname validation; MUST NOT disable verification.

## Web, session, and privileged interfaces

Where applicable:

- MUST preserve CSRF defenses for authenticated browser requests relying on automatically attached credentials, and use secure cookie/session settings.
- MUST prevent open redirects, inappropriate caching of sensitive responses, and exposure of secrets or sensitive data in URLs.
- MUST preserve relevant browser protections, including CSP, framing/clickjacking, and content-type controls.
- MUST enforce permissions and authorization for privileged native, IPC, and API entry points.

## Logging and error handling

- SHOULD record security-relevant events; MUST keep logs structured and actionable where the platform supports it.
- MUST NOT expose stack traces, sensitive internals, or protected data to untrusted clients; MUST retain appropriate diagnostic context securely.
- MUST NOT let logging or telemetry failures bypass security controls.

## Dependencies and supply chain

- MUST use approved dependency sources and preserve ecosystem lockfiles, integrity checks, signatures, and provenance controls where established.
- SHOULD minimize dependencies and assess maintenance, provenance, licensing, and known vulnerabilities before adoption.
- SHOULD constrain versions according to repository policy and preserve existing SBOM/provenance generation.
- MUST NOT bypass security or supply-chain checks just to pass builds; exceptions require narrow, documented justification.

## Verification and AI-assisted development

- MUST add or update tests for security-sensitive changes, including authorization, validation, and failure paths.
- SHOULD run applicable SAST, secret, dependency, container, and IaC checks available in the project.
- MUST investigate high-confidence findings introduced by a change; MUST NOT suppress findings without a specific documented justification.
- MUST review and verify AI-generated or externally sourced code; adherence to these rules alone does not establish security.
- MUST NOT share proprietary code, secrets, personal data, or protected internal context with unapproved external tools or services.
- MUST preserve human review for material security decisions.
