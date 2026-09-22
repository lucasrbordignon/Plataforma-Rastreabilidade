---
tags: [componente, kafka, mensageria]
tipo: componente
status: planejado
---

# Kafka (event bus)

Backbone de eventos de domínio. Na AWS: **Amazon MSK** ([[AWS Mapeamento]]).

## Tópicos
Ver [[Catalogo de Eventos]]:
`machine.telemetry` · `production.started` · `material.consumed` · `quality.inspection` · `production.completed`

## Regras
- Chave de partição definida por tópico: [[Chave de Particao]].
- Contratos versionados: [[Eventos e Schema Registry]].
- Consumidores **idempotentes**, com retry e DLQ: [[Idempotencia e DLQ]].
- Produtores de serviços usam [[Outbox Pattern]].
- Retenção e compactação: [[Retencao de Dados]].

## Por que Kafka
O log de eventos permite **replay**: reconstruir o [[Neo4j]] ou novas projeções a partir do histórico. Isso é central para auditoria e rastreabilidade.

## Quem produz e quem consome
| Papel | Componentes |
|---|---|
| Produz | [[Go Edge Agent]], [[production-service]], [[quality-service]] |
| Consome | [[production-service]], [[quality-service]], [[traceability-service]], [[notifier-service]] |

## Relacionado
[[Diagrama Geral]] · [[Conexao Edge-Nuvem]] · [[Perguntas em Aberto]] (MSK provisionado vs Serverless)
