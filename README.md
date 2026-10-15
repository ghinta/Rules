# Sources and Rationale

This file is intentionally outside `.continue/rules/` so that source references do not consume the coding agent's rule context.

The rule set is a practical engineering baseline synthesized from public, authoritative, and widely adopted standards and guidance. It is not a certification profile and does not by itself establish compliance with any standard or regulation.

## Continue rule design

- Continue Docs — Rules:
  https://docs.continue.dev/customize/deep-dives/rules
- Continue Docs — Rules overview:
  https://docs.continue.dev/customize/rules
- OpenSSF — Security-Focused Guide for AI Code Assistant Instructions:
  https://best.openssf.org/Security-Focused-Guide-for-AI-Code-Assistant-Instructions.html

Design implication: rules are kept concise, specific, actionable, and scoped by `alwaysApply`, `globs`, and `description`.

## Core secure software development

- NIST SP 800-218 — Secure Software Development Framework (SSDF) v1.1:
  https://csrc.nist.gov/pubs/sp/800/218/final
- OpenSSF — Secure Software Development Guiding Principles:
  https://best.openssf.org/SecureSoftwareGuidingPrinciples.html
- OpenSSF — Concise Guide for Developing More Secure Software:
  https://best.openssf.org/Concise-Guide-for-Developing-More-Secure-Software.html
- OWASP Top 10:2025:
  https://top10.owasp.org/2025/
- OWASP ASVS 5.0:
  https://owasp.org/www-project-application-security-verification-standard/

## Architecture

- ISO/IEC/IEEE 42010:2022 — Architecture description:
  https://www.iso.org/standard/74393.html
- Google Engineering Practices — Code Review:
  https://google.github.io/eng-practices/review/
- Google Engineering Practices — What to look for in a code review:
  https://google.github.io/eng-practices/review/reviewer/looking-for.html

The architecture rule does not claim ISO 42010 conformance. It adopts compatible principles such as explicit architectural concerns, boundaries, contracts, and documented architectural decisions.

## Python / Django

- PEP 8 — Style Guide for Python Code:
  https://peps.python.org/pep-0008/
- Python Typing Specification:
  https://typing.python.org/en/latest/spec/
- Python Typing Best Practices:
  https://typing.python.org/en/latest/reference/best_practices.html
- Django — Security documentation:
  https://docs.djangoproject.com/en/stable/topics/security/
- Django — Deployment checklist:
  https://docs.djangoproject.com/en/stable/howto/deployment/checklist/
- Django — Testing:
  https://docs.djangoproject.com/en/stable/topics/testing/

## React / TypeScript

- React — Rules of React:
  https://react.dev/reference/rules
- React — Components and Hooks must be pure:
  https://react.dev/reference/rules/components-and-hooks-must-be-pure
- React — Rules of Hooks:
  https://react.dev/reference/rules/rules-of-hooks
- TypeScript — `strict` compiler option:
  https://www.typescriptlang.org/tsconfig/strict

## Testing

- Django testing documentation:
  https://docs.djangoproject.com/en/stable/topics/testing/
- Martin Fowler — Test Pyramid:
  https://martinfowler.com/bliki/TestPyramid.html
- Martin Fowler / Ham Vocke — The Practical Test Pyramid:
  https://martinfowler.com/articles/practical-test-pyramid.html
- Google Engineering Practices — Code Review:
  https://google.github.io/eng-practices/review/

The testing rule treats the test pyramid as a heuristic, not a fixed numeric ratio.

## Infrastructure as Code

- HashiCorp Terraform — Style Guide:
  https://developer.hashicorp.com/terraform/language/style
- HashiCorp Terraform — Module development:
  https://developer.hashicorp.com/terraform/language/modules/develop
- OpenTofu — Style Conventions:
  https://opentofu.org/docs/language/syntax/style/
- OWASP — Infrastructure as Code Security Cheat Sheet:
  https://cheatsheetseries.owasp.org/cheatsheets/Infrastructure_as_Code_Security_Cheat_Sheet.html

## Compliance, privacy, licensing, and governance

- GDPR / Regulation (EU) 2016/679 — especially Article 5 and Article 25:
  https://eur-lex.europa.eu/eli/reg/2016/679/oj
- EU Cyber Resilience Act / Regulation (EU) 2024/2847:
  https://eur-lex.europa.eu/eli/reg/2024/2847/oj
- ISO/IEC 27001:2022 overview:
  https://www.iso.org/standard/27001
- OpenChain / ISO/IEC 5230 — Open Source License Compliance:
  https://openchainproject.org/license-compliance
- OpenSSF — Concise Guide for Evaluating Open Source Software:
  https://best.openssf.org/Concise-Guide-for-Evaluating-Open-Source-Software.html
- OWASP ASVS 5.0 — Data Protection / Logging and Error Handling:
  https://owasp.org/www-project-application-security-verification-standard/

## Usage note

These rules are intended to be:
- an AI coding assistant baseline,
- version-controlled with the repository,
- supplemented by project-specific ADRs and policies,
- enforced by formatters, linters, type checkers, tests, SAST/SCA/secret scanning, IaC policy checks, and CI/CD controls.

They are not a substitute for:
- organization-specific secure development policies,
- legal advice,
- formal ISO certification controls,
- a GDPR compliance assessment,
- a Cyber Resilience Act conformity assessment,
- or human code/security review.
