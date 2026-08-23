---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2024-11-19T10:40:00
Owner:
  - Eduardo Quinalha
---
# Camada de Rede:

- Prover acesso ao meio físico
- Controle de fluxo
- Métodos de identificação e correção de erro

# Técnicas de Detecção e Correção de erro

- **Paridade**
	- Utiliza um bit de controle
	- Possibilita apenas detectar o erro. Sem possibilidade de correção
	- Não consegue detectar em qual bit o erro ocorreu
	- Se um número par de bits com erros acontecerem, o erro pode passar despercebido
	- Paridade Par → Um número par de bits 1 foi transmitido
	- Paridade Ímpar → Um número ímpar de bits 1 foi transmitido
- **Checksum**
	- Muito utilizado na camada 4 (transporte)
	- Baixo processamento
		- Utilizado quando e dá a nível de software
	- Transmite a soma de duas palavras (binário) e a inversão desta soma
	- No RX, a soma com a inversão transmitida tem que resultar numa sequencia de 1`s
- **Verificação de redundância cíclica (CRC)**
	- Exige bastante processamento
	- Mais eficiente
	- Ocorre a nível de hardware (camada de acesso)
	- A quantidade de bits define o padrão
		- CRC 8, CRC 12, CRC 16 ou CRC 32 (usado no padrão ethernet)
- **Distância de Hamming**
	- Define a quantidade de bits a serem corrigidos

# Endereçamento da Camada de Acesso à Rede

- **Mac Address**
- A primeira metade (3 bytes) destina-se à identifação do fabricante
- **Broadcast**: FF:FF:FF:FF:FF:FF
- **Multicast**
	- O bit 0 do primeiro octeto é reservado para broadcast ou multicast
		- 1: Multicast ou broadcast
		- 0: Unicast
![[Untitled 514.png]]
	- Para o multicast especificamente, o mac address deverá começar com o endereço **01:00:5E, **ou seja, 24 bits são ocupados para marcar o quadro como multicast. O bit mais significativo dos outros 24 restantes não é utilizado, portanto apenas os últimos 23 bits mapeiam o segmento de multicast
![[Untitled 515.png]]

# Ethernet - IEEE 802.3

- Estrutura semelhante ao IEEE 802.3 (algumas bancas trata como sendo o mesmo)
- Utiliza código manchester na codificação dos bits
- Auto negociação: os hardwares negociam entre si a velocidade e a forma (half/full duplex)
- Payload típico: 1500 bytes
	- Jumbo frames: até 9000 bytes
		- No padrão Gigabit Ethernet
		- Tende a diminuir o processamento no hardware receptor
		- Como o frame é maior, o número de frames reduz, consequentemente o processamento também
- Em relação ao IEEE 802.11 (wireless), é semelhante, a diferença reside na camada física e na subcamada MAC
	- **A subcamada LLC é a mesma**

## **Princiopais variantes**

- 802.3az: Green Ethernet → capacidades de gerenciamento de potência e economia de energia
- 802.3af: Power Over Ethernet
- 802.3ad: Link Aggregation

## **Cabeçalho**

> [!note] 🔥
> O tamanho do frame (header + payload) é de 1518 B (ou 1522 após a revisão de 99 que incluiu o VLAN TAG). O tamanho do payload máximo é 1500 B, e o mínimo é de 46 B

![[Camada 2 synced block]]

> [!note] 🔥
> Além do frame, existe um sinal especial para indicar a chegada de um novo quadro, o preâmbulo, de tamanho 7 bytes com bits alternados 1 e 0, acrescido de um 8 bit 1 chamado SFD

> [!note] 🔥
> Quando a mensagem tem um tamanho menor que 46 bytes, é necessário preencher o payload com 0 a fim de alcançar o tamanho mínimo do quadro ethernet (64 bytes). Esta técnica chama-se **padding**

## **Modos de operação**

- Store-and-forward
	- Mais lento
	- Maior latência
	- Cálculo de CRC
	- Aumenta a confiabilidade da rede
- Cut-Through ou Fast Forward
	- Lê apenas os 6 primeiros bytes, até identificar o MAC de destino (Desconsiderando o preâmbulo)
- Fragment-Free
	- Lê os primeiros 64 bytes (tamanho mínimo de frame do padrão)
	- Estatisticamente, se não houve erro nos primeiros 64 bytes, dificilmente haverá erro nos restantes
- Adaptative Cut-Through
	- Faz a comutação automática entre os modos

## Late Collision

- Quando a colisão é detectada após os primeiros 64 bytes
- Significa que o pacote jam não teve tempo suficiente de trafegar por toda a rede antes de ser detectado
- Pode significar segmentos maiores que o padrão

## Gigabit Ethernet

- **extensão de portadora**
	- essencialmente informa ao hardware para adicionar seu próprio preenchimento ao quadro normal, a fim de estendê-lo para 512 bytes.
- **rajada de quadros**
	- permite a um transmissor enviar uma sequência concatenada de vários quadros em uma única transmissão.
	- característica opcional
	- uma estação pode transmitir vários pacotes para o meio físico sem perder o controle. 
	- A transmissão em rajada é feita preenchendo-se o espaço entre os quadros com bits, de maneira que o meio físico não fique livre para as outras estações transmitirem

# HDLC

- High Level Link Control
- Protocolo da camada de Enlace de Dados (Camada 2)
- Conexão de dispositivos ponto a ponto ou ponto - multi-ponto
- Baseado no SDLC
- Garante que os dados sejam entregues sem erros e na ordem correta
- Suporta Half e Full duplex.
- Utiliza janela deslizante

# PPP