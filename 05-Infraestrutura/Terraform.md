---
tags: [infra, terraform, aws]
tipo: infra
status: planejado
---

# Terraform

Provisiona a infraestrutura na AWS. **Não muda** a arquitetura lógica, só cria a base onde ela roda. Ver [[ADR-005 Terraform na AWS]].

## Estrutura sugerida
```
infra/
├── modules/
│   ├── network/        # VPC, subnets, NAT, VPN
│   ├── eks/            # cluster, node groups, IRSA
│   ├── msk/            # Kafka
│   ├── rds/            # PostgreSQL
│   ├── elasticache/    # Redis
│   ├── ecr/            # repositórios de imagem
│   └── iam/            # roles e policies
└── envs/
    ├── dev/            # main.tf, variables.tf, terraform.tfvars
    └── prod/
```

## Regras
- **Estado remoto** em S3 com locking, um estado por ambiente.
- Terraform cria a **infra**. Deploy de aplicações e da stack de [[Observabilidade]] fica com Helm + ArgoCD/Flux ([[CICD e GitOps]]). Não misturar.
- Ambiente `dev` pequeno; `terraform destroy` quando não estiver usando.

## Mapeamento
[[AWS Mapeamento]]

## Relacionado
[[Kubernetes e Docker]] · [[Seguranca]] · [[Roadmap]] (Fase 7)
