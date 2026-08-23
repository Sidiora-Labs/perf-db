# Contributing to PerfDB

Thanks for your interest in improving PerfDB. This document covers the
practical steps for setting up a development environment and getting a
change merged.

## Prerequisites

- Rust 1.75 or newer (stable channel)
- `rustfmt` and `clippy` components: `rustup component add rustfmt clippy`
- Linux or macOS; Windows is not currently supported

## Getting started

```bash
git clone https://github.com/Sidiora-Labs/perf-db.git
cd perf-db
cargo build
cargo test
```

A ready-to-use dev container is available in `.devcontainer/` if you use
VS Code or GitHub Codespaces.

## Development workflow

1. Open an issue describing the bug or feature before starting non-trivial work.
2. Create a branch from `main`.
3. Make your change with tests. Keep commits focused and use descriptive messages.
4. Run the full local check before opening a PR:

   ```bash
   cargo fmt --all -- --check
   cargo clippy --all-targets --all-features -- -D warnings
   cargo test --all-features
   ```

5. Open a pull request against `main` using the provided template.

## Code standards

- Public items require doc comments (`///`) describing behavior, not
  restating the signature.
- Avoid comments that describe *what* a line does when the code already
  makes that obvious; comment on *why* when the reasoning isn't apparent
  from the code itself.
- Unsafe code must include a `// SAFETY:` comment justifying the invariant
  being relied on.
- New public APIs require tests; changes to hot paths require a benchmark
  in `benches/` or a note in the PR explaining why one isn't needed.
- Run `cargo fmt` before committing; CI enforces formatting and lint cleanliness.

## Testing

- Unit tests live alongside the modules they cover (`#[cfg(test)] mod tests`).
- Cross-module behavior belongs in `tests/integration.rs`.
- Crash-recovery and WAL-replay scenarios belong in `tests/recovery.rs`.
- Run a single test with `cargo test <name> -- --nocapture` while iterating.

## Commit and PR etiquette

- Rebase instead of merging `main` into your branch when possible.
- Squash trivial fixups before requesting review.
- Reference the issue a PR resolves (`Closes #123`).
- Breaking changes to the public API must update `CHANGELOG.md` and, if
  relevant, the migration notes in `README.md`.

## Reporting security issues

Do not open a public issue for a security vulnerability. See
[`SECURITY.md`](SECURITY.md) for the private reporting process.

## License

By contributing, you agree that your contributions will be licensed under
the same dual MIT/Apache-2.0 terms as the rest of the project (see
[`LICENSE-MIT`](LICENSE-MIT) and [`LICENSE-APACHE`](LICENSE-APACHE)).
