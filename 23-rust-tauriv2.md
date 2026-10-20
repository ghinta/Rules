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

## Tauri, IPC & Platform Integration

- MUST validate command inputs and explicitly authorize sensitive operations in Rust.
- MUST NOT assume custom `invoke_handler` commands are restricted by plugin capabilities automatically.
- MUST apply least-privilege Tauri v2 capabilities, permissions, and scopes per window, webview, and platform.
- SHOULD expose narrow, typed IPC interfaces instead of broad access to native functionality.
- SHOULD handle OS-specific behavior explicitly and preserve supported-platform compatibility.

## Security & Reliability

- MUST NOT introduce `unsafe` without documented invariants and clear justification.
- MUST handle expected failures explicitly; avoid `unwrap()` or `expect()` on fallible runtime paths.
- MUST preserve update verification, signing, and platform security controls where applicable.

## Concurrency & Performance

- MUST avoid blocking the UI thread or async executor with expensive or blocking work.
- SHOULD use appropriate concurrency primitives and avoid holding locks across `.await`.
- MUST clean up listeners, background tasks, and native resources when their lifecycle ends.
- SHOULD measure performance before introducing caches, complex concurrency, or premature optimizations.

## Code Quality & Testing

- SHOULD cover IPC validation, permissions, errors, persistence, and platform-specific behavior where relevant.
- MUST use the project's configured formatting, linting, and test workflows (typically `cargo fmt`, `cargo clippy`, and `cargo test`).
- SHOULD favor focused tests at stable interfaces over tests coupled to implementation details.
