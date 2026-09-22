---
tags: [dominio, postgres]
tipo: dominio
status: planejado
---

# Modelo relacional (PostgreSQL)

Rascunho inicial. A genealogia completa vive no [[Neo4j]] ([[Modelo de Grafo]]); aqui fica o estado transacional.

```mermaid
erDiagram
  PRODUCTION_ORDER ||--o{ PRODUCTION_STEP : tem
  PRODUCTION_ORDER ||--o{ MATERIAL_CONSUMPTION : consome
  MATERIAL_LOT ||--o{ MATERIAL_CONSUMPTION : origem
  PRODUCTION_ORDER ||--o| FINISHED_LOT : gera
  PRODUCTION_ORDER ||--o{ QUALITY_INSPECTION : inspecionada
  PRODUCTION_ORDER {
    uuid id PK
    string codigo
    string status
    timestamp inicio
    timestamp fim
  }
  PRODUCTION_STEP {
    uuid id PK
    uuid order_id FK
    string etapa
    string machine_id
    timestamp inicio
    timestamp fim
  }
  MATERIAL_LOT {
    uuid id PK
    string codigo
    string fornecedor
  }
  MATERIAL_CONSUMPTION {
    uuid id PK
    uuid order_id FK
    uuid lot_id FK
    numeric quantidade
  }
  FINISHED_LOT {
    uuid id PK
    uuid order_id FK
    string codigo
  }
  QUALITY_INSPECTION {
    uuid id PK
    uuid order_id FK
    string resultado
    timestamp data
  }
```

## Tabelas técnicas
| Tabela | Uso | Nota |
|---|---|---|
| `outbox_event` | eventos a publicar (`id`, `aggregate_id`, `type`, `payload`, `created_at`, `published_at`) | [[Outbox Pattern]] |
| `processed_event` | ids de eventos já processados (`event_id` PK, `processed_at`) | [[Idempotencia e DLQ]] |

## Retenção
Particionar por data as tabelas de alto volume: [[Retencao de Dados]].

## Usado por
[[production-service]] · [[quality-service]] · [[traceability-service]] · [[PostgreSQL]]
