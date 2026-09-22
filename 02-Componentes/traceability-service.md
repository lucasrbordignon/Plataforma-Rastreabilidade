---
tags: [componente, java, servico, grafo]
tipo: componente
status: planejado
linguagem: Java
---

# traceability-service

Coração da rastreabilidade. Java + Spring Boot, [[Arquitetura Hexagonal|hexagonal]].

## Responsabilidades
- Consumir `production.started`, `material.consumed`, `quality.inspection` e `production.completed`.
- **Projetar** os eventos no grafo de genealogia ([[Neo4j]], ver [[Modelo de Grafo]]).
- Expor a **consulta-chave**: origem, processo, operadores, máquina, qualidade e destino ([[Recall e Rastreio]]).
- Guardar metadados no [[PostgreSQL]] quando fizer sentido.

## Estrutura de pacotes sugerida
```
com.empresa.traceability/
├── domain/
│   ├── model/          # Lote, Ordem, Consumo (sem framework)
│   └── service/
├── application/
│   ├── port/in/        # RegistrarConsumoUseCase, ConsultarRecallUseCase
│   ├── port/out/       # LoteGrafoPort, EventoProcessadoPort
│   └── usecase/
└── adapter/
    ├── in/kafka/       # consumers
    ├── in/rest/        # consultas
    ├── out/neo4j/      # implementa LoteGrafoPort
    └── out/postgres/
```

## Regras
- Consumidor **idempotente** (mesmo evento, mesmo efeito): [[Idempotencia e DLQ]].
- O grafo é uma **projeção**: pode ser reconstruído por replay do [[Kafka]].

## Decisões
[[ADR-002 Neo4j para genealogia]]
