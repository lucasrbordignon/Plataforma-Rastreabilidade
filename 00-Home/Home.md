---
tags: [moc, home]
tipo: moc
---

# Plataforma de Rastreabilidade de Produção

Plataforma que acompanha a produção do chão de fábrica até o lote final, permitindo **rastrear** de onde cada lote veio e fazer **recall** de para onde ele foi. Este vault guarda todo o contexto, as decisões e o plano de implementação.

> [!info] Foco tecnológico
> Go (edge) · Java (core) · Kubernetes + Docker · Kafka · Arquitetura Hexagonal (ports and adapters) · Grafo (Neo4j) · OpenTelemetry · Prometheus · Grafana · Terraform + AWS

## Comece por aqui
1. [[Contexto e Objetivo]]
2. [[Diagrama Geral]]
3. [[Stack Tecnologica|Stack tecnológica]]
4. [[Fluxo Principal]]
5. [[Roadmap]]

## Mapa do vault

### Visão geral
[[Contexto e Objetivo]] · [[Diagrama Geral]] · [[Stack Tecnologica]] · [[Fluxo Principal]] · [[Glossario]]

### Componentes
- Borda: [[Go Edge Agent]]
- Mensageria: [[Kafka]]
- Serviços: [[production-service]] · [[quality-service]] · [[traceability-service]] · [[notifier-service]]
- Dados: [[PostgreSQL]] · [[Neo4j]] · [[Redis]]

### Padrões
[[Arquitetura Hexagonal]] · [[Outbox Pattern]] · [[Idempotencia e DLQ]] · [[Eventos e Schema Registry]] · [[Chave de Particao]]

### Domínio
[[Modelo de Grafo]] · [[Recall e Rastreio]] · [[Catalogo de Eventos]] · [[Modelo Relacional]]

### Observabilidade
[[Observabilidade]] · [[OpenTelemetry]] · [[Prometheus]] · [[Grafana]] · [[Loki e Tempo]]

### Infraestrutura
[[Kubernetes e Docker]] · [[Terraform]] · [[AWS Mapeamento]] · [[Conexao Edge-Nuvem]] · [[Seguranca]] · [[CICD e GitOps]] · [[Retencao de Dados]]

### Decisões (ADRs)
- [[ADR-001 Go no edge e Java no core]]
- [[ADR-002 Neo4j para genealogia]]
- [[ADR-003 Outbox pattern]]
- [[ADR-004 Comecar com poucos servicos]]
- [[ADR-005 Terraform na AWS]]
- [[ADR-006 OpenTelemetry como padrao de telemetria]]

### Planejamento
[[Roadmap]] · [[Checklist]] · [[Perguntas em Aberto]]

### Referências
[[Revisao da Arquitetura Original]]

## Como usar no Obsidian
- Abra a pasta `Plataforma-Rastreabilidade` como vault (*Abrir pasta como cofre*).
- Use o **Graph view** (Ctrl/Cmd + G) para ver as conexões. Já há cores por pasta.
- Os diagramas são blocos `mermaid` e renderizam sem plugin.
- Cada nota tem `tags` e `status` no frontmatter. Atualize o `status` conforme avança (`planejado`, `em-andamento`, `feito`).
- Ao tomar uma decisão nova, crie um ADR em `07-Decisoes` e ligue ele às notas afetadas.
