# Universal Delivery Protocol (UDP)

### *O entregador não é um algoritmo. É um agente autônomo com risco de vida.*

**Language**: [🇧🇷 Português](#1-resumo) | [🇺🇸 English](./ABSTRACT.en.md)

**Namespace:** `u.delivery` | **Base:** [Open USP](https://github.com/LucasArgate/open-usp)

---

## 1. Resumo

O **Universal Delivery Protocol (UDP)** é um padrão aberto de protocolo para logística **Last Mile** — um **protocolo em si**, não uma extensão. Opera no namespace `u.delivery` e é a **esfera de entrega física** (um hólon autossuficiente e interdependente) da holarquia universal `u.*`, construído **sobre** o [Open USP (Universal Service Protocol)](https://github.com/LucasArgate/open-usp) (`u.service`) como base — suas mensagens de negociação trafegam pelo transporte do USP. O UDP move **átomos** (objetos do mundo real de A→B), não bytes; é a ponte físico-digital entre as esferas. Na tendência em que Google e big techs investem em protocolos como o UCP (Universal Commerce Protocol), o futuro é mais protocolos que aplicações; o UDP posiciona-se como um deles. Ele especifica como **Requesters** (quem precisa enviar) e **Providers** (quem entrega) descobrem, negociam e executam entregas em um modelo de **mercado descentralizado** (broadcast + lances), com segurança física e econômica no centro do desenho.

No modelo atual (apps centralizados), a alocação de corridas é uma caixa preta. O UDP propõe **informação como poder de negociação**: ofertas visíveis, risco precificado, recusa sem punição obscura e reputação portável.

---

## 2. O problema que o UDP endereça

- **Assimetria de informação:** O entregador não sabe por que recebeu aquela corrida por aquele valor; o restaurante não sabe por que a taxa mudou; o cliente não vê quanto vai de fato para quem corre o risco.
- **Risco invisível:** Entregar em certas áreas ou condições (clima, horário) tem custo real (acidente, assalto, desgaste). Hoje esse custo não é negociado de forma transparente.
- **Dependência da plataforma:** Reputação e histórico ficam presos a um app; mudar de plataforma significa perder lastro profissional.

O UDP não resolve sozinho a desigualdade social; fornece as **ferramentas tecnológicas** para que trabalhadores e negócios negociem e operem com mais dignidade e transparência.

---

## 3. Pilares do protocolo

### I. Autonomia real (Agency)

O entregador atua via **Agente Pessoal** (no seu dispositivo). Esse agente:

- Recebe ofertas da região (broadcast).
- Calcula lucratividade e risco (clima, área, horário).
- Decide dar lance (BID) ou ignorar.

Se ignorar, não há score negativo obscuro. É oferta e demanda.

Esse agente decide em **dois ritmos** (processo dual, inspirado em Kahneman): **S1 — pensar rápido** (reflexo na borda: lance/recusa em segundos e reações de segurança na rua) e **S2 — pensar devagar** (deliberação: comparar ofertas, otimizar rota, reputação, governança). A segurança (S1) nunca espera a análise (S2). Detalhe técnico em [specification.md §3](./specification.md#3-processo-dual-s1s2-pensar-rápido-e-devagar).

### II. Segurança como variável econômica

O protocolo permite **Risk Premium** (prêmio de risco) no lance, de forma explícita. O Requester decide se aceita pagar. Ninguém é forçado a trabalhar no escuro por um preço que não cobre o risco.

### III. Identidade e reputação portáveis

Identidade e reputação são assinadas criptograficamente (ex.: DID) e **pertencem ao trabalhador**. Trocar de agregador não significa perder histórico; a reputação pode servir ainda como base para crédito e financiamento (Score de Confiabilidade Logística).

### IV. Transparência para o humano no centro

O protocolo incentiva a exibição de um **Fair Trade Breakdown** para o consumidor: valor base, prêmio de risco, seguro, total para o entregador — educando para consumo ético.

---

## 4. Visão 2026

- **Restaurantes** com agentes que gerenciam canais e escolhem frota própria ou terceirizada de forma dinâmica.
- **Entregadores** com agentes pessoais (moltbot/clawdbot) que otimizam ganho e segurança, recusam automaticamente corridas abusivas e, na mesma base de identidade e protocolo, ajudam em necessidades vitais (compras, manutenção). Ver [Visão: agente pessoal do entregador](./VISAO_AGENTE_PESSOAL_ENTREGADOR.md).
- **Clientes** vendo o custo real da logística e podendo escolher pagar por condições justas.
- **Infraestrutura urbana** (lockers, robôs de portaria) integrada via protocolo de Handoff.

---

## 5. Compromisso

O Open UDP compromete-se a:

- Tratar a logística como **mercado de negociação entre agentes**, removendo a caixa preta algorítmica.
- Incorporar **segurança física e econômica** do entregador como variáveis explícitas (risco, espera, seguro, handoff).
- Permitir **governança coletiva** (ex.: fundos mútuos por região) para proteção quando o seguro padrão não cobrir.
- Manter o protocolo **extensível e aberto**, para que novas regras (micro-seguro, return fee, wait-time) possam ser adotadas sem quebrar a base.

---

## 6. Licença e governança

O UDP é lançado sob **licença MIT**, como padrão aberto e dirigido pela comunidade. É um protocolo próprio, compatível com o ecossistema [Open USP](https://github.com/LucasArgate/open-usp).

---

*Não estamos construindo um marketplace. Estamos construindo a linguagem que permite que marketplaces e agentes conversem com a logística real. Junte-se a nós na construção do protocolo da entrega justa e segura.*

---

**Versão:** 0.1.0  
**Última atualização:** Fevereiro 2026  
**English:** [ABSTRACT.en.md](./ABSTRACT.en.md)
