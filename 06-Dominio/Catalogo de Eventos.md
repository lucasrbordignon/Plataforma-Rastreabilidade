---
tags: [dominio, kafka, contrato]
tipo: dominio
status: planejado
---

# Catálogo de eventos

> [!note] Produtores e consumidores são sugestões iniciais. Ajuste conforme a implementação.

| Evento | Produtor | Consumidores | Chave | Descrição |
|---|---|---|---|---|
| `machine.telemetry` | [[Go Edge Agent]] | [[production-service]] | `machine_id` | Leituras de máquina e sensores |
| `production.started` | [[production-service]] | [[traceability-service]], [[quality-service]] | `production_order_id` | Início da ordem |
| `material.consumed` | [[Go Edge Agent]] / [[production-service]] | [[traceability-service]] | `production_order_id` | Baixa de lote de matéria-prima |
| `quality.inspection` | [[quality-service]] | [[traceability-service]], [[notifier-service]] | `production_order_id` | Resultado de inspeção |
| `production.completed` | [[production-service]] | [[traceability-service]], [[notifier-service]] | `production_order_id` | Lote produzido gerado |

## Contrato
Envelope e versionamento: [[Eventos e Schema Registry]].
Chaves: [[Chave de Particao]].
Falhas: [[Idempotencia e DLQ]].

## Relacionado
[[Kafka]] · [[Fluxo Principal]]
