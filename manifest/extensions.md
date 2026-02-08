# Extensões — Open UDP v0.1

**Namespace:** `usp.delivery`

O protocolo Open UDP é extensível por design. Este documento descreve o mecanismo de extensão e exemplos previstos para versões futuras, sem quebrar a base v0.1.

---

## 1. Mecanismo de extensão

- **Campo `meta`:** Mensagens podem incluir um objeto `meta` com chaves namespaced (ex.: `meta.delivery.*`, `meta.payment.*`). Implementações que não reconhecem uma chave devem ignorá-la ou repassá-la opaquamente.
- **Novos tipos de mensagem:** Extensões podem definir novos `type` (ex.: para handoff, micro-seguro). Implementações base não são obrigadas a processá-los.
- **Novos valores em enums:** Campos como `incident_type`, `cargo.type` ou `address_type` podem ganhar novos valores em extensões; implementações devem tolerar valores desconhecidos (ignorar ou repassar).

---

## 2. Extensões previstas (roadmap)

### 2.1 Já suportados na base (v0.1)

- **Risk Premium:** Inclusão de `risk_assessment` e valor diferenciado no `SUBMIT_BID`.
- **Proof of Delivery:** Campo `proof` em `UPDATE_STATUS` para IN_TRANSIT e DELIVERED.
- **Meta genérico:** Ex.: `meta.delivery.thermal_bag_required`, `meta.payment.credit_card_machine`.

### 2.2 Planejados para versões futuras

| Extensão | Descrição breve |
|----------|-----------------|
| **Wait-time / estada** | Taxa de espera no pickup: se o Provider reportar ARRIVED_PICKUP e o Requester não validar IN_TRANSIT em X minutos, valor sobe por minuto (contrato). |
| **Micro-seguro por corrida** | BID pode incluir referência a agente de seguro; fração do valor vai para pool de cobertura; REPORT_INCIDENT pode acionar sinistro automático. |
| **Return fee / dead leg** | Custo de "volta" quando o destino é zona de baixa demanda; o Provider pode incluir no BID. |
| **Handoff (usp.delivery.handoff)** | Protocolo para entregador ↔ locker/robô de portaria (depositar pedido e finalizar entrega sem subir ao andar). |
| **Fair Trade Breakdown** | Schema opcional para exibir ao cliente: valor base, prêmio de risco, seguro, total para o entregador. |
| **Governança / fundo mútuo** | Pequena taxa por transação para fundo por região (ex.: DAO de entregadores) para casos não cobertos pelo seguro padrão. |

---

## 3. Convenção de nomes para `meta`

- `meta.delivery.*` — Restrições ou capacidades de entrega (thermal, handoff, etc.).
- `meta.payment.*` — Formas de pagamento ou instrumentos (maquininha, tip, etc.).
- `meta.insurance.*` — Seguro ou pool associado à corrida.
- `meta.wait_time.*` — Regras de tempo de espera no pickup.

Implementações que não suportam uma chave devem ignorá-la sem falha.

---

## 4. Referências

- [Open USP — Extensions](https://github.com/LucasArgate/open-usp/blob/main/manifest/extensions.md)
- [Open UDP — Specification](./specification.md)
- [Open UDP — Messages](./messages.md)

---

**Versão:** 0.1.0  
**Última atualização:** Fevereiro 2026
