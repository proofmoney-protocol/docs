# ProofMoney Docs

**ProofMoney** is an open protocol initiative for **verifiable money integrity**.

Core statement:

> **If money cannot be verified, it is only a promise.**

ProofMoney explores how monetary systems can make issuance, supply, ownership, flow, and rules independently verifiable.

This repository contains the public documentation for the ProofMoney protocol design.

---

## What is ProofMoney?

ProofMoney is a protocol design focused on replacing monetary promises with verifiable proofs.

It is built around five core proofs:

1. **Proof of Issuance** — verifies how each unit enters the system.
2. **Proof of Supply** — verifies current and historical supply.
3. **Proof of Ownership** — verifies who controls value.
4. **Proof of Flow** — verifies how value moves.
5. **Proof of Rule** — verifies which rules are enforced.

Together, these proofs form the foundation of the **ProofMoney Integrity Stack**.

---

## ProofMoney Integrity Stack

ProofMoney is designed as a money integrity stack:

- **Proof Ledger** — the verifiable monetary state layer.
- **Proof Engine** — the verification logic for the five core proofs.
- **Proof Wallet** — a wallet that shows the proof behind the balance.
- **Proof Explorer** — a public interface for inspecting system integrity.
- **Proof Vault** — a multi-signature and auditable fund control layer.
- **Proof API** — developer access to money integrity proofs.

**Verification is the product.**

---

## Current Status

ProofMoney is currently in the **principles, documentation, and prototype design stage**.

At this stage:

- no PRM is being sold;
- no public network is live;
- no test unit has monetary value;
- no exchange listing is promised;
- no yield is promised;
- no private allocation is recognized;
- no test-to-main conversion is promised.

ProofMoney should be treated as an experimental open protocol design.

---

## Core MVP Prototype

ProofMoney Core v0.3.0-ownership-and-flow is now available.

Core repository:

https://github.com/proofmoney-protocol/core

The current Core MVP is a local Rust prototype. It includes a Cargo workspace, CLI commands, Starting State Proof, Proof Release Curve simulation, deterministic event hashing, local ledger JSON persistence, release event append flow, computed supply verification, local wallet persistence, address inspection, message signing, transfer event creation, local balance tracking, insufficient balance rejection, stronger Proof of Flow, Proof of Rule, Proof of Ownership, and GitHub Actions CI.

Read the Core MVP reports:

- [ProofMoney Core MVP Report v0.1.0-alpha](./docs/12-core-mvp-report-v0.1.0-alpha.md)
- [ProofMoney Core MVP Report v0.2.0-local-ledger](./docs/13-core-mvp-report-v0.2.0-local-ledger.md)
- [ProofMoney Core MVP Report v0.3.0-ownership-and-flow](./docs/14-core-mvp-report-v0.3.0-ownership-and-flow.md)

This prototype is experimental. It is not a public network, PRM sale, yield product, airdrop claim, exchange integration, or production wallet.

---

## Native Unit: PRM

PRM is the proposed native unit of the ProofMoney protocol.

PRM does **not** represent:

- equity;
- debt;
- profit share;
- guaranteed yield;
- ownership of any company;
- redemption rights;
- guaranteed liquidity;
- guaranteed market access.

The legitimacy of PRM, if implemented, must come from verifiable protocol rules, not promotional promises.

---

## Zero-Privilege Launch

ProofMoney follows a **Zero-Privilege Launch** principle:

- no initial founder allocation;
- no private sale;
- no insider round;
- no hidden address;
- no guaranteed yield;
- no test-unit conversion promise;
- no unilateral rule privilege.

ProofMoney does not ask users to trust that the launch is clean.

It must let them verify it.

---

## Documentation

| Document | Description |
|---|---|
| [Project Principles](./docs/00-project-principles-v1.0.md) | Defines the highest-level principles of ProofMoney. |
| [Manifesto](./docs/01-manifesto-v1.0.md) | Explains the mission and philosophy of ProofMoney. |
| [Whitepaper](./docs/02-whitepaper-v1.0.md) | Describes the protocol concept and money integrity model. |
| [Integrity Stack](./docs/03-integrity-stack-v1.0.md) | Defines Proof Ledger, Proof Engine, Proof Wallet, Proof Explorer, Proof Vault, and Proof API. |
| [Zero-Privilege Launch](./docs/04-zero-privilege-launch-v1.0.md) | Defines the launch constraints and no-privilege rules. |
| [Proof Release Curve](./docs/05-proof-release-curve-v1.0.md) | Describes how PRM may enter the system through public and verifiable rules. |
| [Risk Disclosure](./docs/06-risk-disclosure-v1.0.md) | Explains technical, economic, legal, market, and user risks. |
| [Forbidden Activities](./docs/07-forbidden-activities-v1.0.md) | Defines activities not permitted or endorsed by ProofMoney. |
| [MVP Roadmap](./docs/08-mvp-roadmap-v1.0.md) | Describes the prototype development plan. |
| [Repository Structure](./docs/09-repository-structure-v1.0.md) | Describes the planned GitHub repository structure. |
| [Rust MVP Implementation Plan](./docs/10-rust-mvp-implementation-plan-v1.0.md) | Defines the Rust local MVP direction. |
| [Release Integrity Report Template](./docs/11-release-integrity-report-template-v1.0.md) | Template for future release integrity reporting. |

---

## Important Risk Notice

ProofMoney is experimental.

PRM may never have market value.  
PRM may have no liquidity.  
ProofMoney software may contain bugs.  
Private keys may be lost or stolen.  
Transactions may be irreversible.  
Test units have no monetary value.  
Third-party services may be unsafe.  
Regulatory treatment is uncertain.  
The protocol may fail.

Read the full [Risk Disclosure](./docs/06-risk-disclosure-v1.0.md) before interacting with any ProofMoney software, documentation, test environment, or related infrastructure.

---

## No PRM Sale

ProofMoney does not offer, sell, or solicit the purchase of PRM.

There is no official:

- private sale;
- public sale;
- pre-sale;
- whitelist sale;
- advisor allocation;
- influencer allocation;
- exchange allocation;
- guaranteed conversion;
- yield program;
- fundraising sale.

Any claim that official PRM is currently for sale should be treated as unauthorized and suspicious.

---

## Test Units Have No Value

Any ProofMoney test environment is for testing only.

Test units:

- have no monetary value;
- are not PRM;
- are not redeemable for PRM;
- do not create future allocation rights;
- should not be bought or sold;
- may be reset, deleted, or invalidated at any time.

Testing is for improving protocol integrity, not for creating financial expectations.

---

## Author

Initial design authored by **Vingen Motoki**.

The protocol is intended to outgrow its initial author.

---

## Final Statement

ProofMoney is not built on financial promises.

It is built on the belief that monetary claims should be verifiable.

If money cannot be verified, it is only a promise.

**Money should be proven, not promised.**
