# ProofMoney Core MVP Report v0.9.0-protocol-spec-freeze

**Version:** v0.9.0-protocol-spec-freeze  
**Project:** ProofMoney  
**Repository:** https://github.com/proofmoney-protocol/core  
**Website:** https://proofmoney.org  
**Initial Author:** Vingen Motoki  
**Status:** Protocol specification freeze release  
**Core Statement:** If money cannot be verified, it is only a promise.

---

## 1. Purpose

This report records the ninth ProofMoney Core MVP milestone.

The purpose of v0.9.0-protocol-spec-freeze is to freeze the current local MVP protocol semantics as written specifications.

This milestone focuses on documenting:

- amount model;
- event schema;
- proof result schema;
- Proof Release Curve;
- local ledger state;
- proof export JSON;
- wallet and ownership safety boundary;
- frozen MVP semantics;
- known limitations.

This milestone does not claim external audit completion.

This milestone does not claim production readiness.

---

## 2. Current Status

ProofMoney Core v0.9.0-protocol-spec-freeze is a local Rust MVP prototype with frozen MVP protocol semantics.

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

## 3. Implemented in v0.9.0

| Area | Status |
|---|---|
| Amount Model Specification v0.1 | Implemented |
| Event Schema Specification v0.1 | Implemented |
| Proof Result Schema Specification v0.1 | Implemented |
| Proof Release Curve Specification v0.1 | Implemented |
| Local Ledger State Specification v0.1 | Implemented |
| Proof Export JSON Specification v0.1 | Implemented |
| Wallet and Ownership Safety Specification v0.1 | Implemented |
| Protocol spec freeze report and release notes | Implemented |

---

## 4. Protocol Specification Index

The protocol specification index is located at:

```text
docs/specs/protocol-spec-index-v0.1.md
```

It collects:

```text
docs/specs/amount-model-v0.1.md
docs/specs/event-schema-v0.1.md
docs/specs/proof-result-schema-v0.1.md
docs/specs/proof-release-curve-v0.1.md
docs/specs/local-ledger-state-v0.1.md
docs/specs/proof-export-json-v0.1.md
docs/specs/wallet-ownership-safety-v0.1.md
```

This index freezes the current local MVP protocol semantics.

It is not a public network specification, external audit, or production wallet specification.

---

## 5. Amount Model Specification

The Amount Model Specification v0.1 documents:

- smallest unit name;
- `1 PRM = 100,000,000 proof`;
- integer-only accounting;
- decimal display format;
- decimal parsing rules;
- invalid amount rules;
- zero amount behavior;
- maximum supply boundary;
- overflow safety expectations.

Core rule:

```text
All monetary-like calculations in the MVP should use integer proof units.
```

Floating-point monetary logic is not allowed.

---

## 6. Event Schema Specification

The Event Schema Specification v0.1 documents:

- common event fields;
- event id;
- event type;
- event height;
- timestamp;
- rule version;
- payload;
- event hash;
- release event payload;
- transfer event payload;
- event hash view;
- mutable fields excluded from hash;
- known MVP limitations.

Event hash rule:

```text
same event content = same hash
changed event content = changed hash
hash field itself is excluded
```

Known limitation:

```text
The local MVP event schema does not define public consensus.
```

---

## 7. Proof Result Schema Specification

The Proof Result Schema Specification v0.1 documents:

- proof result structure;
- proof type;
- proof status;
- rule version;
- data object;
- summary;
- safety notice;
- Starting State proof output;
- Proof of Supply output;
- Proof of Rule output;
- Proof of Ownership output;
- Proof of Flow output;
- Integrity Status output.

Proof results are local MVP verification outputs.

They do not imply external audit or public settlement finality.

---

## 8. Proof Release Curve Specification

The Proof Release Curve Specification v0.1 documents:

- purpose of the release curve;
- local MVP release simulation;
- actual release amount;
- Public Proof Fund allocation;
- proof contributor reward;
- interval behavior;
- supply boundary;
- what is not included;
- no sale / no allocation / no yield boundary.

The specification explicitly states that the Proof Release Curve is not:

- a sale schedule;
- a fundraising plan;
- an airdrop plan;
- a yield model;
- a price narrative.

---

## 9. Local Ledger State Specification

The Local Ledger State Specification v0.1 documents:

- ledger version;
- current height;
- current supply;
- Public Proof Fund balance;
- rule version;
- event list;
- last event hash;
- local storage path;
- reset behavior;
- validation behavior;
- tamper detection behavior;
- known local-only limitations.

Local ledger state is not public network consensus.

---

## 10. Proof Export JSON Specification

The Proof Export JSON Specification v0.1 documents:

- proof snapshot structure;
- export metadata;
- freshness metadata;
- starting state export;
- ledger status export;
- supply export;
- rule export;
- integrity status export;
- release events export;
- transfer events export;
- local explorer data expectations;
- stale export warning.

Required freshness warning:

```text
This proof export is a local snapshot. It can become stale after local ledger changes. Regenerate exports after state changes.
```

Proof exports are local MVP snapshots.

They are not signed public audit artifacts or public consensus.

---

## 11. Wallet and Ownership Safety Specification

The Wallet and Ownership Safety Specification v0.1 documents:

- MVP wallet purpose;
- local wallet path;
- address format;
- message signing;
- ownership proof boundary;
- private key exposure risk;
- what the wallet is not;
- forbidden production custody claims;
- user safety warnings.

Required warning:

```text
The MVP wallet is experimental and must not be used with valuable assets.
```

Forbidden wallet claims include:

```text
secure wallet
production wallet
safe custody
real PRM wallet
asset wallet
mainnet wallet
exchange wallet
```

---

## 12. Frozen MVP Semantics

v0.9.0 freezes the current local MVP semantics for:

- amount unit representation;
- event structure;
- event hashing boundary;
- proof result structure;
- local release simulation;
- local ledger state;
- local state validation;
- local proof export;
- MVP wallet safety boundary.

This freeze means future changes to these semantics should be:

- intentional;
- reviewed;
- documented;
- versioned.

---

## 13. What Is Not Frozen

This specification does not freeze:

- public network consensus;
- peer-to-peer behavior;
- mempool behavior;
- production wallet custody model;
- exchange integration;
- token sale mechanics;
- legal or regulatory classification;
- final economic policy;
- mainnet behavior.

---

## 14. CI Verification

The GitHub Actions Rust CI has passed for the v0.9.0-protocol-spec-freeze milestone.

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

## 15. Completed Milestone Scope

The v0.9.0-protocol-spec-freeze milestone covers:

1. Amount Model Specification v0.1;
2. Event Schema Specification v0.1;
3. Proof Result Schema Specification v0.1;
4. Proof Release Curve Specification v0.1;
5. Local Ledger State Specification v0.1;
6. Proof Export JSON Specification v0.1;
7. Wallet and Ownership Safety Specification v0.1;
8. v0.9.0 protocol spec freeze report and release notes.

---

## 16. MVP Limitations

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

## 17. Next Engineering Priorities

Recommended next milestone:

```text
v1.0.0-local-mvp-freeze
```

Suggested priorities:

1. consolidate all current docs into a local MVP freeze package;
2. tag v1.0.0-local-mvp-freeze as the first stable local MVP baseline;
3. publish a public local MVP summary;
4. mark pre-v1 releases as historical prototype releases;
5. improve website to show “Local MVP baseline” clearly;
6. prepare external review / audit-ready package;
7. avoid adding new protocol semantics before review;
8. keep token-sale / airdrop / yield / exchange scope frozen;
9. decide whether future work should be testnet design, SDK, or external audit preparation;
10. preserve clear legal and safety boundaries.

---

## 18. Safety Statement

ProofMoney does not offer, sell, or solicit the purchase of PRM.

PRM does not guarantee price, liquidity, yield, profit, or exchange access.

ProofMoney is experimental and may fail.

Test units, if any, have no monetary value.

This report is not an external audit report.

---

## 19. Final Statement

ProofMoney Core v0.9.0-protocol-spec-freeze is not a finished monetary network.

It is a local MVP prototype with documented and frozen local MVP protocol semantics.

If money cannot be verified, it is only a promise.
