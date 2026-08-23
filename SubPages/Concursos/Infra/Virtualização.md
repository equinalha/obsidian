---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2024-09-05T15:03:00
Owner:
  - Eduardo Quinalha
---
[https://edisciplinas.usp.br/pluginfile.php/5232618/mod_resource/content/1/105-Técnicas de virtualizacao-v13.pdf](https://edisciplinas.usp.br/pluginfile.php/5232618/mod_resource/content/1/105-T%C3%A9cnicas%20de%20virtualizacao-v13.pdf)

# Hypervisor

> [!tip] 💡
> Também conhecido como VMM (Virtual Machine Monitor) ou monitor de máquina virtual, o hypervisor é uma camada de software que permite a criação e a execução de múltiplas máquinas virtuais em um único hardware físico. Ele funciona como um intermediário entre o hardware subjacente e os sistemas operacionais convidados, gerenciando e coordenando o acesso aos recursos físicos do sistema, como CPU, memória, armazenamento e dispositivos de entrada/saída.

## Tipos

- **Hypervisors de tipo 1 (Bare-metal)**: são sistemas de virtualização que são instalados diretamente no hardware físico do servidor, sem a necessidade de um sistema operacional intermediário. Eles controlam o acesso e a alocação de recursos entre as máquinas virtuais. Características-chave dos hypervisors de tipo 1 incluem alta eficiência e desempenho, já que não há camada adicional de sistema operacional hospedeiro, e um menor nível de sobrecarga, resultando em melhor utilização dos recursos físicos.
- **Hypervisors de tipo 2 (Hosted):** são instalados e executados sobre um sistema operacional hospedeiro convencional. Eles funcionam como aplicativos dentro deste SO e criam uma camada adicional de abstração entre o hardware físico e as máquinas virtuais. Os hypervisors de tipo 2 são geralmente mais fáceis de instalar e configurar, mas podem introduzir uma sobrecarga adicional devido à camada do sistema operacional hospedeiro.

## Funcionamento

Arquiteturas de processadores modernos utilizam o conceito de níveis de proteção, ou modos de operação, que são um mecanismo de segurança para controlar o acesso aos recursos do sistema. Também conhecidos por anéis de proteção, eles definem diferentes níveis de privilégio para o acesso aos recursos do sistema, permitindo que o sistema operacional e os aplicativos executem tarefas com diferentes graus de autoridade.

![[hsbCTGvnCwrIU8wdMMH79gq1cA3FMN38liQJIx_Lpn4Mj4BSz-CgEhqbaEur_BaBfRKLvjFNiesPJXbASUjluOhgNpSmL-OrWjAiV4IO0hFgR1BNAw4BLbDdamSVsPIA9qRIiBaVzJBLi8ZfCs54DLA.png]]

Geralmente, os processadores atuais possuem quatro anéis de proteção, numerados de 0 a 3, sendo que o nível 0 é o mais privilegiado e o nível 3 é o menos privilegiado. No entanto, os sistemas operacionais tradicionais utilizam apenas dois desses anéis, definindo dois modos de operação:

- **Modo Usuário: **Em que o processador executa instruções de aplicativos de usuário, como programas e aplicativos. Neste modo, o acesso a recursos críticos do sistema é restrito para evitar que os programas interfiram no funcionamento do sistema operacional ou de outros aplicativos em execução.
- **Modo Kernel:** Neste modo, o processador executa o código do núcleo do sistema operacional, conhecido como kernel e dá acesso completo a todos os recursos do hardware, podendo executar instruções privilegiadas, como manipular interrupções de hardware, gerenciar a memória do sistema e controlar dispositivos de entrada e saída.

Os hypervisors do tipo 1 (bare metal) geralmente operam no anel de maior privilégio (anel 0), enquanto os sistemas operacionais convidados (guest OS) são executados em anéis de menor privilégio (anéis 1 a 3). Quando um sistema operacional convidado faz uma chamada de sistema, o hypervisor intercepta essa chamada e a encaminha para o hardware subjacente, gerenciando esse acesso ao hardware por meio de **hypercalls**.

# Tipos de Virtualização

- **Virtualização Total (Full Virtualization)**
	- O hipervisor cria uma camada de abstração completa entre o sistema operacional convidado (guest OS) e o hardware físico subjacente. 
	- Permite que o sistema operacional convidado seja executado sem modificações, como se estivesse sendo executado em hardware físico real. 
	- O hipervisor emula todos os componentes de hardware necessários e traduz as instruções do sistema operacional convidado para instruções compreensíveis pelo hardware físico.
- **Virtualização Assistida por Hardware (Hardware-Assisted Virtualization)**
	-  hardware físico do servidor fornece suporte específico para a execução de máquinas virtuais de forma mais eficiente.
	- Alcançado por meio de extensões de virtualização incorporadas nos processadores modernos, como Intel VT-x e AMD-V. 
	- Essas extensões permitem que o hipervisor execute operações de virtualização de forma mais direta e eficiente, reduzindo a sobrecarga de desempenho e melhorando o desempenho geral das máquinas virtuais. 
	- A virtualização assistida por hardware é comumente usada em ambientes de produção e é suportada por muitos hipervisors de tipo 1 e tipo 2.
- **Paravirtualização (Paravirtualization)**
	- O sistema operacional convidado é modificado para ser consciente de que está sendo executado em um ambiente virtualizado. 
	- O sistema operacional convidado não executa instruções diretamente no hardware físico, mas em chamadas de sistema otimizadas que são interceptadas pelo hipervisor e traduzidas para operações de hardware subjacentes. 
	- A paravirtualização geralmente oferece **melhor desempenho do que a virtualização total,** pois reduz a sobrecarga de virtualização.

# **Hypervisores na arquitetura X86**

Instruções privilegiadas são exclusividade do sistema operacional nativo. A arquitetura x86 provê 4 modos de operação do processador, cada qual com níveis de privilégios diferente. Estes níveis (rings) são de ring 0 a ring 3, sendo ring 0 com maior privilégio e ring 3 com menor privilégio.

Os sistemas operacionais comuns, como Windows e Linux, utilizam somente os níveis 0 (modo kernel) e 3 (modo usuário). O que a VMWare fez, foi transportar o hypervisor para o ring 0, enquanto que o SO roda agora em um nível intermediário entre 0 e 3.
	- **Virtualização total (completa)**
		- Baseada em translação binária e execução direta
		- O SO já permite nativamente a virtualização (desde que tenha a aplicação de VM instalada)
		- Facilita a migração de VM’s entre servidores físicos (live migration)
		- Desempenho prejudicado
		- Usa técnicas de translação binária e execução direta
		- Utilizado por aplicações de virtualização hosted como
			- Virtual Box
			- VMWare
	- **Paravirtualização (Assistida pelo SO)**
		- virtualização assistida pelo SO
		- Torna-se necessário a modificação do SO** convidado** para permitir a virtualização
		- **Hypercall: **O SO convidado é alterado de forma a chamar o hypervisor sempre que executar uma instrução que possa alterar o estado do sistema (Instruções privilegiadas)
		- Normalmente consiste em instalação de drivers específicos
		- Tendem a ser mais rápidos
		- Exemplo: Xen Open Source
	- **Virtualização assistida pelo hardware**
		- O próprio hardware dispõe de recursos de virtualização
		- Melhor desempenho
		- Equiparou-se ao desempenho da paravirtualização
		- Exemplos
			- Intel VT
			- AMD-V

# Segurança

- **Agent**
	- Em um ambiente de virtualização, é comum empregar técnicas de segurança para isolar máquinas virtuais e protegê-las de ameaças como códigos maliciosos. 
	- Uma estratégia comum é a utilização de **agentes de segurança**, que são softwares instalados em cada máquina virtual para realizar tarefas como antivírus e detecção de intrusão.
	- No entanto, essa estratégia pode causar um consumo adicional de recursos, pois cada máquina virtual precisa rodar seu próprio agente. 
- **Agentless**
	- Em contrapartida, a abordagem *agentless* busca minimizar o uso de recursos ao centralizar a proteção de segurança no nível do hypervisor ou host, em vez de dentro de cada máquina virtual individualmente.
	- Isso significa que não são instalados agentes em cada máquina virtual, economizando recursos de CPU, memória e armazenamento.