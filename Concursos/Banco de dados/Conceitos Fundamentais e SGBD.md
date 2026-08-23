---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2024-08-26T18:07:00
Owner:
  - Eduardo Quinalha
---
# Resumo

## Conceitos Básicos

- Banco de dados
	- Dados armazenados
	- Metadados / Dicionário de Dados / Catálogo de Dados
- SGBD
	- Controle de transações
		- ACID
	- Segurança de Acesso
	- Recuperação pós falha
	- Controle de concorrência
	- Ajuste / Tunning
- SBD
	- SGBD + BD

# Propriedades

- Persistentes
- Compartilhados
- Inter-relacionados

# Personagens

- Administrador de Dados (projetista de dados)
	- Padronizar os nomes dos objetos
	- Gerenciar e auxiliar na definição das regras de integridade
	- Controlar a existência de informações redundantes
	- Trabalhar de forma corporativa nos modelos de dados da organização
- DBA
	- Definir o esquema conceitual (lógico)
	- Definir o esquema interno
	- Contactar com os usuários
	- Definir as restrições de segurança e integridade
	- Monitorar o desempenho e requisitos de mudança
	- Definir políticas de carga/descarga (dump)

# Evolução histórica

- Hierárquico
	- árvore
	- 1:n
- Rede
	- Registros
	- n:n
- Relacional
	- Lógica de primeira ordem
	- Teoria dos conjuntos
	- SQL
- Objeto Relacional
- NoSQL

# Modelos de Dados

- Instância / Extensão / Fotografia
- Esquema / Projeto de BD / Intenção
- Modelos:
	- Conceitual
	- Lógico
	- Físico

# Arquitetura em três camadas

> [!note] 🔥
> **Atenção para pegadinha das bancas!**
> | **CONCEITUAL** | **EXTERNO** |
> | --- | --- |
> | **LÓGICO** | **CONCEITUAL** |
> | **FÍSICO** | **INTERNO** |

- Níveis
	- Interno
		- Mais próximo do meio de armazenamento físico
		- Como os dados são armazenados
	- Conceitual
		- Lógico
		- De comunidade
	- Visão
		- Nível lógico do usuário
		- Mais próximo do usuário
- Independência dos dados
	- Física
	- Lógica

# Fundamentos

## Definição

Trata-se de uma coleção de dados relacionados. Possuem 3 propriedades implícitas:

1. Representa algum aspecto do mundo real
2. Coleção de dados logicamente coerentes
3. Atende a uma necessidade específica

> [!note] 🔥
> Dados ≠ Informação

DBA = Suporte. Usuário Técnico

AD = Projetista. Mais ligado ao negócio

> [!note] 🔥
> Banco de dados orientado a objeto → Armazena também operações sobre os objetos (métodos). Visa aproximar o conceito de OO ao banco de dados

## ACID *** Cai muito em concurso

Provido pelo gerenciador de transações

- **Atomicidade:**** **Tudo ou nada! Ou todas as operações da transação são executadas (commit), ou nenhuma (rollback);
	- Responsável: Subsistema de recuperação
- **Consistência:**** **A transação deve ir de um estado consistente para outro, também consistente;
	- Responsável: Programador ou Módulo de Restrições de Integridade
- **Isolamento:**** **Transações concorrentes devem ser isoladas umas das outras. Uma não tem conhecimento da outra;
	- Responsável: Subsistema de controle de concorrência
- **Durabilidade:**** **Depois da transição ter sido comitada, a base entra em um novo estado permanente.
	- Responsável: Subsistema de recuperação

## SGBD

Conjunto de programas que permite aos usuários criar e manter um BD.

> [!note] 🔥
> O BD em si são arquivos. O SGBD gerenciam estes arquivos e aspectos relacionados a eles.
Também gerencia a proteção dos dados, backups, recuperação, etc…

> [!note] 🔥
> Metadados: Especificam os tipos de dados armazenados, estruturas, restrições e relações entre estes dados

> [!note] 🔥
> SBD = SGBD + BD

## Atores

### Administrador de Dados

- Visão estratégica
- Olha para os dados de forma corporativa
- Validador dos dados
- Fundamental para consistência e evitar redundância
- Decidir quais informações serão mantidas no BD
- Projeto lógico e conceitual
- Gerencia as regras de negócio

### DBA

- Opera o banco
- Instala o banco
- Cuida da infra, atualizações, permissionamento, etc.
- Suporte técnico
- Otimizações
- Recurso principal: Banco de dados
- Recurso secundário: SGBD
- Definir o esquema conceitual
- Definir o esquema interno
- Definir normas de carga e descarga (dump)

### Usuários Finais

- Necessitam de acesso ao BD para CRUD e relatórios
	- Casuais: Ocasionalmente utilizam
	- Iniciantes ou paramétricos: Tem função de consulta e atualização regular dos dados
	- Sofisticados: Implementam suas próprias aplicações
	- Isolados: Possuem um BD próprio

## Linguagem procedural

Utiliza estruturas de controle de fluxo e laços. Exemplo PL/SQL

## Linguagem não procedural

Apenas CRUD, DDL, DTL, etc…. (SQL)

## Histórico

### 1ª Geração

- Hierárquico
	- Apenas relacionamento 1:n (não tem n:n)
	- árvores onde cada registro é considerado uma coleção de campos ou atributos
- Rede
	- Lista duplamente encadeada
	- Permite relacionamento n:n
- Arquivos invertidos

### 2ª Geração

- Relacional
	- Baseia-se em entidade - relacionamento

## XML

Utilizado para intercâmbio de dados na web. É capaz de transmitir dados e metadados no mesmo arquivo

## Bancos de dados Dedutivos

Armazenam fatos (equivalente aos dados) e regras (equivalente às tabelas) e que podem ser utilizados para deduzir outros fatos que não estejam diretamente armazenados

# Banco de dados NoSQL

Ao contrário dos bancos relacionais, não é ACID.

Ao invés do ACID, respeita as propriedades BASE

**BASE**:

- **Basically Available**
	- Sempre disponível
- **Soft State**
	- Estado flexível
- **Eventualy Consistent**

Grande quantidade de dados

Características específicas:

- Colunar
- Chave valor
- documentos
- grafos

Obter uma resposta rápida, é mais importante do que receber uma resposta 100% correta

### Exemplos de NoSQL

- MongoDB → Documentos
- Neo4J → Grafos, SGBD em memória
- Redis → Chave / Valor, em memória

![[Untitled 741.png]]

# Modelo De Dados

## Modelo Conceitual

- Modelo Entidade - Relacionamento
- Não sabe-se ainda qual será o modelo de banco de dados
- Define atributos e relações
- Nível de abstração alto

## Modelo Lógico

- Escolhe-se o modelo do banco de dados (relacional, NoSQL)
- Mas ainda não se define qual o banco de dados específico (Oracle, MySQL)
- Desenham-se as tabelas

## Modelo Físico

- Escolha do SGBD
- Linguagem SQL
- Implementação
- Construção dos relacionamentos
- Nível de abstração baixo

# Esquema vs Instância

**Esquema →** É o projeto do BD. Descreve os dados e suas relações

**Instância →** Coleção de dados armazenados no BD em um determinado instante

# Arquitetura em 3 camadas e independência de dados

- Também é conhecido como padrão **ANSI-SPARC**
- Provê a independência de dados
- O processo de transformação dos dados entre os três níveis é chamado de **MAPEAMENTO**

<!-- Column 1 -->
![[Untitled 742.png]]

<!-- Column 2 -->
![[Untitled 743.png]]

## Independência de Dados Lógica / Conceitual

Uma alteração no modelo conceitual, não gera uma necessidade de alteração no nível externo

## Independência de Dados Física

Uma alteração no modelo físico, não gera uma necessidade de alteração no modelo conceitual, por consequência, não gera também uma necessidade e alteração no modelo externo

# Subsistemas de um SGBD

- Backup e Recuperação de dados
	- Visa garantir que um dado persistido possa ser recuperado depois
	- Não tem nenhuma relação com a construção de índices para acelerar a busca
- Otimizador de consultas
	- se preocupa com o rearranjo e a possível reordenação de operações 
	-  eliminação de redundâncias 
	- uso de algoritmos e índices corretos durante a execução de uma consulta SQL
