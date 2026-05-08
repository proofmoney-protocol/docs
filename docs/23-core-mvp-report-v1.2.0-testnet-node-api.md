# ProofMoney Core MVP Report v1.2.0-testnet-node-api

**Version:** v1.2.0-testnet-node-api  
**Project:** ProofMoney  
**Repository:** https://github.com/proofmoney-protocol/core  
**Website:** https://proofmoney.org  
**Initial Author:** Vingen Motoki  
**Status:** Minimal testnet node/API skeleton release  
**Core Statement:** If money cannot be verified, it is only a promise.

---

## 1. Purpose

This report records the ProofMoney Core v1.2.0 testnet node/API skeleton milestone.

The purpose of v1.2.0-testnet-node-api is to add the first minimal `proofmoney-node` crate and API model layer after the v1.1.0 public testnet design milestone.

This milestone is still not a public testnet launch.

It does not launch mainnet.

It does not create PRM with monetary value.

---

## 2. Current Status

ProofMoney Core now has:

- stable local MVP baseline;
- public testnet design documents;
- first minimal testnet node/API model skeleton.

At this stage:

- no public testnet is live;
- no mainnet is live;
- no public hosted API is live;
- no faucet is live;
- no public write API is enabled;
- no PRM is being sold;
- no test unit has monetary value;
- no exchange listing is promised;
- no yield is promised;
- no airdrop or claim page exists;
- no test-to-main conversion is promised;
- no external audit has been completed.

---

## 3. Implemented in v1.2.0

| Area | Status |
|---|---|
| `proofmoney-node` crate skeleton | Implemented |
| Testnet node status API model | Implemented |
| Testnet ledger status API model | Implemented |
| Testnet proof query API model | Implemented |
| Testnet event list API model | Implemented |
| Disabled-by-default event submission API draft | Implemented |
| Disabled-by-default faucet API draft | Implemented |
| v1.2.0 testnet node/API report and release notes | Implemented |

---

## 4. proofmoney-node Crate Skeleton

New crate:

```text
crates/proofmoney-node/
```

The crate includes:

```text
Cargo.toml
src/lib.rs
src/config.rs
src/api.rs
src/service.rs
README.md
```

The crate is registered in the workspace and builds with CI.

---

## 5. Node Status API Model

Proposed endpoint:

```text
GET /status
```

The model includes:

- node version;
- network name;
- protocol version;
- mode;
- ledger height;
- event count;
- last event hash;
- sync status;
- write API enabled flag;
- faucet enabled flag;
- safety notice.

---

## 6. Ledger Status API Model

Proposed endpoint:

```text
GET /ledger/status
```

The model includes:

- ledger version;
- current height;
- current supply;
- Public Proof Fund balance;
- rule version;
- event count;
- last event hash;
- network label;
- safety notice.

The model exposes testnet/local state only and does not define public consensus.

---

## 7. Proof Query API Model

Proposed endpoint:

```text
GET /proofs/:proof_type
```

Supported model proof types:

- Starting State Proof;
- Proof of Supply;
- Proof of Rule;
- Proof of Flow;
- Integrity Status.

Proof outputs are testnet/local MVP verification results and do not imply external audit or public settlement finality.

---

## 8. Event List API Model

Proposed endpoint designs:

```text
GET /events
GET /events/releases
GET /events/transfers
```

The event list model includes:

- all events;
- release events;
- transfer events;
- pagination fields;
- event hash validity;
- event status;
- safety notice.

Event listing is for testnet proof visibility only and is not a trading, claim, or exchange interface.

---

## 9. Disabled Event Submission API Draft

Proposed endpoint:

```text
POST /events
```

In v1.2.0 this API is model-only and disabled by default.

No public write API is launched.

---

## 10. Disabled Faucet API Draft

Proposed endpoint:

```text
POST /faucet/request
```

In v1.2.0 this API is model-only and disabled by default.

The faucet model includes:

- rate limit status;
- denial reason;
- no monetary value notice;
- no airdrop notice;
- no test-to-main conversion notice;
- safety notice.

There is no live faucet in this release.

---

## 11. Node README

New file:

```text
crates/proofmoney-node/README.md
```

It documents:

- crate status;
- purpose;
- included models;
- what it is not;
- safety boundary.

---

## 12. CI Verification

The GitHub Actions Rust CI has passed for the v1.2.0-testnet-node-api milestone.

The workflow verifies:

```bash
cargo fmt --all -- --check
cargo build --workspace --all-targets
cargo test --workspace --all-targets
bash scripts/demo-local.sh
bash scripts/demo-transfer-local.sh
```

---

## 13. Completed Milestone Scope

The v1.2.0-testnet-node-api milestone covers:

1. `proofmoney-node` crate skeleton;
2. node status API model;
3. ledger status API model;
4. proof query API model;
5. event list API model;
6. disabled-by-default event submission draft;
7. disabled-by-default faucet API draft;
8. v1.2.0 testnet node/API report and release notes.

---

## 14. Known Limitations

This milestone does not include:

- live public testnet;
- public node deployment;
- hosted public API;
- live faucet;
- public write API;
- mainnet;
- public consensus;
- peer-to-peer networking;
- production wallet security;
- independent external audit;
- exchange integration;
- token sale;
- airdrop claim;
- yield product.

---

## 15. Next Engineering Priorities

Recommended next milestone:

```text
v1.3.0-testnet-read-api-server
```

Suggested priorities:

1. add HTTP server dependency behind feature flag;
2. implement local-only `/status`;
3. implement local-only `/ledger/status`;
4. implement local-only `/proofs/:proof_type`;
5. implement local-only `/events`;
6. add server config with disabled write APIs;
7. add API smoke tests;
8. add local server README;
9. keep faucet disabled;
10. keep public testnet launch, mainnet, sale, airdrop, yield, and exchange scope frozen.

---

## 16. Safety Statement

ProofMoney does not offer, sell, or solicit the purchase of PRM.

PRM does not guarantee price, liquidity, yield, profit, or exchange access.

ProofMoney is experimental and may fail.

Test units, if any, have no monetary value.

This report is not an external audit report.

This release is not a public testnet launch.

This release is not a mainnet launch.

---

## 17. Final Statement

ProofMoney Core v1.2.0-testnet-node-api adds the first minimal testnet node/API skeleton.

It is not a live network.

If money cannot be verified, it is only a promise.
