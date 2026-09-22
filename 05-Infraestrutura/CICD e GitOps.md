---
tags: [infra, cicd]
tipo: infra
status: planejado
---

# CI/CD e GitOps

Lacuna da arquitetura original ([[Revisao da Arquitetura Original]], item 9).

## Pipeline por serviço
1. Build e testes (incluindo testes de arquitetura, ver [[Arquitetura Hexagonal]]).
2. Build da imagem Docker e push para o ECR.
3. Varredura de vulnerabilidades.
4. Atualização do chart Helm/manifest no repositório de deploy.

## GitOps
ArgoCD ou Flux observam o repositório e aplicam no cluster ([[Kubernetes e Docker]]). Dashboards do [[Grafana]] também podem ser provisionados assim.

## Terraform
Pipeline separado: `plan` em PR, `apply` com aprovação ([[Terraform]]).

## Relacionado
[[Roadmap]] (Fase 8)
