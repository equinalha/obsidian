---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2024-08-26T18:26:00
Owner:
  - Eduardo Quinalha
---
## **Premissas básicas**

> [!note] 🔥
> **OSI** é um modelo de referência, especificação, teórico! Ao passo em que **TCP/IP **é uma implementação, arquitetura, pilha de protocolos

- Serviços - Cada camada presta serviços à camada superior
- Interfaces - Determina a forma de interação entre as camadas
- Protocolos - É a implementação do serviço propriamente dito
- **Camadas de HOST → 4 superiores**
- **Camadas de MEIO ou REDE → 3 inferiores**

![[Untitled 465.png]]

## Encapsulamento

- Os dados da camada superior são encapsulados na camada inferior
- Um cabeçalho é acrescido
- **PDU**
	- Protocol Data Unit
	- Cada camada tem uma definição de PDU
		- Camadas 7, 6, e 5
			- PDU = Dados
		- Camada 4 (transporte)
			- PDU = Segmento
		- Camada 3
			- PDU = Pacote
		- Camada 2
			- PDU = Quadro
		- Camada 1
			- PDU = bits

## 1- Camada Física

- Responsável por converter bits em sinais elétricos, ópticos ou eletromagnéticos
- Define critérios de
	- Interfaces de acesso ao meio
	- Cabeamento
- Formas de inserção de sinal no meio
	- SIMPLEX
	- HALF-DUPLEX
	- FULL-DUPLEX
		- Na prática trata-se de dois canais SIMPLEX simultâneos

## 2- Enlace

| **Característica** | **Com. por circuito** | **Com. por pacotes** |
| --- | --- | --- |
| Circuito dedicado | Sim | Não |
| Largura de banda | Fixo | Variável |
| Desperdício de banda | Sim | Não |
| Armazenamento nos nós | Não | Sim |
| Requer conexão prévia | Sim | Não |
| Congestionamento | Início da chamada | Em cada pacote |
| Ocorrência de atrasos | Em regra, não | Sim |
| Principais aplicações | Telefonia convencional | Internet, Videoconferências, VoIP |

- Provê um meio confiável
- Pode empregar técnicas de detecção e correção de erros
- **Não torna o meio livre de erros**
- Sequenciamento dos quadros a serem transmitidos
- Estabelece conexão entre dispositivos adjacentes

### **Comutação**

- Por Circuitos
	- A informação só é trafegada após o estabelecimento do circuito fim a fim
	- O circuito fica alocado por tempo indefinido, transmitindo ou não informações
	- Alocação de recursos
	- Não há concorrência
	- **Não depende de processamento nos nós intermediários**
	- Não necessita de controle de sequenciamento
		- Os pacotes chegam na mesma ordem em que são transmitidos
	- Os erros só serão tratados nas extremidades
	- Desperdício de banda nos períodos de ociosidade
- Por Pacotes
	- Fragmentação da mensagem em pacotes
	- Cada pacote pode seguir seu próprio caminho até o destino
	- Os pacotes podem chegar fora de ordem (Exige controle de sequenciamento)
	- Maior eficiência na ocupação do meio de forma compartilhada
	- Há processamento nos nós intermediários
		- Correção de erros
	- Via de regra, a informação demora mais tempo até o destino
	- Não há garantia de recursos do meio (taxa de transmissão fixa, por exemplo)
- Mensagens
	- Mesmos princípios da comutação por pacotes
	- **Não há fragmentação da mensagem!**
	- Depende de buffers nos nós intermediários

### **Subdivisão da camada de enlace**

- MAC - Media Access Control
	- Mais próximo da camada física
	- Meios necessários para o efetivo acesso ao meio
	- CSMA/CD e CSMA/CA
- LLC - Logical Link Control
	- Checagem e correção dos quadros
	- Sincronia dos pacotes
	- Relações lógicas entre os dispositivos
	- 3 Tipos
		- Não orientado a conexão e sem confirmação de entrega
		- Orientado a conexão com confirmação de entrega
		- Não orientado a conexão com confirmação de entrega

## 3- Rede

> [!note] 🔥
> A Fragmentação ocorre na camada de rede

- PDU também pode ser conhecida como datagrama
- Encaminhamento dos datagramas entre dois dispositivos de rede distintos
- Roteamento
- Pode ou não ter alguma implementação de controle de nível de qualidade
- **Fragmentação e remontagem dos pacotes**
	- Depende da capacidade de transmissão do meio MTU

## 4- Transporte

- Segmentação dos dados recebidos da camada superior
- Pode implementar
	- Controle de fluxos
	- Ordenação de pacotes
	- Detecção e correção de erros
- Utiliza MSS (Máx segment size) - Equivalente ao MTU
- Busca evitar a fragmentação de pacotes pelas camadas inferiores

## 5- Sessão

- PDU - Dados
- Implementa sessões
- Processos em execução nos dispositivos
- Sincronização
- Ponto de recupração

## 6- Apresentação

- Formatação dos dados
- Criptografia
- Compressão
- Modelagem e conversão dos dados para fornecer à camada de aplicação

## 7- Aplicação

- Permite a comunicação de aplicações e usuário com serviços de rede
- Recursos implementados a nível de software