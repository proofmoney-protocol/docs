# ProofMoney Repository Structure v1.0

**Version:** v1.0  
**Project:** ProofMoney  
**Initial Author:** Vingen Motoki  
**Purpose:** GitHub organization and repository structure

---

## 1. Current GitHub Organization

```text
proofmoney-protocol
```

Current first repository:

```text
https://github.com/proofmoney-protocol/docs
```

---

## 2. Recommended Repository List

The initial GitHub organization should contain:

```text
proofmoney-protocol/
├── docs
├── website
├── core
├── api
├── explorer
└── wallet
```

Do not create unnecessary repositories at the beginning.

The goal is clarity, not volume.

---

## 3. Repository: docs

Purpose:

The `docs` repository contains all public protocol documents.

It is the source of truth for:

- project principles;
- manifesto;
- whitepaper;
- integrity stack;
- zero-privilege launch;
- proof release curve;
- risk disclosure;
- forbidden activities;
- roadmap;
- contribution rules;
- security policy.

---

## 4. Repository: website

Purpose:

The `website` repository contains the public website.

The website should be informational, not promotional.

It should not include buy buttons, claim buttons, countdown sale timers, price charts, yield promises, exchange links, or private sale forms.

---

## 5. Repository: core

Purpose:

The `core` repository contains the Rust prototype implementation of the Proof Ledger and Proof Engine.

The first version should focus on local prototype development, not a public live network.

---

## 6. Repository: api

Purpose:

The `api` repository contains the Proof API specification and prototype service.

It provides developer access to ProofMoney integrity proofs.

---

## 7. Repository: explorer

Purpose:

The `explorer` repository contains the Proof Explorer.

The Proof Explorer is a public integrity dashboard.

---

## 8. Repository: wallet

Purpose:

The `wallet` repository contains the Proof Wallet prototype.

The wallet should show more than balances.

It should show the proof behind the balance.

---

## 9. Creation Order

1. `docs`
2. `website`
3. `core`
4. `api`
5. `explorer`
6. `wallet`

---

## 10. Repository Disclaimer

Each repository README should include:

```text
ProofMoney does not offer, sell, or solicit the purchase of PRM. PRM does not guarantee price, liquidity, yield, profit, or exchange access. ProofMoney is experimental and may fail. Test units, if any, have no monetary value.
```


---

## Project Safety Notice

ProofMoney does not offer, sell, or solicit the purchase of PRM. PRM does not guarantee price, liquidity, yield, profit, or exchange access. ProofMoney is experimental and may fail. Test units, if any, have no monetary value.
