---
name: Rust and Tauri v2 Development Rules
globs:
  - "**/*.rs"
  - "**/Cargo.toml"
  - "**/Cargo.lock"
  - "**/rust-toolchain.toml"
  - "**/tauri.conf.*"
  - "**/src-tauri/capabilities/**"
  - "**/src-tauri/permissions/**"
  - "**/.cargo/config.toml"
alwaysApply: false
description: Rust and Tauri v2 standards for architecture, IPC, security, cross-platform behavior, and quality.
---

# Rust and Tauri v2 Development Rules

## Standards & Tooling

- MUST follow the repository's Rust toolchain, edition, supported platforms, and configured quality tools.
- MUST follow currently applicable stable Rust guidelines and maintained Tauri v2 documentation.
- MUST use Cargo for Rust dependencies and respect the repository's lockfile policy.
- SHOULD favor idiomatic ownership, explicit types, `Result`, and standard-library abstractions.
- SHOULD evaluate maintenance, compatibility, permissions, and platform support before adding crates or plugins.

## Architecture & Technology

- MUST keep domain logic separate from Tauri commands and UI-specific infrastructure where practical.
- SHOULD prefer simple, modular designs and minimize unnecessary shared mutable state.
- MUST reassess the architecture and technology stack before substantial or cross-cutting changes.
- SHOULD consider maintained alternatives when they meaningfully improve security, portability, performance, or maintainability.
- MUST explain trade-offs, migration costs, compatibility, and long-term implications before proposing major changes.
- MUST NOT perform major technology migrations without explicit approval.

## Tauri, IPC & Platform Integration

- MUST treat frontend IPC, external data, URLs, and filesystem paths as untrusted input.
- MUST validate command inputs and explicitly authorize sensitive operations in Rust.
- MUST NOT assume custom `invoke_handler` commands are restricted by plugin capabilities automatically.
- MUST apply least-privilege Tauri v2 capabilities, permissions, and scopes per window, webview, and platform.
- SHOULD expose narrow, typed IPC interfaces instead of broad access to native functionality.
- SHOULD handle OS-specific behavior explicitly and preserve supported-platform compatibility.

## Security & Reliability

- MUST preserve restrictive content security policies, trusted origins, and secure transport.
- MUST NOT embed secrets in frontend assets or distributable application binaries.
- MUST prevent command injection, path traversal, and unauthorized filesystem or process access.
- MUST NOT introduce `unsafe` without documented invariants and clear justification.
- MUST handle expected failures explicitly; avoid `unwrap()` or `expect()` on fallible runtime paths.
- MUST NOT leak sensitive internals through IPC errors, logs, or user-visible messages.
- MUST preserve update verification, signing, and platform security controls where applicable.

## Concurrency & Performance

- MUST avoid blocking the UI thread or async executor with expensive or blocking work.
- SHOULD use appropriate concurrency primitives and avoid holding locks across `.await`.
- MUST clean up listeners, background tasks, and native resources when their lifecycle ends.
- SHOULD measure performance before introducing caches, complex concurrency, or premature optimizations.

## Code Quality & Testing

- MUST add or update tests when observable behavior changes.
- SHOULD cover IPC validation, permissions, errors, persistence, and platform-specific behavior where relevant.
- MUST use the project's configured formatting, linting, and test workflows (typically `cargo fmt`, `cargo clippy`, and `cargo test`).
- SHOULD favor focused tests at stable interfaces over tests coupled to implementation details.
