---
tags: [visao-geral, stack]
tipo: referencia
status: planejado
---

# Stack tecnológica

| Camada | Tecnologia | Nota |
|---|---|---|
| Edge | Go | [[Go Edge Agent]] |
| Serviços de negócio | Java + Spring Boot | [[production-service]], [[quality-service]], [[traceability-service]] |
| Serviço leve | Go | [[notifier-service]] |
| Arquitetura | Hexagonal (ports and adapters) | [[Arquitetura Hexagonal]] |
| Mensageria | Apache Kafka (MSK na AWS) | [[Kafka]] |
| Banco transacional | PostgreSQL (RDS) | [[PostgreSQL]] |
| Banco de grafo | Neo4j | [[Neo4j]] |
| Cache | Redis (ElastiCache) | [[Redis]] |
| Contêineres | Docker | [[Kubernetes e Docker]] |
| Orquestração | Kubernetes (EKS) | [[Kubernetes e Docker]] |
| Telemetria | OpenTelemetry | [[OpenTelemetry]] |
| Métricas | Prometheus | [[Prometheus]] |
| Dashboards | Grafana | [[Grafana]] |
| Logs e traces | Loki e Tempo | [[Loki e Tempo]] |
| Infra como código | Terraform | [[Terraform]] |
| Nuvem | AWS | [[AWS Mapeamento]] |

## Divisão de linguagens
Go onde importa ser leve e rodar perto das máquinas; Java onde a regra de negócio é rica. Ver [[ADR-001 Go no edge e Java no core]].
