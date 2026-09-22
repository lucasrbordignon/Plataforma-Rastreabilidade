---
tags: [infra, seguranca, edge]
tipo: infra
status: planejado
---

# Conexão edge → nuvem

O [[Go Edge Agent]] roda fora da AWS. O link é um ponto sensível.

| Opção | Prós | Contras |
|---|---|---|
| **Site-to-Site VPN + mTLS** | Tráfego privado, bom padrão | Mais configuração |
| **Direct Connect** | Estável, baixa latência | Custo e prazo (produção) |
| **MSK público com TLS + autenticação** | Simples | Maior superfície de ataque |
| **Gateway de ingestão (HTTP/gRPC) na frente do Kafka** | Edge não precisa falar Kafka; controle central | Mais um componente |

## Recomendação inicial
VPN + mTLS, com o edge falando direto com o [[Kafka]]. Reavaliar o gateway de ingestão se surgirem muitos edges ou restrições de rede ([[Perguntas em Aberto]]).

## Resiliência
Buffer local no edge cobre quedas de rede. Definir o comportamento offline prolongado.

## Relacionado
[[Seguranca]] · [[AWS Mapeamento]] · [[Terraform]]
