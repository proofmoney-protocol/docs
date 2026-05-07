# ProofMoney Core MVP Report v0.3.0-ownership-and-flow

**Version:** v0.3.0-ownership-and-flow  
**Project:** ProofMoney  
**Repository:** https://github.com/proofmoney-protocol/core  
**Website:** https://proofmoney.org  
**Initial Author:** Vingen Motoki  
**Status:** Local ownership and flow MVP prototype  
**Core Statement:** If money cannot be verified, it is only a promise.

---

## 1. Purpose

This report records the third ProofMoney Core MVP milestone.

The purpose of v0.3.0-ownership-and-flow is to move the local MVP from ledger persistence and release-event validation into local wallet, ownership, transfer, balance, and Proof of Flow validation.

This milestone strengthens the ability to verify who controls value and how value moves inside the local MVP.

---

## 2. Current Status

ProofMoney Core v0.3.0-ownership-and-flow is a local Rust prototype.

It includes:

- local wallet persistence;
- local address inspection;
- message signing;
- ownership proof CLI flow;
- transfer event model;
- deterministic transfer event hashing;
- local balance tracking;
- insufficient balance rejection;
- stronger Proof of Flow;
- GitHub Actions CI.

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

## 4. Implemented in v0.3.0-ownership-and-flow

This milestone implements:

| Area | Status |
|---|---|
| Local wallet file persistence | Implemented |
| No silent wallet overwrite without `--force` | Implemented |
| `new-address` CLI command | Implemented |
| Local wallet message signing | Implemented |
| Ownership proof CLI flow | Implemented |
| Transfer event model | Implemented |
| Deterministic transfer event hashing | Implemented |
| Local balance tracking | Implemented |
| Insufficient balance rejection | Implemented |
| Stronger Proof of Flow | Implemented |
| `create-transfer` CLI command | Implemented |
| `verify-flow` CLI command | Implemented |

---

## 5. Local Wallet Storage

The local MVP stores wallet state at:

```text
~/.proofmoney/wallets/default.json
```

This file is local only.

It is not production custody software.

It must not be used with valuable assets.

The wallet command should warn clearly that the wallet is experimental.

---

## 6. Current CLI Commands

The current CLI supports:

```bash
cargo run -p proofmoney-cli -- create-wallet
cargo run -p proofmoney-cli -- new-address
cargo run -p proofmoney-cli -- sign-message --message "verify ownership"
cargo run -p proofmoney-cli -- verify-ownership --address <address> --message <message> --signature <signature> --public-key <public_key>
cargo run -p proofmoney-cli -- simulate-release --interval 1 --recipient <address> --append
cargo run -p proofmoney-cli -- create-transfer --from <address> --to <address> --amount 1.25
cargo run -p proofmoney-cli -- create-transfer --from <address> --to <address> --amount 1.25 --append
cargo run -p proofmoney-cli -- verify-flow --tx <transaction_id>
```

---

## 7. Ownership Flow

The local ownership flow is:

```text
Create local wallet
Inspect local address
Sign a message
Verify ownership with address + message + signature + public key
```

Example:

```bash
cargo run -p proofmoney-cli -- create-wallet
cargo run -p proofmoney-cli -- new-address
cargo run -p proofmoney-cli -- sign-message --message "verify ownership"
```

Ownership proof verifies local key control only.

It does not prove market value, custody safety, network finality, or investment status.

---

## 8. Transfer Flow

The local transfer flow is:

```text
Load local wallet
Validate sender address
Validate receiver address
Parse amount using integer-only smallest units
Create transfer signing message
Sign transfer event
Verify Proof of Flow
Optionally append transfer event
Update local balances
```

Example:

```bash
cargo run -p proofmoney-cli -- create-transfer --from <address> --to <address> --amount 1.25 --append
```

Transfer events are local MVP state transitions only.

They are not public network transactions.

---

## 9. Local Balance Tracking

v0.3.0 introduces local balance tracking from ledger events.

The local balance model:

- credits release recipient;
- credits Public Proof Fund allocation;
- debits transfer sender;
- credits transfer receiver;
- rejects insufficient balance;
- computes balances from local ledger events.

This supports stronger Proof of Flow in the local MVP.

---

## 10. Proof of Flow

The stronger Proof of Flow checks:

- transfer event structure;
- sender address validity;
- receiver address validity;
- amount greater than zero;
- signature presence;
- signature validity where possible;
- address and public key relationship;
- sender balance sufficiency;
- deterministic event hash validity.

This is still local MVP validation.

It does not imply public consensus or real asset settlement.

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
cargo run -p proofmoney-cli -- create-wallet
cargo run -p proofmoney-cli -- new-address
```

The CI has passed for the v0.3.0-ownership-and-flow milestone.

---

## 12. Completed Milestone Scope

The v0.3.0-ownership-and-flow milestone covers:

1. local wallet file persistence;
2. `new-address` CLI command;
3. ownership proof CLI flow;
4. transfer event model;
5. `create-transfer` CLI command;
6. local balance tracking;
7. insufficient balance rejection;
8. stronger Proof of Flow.

---

## 13. MVP Limitations

The current MVP remains intentionally limited.

It does not include:

- public network;
- public node consensus;
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
v0.4.0-proof-explorer-api
```

Suggested priorities:

1. build local Proof API outputs;
2. expose read-only proof JSON endpoints;
3. create Proof Explorer static interface;
4. display Starting State proof;
5. display supply proof;
6. display release event proof;
7. display ownership proof examples;
8. display flow proof examples;
9. add local data export;
10. prepare external Rust code review.

---

## 15. Safety Statement

ProofMoney does not offer, sell, or solicit the purchase of PRM.

PRM does not guarantee price, liquidity, yield, profit, or exchange access.

ProofMoney is experimental and may fail.

Test units, if any, have no monetary value.

---

## 16. Final Statement

ProofMoney Core v0.3.0-ownership-and-flow is not a finished monetary network.

It is a local proof prototype.

It shows that ProofMoney can move from written protocol principles into verifiable local ownership and flow logic.

If money cannot be verified, it is only a promise.
