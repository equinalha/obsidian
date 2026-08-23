---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2024-08-30T10:09:00
Owner:
  - Eduardo Quinalha
---
# Noções Gerais

- São estruturas em redes para armazenamento de dados
- Pode ser um equipamento ou uma infraestrutura de rede
- DAS  e NAS são equipamentos
- SAN é uma rede

# DAS - Direct Attached Storage

- Conectado a um computador (servidor)
- Não é possível o acesso direto ao storage
- Utiliza o SO do host
- **Algumas bancas consideram que um HD externo ou Pendrive pode ser um DAS, desde que compartilhado com a rede**
- acesso a nível de blocos
- Vantagens
	- Simplicidade
	- Baixo custo
- Desvantagens
	- Desempenho

![[Untitled 735.png]]

## NAS - Network Attached Storage

- Acesso direto ao dispositivo via rede
- Possui SO e filesystem próprio
	- Consequentemente tem CPU e memória
- **acesso a nível de arquivos e não blocos, como o DAS e SAN**
- Protocolos NFS e CIFS
- Vantasgens
	- Versatilidade de posicionamento físico na rede
	- Maior desempenho

![[DAS_e_NAS.png]]

# SAN - Storage Area Network

- Vantagens
	- Robustez
	- Segurança
	- Disponibilidade
	- Desempenho
- Desvantagens
	- Maior custo de investimento e manutenção
- **Acesso a nível de blocos**
- Isolamento de redes
- Rede de alta velocidade
- Processos de backup **LAN Free**
	- A transferência ocorre diretamente entre os dispositivos, sem concorrer com o tráfego da LAN

![[Untitled 736.png]]

- **Tecnologias**
	- Fiber Channel (fibra ótica)
	- iSCSI (par trançado)
- Portas TCP/86 e TCP/3260
- Identificadores IQN (iSCSI Qualified Name)

## Fibre Channel

- Arquitetura própria de comunicação

### 3 formas de conexão

- **Ponto a ponto (FC-P2P)**
	- Os dispositivos são conectados ponto a ponto entre si
- **Arbitrated Loop (FC-AL)**
	- Rede anel
- **Switched Fabric (FC-SW)**
	- Rede estrela, mesh ou hierárquica
	- Switches
		- Switch SAN ou Fabric
		- Utiliza-se técnica conhecida como Zoning
	- Identificação dos dispositivos
		- WWN → Semelhante ao MAC Address
			- Sub dividido em WWNN → World Wide Node Name
			- e WWPN → World Wide Port Name
	- Os Switches são agrupados em Zonas, equivalentes às VLAN’s
		- Soft Zoning
			- Mais simples e flexível
			- Menos segurança, menos controles
			- Dispositivos são associados às zonas de acordo com seus WWN’s
		- Hard Zoning
			- Segregação por portas do switch
- Essencialmente utiliza-se fibra ótica, mas é possível conexão elétrica também

![[Untitled 737.png]]

## Componentes SAN

- HBA - Host Bus Adapter
	- Similar a uma placa de rede
	- Controladoras acopladas aos servidores que farão acesso à FC
- Storage
	- Equipamento que contém o conjunto de discos
- Switches
	- Atuam na camada FC-2
	- Comunicação por meio de ISL
- Director Fiber Channel
	- Mais robustos que os switches
	- Maior tolerância a falhas
- HUBs
	- Muito similar ao hub ethernet
- Bridges
	- FC ↔ iSCSI
	- Interliga as duas tecnologias
	- Conversão de sinais e protocolos
	- Aproveitamento de dispositivos legados

## SAN - Multipathing

- Redundância de caminhos e formas de interconexão
- Multiplicidade de switches e hba’s
- Caso falhe um switch, não para a rede

## VSAN - Virtual SAN

- SAN’s virtuais a partir de um ou mais switches SAN
- Muito similar à VLAN
- Cada VSAN pode rodar sua própria pilha de protocolos
- Isolamento de tráfego

## ThinProvisioning

- Permite criar um em espaço virtual de armazenamento maior que a capacidade física
- Analogia à memória virtual

## Estrutura em camadas

- A pilha de protocolos da arquitetura SAN assemelha-se à pilha TCP/IP
- São 5 níveis
	- FC-4
		- Mapeia blocos de dados em PDU’s
		- Equivalente à camada de aplicação TCP/IP
		- **Camada de transporte**
		- responsável por promover a integração dos protocolos de nível superior, como, por exemplo, SCSI e FICON, com os protocolos das camadas inferiores.
		- FCP
	- FC-3
		- Camada de serviços gerais, protocolos auxiliares
		- Criptografia, recursos de segurança
		- Confiabilidade, RAID
			- Hunt Groups
			- Striping
			- Multicast → Transmissão para várias portas de destino
	- **FC-2 → Principal camada, equivale à camada de REDE**
		- Camada de rede
		- Switches estão nesta camada
		- **Definição do formato dos quadros**
		- Capacidade de zoneamento
		- Gestão de tráfego
		- Conexões ponto a ponto
		- Classes de serviço
	- FC-1
		- Codificação do sinal
		- Enlace de dados
		- Controle de erros
	- FC-0
		- Camada física
		- cabeamento, conectores
![[Untitled 738.png]]

## Protocolos

- FCP - Fiber Channel Protocol
	- Atua na FC-4 - Transporte
	- Análogo ao TCP
	- Nativo, não há necessidade de inserção de nenhum componente
	### Tipos de portas
	- N-Port
		- Conecta-se ao Switch FC
		- Pode ser um servidor ou dispositivo de armazenamento
	- F-Port
		- Porta do Switch Fabric
		- Conecta-se ao Nó
		- Conecta-se a uma N-Port
	- L-Port
		- Loop entre switches
		- Utilizado para Arbitraded Loop
	- E-Port
		- Portas de extensão
		- Cascata de switches
		- Expansão do número de portas do Switch
	- G-Port
		- Genérica
		- Pode operar como E-port ou F-port
		- Depende do que se conecta a ela
![[Untitled 739.png]]
- FCoE
	- Fiber Channel Over Ethernet
	- Encapsula as camadas FC-4, FC-3 e FC-2 em um quadro ethernet
	- Permite o uso de switches ethernet em uma rede SAN, substituindo os Switches Fabric que são mais caros
- FCIP
	- Fiber Channel Over IP
	- Troca de dados entre SANs distintas, interligadas por redes IP
	- Cria um Túnel SAN sobre uma rede IP
	- Apesar de o foco ser o IP, mas utiliza também o TCP para o tráfego da informação

## Visão em 3 camadas

- Host Layer
	- Servidores e demais componentes
- Fabric Layer
	- Dispositivos de conexão SAN
	- Cabos e Switches
- Storage Layer
	- Armazenamento
	- Mídias de armazenamento

![[Untitled 740.png]]

# iSCSI

iSCSI usa ethernet e TCP/IP como sua camada de transporte, possibilitando usar a infraestrutura ethernet da rede local existente em sua empresa.

A principal diferença entre usar storages Fibre Channel ao invés de sistemas iSCSI é a estrutura de transporte. Uma rede SAN baseada em FC exige sua própria infraestrutura de rede, pois não usa ethernet

- Utiliza par trançado
- Permite o uso da infra tradicional de rede

![[SAN.png]]

