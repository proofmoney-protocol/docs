# ProofMoney Core MVP Report v0.5.0-developer-release

**Version:** v0.5.0-developer-release  
**Project:** ProofMoney  
**Repository:** https://github.com/proofmoney-protocol/core  
**Website:** https://proofmoney.org  
**Initial Author:** Vingen Motoki  
**Status:** Developer readiness MVP release  
**Core Statement:** If money cannot be verified, it is only a promise.

---

## 1. Purpose

This report records the fifth ProofMoney Core MVP milestone.

The purpose of v0.5.0-developer-release is not to add more protocol functionality.

The purpose is to prepare the project for external developer review by improving onboarding, examples, repeatable demos, fixtures, architecture documentation, contributor guidance, and security review scope.

---

## 2. Current Status

ProofMoney Core v0.5.0-developer-release is a local Rust prototype prepared for developer review.

It includes:

- developer quickstart guide;
- local demo script;
- sample proof data fixtures;
- architecture overview;
- CLI examples;
- security review scope;
- contributor guide;
- CI execution of local demo script.

At this stage:

- no public network is live;
- no public hosted API is live;
- no PRM is being sold;
- no test unit has monetary value;
- no exchange listing is promised;
- no yield is promised;
- no airdrop or claim page exists;
- no test-to-main conversion is promised.

---

## 3. Repository

Core repository:

```text
https://github.com/proofmoney-protocol/core
```

Primary documentation repository:

```text
https://github.com/proofmoney-protocol/docs
```

Website:

```text
https://proofmoney.org
```

---

## 4. Implemented in v0.5.0-developer-release

This milestone implements:

| Area | Status |
|---|---|
| Developer quickstart guide | Implemented |
| Local demo script | Implemented |
| Sample proof data fixtures | Implemented |
| Architecture overview document | Implemented |
| CLI examples improvement | Implemented |
| Security review scope document | Implemented |
| Contributor guide v1.0 | Implemented |
| CI execution of local demo script | Implemented |

---

## 5. Developer Quickstart

The developer quickstart is located at:

```text
docs/developer-quickstart.md
```

It covers:

- cloning the repository;
- installing Rust;
- building the workspace;
- running tests;
- running CLI smoke tests;
- wallet and ownership commands;
- proof export commands;
- local demo script;
- local data paths;
- troubleshooting notes;
- safety boundaries.

---

## 6. Local Demo Script

The local demo script is located at:

```text
scripts/demo-local.sh
```

It runs a repeatable local MVP flow:

```bash
cargo build --workspace --all-targets
cargo test --workspace --all-targets
cargo run -p proofmoney-cli -- starting-state
cargo run -p proofmoney-cli -- simulate-release --interval 1 --append
cargo run -p proofmoney-cli -- ledger-status
cargo run -p proofmoney-cli -- verify-supply
cargo run -p proofmoney-cli -- create-wallet --force
cargo run -p proofmoney-cli -- new-address
cargo run -p proofmoney-cli -- export-proof-snapshot --json
cargo run -p proofmoney-cli -- prepare-explorer
```

The script is local only.

It does not create PRM with monetary value.

---

## 7. Sample Proof Fixtures

Sample proof fixtures are located under:

```text
fixtures/
```

Included files:

```text
fixtures/starting-state.sample.json
fixtures/ledger-status.sample.json
fixtures/supply.sample.json
fixtures/rule.sample.json
fixtures/integrity-status.sample.json
fixtures/release-events.sample.json
fixtures/transfer-events.sample.json
fixtures/proof-snapshot.sample.json
```

Fixtures are:

- sample data only;
- not public network state;
- not PRM with monetary value;
- not claim data;
- not wallet data;
- not private keys;
- not secrets.

---

## 8. Architecture Overview

The architecture overview is located at:

```text
docs/architecture-overview.md
```

It documents:

- workspace structure;
- crate responsibilities;
- CLI layer;
- local ledger layer;
- event model;
- proof engine layer;
- wallet layer;
- proof export layer;
- local explorer layer;
- MVP limitations.

---

## 9. Security Review Scope

The security review scope is located at:

```text
docs/security-review-scope.md
```

It prepares the project for external Rust/security review.

Initial review areas include:

- amount model;
- release curve;
- event hashing;
- ledger state transition;
- proof verification;
- wallet handling;
- signature verification;
- local storage;
- proof export.

This document does not claim that ProofMoney has been audited.

---

## 10. Contributor Guide

The contributor guide is located at:

```text
CONTRIBUTING.md
```

It defines:

- project purpose;
- local setup;
- code style;
- pull request expectations;
- issue workflow;
- forbidden changes;
- security review handling;
- safety boundaries.

Forbidden changes include:

- PRM sale functionality;
- claim pages;
- yield language;
- price charts;
- exchange integration;
- trading functionality;
- hidden allocation logic;
- privileged founder allocation;
- production custody claims.

---

## 11. CI Verification

The GitHub Actions Rust CI verifies:

```bash
cargo fmt --all -- --check
cargo build --workspace --all-targets
cargo test --workspace --all-targets
cargo run -p proofmoney-cli -- starting-state
cargo run -p proofmoney-cli -- starting-state --json
cargo run -p proofmoney-cli -- simulate-release --interval 1
cargo run -p proofmoney-cli -- simulate-release --interval 1 --append
cargo run -p proofmoney-cli -- ledger-status
cargo run -p proofmoney-cli -- verify-supply
cargo run -p proofmoney-cli -- verify-rule
cargo run -p proofmoney-cli -- integrity-status
cargo run -p proofmoney-cli -- create-wallet --force
cargo run -p proofmoney-cli -- new-address
cargo run -p proofmoney-cli -- list-release-events
cargo run -p proofmoney-cli -- list-release-events --json
cargo run -p proofmoney-cli -- list-transfer-events
cargo run -p proofmoney-cli -- list-transfer-events --json
cargo run -p proofmoney-cli -- export-proof-snapshot --json
cargo run -p proofmoney-cli -- export-proof-snapshot --output /tmp/proof-snapshot.json
cargo run -p proofmoney-cli -- export-proof-site-data
cargo run -p proofmoney-cli -- prepare-explorer
bash scripts/demo-local.sh
```

The CI has passed for the v0.5.0-developer-release milestone.

---

## 12. Completed Milestone Scope

The v0.5.0-developer-release milestone covers:

1. developer quickstart guide;
2. local demo script;
3. sample proof data fixtures;
4. architecture overview document;
5. CLI examples improvement;
6. security review scope document;
7. contributor guide v1.0;
8. v0.5.0 developer release report and release notes.

---

## 13. MVP Limitations

The current MVP remains intentionally limited.

It does not include:

- public network;
- public node consensus;
- hosted public API;
- production explorer;
- production wallet security;
- encrypted wallet storage;
- full consensus;
- mempool;
- peer-to-peer networking;
- full transaction fee market;
- independent security audit;
- exchange integration;
- token sale;
- airdrop claim;
- yield product.

The wallet module is experimental and must not be used with valuable assets.

---

## 14. Next Engineering Priorities

Recommended next milestone:

```text
v0.6.0-external-review
```

Suggested priorities:

1. request external Rust code review;
2. open architecture review issues;
3. review amount model safety;
4. review event hashing determinism;
5. review ledger state transition correctness;
6. review signature and ownership proof logic;
7. review wallet storage risk;
8. review proof export correctness;
9. produce review response log;
10. freeze MVP scope before public developer announcement.

---

## 15. Safety Statement

ProofMoney does not offer, sell, or solicit the purchase of PRM.

PRM does not guarantee price, liquidity, yield, profit, or exchange access.

ProofMoney is experimental and may fail.

Test units, if any, have no monetary value.

---

## 16. Final Statement

ProofMoney Core v0.5.0-developer-release is not a finished monetary network.

It is a developer-ready local MVP prototype.

It makes ProofMoney easier to run, inspect, review, and contribute to.

If money cannot be verified, it is only a promise.
