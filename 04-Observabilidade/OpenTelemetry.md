---
tags: [observabilidade]
tipo: ferramenta
status: planejado
---

# OpenTelemetry

Padrão aberto para gerar e exportar **traces, métricas e logs**.

## Como usamos
- SDK/agent em cada serviço: Java (agent) e Go (SDK).
- Exportação via **OTLP** para o **OTel Collector**.
- O Collector distribui para [[Prometheus]], [[Loki e Tempo]].
- O [[Go Edge Agent]] também exporta telemetria (caminho tracejado no [[Diagrama Geral]]).

## Propagação de contexto
Propague o `traceparent` nos headers das mensagens [[Kafka]] para conectar o trace de ponta a ponta (edge → Kafka → serviço → banco). Use também o `correlation_id` do [[Eventos e Schema Registry|envelope]].

## Decisão
[[ADR-006 OpenTelemetry como padrao de telemetria]]

## Relacionado
[[Observabilidade]] · [[Kubernetes e Docker]] (Collector como DaemonSet ou Deployment)
