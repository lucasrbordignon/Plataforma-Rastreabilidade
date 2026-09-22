---
tags: [componente, dados]
tipo: componente
status: planejado
---

# PostgreSQL

Banco **transacional**. Na AWS: **RDS** ([[AWS Mapeamento]]).

## Guarda
- Ordens, etapas, consumos, lotes, inspeções ([[Modelo Relacional]]).
- Tabela `outbox_event` ([[Outbox Pattern]]).
- Tabela `processed_event` para idempotência ([[Idempotencia e DLQ]]).

## Não é o lugar da genealogia
Consultas de recall em cadeia são um problema de grafo. Para isso existe o [[Neo4j]] ([[ADR-002 Neo4j para genealogia]]).

## Cuidados
- Controle de concorrência com **locks otimistas/pessimistas no próprio banco**, não em [[Redis]].
- Particionamento por data para retenção longa ([[Retencao de Dados]]).

## Usado por
[[production-service]] · [[quality-service]] · [[traceability-service]]
