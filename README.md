# Open UDP — Universal Delivery Protocol

[![License](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)
[![Status](https://img.shields.io/badge/status-v0-green.svg)](https://github.com/LucasArgate/open-udp)
[![Protocol](https://img.shields.io/badge/protocol-Open%20Protocol-blue)](https://github.com/LucasArgate/open-usp)
[![Namespace](https://img.shields.io/badge/namespace-u.delivery-blue)](./manifest/)

**Language**: [🇧🇷 Português](#-sobre-o-projeto) | [🇺🇸 English](#-about-the-project)

---

## 📋 Sobre o Projeto

**Open UDP (Universal Delivery Protocol)** é um **protocolo aberto** para logística **Last Mile** e economia de serviços de delivery. Opera no namespace `u.delivery` e é compatível com o ecossistema [Open USP (Universal Service Protocol)](https://github.com/LucasArgate/open-usp). Na tendência em que Google e big techs investem em protocolos como o UCP (Universal Commerce Protocol), o futuro é mais protocolos que aplicações — o UDP é um deles.

Enquanto o USP define *como* pedir um serviço, o UDP define *como* esse serviço se move fisicamente de A para B com **segurança**, **justiça** e **eficiência** — em ambiente aberto e auditável.

> **Posicionamento:** O Open UDP é para a entrega o que o HTTP foi para a web: a **infraestrutura de base** que permite que a concorrência aconteça no serviço, não na conexão. Não é um concorrente de plataformas; é o padrão que desbloqueia interoperabilidade e reduz risco regulatório e operacional.

> 🤖 **Ascensão agêntica:** com o [WebMCP](https://developer.chrome.com/blog/ai-webmcp-origin-trial) (origin trial no Chrome 149, jun/2026) a web passou a **declarar ferramentas** para agentes em vez de deixá-los adivinhar a interface. O UDP é o equivalente disso para o Last Mile: o agente pessoal do entregador (um **Mobolt**, o novo OpenClaw) invoca contratos claros (broadcast/BID/AWARD) em vez de raspar telas. Ver [A Web Vai Falar com Agentes](https://www.linkedin.com/pulse/web-vai-falar-com-agentes-o-que-webmcp-muda-para-quem-lucas-argate-vzzif/).

### Princípios de fundação

1. **Desacoplamento:** Venda (Restaurante) e Logística (Entregador) são entidades que negociam livremente via broadcast e lances (BID).
2. **Safety-by-Design:** Risco físico (clima, área, horário) é variável explícita do protocolo — precificada e monitorada.
3. **Agentes autônomos:** O entregador atua via Agente Pessoal que analisa ofertas, calcula risco e decide dar lance ou recusar, sem punição obscura.
4. **Identidade portável:** Reputação e histórico pertencem ao trabalhador (DID), não à plataforma.
5. **Processo dual (S1/S2):** O agente decide em dois ritmos — S1 (pensar rápido: reflexo de lance e segurança na borda) e S2 (pensar devagar: deliberação, rota, reputação). Segurança nunca espera análise.

## 🎯 Objetivos

- **Padronização Last Mile:** Definir contrato e mensagens para descoberta, negociação (BID/AWARD) e execução de entregas.
- **Interoperabilidade:** Permitir que múltiplas plataformas e infraestruturas (lockers, robôs) conversem via mesmo protocolo.
- **Redução de risco regulatório:** Transparência algorítmica e relação marketplace (não empregatícia) como desenho do sistema.
- **Extensibilidade:** Suportar Risk Premium, Proof of Delivery, Kill Switch e extensões de domínio (thermal, handoff, micro-seguro).

## 📚 Documentação

Toda a especificação está em [`manifest/`](./manifest/):

### Visão e negócio

- [Abstract](./manifest/ABSTRACT.md) — Manifesto fundador (PT)
- [Abstract](./manifest/ABSTRACT.en.md) — Founding manifesto (EN)
- [Visão: agente pessoal do entregador](./manifest/VISAO_AGENTE_PESSOAL_ENTREGADOR.md) — Motoboy, Mobolt (o novo OpenClaw), WebMCP, necessidades vitais e tendência agêntica
- [Executive Summary](./manifest/EXECUTIVE_SUMMARY.md) — Operational resilience & legal de-risking (CEOs)

### Especificações técnicas

- [Manifest (visão geral)](./manifest/README.md) — Arquitetura e índice
- [Especificação técnica](./manifest/specification.md) — Fluxo Broadcast–Bid–Award, estados, exceções
- [Contratos](./manifest/contracts.md) — Requester, Provider, Observer; termos e obrigações
- [Mensagens](./manifest/messages.md) — Payloads JSON `u.delivery`
- [Segurança](./manifest/security.md) — Safety-by-Design, Kill Switch, Proof of Delivery
- [Extensões](./manifest/extensions.md) — Meta, Risk Premium, handoff, roadmap

## 📁 Estrutura do Projeto

```
open-udp/
├── manifest/              # Especificação e documentação do protocolo
│   ├── README.md          # Visão geral do manifesto
│   ├── ABSTRACT.md        # Manifesto fundador (PT)
│   ├── ABSTRACT.en.md     # Founding manifesto (EN)
│   ├── EXECUTIVE_SUMMARY.md
│   ├── specification.md
│   ├── contracts.md
│   ├── messages.md
│   ├── security.md
│   └── extensions.md
├── examples/              # Exemplos de implementação (futuro)
│   ├── basic/
│   └── README.md
├── LICENSE
├── REPO_DESCRIPTION.md    # Descrição para GitHub (até 350 caracteres)
└── README.md
```

## 🤝 Contribuindo

1. Leia o [manifest/README.md](./manifest/README.md) e a [especificação](./manifest/specification.md).
2. Abra issues e PRs para melhorias de texto, schemas ou novos casos de uso.
3. Respeite o namespace `u.delivery` e a compatibilidade com [Open USP](https://github.com/LucasArgate/open-usp).

## 📄 Licença

Este projeto está sob a licença MIT. Veja [LICENSE](./LICENSE).

## 👤 Autor

**Lucas Argate** — [GitHub](https://github.com/lucasargate)

---

## 🌐 About the Project

**Open UDP (Universal Delivery Protocol)** is an **open protocol** for **Last Mile** logistics and the delivery service economy. It operates under the namespace `u.delivery` and is compatible with the [Open USP (Universal Service Protocol)](https://github.com/LucasArgate/open-usp) ecosystem. As Google and big techs invest in protocols like UCP (Universal Commerce Protocol), the trend is toward more protocols than applications — UDP is one of them.

While USP defines *how* to request a service, UDP defines *how* that service physically moves from A to B with **safety**, **fairness**, and **efficiency** — in an open, auditable environment.

> **Positioning:** Open UDP is to delivery what HTTP is to the web: the **base infrastructure** that lets competition happen on service, not on connection. It is not a competitor to platforms; it is the standard that unlocks interoperability and reduces regulatory and operational risk.

> 🤖 **The agentic rise:** with [WebMCP](https://developer.chrome.com/blog/ai-webmcp-origin-trial) (origin trial in Chrome 149, Jun 2026) the web began to **declare tools** for agents instead of letting them guess the interface. UDP is the Last Mile equivalent: the courier's personal agent (a **Mobolt**, the new OpenClaw) invokes clear contracts (broadcast/BID/AWARD) instead of scraping screens.

### Founding principles

1. **Decoupling:** Sales (Restaurant) and Logistics (Courier) are entities that negotiate freely via broadcast and bids (BID).
2. **Safety-by-Design:** Physical risk (weather, area, time) is an explicit variable of the protocol — priced and monitored.
3. **Autonomous agents:** The courier acts through a Personal Agent that analyzes offers, computes risk, and decides to bid or decline, without obscure penalties.
4. **Portable identity:** Reputation and history belong to the worker (DID), not to the platform.
5. **Dual process (S1/S2):** The agent decides at two speeds — S1 (thinking fast: bid and safety reflexes at the edge) and S2 (thinking slow: deliberation, routing, reputation). Safety never waits for analysis.

## 🎯 Goals

- **Last Mile standardization:** Define contract and messages for discovery, negotiation (BID/AWARD), and execution of deliveries.
- **Interoperability:** Allow multiple platforms and infrastructures (lockers, robots) to interoperate via the same protocol.
- **Regulatory risk reduction:** Algorithmic transparency and marketplace (non-employment) relationship as a design goal.
- **Extensibility:** Support Risk Premium, Proof of Delivery, Kill Switch, and domain extensions (thermal, handoff, micro-insurance).

## 📚 Documentation

All specification is in [`manifest/`](./manifest/):

- [Abstract (EN)](./manifest/ABSTRACT.en.md)
- [Executive Summary](./manifest/EXECUTIVE_SUMMARY.md)
- [Manifest overview](./manifest/README.md)
- [Technical specification](./manifest/specification.md)
- [Contracts](./manifest/contracts.md)
- [Messages](./manifest/messages.md)
- [Security](./manifest/security.md)
- [Extensions](./manifest/extensions.md)

## 📄 License

This project is licensed under the MIT License. See [LICENSE](./LICENSE).

**Version:** 0.1.0  
**Last update:** February 2026
