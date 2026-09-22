---
tags: [adr, decisao]
tipo: adr
status: aceita
---

# ADR-003: Outbox pattern para publicar eventos

**Status:** aceita

## Contexto
Gravar no banco e publicar no Kafka não é atômico. Risco de perder ou duplicar eventos.

## Decisão
Adotar o [[Outbox Pattern]] nos serviços que publicam eventos, com consumidores idempotentes.

## Consequências
- Garantia *at least once* sem perda.
- Necessidade de tabela `outbox_event` e de um publisher.
- Consumidores precisam tratar duplicatas ([[Idempotencia e DLQ]]).

## Alternativas consideradas
- Publicar direto no Kafka após o commit: simples, mas com janela de perda.
- Transações distribuídas: complexas e frágeis.

## Relacionado
[[PostgreSQL]] · [[Kafka]] · [[Modelo Relacional]]
