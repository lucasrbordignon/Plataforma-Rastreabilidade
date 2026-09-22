---
tags: [adr, decisao]
tipo: adr
status: aceita
---

# ADR-004: Começar com poucos serviços

**Status:** aceita

## Contexto
A arquitetura original tinha cinco serviços mais gateway, muita superfície para começar.

## Decisão
Iniciar com [[production-service]], [[quality-service]], [[traceability-service]] e [[notifier-service]]. `api-gateway`, `integration-service` e o dashboard web ficam para depois, conforme necessidade real.

## Consequências
- Menos operação e menos deploys.
- Fronteiras precisam continuar limpas (hexagonal) para permitir extração futura.

## Alternativas consideradas
- Monólito modular: ainda menor, mas perde treino de operação distribuída.
- Manter todos os serviços originais.

## Relacionado
[[Revisao da Arquitetura Original]] · [[Arquitetura Hexagonal]] · [[Roadmap]]
