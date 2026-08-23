---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2026-08-06T09:27:00
Owner:
  - Eduardo Quinalha
---
# O que é?

- Framework de modelagem
- Linguagem de especificação
- Independente de tecnologia
- Diminui a fragmentação, aumenta a padronização
- Padrão aberto

# Visões de Sistemas

- Organização da arquitetura, direcionando cada visão a um conjunto de interesses específico

| Visão | Objetivo (ponto de vista do …) |
| --- | --- |
| Lógica (de projeto) | **Usuário Final**. Requisitos funcionais. Diagramas: `Classe, Objeto, Pacotes` |
| De desenvolvimento | **Desenvolvedor**. Organização estática dos módulos que formam o software. `Diagramas: Componentes` |
| De processo | **Integrador**. Requisitos não funcionais. Diagramas: `Sequência, Estrutura composta, Máquina de Estados e Atividade.` |
| Física (ou de implantação) | **Engenheiro de Sistemas.** Topologia, distribuição física. Diagramas: `Implantação e Componentes.` |
| De casos de uso | **Todos os usuários**. Diagramas: `Casos de Uso.` |

# Diagramas

![[image 123.png]]

- 7 Estáticos (estruturais)
- 7 Dinâmicos (comportamentais)

## Diagrama de Classes

> [!note] 🔥
> Cai muito em prova

- Elementos mais importantes de um sistema orientado a objetos
- Classes, interfaces e relacionamentos
- Métodos e atributos

![[Untitled 612.png]]

- A única coisa obrigatória na representação é o nome da classe

![[Untitled 613.png]]

- Qualificadores
	- Atributo <u>estático </u>→ Pertence à classe (comum a todos os objetos)
	- Operações *abstratas → *Será implementado por outra classe herdeira
	- Público (+)
	- Protegido (#)
	- Pacote (~)
	- Privado (-)
- Relacionamentos
	- Associação
		- Simples
![[Untitled 614.png]]
		- Agregação
			- Relacionamento do tipo “todo-parte”
			- Sinalizado por um diamante
			- O diamante sempre está no lado do “Todo”
			- As partes que compõem o todo tem seu ciclo de vida independente
![[Untitled 615.png]]
			- Neste exemplo, pessoas não deixam de existir sem o clube
		- Composição
			- Também é um relacionamento “todo-parte”
			- Sinalizado pelo diamante fechado
			- As partes não existem (ou não fazem sentido) sem o todo
			- As partes não podem ser compartilhadas em outros relacionamentos
![[Untitled 616.png]]
	- **Dependência**
		- **Mudança em um elemento pode causar mudanças no outro**
![[Untitled 617.png]]
		- Pode ocorrer entre classe e interface
	- Generalização
		- Herança
		- Sinalizado pela linha com seta fechada, no lado da classe mais genérica
![[Untitled 618.png]]
	- restrições sobre herança/generalizações:
		- overlapping ( sobreposição) : o objeto da superclasse pode existir simultaneamente em suas subclasses.
		- disjuntiva (disjoint): o objeto da superclasse só pode ser instanciado por uma das subclasses.
		- completa : todas as subclasses já estão descritas;
		- incompleta: ainda podem existir mais subclasses.
![[Untitled 619.png]]
	- Realização
		- Ocorre quando uma classe implementa uma interface
		- Linha pontilhada, seta fechada
![[Untitled 620.png]]

## Diagrama de Objetos

- Representa uma fotografia de um dado instante do sistema
- Instância do diagrama de classes
- **Não se representa os métodos no diagrama de objetos**

![[Untitled 621.png]]

- Padrão de nomes:

![[Untitled 622.png]]

## Diagrama de Componentes

- Modelagem em termos de componentes e seus relacionamentos
- Decomposição em subsistemas que detalham a estrutura interna
- Alguns componentes existem em tempo de ligação (compilação) e outros em tempo de execução

![[Untitled 623.png]]

- Os relacionamentos são os mesmos do diagrama de classes

![[Untitled 624.png]]

![[Untitled 625.png]]

## Diagrama de Pacotes

- Pacotes permitem agrupar qualquer construção
- Pode ilustrar relações de dependência entre pacotes

## Diagrama de implantação

- Modela a configuração física do sistema
- Detalha quais elementos de software rodam em quais equipamentos físicos
- Inclui
	- Nós
		- Hardware
		- Ambiente
	- Artefatos
		- Código fonte
		- Executáveis

![[Untitled 626.png]]

## Diagrama de Estrutura Composta

- Surgiu na UML 2.0
- Usado para** modelar colaboração** entre interfaces, objetos e classes

![[Untitled 627.png]]

- Usado no modelamento de hardware

## Diagrama de Perfis

- Diagrama auxiliar
- Define estereótipos
	- << >>
	- { }
- Permite adaptar os modelos para diferentes plataformas e domínios

## Diagrama de Casos de Uso

- Diagrama de comportamento
- Agrupamento de requisitos
- Funcionalidades
- Atores
- Casos de uso abstratos são representados em *itálico*
- Relações
	- Extend → Opcional ou baseada em gatilhos
![[Untitled 628.png]]
	- Include → Inclusão obrigatória
![[Untitled 629.png]]
	- Generalização ou herança → Pode ser em atores ou casos de uso
![[Untitled 630.png]]
	- Dependência
![[Untitled 631.png]]

### Caso de Uso 2.0

- é uma evolução do modelo tradicional de casos de uso, que busca oferecer uma abordagem mais **ágil **e **iterativa **para o desenvolvimento de software, mantendo o foco na entrega de valor ao usuário final.
- foi proposta para superar algumas limitações dos modelos tradicionais de casos de uso, especialmente em ambientes de **desenvolvimento ágil.**
- Características
	- enfatiza o desenvolvimento incremental e iterativo.
	- Propõe dividir os casos de uso em pedaços menores e mais gerenciáveis, chamados de "**fatias de caso de uso**" (use case slices), que podem ser implementadas e testadas em ciclos curtos.
	- Permite que os casos de uso sejam facilmente integrados no backlog do produto e priorizados conforme as necessidades do projeto.
- Fatias de Casos de Uso
	- Pequena parte funcional de um caso de uso que pode ser desenvolvida e entregue de forma independente.
	- Cada fatia representa um incremento no sistema que é utilizável e agrega valor ao usuário
	- Isso permite que o desenvolvimento progrida de forma incremental, com feedback constante.

## Diagrama de Atividades

- Descreve lógicas de procedimento
- Processos de negócio
- Fluxos de trabalho **Workflow**
- Permite mostrar responsabilidades por meio de raias
- O diagrama representa uma atividade
- Uma atividade se divide em n ações

![[Untitled 632.png]]

![[Untitled 633.png]]

- **Junção**: Só permite prosseguir quando todas as entradas forem finalizadas
![[Untitled 634.png]]
- **Merge:** entradas seguem de forma independente
![[Untitled 635.png]]

## Diagrama de Máquina de Estados

- Mostra os vários estados possíveis por qual o objeto pode passar
- Ilustra somente 1 objeto por vez
- Elementos
	- Estados
	- Transições
		- Pode-se ter eventos associados
		- evento [condição de guarda] / ação
	- Ações
		- Ao passar de um estado para outro, pode realizar ações
	- Atividades
![[Untitled 636.png]]
- Os retângulos podem ser divididos em até 3 compartimentos:
	- nome, comportamento interno, transição interna
- Estado composto
![[image 124.png]]
	- Significa que o estado interno é composto por mais de um estado

## Diagrama de sequência

> [!tip] 💡
> Cai muito em prova

- Diagrama comportamental e de interação
- Ilustra a ordem no tempo
- O tempo é ilustrado na vertical, de cima para baixo
	- Linha de vida
- Seta fechada → Mensagem síncrona
- Seta aberta → Mensagem assíncrona
- Retorno → Linha pontilhada
- Os retângulos superiores são os participantes (objetos)
- Os objetos são denotados como **nome****:****classe**
- As barras na linha de vida são a ativação dos participantes
- o diagrama de sequência **permite mostrar a resposta de um sistema para um ator,** representando assim a comunicação bidirecional.
- é possível representar a **comunicação entre atores **no diagrama de sequência para fins ilustrativos, mesmo que este fluxo não faça parte do sistema em si.

![[Untitled 637.png]]

- Um participante pode ser instanciado ou destruído durante a linha de vida

![[Untitled 638.png]]

- Fragmentos combinados
	- são uma forma de adicionar lógica condicional ou de controle de fluxo, como loops, ramificações e paralelismo.
	- são utilizados para representar partes específicas do fluxo em um diagrama de sequência, onde comportamentos distintos podem acontecer dependendo de certas condições ou interações entre os objetos
	- O operador **Alt**, que é um dos vários operadores de interação em UML, é utilizado em um **fragmento combinado** para indicar fluxos alternativos dentro de um diagrama de sequência.
![[Untitled 639.png]]

## Diagrama de Comunicação

- **O Diagrama de colaboração mudou de nome na UML 2.0 e virou o diagrama de comunicação.**
	- Isto porque ele não ilustra bem a colaboração
	- **Quem faz isto é o diagrama de estrutura composta**
- ênfase na ordem estrutural das mensagens
- Mostra objeto e mensagens trocadas entre eles
- Melhora a legibilidade na perspectiva das trocas de mensagens

![[Untitled 640.png]]

## Diagrama de Tempo

- Comportamento dos objetos ao longo do tempo
- Duração do estado
- Restrição de tempo das iterações

![[Untitled 641.png]]

## Diagrama de Interação Geral

- Diagrama misto
	- Sequência
	- Atividade
- Workflow

![[Untitled 642.png]]

# Object Constraint Language

- Extensão da UML
- Representa as restrições sobre objetos
- Linguagem declarativa
- Modelos mais completos
- Pode ser convertido em código