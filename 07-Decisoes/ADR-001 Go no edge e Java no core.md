---
tags: [adr, decisao]
tipo: adr
status: aceita
---

# ADR-001: Go no edge e Java no core

**Status:** aceita

## Contexto
O agente precisa rodar perto das máquinas (recursos limitados, binário simples). O núcleo concentra regra de negócio mais rica.

## Decisão
Usar **Go** no [[Go Edge Agent]] (e no [[notifier-service]]) e **Java + Spring Boot** nos serviços de negócio.

## Consequências
- Edge leve, binário único, baixo consumo.
- Duas linguagens para manter: pipelines e padrões de observabilidade precisam cobrir ambas ([[OpenTelemetry]]).

## Alternativas consideradas
- Tudo em Java: mais uniforme, edge mais pesado.
- Tudo em Go: núcleo com menos ecossistema corporativo pronto.

## Relacionado
[[Stack Tecnologica]] · [[Arquitetura Hexagonal]]
