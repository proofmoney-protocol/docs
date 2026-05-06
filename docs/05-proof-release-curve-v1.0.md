# ProofMoney Proof Release Curve v1.0

**Version:** v1.0  
**Project:** ProofMoney  
**Initial Author:** Vingen Motoki  
**Native Unit:** PRM  
**Core Statement:** If money cannot be verified, it is only a promise.

---

## 1. Purpose

The Proof Release Curve defines how PRM may enter the ProofMoney system through public, bounded, and verifiable rules.

It is not a fundraising schedule.  
It is not a private allocation plan.  
It is not a yield model.  
It is not a price narrative.  
It is not a promise of future market value.

The purpose of the Proof Release Curve is to ensure that every unit of PRM can be explained by protocol state.

---

## 2. Core Principle

> **Every released unit must have a verifiable origin.**

PRM should not appear because a team says it exists.

PRM should only enter the system through rules that can be checked by independent verification tools.

---

## 3. Release Design Goals

The release model should satisfy:

- verifiable origin;
- bounded supply;
- zero initial privilege;
- public rule enforcement;
- Public Proof Fund transparency;
- long-term security contribution;
- user-readable verification.

---

## 4. Components

The Proof Release Curve contains four major components:

1. Starting State
2. Proof Contributor Rewards
3. Public Proof Fund Allocation
4. Supply Boundary

---

## 5. Starting State

The Starting State should contain:

```text
Initial Supply: 0 PRM
Privileged Allocation: None
Private Sale Allocation: None
Hidden Address Allocation: None
Public Proof Fund Preload: None
```

---

## 6. Proof Contributor Rewards

Proof Contributor Rewards are protocol-defined rewards for participants who provide resources to maintain the Proof Ledger and support verifiable state transitions.

Rewards must be rule-based and verifiable.

---

## 7. Public Proof Fund Allocation

The Public Proof Fund is a transparent protocol-level fund for maintaining ProofMoney’s integrity infrastructure.

For v1.0 discussion, the initial proposed Public Proof Fund allocation is:

```text
Public Proof Fund Allocation: 3% of each valid release event
Proof Contributor Reward: 97% of each valid release event
```

This parameter remains subject to technical review, legal review, and public documentation review before any live network.

---

## 8. Supply Boundary

For v1.0 discussion, the proposed supply boundary is:

```text
Maximum Supply Boundary: 100,000,000 PRM
```

The supply boundary must be:

- public;
- fixed by rule;
- machine-verifiable;
- visible through Proof of Supply;
- resistant to unilateral change;
- included in Proof of Rule;
- rejected if exceeded.

---

## 9. Proposed Release Curve v1.0

Draft parameters:

```text
Maximum Supply Boundary: 100,000,000 PRM
Initial Supply: 0 PRM
Initial Release Event Size: 25 PRM
Release Interval: Protocol-defined state interval
Release Reduction Window: 2,000,000 intervals
Public Proof Fund Allocation: 3%
Proof Contributor Reward: 97%
Starting Protection Window: 20,160 intervals
```

The term **interval** is used instead of binding the model to a specific technical implementation.

---

## 10. Starting Protection Window

Proposed structure:

```text
Intervals 1 - 10,080: 20% of base release
Intervals 10,081 - 20,160: 50% of base release
Intervals 20,161 onward: 100% of base release
```

Unreleased PRM during the Starting Protection Window should not be backfilled.

Principle:

> **Unreleased units should remain unreleased, not reassigned.**

---

## 11. Summary

The Proof Release Curve defines how PRM may enter the ProofMoney system without private monetary privilege.

It exists to make issuance:

- public;
- bounded;
- predictable;
- auditable;
- verifiable.

Every released unit must have a verifiable origin.


---

## Project Safety Notice

ProofMoney does not offer, sell, or solicit the purchase of PRM. PRM does not guarantee price, liquidity, yield, profit, or exchange access. ProofMoney is experimental and may fail. Test units, if any, have no monetary value.
