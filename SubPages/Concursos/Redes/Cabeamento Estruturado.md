---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2024-08-26T18:26:00
Owner:
  - Eduardo Quinalha
---
## **Meios guiados**

Nomenclatura: Velocidade|Banda|Meio

# Cabo Coaxial

- 10BASE2
	- 10 MBPS
	- Cabo coaxial fino
	- 185m de alcance
- 10BASE5
	- 10 MBPS
	- Cabo coaxial grosso
	- 500m

> [!note] 🔥
> Cabos coaxiais ainda são considerados como meio de transmissão de banda larga e alta imunidade a ruídos.

> **2.2.3 Cabo Coaxial**
> Outro meio de transmissão comum é o cabo coaxial (conhecido por muitos apenas como ‘coax’). Ele tem **melhor blindagem que os pares trançados** e, assim, pode se estender por distâncias mais longas em **velocidades mais altas**. Dois tipos de cabo coaxial são amplamente utilizados. Um deles, o cabo de **50 ohms**, é comumente empregado nas transmissões digitais. O outro tipo, o cabo de **75 ohms**, é usado com frequência nas transmissões analógicas e de televisão a cabo. Essa distinção se baseia mais em fatores históricos do que técnicos (por exemplo, as primeiras antenas dipolo tinham uma impedância de 300 ohms e era fácil desenvolver transformadores de casamento de impedância de 4:1). Começando em meados da década de 1990, as operadoras de TV a cabo começaram a oferecer acesso à Internet por cabo, o que tornou o cabo de 75 ohms mais importante para a comunicação de dados. Um cabo coaxial consiste em um fio de cobre esticado na parte central, protegido por um material isolante. O isolante é envolvido por um condutor cilíndrico, geralmente  como uma malha sólida entrelaçada. O condutor externo é coberto por uma camada plástica protetora. A Figura 2.3 apresenta uma vista de corte de um cabo coaxial. A construção e a blindagem do cabo coaxial proporcionam a ele uma boa combinação de **alta largura de banda e excelente imunidade ao ruído.** A largura de banda possível depende da qualidade e do tamanho do cabo. Os cabos modernos têm uma largura de banda de até alguns GHz. Os cabos coaxiais eram muito usados no sistema telefônico para linhas de longa distância, mas agora estão sendo substituídos por fibras ópticas nas rotas de longa distância. Porém, os cabos coaxiais ainda são usados em larga escala pelas redes de televisão a cabo e em redes metropolitanas.

# Par trançado

- Melhor custo benefício
- Maior velocidade quando comparados aos coaxiais
- são maleáveis
- Tranças em 4 pares trançados para diminuir a interferência

> [!note] 🔥
> Interpretando: 100BASE-TX / 100BASE-T
100 → Velocidade
BASE → Banda Base
TX → 2 pares
T → 4 pares

- **Categorias**
	- UTP
		- Unshielded (sem blindagem)
		- Em geral a distância máxima é de 100m a única exceção é no CAT6 para 10Gb

| **Categoria** | **Freqüência** | **Padrão** | **Obs** |
| --- | --- | --- | --- |
| **CAT5** | 100 MHz | 100BASE-TX |   |
| **CAT5E** | 125 MHz | 1000BASE-T |   |
| **CAT6** | 250 MHz | 1000BASE-TX | Protótipo de 10GBPS porém com alcance de apenas 55m |
| **CAT6A** | 500 MHz | 10GBASE-T |   |
| **CAT7 e CAT7A** | 600 - 700 MHz e 1000MHz | 100GBASE-T |   |
	- FTP
		- Blindagem simples
		- Previne interferência externa (entre outros cabos)
	- STP
		- Blindagem nos pares
		- Previne interferência entre pares (crosstalk)
	- SSTP ou SFTP
		- Blindagem dupla entre pares e externa

<!-- Column 1 -->
![[Untitled 481.png]]

<!-- Column 2 -->
![[Untitled 482.png]]

# Fibra Ótica

Sofre influência da reflexão e refração

## **Fontes**

- LED
	- Mais barato
	- Menos eficiente
	- Mais durável
- LASER
	- Mais caro
	- Mais eficiente
	- Menos durável (mais sensível)
	- Maior dificuldade de acoplamento
	- Maior taxa de transmissão

## **Tipos**

Modos são faixas de frequência distintas. Os tempos de chegada de cada modo são distintos, provocando um alargamento do espectro

### **Multimodo (MMF)**

Tipo de fibra mais comum de ser utilizado para conexões em curtas distâncias

- Maior diâmetro
	- 50 a 62,5 mícrons
- Mais baratas
- Mais maleáveis
- Maior dispersão
- Distâncias
	- 300 m (10 Gbps)
	- 550 m (1 Gbps)
	- Há casos de uso de até 2km
- Perfis
	- degrau
		- O núcleo é um pouco maior que a de índice gradual
		- Menores distâncias
		- Menores velocidades
		- Mais modos
	- gradual
		- Núcleo um pouco menor
		- Maiores distâncias
		- Maiores velocidades
		- Menos modos
- Tipos de multimodos

> [!note] 🔥
> OM1: Alta mabealidade, núcleo maior, LED
OM2: Núcleo menor, maior banda, LED
OM3: Maior banda, LASER
OM4: Maior banda, LASER

![[Untitled 483.png]]

### Monomodo (SMF)

- Na prática ainda existem modos, porém numa quantidade muito menor que a fibra multimodo
- Diâmetros menores (8 a 10 mícrons)
- Mais caras e maleáveis
- **Não tem dispersão modal**
- Distâncias
	- 80 km (10 Gbps)
	- 40 km (100 Gbps)

**Padrões**

> [!note] 🔥
> 100BASE-(SFBL)X / 1000BASE-(SL)X

SFBL - SL
100 Se for Bloquear a Luz - 1000 Só Luz

![[Untitled 484.png]]

### **Janelas**

- 850 um
- 1310 um
- 1550 um

---

# Cabeamento Estruturado

[https://www.osetoreletrico.com.br/normas-para-cabeamento-estruturado/](https://www.osetoreletrico.com.br/normas-para-cabeamento-estruturado/)

# Normas

- ABNT NBR 14565 → Edifícios e Data centers
	- Baseia-se nas normas ISO/IEC 11801 e 24764
- ABNT NBR 14264 → Residências

## ABNT NBR 14565

- Edifícios
- Data centers
- Cabeamentos metálicos e óticos
- **Elementos funcionais**
	- Distribuidor de Campus (CD)
	- Backbone de Campus
	- Distribuidor de Edifíco (BD)
	- Backbone de edifício
	- Distribuidor de piso (FD)
	- Cabeamento horizontal
	- Ponto de consolidação (CP)
	- Cabo do ponto de consolidação
	- Tomada de telecomunicações multiusuário (MUTO)
	- Tomada de telecomunicações (TO)
	- Equipamento terminal (TE) → Não faz parte da norma
![[Untitled 485.png]]
![[Untitled 486.png]]
- E**lementos funcionais para data centers**
	- Interface de rede externa (ENI)
	- Cabo de acesso à rede
	- Distribuidor principal (MD)
	- Distribuidor de Zona (ZD)
	- Ponto de distribuição local (LDP)
	- Tomada de equipamento (EO)
![[Untitled 487.png]]
![[Untitled 488.png]]

## Subsistemas de cabeamento

- Devem ser utilizados cabeamentos de par trançado ou fibra ótica
- Tipos
	- **Backbone de campus**
		- necessários cabos com maior proteção mecânica
		- Na maioria dos casos, estes cabos não podem ser utilizados dentro de edifícios por propagarem chamas e liberar fumaça tóxica em caso de incêndio
	- **Backbone de edifício**
		- Interliga TR com ER
		- Topologia estrela
		- Não é obrigatório que um CD interligue a um BD no mesmo edifício, podendo conectar diretamente aos FD
		- CD não pode estar conectado a FD em outro edifício
		- Também é possível conectar BD diretamente às TO
	- **Cabeamento horizontal**
		- Obrigatório topologia em estrela
		- Soma dos patch cords → Máximo 10 m
		- Soma dos patch cords + cabeamento horizontal → Máximo 100m
		- Cabeamento horizontal → Máximo 90m
			- Somente cabo par trançado rígido
			- Cabos flexíveis sofrem maior atenuação
		- Óptico:
			- Fibras MM OM3 ou OM4
		- Admite um ponto de consolidação (CP)
			- Sob o piso elevado ou teto falso
			- Mínimo de 15m do distribuidor de piso
			- Mínimo de 5m até a área de trabalho
		- MUTO
			- Até 12 áreas de trabalho
			- Neste caso, patch cord pode chegar até 20m
	- **Cabeamento Vertical**
		- **As quatro opções de mídia para um cabeamento backbone são:**
			- **cabo de par trançado** de 100-ohm não-blindado (**UTP**) (não excedendo 800 metros)
			- **cabo de par trançado** de 150-ohm blindado (**STP**) (não excedendo 700 metros)
			- **cabo coaxial** de 50-ohm (não excedendo 500 metros)
			- **fibra ótica **de 62.5/125um multi-modo (não excedendo 2,000 metros)

## Espaços

- **Sala de equipamentos (ER)**
	- Equipamentos gerais
	- Switches Core
	- Abriga o CD ou BD
	- Pode ser um data center
- **Sala de telecomunicações (TR)**
	- Abriga o FD
	- É recomendado que exista uma TR por piso, no entanto, em edifícios em que isto não seja possível, uma TR pode atender o próprio piso e os adjacentes
	- Além disto, foi visto que o BD pode atender diretamente às TO’s, neste caso, também dispensaria a existência de uma TR
- **Área de trabalho (WA)**
	- Cada área de trabalho deve ter 2 tomadas de telecomunicações:
		- 1 - cabo CAT5e ou superior, U/UTP ou F/UTP
		- A outra pode ser:
			- cabo CAT5e ou superior, U/UTP ou F/UTP
			- cabo de categorias superiores, U/UTP ou F/UTP
			- fibra multimodo OM-3 ou OM-4
			- fibra multimodo OM-1 (62,5/125um)
- **Sala de entrada e infraestrutura de entrada (EF)**
	- Sala onde ocorre a ligação do Backbone de Edifício com o Backbone de Campus
	- Pode ser utilizada para interligação com link da operadora (ENI)

## Classes de desempenho

| **Classe** | **Categoria de cabo** |
| --- | --- |
| C | CAT 3 |
| D | CAT 5e |
| E | CAT 6 |
| EA | CAT 6A |
| F | CAT 7 |

## Requisitos de desempenho

### Perda de Inserção

- Não é linearmente proporcional ao comprimento do cabo

### Perda de Retorno

- Causado por descasamento de impedâncias
- Varia com a frequência

### Diafonia (Crosstalk)

- Acoplamentos indutivos e capacitivos
- Maior fator limitante de desempenho em cabos de pares trançados
- Não pode ser eliminada, porém pode ser reduzida:
	- Uso de terminações balanceadas
	- Entrelaçamento dos pares com diferentes passos de torção
	- Uso de cabos blindados

### Atraso de propagação

- Tempo que o sinal leva para percorrer o trecho de cabo
- Diretamente associado aos parâmetros primários do cabo:  resistência, indutância, capacitância e condutância)

### Delay Skew

- Diferença entre os atrasos de propagação dos pares mais rápido e mais lento em um cabo balanceado de 4 pares

# GPON

**GPON** é a sigla em inglês de Gigabit-capable Passive Optical Network, ou Rede Óptica Passiva com Capacidade de conexão em Gigabits. Também conhecido como G.984, é um dos padrões possíveis para a topologia de rede PON, ou Passive Optical Network (Rede Óptica Passiva).

Para entender o que é GPON, é preciso primeiro entender o que é **PON.** Por ser uma rede passiva, isso significa que o splitter, responsável por redistribuir a conexão entre o concentrador de rede da operadora (Optical Line Terminal, ou OLT) e o receptor do usuário (Optical Network Unit, ou ONU, também chamado de Optical Network Terminal, ou ONT) não é energizado.

Por não existir uma corrente elétrica na estrutura da rede, é possível usar bem menos infraestrutura do que uma rede tradicional na “última milha”, a distância final entre o provedor e o consumidor, bem como o risco de acidentes é menor.