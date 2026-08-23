---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2024-12-05T16:23:00
Owner:
  - Eduardo Quinalha
---
# Telefonia na Internet

- Múltiplos fluxos
- Taxas variadas
- Gestão integrada de tráfego
- Concorrência com outros fluxos

# Protocolos de Multimídia

## RTSP

- É utilizado para **controle de reprodução da mídia.**
- Podemos fazer a analogia ao controle remoto de uma televisão
- Porta 554 TCP/UDP
- Possui uma implementação simples em ASCII.
- **RTSP não é responsável pelo transporte da mídia em si, somente os controles**

## MMS

- Proprietário Microsoft
- 1755 TCP/UDP
- Mesmas funções do RSTP, por isso tornou-se obsoleto

## RTP (um dos mais cobrados em provas)

- Este protocolo é um pouco peculiar, pois é difícil situa-lo em uma das camadas
- **Diz-se que implementa recursos de transporte na camada de aplicação**
- RealTime Trasnport Protocol
- Padrão para streaming de áudio e vídeo
- Normalmente executado sobre o UDP em uma porta de **número par**
- **Áudio e Vídeo são enviados separadamente**
- **Somente multicast ou unicast, não suporta BROADCAST**
- **Não implementa QoS, controle de fluxo, erro, ordenamento de pacotes e confirmação**
- Possui recurso de sincronização por timestamp
- Como este recurso não está presente no UDP, é implementado diretamente pelo RTP na camada de aplicação

![[image 112.png]]

- O Socket apresentado na figura anterior gera o conceito de sessão: IP + Porta UDP. Logo, **não há o que se falar de estabelecimento de conexão para o protocolo RTP**.
- Gera-se uma sessão distinta para cada fluxo de mídia.

## RTCP

- Atua em conjunto com o RTP provendo informações de controle
- Atua na camada de aplicação com UDP
- Porta dinâmica
- A porta será uma acima da conexão RTP (RTP + 1), sendo esta sempre um número ímpar
- Como o transporte fica a cargo exclusivo do RTP, o RTCP se restringe ao controle, não transportando dados de mídia.
- **Tem por finalidade monitorar o atraso e a qualidade de voz.**
- O controle é efetuado por meio da troca de **mensagens periódicas** entre os pares coletando informações dos terminais e da **qualidade do serviço** da comunicação (largura de banda, latência, Jitter, entre outros).

## SRTP e SRTCP

- Seguindo a mesma lógica de HTTP, FTP e afins, o RTP e RTCP não implementam critérios de segurança
- Utilizando o SRTP e SRTCP é criado uma camada adicional de segurança acima do protocolo UDP

![[image 113.png]]

# Tipos de conferência

- Web conferência: 
	- Tipo mais simples, utilizando notebook, ou desktop. 
	- Não necessita de hardware específico
- Videoconferência: 
	- Envolve soluções de hardware ou appliance. 
	- Utiliza protocolos padronizados como SIP ou H.323
- Telepresença:
	- Experiência mais imersiva

# VoIP

- **Orientado a conexão e não confiável**
- Sinalização: 
	- Estabelecimento e encerramento das ligações
	- SIP e H.323
	- Tipos:
		- CAS - Sinalização trafega no mesmo canal de voz
		- CCS - Sinalização trafega em canais distintos
- Utiliza os protocolos RTP e RTCP

# FEC - Forward Error Correction

- Técnica utilizada com o objetivo de eliminar o Jitter
- O mecanismo de correção de erros de repasse pode ajudar a ocultar a perda de pacotes na transmissão VoIP
- Utiliza-se do recurso de acréscimo de dados redundantes que permitem suprir ou recuperar as parcelas perdidas.
- O objetivo do FEC (forward error correction) é rearranjar a sequência dos pacotes no receptor antes da transmissão, uma vez que o áudio pode ser enviado intercalado, e, assim, se garante que não haja variação de atraso.

# SIP - Session Initiation Protocol

- Atua na camada de aplicação com portas 5060 TPC/UDP
- Projetado para redes WAN
- Sinalização por meio de URL
- **Não provê recursos de QoS**, deixando-os a cargo de outros protocolos
- O transporte, **normalmente** é feito pelo RTP
	- No entanto, sua especificação não se restringe a esse protocolo
- Considerado um protocolo outband por trafegar sinalização em canal distinto da mídia
- Permite integração com redes analógicas por meio de gateways de voz
- Modelado sobre a estrutura do HTTP
- Aspectos de segurança
	- Suporta algoritmos de criptografia
	- S/MIME
	- HASH - MD5
	- TLS/SSL → SIPS Porta 5061
	- IPSec

## Estrutura do protocolo SIP

- modelado sobre a estrutura do protocolo HTTP
- Formas de endereçamento
	- Diretamente pelo endereço IPv4 ou IPv6;
	- Nome específico com a tradução de DNS (Nome de registro);
	- Endereço Telefônico;
	- Endereço de Email
- Mensagens:
	- INVITE: Solicita o estabelecimento de uma sessão;
	- re-INVITE: modificação de parâmetros em uma sessão já estabelecida;
	- ACK: Confirmação de um INVITE;
	- CANCEL: Cancela todos os métodos pendentes de resposta;
	- BYE: Encerra uma sessão estabelecida;
	- OPTIONS: **Consulta um host sobre seus recursos. Ex. Codecs suportados**
	- REGISTER: Informa ao servidor a localização atual do usuário.

## Principais Elementos

### User Agent (UA)

- Unidade lógica responsável pela interação do cliente com o sistema VoiP
- Divide-se em:
	- User Agent Client (UAC)
		- Interage com o usuário
		- Aplicação SIP, Telefone VoIP, softphone
	- User Agent Server (UAS)
		- Provê recursos aos dispositivos
		- Recebe a requisição de chamada

### Proxy Server

- Elemento intermediário
- Suas principais funções são de identificar e localizar os usuários requisitados nas chamadas e rotear (encaminhar) as chamadas até esses dispositivos
- o UAC que deseja realizar a chamada, caso desconheça o caminho e endereço IP do destino, deve conhecer seu PROXY SERVER e encaminhar a chamada até este elemento para que ele trate a chamada.

### Registrar Server

- Elemento responsável por efetuar os registros das informações de um UA
- Possibilita que o novo cliente VoIP se torne conhecido e possível de ser alcançado
- A principal informação a ser enviada no momento do registro é o endereço IP de determinado usuário.
- Assim, o servidor realizará o mapeamento do nome de domínio de registro e o seu IP, entre outros parâmetros.

### Redirect Server

- Responsável por realizar o redirecionamento de requisições de forma dinâmica e automática para outros servidores SIP
- Sua principal utilização se dá no momento de mudanças de endereços ou localizações de UA’s nos domínios da rede.

## Formas de Comunicação

### Direta

![[image 114.png]]

### Com Proxy

![[image 115.png]]

### Multidomínio

![[image 116.png]]

## Cabeçalho

- TO
- FROM
- CSeq
	- Número de sequência + identificação da mensagem
- Call-ID
	- Identificador global único para a chamada em curso
- Max-Forwards
	- Limite de saltos
- Via
	- Define o caminho a ser percorrido pela comunicação

## SDP

- Protocolo que define o formato das mensagens que trafegam em uma arquitetura SIP
- A relação entre SIP e SDP é como do HTML para o HTTP

| **Protocolo** | **Formato da mensagem** |
| --- | --- |
| HTTP | HTML |
| SIP | SDP |

- Define:
	- Tipos de mídia
	- CODEC’s
	- Protocolo de transporte (normalmente RTP)
	- Portas para troca de fluxo
	- Dentre outros aspectos

# H.323

- Estrutura muito mais complexa se comparado ao SIP
- Provê uma estrutura completa (padrão guarda-chuva) para a telefonia e videoconferência sobre a arquitetura TCP/IP, envolvendo diversos protocolos e tecnologias
auxiliares
- Arquitetura monolítica

![[Untitled 438.png]]

- Não garante aspectos de QoS
- Projetado para redes LAN
	- O SIP foi projetado para redes WAN
	- Porém hoje não há mais esta distinção e ambos operam nos dois tipos de redes
- Suporta diversos tipos de fluxo (audio, video e dados) sendo o áudio **obrigatório** (serviço mínimo)
- Sua sinalização funciona em **ASN.1** binário ao invés de ASCII como no SIP
- Sinalização por combinação de número de host e número de telefone
- Serviços de dados padrão T.120
	- Lousa eletrônica
	- Transferência de arquivos em comunicação interativa
	- Compartilhamento de aplicações

## Componentes

### Terminais

- Computador ou telefone VoIP

### Gateways

- Opcional
- Interconexão entre redes H.323 distintas
- Interconexão com redes analógicas (PSTN)

### Unidades de controle MCU

- Opcional
- Realiza conferência entre os elementos

### Gatekeeper

- Opcional
- Centralização e controle das chamadas em uma LAN
- Billing
- Administra largura de banda
- Conceito de ZONA H.323

![[image 117.png]]

![[VoIP_e_Multimdia.png]]

# RTP/RTCP

- Transporte de dados com características de tempo real, por exemplo, áudio e vídeo interativo
- RTP → Transporte dos dados
	- Executado de ponta a ponta
	- Não confiável
	- Funções:
		- Timestamping
		- Numeração sequencial
		- Identificação do tipo de payload
		- Identificação da fonte
![[Untitled 439.png]]
- RTCP → Monitoração da qualidade de serviço e envio de informação sobre os participantes numa sessão
	- Feedback sobre a qualidade do serviço
		- Receptores identificam a qualidade em pacotes perdidos, jitter e round-trip delay
		- Esta informação pode ser utilizada para ajustar codificação e parâmetros
	- Sincronização
		- Áudio e vídeo
		- O áudio tipicamente é enviado em streaming separado
	- Identificação dos participantes na sessão
	- Controle da sessão
- Funcionam sobre UDP
- Adotados pela arquitetura multimídia IETF e H.323

# **DIFERENÇA ENTRE H.323 E SIP**

**H.323:**

H.323 é o sistema baseado principalmente em phonephone. E seu design é monolítico. A extensão ou quantificabilidade do H.323 é restrita e é muito pouco versátil. O H.323 não oferece o poder das mensagens eletrônicas instantâneas.

![[Untitled-Diagram-66.png]]

**Protocolo de iniciação de sessão (SIP):**

SIP é o protocolo da camada de sessão. Seu design é um design padrão. Sip é ascendível mais saudável que H.323 e é muito versátil que H.323 também. O Sip oferece a capacidade de mensagens eletrônicas instantâneas.

![[Untitled-Diagram-67.png]]

Vamos ver que a diferença entre H.323 e SIP:

| S.NO | H.323 | TRAGO |
| --- | --- | --- |
| 1 | H.323 é uma arquitetura monolítica. | SIP é uma arquitetura modular. |
| 2 | A escalabilidade do H.323 é limitada. | SIP é melhor escalável. |
| 3 | H.323 é um pouco flexível. | É mais flexível. |
| 4 | H.323 não fornece a facilidade de mensagens instantâneas. | O SIP fornece a facilidade de mensagens instantâneas. |
| 5 | H.323 é complexo absoluto em termos de complexidade. | É moderadamente complexo em termos de complexidade. |
| 6 | O formato da mensagem de H.323 é binário. | Enquanto o formato da mensagem do sip está no formato ASCII. |
| 7 | Não é compatível com a Internet. | Embora seja compatível com a internet. |
| 8 | H.323 é construído inteiramente em sistemas telefônicos. | Enquanto o SIP depende completamente da conexão com a internet. |

# **DIFERENÇA ENTRE H.323 E SIP**

**H.323:**

H.323 é um padrão para áudio e vídeo conferência em tempo real pela Internet. H.323 também especifica como o sistema final é conectado à Internet pela rede telefônica comutada por circuito.

**SIP: **

**O **protocolo do iniciador de sessão descreve o estabelecimento, gerenciamento e encerramento da sessão multimídia. As sessões de multimídia podem ser videoconferências por chamada telefônica pela Internet.

**Diferença entre H.323 e SIP:**

H.323TRAGO É compatível com PSTN. Não é compatível com PSTN.H.323 não é compatível com a Internet. SIP é compatível com a Internet. Segue arquitetura monolítica. Segue arquitetura modular .Ele usa o formato de mensagem binário. Ele usa o formato de mensagem ASCII. Para fins de endereçamento, ele usa números de host ou de telefone. Para endereçamento usa URL. Ele não oferece suporte a mensagens instantâneas. Suporta mensagens instantâneas. Implementação ampla e complexa. Implementação moderada. Desenhado pela ITU. Desenhado pela IETF.

# VoIP (voz sobre IP)

**Protocolos auxiliares para controlar este tipo de comunicação: o **SIP e H.323. OS DOIS usam o protocolo RTP

## **RTP:**

- se situa entre a camada de aplicação
- funciona sobre UDP
- Não é atribuída nenhuma porta conhecida ao RTP porem deve ser par
- Em uma sessão multimídia, cada mídia é transportada sobre uma **sessão RTP diferente**
- o áudio e o vídeo são transportados sobre sessões diferentes

O <u>**RTP**</u> (*real-time transport protocol*) tem capacidade para transportar dados de um <u>**serviço VoIP**</u> sobre o protocolo<u>** UDP**</u> (*user datagram protocol*). **(C)**

**É controlado pelo RTCP que atua junto com RTP**

Não oferece qualquer garantia que os pacotes serão entregues num determinado intervalo.

não é atribuída nenhuma porta conhecida ao RTCP deve USADO PORTA IMPAR

## **SIP**

- UTILIZA O RTP
- Camada de aplicação
- estabelece, gerencia e encerra uma sessão multimídia
- Pode criar uma sessão entre duas partes, entre várias partes ou e multicast.
- Pode ser suportado tanto pelo UDP, TCP ou SCTP da camada de transporte.
- MENSAGENS utilizadas são baseadas em texto (ASCII).
- um dos padrões de telefonia por Internet.
- O protocolo SIP permite bastante flexibilidade SESSÃO SIMPLES
- Uma sessão simples utilizando o SIP é constituída de três fases: estabelecimento, comunicação e encerramento.

O estabelecimento é feito através de um handshake triplo, no qual o originador envia uma mensagem INVITE. Caso esteja disposto, o recebedor envia uma mensagem aceitando a sessão. Para confirmar o recebimento, o originador envia uma mensagem ACK 

## **H.323**

- permite a comunicação entre rede de telefonia convencional e computadores conectados à internet
- MENSAGENS utilizadas : notação binária para comunicação.
- o *stream *de mídia é transportado pelo protocolo RTP
- **O H323 utiliza o protocolo RTP para o transporte de dados de áudio e de vídeo**.
- inclui componentes como gatekeeper e MCU gateway estabelece uma conexão entre a Internet e a rede de telefonia pública GATEWAY é um dispositivo de cinco camadas capaz de traduzir mensagens de uma pilha de protocolo em outra.
- Elementos obrigatórios do H.323:
	- Voz;
	- H.245: negocia uso do canal e controle de mídia;
	- H.225.0: sinalização e estabelecimento da chamadas;
	- RAS: protocolo para comunicação com Gatekeepers;
	- RTP/RTCP: Sequenciamento de pacotes de áudio e vídeo.

O MCU (multipoint control unit) é o sistema que permite um contato visual e sonoro simultâneo entre várias pessoas que estejam em lugares diferentes.
