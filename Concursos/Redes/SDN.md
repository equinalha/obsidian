---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2024-12-05T16:20:00
Owner:
  - Eduardo Quinalha
---
# Características

- Arquitetura de rede que se baseia em softwares e na programabilidade de um plano de controle centralizado, ágil, que recebe instruções de um controlador, independentemente de fornecedor.
- Separa o plano de controle e o plano de dados de modo transparente
- Possibilita minimizar os custos com roteadores e hardwares e passam a ter acesso a um modo facilitado de executar alterações de rede e uma automação de regras para a distribuição dos fluxos de dados.
- Nas estruturas de rede de computadores tradicionais, a configuração de cada um dos dispositivos se dá de maneira individual, visto que, geralmente, cada dispositivo tem a própria API, além de fabricantes diferentes.
- Em uma SDN, o controlador, que pode ser uma máquina virtual, por exemplo, gerencia os demais dispositivos alocados no plano de encaminhamento (ou plano de dados), alterando a dinâmica de um sistema distribuído (por exemplo, protocolos de roteamento, como RIP e OSPF) para um centralizado, o que permite que as alterações de rede sejam realizadas de forma rápida e eficiente.
![[Concursos/images/image 27.png]]
- **Plano de dados ou de encaminhamento:** 
	- composto pelos dispositivos de encaminhamento, principalmente switches.
	- Recebe instruções de um protocolo que permite a comunicação com o plano de controle.
- **Plano de controle:**
	- controlador que gerencia o plano de dados. 
	- Vai implementar toda a parte lógica do gerenciamento de dados, por meio de um protocolo de comunicação para redes definidas por software, como o OpenFlow, por exemplo.
- **Tabela de fluxos:** 
	- o plano de controle da SDN gerencia o tráfego de rede, por meio da tabela de fluxos estabelecida no plano de dados, a qual armazena três principais informações por linha: as de cabeçalho, as de contadores e as ações que são tomadas. 
	- Essa combinação de informações viabiliza que determinado pacote de dados seja processado e passado adiante ou reescrito. 
- Protocolos
	- Southbound
	- OpenFlow
