---
tags: [infra, seguranca]
tipo: infra
status: planejado
---

# Segurança

Lacuna da arquitetura original ([[Revisao da Arquitetura Original]], item 7).

## Camadas
- **Autenticação/autorização de usuários**: OIDC (Keycloak ou Cognito).
- **Edge ↔ nuvem**: mTLS + VPN ([[Conexao Edge-Nuvem]]).
- **Serviço ↔ AWS**: **IRSA** (permissões mínimas por pod), sem chaves fixas.
- **Segredos**: Secrets Manager (ou Vault).
- **Rede**: `NetworkPolicy` no Kubernetes, subnets privadas, security groups restritivos.
- **Kafka**: autenticação IAM ou mTLS e ACLs por tópico.
- **Imagens**: varredura de vulnerabilidades no ECR.

## Relacionado
[[Kubernetes e Docker]] · [[Terraform]] · [[AWS Mapeamento]] · [[Go Edge Agent]]
