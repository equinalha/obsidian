---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2024-11-17T10:16:00
Owner:
  - Eduardo Quinalha
---
# Projeto e Dimensionamento

- Tecnologias de consolidação:
	- Virtualização
	- Poder de processamento
- A meda que estas tecnologias evoluem, datacenteres passaram a ser dimensionados pelo consumo de energia elétrica

[https://www.techtarget.com/searchdatacenter/feature/What-you-should-consider-when-right-sizing-a-data-center](https://www.techtarget.com/searchdatacenter/feature/What-you-should-consider-when-right-sizing-a-data-center)

[https://zeittec.com.br/construcao-de-data-center/](https://zeittec.com.br/construcao-de-data-center/)

[https://www.tiespecialistas.com.br/compreendendo-os-requisitos-de-um-datacenter/](https://www.tiespecialistas.com.br/compreendendo-os-requisitos-de-um-datacenter/)

[https://prodest.es.gov.br/conheca-os-cinco-principais-tipos-de-data-center](https://prodest.es.gov.br/conheca-os-cinco-principais-tipos-de-data-center)

# Níveis de Redundância

## Nível N

- Mais básico
- Redundância praticamente inexistente

## Nível N+1

- Ao menos um equipamento extra disponível

## Nível N+2

- Dois equipamentos redundantes
- Backup do backup

## Nível 2N

- Toda a infraestrutura é duplicada
- Dois hardwares, alimentação elétrica de emergência, segundo link de dados

## Nível 2(N+1)

- Nível mais alto de redundância
- Cuidado extra para sistemas críticos
- Dobro da quantidade de equipamentos e um módulo extra para cada N

# Classificação TIER

## TIER I

- Critérios básicos de conformidade com as normas pertinentes
- Prevê climatização e subsistemas de energia elétrica
- **Não há redundância**
- Disponibilidade: 99,671%
- Downtime anual permitido: 28,8 horas

## TIER II

- Parcialmente redundante
- Adequado para pequenas empresas somente
- Disponibilidade: 99,749%
- Downtime anual permitido: 22,0 horas

## TIER III

- Totalmente redundante (2N)
- Disponibilidade: 99,982%
- Downtime anual permitido: 1,6 horas

## TIER IV

- Redundância robusta
- Mesmo diante de falhas, continua operando
- Adequado a grandes empresas
- Disponibilidade de 6 9’s (99,9999%)