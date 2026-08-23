---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2024-09-05T15:05:00
Owner:
  - Eduardo Quinalha
---
# Problemas do modelo relacional

- **Incompatibilidade de impedância**
	- Diferença entre o modelo relacional e as estruturas de dados na memória
	- Bancos relacionais organizam os dados em tabelas ou um conjunto de tuplas
	- Frameworks ORM amenizaram o problema de incompatibilidade de impedância
	- Frameworks ORM poupam trabalho na questão de mapeamento, ao ignorar totalmente o banco de dados, o desempenho pode ser comprometido
- **Escalabilidade**

# NoSQL

- Não há uma definição universal
- Não utilizam o modelo relacional
- Boa execução em clusters
- Open Source
- Não tem esquema definido
- Persistência poliglota
- geralmente têm uma arquitetura distribuída, escalável e tolerante a falhas, e não requerem esquema rígido.
- Ele é usado para lidar com **grandes volumes de dados não estruturados ou semiestruturados** e, portanto, é particularmente adequado para **aplicações de Big Data**

## Chave-Valor

- Tipo mais simples
- Permite a visualização do banco como uma grande **tabela hash**
- Cada chave é associada a um único valor, que pode ser uma string, número, objeto ou estruturas mais complexas como documentos
- Exemplos:
	- Redis
	- DynamoDB
![[Untitled 371.png]]
- Vantagens:
	- Velocidade
	- Simplicidade
	- Poucas operações (get(), set())
	- Alta escalabilidade
- Desvantagens
	- Não suporta consultas complexas
- Operações básicas
	- As operações primárias nesse modelo são a obtenção (GET), gravação (PUT) e exclusão (DELETE) de um valor associado a uma chave específica.
- **Atomicidade e consistência**
	- Operações são atômicas apenas a nível de uma única chave
	- Para uma única chave, é garantido que esta sempre estará em um estado consistente
	- Cada operação em uma chave é isolada das outras
	- No entanto, operações que envolvam múltiplas chaves não têm consistência garantida
	- Especialmente em ambientes distribuídos

## Documento

- Similar ao modelo chave valor
- Porém suporta estruturas mais complexas como documentos dentro de outros documentos
- Não tem um esquema rígido
- Exemplos
	- MongoDB
	- CouchDB
![[Untitled 372.png]]
- **Consistência e Atomicidade**
	- A consistência e atomicidade é garantida dentro de um único documento
	- Quando operações envolvem múltiplos documentos, a consistência pode variar.
		- Alguns bancos de dados de documentos oferecem suporte a transações que permitem consistência ACID entre documentos (por exemplo, MongoDB em operações que envolvem documentos em uma única coleção)
		- Em configurações distribuídas, a consistência entre diferentes documentos segue o modelo BASE

## Colunar

- Orientado por colunas
- Também conhecido como **BigTable**
- Dados indexados por uma trilha (linha, coluna e timestamp)
- As operações são atômicas, ou seja, todos os valores associados a uma linha são considerados na execução
![[Untitled 373.png]]
- Exemplos
	- Cassandra
	- Hbase
- **Consistência e Atomicidade**
	- Uma operação de escrita ou leitura em uma única célula (coluna de uma linha) ou em uma pequena família de colunas é geralmente atômica.
	- Muitos bancos de dados colunar, como Cassandra, seguem um modelo de consistência eventual, onde as atualizações feitas em uma coluna são propagadas para todos os nós ao longo do tempo.
	- Operações que envolvem múltiplas colunas ou múltiplas linhas distribuídas entre diferentes nós podem não ser atômicas, e a consistência pode ser garantida apenas de forma eventual.

## Grafos

- Registros pequenos com interconexões complexas
- Grafos dirigidos
- Componentes
	- **Nós **(vértices)
	- **Relacionamentos **(arestas)
	- **Propriedades **(atributos)
- Possuem desempenho superior para casos que seriam muito complexos em bancos relacionais, especialmente aqueles casos em que são necessários muitos joins
- Exemplos
	- Neo4J

![[Untitled 374.png]]

- **Consistência e Atomicidade**
	- Forte em operações que envolvem um único nó ou um subconjunto pequeno de nós e arestas
	- Operações em pequenos subgrafos tendem a ser consistentes e atômicas
	- operações que envolvem a atualização de muitos nós e arestas distribuídos, a consistência pode ser mais desafiadora
	- Em sistemas de grafos distribuídos, a consistência é eventual (BASE)
	- Alguns bancos de dados de grafos, como o Neo4j, oferecem suporte a transações **ACID**, o que significa que eles podem garantir consistência forte para operações transacionais que envolvem múltiplos nós e arestas. No entanto, essa garantia pode vir com um custo de desempenho ou escalabilidade.

# NewSQL

- Classe de bancos de dados relacionais que visam prover a escalabilidade e performance dos bancos NoSQL com a consistência transacional dos bancos SQL tradicionais
- São desenvolvidos para uso em larga escala, alta velocidade e processamento de dados analíticos
- Construídos em arquiteturas distribuídas
- Utilizam técnicas como
	- Fragmentação
	- Replicação
	- Processamento paralelo
	- Otimização e indexação de consultas
- Podem escalar horizontalmente
- Controle de concorrência não bloqueante, para que as leituras e escritas não causem conflitos entre si;
- Atendem as propriedades ACID
- Alta performance
- Flexibilidade para trabalhar com dados estruturados e semiestruturados
- Usos
	- OLTP
	- BI e analítica
	- DW e Data Lakes
- Exemplos
	- VoltDB
	- MemSQL
	- SQLFire
	- MariaDB

# Índices em NoSQL

- Os mecanismos de índices podem variar entre os tipos de bancos NoSQL
- **Chave-Valor**
	- Não há necessidade de uso de índices primários, visto que os dados são acessados pela chave (hash table)
	- Alguns bancos permitem a criação de índices secundários, por exemplo Redis
- **Documentos**
	- A chave primária do documento `_id` normalmente é automaticamente indexada
	- Índices secundários podem ser criados em qualquer campo ou conjunto de campos dentro do documento
	- Também é possível o uso de índices compostos (mais de um campo do documento) e campos de documentos aninhados
	- Também é possível o uso de índices geoespaciais
- **Grafos**
	- Índices são utilizados para localizar os nós com base em propriedades
	- A busca do nó é otimizada com o uso de índices, mas a navegação a partir deste ainda ocorre normalmente

# Bancos Distribuídos

## Modelos de Coerência

- Definem como e quando as atualizações feitas em um nó se tornam visíveis para outros nós e para os clientes que realizam leituras.
- **Modelos**
	- **Coerência Forte**
		- Após uma operação de escrita ser confirmada, qualquer leitura subsequente em qualquer nó do sistema deve retornar o valor mais recente escrito
		- Os dados são sempre consistentes e qualquer usuário em qualquer localidade verá as mesmas informações.
		- Pode levar a maiores latências, especialmente em sistemas distribuídos
	- **Coerência Eventual**
		- Se não houver novas atualizações em um dado, todas as réplicas do sistema distribuído eventualmente convergirão para o mesmo estado após um tempo
		- Imediatamente após uma escrita, diferentes nós podem retornar valores diferentes.
		- Permite alta disponibilidade e baixa latência, mas sacrifica a consistência imediata.
	- **Coerência Casual**
		- Se uma operação A causou uma operação B, qualquer nó que veja B também deve ver A.
		- Operações que são independentes (sem relação causal) podem ser vistas em ordens diferentes em diferentes nós.
		- A coerência casual é mais fraca que a coerência forte, mas oferece garantias que são mais intuitivas que a coerência eventual
	- **Coerência Monótona**
		- **Descrição**: Existem dois tipos principais de coerência monótona:
			- **Leitura Monótona**: Se um cliente lê um valor para uma determinada chave, leituras subsequentes do mesmo cliente não retornarão valores mais antigos.
			- **Escrita Monótona**: Se um cliente faz múltiplas atualizações em uma chave, essas atualizações são vistas na ordem em que foram realizadas.
		- **Exemplo**: Em um sistema de e-mails, se um cliente lê uma mensagem como "lida", ele nunca verá essa mensagem como "não lida" novamente.
		- **Impacto**: A coerência monótona é menos rígida que a coerência forte, mas ainda proporciona uma experiência mais consistente para o usuário final.
	- **Coerência de Sessão**
		- oferece garantias de consistência dentro do contexto de uma única sessão
		- Fora da sessão, essa garantia não é necessariamente mantida.
