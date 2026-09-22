---
tags: [infra, dados]
tipo: infra
status: planejado
---

# Retenção de dados

Rastreabilidade costuma exigir **anos** de retenção (regulatório). Lacuna da arquitetura original ([[Revisao da Arquitetura Original]], item 10).

## Estratégia inicial
- [[PostgreSQL]]: particionar tabelas grandes por data; arquivar partições antigas.
- **S3**: laudos, evidências e arquivos frios, com *lifecycle* para classes mais baratas.
- [[Kafka]]: retenção limitada por tópico; o histórico de longo prazo precisa de destino (ex.: sink para S3) se o replay for depender dele.
- [[Neo4j]]: reconstruível a partir de eventos; definir se o histórico completo fica no grafo.
- [[Loki e Tempo]]: retenção curta a média (dias/semanas).

## Pendente
Definir prazos reais conforme o setor: [[Perguntas em Aberto]].
