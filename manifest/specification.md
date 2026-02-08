# Especificação Técnica — Open UDP v0.1

**Language**: [🇧🇷 Português](#1-visão-geral) | [🇺🇸 English](#1-overview)

**Namespace:** `usp.delivery`  
**Base:** [Open USP — Specification](https://github.com/LucasArgate/open-usp/blob/main/manifest/specification.md)

---

## 1. Visão Geral

Esta especificação define o comportamento de agentes e serviços no protocolo Open UDP (Universal Delivery Protocol), operando sob o namespace `usp.delivery`. O UDP é um **protocolo próprio** para o domínio Last Mile, compatível com o ecossistema Open USP — não uma extensão.

O Open UDP opera em um modelo de **mercado descentralizado (P2P/Broadcast)** em que **Requesters** publicam intenções de entrega e **Providers** respondem com ofertas (Bids).

### 1.1 Atores do sistema

| Ator | Descrição |
|------|-----------|
| **Requester** | Agente que inicia o pedido (restaurante, e-commerce, consumidor). |
| **Provider** | Agente que executa a logística (motoboy, ciclista, drone). |
| **Observer** | Entidade opcional de auditoria/seguro (cooperativa, seguradora). |

### 1.2 Versão

**Versão atual:** 0.1.0

---

## 2. Fluxo de negociação (The Handshake)

O ciclo de vida de uma entrega segue o padrão **Broadcast → Bid → Award**.

### 2.1 Fase 1: Descoberta — `BROADCAST_ORDER`

O Requester emite uma mensagem para a rede (via PubSub, DHT ou API de Relay) anunciando a necessidade de transporte.

- **Campos obrigatórios:** `origin`, `destination`, `cargo` (ou `cargo_type`), `pickup_time` (ou janela em `constraints`).
- **Campos opcionais:** `offer.amount` (preço sugerido), `constraints` (ex.: `must_be_human`).

### 2.2 Fase 2: Análise e lance — `SUBMIT_BID`

Os agentes Provider na região recebem o broadcast.

1. **Filtro local:** O agente verifica se a rota é viável (raio de atuação, bateria/combustível).
2. **Cálculo de risco:** O agente pode consultar APIs de clima e segurança. Se chover ou a área for de risco, o custo pode subir (Risk Premium).
3. **Envio de lance:** Se interessar, o agente envia um `BID` assinado.
   - O BID pode ser maior ou menor que o preço sugerido.
   - O BID inclui `eta_pickup` (tempo estimado até o pickup).

### 2.3 Fase 3: Seleção — `AWARD_ORDER`

O Requester recebe múltiplos BIDs.

1. **Ranking:** Ordena por preço, reputação ou tempo (critério do Requester).
2. **Seleção:** Escolhe um vencedor e emite `AWARD_ORDER`.
3. **Contrato:** Termos finais e, quando aplicável, smart contract ou ledger de confiança com os termos acordados.

---

## 3. Execução e estados

Após o `AWARD_ORDER`, a entrega entra em execução com os seguintes estados:

| Estado | Descrição |
|--------|-----------|
| `ACCEPTED` | Provider aceitou e está a caminho do pickup. |
| `ARRIVED_PICKUP` | Provider chegou no ponto de retirada. |
| `IN_TRANSIT` | Provider pegou o pedido (prova: scan QR ou assinatura). |
| `ARRIVED_DROPOFF` | Provider chegou no destino. |
| `DELIVERED` | Cliente recebeu (prova: scan QR ou assinatura). |
| `CANCELLED` | Cancelado por uma das partes (com penalidade, salvo força maior). |
| `FROZEN` | Incidente reportado; entrega pausada para tratamento. |

### 3.1 Transições com prova

Para evitar fraude, as transições críticas **IN_TRANSIT** e **DELIVERED** devem ser acompanhadas de prova criptográfica (assinatura do restaurante/cliente ou scan de token físico), conforme [security.md](./security.md).

---

## 4. Tratamento de exceções

### 4.1 Incidentes (Safety)

Se o Provider reportar `REPORT_INCIDENT` (acidente, crime, pane), o estado pode mudar para `FROZEN`.

- A reputação do Provider não é afetada negativamente por incidente legítimo.
- O pagamento proporcional ao trajeto percorrido deve ser garantido quando houver seguro ou termos acordados.

### 4.2 Atraso excessivo

Se o Provider exceder o ETA acordado em um percentual definido no contrato, o Requester pode cancelar sem multa e reabrir o broadcast.

### 4.3 Cancelamento

Regras de cancelamento e penalidades ficam definidas no contrato (ver [contracts.md](./contracts.md)); o protocolo não impõe um único modelo.

---

## 5. Extensibilidade

O protocolo permite extensões via campo `meta`, por exemplo:

- `meta.delivery.thermal_bag_required`: boolean
- `meta.payment.credit_card_machine`: boolean
- `meta.delivery.handoff_supported`: boolean

Detalhes em [extensions.md](./extensions.md).

---

## 6. Referências

- [Open USP — Especificação](https://github.com/LucasArgate/open-usp/blob/main/manifest/specification.md)
- [Open UDP — Segurança](./security.md)
- [Open UDP — Mensagens](./messages.md)
- [Open UDP — Contratos](./contracts.md)

---

**Versão:** 0.1.0  
**Última atualização:** Fevereiro 2026
