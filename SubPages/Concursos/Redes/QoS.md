---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2024-10-09T14:35:00
Owner:
  - Eduardo Quinalha
---
# QoS

- Busca agregar qualidade nas transmissões de sinais em redes
- Coleção de tecnologias ou serviços
- Busca maior previsibilidade
- Conceitos
	- **Jitter ou flutuação: Atraso variável**
		- Variação da latência
		- Pode ser melhorado com o uso de buffer
	- Latência: Atraso constante
- Permeia diversos contextos e camadas da arquitetura TCP/IP
	- ATM, 802.1q, 802.1p e MPLS
	- IPv4 e IPv6
		- ToS/DS no IPv4
	- TCP, UDP e SCTP
	- Entre outros…
	- Exemplo:
		- 802.1q → VLAN, implementa o 802.1p → QoS 3bits presentes no cabeçalho
- Técnicas disponíveis
	- Armazenamento em buffer
		- Acontece tanto no emissor quanto no receptor
		- Suaviza o jitter
		- Aumenta a latência
		- Aumenta a confiabilidade
		- Não altera a largura de banda
	- Redução da burocracia e overhead da rede → Uso do UDP
	- Priorização de tráfego com marcação de pacotes
	- Otimização do meio de transmissão e redução da concorrência
	- Reserva de recursos e serviços diferenciados específicos
	- Implementação de técnicas variadas na arquitetura TCP/IP

# Modelos de QoS

## **INTSERV - Serviços Integrados**

- Reserva de recursos para necessidades e aplicações críticas
- Ex: ATM e circuitos virtuiais ou dedicados
- **RSVP - Resource reservation protocol**
	- Negociação e sinalização entre nós finais e intermediários
	- Permite a negociação de reserva de banda entre os roteadores que vão participar da transmissão dos pacotes
- Utiliza o campo tipo de serviço do cabeçalho IP com o número de protocolo 46 - INTSERV
- Mensagens do tipo PATH
	- T-Spec (características) → IDA
	- P-Hop → Nó anterior aceitou as especificações
- Mensagens RESV - Confirmação da reserva a partir do receptor → VOLTA
	- N-Hop → Nó anterior aceitou as especificações

![[image 119.png]]

## **DIFFSERV - Serviços Diferenciados**

- Foco na categorização de tráfego e não para um fluxo específico
- Não depende de protocolos específicos ou implementações mais robustas
- Utiliza o campo **ToS** ou DS do pacote IP
- Utiliza 6 bits (DSCP) dos 8 bits do campo DS do cabeçalho IPv4
	- Especificam até 64 classes disponíveis, porém o uso mais comum é baseado nas seguintes classes pré-definidas - per-hop behaviors (PHB):
		- Default Forwarding (DF) - Baseado no melhor esforço
		- Expedited Forwarding (EF) - Tráfego de baixa perda e baixa latência
		- Voice Admit (VA) - Tem os mesmas características do EF, porém também prioriza o tráfego usando protocolos de controle
		- Assured Forwarding (AF) - Garantia de entrega, dentro de condições pré-determinadas
			- Assegura o encaminhamento, desde que não exceda alguma taxa de limite
			- O tráfego que exceder tal limite, terá grande probabilidade de ser descartado
			- Define 4 classes, com 3 níveis de precedência cada, onde o nível mais alto significa maior quantidade de pacotes descartados
			- Dá-se nomes iniciando com AFXX onde o primeiro X é a classe e o segundo é a precedência.
				- Vai de AF11 até AF43
				- AF11 → Menos descartes
				- AF43 → Mais descartes
		- Class Selector (CS) - Mantém compatibilidade com o campo QoS das versões anteriores do IPv4
			- Usa 8 tipos de tráfego (3 bits), de acordo com a regra antiga de QoS do IPv4
				- 000 (CS1) - Padrão (DF)
				- 001 (CS2) - Baixa prioridade. Transferência de arquivos (FTP, SMB)
				- 010 (CS3) - Operações de controle de rede - SNMP, ICMP, SSH
				- 011 (CS4) - Broadcast vídeo
				- 100 (CS5) - Real-time - Jogos, videoconferência
				- 101 (CS6) - Peer-to-peer (SIP, H.323, H.248), NTP
				- 110 (CS7) - Protocolos de roteamento
				- 111 (CS8) - Reservado para uso futuro
- **Resumão**:
	- DF - Default = CS1
	- EF - Baixa latência. VOiP
	- VA - Controle
	- AF - Entrega garantida
		- AF11 - Mais prioritário - Menos descartes
		- AF43 - Mais descartes permitidos
	- CS - Mantém compatibilidade com o campo QoS das versões anteriores do IPv4

# Mecanismos de Escalonamento

## FIFO

- First Come/First Served (FCFS)

## Enfileiramento Prioritário

- Uso de múltiplas filas
- Diferentes categorias
- Pode ocorrer o fenômeno de **starvation**

## Enfileiramento Justo Ponderado (WQF) e Varredura Cíclica

- Objetiva eliminar o starvation
- Alternância entre filas
- No caso do WQF é estipulado pesos diferentes para cada fila

# Regulação de Tráfego

- Técnicas que buscam garantir: 
	- taxas médias estáveis (perspectiva de tempo longa)
	- taxas de pico limites (perspectiva de tempo curta)
	- tamanhos de rajada

## Leaky Bucket

- A partir de um fluxo descontrolado e não regulado, busca-se gerar uma saída de fluxo constante.
- Buffer que armazena um fluxo irregular e fornece uma saída regular (capacitância)
- Similar a um balde furado
- Quando o buffer está cheio, **novos pacotes são descartados**

## Token Bucket

- Foca na geração de tráfegos em rajada
- Tokens no dispositivo determinam por quanto tempo poderá haver uma transmissão de pacotes
- Cria-se diversos segmentos de fluxos bem definidos, caracterizando assim o tráfego em rajada
- Quando um dispositivo obtém um token, ele pode gerar o tráfego que ele puder durante um determinado tempo.
- Quando o balde enche, tem-se o **descarte de símbolos** e não de pacotes, isto é, tem-se **perda de taxa ou capacidade de transmissão.**

# Políticas de Transmissão

- RFC 2544 - Benchmarking Methodology for Network Interconnect Devices (Mais Generalista)
	- Descreve testes e características de desempenho de dispositivos de interconexão de rede
	- Define características e conceitos das variáveis de QoS
		- Taxa de transferência: Taxa máxima de bits que um dispositivo pode processar sem perda de quadros
		- Latência: Maior tempo necessário opara um quadro atravessar o dispositivo
		- Perda de quadros: Porcentagem de quadros descartados pelo dispositivo durante períodos de congestionamento
	- Testes
		- Teste Back to Back: medir a capacidade do dispositivo de lidar com rajadas consecutivas
		- Teste de estresse e recuperação: Resiliência e capacidade de recuperação após falhas
		- Relatórios de teste
	- Metodologia
		- Envio de quadros de tamanhos variados - 64, 128, 256, 512, 1021, 1280 e 1516 bytes
- RFC - 2889 - Benchmarking Methodology for LAN Shwitching Devices (Mais específica)
	- Switches Ethernet
	- Foco na sub-camada MAC
	- Testes aplicados a diferentes tipos de tráfego: unicast, multicast, broadcast
	- Mesmos testes da 2544 com um adicional:
		- Teste de aprendizagem de endereços: avaliar a capacidade do dispositivo de aprender e armazenar os endereços MAC (ARP)
	- Testes
		- Testes de Multicast e Broadcast
		- Testes de estresse e recuperação
			- Inclui testes de buffer overflow e queda de energia
		- Relatórios de teste

# HSRP e VRRP

1. **HSRP (Hot Standby Router Protocol)**:
	- HSRP é um protocolo proprietário da Cisco.
	- Permite que dois ou mais roteadores trabalhem juntos em uma configuração de redundância, mas apenas um deles é o ativo (rota principal) enquanto os outros estão em standby.
	- Um dos roteadores é eleito como o roteador ativo e é responsável por encaminhar o tráfego para a rede.
	- Os outros roteadores estão em standby, prontos para assumir a função de roteador ativo se o roteador principal falhar.
	- HSRP usa um endereço IP virtual (VIP) que é associado ao roteador ativo. Os dispositivos na rede usam esse VIP como o gateway padrão.
	- A transição de um roteador standby para ativo geralmente envolve um pequeno tempo de inatividade.
2. **VRRP (Virtual Router Redundancy Protocol)**:
	- VRRP é um padrão definido na RFC 3768 e é suportado por uma variedade de fabricantes de equipamentos de rede.
	- Funciona de maneira semelhante ao HSRP, onde vários roteadores trabalham juntos para fornecer redundância, mas apenas um é o roteador ativo.
	- Como o HSRP, o VRRP também usa um endereço IP virtual (VIP) que é compartilhado entre os roteadores. Esse endereço é usado como o gateway padrão pelos dispositivos na rede.
	- A principal diferença em relação ao HSRP é que o VRRP é um protocolo de código aberto, o que significa que não é restrito a dispositivos de uma única empresa.

Ambos os protocolos, HSRP e VRRP, desempenham um papel importante na melhoria da QoS ao fornecer alta disponibilidade de roteamento. Eles garantem que, se um roteador principal falhar, a rede ainda seja capaz de encaminhar o tráfego, minimizando assim a interrupção dos serviços de rede e melhorando a confiabilidade. A escolha entre HSRP e VRRP muitas vezes depende das preferências e das tecnologias de rede utilizadas em uma organização.

# QoS no IPv6

- O cabeçalho IPv6 inclui o campo "Classe de Tráfego" (Traffic Class) e o campo "Fluxo de Rótulo" (Flow Label) para ajudar na implementação do QoS.
- O campo Classe de Tráfego é semelhante ao campo Tipo de Serviço (TOS) do IPv4 e pode ser usado para especificar a prioridade de tráfego.
- O campo Fluxo de Rótulo permite que os pacotes sejam associados a um fluxo específico, facilitando a aplicação de políticas de QoS a um conjunto específico de pacotes.
- O IPv6 inclui mecanismos para gerenciamento de congestionamento, como o uso de pacotes de controle ICMPv6 para sinalizar congestionamento na rede e solicitar a redução da taxa de transmissão por parte dos emissores.
- O IPv6 suporta várias técnicas de controle de tráfego, como Controle de Admissão de Fluxo (Flow Admission Control) e Limitação de Taxa (Rate Limiting), para evitar que o tráfego excessivo cause congestão na rede.
- O IPv6 é compatível com a arquitetura DiffServ, que permite a marcação e o tratamento diferenciado de pacotes com base em seu nível de serviço.