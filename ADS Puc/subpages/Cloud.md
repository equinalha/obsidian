---
base: "[[ADS - PUC-PR.base]]"
Reviewed: false
Created: 2024-05-27T20:39:00
Status: Not started
Description: ""
---
# Datacenter

## Tipos de redudância

### **ANSI/TIA/EIA-942**

| Classificação | Descrição |
| --- | --- |
| N | Sem redundância |
| N+1 | Uma redundância |
| N+2 | Duas redundâncias |
| 2N | Redundância Completa |
| 2(N+1) | Todos os equipamentos apresentam redundância extra |

## Classificação (Tier)

| Nível | Descrição | Disponibilidade | Redundância |
| --- | --- | --- | --- |
| Tier 1 | Básico | 99,671 | N |
| Tier 2 | Componentes Redundantes | 99.749 | N+1 (Parcial) |
| Tier 3 | Sistema Autossustentado | 99.982 | N+1 (Todos os sistemas) |
| Tier 4 | Alta Tolerância a falhas | 99.995 | 2(N+1) |

## Áreas

| Sigla | Descrição | Detalhes |
| --- | --- | --- |
| **EDA** | Equipament Distribution Area | Onde localizam-se os racks e equipamentos |
| **ER** | Entrance Room | Interligação com a rede de telecomunicações |
| **HDA** | Horizontal Distribution Area | Área reservada para switches LAN, SAN e KVM |
| **MDA** | Main Distribution Area | Onde fica o backbone, roteadores e cabeamento principal |
| **ZDA** | Zona Distribution Area | Setor opcional. Divisão entre áreas de distribuição horizontal e de equipamentos |

![[ADS Puc/images/Untitled.png]]

# Computação em Nuvem

## Nuvem Privada

é o modelo no qual a infraestrutura de nuvem é utilizada exclusivamente por uma organização, sendo física na empresa ou remota, não deixando de ser administrada pela própria organização.

## Nuvem Pública

nele a infraestrutura é disponibilizada para o grande público, sendo acessada por qualquer usuário que conheça a localização do serviço.

## Nuvem Comunitária

agrupa uma comunidade que tenha afinidade ou interesses em comum.

## Nuvem híbrida

fornece uma infraestrutura composta de uma ou mais nuvens, que podem ser do tipo privada, pública ou comunidade e que continuam a ser entidades únicas, porém conectadas por meio e tecnologia própria ou padronizada que permite o acesso de dados e aplicações.

# Virtualização

## Virtualização Total

O sistema convidado não tem acesso direto ao hardware. Toda chamada é interceptada pelo hypervisor.

![[ADS Puc/images/Untitled 1.png]]

## Paravirtualização

O sistema convidado é modificado de forma que consegue ter acesso controlado ao hardware. Possui melhor desempenho que a virtualização total.

![[ADS Puc/images/Untitled 2.png]]