---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2024-11-22T07:55:00
Owner:
  - Eduardo Quinalha
---
# Gerenciamento de Redes

## FCAPS

O modelo FCAPS é um framework de gerenciamento de redes proposto pela ISO (International Organization for Standardization) para gerência e monitoramento de redes, serviços e aplicações. FCAPS é um acrônimo que representa as cinco áreas funcionais de gerenciamento de rede:

## **Áreas Funcionais do FCAPS**

1. **F - Fault Management (Gerência de Falhas)**
	- Foca na detecção, isolamento e correção de problemas na rede.
	- Inclui monitoramento proativo, análise de alarmes e recuperação de falhas.
2. **C - Configuration Management (Gerência de Configuração)**
	- Envolve o monitoramento e controle das configurações de dispositivos de rede.
	- Abrange rastreamento de alterações, provisão de circuitos e planejamento de expansões.
3. **A - Accounting Management (Gerência de Contabilidade)**
	- Responsável pela coleta de informações sobre o uso da rede pelos usuários.
	- Permite a alocação de custos e o estabelecimento de políticas de uso.
4. **P - Performance Management (Gerência de Desempenho)**
	- Mede e monitora o desempenho da rede e seus serviços.
	- Inclui análise de parâmetros como tráfego, latência e qualidade de serviço (QoS).
5. **S - Security Management (Gerência de Segurança)**
	- Lida com a proteção da rede contra ameaças e vulnerabilidades.
	- Abrange controle de acesso, detecção de intrusões e implementação de políticas de segurança.

## FAB

Modelo Top-down, centrada no negócio

- Fault → Assurance
- Configuration → Fulfillment
- Accounting → Billing
- Performance → Assurance
- Security → Fulfillment

# MIB

## MIB

> [!note] 🔥
> **MIB (Management Information Base): **É uma estrutura de dados hierárquica que define as informações gerenciadas que podem ser acessadas e controladas por um gerente SNMP. A MIB contém objetos gerenciados identificados por meio de OIDs (Object Identifiers).

**Object Identifier (OID).** O OID é uma sequência numérica que identifica exclusivamente cada objeto gerenciável na MIB (Management Information Base).

- Definição dos objetos de gerenciamento em uma base de dados virtual
- Trata da informação propriamente dita
- Pode assumir diversos valores
	- Quantitativos
	- Descritivos
	- Informativos
- Base de informações de gerenciamento que define um conjunto de objetos gerenciados em dispositivos de rede.
- Estrutura hierárquica que organiza os objetos em grupos e subgrupos.
- Cada objeto possui um identificador único (OID) e características específicas, como tipo de dado, acesso e valor.
- Permite monitorar e gerenciar dispositivos **de forma padronizada, independente do fabricante ou modelo.**
- Cada objeto na MIB é composto por:
	- **Nome (Name)**: Identifica o objeto de forma única na hierarquia da MIB.
	- **Sintaxe (Syntax)**: Define o tipo de dado do objeto (por exemplo, INTEGER, STRING).
	- **Acesso (Access)**: Especifica o tipo de acesso permitido ao objeto (por exemplo, read-only, read-write).
	- **Status**: Indica o status do objeto (por exemplo, current, obsolete).

## MIB II

- É um subconjunto da MIB original, padronizado no RFC 1213.
- Define um conjunto de objetos básicos para **gerenciar dispositivos TCP/IP.**
- Inclui **informações sobre interfaces de rede, estatísticas de tráfego, tabelas de roteamento, entre outras.**
- É a MIB mais utilizada em redes TCP/IP e é implementada por padrão na maioria dos dispositivos.

| **Característica** | **MIB** | **MIB II** |
| --- | --- | --- |
| Abrangência | Ampla, define objetos para diversos tipos de dispositivos. | Restrita, define objetos para dispositivos TCP/IP. |
| Objetos | Maior quantidade de objetos, com foco em funcionalidades específicas de cada tipo de dispositivo. | Menor quantidade de objetos, com foco em funcionalidades básicas de gerenciamento de dispositivos TCP/IP. |
| Implementação | Opcional, depende da implementação do fabricante do dispositivo. | Obrigatória em dispositivos que suportam SNMP. |

- usa o modelo de arquitetura de árvore para organizar todas as suas informações.
- o único nó da árvore que não é rotulado é o nó raiz.
- **O nó raiz da MIB tem, pelo menos, três filhos diretamente abaixo dele:**
	- **ccitt(0)**, administrada pelo CCITT
	- **iso(1)**, administrada pela ISO
	- **joint-iso-ccitt(2**), administrada pela ISO juntamente com o CCITT.

![[Untitled 453.png]]

- MIB Privada
	- Específica de cada fabricante
	- Informações adicionais sobre dispositivos específicos ou funcionalidades proprietárias.
- **MIB-III:** Introduziu uma estrutura mais hierárquica e modular para facilitar o gerenciamento de redes complexas.
- SMI
	- É um conjunto de regras e definições que define a estrutura e o formato das MIBs
	- Define os tipos de dados, as operações de acesso e outras características dos objetos gerenciados em uma MIB.
	- Atua como uma linguagem formal para a descrição de MIBs, garantindo interoperabilidade entre diferentes implementações de SNMP.
	- Definição dos dados
		- Tipos de dados
		- Modelo dos objetos
		- Regras para escrita
	- A estrutura segue o padrão ASN.1
	- Hierarquizada
- **SMIv2:** Simplificou a estrutura da MIB e introduziu novos recursos, como suporte a SNMPv3.
- SNMP
	- Protocolo para transportar as informações e comandos entre a entidade gerenciadora e os agentes dos dispositivos gerenciados.

# SNMP

- Não é uma arquitetura cliente-servidor tradicional
	- Os pares de dispositivos atuam tanto como cliente como servidor no envio e recebimento de informações
- Utiliza-se mais comumente a nomenclatura gerente-servidor, na qual o dispositivo gerente sempre recebe as informações, seja via requisições dele mesmo ou via traps, enviadas dos dispositivos gerenciados
- As informações dos dispositivos gerenciados podem ser obtidas de duas formas:
	- Via requisição
		- Porta 161/UDP
		- Também há o suporte para TCP
	- Via traps
		- Porta 162/UDP
		- Também há suporte a TCP
		- Não há mensagem de resposta
- Por que UDP?
	- evitar overhead de rede
	- Necessidade de comunicação em tempo real
	- As mensagens são simples e curtas

## Mensagens

- **GET REQUEST **
	- Mensagem mais básica. 
	- É utilizada para solicitar o valor armazenado nos objetos da MIB do agente que está rodando no dispositivo gerenciado. 
	- Tem o foco na coleta de informações;
- **GETNEXTREQUEST**
	- Busca o valor da próxima instância da MIB em uma lista ou tabela;
- **SET REQUEST**
	- É utilizada para definir valores de variáveis dos objetos da MIB. Possui um caráter de configuração;
- **INFORM REQUEST**
	- Incluída a partir do SNMPv2
	- Permite a troca de mensagens entre dois gerentes ou entidades de gerenciamento;
- **GETBULK REQUEST**
	- Incluída a partir do SNMPv2
	- Utilizado para consultas que possuem um grande volume de dados;
- **RESPONSE**
	- Resposta gerada pelos agentes ou gerentes às requisições anteriores;
- **TRAP**
	- Mensagem que possui o mesmo sentido do tipo RESPONSE, porém, não dependendo de uma requisição para ocorrer. 
	- Informa ao gerente um evento excepcional ocorrido;

## Arquitetura

- **Agentes SNMP:** 
	- São processos ou software que residem em dispositivos de rede e são responsáveis por coletar e armazenar informações gerenciadas, bem como responder a solicitações de gerentes SNMP.
- **MIB (Management Information Base)**
- **Gerentes SNMP:** 
	- São sistemas de software responsáveis por monitorar e controlar os dispositivos de rede por meio do SNMP. Eles emitem solicitações para os agentes SNMP e recebem respostas e notificações em troca.

## Versões

[https://www.noction.com/blog/snmp-versions-evolution-security](https://www.noction.com/blog/snmp-versions-evolution-security)

### SNMPv1

- Estrutura mais básica e simples
- Senha em texto claro:
	-  Comunidades
		- **Pública**
			- comunidade mais comum, geralmente usada para leitura de informações básicas do dispositivo.
		- **Privada**
			- comunidade mais segura, geralmente usada para leitura e modificação de informações confidenciais do dispositivo.
		- **Específicas**
			- Comunidades personalizadas para controlar o acesso a grupos específicos de dispositivos ou funcionalidades.

### SNMPv2

- Permite autenticação de mensagens
- Mantém a característica de senhas baseadas em nomes de comunidades em texto claro
- Acrescentadas as mensagens:
	- INFORM REQUEST
	- GETBULK REQUEST
- Subversões:
	- **SNMPv2c:** Versão mais simples e comumente utilizada.
	- **SNMPv2u:** Versão mais complexa que oferece suporte a funcionalidades avançadas como criptografia de mensagens.

### SNMPv3

> [!tip] 💡
> A versão mais recente do protocolo, o **SNMPv3**, não fez grandes alterações estruturais, porém adicionou uma camada de segurança ao protocolo. As mensagens do SNMPv1 e do SNMPv2 continuam sendo utilizadas, porém o cabeçalho da mensagem SNMP passa a conter informações relacionadas à segurança da mesma.

> O SNMPv3 introduziu recursos de segurança robustos, incluindo autenticação de mensagens, criptografia de dados e controle de acesso baseado em papéis (RBAC). Agora, o protocolo oferece três modelos de segurança diferentes:

- **Modelo de Segurança por Comunidade (Community-Based Security Model)**
	- Este modelo é semelhante aos modelos de segurança das versões anteriores (SNMPv1 e SNMPv2).
	- Ele utiliza uma "comunidade" como uma senha em texto claro para autenticação.
	- As comunidades podem conceder acesso de leitura (read-only) ou acesso de leitura e escrita (read-write) à MIB do dispositivo.
	- Apesar de ser menos seguro, ainda é suportado pelo SNMPv3 para garantir a compatibilidade com dispositivos mais antigos.
- **Modelo de Segurança por Usuário (User-Based Security Model - USM)**
	- Este é o **modelo principal **de segurança do SNMPv3, oferecendo autenticação e privacidade robustas.
	- Ele requer que os agentes e gerentes tenham identidades de usuário únicas.
	- A autenticação é realizada usando um algoritmo de hash criptográfico (MD5 ou SHA) e uma senha.
	- Além da autenticação, o USM também suporta privacidade de dados, permitindo que as mensagens SNMP sejam **criptografadas** usando algoritmos como DES, 3DES, AES ou outros.
- **Modelo de Segurança por Contexto (View-Based Access Control Model - VACM)**
	- Este modelo lida com o controle de acesso baseado em papéis **(RBAC) no SNMPv3.**
	- Ele define quais partes da MIB um usuário ou gerente pode acessar.
	- Isso é feito através da criação de "visualizações" (views) que especificam quais objetos da MIB podem ser acessados e em que contexto.
	- O VACM também permite a definição de regras de acesso baseadas em identidades de usuário e grupos de usuários, fornecendo um controle granular sobre as operações SNMP permitidas.
- Em SNMPv3, as comunidades são substituídas por **identificadores de segurança **(Security Identifiers, também conhecidos como "security strings"), que são associados a um ou mais grupos de acesso.

> [!tip] 💡
> Outra alteração importante foi o abandono à ideia de **gerentes** e **agentes**. No SNMPv3, o foco passou a ser na definição de **entidades gerenciadas** (managed entities) e **entidades de gerenciamento** (management entities). Essa mudança reflete uma abordagem mais flexível e orientada para objetos, onde tanto dispositivos quanto sistemas de gerenciamento podem desempenhar papéis dinâmicos, dependendo do contexto.

Nesse novo paradigma, uma entidade gerenciada pode ser qualquer dispositivo ou recurso de rede que tenha informações gerenciáveis, enquanto uma entidade de gerenciamento pode ser um sistema de gerenciamento de rede, como um console de gerenciamento ou uma estação de gerenciamento. Essa abordagem permite uma modelagem mais abstrata e adaptável do ambiente de gerenciamento de rede, facilitando a integração com diferentes tecnologias e permitindo uma maior escalabilidade e eficiência na administração de redes complexas.

- Foco em aspectos de segurança
- Suporte a autenticação e criptografia
- Suporte a criptografia com algoritmo AES
- Suporte a funções de HASH MD5 e SHA
- Suporte a SSL
- Senhas distintas para leitura e escrita
- **Controle de acesso granular**
	- Permissões detalhadas podem ser configuradas para usuários, grupos e dispositivos, possibilitando um controle preciso do acesso aos recursos.
	- Implementa os conceitos de **SNMP View, SNMP Group, and SNMP User.**
		- *NMP View defines what a particular SNMpv3 user can view. For example, it is possible to configure that a user will only have access to view the interface index, OID 1.3.6.1.2.1.2, and anything below that.*
		- *SNMP Group is associated with the SNMP View and it defines a type of the access – read-only or read/write. It also defines the type of security that is active when interacting with the device.*
```plain text
   noauth – nor authentication or encryption
   auth – only authentication, no encryption
   priv – authentication and encryption
```
		- *SNMP User is added to the group with the level of authentication and encryption. The security model must match the group, e.g. priv, a type of the hash for the password (e.g. SHA), the password, encryption algorithm (e.g. AES), and a shared secret for generating encryption keys.*
- **Níveis de Segurança**
	- Os aprimoramentos do SNMPv3 são organizados em **três níveis de segurança:**
		- **noAuthNoPriv**
			- Esse é o nível de segurança mais baixo no SNMPv3.
			- Não há autenticação nem criptografia.
			- semelhante ao comportamento das versões anteriores (SNMPv1 e v2c) e só deve ser usado em redes altamente confiáveis ou seguras fisicamente.
		- **authNoPriv**
			- Neste nível, há autenticação, mas **ainda não há criptografia.**
			- A identidade do remetente da mensagem é verificada usando um protocolo de autenticação como HMAC-MD5 ou HMAC-SHA.
		- **authPriv**
			- As mensagens são criptografadas usando algoritmos como DES ou AES

# RMON

[http://penta.ufrgs.br/gere97/unama/rmonrmon2.pdf](http://penta.ufrgs.br/gere97/unama/rmonrmon2.pdf)

- Trata-se de uma **extensão de MIB**, Management Information Base, para ser utilizada com protocolos de gerenciamento de rede em internets baseadas em TCP/IP.
- **O RMON utiliza o SNMP**** para coletar dados de dispositivos de rede:** O RMON define um conjunto de MIBs (Management Information Bases) que especificam os tipos de dados que podem ser coletados dos dispositivos. O SNMP é utilizado para acessar esses dados e transferi-los para um sistema de gerenciamento.
- **O SNMP pode ser utilizado para configurar o RMON:** O SNMP pode ser utilizado para configurar parâmetros de monitoramento no RMON, como quais tipos de dados serão coletados e com que frequência.
- Oferece mecanismos para um gerente não apenas configurar e controlar um monitor remoto, mas também coletar seus dados e receber seus alarmes.
- Os dispositivos gerenciados precisam ter instalados um agente e uma MIB
- O gerenciamento gera um tráfego que pode ser elevado
- RMON é específico para os protocolos Ethernet e Token Ring, no entanto existe implementação para ATM
- Um dispositivo que implementa suporte para o RMON se chama **probe**
	- Agente SNMP
- O Probe deve ficar em um ponto da rede que concentre o tráfego
- Concentra e armazena as informações sobre eventos e tráfego de rede, enviando periodicamente esta informação ao gerente
- RMON é uma MIB SNMP, portanto depende do protocolo SNMP
- Fornece informações mais precisas do que o SNMP puro

![[image 118.png]]

## MIB RMON

- Os objetos RMON são organizados em 20 grupos. Os primeiros 10 grupos constituem a MIB RMON1, voltada ao gerenciamento das operações realizadas nos níveis físico e de enlace em redes Ethernet
- Os 10 grupos restantes constituem a MIB RMON2, proposta para viabilizar a coleta de estatísticas e informações para protocolos acima do nível de enlace.
- MIB RMON I
	- Atua a nível de camadas 1 e 2 OSI
	- Fornece estatísticas sobre erros de rede, utilização da banda, endereçamento MAC e colisões.
- MIB RMON II
	- Camadas 3 a 7
	- Fornece estatísticas sobre protocolos de rede, distribuição de tráfego por aplicativo, latência e jitter.

![[Untitled 454.png]]

## Objetivos do RMON

- Operação off-line
	- O agente deve tentar notificar a estação de gerenciamento sobre a ocorrência de algum evento importante. Se a comunicação de notificação falhar, a informação sobre essa ocorrência pode ser continuamente acumulada pelos monitores e repassada às estações de gerenciamento da
forma mais conveniente e eficiente possível.
- Monitoração pró-ativa:
- Detecção e registro de problemas
- Dados com valor agregado
- Múltiplos gerentes
