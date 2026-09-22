---
tags: [roadmap, checklist]
tipo: checklist
status: em-andamento
---

# Checklist

Volta para: [[Roadmap]]

## Fase 0: base local
- [ ] `docker compose` com [[Kafka]]
- [ ] [[PostgreSQL]], [[Neo4j]] e [[Redis]] no compose
- [ ] OTel Collector, [[Prometheus]], [[Loki e Tempo]] e [[Grafana]] no compose

## Fase 1: edge
- [ ] Simulador de máquinas/sensores
- [ ] Coleta + normalização para o envelope ([[Eventos e Schema Registry]])
- [ ] Buffer local em disco e reenvio
- [ ] Healthcheck e telemetria própria
- [ ] Testar queda e volta da rede

## Fase 2: production-service
- [ ] Esqueleto hexagonal ([[Arquitetura Hexagonal]]) e teste de arquitetura
- [ ] Ordens, consumo e apontamento
- [ ] [[Outbox Pattern]] + publisher
- [ ] Consumers idempotentes ([[Idempotencia e DLQ]])

## Fase 3: traceability
- [ ] Constraints e índices no Neo4j ([[Modelo de Grafo]])
- [ ] Projeção dos eventos com `MERGE`
- [ ] Endpoints de rastreio e recall ([[Recall e Rastreio]])
- [ ] Teste de replay reconstruindo o grafo

## Fase 4: qualidade e notificação
- [ ] [[quality-service]] com evidências em objeto
- [ ] [[notifier-service]] consumindo eventos

## Fase 5: observabilidade
- [ ] Propagação de `traceparent` nas mensagens Kafka
- [ ] Dashboards (saúde, Kafka, edge, rastreabilidade)
- [ ] Alertas de lag e DLQ

## Fase 6: Kubernetes local
- [ ] Dockerfiles multi-stage
- [ ] Helm charts por serviço
- [ ] Probes, HPA, NetworkPolicy

## Fase 7: Terraform + AWS
- [ ] Módulos `network` e `eks` (com IRSA)
- [ ] MSK, RDS, ElastiCache, ECR
- [ ] VPN edge ↔ VPC ([[Conexao Edge-Nuvem]])
- [ ] Estado remoto em S3

## Fase 8: hardening
- [ ] OIDC, mTLS, Secrets Manager ([[Seguranca]])
- [ ] Pipelines CI/CD e GitOps ([[CICD e GitOps]])
- [ ] Políticas de retenção ([[Retencao de Dados]])
