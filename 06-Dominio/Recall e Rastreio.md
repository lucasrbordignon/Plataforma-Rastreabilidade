---
tags: [dominio, grafo, consulta]
tipo: dominio
status: planejado
---

# Recall e rastreio

Duas direções sobre o [[Modelo de Grafo]]:

| Pergunta | Direção | Nome |
|---|---|---|
| "De onde veio o lote PA-7?" | para trás | **Rastreio** |
| "Para onde foi a matéria-prima MP-A?" | para frente | **Recall** |

## Recall (para frente)
```cypher
MATCH p = (:LoteMP {codigo: $codigo})-[:CONSUMIDO_EM|PRODUZ|EXPEDIDO_PARA*1..10]->(c:Cliente)
RETURN DISTINCT c.codigo, c.nome, length(p) AS profundidade
```

## Rastreio (para trás)
```cypher
MATCH p = (mp:LoteMP)-[:CONSUMIDO_EM|PRODUZ*1..10]->(:LotePA {codigo: $codigo})
RETURN DISTINCT mp.codigo, mp.fornecedor
```

## Consulta-chave completa
Origem, processo, operadores, máquina, qualidade e destino: combine o rastreio com `EXECUTADA_EM` e `INSPECIONADA_EM`.

> [!tip] Sempre limite a profundidade
> `*1..10` evita travessias sem limite. Ajuste conforme a profundidade real da sua genealogia.

## Expostas por
[[traceability-service]] (REST, adapter de entrada). Meça o tempo das consultas no [[Grafana]].

## Relacionado
[[Fluxo Principal]] (etapa 6) · [[Neo4j]]
