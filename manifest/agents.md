# Open UDP — Manifest

## Purpose
Specification and documentation of the Universal Delivery Protocol (UDP). Single source of truth for contracts, messages, security, and extensions.

## Context
- **ABSTRACT.md / ABSTRACT.en.md** — Founding manifesto (PT/EN).
- **EXECUTIVE_SUMMARY.md** — For decision-makers: operational resilience, legal de-risking.
- **specification.md / specification.en.md** — Flow (Broadcast–Bid–Award), actors, states, exceptions.
- **contracts.md** — Requester, Provider, Observer; terms and obligations.
- **messages.md** — JSON payloads `usp.delivery` (BROADCAST_ORDER, SUBMIT_BID, AWARD_ORDER, UPDATE_STATUS, REPORT_INCIDENT).
- **security.md** — Safety-by-Design, Kill Switch, Proof of Delivery, privacy.
- **extensions.md** — Meta, Risk Premium, handoff, roadmap.

## Key terms
Requester, Provider, Observer, BROADCAST_ORDER, SUBMIT_BID, AWARD_ORDER, ACCEPTED, ARRIVED_PICKUP, IN_TRANSIT, ARRIVED_DROPOFF, DELIVERED, CANCELLED, FROZEN, usp.delivery.

## Retrieval
Use README.md as index. Prefer specification.md and messages.md for implementation; contracts.md for roles; security.md for safety and incidents.
