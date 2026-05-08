# ProofMoney Core MVP Report v1.1.0-testnet-design

**Version:** v1.1.0-testnet-design  
**Project:** ProofMoney  
**Repository:** https://github.com/proofmoney-protocol/core  
**Website:** https://proofmoney.org  
**Initial Author:** Vingen Motoki  
**Status:** Public testnet design release  
**Core Statement:** If money cannot be verified, it is only a promise.

---

## 1. Purpose

This report records the ProofMoney Core v1.1.0 public testnet design milestone.

The purpose of v1.1.0-testnet-design is to define the architecture and safety boundaries for a future public testnet before public-network implementation begins.

This milestone is design-only.

It does not launch a public testnet.

It does not launch mainnet.

It does not create PRM with monetary value.

---

## 2. Current Status

ProofMoney Core has completed:

```text
v1.0.0-local-mvp-freeze
```

and now has public testnet design documents under:

```text
docs/testnet/
```

At this stage:

- no public testnet is live;
- no mainnet is live;
- no public hosted API is live;
- no faucet is live;
- no PRM is being sold;
- no test unit has monetary value;
- no exchange listing is promised;
- no yield is promised;
- no airdrop or claim page exists;
- no test-to-main conversion is promised;
- no external audit has been completed.

---

## 3. Implemented in v1.1.0

| Area | Status |
|---|---|
| Public testnet goals and scope | Implemented |
| Testnet node architecture | Implemented |
| Testnet network message model | Implemented |
| Testnet ledger sync model | Implemented |
| Testnet faucet boundary | Implemented |
| Public testnet explorer requirements | Implemented |
| Testnet wallet safety policy | Implemented |
| v1.1.0 testnet design report and release notes | Implemented |

---

## 4. Testnet Design Index

The testnet design index is located at:

```text
docs/testnet/testnet-design-index-v1.1.0.md
```

It links the core testnet design documents:

```text
docs/testnet/testnet-goals-and-scope-v1.1.0.md
docs/testnet/testnet-node-architecture-v1.1.0.md
docs/testnet/testnet-network-message-model-v1.1.0.md
docs/testnet/testnet-ledger-sync-model-v1.1.0.md
docs/testnet/testnet-faucet-boundary-v1.1.0.md
docs/testnet/testnet-explorer-requirements-v1.1.0.md
docs/testnet/testnet-wallet-safety-policy-v1.1.0.md
```

---

## 5. Public Testnet Goals and Scope

The public testnet goals and scope document defines:

- purpose of the public testnet;
- what developers can test;
- what proof types should be exposed;
- expected CLI / API flows;
- what is explicitly out of scope;
- difference between local MVP, public testnet, and future mainnet;
- test unit safety boundary.

Core boundary:

```text
Public testnet units have no monetary value and do not imply future mainnet allocation.
```

---

## 6. Testnet Node Architecture

The node architecture document defines:

- node responsibilities;
- local ledger vs testnet ledger distinction;
- node storage model;
- event acceptance flow;
- proof verification flow;
- read API responsibilities;
- write API responsibilities;
- node operator assumptions;
- MVP simplifications.

The document makes clear that this is architecture design only, not a public network launch.

---

## 7. Testnet Network Message Model

The network message model document defines initial message categories for:

- node status;
- event submission;
- event broadcast;
- ledger state query;
- proof query;
- transfer event query;
- release event query;
- error response;
- version negotiation.

It includes request / response examples and versioning assumptions.

The message model is for testnet design only and does not define final mainnet consensus.

---

## 8. Testnet Ledger Sync Model

The ledger sync model document defines:

- sync purpose;
- event ordering assumptions;
- height-based sync;
- last event hash checking;
- event hash verification;
- invalid event rejection;
- resync behavior;
- MVP sync limitations;
- future consensus gap.

Core distinction:

```text
Ledger sync is not the same as public consensus.
```

---

## 9. Testnet Faucet Boundary

The faucet boundary document defines:

- faucet purpose;
- test unit distribution rules;
- rate limit assumptions;
- abuse prevention;
- no monetary value statement;
- no airdrop statement;
- no test-to-main conversion promise;
- faucet logging expectations;
- safety language.

Required statements:

```text
Testnet units have no monetary value.
Testnet faucet distribution is not an airdrop and does not imply future PRM allocation.
Testnet units do not convert to mainnet PRM.
```

---

## 10. Public Testnet Explorer Requirements

The explorer requirements document defines:

- ledger height display;
- event listing;
- release event view;
- transfer event view;
- proof result display;
- supply proof display;
- tamper / invalid state indicators;
- API data source;
- safety notices;
- no trading / no claim page boundary.

The explorer must not include:

- price chart;
- trading button;
- swap interface;
- claim page;
- airdrop eligibility;
- investment language;
- yield display;
- exchange listing language.

---

## 11. Testnet Wallet Safety Policy

The wallet safety policy document defines:

- testnet wallet purpose;
- testnet address format;
- private key warning;
- test unit warning;
- no production custody statement;
- no valuable asset usage;
- key backup warning;
- wallet reset behavior;
- future production wallet gap.

Required warning:

```text
The testnet wallet is experimental and is not production custody software.
```

---

## 12. CI Verification

The GitHub Actions Rust CI has passed for the v1.1.0-testnet-design milestone.

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

## 13. Completed Milestone Scope

The v1.1.0-testnet-design milestone covers:

1. public testnet goals and scope;
2. testnet node architecture;
3. testnet network message model;
4. testnet ledger sync model;
5. testnet faucet boundary;
6. public testnet explorer requirements;
7. testnet wallet safety policy;
8. v1.1.0 testnet design report and release notes.

---

## 14. Known Limitations

This milestone does not include:

- public testnet implementation;
- public node;
- public hosted API;
- hosted explorer;
- live faucet;
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
v1.2.0-testnet-node-api
```

Suggested priorities:

1. define crate/module structure for a testnet node;
2. add minimal HTTP read API design;
3. add node status endpoint;
4. add ledger status endpoint;
5. add proof query endpoint;
6. add event list endpoint;
7. add transfer event submission API draft;
8. add faucet API draft with disabled-by-default safety gate;
9. add testnet node README;
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

ProofMoney Core v1.1.0-testnet-design prepares the public testnet architecture boundary after the first stable local MVP baseline.

It is design-only.

If money cannot be verified, it is only a promise.
