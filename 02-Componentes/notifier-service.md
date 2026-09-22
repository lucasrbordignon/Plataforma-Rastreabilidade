---
tags: [componente, go, servico]
tipo: componente
status: planejado
linguagem: Go
---

# notifier-service

Serviço leve em Go que envia notificações (e-mail, webhook, chat) a partir de eventos.

## Responsabilidades
- Consumir eventos relevantes (ex.: `quality.inspection` reprovada, recall aberto).
- Enviar alertas ao canal configurado.
- Ser simples e barato de operar.

## Notas
- Começar como serviço próprio faz sentido por ser em Go e pequeno. Alternativa: módulo dentro de outro serviço, ver [[ADR-004 Comecar com poucos servicos]].
- Alertas de **infraestrutura** ficam no [[Grafana]]/[[Prometheus]], não aqui.

## Relacionado
[[Kafka]] · [[Catalogo de Eventos]]
