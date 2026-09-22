---
tags: [adr, decisao]
tipo: adr
status: aceita
---

# ADR-006: OpenTelemetry como padrão de telemetria

**Status:** aceita

## Contexto
Queremos trocar backends de observabilidade sem alterar código.

## Decisão
Todos os serviços e o edge exportam via **OTLP** para o OTel Collector, que distribui para [[Prometheus]] e [[Loki e Tempo]]. [[Grafana]] consome.

## Consequências
- Portabilidade (self-hosted ou gerenciado na AWS).
- Um Collector a operar.
- Propagar `traceparent` nas mensagens [[Kafka]].

## Alternativas consideradas
- SDKs proprietários por backend: acoplamento.
- Só Prometheus e logs de arquivo: sem traces.

## Relacionado
[[OpenTelemetry]] · [[Observabilidade]]
