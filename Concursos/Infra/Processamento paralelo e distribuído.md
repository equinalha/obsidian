---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2024-09-19T07:53:00
Owner:
  - Eduardo Quinalha
---
# Paralelismo

## Conceitos

- Multitarefa
	- Execução de forma aparentemente simultânea
	- Ocorre o escalonamento e preempção
- Multiprogramação
	- Carregamento simultâneo de vários programas na memória
- Execução Concorrente
	- Apenas uma tarefa por vez
	- Uma CPU
- Execução Simultânea
	- Mais de uma tarefa por vez
	- Várias CPU’s

# Sistemas distribuídos

**Middleware: **Camada de software localizada entre o nível mais alto e a camada subjacente (frameworks, facilidades de comunicação, etc). Serve para ocultar do usuário que a aplicação é executada em máquinas distribuídas geograficamente e também a heterogeneidade dos sistemas operacionais.

**Principais características de um sistema distribuído:**

- Concorrência → diferentes nós do sistema distribuído executam em concorrência
- Os relógios locais não são iguais, a única forma de coordenação é por **troca de mensagens**
- Falhas independentes. Uma falha em um dos nós, não afeta os demais

**Desvantagens:**

- Maior custo de desenvolvimento
- Maior complexidade de desenvolvimento (maior chance de bugs)

## Sistemas operacionais de rede

- O usuário enxerga e tem conhecimento da existência de vários computadores (ou recursos)
- Cada computador pode executar um SO diferente
- Permite compartilhar recursos na rede

## Sistemas operacionais distribuídos

- Usuário desconhece onde os programas são executados ou armazenados
- Existência de um único SO em cada computador → Cluster
- Existência de mais de um SO → Grid + middleware
- A mesma aplicação pode ser executada em vários computadores

## Tipos de sistemas distribuídos

### Cluster

> [!note] 🔥
> Cluster é um sistema** fortemente acoplado
****Exemplo: Kubernetes**

- Compostos por uma coleção de computadores autônomos, interconectados, trabalhando em conjunto para processar uma tarefa
- Normalmente são sistemas homogêneos do ponto de vista de SO
- Compartilham a mesma rede
- Normalmente há um nó mestre (centralizador)

![[Processamento paralelo e distribuído synced block]]

- É recomendado que cada rede que conecta os nós de um cluster seja configurada como uma sub-rede IP independente, para garantir uma comunicação confiável e evitar problemas de colisão de pacotes e conflitos de endereços.

### Grid

- Descentralizado
- Fracamente acoplado
- Não há requisito de alta disponibilidade
- Distribuído (pode até ser mundialmente)
- Exemplo SETI

### Outros tópicos

**RMI:** Remote Method Invocation. Utilizado em sistemas de objetos distribuídos. Permite invocar métodos de objetos que estão fisicamente em outros computadores.

**CORBA:** Idem ao RMI, porém é a arquitetura padrão proposta pelo Object Management Group (OMG). Permite a troca de dados entre sistemas distribuídos e heterogêneos.

# Sistemas Paralelos

## SMP

SMP é uma sigla que designa computadores com mais de um processador com as mesmas características, daí o termo Symetric Multi Processor.Requer máquinas com dois ou mais processadores. Os programas devem ser desenvolvidos com o uso de múltiplas threads (multi-threadings) ou múltiplos-processos (multi-processing).

- Memória principal compartilhada
- Não há hierarquia
- Como a memória principal é compartilhada, precisam de mecanismos de coerência de cache para que os dados da memória principal não fiquem incoerentes
- A coerência de cache é provida pelo protocólo MESI

## AMP

- Processamento assimétrico
- Cada CPU tem sua própria memória
- Uma CPU irá controlar a distribuição das instruções
- Nem todas as CPU’s são tratadas de forma igualitária
- Um processador mestre executa as tarefas do sistema operacional
- Processadores podem ter características distintas

## Lei de Amdahl

- Potencial de speedup por utilizar paralelismo: $S = {\frac {T(1)} {T(N)}}$
- Na prática, para um número muito grande de processadores (N), considerando P como a parte do programa que pode ser paralelizável em uma fração de 0 a 1:
	- $S(N) = {\frac {1} {1-P}}$
	- Equivale ao potencial máximo
- Para um número menor de N
	- $S(N) = {\frac {1} {(1-P) + {\frac P N}}}$

## Taxonomia de Flynn

Maneira como as instruções e dados são organizados em um tipo de processamento

- **SISD** - Single Instruction Single Data
	- Segue o padrão de Von Neumann
	- Uma instrução completa de cada vez
	- Sem paralelismo!
- **SIMD** - Single Instruction Multiple Data
	- múltiplos elementos processadores supervisionados pela mesma unidade de controle. Todos as unidades processadoras recebem a mesma instrução distribuída pela unidade de controle, mas operam sobre diferentes conjuntos de dados. A memória compartilhada pode conter múltiplos módulos.
	- Mesma sequência de instruções sobre diferentes conjuntos de dados
	- Também chamados de processadores matriciais
	- Exemplo: GPU
	- **SWAR** - SIMD Within a Register
		- Utiliza instruções MMX
		- Possibilita processamento paralelo em máquinas com somente 1 processador
- **MISD** - Multiple Instruction Single Data
	- n unidades processadoras, cada uma recebendo instruções distintas, operando sobre o mesmo conjunto de dados. Não há implementação deste tipo de arquitetura.
	- Processamento vetorial
- **MIMD** - Multiple Instruction Multiple Data
	-  sistemas multiprocessadores. Diz-se que um sistema é fortemente acoplado se o grau de interações entre os processadores é muito alto. Caso contrário, é dito fracamente acoplado, sendo este o mais comum.
	- Multiplas insruções manipulando múltiplos dados

## Processamento Paralelo

- Não sequencial
- Execução de mais de uma instrução ao mesmo tempo
- Paralelismo a nível de instrução
	- Pipelining
- Paralelismo a nível de processador
	- Mais de uma CPU trabalhando simultaneamente

## Pipelining

> [!note] 🔥
> Pipelining é considerado paralelismo a nível de instrução

- Execução da instrução é dividida em partes
- Cada uma é manipulada por uma parte dedicada do hardware
- Todas podem acontecer em paralelo
- O tempo de execução de cada tarefa individualmente é o mesmo ou até um pouco maior
- O tempo de execução de um conjunto de tarefas será menor (melhora o throughput)
- Pipeline de 5 estágios
> [!note] 🔥
> **FD MES**

	- fetch
	- decode
	- search (data) (acesso a memoria)
	- exec
	- store
![[Untitled 524.png]]
- Missão fora de ordem
	- Algumas instruções que ingressam no pipeline podem apresentar dependência de outras
	- Neste caso, alguns processadores implementam o recurso de missão fora de ordem para analisar estas dependências
	- Quando uma instrução que não possui dependência ingressa no pipeline, ela pode ser colocada a frente de outras para evitar o bloqueio da CPU
	- Requer elementos de hardware adicionais e é uma análise complexa
	- Apesar deste processo, a conclusão das instruções ainda é colocada em ordem no final
- Conclusão fora de ordem
	- Estrutura que funciona em conjunto com a missão fora de ordem para armazenar as instruções intermediárias até que suas dependências sejam resolvidas
	- Garante o resultado final, mesmo que a execução tenha ocorrido fora de ordem
- hazard 
> [!note] 🔥
> **CD EF**

	- controle
		- Ocorre quando uma instrução depende do resultado da instrução anterior para controle do fluxo, por exemplo, desvio condicional
	- dados
		- Ocorre quando uma instrução depende do resultado da anterior
	- estrutural
		- Está ligado à limitação de recursos físicos do pipeline
	- Bypassing ou Forwarding
		- Capacidade do hardware enviar os dados diretamente para a instrução subsequente (dentro do pipeline) sem a necessidade de armazenamento em registradores visíveis ao programador.
- Ganho de pipeline
	- Sem pipeline: $T = M*t$
	- Com pipeline: $T = (M/K)*t$
	- O ganho teórico de um pipeline é igual ao número de estágios K, porém na prática este ganho nunca é atingido, pois existem fatores que irão influenciar como os hazards e tempo de enchimento do pipeline
	- Na teoria, sendo t1 o tempo de processamento de N instruções sem pipeline, o tempo de processamento das mesmas n instruções com pipeline seria t2 = t1/K

## Arquiteturas superescalares

- Possui mais de um pipeline na mesma CPU
- Tende a piorar o problema de hazards, que ocorrem em um pipeline simples
- Alguns estágios podem ser compartilhados entre as pipelines, por exemplo a unidade de busca de instrução
- Possíveis problemas desta arquitetura
	- Dependência de dados
	- Estrutura de desvios
	- Conflito entre recursos requeridos

## VLIW

- Alternativa ao pipeline para CISC
- Utiliza instruções muito longas que são decodificadas em várias instruções menores
- **Paralelismo a nível de compilador!**

## Arquitetura vetorial

- Paralelismo dos dados
- Aplicação típica em calculo de vetores
- Processadores vetoriais possuem duas partes
	- Unidade escalar (com pipeline)
	- Unidade vetorial
- **é uma unidade de processamento central** que pode **trabalhar em um vetor inteiro em uma instrução**. A instrução para o processador está na forma de um vetor completo em vez de seu elemento
- Os processadores vetoriais são usados **porque reduzem o consumo e interpretam a largura de banda devido ao fato de que menos instruções devem ser buscadas**
- Um processador de vetor também é conhecido como processador de matriz**.**

## Computadores paralelos

> [!note] 🔥
> Execução concorrente: Falso paralelismo. Apenas uma CPU com processos multiprogramados
Execução simultânea: Paralelismo real. Mais de uma CPU

Solução com mais CPUs
	- Multiprocessadores
		- Mais de uma CPU
		- Mesmo barramento
		- CPUs fortemente acopladas
		- Memória compartilhada
		- Multi-core
		- Pode haver uma pequena memória local (por CPU)
	- Multicomputadores
		- CPUs fracamente acopladas
		- Comunicação via barramento
		- Mais difíceis de programar
		- Mais fáceis de construir
		- primitivas de software *send* e *receive* costumam ser utilizadas na comunicação entre processos

## UMA x NUMA

- UMA
	- Todos os processadores possuem acesso a todas as áreas de memória
	- O tempo de acesso para todos as regiões é o mesmo
	- O barramento é compartilhado por todos os processadores
	- Usado em multiprocessamento simétrico
	- Quando o número de processadores for grande, o barramento pode ser um gargalo
- NUMA
	- O tempo de acesso a algumas regiões pode variar de acordo com o processador
	- Cada processador tem sua própria memória local
	- O acesso a regiões de memória vinculada a outros processadores terá que passar por estes
	- Permite uma melhor escalabilidade
	- Utilizada em servidores de alto desempenho

# Conceitos de Clusterização e Grid

## Cluster

- Conjunto de computadores conectados entre si, em geral na mesma rede
- Autônomos
- Utiliza programação paralela
- Trabalham juntas
- Podem fornecer:
	- Alta disponibilidade
		- Necessário a presença de nós “sobrando” para assumir em caso de falha\
		- Auto-monitoramento por rede separada
	- Balanceamento de carga
	- Alto desempenho
- Middleware
	- Camada intermediária entre o nível mais alto (usuários e aplicações) e uma camada subjacente (frameworks)
	- Visam ocultar a própria distribuição e heterogeneidade de SO’s e protocolos

## Grid

- Geograficamente distribuídas
- Heterogêneas
- Fracamente acopladas

# Message Passing Interface (MPI)

- Biblioteca padrão de comunicação distribuída para computação paralela
- **adequada para sistemas homogêneos**
- os tensores são frequentemente utilizados para representar grandes volumes de dados que precisam ser distribuídos e processados em diferentes nós de um cluster.
- permite a realização de cálculos distribuídos em larga escala, como simulações científicas e aprendizado profundo em GPUs distribuídas.
- A comunicação entre processos em MPI é realizada através da troca de **mensagens**.
- O MPI é ideal para ambientes de memória distribuída, como clusters, onde cada nó tem sua própria memória.
- MPI é projetado para ser altamente portátil, o que significa que um programa escrito com MPI pode ser executado em uma grande variedade de sistemas, desde clusters de computadores pessoais até supercomputadores massivamente paralelos.

## Operações

- **Broadcast (MPI_Bcast)**: Um processo envia dados para todos os outros processos.
- **Gather (MPI_Gather)**: Todos os processos enviam seus dados para um processo raiz que coleta os dados.
- **Scatter (MPI_Scatter)**: Um processo distribui dados para todos os outros processos.
- **Reduce (MPI_Reduce)**: Combina os dados de todos os processos em um valor único, como somas, máximos ou mínimos.

# Parallel Virtual Machine (PVM)

- Ambiente de software que permite que um **conjunto heterogêneo de computadores**** **funcione como um único sistema paralelo. 
- Ele foi muito popular nos anos 90, antes do surgimento de MPI, e ainda é usado em algumas áreas, embora seu uso tenha diminuído com o tempo em favor do MPI.
- O PVM pode funcionar em uma rede de computadores diferentes, como PCs, estações de trabalho e supercomputadores. 
- Ele cria uma "máquina virtual" paralela, permitindo que sistemas com diferentes arquiteturas e sistemas operacionais trabalhem juntos.
- PVM utiliza passagem de mensagens para comunicação entre processos.
- permite a adição e remoção de máquinas ao cluster de maneira dinâmica, enquanto a execução está em andamento.
- adota um modelo no qual existe um **processo mestre **que coordena os processos escravos, embora também suporte execuções mais flexíveis.
