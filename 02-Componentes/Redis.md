---
tags: [componente, dados]
tipo: componente
status: planejado
---

# Redis

Cache e dados temporários. Na AWS: **ElastiCache** ([[AWS Mapeamento]]).

## Usos
- Cache de leituras frequentes.
- Sessões e dados temporários.

## Cuidado
Locks distribuídos em Redis **não são garantia forte** de exclusão mútua. Para operações críticas de rastreabilidade, use controle transacional no [[PostgreSQL]]. Ver [[Revisao da Arquitetura Original]] (item 5).

## Usado por
[[production-service]]
