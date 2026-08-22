---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2024-08-26T18:26:00
Owner:
  - Eduardo Quinalha
---
![[Untitled 502.png]]

- **Domínio de colisão**
	- Meio compartilhado, há concorrência
	- A banda disponível é compartilhada por todos
	- Necessita controle/detecção de colisão
	- Associado à topologia física
	- **Visibilidade até a segunda camada OSI**
- **Domínio de broadcast**
	- **Visibilidade até a terceira camada**
	- Associado à topologia lógica
	- Domínio lógico que identifica os dispositivos físicos da rede
	- Dentro de um mesmo domínio, os pacotes só serão transmitidos a todos casa haja um comando expresso para isso
	- Representa o isolamento lógico entre redes
	- **É formado por agrupamento de domínios de colisão**
- **HUB**
	- Camada 1
	- Um domínio de colisão
	- Um domínio de broadcast
	- Comunicação half duplex
	- **Evolução do repetidor (tinha apenas duas portas)**
	- **Ativos**
		- Amplificam
		- Restauram a forma e sincronismo
	- **Passivos**
		- Apenas replicação
	- **Inteligentes**
		- Gerência mínima de rede
- **Bridge**
	- Faz a interligação de 2 enlaces ou dois segmentos da mesma rede
	- **Não interliga duas redes diferentes!**
	- Apenas 2 portas
	- Camada 2
	- **Divide os domínios de colisão em 2**
	- **Apenas 1 domínio de brodcast**
	- Mapeia os macs via tabela de controle interna (tabela CAM)
- **Switch (Comutador)**
	- Evolução da bridge
	- Camada 2
	- N domínios de colisão
	- 1 domínio de broadcast
	- Isolam os domínios de colisão entre suas interfaces
		- Cada porta é um domínio de colisão
	- Mapeia os macs via tabela de controle interna (tabela CAM)
		- Content Addressable Memory
		- Armazenada em memória
	- Tipos de tráfego
		- Unicast
		- Broadcast
		- Multicast
	- **Possíveis problemas**
		- Estouro da tabela CAM
			- O Switch abre e começa a atuar como um HUB
		- Diferentes velocidades nas interfaces (comutação assimétrica) pode gerar acúmulo em memória e estouro de buffer
	- **Tipos especiais**
		- Switches modernos podem atuar até a camada 7
		- O mais comum é o switch L3 (camada 3)
			- Emprega técnicas de roteamento
			- **Segmenta os domínios de broadcast**
			- É capaz de rotear a nível de hardware, ao passo que roteadores roteiam a nível de software
			- Possui maior desempenho de roteamento
> [!note] 🔥
> **Pegadinha frequente!****
**
Switch L3 e Roteadores são equivalentes a nível **Funcional**, porém são diferentes a nível **Operacional**
- **Roteadores**
	- Nativos da camada 3
	- **Isolam domínios de colisão e broadcast nas suas interfaces**
	- Uso de tabelas de roteamento
	- Políticas de alto nível no tratamento de pacotes (QoS)
	- Interconecta segmentos com tecnologias diferentes a nível da camada de enlace
	- **ACLs:**
		- **incoming/outcoming (entrada/saída):**
			- ACLs podem ser aplicados tanto nas interfaces de entrada (incoming) quanto nas interfaces de saída (outcoming) dos roteadores. Isso permite controlar o tráfego que entra na rede, bem como o tráfego que sai dela.
		- **standard/extended (padrão/estendido):**
			- Standard: 
				- Baseiam-se apenas no endereço de origem. Não fazem qualquer validação de outros parâmetros, como endereço de destino ou porta
				- Recebem uma numeração inferior a 100 (0 a 99)
			- Extended: 
				- Avaliam parâmetros extras como porta, protocolo (tcp/udp) e endereço de destino
				- Recebem uma numeração de 100 a 199
		- **numbered/named (numeradas/nomeadas):**
			- As ACLs podem ser numeradas ou nomeadas. As ACLs numeradas são identificadas por números, como ACL 1, ACL 2, etc., enquanto as ACLs nomeadas são identificadas por nomes descritivos, como "ACL_PARA_REDES_INTERNAS".
```bash
access-list 101 permit tcp host 10.1.1.2 host 172.16.1.1 eq telnet
access-list 102 permit ip 10.1.1.0 0.0.0.255 172.16.1.0 0.0.0.255   
```
	- Existe uma ACL implícita ao final que é a `deny all`
	- Além de ser especificada, para ter efeito, cada ACL deverá ser aplicada a uma interface e sentido de tráfego (ingress / egress)
- **Gateway**
	- Tipos
		- Escoamento de tráfego
		- Elemento de conexão (Equipamento)
	- **Atuam em todas as camadas do modelo OSI (até a 7)**
		- Diz-se ser um elemento de camada 7
	- Comunicação entre diferentes protocolos e tecnologias
		- Ex: Gateway de voz (TDM para IP)
		- Gateway de rede (IP para IPX)
