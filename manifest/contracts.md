# Contratos — Open UDP v0.1

**Namespace:** `usp.delivery`

Este documento define as obrigações e expectativas dos atores do protocolo Open UDP, sem substituir contratos jurídicos específicos entre partes.

---

## 1. Requester (Quem envia)

### 1.1 Responsabilidades

- Publicar `BROADCAST_ORDER` com dados corretos de origem, destino, carga e restrições.
- Definir janela de pickup e, quando aplicável, preço base sugerido (`offer`).
- Selecionar um Provider a partir dos BIDs recebidos e emitir `AWARD_ORDER` com termos finais.
- Garantir que o token de pickup (ou equivalente) seja entregue ao Provider vencedor para prova de retirada.
- Respeitar pagamento e condições acordadas no `AWARD_ORDER` (incluindo Risk Premium e wait-time quando contratado).

### 1.2 Direitos

- Estabelecer critérios de seleção (preço, reputação, ETA).
- Cancelar ou reabrir ordem conforme regras de atraso e exceção definidas no contrato comercial.
- Exigir prova (PoD) para transições IN_TRANSIT e DELIVERED quando o protocolo ou o contrato assim o exigir.

---

## 2. Provider (Quem entrega)

### 2.1 Responsabilidades

- Enviar `SUBMIT_BID` com boa fé: valor, ETA e, quando aplicável, motivo de sobretaxa (risk_assessment).
- Assinar o BID (campo `signature`) para não-repúdio.
- Atualizar estado da entrega via `UPDATE_STATUS` nos marcos definidos (ACCEPTED, ARRIVED_PICKUP, IN_TRANSIT, ARRIVED_DROPOFF, DELIVERED).
- Fornecer prova (scan, assinatura) quando exigido para IN_TRANSIT e DELIVERED.
- Reportar incidentes reais via `REPORT_INCIDENT` quando houver acidente, crime ou pane que afete a entrega ou a segurança.

### 2.2 Direitos

- Recusar ofertas sem penalidade obscura (sem shadowban por não dar lance).
- Incluir Risk Premium no BID de forma transparente.
- Ter reputação e identidade portáveis (DID); não ficar preso a uma única plataforma.
- Receber pagamento proporcional ao trajeto em caso de incidente legítimo (conforme seguro/contrato).

---

## 3. Observer (Opcional)

Entidades que atuam como auditoria, seguro ou cooperativa podem:

- Consumir eventos públicos do fluxo (broadcast, award, status, incident) para analytics, seguro ou governança.
- Não alteram o contrato entre Requester e Provider; sua participação é definida por acordos laterais (ex.: pool de seguro, fundo mútuo).

---

## 4. Termos do AWARD_ORDER

O `AWARD_ORDER` estabelece o contrato executável daquela entrega. Deve conter, no mínimo:

- `order_id`
- `selected_provider_did`
- `final_terms`: valor, moeda, ETA limite de pickup (e, quando aplicável, wait-time, seguro, return fee).

Implementações podem adicionar `contract_address` (escrow) e `pickup_token` para prova de retirada.

---

## 5. Penalidades e exceções

- **Cancelamento pelo Requester:** Conforme regras de atraso e força maior; o protocolo não define valores, apenas que o comportamento deve ser consistente com o contrato.
- **Cancelamento pelo Provider:** Pode incorrer em penalidade conforme contrato; incidente legítimo (REPORT_INCIDENT) não deve ser tratado como abandono.
- **Fraude (prova falsa):** Tratada por reputação e, quando aplicável, por mecanismos legais e de seguro.

---

**Versão:** 0.1.0  
**Última atualização:** Fevereiro 2026
