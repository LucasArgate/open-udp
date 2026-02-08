# Technical Specification — Open UDP v0.1

**Language**: [🇧🇷 Português](./specification.md) | [🇺🇸 English](#1-overview)

**Namespace:** `usp.delivery`  
**Base:** [Open USP — Specification](https://github.com/LucasArgate/open-usp/blob/main/manifest/specification.en.md)

---

## 1. Overview

This specification defines the behavior of agents and services in the Open UDP (Universal Delivery Protocol), under the namespace `usp.delivery`. UDP is a **protocol in its own right** for the Last Mile delivery domain, compatible with the Open USP ecosystem — not an extension.

Open UDP operates in a **decentralized market (P2P/Broadcast)** model where **Requesters** publish delivery intents and **Providers** respond with bids.

### 1.1 System actors

| Actor | Description |
|-------|-------------|
| **Requester** | Agent that initiates the order (restaurant, e-commerce, consumer). |
| **Provider** | Agent that executes logistics (courier, cyclist, drone). |
| **Observer** | Optional audit/insurance entity (cooperative, insurer). |

### 1.2 Version

**Current version:** 0.1.0

---

## 2. Negotiation flow (The Handshake)

Delivery lifecycle follows **Broadcast → Bid → Award**.

### 2.1 Phase 1: Discovery — `BROADCAST_ORDER`

Requester publishes to the network (via PubSub, DHT or Relay API) the need for transport. Required: `origin`, `destination`, `cargo`, pickup window. Optional: `offer.amount`, `constraints`.

### 2.2 Phase 2: Bidding — `SUBMIT_BID`

Providers in the region receive the broadcast, filter locally, optionally compute risk, and send a signed `BID` with amount, `eta_pickup`, and optional `risk_assessment`.

### 2.3 Phase 3: Award — `AWARD_ORDER`

Requester selects a winner and issues `AWARD_ORDER` with final terms. Contract/escrow may be created as agreed.

---

## 3. Execution and states

After `AWARD_ORDER`, delivery runs through: `ACCEPTED` → `ARRIVED_PICKUP` → `IN_TRANSIT` → `ARRIVED_DROPOFF` → `DELIVERED`. Optional: `CANCELLED`, `FROZEN` (on incident). Critical transitions `IN_TRANSIT` and `DELIVERED` require proof when required by contract (see [security.md](./security.md)).

---

## 4. Exceptions

- **REPORT_INCIDENT:** Provider reports accident, crime, or breakdown; state may become `FROZEN`; reputation not negatively affected; proportional payment per contract/insurance.
- **Excessive delay:** Requester may cancel without penalty and re-broadcast per contract.
- **Cancelation rules:** Defined in [contracts.md](./contracts.md).

---

## 5. Extensibility

Extensions via `meta` (e.g. `meta.delivery.thermal_bag_required`). See [extensions.md](./extensions.md).

---

## 6. References

- [Open USP — Specification (EN)](https://github.com/LucasArgate/open-usp/blob/main/manifest/specification.en.md)
- [Open UDP — Security](./security.md)
- [Open UDP — Messages](./messages.md)
- [Open UDP — Contracts](./contracts.md)

---

**Version:** 0.1.0  
**Last update:** February 2026
