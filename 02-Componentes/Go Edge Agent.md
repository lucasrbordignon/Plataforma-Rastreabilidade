---
tags: [componente, go, edge]
tipo: componente
status: planejado
linguagem: Go
---

# Go Edge Agent

Agente que roda **na fábrica**, perto das máquinas. Coleta dados, normaliza e envia ao [[Kafka]].

## Responsabilidades
- **Coleta** de máquinas/PLCs, sensores, balanças/scanners e ERP local/CSV/APIs.
- **Normalização** para o envelope de evento ([[Catalogo de Eventos]]).
- **Buffer local**: se a rede cair, guarda os eventos em disco e reenvia depois.
- **Reenvio** com retry e backoff, mantendo a ordem por chave ([[Chave de Particao]]).
- **Healthcheck** para o Kubernetes/monitoramento.
- **Telemetria própria** (métricas, logs, traces) via [[OpenTelemetry]].

## Conectores
Modbus TCP · MQTT · HTTP · CSV

## Estrutura sugerida (ports and adapters também no Go)
```
edge-agent/
├── cmd/edge-agent/main.go
└── internal/
    ├── domain/        # Evento, regras de normalização
    ├── ports/         # interfaces: Collector, Buffer, Publisher
    ├── adapters/
    │   ├── modbus/    # implementa Collector
    │   ├── mqtt/
    │   ├── csv/
    │   ├── diskbuffer/  # implementa Buffer (ex.: BoltDB/Badger/SQLite)
    │   └── kafka/     # implementa Publisher
    ├── health/
    └── telemetry/
```

## Pontos de atenção
- Definir o que o edge faz **sozinho** se ficar horas sem nuvem (ex.: validar lote localmente). Ver [[Perguntas em Aberto]].
- Segurança do link edge → nuvem: [[Conexao Edge-Nuvem]] e [[Seguranca]].
- Tamanho máximo do buffer e política de descarte.

## Decisões
[[ADR-001 Go no edge e Java no core]]

## Relacionado
[[Kafka]] · [[Idempotencia e DLQ]] · [[Roadmap]] (Fase 1)
