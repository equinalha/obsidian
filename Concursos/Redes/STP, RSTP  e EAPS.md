---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2024-12-05T16:20:00
Owner:
  - Eduardo Quinalha
---
> [!note] 🔥
> A prioridade de uma bridge (que representa um switch) no protocolo STP é ajustada em incrementos de 4096. Logo, a menor prioridade logo abaixo de 8192 é 4096

# STP (802.1d)

Spanning Tree Protocol

Visa resolver o probelma de loopings na rede

Transforma a estrutura física de malha em uma estrutura lógica de árvore (estrutura de dados). Sendo assim, sempre haverá um caminho único de um nó a outro (switches)

- Premissas
	- Bloqueio dinâmico de portas (switches)
	- Criação de um único caminho operacional
		- Redundância de caminhos físicos
		- Um único caminho lógico
		- Impede a ocorrência de broadcast Storm
![[Untitled 440.png]]
- Considerações
	- Rotas com menor número de saltos
	- Rotas com menor tráfego
	- Diferentes velocidades de enlaces
- Comunicação
	- Geração de BPDU’s - Bridge Protocol Data Unit
	- Possuem informações sobre:
		- Nó (switch)
		- Interface
		- Enlace
- Bridge ID
	- Estrutura de 8 bytes
![[STP, RSTP  e EAPS synced block]]
	- A Bridge ID é composta pelos valores de Bridge Priority e MAC Address
- Bridge Raiz
	- É eleita aquela que possuir o **menor** bridge ID, ou seja, a que possuir o **menor** Bridge Priority ou em caso de empate deste, o <u>**menor**</u> MAC Address
	- Servirá de base para a construção da árvore de comunicação (Será a raíz)
- Root Ports
	- Única por switch
	- Nos demais switches que não são ROOT
	- Interface de saída para a ROOT BRIDGE
	- Não necessariamente estará conectada diretamente ao switch raíz
	- Critérios
		- Será eleita Root Port a que tiver menor custo, considerando velocidade, modo de operação e quantidade de saltos
		- Modo forwarding
		- valores padrão:
			- 10 Gbps: 2
			- 1 Gbps: 4
			- 100 Mbps: 19
			- 10 Mbps: 100
		- Desempate
			- Bridge ID do sender
			- Prioidade da porta do sender
			- Menor ID da interface
- Designated Ports
	- Recebem quadros da rede para encaminhar para a root port
	- Modo forwarding
	- Todas as portas do switch raíz serão designated ports
- Alternate Port
	- **Possível substituta da Root Port**
- Backup Port
	- **Possível substituta da Designated Port**
- Demais portas
	- Modo blocking
	- Não aceitam o recebimento de pacotes

![[Untitled 442.png]]

- Estado das portas

![[Untitled 443.png]]

- Tempos de transição
	- Blocking → Listening: Até 20s
	- Listening → Learning: Até 15s
	- Learning → Forwarding: Até 15s
	- Tempo máximo de convergência: Até 50s

# RSTP (802.1w)

[https://www.cisco.com/c/pt_br/support/docs/lan-switching/spanning-tree-protocol/24062-146.html](https://www.cisco.com/c/pt_br/support/docs/lan-switching/spanning-tree-protocol/24062-146.html)

Rapid Spanning Tree

Resolve o problema de redes instáveis muito extensas (com muitos switches)

Reduz o número de estados das portas para apenas 3

- Forwarding
- Learning
- Discarding
	- Agrupa os estados de blocking, disabled e listening
- Portas de Ponta (Edge)
	- São as portas conectadas diretamente às estações finais (computadores e outros dispositivos)
	- Não são capazes de formar loops
	- Por isso, transitam diretamente ao estado de encaminhamento, pulando os estágios listening e learning

![[STP.png]]

# Ethernet Automatic Protection Switching (EAPS)

- Provê alta disponibilidade e redundância
- Redes LAN e MAN
- Trabalha com rotas redundântes
- Mantém todas as portas ativas
- Detecta falha na rede e redireciona o tráfego dinamicamente
- Detecção e restabelecimento de falhas rapidamente
- Evita loops
- Prioriza tráfegos
- Funciona principalmente em topologias do tipo anel

## EAPS vs STP

1. **Objetivo Principal**:
	- **EAPS:** O principal objetivo do EAPS é fornecer alta disponibilidade e recuperação rápida em redes Ethernet, especialmente em cenários de anéis ou topologias em anel. Ele se concentra em evitar a interrupção da comunicação de dados em caso de falhas na rede.
	- **STP:** O Spanning Tree Protocol (STP) é projetado para evitar loops em redes Ethernet com topologias redundantes, garantindo que apenas um caminho ativo esteja em uso a qualquer momento. O principal objetivo do STP é evitar loops, não necessariamente fornecer alta disponibilidade rápida.
2. **Tempo de Recuperação**:
	- **EAPS:** O EAPS é conhecido por seu tempo de recuperação rápido, muitas vezes na faixa de milissegundos. Isso é fundamental para redes que exigem recuperação quase instantânea em caso de falha.
	- **STP:** O STP não foi projetado para recuperação rápida. Ele pode levar vários segundos ou até minutos para detectar e resolver um loop na rede, o que pode resultar em tempo de inatividade percebido em aplicações sensíveis à latência.
3. **Topologias Suportadas**:
	- **EAPS:** O EAPS é frequentemente usado em topologias em anel, onde os dispositivos de rede estão conectados em um anel físico ou lógico. Ele permite que os pacotes fluam em ambas as direções, fornecendo redundância.
	- **STP:** O STP é usado para evitar loops em topologias de árvore, onde há múltiplos caminhos entre dispositivos. Ele desativa caminhos redundantes para evitar loops.
4. **Ativação de Portas**:
	- **EAPS:** O EAPS geralmente mantém todas as portas ativas e apenas ativa uma porta alternativa quando ocorre uma falha. Isso minimiza o tempo de inatividade.
	- **STP:** O STP desativa portas redundantes para evitar loops. Portas adicionais são ativadas apenas se a porta primária falhar.
5. **Aplicabilidade**:
	- **EAPS:** É mais comum em ambientes onde a recuperação rápida é crítica, como redes de telecomunicações, sistemas de monitoramento de segurança e outras aplicações de missão crítica.
	- **STP:** É mais amplamente utilizado em redes locais corporativas para evitar loops e garantir a integridade da rede, mas pode não ser adequado para ambientes que exigem recuperação rápida.

## Funcionamento

- Um anel é configurado como um domínio
- Cada domínio possui um único nó mestre (master node) e vários nós de transito (transit nodes)
- Cada nó possui duas portas habilitadas a enviar dados para o mestre (primária e secundária)
- Em condições normais, somente a primária fará o envio
- A porta secundária ficará bloqueada para qualquer tráfego que não o de controle
- Em caso de falha, os dispositivos que a detectarem enviarão um sinal de controle ao master que fará o desbloqueio da porta secundária e irá instruir os transit nodes a fazerem o mesmo
- Um mesmo switch poderá pertencer a múltiplos domínios (múltiplos anéis)
