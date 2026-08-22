---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2024-11-16T08:04:00
Owner:
  - Eduardo Quinalha
---
# A camada de transporte

| Orientado a conexão | Confiável | **TCP** |
| --- | --- | --- |
|   | não confiável | SIP (aplicação) |
| Não orientado a conexão | Confiável |   |
|   | não confiável | **UDP** |

- Comunicação fim a fim
- **Controle de fluxo**
- Correção de dados
- Portas
	- Utilizado por todos os protocolos da camada de transporte
	- Ligação entre processos e camadas de rede
- Socket
	- Combinação de Endereço IP + Porta + Protocolo de transporte vinculado a cada processo em execução no dispositivo
- Portas
	- NTP → 123/UDP
	- FTP (dados) → 20/TCP UDP
	- IMAP → 143

# Controle de Fluxo vs Controle de Congestionamento

- **Controle de fluxo:**
	- **Camada 2:** Implementado em protocolos como Ethernet e PPP.
	- **Camada 4:** Implementado em protocolos como TCP e UDP.
- **Controle de congestionamento:**
	- **Camada 3:** Implementado em protocolos como IP e ICMP.
- O controle de fluxo pode ser implementado em diferentes camadas, dependendo do protocolo específico.
- O controle de congestionamento é geralmente implementado na camada 3, mas também pode ser implementado em outras camadas.

## Controle de Fluxo

- Gerencia o fluxo de dados **entre dois hosts específicos **em uma comunicação
- Visa evitar que um host envie dados mais rapidamente do que o outro pode receber

**Mecanismos de Controle de Fluxo:**

- **Janela deslizante:** Define um limite para a quantidade de dados que um host pode enviar sem receber um aviso do outro host.
- **Controle de taxa:** Limita a taxa de envio de dados de um host.
- **Parada e espera:** O receptor envia um ACK para cada pacote recebido. O remetente só envia o próximo pacote após receber o ACK.

**Exemplos:**

- **TCP Tahoe:** Usa um algoritmo de controle de congestionamento de "**janela deslizante**" para controlar o fluxo de dados.

## Controle de Congestionamento

- Gerencia o fluxo de dados em** toda a rede**, evitando o congestionamento em links e roteadores
- Visa otimizar o uso da largura de banda disponível e evitar a perda de pacotes

**Mecanismos de Controle de Congestionamento:**

- **Algoritmos de controle de congestionamento:** Ajustam a taxa de envio de dados de acordo com o estado da rede.
- **Descarte de pacotes:** Roteadores descartam pacotes quando a fila de espera excede um limite.
- **Roteamento dinâmico:** Roteadores ajustam suas rotas para evitar links congestionados.

**Exemplos:**

- **RED (Random Early Detection):** Algoritmo de controle de congestionamento que descarta pacotes de forma aleatória para evitar congestionamento.

# UDP

> [!tip] 💡
> Para o UDP a porta de origem é **OPCIONAL** no cabeçalho, uma vez que ele não é orientado à conexão e não espera uma resposta do servidor

- Mais rápido
- Não orientado a conexão
- Não confiável: Não garante a entrega
- Sem controle de fluxo: Não garante a sequencia
- Cabeçalho:
	- 8 Bytes de cabeçalho
![[TCP, UDP, SCTP e RTP synced block]]

# TCP - Transmission Control Protocol

[https://www.maxwell.vrac.puc-rio.br/5751/5751_3.PDF](https://www.maxwell.vrac.puc-rio.br/5751/5751_3.PDF)

- **Confiável**: Confirmação de entrega
- **Orientado à conexão:** Estabelece conexão com o 3 way handshake
- **Verificação de erros**
- **Recuperação de perda de pacotes:** descarte de pacotes duplicados
- **Controle de fluxo:** janela deslizante
	- Controla a ordenação dos pacotes
- **Comunicação ponto a ponto**

> [!tip] 💡
> Os campos de sequencia de dados Seq number e Ack number **são contabilizados em Bytes. **Assim, o envio de um segmento cuja seq seja 92 e tenha 8 bytes de dados, implica em um ACK de valor 100

## Cabeçalho

- Tamanho: 20 bytes

![[TCP, UDP, SCTP e RTP synced block 1]]

- Principais
	- Source Port
	- Dest Port
	- SEQ Number
		- 32 bits
		- Número de sequência para controle e confiabilidade
		- Número de sequência da perspectiva de quem iniciou a comunicação. Implica em uma resposta do outro lado com a mesma sequência no campo Ack Number
	- ACK Number
		- Número de sequência esperado
	- Data Offset
- Flags
	- URG
		- Prioridade de tráfego. Passa pelo buffer, mas com prioridade em relação aos outros
		- Trabalha em conjunto com o campo Urgent Pointer
	- ACK
		- Se ativado, lê o campo do acknowledgement
		- Caso contrário, o campo é ignorado
	- PSH
		- Faz com que o pacote vá direto para a próxima camada, sem passar pelo buffer
	- RST
		- Reinicia a conexão
	- SYN
		- Estabelecimento de conexão
	- FIN
		- Encerramento de conexão
- Window (16 bits)
	- Controle de fluxo
- Checksum
	- Detecção de erro de **todo o segmento**

## Campos de controle

- SEQ Number
- ACK Number
- ACK
- Window

## Estabelecimento da Conexão

- 3-Way-Handshake

![[Untitled 504.png]]

- Toda mensagem precisa de um número de sequência, mesmo que seja simplesmente para o estabelecimento de uma conexão
- Sequência: SYN → SYN, ACK → ACK
	1. Cliente envia um segmento com a flag SYN e um número de sequência X gerado por ele no campo SEQ Number
	2. Servidor responde com as flags SYN e ACK (sempre que tiver flag ACK, tem que ler o campo Ack number). No ack number vai X+1 sinalizando a continuidade da sequencia gerada pelo cliente e um novo SEQ number Y, gerador pelo servidor (as perspectivas são diferentes. X → Dados do cliente, Y → dados do servidor)
	3. Cliente responde com um ACK e Ack number Y+1, dando continuidade na mensagem recebida do servidor, e Seq number X+1 (continuidade na mensagem enviada pelo cliente) e assim já pode enviar dados.
> [!tip] 💡
> **OBS**: Apesar do exemplo X+1 e Y+1, os campos são contabilizados em bytes e o ack será sempre SEQ + Tamanho da informação em Bytes
- A porta de destino deve estar no estado LISTENING (porta aberta)

## Encerramento de Conexão

- Qualquer uma das partes pode encerrar a conexão

![[Untitled 505.png]]

- Simétrico
	- Pode acontecer em 4 ou 3 vias (3 way handshaking ou 4 way handshaking)
	- 3 vias ocorre igual ao 3-way-handshake: FIN → FIN/ACK → ACK
	- 4 vias: FIN, ACK, FIN, ACK
- Assimétrico
	- Envio de um único segmento com a flag RST, porém sem abrir uma nova conexão

## Estados

![[Untitled 506.png]]

![[Untitled 507.png]]

## Segmentação

- MSS - Max Segment Size
- Busca evitar a fragmentação na camada de rede pelos nós intermediários
- Ocorre fim a fim

## Sequenciamento e Controle de Fluxo

- RTT - Roundtrip Time → Tempo de espera de uma resposta
- Cenário 1
	- Sender envia um pacote, porém este não chega ao receiver
	- Receiver não tendo conhecimento do envio, não manda a resposta
	- Ocorre um timeout no Sender, uma vez que não recebeu a confirmação
	- Sender dispara novamente o pacote
- Cenário 2
	- Sender envia o pacote
	- Receiver recebe e envia a confirmação (ACK), porém esta não chega no sender
	- Ocorre um timeout e o Sender envia novamente o pacote
	- Ocorre uma duplicação do pacote no receiver
- **Janela Deslizante**
	- Contabilização feita em bytes **Perdas de pacotes utilizando janela deslizante**
![[Untitled 508.png]]
- Timeout
- Recebimento de 3 acks iguais
- **Go back N: **
	- Descarta todos os segmentos recebidos após um não recebido
	- O remetente envia novamente o pacote faltante e todos os seguintes
- **Retransmissão seletiva:**
	- Quando há perda de um pacote, o destino começa a armazenar em buffer os segmentos seguintes e aguarda a retransmissão pelo remetente
	- Não há retransmissão dos pacotes seguintes
	- Os pacotes podem ser reordenados

## Técnicas de controle da janela deslizante

- Tamanho inicial da janela (por RFC): 1MSS → 1 segmento
- **Partida lenta** (técnica padrão)
	- Incremento do tamanho de 1MSS para cada ACK recebido
	- Duplica o tamanho a cada ack recebido
	- Crescimento exponencial
	- Valor limite 64 KB
	- Ou seja, começa crescendo exponencialmente até 64KB, passando deste valor segue um crescimento linear
	- Caso haja perda durante o processo, redefine o valor do limiar para a metade do valor **corrente **da janela
![[Untitled 509.png]]
![[Untitled 510.png]]

## Recuperação rápida

- TCP tradicional TAHOE → Usa partida lenta com recuperação do zero,
- TCP novo RENO → Na ocorrência de erro, recalcula o limiar para metade do valor corrente da janela e retorna deste valor, já na fase de prevenção de congestionamento (aumento linear)

![[Untitled 511.png]]

![[Untitled 512.png]]

Resp: A

# SCTP - Stream Control Transmission Protocol

- Intermediário entre TCP e UDP
- Não é tão burocrático como o TCP, mas implementa alguns métodos de controle
- É confiável (reconhecimento das mensagens transmitidas)
- Orientado a conexão
- 4 way handshaking
- O encerramento se dá somente a partir da origem
- suporta apenas NAT estático
- Conceitos novos
	- Multihoming: Múltiplos endereços IP’s para um mesmo destino
	- Multistreaming: Em uma mesma conexão, diversos fluxos de dados
- A PDU é tratada como Pacote
- Vários chunks (fluxo de dados) podem ser multiplexados dentro de um mesmo pacote SCTP
- Um chunk pode ter informações de controle e dados

![[Untitled 513.png]]

- Header fixo: 12 bytes

# RTP

**RTP (Real Time Protocol) tem como função básica multiplexar diversos fluxos de dados em tempo real sobre um único fluxo de pacotes UDP.**

Não há nenhuma garantia especial sobre a entrega, pacotes podem ser perdidos, alterados, atrasados.

Para isso usamos em conjunto o protocolo RTCP (Real Time Control Protocol) que cuida do feedback, da sincronização e da interface do usuário de uma comunicação por RTP, mas não transporte nenhuma mídia.

Bons estudos!
