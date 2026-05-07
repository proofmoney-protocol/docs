# ProofMoney Core MVP Report v0.1.0-alpha

**Version:** v0.1.0-alpha  
**Project:** ProofMoney  
**Repository:** https://github.com/proofmoney-protocol/core  
**Website:** https://proofmoney.org  
**Initial Author:** Vingen Motoki  
**Status:** Local MVP scaffold  
**Core Statement:** If money cannot be verified, it is only a promise.

---

## 1. Purpose

This report records the first working Rust MVP scaffold for ProofMoney Core.

The purpose of this MVP is not to launch a public network.

The purpose is to prove that the ProofMoney concept can move from documents into a working local codebase with verifiable command-line outputs.

---

## 2. Current Status

ProofMoney Core v0.1.0-alpha is a local Rust prototype.

It includes a Cargo workspace, core crates, CLI commands, basic proof modules, local wallet model, and GitHub Actions CI.

At this stage:

- no public network is live;
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

## 4. Implemented Crates

The v0.1.0-alpha scaffold contains:

| Crate | Purpose |
|---|---|
| `proofmoney-cli` | Command-line interface |
| `proofmoney-types` | Shared domain types |
| `proofmoney-crypto` | Hashing, keys, signatures, addresses |
| `proofmoney-ledger` | Starting State and local ledger state |
| `proofmoney-release` | Proof Release Curve logic |
| `proofmoney-proof` | Proof Engine modules |
| `proofmoney-wallet` | Local experimental wallet model |
| `proofmoney-storage` | Local JSON storage helpers |

---

## 5. Implemented MVP Features

The current scaffold includes:

- integer-only amount model;
- `1 PRM = 100,000,000 proof`;
- Starting State generation;
- Starting State verification;
- Proof Release Curve simulation;
- protection window logic;
- Public Proof Fund allocation calculation;
- Proof of Supply;
- Proof of Rule;
- Proof of Ownership MVP;
- experimental local wallet creation;
- CLI smoke commands;
- GitHub Actions Rust CI.

---

## 6. Current CLI Commands

The current CLI supports:

```bash
cargo run -p proofmoney-cli -- starting-state
cargo run -p proofmoney-cli -- starting-state --json
cargo run -p proofmoney-cli -- simulate-release --interval 1
cargo run -p proofmoney-cli -- verify-supply
cargo run -p proofmoney-cli -- verify-rule
cargo run -p proofmoney-cli -- integrity-status
cargo run -p proofmoney-cli -- create-wallet
```

---

## 7. CI Verification

The GitHub Actions Rust CI verifies:

```bash
cargo build --workspace --all-targets
cargo test --workspace --all-targets
cargo run -p proofmoney-cli -- starting-state
cargo run -p proofmoney-cli -- starting-state --json
cargo run -p proofmoney-cli -- simulate-release --interval 1
cargo run -p proofmoney-cli -- verify-supply
cargo run -p proofmoney-cli -- verify-rule
cargo run -p proofmoney-cli -- integrity-status
```

The CI has passed for the v0.1.0-alpha scaffold.

---

## 8. Starting State Integrity

The Starting State is designed to verify:

```text
Initial Supply: 0 PRM
Founder Allocation: 0 PRM
Private Sale Allocation: 0 PRM
Hidden Address Allocation: 0 PRM
Public Proof Fund Preload: 0 PRM
Rule Version: v1
Status: Valid
```

This supports the Zero-Privilege Launch principle.

---

## 9. Proof Release Curve

The MVP includes early Proof Release Curve logic.

Current draft parameters:

```text
Initial Release Event Size: 25 PRM
Protection Window 1: 20%
Protection Window 2: 50%
Full Release Factor: 100%
Public Proof Fund Allocation: 3%
Proof Contributor Reward: 97%
Maximum Supply Boundary: 100,000,000 PRM
```

Example interval 1 result:

```text
Base Release: 25 PRM
Protection Factor: 20%
Actual Release: 5 PRM
Public Proof Fund: 0.15 PRM
Proof Contributor Reward: 4.85 PRM
```

---

## 10. MVP Limitations

The current MVP is intentionally limited.

It does not include:

- public network;
- public node consensus;
- production wallet security;
- full transaction engine;
- full balance engine;
- full double-spend prevention;
- production key management;
- independent security audit;
- exchange integration;
- token sale;
- airdrop claim;
- yield product.

The Proof of Flow module is still simplified.

The wallet module is experimental and must not be used with valuable assets.

---

## 11. Next Engineering Priorities

Next priorities:

1. strengthen deterministic event hashing;
2. persist local ledger state;
3. compute supply from release events;
4. improve ownership verification;
5. implement transfer state model;
6. implement basic balance tracking;
7. reject insufficient balance;
8. improve Proof of Flow;
9. restore strict formatting check in CI;
10. prepare code review by an external Rust engineer.

---

## 12. Safety Statement

ProofMoney does not offer, sell, or solicit the purchase of PRM.

PRM does not guarantee price, liquidity, yield, profit, or exchange access.

ProofMoney is experimental and may fail.

Test units, if any, have no monetary value.

---

## 13. Final Statement

ProofMoney Core v0.1.0-alpha is the first step from protocol concept to verifiable implementation.

It is not a finished monetary network.

It is a local proof prototype.

If money cannot be verified, it is only a promise.
