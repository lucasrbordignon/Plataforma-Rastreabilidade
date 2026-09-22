---
tags: [padrao, kafka]
tipo: padrao
status: planejado
---

# Chave de partição

No [[Kafka]], a ordem só é garantida **dentro de uma partição**. A chave define a partição.

| Tópico | Chave sugerida | Motivo |
|---|---|---|
| `machine.telemetry` | `machine_id` | Ordem por máquina |
| `production.started` | `production_order_id` | Ordem por ordem de produção |
| `material.consumed` | `production_order_id` | Consumo antes da conclusão |
| `quality.inspection` | `production_order_id` | Junto do fluxo da ordem |
| `production.completed` | `production_order_id` | Fecha o ciclo da ordem |

> [!warning] Sugestão inicial
> Validar com o comportamento real. Chave mal escolhida gera partições quentes ou perda de ordenação.

## Relacionado
[[Catalogo de Eventos]] · [[Eventos e Schema Registry]] · [[Go Edge Agent]]
