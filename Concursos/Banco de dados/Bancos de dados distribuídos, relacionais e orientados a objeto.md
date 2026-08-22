---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2024-08-26T18:07:00
Owner:
  - Eduardo Quinalha
---
## Mapas Mentais

![[BD_Distribudos.png]]

# Aspectos

- **Rede** → Cliente-servidor
- **Paralelismo** → Banco de dados paralelos
	- Processamento em paralelo
	- Num mesmo computador
	- Execução de múltiplas tarefas ao mesmo tempo
	- Faz o uso de múltiplos cores ou múltiplos processadores
- **Distribuição** → Banco de dados distribuídos
	- Múltiplos computadores
	- Também oferece a possibilidade de paralelismo
	- Armazenamento em paralelo
- **Arquitetura centralizada**
	- Não interage com outros sistemas
	- Uma única estrutura computacional
- **Arquitetura Cliente - Servidor**
	- Backend
	- Frontend
	- **Servidores de transação**
		- Recebem requisições dos clientes, processam e devolvem os dados
		- Tipo mais utilizado
	- **Servidores de dados**
		- Usados em redes locais com conexões de alta velocidade
		- Fornecem os dados para serem processados no cliente
- **Arquitetura paralelas**
	- Sistemas multiprocessador
	- Compartilhamento
		- memória
		- disco
		- nada compartilhado (cada nó tem seu próprio conjunto)
	- Não tem overhead de mensagem por uma rede **(está tudo no mesmo hardware)**
	- Utiliza-se banco de dados paralelos
- **Arquitetura distribuída**
	- Interligados por rede (sites)
	- Remotos
![[Untitled 726.png]]
	- Existe um receptor de consulta global, que faz a compilação, otimização e gestão para então distribuir as subconsultas distribuídas onde vários nós podem executar partes da consulta original e devolver os dados que são recebidos no nó global, organizados e então entregues ao solicitante.
![[Untitled 727.png|Arquitetura em 3 camadas para a arquitetura cliente-servidor]]


# Banco de dados paralelos

## Tipos

![[Untitled 728.png]]

**Granularidade Grossa: **Poucos processadores porém com grande poder de processamento

**Granularidade Fina:** Muitos processadores, de baixo poder

- **Memória compartilhada**
	- Extrema eficiência na comunicação entre processadores
	- Não é adequado ao uso de mais de 32 ou 64 processadores
- **Disco compartilhado**
	- O acesso a memória não é mais um gargalo, visto que cada processador tem sua própria memória
	- Aumenta a tolerância a falhas
	- A desvantagem é o próprio grau de crescimento
- **Nada compartilhado**
	- As requisições não precisam mais passar pela rede
	- Suporte a um grande número de processadores
	- A comunicação entre os processadores passa a ser o fator limitante
	- Acesso ao disco não local
- **Hierárquico / Híbrido**
	- Combina as características das arquiteturas anteriores
	- Reduz a necessidade de complexidade entre processadores

## Características

- Muitas operações são realizadas em paralelo
- Melhoram as velocidades
- Medidas de desempenho
	- Throughput → Vazão, número de tarefas por unidade de tempo
	- Tempo de resposta → tempo para completar uma tarefa isolada
- Ganho de velocidade
	- Linear
	- Sublinear → Mais realista
- Ganho de escala
	- Benefício obtido pelo aumento do número de CPU

## Fatores contrários ao paralelismo

- Custo de partida
- Interferência - processos que acessam recursos compartilhados
- Distorções (skew) - Dividir uma tarefa em partes com igual tempo de processamento pode ser complicado. Algumas destas tarefas podem ter tamanhos menores que as outras, causando um desbalanceamento entre as CPU’s / Núcleos

# Banco de dados distribuídos

## **Sistema de computação distribuído**

- Vários elementos de processamento, **não necessariamente homogêneos**, interconectados por uma rede de computadores.
- Banco de dados distribuídos
	- Necessita de um SGBDD → Gerenciador de banco distribuído
	- **Transparente para o usuário**
	- Coleção de múltiplos bancos de dados logicamente inter-relacionados, distribuídos e conectados por uma rede de computadores.

## **Esquemas**

- 1 esquema conceitual global
- n esquemas conceituais locais

## **Regras associadas ou Objetivos secundários**

- **Autonomia local: **Cada nó tem autonomia e pode entregar resultado por si só
- **Não dependência de um nó central**
- **Operação contínua: **Independente de falha em um dos nós
- **Independência de localização**
- **Independência de fragmentação**
- **Independência de replicação**
- **Processamento de consultas distribuído**
- **Gerenciamento de transações distribuídas**
- **Independência de hardware**
- **Independência de Sistema Operacional**
- **Independência de Rede**
- **Independência de SGBD**

> **Dados****
****Infraestrutura**

## Condições para ser distribuído

- Interconexão por rede de computadores
- Inter-relação lógica dos bancos de dados
- Ausência de restrição de homogeneidade entre os nós

## Regras de fragmentação dos dados

- Fragmentação vertical e normalização são conceitos semelhantes
- São necessárias regras para assegurar que o BD não sofrerá nenhuma mudança semântica durante a fragmentação
	- Completeza
		- Os dados de uma relação global serão mapeados em fragmentos sem perdas
	- Reconstrução
		- Para uma relação decomposta em fragmentos, deverá existir um operador relacional capaz de reconstruir a relação original
	- Disjunção
		- Aplicado à fragmentação horizontal
		- Garante que um item de dado de um fragmento não estará presente em outro

## **Características**

- **Transparência de organização dos dados**
	- Local: O comando para executar uma tarefa independe do local dos dados onde o comando foi emitido
	- Nomes: Os nomes dos objetos são entendidos em qualquer nó, independente do local onde está armazenado
- **Transparência de replicação**
	- As cópias dos mesmos objetos podem estar armazenadas em vários sites
	- Melhora a disponibilidade, desempenho e confiabilidade
	- Torna o usuário desavisado a existência destas cópias
- **Transparência de fragmentação**
	- Horizontal: O conjuto das tuplas pode estar em locais diferentes
	- Vertical: As colunas de uma mesma relação pode estar em nós distintos
	- Mista
- **Transparência de projeto **
	- Liberdade de projeto
	- Como o BD é projetado
- **Transparência de execução**
	- Onde a transação é executada
	- Pode ser executado em mais de um nó ao mesmo tempo, mas isso é transparente ao usuário
- **Autonomia**
- **Confiabilidade e Disponibilidade**
	- São as vantagens atribuídas aos BDD

## **Gerenciamento do catálogo**

- Crítico para garantir um desempenho satisfatório
- Podemos ter catálogos:
	- Centralizados
	- Totalmente replicados
	- Particionados

## **Deadlock**

- O encadeamento de transações gera um grafo (ou gráfico, segundo alguns autores)
- Sempre que este gráfico se tornar cíclico, ocorre um deadlock
- Em BDD, existem além dos grafos locais, o grafo global, originado a partir da união de todos os grafos locais dos diversos bancos
- Se o grafo global se tornar cíclico, há a presença de um deadlock, mesmo que os grafos locais sejam acíclicos

![[Untitled 729.png]]

## **Vantagens**

- Facilidade e flexibilidade no desenvolvimento de aplicações
	- Consequência da transparência de distribuição
- Maior confiabilidade e disponibilidade
	- Isolamento de falha no site de origem
	- Replicação de dados e software
- Maior desempenho
	- Fragmentação
	- Paralelismo
- Expansão mais fácil
	- Basta adicionar novo nó

## **Taxonomia**

- Grau de homogeneidade
	- Homogêneo → Hardwares similares
	- Heterogêneo → Hardwares diferentes
- Grau de autonomia local
	- Com autonomia → Cada nó tem um grau de liberdade maior
	- Sem autonomia → Maior dependência de um nó central
- Grau de distribuição
	- Centralizado
	- Distribuído
- Exemplos:
	- Bancos de dados centralizados tradicionais
		- alta autonomia
		- 0 distribuição
		- 0 heterogeneidade
	- Bancos de dados Distribuídos puros
		- 0 autonomia
		- alta distribuição
		- 0 heterogeneidade
	- **Bancos de dados Federados**
		- Média autonomia
		- Alta distribuição
		- Alta heterogeneidade
	- Sistema multi-bancos ou peer to peer
		- Alta autonomia
		- Alta distribuição
		- Alta heterogeneidade

## Processamento e otimização de consultas

- Mapeamento da consulta: Validação frente ao esquema global
- Localização: Fragmentação da consulta de acordo com os bancos que compõem o cluster
- Otimização global da consulta
- Otimização local da consulta

> Site central
Bancos locais

### Operações de otimização

- Semi-junção
	- Em uma operação de junção normal, a tabela que está sendo “juntada” será pesquisada mesmo para os valores que não tenham correspondência, gerando tráfego desnecessário na rede.
	- Em uma operação de semi-junção, a primeira tabela é varrida a fim de montar apenas os atributos de junção que serão necessários.
	- De posse deste conjunto, a pesquisa na tabela “juntada” é limitada apenas a estes valores, que serão transferidos uma única vez

## Teorema CAP ou Teorema de Brewer

Os seguintes comportamentos podem ser associados a SGBDD

- **Consistência** (**C**onsistent): É garantido o retorno do dado mais atualizado logo após a escrita, independentemente do nó consultado

![[Untitled 730.png]]

- **Disponibilidade** (**A**valiable): O banco sempre retornará um valor, desde que ao menos um nó esteja online
- **Tolerância a partição/falhas **(**P**artition tolerant): O sistema como um todo continua funcionando, mesmo que um dos nós participantes esteja offline.

![[Untitled 731.png]]

O teorema diz que qualquer sistema de banco de dados distribuído pode apenas agregar duas destas três características, simultaneamente. Ou seja, é impossível a existência de um sistema de banco de dados distribuídos que agregue as três características simultaneamente.

![[Untitled 732.png]]

**Consistência Eventual:** A escrita de dados é priorizada, sendo que a sincronização dos dados é feita em um monento posterior, sendo assim, durante um intervalo de tempo, os dados podem estar inconsistentes. Em geral, esta é uma característica dos banco NoSQL

**Tolerância a Partição:** Tende a ser uma característica implícita do sistema de banco de dados distribuído.

## ACID x BASE

- ACID
	- Abordagem Pessimista
	- Utiliza controles de simultaneidade com aplicação de bloqueios de registro
	- Força a consistência no final de cada operação
	- Atomicidade
	- Consistência
	- Isolamento
	- Durabilidade
- BASE
	- Otimista
	- Aceita que a consistência não seja instantânea
	- Tolera falhas parciais no sistema
	- Persistência não ocorre em tempo real
	- Favorece a disponibilidade em detrimento da consistência
	- Basically Available
		- Sempre retornará uma resposta ao cliente
	- Soft State
		- Pode estar em um estado inconsistente enquanto os dados são lidos
	- Eventualy Consistent
		- Leituras feitas por usuários diferentes, pode retornar valores diferentes

## Topologia Master-Slave

A topologia master-slave é uma configuração comum em sistemas distribuídos, em que um nó master (ou primário) é responsável por gerenciar e controlar as operações de gravação de dados, enquanto um ou mais nós slaves (ou secundários) podem ser utilizados para leitura de dados.

Na maioria das implementações, apenas o nó master é autorizado a realizar gravações ou alterações no estado do sistema, enquanto os nós slaves apenas podem ler o estado atual do sistema. Por esse motivo, dados nunca são criados diretamente nos nós slaves.

No entanto, em alguns sistemas, é possível que os nós slaves possam ser usados para gravação em situações específicas. Nesses casos, há um mecanismo de sincronização entre o nó master e os nós slaves, para garantir que as operações de gravação sejam propagadas de forma consistente em todo o sistema.

Em resumo, em geral, a topologia master-slave é usada para leitura de dados, e o nó master é o responsável por todas as operações de gravação. Mas existem casos em que os nós slaves podem ser usados para gravação, embora isso seja menos comum.

## CDC - Change Data Capture

CDC é uma técnica utilizada para capturar alterações feitas em bancos de dados, como inserções, atualizações e exclusões, com o objetivo de replicá-las em outro sistema para análises e processamento de dados atualizados. Essa técnica é crucial em ambientes de dados distribuídos e sistemas de integração de dados.

O CDC é eminentemente utilizado para garantir que as alterações nos dados de origem sejam replicadas de forma consistente e em tempo real ou quase real, para outros sistemas de armazenamento de dados ou plataformas de análise, sem a necessidade de recarregar todo o conjunto de dados. Portanto, o foco do CDC não é o controle da computação distribuída, mas a captura e transferência eficientes de alterações de dados específicas.

# Banco de dados orientado a objeto

## Conceitos Básicos

- Conhecidos como BDO ou BDOO
- Concebidos para atender uma demanda de aplicações mais complexas
	- Sistemas de aplicações geográficas
	- CAD / CASE
- Identidade de objeto
	- OID
	- Independente dos valores de atributo da instância do objeto
	- Gerado pelo sistema
	- Não é visto pelo usuário
	- Usado internamente
- Construtores de Tipo
	- Estruturas de objeto complexas podem ser construídas ao aplicar de maneira aninhada um conjunto de construtores básicos como tuple, set, list, array e bag

## Armazenamento de Objetos

- O armazenamento em objeto é uma forma de armazenamento de dados que organiza informações em "objetos", que incluem dados em si, bem como metadados associados.
- Um objeto consiste em dados binários ou texto, juntamente com metadados que descrevem esses dados. Os metadados podem incluir informações como data de criação, tipo de arquivo, permissões de acesso, entre outros.
- Os sistemas de armazenamento em objeto são frequentemente usados em armazenamento de grande escala, como em data lakes, devido à sua escalabilidade e eficiência na gestão de grandes volumes de dados não estruturados e semiestruturados.