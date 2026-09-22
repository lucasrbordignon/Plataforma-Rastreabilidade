---
tags: [padrao, kafka, consistencia]
tipo: padrao
status: planejado
---

# Outbox pattern

## Problema
Gravar no [[PostgreSQL]] e publicar no [[Kafka]] são duas operações. Se uma falhar, perde-se ou duplica-se evento.

## Solução
Na **mesma transação** do dado de negócio, grava-se o evento em `outbox_event`. Um processo separado lê a tabela e publica no Kafka.

```mermaid
sequenceDiagram
  participant UC as Caso de uso
  participant DB as PostgreSQL
  participant PUB as Kafka publisher
  participant K as Kafka
  UC->>DB: BEGIN, grava dado + outbox_event, COMMIT
  PUB->>DB: lê eventos não publicados
  PUB->>K: publica evento
  PUB->>DB: marca como publicado
```

## Variações
- **Polling**: publisher lê a tabela periodicamente. Mais simples para começar.
- **CDC (Debezium)**: lê o log do banco. Menor latência, mais peças.

Comece com polling e decida depois ([[Perguntas em Aberto]]).

## Garantia resultante
*At least once*. Por isso os consumidores precisam ser idempotentes: [[Idempotencia e DLQ]].

## Estrutura da tabela
Ver [[Modelo Relacional]].

## Decisão
[[ADR-003 Outbox pattern]]
