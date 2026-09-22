---
tags: [visao-geral, diagrama]
tipo: diagrama
status: planejado
---

# Diagrama geral

```mermaid
flowchart TD
  subgraph Fabrica["Fábrica (on-prem)"]
    M["Máquinas, sensores, PLCs"] --> E["Go Edge Agent"]
  end
  E -->|"VPN + mTLS"| K{{"Kafka (MSK)"}}
  subgraph K8S["Kubernetes (EKS)"]
    P["production-service (Java)"]
    Q["quality-service (Java)"]
    T["traceability-service (Java)"]
    N["notifier (Go)"]
  end
  K --> P
  K --> Q
  K --> T
  K --> N
  P --> PG[("PostgreSQL")]
  Q --> PG
  T --> PG
  T --> NEO[("Neo4j")]
  P --> R[("Redis")]
  K8S -.->|OTLP| OT["OpenTelemetry Collector"]
  E -.->|OTLP| OT
  OT --> PROM["Prometheus"]
  OT --> TEMPO["Tempo"]
  OT --> LOKI["Loki"]
  PROM --> G["Grafana"]
  TEMPO --> G
  LOKI --> G
```

## Leitura
1. O [[Go Edge Agent]] coleta, normaliza e reenvia eventos, com buffer local para tolerar queda de rede.
2. O [[Kafka]] é o backbone. Os serviços também **publicam** eventos de volta via [[Outbox Pattern]] (a seta só mostra o consumo para não poluir).
3. O [[traceability-service]] projeta os eventos no [[Neo4j]] (grafo de genealogia).
4. Toda telemetria passa pelo [[OpenTelemetry]] Collector. Ver [[Observabilidade]].

## Diagramas relacionados
- Estrutura interna de um serviço: [[Arquitetura Hexagonal]]
- Grafo de lotes: [[Modelo de Grafo]]
- Infra na AWS: [[AWS Mapeamento]]
