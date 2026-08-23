---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2024-08-26T18:25:00
Owner:
  - Eduardo Quinalha
---
> [!tip] 💡
> No caso de aplicações web que fazem uso de banco de dados, ambos on premises, é uma boa prática, segregar servidor web e BD em redes, diferentes, no caso, pelo uso de duas DMZ’s separadas. Desta forma, os usuários internos não têm acesso diretamente ao banco, se não pelo servidor de backend. Este arranjo é previsto pelas boas práticas de DLP

> [!tip] 💡
> Não existe nenhuma aplicação de firewall que nativamente se conjugue com as características de antivirus. No entanto, existem appliances que juntam as duas soluções (como aplicações separadas rodando dentro deles)

![[20230827_051120.jpg]]

# Firewall

- Elemento de borda
- Quando do uso de 2 firewalls (DMZ + Defesa em produndidade), é recomendável o uso de firewalls de fabricantes diferentes
	- Desta forma, caso tenha sido explorado uma vulnerabilidade específica de frabricante, inviabiliza a exploração do segundo firewall
- Bastion Host
	- Equipamento que provê recursos ao público externo
	- Hardening
	- Robusto
	- Recursos mínimos necessários para as funcionalidades esperadas
	- Baixíssima superfície de ataque

## Topologias com Firewall

- Dual Homed Host
	- Um único equipamento
	- Duas interfaces
	- Uma para fora, outra para dentro
	- Não tem DMZ
- Screened Host
	- Faz o uso de um **Bastion Host**
		- Na prática, é o firewall, com uma interface física apenas, localizado na intranet (do ponto de vista físico)
		- Do ponto de vista lógico, implementa um firewall com duas interfaces, uma voltada para fora, outra voltada para dentro
	- Este Bastion Host, recebe e responde ao tráfego externo e também recebe e responde ao tráfego interno
	- Está logicamente na intranet
	- O fluxo passa antes por um router que encaminha todo o tráfego para o bastion host
- Screened-subnet host
	- Implementa uma DMZ
	- O **Bastion Host **fica dentro da DMZ
		- Do ponto de vista lógico, tem-se dois firewalls, um para fora e outro para dentro, segregando a DMZ
		- Do ponto de vista físico, tem-se dois roteadores, um para fora, outro para dentro, segregando a DMZ, e o bastion Host implementando dois firewalls virtuais
	- Dois roteadores delimitam a DMZ, um para fora, outro para dentro

## DMZ

- Usuários externos são jogados numa zona neutra, que não se mistura com a rede interna
- Pode ser implementada de forma física ou lógica
- Pode ser implementado por meio de interfaces virtuais, no lado da intranet

## Classificação de Firewalls

> [!tip] 💡
> A classificação se dá de acordo com a camada pela qual ele consegue interpretar os pacotes

### **Bridge**

- Camada de enlace
- Não possui endereço IP
- Não tem visibilidade externa, só é possível o acesso pelo mesmo enlace
- Na prática só é acessível por meio de um cabo conectado fisicamente a ele
- Limitado com relação às informações que consegue filtrar

### **Filtro de pacotes**

- Também conhecido como **stateless ou estático**
	- Cada fluxo é tratado como um fluxo novo
- Camada de rede
- **A ordem das regras é importante**
	- Os fluxos mais relevantes devem estar nas primeiras posições da tabela de regras
- Consegue interpretar algumas poucas informações da camada de transporte
- Filtragem de IP e porta
- A direção do fluxo da informação é importante

### **Circuit Level**

- Camada de sessão do modelo OSI
- UDP
- 3 Way Handshake do TCP

### **Filtro de pacotes baseado em estados**

- Abrange também a camada de transporte
- Também conhecido como **Filtro de estado, Firewall dinâmico ou statefull**
	- Alguns chamam de NG Firewall (Next Generation Firewall)
- Utiliza uma tabela de estados
- A direção do fluxo não é mais importante, após a primeira validação
- No caso do UDP, utiliza o conceito de contextos

### **Proxies**

- **Camada de aplicação**
- Estabelece duas conexões
- Camada adicional de autenticação e segurança
- pode operar tanto no nível de aplicação quanto no nível de transporte.
	- No **nível de aplicação**, um proxy específico é usado para cada aplicação. Este tipo de proxy é **capaz de ler e interpretar o conteúdo das mensagens trocadas entre cliente e servidor**, permitindo um controle mais granular do tráfego de rede.
		- Exemplos comuns incluem proxies HTTP, FTP e SMTP.
	- No nível de transporte, **um proxy genérico pode ser usado para conexões TCP e UDP**.
		- Este tipo de proxy, também conhecido como** proxy de circuito**, estabelece uma conexão entre cliente e servidor e repassa os pacotes entre eles <u>**sem inspecionar o conteúdo das mensagens**</u>.

### **DPI**

- Deep Packet Inspection
- Verifica o conteúdo do pacote, além do cabeçalho

### **Proxy Reverso**

- Proteção
- Balanceamento de carga
- Cache
- Permite trabalhar com portas diferentes
	- Você acessa o proxy com a porta padrão, porém este redireciona internamente para o servidor, que roda em outra porta

### **WAF**

- Web Application Filter
- Proteção da aplicação
	- XML Injection
	- SQL Injection
	- XSS
	- Dentre outros
- Atua na camada de aplicação

![[Untitled 308.png]]

### **UTM**

- Integra todas as soluções acima
	- Firewall stateful
	- Proxy
	- VPN
	- WAF
	- IDS/IPS

## Modos de atuação

- Modo de detecção
	- Tanto para firewalls como IDS/IPS
	- Análise do tráfego em busca de padrões conhecidos de ameaças ou ataques
	- Emite alertas em caso de deteção
- **Modo de Fluxo**
	- Análise contínua do tráfego de rede em tempo real, sem interromper ou bloquear o fluxo normal de pacotes.
	- Firewalls de **DPI** (Deep Package Inspection)
	- Detecta ameaças mais complexas
	- Pode gerar alertas e/ou bloquear o fluxo
- Modo de prevenção
	- Bloqueio para previnir ataques
	- IPS
	- Pode enviar comandos para outros dispositivos

![[Firewall.png]]

# SIEM

- Security Information and Event Management
- Inteligência de dados
- Pode ser implementado com ElasticSearch
- Recepciona e consolida logs de diversas fontes relacionadas a SI como:
	- Firewall
	- Roteadores
	- IDS/IPS
	- Sistemas
- Com base no cruzamento destas informações, provê maior facilidade na identificação de falhas e vulnerabilidades
- Gera alertas e relatórios de auditoria e prevenção
- O sincronismo de tempo é essencial para o bom funcionamento deste sistema

![[20230911_071445.jpg]]

# IDS/IPS

## Metodologias de Detecção

- **Base de conhecimento**
	- Lista de regras ou assinaturas
	- **Normalmente utilizado pelo IDS**
- **Base de comportamento**
	- Levantamento histórico
	- Aprende os padrões de tráfego da rede
	- Quando um tráfego desvia do padrão, pode ser tomado uma atitude
	- **Normalmente utilizado por IPS**

> [!tip] 💡
> Ambos estão sujeitos a falsos positivos/negativos, embora o baseado em assinaturas (base de conhecimento) tem uma probabilidade menor de erro se comparado com a base de comportamento

- **Formas de conexão**
	- Port Span
		- Replica-se todo o tráfego do switch para uma porta de alta capacidade
	- Splitting Wire / Optical Tap
		- Deriva a conexão
		- Pode ser por equipamento específico ou até mesmo um hub
		- Cópia do sinal original
	- Port Mirror
		- Espelhamento de uma porta para outra

## IDS

- Simplesmente detecta
- Posiciona-se em paralelo ao tráfego
- Não age sobre o tráfego
- Pode ser utilizado em conjunto com firewall
	- O IDS analiza o tráfego e sinaliza ao firewall para realizar o bloqueio
- **Tipos**
	- **NIDS (Network based IDS)**
		- Vantagens
			- Pode ser utilizado em pontos estratégicos da rede
			- Atuando de modo passivo, não interfere no desempenho
			- Difícil de ser detectado por atacantes
		- Desvantagens
			- Não é eficiente em situações de tráfego intenso
			- Incapacidade de lidar com tráfego criptografado
			- Não bloqueia o ataque
> [!tip] 💡
> Switches e roteadores modernos já disponibilizam soluções de NIDS

	- **HIDS (Host based IDS)**
		- Vantagens
			- Capazes de detectar ataques mais específicos
			- Pode tratar dados criptografados (antes e depois)
			- Não são afetados por elementos de rede
		- Desvantagens
			- Difícil configuração (especificidades de cada estação)
			- Podem ser derrubados por DoS
			- Degradação de desempenho da estação
	- **IDS baseado em pilhas**
		- Comportamento entre as camadas TCP
		- Analiza alterações nos cabeçalhos e outros comportamentos
- Características desejáveis a um IDS:
	- Executar continuamente com mínima supervisão humana.
	- Ser tolerante a falhas no sentido de ser capaz de se recuperar de quedas e reinicializações de sistema.
	- Resistir à subversão. O IDS deve ser capaz de monitorar a si mesmo e detectar se foi modificado por um atacante.
	- Impor um sobrecusto computacional mínimo ao sistema no qual está executando.
	- Poder ser configurado de acordo com as políticas de segurança do sistema que está sendo monitorado.
	- Ser capaz de se adaptar a mudanças no comportamento do sistema e do usuário ao longo do tempo.
	- Ser escalável, de modo a poder monitorar grande número de estações.
	- Prover degradação elegante de serviço no sentido de que, se alguns componentes do IDS pararem de funcionar por qualquer razão, o resto deles deve ser afetado o mínimo possível.
	- Permitir reconfiguração dinâmica, isto é, a capacidade de reconfigurar o IDS sem ter de reiniciá-lo.

## IPS

- Posiciona-se no fluxo de dados (in-line)
- Tem capacidade de bloqueio de tráfego
- Atua de forma preventiva

## WIPS (Wireless Intrusion Prevent System)

- Monitora o espectro de ondas de rádio

![[IDS_IPS.png]]

# NGAV

- Next Generation Antivirus
- Além da clássica detecção por assinaturas, é capaz de prover
	- Análise comportamental
	- Machine Learning e IA
	- Detecção em tempo real
	- Prevenção de exploração de vulnerabilidades

# AntiSpam

- **Técnicas de Bloqueio**
	- Lista de bloqueio
		- Blacklists
		- Whitelists
		- Graylists
	- Filtro de conteúdo
		- Busca por padrões categorizados
		- Pode gerar falsos positivos
	- SPF
		- Busca garantir a legitimidade do remetente
		- Pode combater a falsificação de return-paths através da validação de IP’s
	- DKIM
		- Baseado na autenticação com utilização de chaves públicas
		- **Enquanto SPF verifica apenas endereço IP, DKIM averigua informações de cabeçalho e de conteúdo**
	- Gerência da porta 25
		- Principal modelo atual
		- Envio do e-mail em duas fases:
			- Usuário para o provedor de acesso
			- Comunicação entre servidores
			- Reserva a porta 25 exclusivamente para comunicação entre MTA’s
