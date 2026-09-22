---
tags: [infra, kubernetes, docker]
tipo: infra
status: planejado
---

# Kubernetes e Docker

## Docker
- **Multi-stage build** em todos os serviços.
- Go: binário estático em imagem mínima (distroless/scratch).
- Java: JRE enxuto, jar em camadas para cache.
- Imagens no **ECR** ([[AWS Mapeamento]]).

## Kubernetes (EKS na AWS)
- Namespaces sugeridos: `apps`, `data` (ex.: [[Neo4j]]), `observability`.
- Por serviço: `Deployment`, `Service`, `HPA`, *liveness/readiness probes*, *resource requests/limits*.
- Configuração em `ConfigMap`; segredos via Secrets Manager ([[Seguranca]]).
- Um **Helm chart** por serviço.
- `NetworkPolicy` para restringir tráfego entre namespaces.
- Neo4j como `StatefulSet` com volume persistente.

## Ambiente local
`docker compose` para a Fase 0 e `kind`/`minikube` para testar manifests antes da AWS ([[Roadmap]]).

## O que roda no cluster
[[production-service]] · [[quality-service]] · [[traceability-service]] · [[notifier-service]] · stack de [[Observabilidade]] · [[Neo4j]]

## Relacionado
[[Terraform]] (cria o cluster) · [[CICD e GitOps]] (faz o deploy)
