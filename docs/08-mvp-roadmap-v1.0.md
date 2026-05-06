# ProofMoney MVP Roadmap v1.0

**Version:** v1.0  
**Project:** ProofMoney  
**Initial Author:** Vingen Motoki  
**Implementation Language:** Rust  
**Stage:** MVP planning  
**Core Statement:** If money cannot be verified, it is only a promise.

---

## 1. Purpose

This roadmap defines the first minimum viable prototype for ProofMoney.

The goal of the MVP is not to launch a public network.

The goal is not to sell PRM.

The goal is not to create a trading market.

The goal of the MVP is to answer one question:

> **Can ProofMoney generate and verify the five core proofs in a local prototype environment?**

---

## 2. MVP Definition

The ProofMoney MVP is a local prototype of the ProofMoney Integrity Stack.

It should include:

- a local Proof Ledger;
- a basic Proof Engine;
- a command-line verification interface;
- a simple local wallet model;
- sample state transitions;
- proof outputs in machine-readable and human-readable formats;
- basic tests for the five core proofs.

---

## 3. In Scope

The MVP includes:

- Starting State generation;
- Proof of Issuance;
- Proof of Supply;
- Proof of Ownership;
- Proof of Flow;
- Proof of Rule;
- local state storage;
- local transaction model;
- local key generation;
- local signing and verification;
- Proof Release Curve simulation;
- command-line verification commands;
- basic test cases;
- documentation.

---

## 4. Out of Scope

The MVP does not include:

- public main network;
- public test environment with market expectations;
- PRM sale;
- private allocation;
- exchange integration;
- mobile wallet;
- hardware wallet support;
- public fund governance UI;
- real custody services;
- staking or yield products;
- trading functions;
- smart contract platform;
- cross-chain bridges;
- token launch page;
- airdrop claim page.

---

## 5. Milestones

| Milestone | Name | Goal |
|---:|---|---|
| M0 | Documentation Baseline | Prepare project documents and repository structure |
| M1 | Starting State | Generate and verify the initial state |
| M2 | Proof Ledger | Store state transitions locally |
| M3 | Proof Release Curve | Simulate valid PRM release events |
| M4 | Proof Engine | Generate five core proof outputs |
| M5 | Local Wallet Model | Generate keys, addresses, signatures, and ownership proof |
| M6 | CLI Verification | Provide user-facing verification commands |
| M7 | Test Suite | Validate proof correctness and failure cases |
| M8 | MVP Report | Publish prototype results and limitations |

---

## 6. Required CLI Commands

```bash
proofmoney starting-state
proofmoney simulate-release --interval 1
proofmoney verify-issuance --event <event_id>
proofmoney verify-supply
proofmoney create-wallet
proofmoney new-address
proofmoney sign-message --message "verify ownership"
proofmoney verify-ownership --address <address> --message <message> --signature <signature>
proofmoney create-transfer --from <address> --to <address> --amount 1.25
proofmoney verify-flow --tx <transaction_id>
proofmoney verify-rule
proofmoney integrity-status
```

---

## 7. MVP Success Criteria

The MVP is successful if it can demonstrate:

- a verifiable Starting State;
- rule-based PRM release simulation;
- computable supply;
- proof-backed ownership;
- valid state transitions;
- rule verification;
- CLI-based verification;
- invalid state rejection;
- test coverage for the five proofs.

The MVP is not successful if it only shows a balance.

A balance is not enough.

The MVP must show the proof behind the balance.

---

## 8. Non-Negotiables

The MVP must not include:

- PRM sale;
- private allocation;
- yield language;
- exchange integration;
- claim page;
- airdrop promise;
- public trading interface;
- main network branding;
- financial return language;
- test-to-main conversion promise.

---

## 9. Summary

The first ProofMoney MVP should be small, local, verifiable, and honest.

It should not pretend to be a finished monetary network.

It should demonstrate one thing clearly:

> **ProofMoney can turn monetary claims into verifiable proof outputs.**


---

## Project Safety Notice

ProofMoney does not offer, sell, or solicit the purchase of PRM. PRM does not guarantee price, liquidity, yield, profit, or exchange access. ProofMoney is experimental and may fail. Test units, if any, have no monetary value.
