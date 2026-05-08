# ProofMoney Core MVP Report v1.3.0-testnet-read-api-server

**Version:** v1.3.0-testnet-read-api-server  
**Project:** ProofMoney  
**Repository:** https://github.com/proofmoney-protocol/core  
**Website:** https://proofmoney.org  
**Initial Author:** Vingen Motoki  
**Status:** Local read-only testnet API server skeleton release  
**Core Statement:** If money cannot be verified, it is only a promise.

---

## 1. Purpose

This report records the ProofMoney Core v1.3.0 local read-only API server skeleton milestone.

The purpose of v1.3.0-testnet-read-api-server is to move `proofmoney-node` from API model structures into a local read-only route handling skeleton.

This milestone is still not a public testnet launch.

It does not launch mainnet.

It does not create PRM with monetary value.

---

## 2. Current Status

ProofMoney Core now has:

- stable local MVP baseline;
- public testnet design documents;
- minimal testnet node/API model skeleton;
- local read-only API server skeleton.

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

## 3. Implemented in v1.3.0

| Area | Status |
|---|---|
| Local read-only API server skeleton | Implemented |
| `GET /health` route model | Implemented |
| `GET /status` route model | Implemented |
| `GET /ledger/status` route model | Implemented |
| `GET /proofs/:proof_type` route model | Implemented |
| `GET /events` route model | Implemented |
| `GET /events/releases` route model | Implemented |
| `GET /events/transfers` route model | Implemented |
| Local API server smoke tests | Implemented |
| v1.3.0 read API server report and release notes | Implemented |

---

## 4. Local Read-Only API Server

New server module:

```text
crates/proofmoney-node/src/server.rs
```

The module provides:

- `LocalReadApiServer`;
- local bind config model;
- route dispatcher;
- JSON response wrapper;
- structured error response;
- smoke tests for local read-only routes.

Default bind policy:

```text
host: 127.0.0.1
port: 8787
```

---

## 5. GET /health

Response includes:

- status;
- service name;
- node version;
- mode;
- safety notice.

This endpoint only confirms local server process status.

---

## 6. GET /status

Response includes:

- node version;
- network name;
- protocol version;
- mode;
- ledger height;
- event count;
- last event hash;
- sync status;
- write API enabled;
- faucet enabled;
- safety notice.

Write API and faucet are false by default.

---

## 7. GET /ledger/status

Response includes:

- ledger version;
- current height;
- current supply;
- Public Proof Fund balance;
- rule version;
- event count;
- last event hash;
- network label;
- safety notice.

Ledger status is local/testnet visibility only and does not define public consensus.

---

## 8. GET /proofs/:proof_type

Supported proof path values:

```text
starting-state
supply
rule
flow
integrity-status
```

Unsupported proof types return structured errors.

Proof outputs are local/testnet verification results only and do not imply external audit.

---

## 9. Event Endpoints

Implemented route models:

```text
GET /events
GET /events/releases
GET /events/transfers
```

The current skeleton supports empty event lists and pagination placeholders.

Event listing is not a trading, claim, faucet, or exchange interface.

---

## 10. Disabled Write APIs

The following remain disabled by default:

```text
POST /events
POST /faucet/request
```

No public write API is launched.

No faucet is live.

---

## 11. Smoke Tests

The `proofmoney-node` crate includes unit tests for:

- localhost bind config;
- health route;
- status route;
- ledger status route;
- proof query route;
- unsupported proof error;
- event list routes;
- unsupported route error.

---

## 12. CI Verification

The GitHub Actions Rust CI has passed for the v1.3.0-testnet-read-api-server milestone.

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

The v1.3.0-testnet-read-api-server milestone covers:

1. local read-only API server feature;
2. `GET /health`;
3. `GET /status`;
4. `GET /ledger/status`;
5. `GET /proofs/:proof_type`;
6. `GET /events`, `GET /events/releases`, `GET /events/transfers`;
7. local API server smoke tests and README;
8. v1.3.0 read API server report and release notes.

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
v1.4.0-testnet-write-api-sandbox
```

Suggested priorities:

1. keep write API disabled by default;
2. add event submission validation pipeline;
3. add sandbox-only transfer submission model;
4. add rejection reasons;
5. add rate limit placeholders;
6. add write API safety gates;
7. add faucet remains disabled policy;
8. add write API tests;
9. document no public testnet launch;
10. keep mainnet, sale, airdrop, yield, and exchange scope frozen.

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

ProofMoney Core v1.3.0-testnet-read-api-server adds a local read-only API server skeleton.

It is not a live network.

If money cannot be verified, it is only a promise.
