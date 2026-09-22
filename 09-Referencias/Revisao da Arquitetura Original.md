---
tags: [referencia, revisao]
tipo: referencia
status: concluido
---

# Revisão da arquitetura original

A primeira versão (diagrama com Java + Hexagonal + Microsserviços Go + Observabilidade + Kubernetes + Terraform) foi revisada. Resultado: a arquitetura atual, mais enxuta.

## O que estava bom
- Go no edge e Java no core ([[ADR-001 Go no edge e Java no core]]).
- Buffer local e reenvio no edge ([[Go Edge Agent]]).
- Kafka como backbone e eventos bem nomeados ([[Kafka]], [[Catalogo de Eventos]]).
- Observabilidade completa ([[Observabilidade]]).
- Terraform cobrindo a infra ([[Terraform]]).

## Pontos de atenção e onde foram tratados
| # | Ponto | Tratamento |
|---|---|---|
| 1 | Genealogia em Postgres relacional (problema de grafo) | [[ADR-002 Neo4j para genealogia]], [[Modelo de Grafo]] |
| 2 | Microsserviços demais para começar | [[ADR-004 Comecar com poucos servicos]] |
| 3 | Sem Outbox, idempotência e DLQ | [[Outbox Pattern]], [[Idempotencia e DLQ]] |
| 4 | Sem Schema Registry nem chave de partição | [[Eventos e Schema Registry]], [[Chave de Particao]] |
| 5 | Locks distribuídos em Redis para operações críticas | [[Redis]], [[PostgreSQL]] |
| 6 | Kafka aparecia duplicado (bus e infra) | [[AWS Mapeamento]] (MSK) |
| 7 | Segurança ausente | [[Seguranca]], [[Conexao Edge-Nuvem]] |
| 8 | Resiliência offline do edge | [[Go Edge Agent]], [[Perguntas em Aberto]] |
| 9 | Sem CI/CD e GitOps | [[CICD e GitOps]] |
| 10 | Sem estratégia de retenção | [[Retencao de Dados]] |

## Detalhes do diagrama original
- O `api-gateway` não deixava claro que era a entrada de todos os serviços (adiado, ver [[ADR-004 Comecar com poucos servicos]]).
- Muitas setas cruzando na camada de dados.
- Hexagonal detalhada só em um serviço, dando a impressão de que os demais não seguiam o padrão ([[Arquitetura Hexagonal]] vale para todos).

Voltar: [[Home]]
