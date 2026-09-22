---
tags: [adr, decisao]
tipo: adr
status: aceita
---

# ADR-005: Terraform para provisionar a AWS

**Status:** aceita

## Contexto
A infraestrutura precisa ser reproduzível e versionada.

## Decisão
Usar [[Terraform]] com módulos (network, eks, msk, rds, elasticache, ecr, iam) e estado remoto em S3. Deploy de aplicações via Helm + GitOps, separado.

## Consequências
- Ambientes reproduzíveis.
- Custos exigem disciplina (`destroy` em dev).
- Separação clara entre infra e aplicação ([[CICD e GitOps]]).

## Alternativas consideradas
- CloudFormation/CDK: nativos AWS, menos portáveis.
- Criação manual: não reproduzível.

## Relacionado
[[AWS Mapeamento]] · [[Kubernetes e Docker]]
