# Open UDP — Security-by-Design

**Namespace:** `usp.delivery`

O Open UDP foi projetado com a **segurança física do entregador** e a **confiança operacional** do restaurante/cliente como pré-requisitos do protocolo, não como features opcionais.

---

## 1. Segurança física do entregador (Safety)

### 1.1 Kill Switch e detecção de anomalias

O Agente Pessoal do entregador (no smartphone) pode monitorar sensores durante a rota ativa (`IN_TRANSIT`):

- **Acelerômetro:** Detecção de impacto brusco (acidente) ou queda.
- **Giroscópio:** Mudança repentina de orientação (ex.: moto).
- **GPS:** Parada não programada em área de risco mapeada (geofence).

**Ação recomendada:** Em caso de anomalia crítica, o agente pode disparar `REPORT_INCIDENT` com tipo apropriado (ex.: `ACCIDENT`, `CRITICAL_STOP`), permitindo:

- Alertas para contatos de emergência e SAMU (quando integrado).
- Notificação ao Requester/Cliente ("Incidente com entregador, pedido atrasará").
- Possível acionamento de cooperativa ou rede de apoio.

### 1.2 Risk Budget (orçamento de risco)

O agente do entregador pode manter um "saldo de risco" diário configurável. Cada rota aceita consome pontos com base em horário, clima e histórico de risco do trajeto. Se o risco exceder o saldo, o agente pode recusar o BID ou incluir um **Risk Premium** explícito no lance. O protocolo suporta essa negociação via `risk_assessment` no `SUBMIT_BID`.

---

## 2. Confiança e prova (Trust)

### 2.1 Reputação descentralizada (identidade)

A identidade do entregador é um **DID (Decentralized Identifier)**. A reputação é construída por assinaturas criptográficas de entregas concluídas. O entregador que troca de aplicativo ou agregador mantém seu histórico; o Requester pode exigir nível mínimo de reputação para pedidos sensíveis.

### 2.2 Prova de entrega (Proof of Delivery — PoD)

Para reduzir fraude ("não recebi", "motoboy não entregou"):

- **Handoff seguro:** O cliente deve escanear um QR Code dinâmico (ou equivalente) no dispositivo do entregador para liberar pagamento e marcar `DELIVERED`.
- **Geofence lock (recomendado):** O QR só é considerado válido se ambos os dispositivos estiverem dentro de um raio definido do destino (ex.: 50 m).

As transições **IN_TRANSIT** e **DELIVERED** devem ser acompanhadas de `proof` quando o contrato ou a implementação assim exigir (ver [specification.md](./specification.md) e [messages.md](./messages.md)).

---

## 3. Privacidade e proteção de dados

### 3.1 Mascaramento de endereço na fase de BID

Durante a fase aberta de BID, o endereço exato do cliente **não** precisa ser revelado. Apenas bairro ou CEP generalizado podem ser expostos. O endereço completo deve ser enviado apenas ao Provider vencedor no `AWARD_ORDER`, de preferência criptografado com a chave pública do Provider.

### 3.2 Histórico sensível

O histórico detalhado de rotas do entregador pode ser mantido localmente (edge) no dispositivo, não obrigatoriamente na nuvem da plataforma. A plataforma pode receber apenas metadados agregados para analytics, preservando a rotina e a privacidade do trabalhador.

---

## 4. Referências

- [Open USP — Security](https://github.com/LucasArgate/open-usp/blob/main/manifest/security.md)
- [Open UDP — Specification](./specification.md)
- [Open UDP — Messages](./messages.md)

---

**Versão:** 0.1.0  
**Última atualização:** Fevereiro 2026
