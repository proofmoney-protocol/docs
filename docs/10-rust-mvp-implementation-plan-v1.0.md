# ProofMoney Rust MVP Implementation Plan v1.0

**Version:** v1.0  
**Project:** ProofMoney  
**Initial Author:** Vingen Motoki  
**Implementation Language:** Rust  
**Scope:** Local MVP Prototype  
**Core Statement:** If money cannot be verified, it is only a promise.

---

## 1. MVP Goal

The first Rust MVP should answer one question:

> **Can ProofMoney generate and verify the five core money integrity proofs in a local environment?**

The MVP must support:

- Starting State Proof;
- Proof of Issuance;
- Proof of Supply;
- Proof of Ownership;
- Proof of Flow;
- Proof of Rule;
- Integrity Status CLI;
- Local JSON storage;
- Basic test suite.

The MVP must not include:

- public network;
- PRM sale;
- private allocation;
- trading interface;
- public test unit with market value;
- exchange integration;
- yield product;
- airdrop claim page.

---

## 2. Rust Workspace Structure

```text
core/
├── README.md
├── LICENSE
├── Cargo.toml
├── crates/
│   ├── proofmoney-cli/
│   ├── proofmoney-types/
│   ├── proofmoney-crypto/
│   ├── proofmoney-ledger/
│   ├── proofmoney-release/
│   ├── proofmoney-proof/
│   ├── proofmoney-wallet/
│   └── proofmoney-storage/
├── docs/
└── tests/
```

---

## 3. Crate Responsibilities

| Crate | Purpose |
|---|---|
| `proofmoney-cli` | Command-line interface |
| `proofmoney-types` | Shared domain types |
| `proofmoney-crypto` | Hashing, keys, signatures, addresses |
| `proofmoney-ledger` | Starting State, events, ledger state |
| `proofmoney-release` | Proof Release Curve logic |
| `proofmoney-proof` | Five proof modules |
| `proofmoney-wallet` | Local wallet model |
| `proofmoney-storage` | JSON storage for MVP |

---

## 4. Key Technical Decisions

| Area | Decision |
|---|---|
| Language | Rust |
| CLI | clap |
| Serialization | serde / serde_json |
| Hashing | SHA-256 for MVP |
| Signatures | Ed25519 for MVP |
| Address format | Bech32-style prefix |
| Local prefix | `tprm` |
| Public prefix | `prm` |
| Storage | JSON for MVP |
| Amount model | integer-only, no floating point |

---

## 5. Money Amount Rule

```text
1 PRM = 100,000,000 proof
```

All amounts must use integer units.

No floating-point numbers should be used for monetary amounts.

---

## 6. Required Commands

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

Every verification command should support:

```bash
--json
```

---

## 7. Development Milestones

1. Rust workspace setup
2. Types and amount model
3. Starting State
4. Proof Release Curve
5. Proof of Supply and Issuance
6. Rule verification
7. Wallet and Ownership
8. Flow verification
9. Integrity Status
10. Test suite and MVP report

---

## 8. MVP Limitations

This MVP is a local prototype only.

It is not a public network.  
It does not create PRM with monetary value.  
It does not support production wallet security.  
It does not support public node consensus.  
It does not represent a token sale, investment opportunity, yield product, or future allocation right.

Do not use this software with valuable assets.


---

## Project Safety Notice

ProofMoney does not offer, sell, or solicit the purchase of PRM. PRM does not guarantee price, liquidity, yield, profit, or exchange access. ProofMoney is experimental and may fail. Test units, if any, have no monetary value.
