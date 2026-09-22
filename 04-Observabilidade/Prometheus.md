---
tags: [observabilidade]
tipo: ferramenta
status: planejado
---

# Prometheus

Armazena **métricas** e avalia **regras de alerta**.

## Métricas-chave
- Taxa e latência de requisições por serviço
- Lag de consumer group no [[Kafka]]
- Pool de conexões e latência do [[PostgreSQL]] e do [[Neo4j]]
- Métricas do [[Go Edge Agent]] (buffer, reenvios)
- Saúde do cluster ([[Kubernetes e Docker]])

## Alertas
Definidos em regras do Prometheus/Alertmanager e visualizados no [[Grafana]]. Alertas de negócio (ex.: inspeção reprovada) ficam no [[notifier-service]].

## Alternativa AWS
Amazon Managed Service for Prometheus. Ver [[AWS Mapeamento]].

## Relacionado
[[Observabilidade]] · [[OpenTelemetry]]
