# ProofMoney Core MVP Report v0.6.0-external-review

**Version:** v0.6.0-external-review  
**Project:** ProofMoney  
**Repository:** https://github.com/proofmoney-protocol/core  
**Website:** https://proofmoney.org  
**Initial Author:** Vingen Motoki  
**Status:** External review preparation release  
**Core Statement:** If money cannot be verified, it is only a promise.

---

## 1. Purpose

This report records the sixth ProofMoney Core MVP milestone.

The purpose of v0.6.0-external-review is to prepare the repository for external Rust, architecture, and security review.

This milestone focuses on:

- freezing MVP scope;
- documenting review boundaries;
- recording self-review notes;
- clarifying known risks;
- preparing a developer announcement draft;
- ensuring no promotional financial language is introduced;
- keeping the MVP reviewable and stable.

This milestone does not claim that ProofMoney has been audited.

This milestone does not claim production readiness.

---

## 2. Current Status

ProofMoney Core v0.6.0-external-review is a local Rust MVP prototype prepared for external review.

It includes:

- MVP scope freeze;
- external review index;
- amount model review notes;
- event hashing and ledger state transition review notes;
- wallet and ownership risk review notes;
- Proof of Flow and balance validation review notes;
- proof export and local explorer review notes;
- public developer announcement draft;
- CI verification.

At this stage:

- no public network is live;
- no public hosted API is live;
- no PRM is being sold;
- no test unit has monetary value;
- no exchange listing is promised;
- no yield is promised;
- no airdrop or claim page exists;
- no test-to-main conversion is promised;
- no audit has been completed.

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

## 4. Implemented in v0.6.0-external-review

This milestone implements:

| Area | Status |
|---|---|
| MVP scope freeze | Implemented |
| External review index | Implemented |
| Amount model review notes | Implemented |
| Event hashing and ledger transition review notes | Implemented |
| Wallet and ownership risk review notes | Implemented |
| Proof of Flow and balance validation review notes | Implemented |
| Proof export and local explorer review notes | Implemented |
| Public developer announcement draft | Implemented |
| README external review status update | Implemented |

---

## 5. MVP Scope Freeze

The MVP scope freeze is located at:

```text
docs/mvp-scope-freeze.md
```

It defines:

- what is currently in scope;
- what is explicitly out of scope;
- what should not change during external review;
- which areas reviewers should focus on.

The freeze explicitly excludes:

- public network;
- public consensus;
- token sale;
- presale;
- private allocation;
- airdrop claim;
- yield product;
- exchange integration;
- price charts;
- trading interface;
- hosted public API;
- public production explorer;
- production wallet security;
- completed external audit.

---

## 6. External Review Index

The external review index is located at:

```text
docs/external-review-index.md
```

It collects the main review documents:

- MVP Scope Freeze;
- Security Review Scope;
- Architecture Overview;
- Developer Quickstart;
- Contributor Guide;
- Amount Model Review Notes;
- Event Hashing and Ledger Review Notes;
- Wallet and Ownership Risk Review Notes;
- Proof of Flow and Balance Review Notes;
- Proof Export and Explorer Review Notes;
- Public Developer Announcement Draft.

---

## 7. Amount Model Review

The amount model review notes are located at:

```text
docs/review-amount-model.md
```

The review focuses on:

- smallest unit definition;
- `1 PRM = 100,000,000 proof`;
- decimal parsing;
- overflow checks;
- invalid amount rejection;
- zero amount behavior;
- maximum supply boundary.

The review does not certify monetary correctness or production readiness.

---

## 8. Event Hashing and Ledger Review

The event hashing and ledger transition review notes are located at:

```text
docs/review-event-hashing-ledger.md
```

The review focuses on:

- event hash view;
- exclusion of mutable `hash` field;
- hash determinism;
- release event append logic;
- transfer event append logic;
- current height update;
- current supply recomputation;
- Public Proof Fund recomputation;
- local balance recomputation.

This review covers local MVP behavior only, not public consensus.

---

## 9. Wallet and Ownership Risk Review

The wallet and ownership risk review notes are located at:

```text
docs/review-wallet-ownership-risk.md
```

The review focuses on:

- local wallet file storage;
- private key exposure risk;
- overwrite behavior;
- address derivation;
- signing message consistency;
- signature verification;
- ownership proof output;
- safety warning clarity.

The MVP wallet remains experimental and must not be used with valuable assets.

---

## 10. Proof of Flow and Balance Review

The Proof of Flow and balance validation review notes are located at:

```text
docs/review-proof-of-flow-balance.md
```

The review focuses on:

- transfer event model;
- sender and receiver address validation;
- amount greater than zero;
- signature presence;
- signature verification;
- sender balance sufficiency;
- insufficient balance rejection;
- event hash validation;
- local double-application risk.

Proof of Flow remains local MVP validation and does not imply public settlement finality.

---

## 11. Proof Export and Explorer Review

The proof export and local explorer review notes are located at:

```text
docs/review-proof-export-explorer.md
```

The review focuses on:

- proof snapshot fields;
- starting state export;
- ledger status export;
- supply proof export;
- rule proof export;
- release event listing;
- transfer event listing;
- static explorer safety language;
- local-only boundary.

The local explorer is not a public block explorer, hosted API, trading interface, or claim page.

---

## 12. Public Developer Announcement Draft

The public developer announcement draft is located at:

```text
docs/public-developer-announcement-draft.md
```

The draft is prepared for future publication after final review.

It includes:

- project purpose;
- current developer release status;
- what developers can run locally;
- what is not included;
- safety and risk notice;
- GitHub repository links;
- contribution invitation;
- review invitation.

It must not be treated as fundraising, token promotion, exchange promotion, or investment marketing.

---

## 13. CI Verification

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

The CI has passed for the v0.6.0-external-review milestone.

---

## 14. Completed Milestone Scope

The v0.6.0-external-review milestone covers:

1. MVP scope freeze before external review;
2. amount model and decimal parsing review notes;
3. event hashing and ledger state transition review notes;
4. wallet and ownership proof risk review notes;
5. Proof of Flow and balance validation review notes;
6. proof export and local explorer output review notes;
7. public developer announcement draft;
8. v0.6.0 external review report and release notes.

---

## 15. MVP Limitations

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

## 16. Next Engineering Priorities

Recommended next milestone:

```text
v0.7.0-review-response
```

Suggested priorities:

1. collect external review feedback;
2. open review response issues;
3. classify findings by severity;
4. fix high-priority correctness issues;
5. improve tests based on review feedback;
6. update documentation based on reviewer concerns;
7. update safety wording if needed;
8. publish review response log;
9. prepare a cleaner public developer announcement;
10. decide whether to pause feature work until review issues are resolved.

---

## 17. Safety Statement

ProofMoney does not offer, sell, or solicit the purchase of PRM.

PRM does not guarantee price, liquidity, yield, profit, or exchange access.

ProofMoney is experimental and may fail.

Test units, if any, have no monetary value.

This report is not an audit report.

---

## 18. Final Statement

ProofMoney Core v0.6.0-external-review is not a finished monetary network.

It is a local MVP prototype prepared for external review.

It makes the project easier to inspect, question, and challenge before any future public-facing expansion.

If money cannot be verified, it is only a promise.
