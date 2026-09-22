---
tags: [observabilidade]
tipo: ferramenta
status: planejado
---

# Loki e Tempo

- **Loki**: logs centralizados. Use logs estruturados (JSON) com `trace_id`.
- **Tempo**: traces distribuídos.

No [[Grafana]] dá para saltar de um trace para os logs correspondentes pelo `trace_id`.

## Armazenamento
Ambos podem guardar dados em objeto (S3 na AWS). Ver [[AWS Mapeamento]] e [[Retencao de Dados]].

## Relacionado
[[Observabilidade]] · [[OpenTelemetry]]
