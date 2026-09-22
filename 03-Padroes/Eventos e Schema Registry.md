---
tags: [padrao, kafka, contrato]
tipo: padrao
status: planejado
---

# Eventos e Schema Registry

## Envelope padrão
```json
{
  "event_id": "b3f1c2e4-...",
  "event_type": "material.consumed",
  "event_version": 1,
  "occurred_at": "2026-09-21T10:15:00Z",
  "correlation_id": "op-42",
  "source": { "agent_id": "edge-01", "machine_id": "M-3" },
  "data": { "lote_codigo": "MP-A", "ordem_codigo": "OP-42", "quantidade": 12.5 }
}
```

## Regras
- **Versionar** eventos (`event_version`) e evoluir de forma compatível.
- Usar **Schema Registry** com Avro ou Protobuf (na AWS, o Glue Schema Registry é uma opção com MSK).
- `correlation_id` liga o evento ao trace do [[OpenTelemetry]].
- Escolha da chave de partição: [[Chave de Particao]].

## Catálogo
[[Catalogo de Eventos]]

## Pendente
Avro vs Protobuf: [[Perguntas em Aberto]].
