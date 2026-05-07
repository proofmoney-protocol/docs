# ProofMoney Core MVP Report v0.4.0-proof-explorer-api

**Version:** v0.4.0-proof-explorer-api  
**Project:** ProofMoney  
**Repository:** https://github.com/proofmoney-protocol/core  
**Website:** https://proofmoney.org  
**Initial Author:** Vingen Motoki  
**Status:** Local proof export and Proof Explorer MVP prototype  
**Core Statement:** If money cannot be verified, it is only a promise.

---

## 1. Purpose

This report records the fourth ProofMoney Core MVP milestone.

The purpose of v0.4.0-proof-explorer-api is to move the project from command-line verification into local proof export and local proof visualization.

This milestone introduces local proof snapshot export, local Proof API JSON structures, release event listings, transfer event listings, and a static local Proof Explorer prototype.

---

## 2. Current Status

ProofMoney Core v0.4.0-proof-explorer-api is a local Rust prototype.

It includes:

- local proof snapshot export;
- local Proof API JSON output structure;
- local proof export directory;
- release event proof listing;
- transfer event proof listing;
- static local Proof Explorer prototype;
- explorer data preparation command;
- GitHub Actions CI.

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

## 4. Implemented in v0.4.0-proof-explorer-api

This milestone implements:

| Area | Status |
|---|---|
| Proof snapshot export command | Implemented |
| Local Proof API JSON output structure | Implemented |
| Local proof export directory | Implemented |
| Release event proof listing | Implemented |
| Transfer event proof listing | Implemented |
| Static local Proof Explorer prototype | Implemented |
| Explorer data preparation command | Implemented |
| CLI smoke tests for proof export commands | Implemented |

---

## 5. Local Proof Export Directory

The local MVP exports proof JSON files to:

```text
~/.proofmoney/export/
```

Expected files:

```text
starting-state.json
ledger-status.json
supply.json
rule.json
integrity-status.json
release-events.json
transfer-events.json
proof-snapshot.json
```

These files are local MVP proof data only.

They are not public network state.

They do not create PRM with monetary value.

---

## 6. Static Local Proof Explorer

The MVP prepares a static local Proof Explorer under:

```text
~/.proofmoney/explorer/
```

Expected files:

```text
index.html
styles.css
README.md
data/
```

The explorer displays:

- Integrity Status;
- Ledger Status;
- Supply;
- Rule;
- Release Events;
- Transfer Events;
- Risk Notice.

This is a static local proof viewer only.

It is not a hosted public block explorer.

It is not a trading interface.

It is not a claim page.

---

## 7. Current CLI Commands

The current proof export and explorer commands are:

```bash
cargo run -p proofmoney-cli -- export-proof-snapshot
cargo run -p proofmoney-cli -- export-proof-snapshot --json
cargo run -p proofmoney-cli -- export-proof-snapshot --output proof-snapshot.json
cargo run -p proofmoney-cli -- export-proof-site-data
cargo run -p proofmoney-cli -- list-release-events
cargo run -p proofmoney-cli -- list-release-events --json
cargo run -p proofmoney-cli -- list-transfer-events
cargo run -p proofmoney-cli -- list-transfer-events --json
cargo run -p proofmoney-cli -- prepare-explorer
```

---

## 8. Local Proof Snapshot

The proof snapshot is intended to provide a single local JSON object containing:

- project metadata;
- generated timestamp;
- safety notice;
- Starting State proof;
- Ledger Status;
- Supply proof;
- Rule proof;
- Integrity Status;
- Release Events;
- Transfer Events.

This helps external readers, contributors, and future tools inspect ProofMoney local MVP state in a structured way.

---

## 9. Local Proof API JSON Structure

v0.4.0 defines stable local proof output structures for:

```text
starting-state
ledger-status
supply
rule
integrity-status
release-events
transfer-events
proof-snapshot
```

Each output is designed to be understandable by humans and usable by future tools.

The local Proof API JSON output is not a hosted API.

It is a local data format contract.

---

## 10. Release Event Listing

Release event listing exports:

- event id;
- height;
- timestamp;
- recipient;
- actual release;
- Public Proof Fund allocation;
- contributor reward;
- event hash;
- event hash validity;
- proof status.

This improves inspectability of Proof of Issuance.

---

## 11. Transfer Event Listing

Transfer event listing exports:

- transaction id;
- height;
- timestamp;
- sender;
- receiver;
- amount;
- fee;
- event hash;
- event hash validity;
- flow proof status;
- MVP scope.

This improves inspectability of Proof of Flow.

---

## 12. CI Verification

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
```

The CI has passed for the v0.4.0-proof-explorer-api milestone.

---

## 13. Completed Milestone Scope

The v0.4.0-proof-explorer-api milestone covers:

1. proof snapshot export command;
2. local Proof API JSON output structure;
3. local proof export directory;
4. release event proof listing;
5. transfer event proof listing;
6. static Proof Explorer prototype;
7. explorer data preparation command;
8. v0.4.0 MVP report and release notes.

---

## 14. MVP Limitations

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

The Proof Explorer is a local static proof viewer only.

The wallet module is experimental and must not be used with valuable assets.

---

## 15. Next Engineering Priorities

Recommended next milestone:

```text
v0.5.0-developer-release
```

Suggested priorities:

1. improve developer onboarding;
2. add CLI help examples;
3. add sample proof data fixtures;
4. add local demo script;
5. add architecture diagram;
6. add external code review checklist;
7. prepare contributor guide v1.0;
8. prepare security review scope;
9. prepare public developer announcement draft;
10. freeze MVP scope before external review.

---

## 16. Safety Statement

ProofMoney does not offer, sell, or solicit the purchase of PRM.

PRM does not guarantee price, liquidity, yield, profit, or exchange access.

ProofMoney is experimental and may fail.

Test units, if any, have no monetary value.

---

## 17. Final Statement

ProofMoney Core v0.4.0-proof-explorer-api is not a finished monetary network.

It is a local proof export and local proof visualization prototype.

It shows that ProofMoney proof outputs can be exported, inspected, and prepared for explorer-style viewing without relying only on command-line output.

If money cannot be verified, it is only a promise.
