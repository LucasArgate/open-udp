# Mensagens e Schemas (JSON) — Open UDP v0.1

**Namespace:** `usp.delivery`

Este documento define os payloads JSON padrão para comunicação entre **Requester** e **Provider** no protocolo Open UDP. Todos os tipos de mensagem incluem `type` e identificadores de ordem/ator conforme abaixo.

---

## 1. Descoberta — `BROADCAST_ORDER`

O Requester publica a necessidade de entrega para a região.

```json
{
  "type": "BROADCAST_ORDER",
  "id": "ord_uuid_v4",
  "timestamp": "2026-02-08T19:30:00Z",
  "requester": {
    "did": "did:soul:restaurante_sabor_mineiro",
    "name": "Sabor Mineiro",
    "rating": 4.8
  },
  "origin": {
    "lat": -23.5505,
    "lng": -46.6333,
    "address_type": "commercial",
    "instructions": "Entrada de serviço nos fundos"
  },
  "destination": {
    "lat": -23.5615,
    "lng": -46.6559,
    "address_type": "residential_condo",
    "instructions": "Deixar na portaria com o robô"
  },
  "cargo": {
    "type": "food_hot",
    "weight_kg": 0.8,
    "dimensions_cm": [30, 30, 20],
    "fragile": true
  },
  "constraints": {
    "pickup_window_start": "2026-02-08T19:35:00Z",
    "pickup_window_end": "2026-02-08T19:45:00Z",
    "must_be_human": true,
    "thermal_bag_required": true
  },
  "offer": {
    "currency": "BRL",
    "amount": 12.50,
    "tip_guaranteed": 2.00
  }
}
```

---

## 2. Negociação — `SUBMIT_BID`

Os Providers respondem com propostas.

```json
{
  "type": "SUBMIT_BID",
  "order_id": "ord_uuid_v4",
  "provider": {
    "did": "did:soul:motoboy_joao",
    "vehicle_type": "motorcycle",
    "rating": 4.95,
    "total_deliveries": 12503
  },
  "bid": {
    "amount": 15.00,
    "currency": "BRL",
    "eta_pickup": "7m",
    "route_score": 0.85
  },
  "risk_assessment": {
    "weather_condition": "light_rain",
    "traffic_condition": "heavy",
    "surcharge_reason": "rain_risk"
  },
  "signature": "sig_ed25519_..."
}
```

---

## 3. Contrato e aceite — `AWARD_ORDER`

O Requester escolhe o vencedor e define os termos finais.

```json
{
  "type": "AWARD_ORDER",
  "order_id": "ord_uuid_v4",
  "selected_provider_did": "did:soul:motoboy_joao",
  "final_terms": {
    "amount": 15.00,
    "currency": "BRL",
    "eta_pickup_limit": "2026-02-08T19:42:00Z"
  },
  "contract_address": "0xABC123...",
  "pickup_token": "token_encrypted_..."
}
```

---

## 4. Execução — `UPDATE_STATUS`

Atualização de estado da entrega. Campos `location` e `proof` conforme regras de [security.md](./security.md).

```json
{
  "type": "UPDATE_STATUS",
  "order_id": "ord_uuid_v4",
  "provider_did": "did:soul:motoboy_joao",
  "status": "IN_TRANSIT",
  "location": {
    "lat": -23.5550,
    "lng": -46.6400,
    "timestamp": "2026-02-08T19:40:00Z"
  },
  "proof": "scan_qr_result_..."
}
```

**Valores de `status`:** `ACCEPTED` | `ARRIVED_PICKUP` | `IN_TRANSIT` | `ARRIVED_DROPOFF` | `DELIVERED` | `CANCELLED`. Para incidente, usar `REPORT_INCIDENT`; estado resultante pode ser `FROZEN`.

---

## 5. Emergência — `REPORT_INCIDENT`

Comunicação de acidente, crime ou pane que afete a entrega ou a segurança.

```json
{
  "type": "REPORT_INCIDENT",
  "order_id": "ord_uuid_v4",
  "provider_did": "did:soul:motoboy_joao",
  "incident_type": "ACCIDENT",
  "priority": "HIGH",
  "location": {
    "lat": -23.5580,
    "lng": -46.6450
  },
  "data": {
    "accelerometer_spike": "5.2g",
    "user_conscious": true
  }
}
```

**Valores de `incident_type`:** `ACCIDENT` | `CRITICAL_STOP` | `ROBBERY` | `VEHICLE_BREAKDOWN` (ou extensões definidas em [extensions.md](./extensions.md)).

---

**Versão:** 0.1.0  
**Última atualização:** Fevereiro 2026
