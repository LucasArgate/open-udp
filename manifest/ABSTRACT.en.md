# Universal Delivery Protocol (UDP)

### *The courier is not an algorithm. They are an autonomous agent with real-life risk.*

**Language**: [🇧🇷 Português](./ABSTRACT.md) | [🇺🇸 English](#1-abstract)

**Namespace:** `usp.delivery` | **Base:** [Open USP](https://github.com/LucasArgate/open-usp)

---

## 1. Abstract

The **Universal Delivery Protocol (UDP)** is an open standard protocol for **Last Mile** logistics — a **protocol in its own right**, not an extension. It operates in the namespace `usp.delivery` and is compatible with the [Open USP (Universal Service Protocol)](https://github.com/LucasArgate/open-usp) ecosystem. As Google and big techs invest in protocols like UCP (Universal Commerce Protocol), the trend is toward more protocols than applications; UDP is one of them. It specifies how **Requesters** (senders) and **Providers** (couriers) discover, negotiate, and execute deliveries in a **decentralized market** model (broadcast + bids), with physical and economic safety at the center of the design.

In the current model (centralized apps), job allocation is a black box. UDP proposes **information as negotiating power**: visible offers, priced risk, refusal without obscure penalties, and portable reputation.

---

## 2. The problem UDP addresses

- **Information asymmetry:** The courier does not know why they got that job at that price; the restaurant does not know why the fee changed; the customer does not see how much actually goes to whoever bears the risk.
- **Invisible risk:** Delivering in certain areas or conditions (weather, time) has a real cost (accident, theft, wear). Today that cost is not negotiated transparently.
- **Platform lock-in:** Reputation and history are tied to one app; switching platforms means losing professional track record.

UDP does not alone solve social inequality; it provides the **technological tools** so that workers and businesses can negotiate and operate with greater dignity and transparency.

---

## 3. Protocol pillars

### I. Real autonomy (Agency)

The courier acts through a **Personal Agent** (on their device). This agent:

- Receives offers from the region (broadcast).
- Computes profitability and risk (weather, area, time).
- Decides to bid (BID) or ignore.

If they ignore, there is no obscure negative score. It is supply and demand.

### II. Safety as an economic variable

The protocol allows **Risk Premium** in the bid, explicitly. The Requester decides whether to accept the price. No one is forced to work in the dark for a price that does not cover the risk.

### III. Portable identity and reputation

Identity and reputation are cryptographically signed (e.g. DID) and **belong to the worker**. Switching aggregators does not mean losing history; reputation can also serve as a basis for credit and financing (Logistics Trust Score).

### IV. Transparency with the human at the center

The protocol encourages displaying a **Fair Trade Breakdown** to the consumer: base value, risk premium, insurance, total to the courier — educating for ethical consumption.

---

## 4. Vision 2026

- **Restaurants** with agents that manage channels and choose own fleet or outsourced dynamically.
- **Couriers** with agents that optimize earnings and safety and automatically decline abusive jobs.
- **Customers** seeing the real cost of logistics and able to choose to pay for fair conditions.
- **Urban infrastructure** (lockers, lobby robots) integrated via Handoff protocol.

---

## 5. Commitment

Open UDP commits to:

- Treating logistics as a **market for negotiation between agents**, removing the algorithmic black box.
- Incorporating **physical and economic safety** of the courier as explicit variables (risk, wait time, insurance, handoff).
- Allowing **collective governance** (e.g. regional mutual funds) for protection when standard insurance does not cover.
- Keeping the protocol **extensible and open**, so that new rules (micro-insurance, return fee, wait-time) can be adopted without breaking the base.

---

## 6. License and governance

UDP is released under the **MIT License**, as an open, community-driven standard. It is a protocol in its own right, compatible with the [Open USP](https://github.com/LucasArgate/open-usp) ecosystem.

---

*We are not building a marketplace. We are building the language that lets marketplaces and agents talk to real logistics. Join us in building the protocol for fair and safe delivery.*

---

**Version:** 0.1.0  
**Last update:** February 2026  
**Português:** [ABSTRACT.md](./ABSTRACT.md)
