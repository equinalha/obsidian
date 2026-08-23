---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2024-10-01T17:21:00
Owner:
  - Eduardo Quinalha
---
[Referência Oficial](https://www.omg.org/spec/BPMN/2.0/PDF)

> [!tip] 💡
> escritório de processos, ferramentas e tecnologias de gerenciamento de processos, tipologia dos processos e abordagens de melhoria de processos,

[http://www.bpmb.de/images/BPMN2_0_Poster_EN.pdf](http://www.bpmb.de/images/BPMN2_0_Poster_EN.pdf)

# BPM

- Dividido em 9 áreas de conhecimento e em duas perspectivas:
	- Perspectiva de Processo
		- Gerenciamento de Processos de Negócio
		- Modelagem de Processos
		- Análise de Processos
		- Desenho de Processos
		- Gerenciamento de Desempenho de Processos
		- Transformação de Processos
		- Tecnologias de BPM
	- Perspectiva Organizacional
		- Organização do Gerenciamento de Processos
		- Gerenciamento Corporativo de Processos
- Tipos de Processos
	- Primários / Operacionais / Essenciais
		- Orientados à atividade fim
	- Suporte
		- Gerenciamento financeiro, RH, TI e afins
	- Gerenciamento / Governança
		- Não entregam valor diretamente ao cliente, porém certificam-se do funcionamento efetivo e eficiente da organização
		- Buscam controlar as atividades de negócio
		- Conformidades, Riscos, BI

# Business Process Management Notation (BPMN)

- Baseado em flow chart
- Projetado para ser **entendido tanto por TI quanto por negócio**
- Representa **exclusivamente processos de negócio**
- Não serve para
	- Estrutura e recursos organizacionais
	- Repartições funcionais
	- Modelos de dados e informação
	- Estratégia
	- Regras de negócio
- Tipos de submodelos - Diagramas de interação
	- Orquestração
		- Processo Privado
![[Untitled 395.png]]
		- Processo público
			- Apenas as tarefas usadas para se comunicar com o outro participante estão incluídas
![[Untitled 396.png]]
![[Untitled 397.png]]
	- Coreografias
	- Quando atividades fazem parte de uma coreografia, a notação descreve as atividades como interações entre processos representadas por padrões de trocas de mensagens:
![[Untitled 398.png]]
	- Colaborações
![[Untitled 399.png]]

# Níveis

- **Nível 1 - Modelagem Descritiva**
	- Abstrata
	- Alto nível
	- Mapeamento mais simples do fluxo do processo
	- **Omite alguns caminhos de exceção**
	- Usa os principais conceitos:
		- pools, lanes, tarefas, subprocessos e fluxo
- **Nível 2 - Modelagem Analítica**
	- **Notação completa**
	- Descrição precisa do fluxo
	- Inclui caminhos de exceção e eventos
	- Omite detalhes técnicos
		- Estrutura de dados
		- Expressões
	- Pode ser usada para análise do processo e automação
- **Nível 3 - Modelagem Executável**
	- BPMN 2.0
	- Detalhes executáveis em atributos padrão

# Elementos

![[Untitled 400.png]]

## Objetos de fluxo

![[Untitled 401.png]]

- Eventos
	- Coisas que acontecem ao longo de um processo ou coreografia
	- Afetam o fluxo
	- Têm causa ou impacto
![[Untitled 402.png]]
- Gatilhos
	- Ações que podem disparar um evento
![[Untitled 403.png]]
- Atividades
	- Podem ser:
		- Tarefa
			- Tipo de atividade de menor granularidade
		- Subprocesso
			- Subprocesso incorporado – herda todas as características do processo em que está inserido, e não pode conter piscinas ou raias.
			- Subprocesso reutilizável – é uma referência ao diagrama de outro processo, indicando que está sendo reutilizado no fluxo em que está inserido.
			- Subprocesso eventual – representa um conjunto lógico de atividades que pode ou não acontecer durante a execução de um processo, e cujo início não está vinculado à sequência de atividades do fluxo, mas à ocorrência de um evento.
			- Subprocesso transacional – conjunto de atividades logicamente relacionadas que devem ser realizadas em uma única transação, como por exemplo, uma transação bancária.
![[Untitled 404.png]]
![[Untitled 405.png]]

## Objetos de conexão

![[Untitled 406.png]]

- Partições

![[Untitled 407.png]]

- Artefatos

![[Untitled 408.png]]

## Atividades

- Passos lógicos dentro de um processo
- Representado por um retângulo com cantos arredondados
- Pode ser de dois tipos:
	- Tarefa → Atômico
	- Subprocesso → Atividade composta
- Exemplos:

![[Untitled 409.png]]

![[Untitled 410.png]]

- Outras notações possíveis associadas:
	- Subprocessos associados ao símbolo ~ → Indicam que as tarefas não têm ordem definida
	- Símbolo de engrenagem dupla → Tarefa automática

## Eventos

- Algo que pode acontecer em um processo
- Associados a uma causa (trigger) ou impacto
- Representado por círculos

![[Untitled 411.png]]

- Exemplo

![[Untitled 412.png]]

## Gateways

- Controlam o fluxo
- Podem ser pontos de divergência ou convergência
- Representados por losangos
- Só podem ser conectados por fluxos de sequência (Não pode ser interligado por fluxo de mensagem)

![[Untitled 413.png]]

- **Exclusivo **→ Somente um dos ramos será executado, dependendo da condição:

![[Untitled 414.png]]

- **Inclusivo **→ Pode executar apenas um ou até mesmo os dois ramos em paralelo, dependendo de uma condição

![[Untitled 415.png]]

- **Paralelo **→ Os dois ramos serão executados em paralelo

![[Untitled 416.png]]

- O mesmo gateway utilizado na divergência, deverá ser utilizado na convergência, quando reunir os ramos novamente.

## Fluxo

- Ilustram a ordem (sequência)
- Conectam os objetos de fluxo

## Piscinas

- Todo diagrama possui ao menos uma piscina, mesmo que esteja com bordas invisíveis (piscina implícita)
- Cada piscina, contém um único processo

![[Untitled 417.png]]

- Fluxo de sequência (seta contínua) não pode atravessar piscinas:

![[Untitled 418.png]]

## Fluxo de mensagens

- Usado para representar troca de informações e mensagens entre processos e participantes (piscinas)
- Seta com linha tracejada

![[Untitled 419.png]]

- Fluxo de mensagem nunca ocorre dentro de uma mesma piscina

## Raias

- Subdivisão dentro de uma mesma piscina
- Distribui elementos do processo entre papéis internos

![[Untitled 420.png]]

# Artefatos

- Informações adicionais no processo
- Utiliza-se associações (setas com linhas pontilhadas)
- Não tem efeito direto no fluxo de sequência ou mensagem
- Dizem quais atividades precisam de uma informações e quais produzem

![[Untitled 421.png]]

![[Untitled 422.png]]

## Outros

![[Untitled 423.png]]

# EPC - **Event-Driven Process Chain**

- Outra linguagem utilizada para modelagem de processos

![[Untitled 424.png]]

![[Untitled 425.png]]

- Evento
![[Untitled 426.png]]
- Função
	- Descreve transformações de um estado inicial para um resultado
![[Untitled 427.png]]
- Operador
	- And – An and operation corresponds to activate all paths in the control flow concurrently.
	- Or – An or operator corresponds to activate one or more paths among control flows.
	- XOR – An XOR operator corresponds to make a decision on which path to choose among several control flows.
![[Untitled 428.png]]

# DMN - Decision Model and Notation

- descrever, criar e visualizar a tomada de decisão
- Também criada pela OMG (*Object Management Group*)
- **adequada para todos os setores de uma organização**, especialmente aqueles em que a tomada de decisão precisa ser executada com precisão,
- nas empresas em que a gestão de riscos e *compliance* fazem parte das tarefas críticas, **a DMN permite a incorporação de regulamentações governamentais, normas financeiras, ambientais e trabalhistas** para mitigar os riscos.
- DMN foi projetada para trabalhar em conjunto com o **BPMN**
- Enquanto BPMN, CMMN e DMN podem ser usados de forma independente, são cuidadosamente projetados para se complementarem
- BPMN, CMMN e DMN são referidas como a "tríplice coroa" dos padrões de melhoria de processos.
- Composta de 3 níveis
	- Requisitos
		- elementos utilizados na construção de diagramas
		- decisões, entradas de processo, fontes de conhecimento (regulamentação e política) e modelos de conhecimento empresarial (lógica de processo).
		- **define todas as decisões a serem tomadas**
	- Linguagem de expressão
		- O FEEL (***Friendly Enough Expression Language)*** é usado para escrever a lógica da decisão.
	- Nível lógico
		- **estabelece de forma concreta quais decisões serão necessárias**
![[Untitled 429.png]]