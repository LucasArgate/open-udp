# Open UDP Manifest — Universal Delivery Protocol

**Language**: [🇧🇷 Português](#-visão-geral) | [🇺🇸 English](#-overview)

**Namespace:** `usp.delivery`  
**Version:** 0.1.0  
**Base protocol:** [Open USP (Universal Service Protocol)](https://github.com/LucasArgate/open-usp)

---

## 📖 Visão Geral

O **Universal Delivery Protocol (UDP)** é um **protocolo aberto** para logística **Last Mile** que opera no namespace `usp.delivery` e é compatível com o ecossistema [Open USP (Universal Service Protocol)](https://github.com/LucasArgate/open-usp). Define como serviços de **entrega Last Mile** são descobertos, negociados e executados entre **Requesters** (quem envia) e **Providers** (quem entrega), com segurança física e econômica como variáveis explícitas do protocolo.

Este manifesto contém a especificação completa: arquitetura (Broadcast–Bid–Award), contratos, mensagens JSON, segurança (Safety-by-Design, Kill Switch, Proof of Delivery) e extensões.

## 🎯 Princípios Fundamentais

1. **Universalidade:** Agnóstico a plataforma e transporte (HTTP, PubSub, DHT, Relay). Contratos e mensagens são o contrato.
2. **Transparência:** Negociação visível e auditável; sem caixa preta algorítmica na alocação de corridas.
3. **Segurança primeiro:** Risco físico e digital tratados no desenho (Risk Premium, REPORT_INCIDENT, PoD).
4. **Extensibilidade:** Campos `meta` e extensões (handoff, micro-seguro, wait-time) sem quebrar a base.

## 📚 Documentação

### Visão e negócio

- [Abstract](./ABSTRACT.md) — Manifesto fundador (PT)
- [Abstract](./ABSTRACT.en.md) — Founding manifesto (EN)
- [Visão: agente pessoal do entregador](./VISAO_AGENTE_PESSOAL_ENTREGADOR.md) — Motoboy, moltbot/clawdbot, necessidades vitais e tendência agêntica
- [Executive Summary](./EXECUTIVE_SUMMARY.md) — Para decisores (CEOs): resiliência operacional e desrisco jurídico

### Especificações técnicas

- [Especificação técnica](./specification.md) — Fluxo, atores, estados, exceções
- [Contratos](./contracts.md) — Requester, Provider, Observer; obrigações
- [Mensagens](./messages.md) — Payloads `usp.delivery`
- [Segurança](./security.md) — Safety-by-Design, Kill Switch, PoD, privacidade
- [Extensões](./extensions.md) — Meta, handoff, roadmap

## 🏗️ Arquitetura em uma frase

**Requester** publica `BROADCAST_ORDER` → **Providers** enviam `SUBMIT_BID` → **Requester** emite `AWARD_ORDER` → execução com `UPDATE_STATUS` e, se necessário, `REPORT_INCIDENT`.

## 🔄 Fluxo resumido

1. **Descoberta:** Requester publica ordem (origem, destino, carga, restrições, oferta base).
2. **Negociação:** Providers avaliam risco e enviam BIDs (valor, ETA, motivo de sobretaxa).
3. **Award:** Requester escolhe vencedor; termos finais e token de pickup são definidos.
4. **Execução:** Estados ACCEPTED → ARRIVED_PICKUP → IN_TRANSIT → ARRIVED_DROPOFF → DELIVERED (com prova quando exigido).
5. **Exceções:** REPORT_INCIDENT (FROZEN), cancelamento por atraso, penalidades conforme contrato.

## 📦 Componentes principais

| Componente   | Descrição |
|-------------|-----------|
| **Requester** | Agente que inicia o pedido (restaurante, e-commerce, consumidor). |
| **Provider**  | Agente que executa a logística (motoboy, ciclista, drone). |
| **Observer**  | Opcional: auditoria, seguro, cooperativa. |
| **Mensagens**  | BROADCAST_ORDER, SUBMIT_BID, AWARD_ORDER, UPDATE_STATUS, REPORT_INCIDENT. |
| **Estados**    | ACCEPTED, ARRIVED_PICKUP, IN_TRANSIT, ARRIVED_DROPOFF, DELIVERED, CANCELLED, FROZEN. |

## 🚀 Próximos passos

- Ler a [Especificação técnica](./specification.md) para implementação.
- Consultar [Mensagens](./messages.md) para integração.
- Usar [Executive Summary](./EXECUTIVE_SUMMARY.md) para apresentação a negócios.

---

## 🌐 Overview

The **Universal Delivery Protocol (UDP)** is an **open protocol** for **Last Mile** logistics that operates in the namespace `usp.delivery` and is compatible with the [Open USP (Universal Service Protocol)](https://github.com/LucasArgate/open-usp) ecosystem. It defines how **Last Mile** delivery services are discovered, negotiated, and executed between **Requesters** (senders) and **Providers** (couriers), with physical and economic safety as explicit protocol variables.

This manifest contains the full specification: architecture (Broadcast–Bid–Award), contracts, JSON messages, security (Safety-by-Design, Kill Switch, Proof of Delivery), and extensions.

## 🎯 Fundamental principles

1. **Universality:** Platform- and transport-agnostic (HTTP, PubSub, DHT, Relay). Contracts and messages are the contract.
2. **Transparency:** Negotiation visible and auditable; no algorithmic black box for job allocation.
3. **Security first:** Physical and digital risk designed in (Risk Premium, REPORT_INCIDENT, PoD).
4. **Extensibility:** `meta` fields and extensions (handoff, micro-insurance, wait-time) without breaking the base.

## 📚 Documentation

- [Abstract (EN)](./ABSTRACT.en.md)
- [Executive Summary](./EXECUTIVE_SUMMARY.md)
- [Technical specification](./specification.md)
- [Contracts](./contracts.md)
- [Messages](./messages.md)
- [Security](./security.md)
- [Extensions](./extensions.md)

## 🏗️ Architecture in one sentence

**Requester** publishes `BROADCAST_ORDER` → **Providers** send `SUBMIT_BID` → **Requester** issues `AWARD_ORDER` → execution with `UPDATE_STATUS` and, if needed, `REPORT_INCIDENT`.

---

**Version:** 0.1.0  
**Last update:** February 2026
