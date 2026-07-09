# Changelog

All notable changes to this project are documented in this file.

The format follows [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/) once
it reaches 1.0.

## [Unreleased]

### Added

- Time-series engine: mmap-backed tick and candle storage with binary-search
  range queries across 15 timeframes.
- State engine: lock-free market state, position table, order table with
  per-market orderbooks, balance cache, and an in-process pub/sub bus.
- Relational engine: user store, referral tiers, checkpoint tracking.
- Event log engine: dual-partitioned event storage by market and by trader.
- Aggregation layer: trader/daily statistics and leaderboard computation.
- Write-ahead log with CRC-checked segments and configurable fsync policy.
- Snapshot serialization and crash recovery via snapshot + WAL replay.
- Criterion benchmark suite for tick ingestion, candle queries, position
  lookups, and price reads.
- Integration and recovery test suites.

### Status

PerfDB is pre-release. The on-disk format and public API are not yet
stable and may change without notice before 1.0.
