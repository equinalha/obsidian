---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2025-04-11T12:14:00
Owner:
  - Eduardo Quinalha
---
# Resumo

![[20230319_153649.jpg]]

# O que é?

- Conjunto de recursos virtuais de fácil utilização e configuráveis, rapidamente alocados e liberados
	- Hardware
	- Software
	- Desenvolvimento e serviços
- Dinamicamente reconfigurados
- Otimização de recursos
- Uso de virtualização
- Larga escala
- Uso elástico de recursos
- Pay per use
- Para ser considerado nuvem deve atender (De acordo com a NIST):
	- amplo acesso à rede; 
	- autoatendimento sob demanda; 
	- agrupamento de recursos; 
	- rápida elasticidade; 
	- e serviço medido

# Camadas

- **Applications**
	- O usuário é responsável por desenvolver, implantar e manter seus próprios aplicativos e serviços.
- **Data**
	- O usuário é responsável pelo gerenciamento e segurança de seus dados, incluindo backups e políticas de retenção.
- **Runtime (Ambiente de Execução): **
	- Isso se refere à configuração e ao gerenciamento das instâncias de máquinas virtuais ou contêineres em que os aplicativos são executados. 
	- O usuário geralmente é responsável por configurar e gerenciar esses ambientes de execução.
- **Middleware**
	- Meio, o que está entre o SO e a Aplicação
	- O usuário é responsável pela configuração e gerenciamento do middleware necessário para seus aplicativos, como servidores web, bancos de dados e sistemas de mensagens.
- **OS** 
	- O usuário é responsável pela instalação, configuração e manutenção do sistema operacional nas máquinas virtuais ou instâncias.
- **Storage**
	- O provedor gerencia a infraestrutura de armazenamento, garantindo que os dados sejam armazenados com segurança e disponibilidade.
	- Isso inclui armazenamento em bloco, armazenamento de objetos e outros tipos de armazenamento.
- **Virtualization**
	- O provedor gerencia a virtualização da infraestrutura, permitindo que os usuários provisionem máquinas virtuais e recursos de computação de acordo com suas necessidades.

# Atores

- Consumidor
- Provedor
- Auditor
- Agente
- Operador

# Modelos de Serviços

![[Untitled 533.png]]

## SaaS

- Software pronto
- Aplicação final
- **O provedor controle e gerencia:**
	- Rede
	- Sistemas Operacionais
	- Servidores de armazenamento
- Exemplo: google apps

## PaaS

- Oferecido para o **desenvolvedor** de aplicações
- Oferece computação, armazenamento e comunicação para as aplicações
- Framework
- Exemplo:
	- Heroku
	- Azure
	- Kubernetes Engine

## IaaS

- Oferece infraestrutura de processamento, armazenamento, rede, de forma transparente
- Usa** virtualização**
- O usuário tem controle sobre:
	- Sistema Operacional
	- Armazenamento
	- Aplicações
	- Recursos de Rede
- Tipos de precificação
	- Estática → Preço determinado de forma fixa em função do tempo estimado de uso
	- Dinâmica → Pay per use

## CaaS

- Container as a Service

## FaaS

- Function as a Service

# Modelos de Implantação

- Privada
	- Operada e gerenciada pelo cliente (quase sempre)
	- Serviços utilizados internamente pela organização
	- Não disponibilizada para o público em geral
	- O uso do hardware que roda a infraestrutura não é compartilhado
	- Configurada pela TI da empresa
	- Níveis rigorosos de segurança e garantia de disponibilidade
	- Pode ser “On Premises” ou externa
> *“A infraestrutura de nuvem é provisionada para uso exclusivo por uma única organização compreendendo vários consumidores (por exemplo, unidades de negócios). Pode ser propriedade, gerida e operada pela organização, um terceiro, ou alguma combinação deles, e pode existir dentro ou fora das instalações. ”*

> [!note] 🔥
> Esta é a definição formal, do **NIST**, dada no documento **800-145**
- Pública
	- Disponibilizada publicamente
	- Modelo pay per use
	- Provedor de serviço gerencia a infraestrutura
> *“A infraestrutura de nuvem é provisionada para uso aberto pelo público em geral. Pode ser de propriedade, gerenciada e operada por uma organização empresarial, acadêmica ou governamental, ou alguma combinação deles. Ele existe nas instalações do provedor de nuvem. ”*

> [!note] 🔥
> NIST
- Comunitária
	- Empresas com objetivos em comum
	- Nuvens privadas compartilhada entre organizações definidas
	- Exemplo: SERPRO que fornece serviços em nuvem para órgãos do governo
> *A infraestrutura em nuvem é provisionada para uso exclusivo por uma comunidade de consumidores de organizações que compartilham preocupações (por exemplo, missão, requisitos de segurança, política e considerações de conformidade). Pode ser de propriedade, gerenciada e operada por uma ou mais organizações da comunidade, uma entidade externa ou terceira, ou alguma combinação deles, e pode existir dentro ou fora das instalações.*
- Híbrida
	- Uso de duas ou mais estratégias de implantação
	- Exemplo: 
		- Nuvem privada para funções internas da corporação
		- Nuvem pública para os serviços ou aplicações disponibilizadas ao público
> *A infraestrutura de nuvem é uma composição de duas ou mais tipos de nuvens distintas (privadas, comunitárias ou públicas) que permanecem como entidades únicas, mas estão vinculadas por tecnologia padronizada ou proprietária que permite que dados e aplicativos sejam portados (por exemplo, grande volume de dados em nuvem para balanceamento de carga entre nuvens).*
- Multi Cloud
	- Uso de várias nuvens públicas
	- Permite combinar as melhores características de cada
	- Permite maior descentralização, mantendo o serviço operando mais próximo de regiões de interesse

![[20230722_041852.jpg]]

# Tipos de Migração

> [!note] 🔥
> Nomenclatura de acordo com a Google Cloud

- **Lift-and-shift**
	- Pouca ou nenhuma modificação na aplicação
	- Não há grandes benefícios na mudança, considerando escalabilidade, preços, elasticidade e serviços gerenciados
- **Improve-and-move**
	- Ocorre modernização durante a migração
	- As cargas de trabalho são otimizadas para uso dos recursos em nuvem
- **Rip-and-replace**
	- Descontinuação total da aplicação e reescrita de uma nova
	- Aproveitamento máximo dos recursos da nuvem

> [!note] 🔥
> Outra nomenclatura:

<!-- Failed to import synced block: Could not find block with ID: 48e2d449-1ab9-442c-9eec-bed127292a5f. Make sure the relevant pages and databases are shared with your integration "Obsidian". -->

# Servless

Provê independência e abstração no processo de provisionamento e gerenciamento de servidores. Na prática, pode-se implantar aplicações sem a necessidade de se gerenciar um servidor web.

# NIST SP 800-145

## Definição de Nuvem

> [!note] 🔥
> Modelo que habilita **acesso sob-demanda via rede** a um **pool compartilhado de recursos computacionais configuráveis** que podem ser **provisionados e liberados rapidamente**, com mínimo esforço de gerenciamento ou interação com o provedor de serviços

## Características Essenciais

- **Self Service sob demanda**
	- O usuário pode provisionar unilateralmente as capacidades computacionais sem precisar de interação humana com o provedor
- **Amplo acesso a rede**
	- Deve estar acessível via rede e possibilitar ser acessado por mecanismos padrões e heterogêneos como computadores, tablets e smartphones
- **Pool de recursos**
	- Os recursos computacionais são disponibilizados em pools para múltiplos clientes
	- Provê um senso de independência de localização
	- O usuário não tem controle da localização exata dos recursos provisionados, mas pode ter controle sob um aspecto mais amplo como país, estado ou datacenter
- **Elasticidade rápida**
	- Os recursos são provisionados e liberados de forma elástica e podem ser escalados rapidamente para responder à demanda
- **Medição**
	- Controle e automatização dos recursos por meio de capacidade de medição
	- Os uso dos recursos deve ser monitorados, controlados e reportados de forma transparente

## Modelos de Serviços

- **SaaS**
	- Provê acesso à aplicações rodando em infraestrutura de nuvem
	- Acessíveis por múltiplos tipos de dispositivos
- **PaaS**
	- Provê a capacidade de implantar aplicações do usuário em ambiente de nuvem
- **IaaS**
	- Capacidade de provisionar recursos de infraestrutura em nuvem

## Modelos de Implantação

- **Nuvem Privada**
	- Infraestrutura em nuvem provisionada para uso exclusivo por uma única organização
- **Nuvem Comunitária**
	- Infraestrutura provisionada para o uso exclusivo de uma única comunidade de usuários ou corporações que tenham interesses compartilhados
- **Nuvem Publica**
	- Infraestrutura provisionada para uso geral
- **Nuvem Híbrida**
	- Composição de 2 ou mais infraestruturas em nuvem

## Atores

[https://www.nist.gov/system/files/documents/itl/cloud/NIST_SP-500-291_Version-2_2013_June18_FINAL.pdf](https://www.nist.gov/system/files/documents/itl/cloud/NIST_SP-500-291_Version-2_2013_June18_FINAL.pdf)

- O NIST define 5 principais atores na arquitetura de referência
	- **Cloud Consumer**
		- Usuário, consumidor
	- **Cloud Provider**
		- Provedor
	- **Cloud Broker**
		- Gerencia o uso, performance e entrega
		- Negocia relação entre o provedor e o consumidor
	- **Cloud Auditor**
		- Conduz testes e certificações a respeito do serviço prestado
	- **Cloud Carrier**
		- Provê a conectividade entre a nuvem e o consumidor

![[image 120.png]]

# Níveis de Redundância

## Nível 1

- Redundância de Hardware
- Uso de:
	- Armazenamento redundante, por exemplo, RAID
	- Múltiplos dispositivos de rede
	- Servidores em Cluster

## Nível 2

- Redundância de Rede
- Garante que a conectividade seja mantida mesmo em caso de falha
- Uso de:
	- Múltiplos links de comunicação (múltiplos ISP)
	- Balanceamento de carga
	- VPNs redundantes e failover

## Nível 3

- Redundância de Zona de Disponibilidade
- Zonas de disponibilidade são data centers fisicamente separados, mas conectados com baixa latência
- Visa proteger quanto a falhas em uma localização geográfica específica ou uma zona de disponibilidade dentro de um data center

## Nível 4

- Redundância geográfica (regiões de nuvem)
- Visa proteger contra desastres naturais ou grandes interrupções em uma área geográfica
- Envolve replicação de dados e serviços entre regiões

## Nível 5

- Redundância de aplicações e dados
- Visa garantir a continuidade das aplicações e integridade dos dados
- Inclui replicação dos dados entre diferentes bancos ou instâncias de armazenamento
- Estratégias de failover de aplicação entre servidores:
	- Replicação ativa-ativa
	- Replicação ativa-passiva
