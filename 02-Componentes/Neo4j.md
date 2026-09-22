---
tags: [componente, dados, grafo]
tipo: componente
status: planejado
---

# Neo4j

Banco de grafo para a **genealogia de lotes**.

## Papel
Projeção alimentada pelo [[traceability-service]] a partir do [[Kafka]]. Responde rastreio e recall com travessia de caminhos ([[Recall e Rastreio]]).

## Modelo
[[Modelo de Grafo]]

## Onde roda
| Opção | Comentário |
|---|---|
| StatefulSet no EKS + volume EBS | Mais didático, você controla tudo |
| Neo4j AuraDB (Marketplace) | Gerenciado, custo maior |
| Amazon Neptune (openCypher) | Gerenciado pela AWS; testar compatibilidade das queries |

Ver [[AWS Mapeamento]] e [[Perguntas em Aberto]].

## Decisão
[[ADR-002 Neo4j para genealogia]]
