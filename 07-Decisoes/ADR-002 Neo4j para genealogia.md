---
tags: [adr, decisao]
tipo: adr
status: proposta
---

# ADR-002: Neo4j para genealogia de lotes

**Status:** proposta

## Contexto
A genealogia (origem, processo, destino) é um problema de grafo. Recall em cadeia com joins/CTEs recursivas no [[PostgreSQL]] tende a ficar pesado com volume alto.

## Decisão
Usar [[Neo4j]] como **projeção** da genealogia, alimentada por eventos do [[Kafka]]. O Postgres continua com o estado transacional.

## Consequências
- Consultas de [[Recall e Rastreio]] naturais e rápidas.
- Mais um banco para operar; grafo é reconstruível por replay.
- Escolha do modo de hospedagem pendente ([[AWS Mapeamento]]).

## Alternativas consideradas
- Só Postgres com CTE recursiva: mais simples, pode não escalar.
- Amazon Neptune (openCypher): gerenciado, exige validar compatibilidade.

## Relacionado
[[Modelo de Grafo]] · [[traceability-service]] · [[Perguntas em Aberto]]
