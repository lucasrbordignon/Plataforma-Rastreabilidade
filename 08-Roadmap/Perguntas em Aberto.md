---
tags: [roadmap, decisao]
tipo: pendencias
status: em-andamento
---

# Perguntas em aberto

Transforme cada item resolvido em um ADR na pasta `07-Decisoes`.

1. **Neo4j: onde roda?** StatefulSet no EKS, AuraDB ou Neptune? ([[Neo4j]], [[AWS Mapeamento]], [[ADR-002 Neo4j para genealogia]])
2. **MSK provisionado ou Serverless?** ([[Kafka]])
3. **Avro ou Protobuf?** Glue Schema Registry ou Confluent? ([[Eventos e Schema Registry]])
4. **Outbox com polling ou Debezium?** ([[Outbox Pattern]])
5. **Edge fala direto com o Kafka ou via gateway de ingestão?** ([[Conexao Edge-Nuvem]])
6. **O que o edge faz sozinho offline por horas?** Validação local de lote? ([[Go Edge Agent]])
7. **Observabilidade self-hosted ou gerenciada?** ([[Observabilidade]])
8. **Prazos reais de retenção regulatória.** ([[Retencao de Dados]])
9. **Monorepo ou multi-repo?** ([[CICD e GitOps]])
10. **Quem publica `material.consumed`: edge ou production-service?** ([[Catalogo de Eventos]])
11. **Quando extrair `api-gateway` e `integration-service`?** ([[ADR-004 Comecar com poucos servicos]])
