---
tags: [componente, java, servico]
tipo: componente
status: planejado
linguagem: Java
---

# quality-service

Java + Spring Boot, [[Arquitetura Hexagonal|hexagonal]].

## Responsabilidades
- Registrar **inspeções de qualidade** e resultados.
- Guardar evidências (imagens, laudos) em objeto (S3, ver [[AWS Mapeamento]]).
- Publicar `quality.inspection` via [[Outbox Pattern]].
- Reprovações relevantes disparam o [[notifier-service]].

## Dados
Tabelas de inspeção em [[PostgreSQL]] ([[Modelo Relacional]]).

## Relacionado
[[Fluxo Principal]] (etapa 4) · [[Kafka]] · [[Catalogo de Eventos]]
