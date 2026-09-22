---
tags: [observabilidade]
tipo: ferramenta
status: planejado
---

# Grafana

Camada de **visualização** sobre [[Prometheus]] (métricas), [[Loki e Tempo]] (logs e traces).

## Dashboards sugeridos
1. **Saúde dos serviços**: latência, erros, throughput.
2. **Kafka**: lag por consumer group, DLQ.
3. **Edge**: conectividade, buffer, eventos por máquina.
4. **Rastreabilidade**: tempo das consultas de recall, tamanho do grafo.
5. **Produção**: ordens em andamento e concluídas (se as métricas de negócio forem expostas).

## Dica
Salve dashboards como código (JSON no repositório) e provisione via [[CICD e GitOps]].

## Alternativa AWS
Amazon Managed Grafana. Ver [[AWS Mapeamento]].

## Relacionado
[[Observabilidade]]
