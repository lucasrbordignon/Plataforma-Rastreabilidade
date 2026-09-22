---
tags: [componente, java, servico]
tipo: componente
status: planejado
linguagem: Java
---

# production-service

Java + Spring Boot, [[Arquitetura Hexagonal|hexagonal]].

## Responsabilidades
- Receber e gerenciar **ordens de produção** (ERP ou sistema).
- Registrar **consumo de lotes** e **apontamento de etapas**.
- Concluir a produção e gerar o **lote produzido**.
- Publicar eventos de domínio via [[Outbox Pattern]].

## Adapters
| Entrada | Saída |
|---|---|
| REST (ordens, apontamentos) | [[PostgreSQL]] (estado e outbox) |
| Consumer Kafka (`machine.telemetry`, `material.consumed`) | [[Redis]] (cache) |
| | Publisher Kafka (via outbox) |

## Eventos
Publica `production.started` e `production.completed`. Ver [[Catalogo de Eventos]].

## Dados
[[Modelo Relacional]]

## Relacionado
[[Fluxo Principal]] · [[Kafka]] · [[Idempotencia e DLQ]] · [[Observabilidade]]
