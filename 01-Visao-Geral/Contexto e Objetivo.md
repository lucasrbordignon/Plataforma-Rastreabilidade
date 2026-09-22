---
tags: [visao-geral]
tipo: contexto
status: planejado
---

# Contexto e objetivo

## Problema
Em uma fábrica, é preciso saber **de que matéria-prima veio** cada produto e **para onde foi** cada lote. Quando surge um defeito, é necessário localizar rapidamente todos os produtos e clientes afetados (**recall**).

## Objetivo da plataforma
- Coletar eventos do chão de fábrica em tempo real ([[Go Edge Agent]]).
- Transportar os eventos de forma confiável ([[Kafka]]).
- Processar regras de produção, qualidade e rastreabilidade ([[production-service]], [[quality-service]], [[traceability-service]]).
- Responder consultas de genealogia de lote ([[Modelo de Grafo]], [[Recall e Rastreio]]).
- Ter observabilidade de ponta a ponta ([[Observabilidade]]).
- Rodar em Kubernetes, provisionado por Terraform na AWS ([[Kubernetes e Docker]], [[Terraform]]).

## Fontes de dados do chão de fábrica
- Máquinas e PLCs (CNC, injetoras, esteiras, linhas de produção)
- Sensores (temperatura, pressão, vibração, contadores)
- Balanças e scanners (pesagem, leitores de código de barras / RFID)
- ERP local, CSV e APIs (sistemas legados)

## Princípios
- **Hexagonal** em cada serviço: domínio isolado de frameworks ([[Arquitetura Hexagonal]]).
- **Eventos como fonte da verdade**: o grafo e outras projeções podem ser reconstruídos por replay ([[Kafka]]).
- **Começar pequeno**: poucos serviços, evoluir depois ([[ADR-004 Comecar com poucos servicos]]).
- **Portável**: telemetria via OTLP ([[ADR-006 OpenTelemetry como padrao de telemetria]]).

## Origem deste vault
Nasceu de uma arquitetura inicial (ver [[Revisao da Arquitetura Original]]) que foi revisada e simplificada. O plano de execução está em [[Roadmap]].
