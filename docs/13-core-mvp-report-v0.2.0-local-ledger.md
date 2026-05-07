# ProofMoney Core MVP Report v0.2.0-local-ledger

**Version:** v0.2.0-local-ledger  
**Project:** ProofMoney  
**Repository:** https://github.com/proofmoney-protocol/core  
**Website:** https://proofmoney.org  
**Initial Author:** Vingen Motoki  
**Status:** Local ledger MVP prototype  
**Core Statement:** If money cannot be verified, it is only a promise.

---

## 1. Purpose

This report records the second ProofMoney Core MVP milestone.

The purpose of v0.2.0-local-ledger is to move the project from a CLI scaffold into a working local ledger prototype.

This milestone focuses on local state persistence, event append flow, deterministic event hashing, and computed supply verification.

---

## 2. Current Status

ProofMoney Core v0.2.0-local-ledger is a local Rust prototype.

It includes:

- local ledger JSON persistence;
- deterministic release event hashing;
- release event append flow;
- computed supply verification;
- Public Proof Fund balance tracking;
- `ledger-status` CLI command;
- stronger release event validation;
- updated GitHub Actions CI smoke tests.

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

## 4. Implemented in v0.2.0-local-ledger

This milestone implements:

| Area | Status |
|---|---|
| Deterministic event hashing | Implemented |
| Event hash excludes mutable hash field | Implemented |
| Local ledger JSON persistence | Implemented |
| Release event append flow | Implemented |
| Current supply update from events | Implemented |
| Public Proof Fund balance update from events | Implemented |
| Computed supply verification | Implemented |
| `ledger-status` CLI | Implemented |
| Stronger release event validation | Implemented |
| CI smoke tests for local ledger flow | Implemented |

---

## 5. Local Ledger Storage

The local MVP stores ledger state at:

```text
~/.proofmoney/ledger.json
```

This file is local only.

It is not a public network state.

It does not create PRM with market value.

It is only a local prototype state file for testing verification logic.

---

## 6. Current CLI Commands

The current CLI supports:

```bash
cargo run -p proofmoney-cli -- starting-state
cargo run -p proofmoney-cli -- starting-state --json
cargo run -p proofmoney-cli -- simulate-release --interval 1
cargo run -p proofmoney-cli -- simulate-release --interval 1 --append
cargo run -p proofmoney-cli -- ledger-status
cargo run -p proofmoney-cli -- ledger-status --json
cargo run -p proofmoney-cli -- verify-supply
cargo run -p proofmoney-cli -- verify-rule
cargo run -p proofmoney-cli -- integrity-status
cargo run -p proofmoney-cli -- create-wallet
```

---

## 7. Local Ledger Flow

The new local ledger flow is:

```text
Load or initialize local ledger
Generate release event
Validate release event
Append event to ledger
Update current supply
Update Public Proof Fund balance
Save ledger to local JSON
Verify computed supply
Inspect ledger status
```

Example command:

```bash
cargo run -p proofmoney-cli -- simulate-release --interval 1 --append
```

Expected effect:

```text
Current Supply: 5.00000000 PRM
Public Proof Fund Balance: 0.15000000 PRM
```

---

## 8. Deterministic Event Hashing

v0.2.0-local-ledger introduces deterministic event hashing.

The event hash is based on a stable event hash view and excludes the mutable `hash` field itself.

This is necessary because an event cannot safely hash itself while including its own hash field.

The intended rule:

```text
Same event content = same event hash
Changed event content = changed event hash
Mutable hash field is excluded from the hash input
```

---

## 9. Computed Supply Verification

Proof of Supply now checks computed supply from ledger events.

The verification model compares:

```text
stored current supply
computed supply from release events
maximum supply boundary
```

The goal is to move toward a model where supply is computed, not merely claimed.

---

## 10. Release Event Validation

Release event validation now checks:

- event type;
- rule version;
- event hash;
- interval presence;
- actual release amount;
- Public Proof Fund allocation;
- contributor reward;
- privileged allocation flag;
- supply boundary impact.

This strengthens Proof of Issuance.

---

## 11. CI Verification

The GitHub Actions Rust CI verifies:

```bash
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
```

The CI has passed for the v0.2.0-local-ledger milestone.

---

## 12. Completed Milestone Scope

The v0.2.0-local-ledger milestone covers:

1. deterministic event hashing;
2. local ledger JSON persistence;
3. appending release events to local ledger;
4. computing supply from ledger events;
5. ledger status CLI command;
6. stronger release event validation;
7. expanded CI smoke tests.

---

## 13. MVP Limitations

The current MVP remains intentionally limited.

It does not include:

- public network;
- public node consensus;
- production wallet security;
- full transaction engine;
- full account or UTXO balance engine;
- full double-spend prevention;
- production key management;
- independent security audit;
- exchange integration;
- token sale;
- airdrop claim;
- yield product.

The Proof of Flow module remains simplified.

The wallet module is experimental and must not be used with valuable assets.

---

## 14. Next Engineering Priorities

Recommended next milestone:

```text
v0.3.0-ownership-and-flow
```

Suggested priorities:

1. improve wallet key handling;
2. implement safer local wallet persistence;
3. implement account balance tracking;
4. implement transfer event creation;
5. verify transfer signature;
6. reject insufficient balance;
7. improve Proof of Flow;
8. add tests for valid and invalid transfer cases;
9. add JSON output for flow verification;
10. prepare external Rust code review.

---

## 15. Safety Statement

ProofMoney does not offer, sell, or solicit the purchase of PRM.

PRM does not guarantee price, liquidity, yield, profit, or exchange access.

ProofMoney is experimental and may fail.

Test units, if any, have no monetary value.

---

## 16. Final Statement

ProofMoney Core v0.2.0-local-ledger is not a finished monetary network.

It is a local proof prototype.

It shows that ProofMoney can move from written protocol principles into verifiable local state transitions.

If money cannot be verified, it is only a promise.
