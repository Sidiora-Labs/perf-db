# Security Policy

## Supported Versions

PerfDB is pre-1.0 and under active development. Security fixes are applied
to the latest release on the `main` branch only.

| Version | Supported |
|---------|-----------|
| 0.1.x   | Yes       |
| < 0.1   | No        |

## Reporting a Vulnerability

Please do not report security vulnerabilities through public GitHub issues.

Instead, use [GitHub Security Advisories](https://github.com/Sidiora-Labs/perf-db/security/advisories/new)
to submit a private report, or email **security@sidiora.io** with:

- A description of the vulnerability and its potential impact
- Steps to reproduce, including any proof-of-concept code
- The affected version or commit hash

You should expect an initial response within 3 business days. We will keep
you informed of progress until the issue is resolved and coordinate a
disclosure timeline with you.

## Scope

Given PerfDB embeds directly into the calling process and reads/writes
files on local disk, in-scope issues include:

- Memory-safety violations reachable from the public API (including via
  malformed on-disk WAL or snapshot data)
- Data corruption or durability guarantee violations
- Panics or denial-of-service triggerable by untrusted input passed through
  the public API

Out of scope: issues requiring local filesystem access equivalent to the
process's own permissions, and vulnerabilities in third-party dependencies
(report those upstream).
