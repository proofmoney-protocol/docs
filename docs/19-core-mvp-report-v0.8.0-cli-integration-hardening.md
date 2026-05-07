# ProofMoney Core MVP Report v0.8.0-cli-integration-hardening

**Version:** v0.8.0-cli-integration-hardening  
**Project:** ProofMoney  
**Repository:** https://github.com/proofmoney-protocol/core  
**Website:** https://proofmoney.org  
**Initial Author:** Vingen Motoki  
**Status:** CLI integration hardening release  
**Core Statement:** If money cannot be verified, it is only a promise.

---

## 1. Purpose

This report records the eighth ProofMoney Core MVP milestone.

The purpose of v0.8.0-cli-integration-hardening is to make the local MVP CLI layer more repeatable, testable, resettable, inspectable, and demonstrable.

This milestone focuses on:

- isolated CLI integration tests;
- local ledger reset command;
- local state validation command;
- local ledger tamper detection command;
- proof export freshness metadata;
- end-to-end local transfer demo;
- clearer invalid-state error messages;
- CI expansion.

This milestone does not claim external audit completion.

This milestone does not claim production readiness.

---

## 2. Current Status

ProofMoney Core v0.8.0-cli-integration-hardening is a local Rust MVP prototype with strengthened CLI integration hardening.

At this stage:

- no public network is live;
- no public hosted API is live;
- no PRM is being sold;
- no test unit has monetary value;
- no exchange listing is promised;
- no yield is promised;
- no airdrop or claim page exists;
- no test-to-main conversion is promised;
- no external audit has been completed.

---

## 3. Implemented in v0.8.0

| Area | Status |
|---|---|
| Isolated CLI integration test framework | Implemented |
| Local ledger reset command | Implemented |
| Local state validation command | Implemented |
| Local ledger tamper detection command | Implemented |
| Proof export freshness indicator | Implemented |
| End-to-end local transfer demo | Implemented |
| Invalid-state error message improvement | Implemented |
| CLI integration hardening report and release notes | Implemented |

---

## 4. Isolated CLI Integration Tests

The CLI integration tests are located at:

```text
crates/proofmoney-cli/tests/cli_integration.rs
```

The integration tests use isolated temporary home directories to avoid writing test state into the real user home directory.

Covered flow includes:

```text
reset ledger
starting state
append release
ledger status
validate local state
detect tampering
export proof data
prepare explorer
```

The tests improve local MVP confidence, but they do not imply production readiness.

---

## 5. Local Ledger Reset Command

New command:

```bash
proofmoney reset-ledger --yes
proofmoney reset-ledger --json --yes
```

Purpose:

- reset local MVP ledger state;
- require explicit `--yes`;
- print local ledger path;
- print safety warning;
- support JSON output;
- avoid resetting wallet state.

Safety boundary:

```text
Resetting local ledger does not affect any public network because no public network exists.
```

---

## 6. Local State Validation Command

New command:

```bash
proofmoney validate-local-state
proofmoney validate-local-state --json
```

Validation checks include:

- event hash validity;
- rule version consistency;
- event height order;
- computed supply;
- Public Proof Fund recomputation;
- balance recomputation;
- last event hash consistency.

This validates local MVP state only.

It does not validate public consensus.

---

## 7. Local Ledger Tamper Detection Command

New command:

```bash
proofmoney detect-tampering
proofmoney detect-tampering --json
```

Detection areas include:

- invalid event hash;
- mutated event payload;
- mismatched current supply;
- mismatched Public Proof Fund balance;
- mismatched last event hash;
- invalid rule version;
- invalid event height order.

This is local MVP integrity checking only.

It does not imply production forensic security.

---

## 8. Proof Export Freshness Metadata

v0.8.0 adds freshness metadata to proof exports.

Proof exports now include:

- export timestamp;
- ledger height at export;
- last event hash at export;
- event count at export;
- local ledger path;
- freshness warning.

Freshness warning:

```text
This proof export is a local snapshot. It can become stale after local ledger changes. Regenerate exports after state changes.
```

Freshness metadata does not make exports public consensus or signed audit artifacts.

---

## 9. End-to-End Local Transfer Demo

New demo script:

```bash
bash scripts/demo-transfer-local.sh
```

The script runs a repeatable local MVP transfer flow:

1. reset local ledger;
2. create local MVP wallet;
3. read sender address;
4. append release event to sender;
5. create sample receiver address;
6. create and append transfer;
7. validate local state;
8. detect obvious tampering;
9. list transfer events;
10. export proof snapshot;
11. prepare local Proof Explorer.

This is a local demo only.

It does not create PRM with monetary value.

---

## 10. Invalid-State Error Message Improvements

This milestone improves CLI error messages for invalid local MVP states.

Improved areas include:

- missing wallet;
- wallet sender mismatch;
- invalid amount;
- zero amount;
- invalid address;
- insufficient balance;
- invalid event hash;
- rule version mismatch;
- local ledger inconsistency.

Better errors improve local developer experience but do not imply production readiness.

---

## 11. CI Verification

The GitHub Actions Rust CI has passed for the v0.8.0-cli-integration-hardening milestone.

The workflow verifies:

```bash
cargo fmt --all -- --check
cargo build --workspace --all-targets
cargo test --workspace --all-targets
cargo run -p proofmoney-cli -- reset-ledger --yes
cargo run -p proofmoney-cli -- reset-ledger --json --yes
cargo run -p proofmoney-cli -- starting-state
cargo run -p proofmoney-cli -- starting-state --json
cargo run -p proofmoney-cli -- simulate-release --interval 1
cargo run -p proofmoney-cli -- simulate-release --interval 1 --append
cargo run -p proofmoney-cli -- ledger-status
cargo run -p proofmoney-cli -- verify-supply
cargo run -p proofmoney-cli -- verify-rule
cargo run -p proofmoney-cli -- integrity-status
cargo run -p proofmoney-cli -- validate-local-state
cargo run -p proofmoney-cli -- validate-local-state --json
cargo run -p proofmoney-cli -- detect-tampering
cargo run -p proofmoney-cli -- detect-tampering --json
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
bash scripts/demo-transfer-local.sh
```

---

## 12. Completed Milestone Scope

The v0.8.0-cli-integration-hardening milestone covers:

1. isolated CLI integration test framework;
2. local ledger reset command;
3. local state validation command;
4. local ledger tamper detection command;
5. proof export freshness indicator;
6. end-to-end local transfer demo;
7. invalid-state error message improvement;
8. v0.8.0 CLI integration hardening report and release notes.

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
- independent external audit;
- exchange integration;
- token sale;
- airdrop claim;
- yield product.

The wallet module is experimental and must not be used with valuable assets.

---

## 14. Next Engineering Priorities

Recommended next milestone:

```text
v0.9.0-protocol-spec-freeze
```

Suggested priorities:

1. draft protocol spec v0.1;
2. define stable event schema;
3. define stable proof result schema;
4. define amount model specification;
5. define release curve specification;
6. define local ledger state specification;
7. define proof export JSON schema;
8. define wallet safety boundary specification;
9. prepare public protocol spec docs;
10. freeze MVP protocol semantics before broader promotion.

---

## 15. Safety Statement

ProofMoney does not offer, sell, or solicit the purchase of PRM.

PRM does not guarantee price, liquidity, yield, profit, or exchange access.

ProofMoney is experimental and may fail.

Test units, if any, have no monetary value.

This report is not an external audit report.

---

## 16. Final Statement

ProofMoney Core v0.8.0-cli-integration-hardening is not a finished monetary network.

It is a local MVP prototype with stronger CLI integration hardening, local state validation, tamper detection, and demo repeatability.

If money cannot be verified, it is only a promise.
