---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2024-10-07T19:58:00
Owner:
  - Eduardo Quinalha
---
# Características

- Open Source
- Também definido como banco **Objeto-relacional**
- Possui extensões que podem ser incorporadas ao BD (plugins)
- Porta padrão **5432**
	- Existe o conceito de **extensões confiáveis **(verificadas pela comunidade)
- Segurança
	- **SCRAM** (Salted Challenge Response Authentication Mechaninsm)
	- Utiliza um Salt em conjunto com a senha do cliente para gerar um hash que será comparado na autenticação
- Uma instância do PostgreSQL é considerado um **cluster**, uma vez que vários bancos são armazenados em arquivos separados
- O armazenamento é feito em uma pasta específica: PGDATA
- **O PostgreSQL depende do sistema de arquivos subjacente para implementar a persistência**
- Catálogo
	- Conjunto de tabelas especiais que mantém as informações sobre os objetos do banco
	- Consultável e manipulável via SQL
- Um único banco dentro do PostgreSQL é composto por tabelas e diversos objetos
- O banco de dados pode ser organizado em **namespaces ou schemas**
	- **Schemas não podem ser aninhados**
	- Todo objeto pertence a um único esquema, e se este não for especificado, o esquema atribuído por padrão é o público
- **Usuários** são definidos no cluster e **não são vinculados a um banco específico**
	- Usuários podem ser normais ou superusuários
- PostgreSQL tem a capacidade de agir como um banco de dados NoSQL, armazenando e consultando dados JSON e JSONB

# **Gerenciador de Cluster: pg_ctl**

- é um CLI para gerenciamento do cluster
- Permite ações administrativas em cima do cluster:
	- `**start, stop, restart**`
		- O comando stop é crítico, por isso existem 3 formas possíveis de se parar um cluster
			- **smart** → aguarda até o último cliente se desconectar e então para o cluster em segurança
			- **fast** → Desconecta todos os clientes e para o cluster
			- **immediate** → aborta todos os processos. A integridade dos dados não será garantida
	- `**status**`
	- `**initdb**` → Criar um novo cluster de banco de dados
		- `initdb [opções] [—pgdata /-D] <diretório>`
	- `**reload**`
	- `**promote**`

# PSQL - Principais Comandos

- `\l` → Lista todas as bases de dados
- `\c` → Change DB
- `\dt` → Descreve todas as tabelas de um BD
- `\d` `\d+`→ Descreve uma tabela
- `\dn` → Lista todos os esquemas (namespace)
- `\du` → Lista todos os usuários
- `\df` → Lista todas as functions
- `\dv` → Lista todas as views
- `\copy` → Utilizado para transferir dados de uma tabela para um arquivo texto ou vice versa

# Processos

![[Untitled 815.png]]

- O processo principal do cluster é o **Postmaster**
	- Este processo é responsável por aguardar as conexões de entrada
	- **Dá origem os processos de backend**
- Cada processo **Client Backend** serve a uma única conexão
- Existem ainda outros tipos de processos backend:
	- **Checkpointer**
		- Checkpoints de tempo em que o banco garante que os dados foram persistidos
	- **Backgroud Writer**
		- Auxilia no envio dos dados da memória principal para o disco
	- **walwriter**
		- Gravação dos logs Write-Ahead (WAL) que funcionam como journaling
	- **stats collector**
		- Monitora quantidade de dados que o postgresql está manipulando, armazenando-os para análise
		- Estatísticas
	- **logical replication launcher**
		- Replicação lógica

# Arquivos de configuração

Algumas configurações podem/devem ser feitas via arquivos de configuração. Por padrão o PostgreSQL vem configurado para não aceitar configurações remotas, para alterar esta configuração deve-se alterar o arquivo de configuração

- Arquivos de configuração
	- `postgresql.conf`
	- `postgresql.auto.conf`
		- Gerado automaticamente a partir de configurações alteradas por comandos SQL
	- `pg_hba.conf`
	- `PG_VERSON`
		- Versão do PostgreSQL
	- `postmaster.pid`
		- PID do processo principal do cluster

O arquivo de configuração do servidor é o `postgresql.conf`

Algumas instruções de configuração importantes

- `listen_addresses`

Outro arquivo de configuração `pg_hba.conf` responsável pelas configurações de autenticação de usuários e permissões

```plain text
# TYPE  DATABASE    USER    CIDR-ADDRESS    METHOD
host    all         all     0.0.0.0/0       md5    
```

- Type: Local/host/hostssl → acesso local / via rede
- Database: 
	- Um único banco, 
	- lista separada por vírgula, 
	- group role iniciado com +, 
	- arquivo texto com lista iniciando com @ (valores separados por linha)
- User: Mesmas regras do database
- Method:
	- trust → Sem autenticação
	- Métodos: GSSAPI, SSPI, LDAP, RADIUS, PAM
	- SSL
	- scram-sha-256
	- md5
	- reject

# Organização do servidor

- /bin
- /data
	- **É a pasta PGDATA**
	- Armazena arquivos de configuração e tabelas comuns a todos os usuários
	- No linux fica em /var/lib/postgres/data
- /data/base
	- Subdiretório que armazenará outros subdiretórios, sendo um para cada base criada
	- Os arquivos utilizados para armazenar as tabelas de dados no PostgreSQL são chamados de **arquivo heap**
		- É um tipo de estrutura de dados
		- Lista de registros não ordenados de tamanho variável
- /doc
- /include
- /lib

# Segurança e Autenticação

- Existem diferentes métodos de autenticação
- Permite autenticação multi-fator
- Podem ser especificados métodos diferentes com base nos seguintes parâmetros:
	- Host do cliente
	- Banco de dados
	- Usuário
- Métodos
	- trust → aceita conexão sem autenticação
	- reject → rejeita por padrão
	- scram-sha-256
	- md5
	- password → Clear text
	- gss → GSSAPI, somente para conexões TCP/IP
	- sspi → Somente Windows
	- ident
	- peer
	- ldap
	- radius
	- cert → SSL
	- PAM
- Criptografia
	- O PostgreSQL permite a criptografia dos dados do banco
	- Este trabalho é feito pelo módulo **Pgcrypto**
	- `crypt()`
		- Usado tanto para criptografar quanto descriptografar a informação
- Criação de usuário
	- `create user [opções] nome_usuario`
	- Opções
		- Obs: Letra maiúscula **retira** o direito, letra minúscula **concede** o direito
		- `-D, -d `→ Create Database
		- `-R, -r` → Create Roles
		- `-S, -s `→ Super User
		- `-c` → Limite de conexões
		- `—replication`

# SQL no PostgreSQL

## DDL

- `CREATE DATABASE`
	- No PostgreSQL é possível utilizar outro banco já existente como modelo para se criar um novo
	- Para isso utiliza-se a opção `TEMPLATE` no comando `CREATE DATABASE`
```sql
CREATE DATABASE banco
	WITH
	OWNER = usuario
	ENCODING = 'utf8'
	LC_COLLATE = 'Portuguese_Brazil.1252'
	LC_CTYPE = 'Portuguese_Brazil.1252'
	TABLESPACE = pg_default
	CONNECTION LIMIT = -1;
```
- `CREATE SCHEMA`
```sql
CREATE SCHEMA "aulaPostgres"
	AUTHORIZATION thiagocavalcanti;
```
- `CREATE TABLE`
```sql
CREATE TABLE "aulaPostgres"."Alunos"
{
	"CPF" integer NOT NULL,
	"Nome" character varying(60) COLLATE pg_catalog."default" NOT NULL,
	"Endereço" character varying(60) COLLATE pg_catalog."default",
	"Telefone" integer,
	CONSTRAINT "Alunos_pkey" PRIMARY KEY ("CPF")
	}
	TABLESPACE pg_default;
	
ALTER TABLE "aulaPostgres"."Alunos"
	OWNER TO "usuario"

COMMENT ON TABLE "aulaPostgres"."Alunos"
	IS "Primeira tabela";
```
	- `CREATE [{ TEMPORARY | TEMP } | UNLOGGED ] TABLE [ IF NOT EXISTS] table_name (…)`
	- A tabela será de propriedade do usuário que a criou. Pode ser transferido para outro via comando `ALTER TABLE <tabela> OWNER TO <novo_proprietario>`
	- Existem no PostgreSQL 3 tipos de tabelas
		- **Temporárias**: Tabelas muito rápidas, visíveis apenas para o usuário que as criou
			- Tabelas temporárias são removidas ao final da sessão
		- **Não registradas (Unlogged):** Tabelas muito rápidas, usadas como suporte e comuns a todos os usuários
			- Não faz uso do write-ahead log (WAL)
		- **Registradas**: Tabelas comuns
	- Pode ser especificado o esquema onde deseja-se criar a tabela: `CREATE TABLE esquema.tabela`
		- Tabelas temporárias são criadas em um esquema especial, neste caso não é possível especificar o nome do esquema
	- Valores autoincrementados têm um tipo especial no PostgreSQL: `SERIAL`
	- O PostgreSQL permite a criação de tabelas sem chave primária
		- Neste caso haverão efeitos colaterais
			- Possibilidade de duplicação de registros
			- Baixo desempenho em buscas
			- Impossibilidade de uso de alguns recursos como
				- Replicação baseada em log
- `CREATE SEQUENCE`
	- Gerador de números sequenciais
	- Cria e inicia uma nova tabela especial de uma única linha
- `CREATE RULE`  e `CREATE TRIGGER`
	- O postgres tem duas formas de lidar com eventos:
		- RULE
			- Manipulam eventos simples
		- TRIGGER
			- Manipulam eventos complexos
	- Triggers podem ser definidos com as seguintes possibilidades de execução (teporalidade)
![[Untitled 816.png]]
	- Após disparada, a ação da tigger pode executar de 3 formas:
		- BEFORE
		- AFTER
		- INSTEAD OF
			- `INSTEAD OF`** ****Não pode ser utilizado para tabelas!**
	- Dentro da especificação das ações da trigger, os valores das colunas que estão sendo alteradas podem ser referenciadas por:
		- .NEW
		- .OLD
	- O acionamento pode se dar de duas formas
		- ROW LEVEL → Ação disparada 1 vez para cada linha
		- STATEMENT → Ação disparada para todo o conjunto de dados
- `CREATE TABLE AS SELECT`
	- Pode-se utilizar para criar uma tabela usando outra como modelo
```sql
CREATE TABLE backup_cliente AS SELECT * FROM cliente LIMIT 0;
```
- `TRUNCATE`
	- Limpa a tabela conservando sua estrutura
	- Inibe a ação de triggers para `DELETE` associado à tabela, durante sua execução
	- Opções adicionais do comando:
		- `RESTART IDENTITY` - Caso o ID seja um serial autoincrementado, deve-se utilizar esta opção a fim de resetar o valor da sequence para o inicial
		- `ONLY` → Faz o truncamento da tabela sem o `CASCADE` para outras em que ela seja chave estrangeira. Pode gerar inconsistências
			- Pode-se utilizar * para que as tabelas filhas sejam truncadas também: `TRUCATE PROF*`

## DML

- `LIMIT`
	- No PostgreSQL para limitar o número de linhas em uma query usa-se `LIMIT` 
- `OFFSET`
	- Usado em conjunto com o LIMIT
	- Deslocamento do valor inicial a ser exibido
- `FETCH`
	- Pode efetuar as mesmas operações de LIMIT e OFFSET em conjunto.
	- `FETCH { FIRST | NEXT } [count] { ROW | ROWS } ONLY`
```sql
SELECT * FROM processos
	OFFSET 5 ROWS
	FETCH FIRST 5 ROWS ONLY;
```
- `FOR`
	- `FOR UPDATE`
		- Efetua um lock dos registros selecionados e libera somente após o fim da transação
		- O lock do FOR UPDATE é do tipo exclusivo
	- `FOR SHARE`
		- Também efetua o Lock, porém outras operação FOR SHARE são permitidas
	- `NOWAIT`
		- Com esta opção, o select não aguarda a liberação de todos os registros para começar. Ele retornará um erro para cada registro bloqueado, mas continuará executando com os registros liberados.
- CTE (Common Table Expression)
	- Cláusula `WITH`
	- Colocada antes do `SELECT`
	- Permite uma pré carga de valores a serem utilizados na Query que se segue
	- O tempo de vida dos dados são os mesmos da Query
```sql
WITH regional_sales AS (
		SELECT region, SUM(amount) AS total_sales
		FROM orders
		GROUP BY region
	), top_region AS (
		SELECT region
		FROM regional_sales
		WHERE total_sales > (SELECT SUM(total_sales)/10 FROM regional_sales)
	)
SELECT region,
				product,
				SUM(quantity) AS product_units,
				SUM(amount) AS product_sales
	FROM orders
	WHERE region IN (SELECT region FROM top_regions)
	GROUP BY region, product;
```
- `SELECT INTO`
	- Os dados não são retornados ao cliente
	- Ao invés disso, serão inseridos em uma segunda tabela especificada no comando
```sql
SELECT lista_de_valores INTO [TEMPORARY|TEMP|UNLOGGED] [TABLE] nome_da_nova_tabela FROM tabela_de_origem WHERE condição;
```
- `**RETURNING**` 
	- é usado para retornar valores após a execução de uma operação de inserção, atualização ou exclusão.

## DCL

- Criação de grupos / roles
	- Definidos a nível de cluster
	- `CREATE ROLE`
		- Opção `INHERIT` permite que os privilégios das outras roles que o usuário possui sejam herdadas.
		- Sem esta opção, as roles anteriores deverão ser invocadas via comando `SET`
		- Role com privilégio de LOGIN é na prática um usuário
	- `ALTER ROLE`
	- `DROP ROLE`

# Tipos de dados

- Primitivos: Integer, Numeric, String, Boolean
	- Strings
		- TEXT: Tamanho variável
		- VARCHAR: Tamanho máximo definido
		- CHAR: Tamanho exato (completado com espaços em branco)
	- Numéricos
		- Inteiros: 2, 4 e 8 bytes
			- Integer
			- Int2
			- Int8
			- OID
			- Numeric(): Define os digitos de precisão e arredondamento. DECIMAL e NUMERIC são equivalentes
		- Ponto Flutuante: 4 e 8 bytes
			- FLOAT
			- FLOAT4
		- Decimais: Precisão fixa (ponto fixo)
- Structured: Date/Time, Array, Range / Multirange, UUID
	- Date → 4 bytes
	- Time
		- Precisão de microssegundos
		- Tamanho dependente da precisão
			- Mín 8 bytes
			- Máx 16 bytes
			- Sem precisão especificada = time(0) = 8 bytes
	- Timestamp
		- data e hora com 8 bytes (padrão)
		- Tamanho variável
		- de timestamp(0) 8 bytes a timestamp(6) 16 bytes
	- timestamptz
		- Armazena também informações de fuso horário
		- UTC
		- Mesmo tamanho de timestamp
	- Interval
		- 16 bytes
- Document: JSON/JSONB, XML, Key-value (Hstore)
- Geometry: Point, Line, Circle, Polygon
- Customizations: Composite, Custom Types

## BLOB

- Grandes objetos binários podem ser armazenados diretamente do BD
- Qualquer arquivo do filesystem
- Para trabalhar com arquivos, possibilitando inserção e recuperação destes a partir do filesystem, utilizam-se as funções:
	- `lo_import();`
	- `lo_export();`
- Exemplo

```sql
-- Criando a tabela e inserindo dados
CREATE TABLE fruit (name CHAR(30, image OID);
INSERT INTO fruit VALUES ('peach', lo_import('/home/test/images/peach.jpg'));

-- Recuperando os dados
SELECT lo_export(fruit.image, '/tmp/image.jpg') FROM fruit WHERE name = 'peach';

-- Excluindo
SELECT lo_unlink(fruit.image) FROM fruit;
```

## NoSQL

- O PostgreSQL pode lidar com formatos de dados NoSQL:
	- **hstore**
		- Pares chave-valor
	- **xml**
		- Diferente do armazenamento de XML em um campo texto puro, campos do tipo XML permitem verificação da formatação do XML
	- **JSON**
		- JSON → Texto puro
		- JSONB → Binário
		- Para acessar um valor do JSON dentro de uma query SQL utiliza-se o operador →>
```sql
SELECT * FROM Funcionario WHERE contato->>'email' LIKE '%@exemplo.com';
```

## Cast

- No PostgreSQL é possível fazer o CAST de tipos
- Sintaxe: 

```sql
-- <campo>::<tipo de destino>
-- Exemplo:
idade::int
```

# Funções

- Permitem acessar rotinas especializadas de SQL
- Tomam um ou mais argumentos
- `\df` → lista as funções disponíveis

# Índices

[https://halleyoliv.gitlab.io/pgdocptbr/indexes-types.html](https://halleyoliv.gitlab.io/pgdocptbr/indexes-types.html)

- PostgreSQL oferece suporte a vários tipos de índices
- Por padrão, o comando `CREATE INDEX` irá criar índices do tipo **B-TREE**
- Para criar índices de outros tipos, utiliza-se a cláusula **USING
**`CREATE INDEXnome ON tabela USING HASH (coluna);`
- o PostgreSQL consegue combinar vários índices (incluindo vários usos do mesmo índice), para lidar com casos que não podem ser resolvidos por varreduras de índice único. 

## **B-tree**

- Podem lidar com consultas de **igualdade** e de **intervalo em dados** que podem ser classificados por alguma ordenação.
- Por padrão, os índices árvore-B armazenam suas entradas em ordem crescente, com valores nulos por último
- Atualmente, apenas os índices árvore-B podem ser declarados como sendo `UNIQUE`.
	- Valores nulos não são considerados como iguais. 
	- Um índice multicoluna `UNIQUE` rejeita apenas os casos em que todas as colunas indexadas são iguais em várias linhas.
- O PostgreSQL cria automaticamente um índice de unicidade quando uma restrição `UNIQUE`, ou chave primária, é definida para a tabela. 
	- Não há necessidade de criar índices manualmente em colunas com unicidade; fazer isso apenas duplica o índice criado automaticamente.
- Adequado para agilizar a busca por comparação de valores utilizando os operadores:
	- `<   <=   =   >=   >`
	- `BETWEEN`
	- `IN`
	- `IS [NOT] NULL`

## **HASH**

- Armazenam um **código hash de 32 bits** derivado do valor da coluna indexada.
- Só podem lidar com comparações de** igualdade simples**

## **GiST (Generalized Search Tree)**

- Adotado principalmente para dados **geométricos** e de** localização geográfica**
- Os índices GiST não são um único tipo de índice, mas sim uma** infraestrutura onde muitas estratégias de indexação diferentes podem ser implementadas. **
- Operadores de comparação variam de acordo com a estratégia de indexação adotada
- Os índices GiST também são capazes de otimizar pesquisas de “vizinho-mais-próximo” (`nearest-neighbor`), como:
`SELECT * FROM places ORDER BY location <-> point '(101,456)' LIMIT 10;`
(encontra os dez lugares mais próximos de um determinado ponto de destino)

## **SP-GiST (Space-Partitioned Generalized Search Tree)**

- Assim como o GiST, é adotado principalmente para dados **geométricos** e de** localização geográfica**
- Os índices SP-GiST não são um único tipo de índice, mas sim uma** infraestrutura onde muitas estratégias de indexação diferentes podem ser implementadas. **
- Particionamento espacial
- Dados de geometria e localização

## **GIN (Generalized Inverted Index)**

- “índices invertidos”, apropriados para valores de dados que contêm vários valores componentes, como matrizes.
- Assim como os índices GiST e SP-GiST, GIN pode dar suporte a muitas estratégias de indexação definidas pelo usuário
- Os operadores específicos com os quais um índice GIN pode ser usado variam dependendo da estratégia de indexação.
- Facilita a busca por array (Matrizes), JSON
- Mais adequado para pesquisa de texto e documentos

## **BRIN (Block Range Index)**

- Armazenam resumos sobre os valores armazenados em intervalos de blocos físicos consecutivos de uma tabela. 
- Eficazes para busca em colunas relacionadas com o posicionamento físico na informação no arquivo de dados
- Exemplo busca por uma coluna que contenha a data de criação, pois esta data terá correlação com o ordenamento físico de inserção dos dados na tabela.

# Transações

## Níveis de isolamento:

- RU - Read Uncomitted
- RC - Read Comitted
- RR - Repeatable Read
- SS - Serializable
- Save Points
	- Faz marcações (labels) em pontos específicos da transação
	- Permite o rollback para a posição do label, ao invés de desfazer toda a transação
	- `ROLLBACK TO SAVEPOINT <label>`

## MVCC

- Multi Version Concurrency Control
- Toda transação que se inicia recebe um identificador, autoincrementado, o **TXID**

![[Untitled 817.png|xmin → TXID da transação que inseriu o dado
xmax → TXID da transação que alterou ou excluiu o valor. Quando é 0, significa que o valor ainda é válido]]

![[Untitled 818.png|Inicia a operação de update]]

![[Untitled 819.png|O valor atual é anotado com xmax = TXID da transação atual]]

![[Untitled 820.png|O valor atualizado é inserido com xmin = TXID atual e xmax = 0]]

![[Untitled 821.png|Tabela atualizada]]

![[Untitled 822.png|Inserção de uma nova informação]]

![[Untitled 823.png|Tabela atualizada]]

![[Untitled 824.png|Exclusão de um registro]]

![[Untitled 825.png|Tabela atualizada]]

- Na leitura das informações, somente valores com `xmax = 0` são retornados. Os demais, permanecem ocultos.
- Para remoção definitiva das tuplas anotadas com xmax, entra em ação o **VACUUM**
	- Este processo vai eliminar os registros “mortos” e rearranjar os dados
	- Similar o defrag
- Deadlocks (Time out)
- Persistência e Consistência
	- WAL

# Otimização de Desempenho

- Índices
- `EXPLAIN`
- `ANALYZE`
- Auto-explain

# Principais tabelas de metadados (do banco) - Catálogo do sistema

- Armazena os metadadados
- No PostgreSQL são tratadas como tabelas regulares
- Pode-se fazer alterações nestas, no entanto, há o risco de danificar o banco
- A principal a saber é a visão `pg_settings`
	- Armazena os parâmetros run-time do servidor
	- Não pode ter linhas inseridas ou apagadas
	- Pode ter valores atualizados, porém **só valerão para a sessão atual**
- **pg_stat_database**
	- Estatísticas sobre o banco de dados
	- Número de conexões
	- Tempo de execução
	- Espaço em disco
	- Número de conexões ativas
- **pg_class**
	- Informações sobre todos os objetos de banco
- **pg_attribute**
	- Informações sobre colunas
- **pg_index**
	- Detalhes sobre os índices existentes
- **pg_constraint**
	- Restrições de integridade
- **pg_namespace**
	- Esquemas

# Administração de servidores PostgreSQL

## Particionamento

- Existe no postgreSQL uma área de memória RAM alocada no servidor, compartilhada, onde os dados das tabelas são trabalhados, chamada **shared_buffers**
	- Os dados são retirados dos discos
	- Colocados no shared_buffers
	- Porcessados no shared_buffers
	- baixados para o disco
- Esta área ocupa cerca de 1/3 a 1/4 do total de RAM do servidor
- Quando uma tabela cresce excessivamente em relação ao shared_buffer, haverá perda de desempenho
	- Neste caso recomenda-se o particionamento dos dados
- O particionamento é transparente para o cliente
- Cada partição ficará armazenada em um arquivo físico diferente
- Tipos
	- **Range partitioning**
		- Dividida em intervalos
		- Os intervalos não podem se sobrepor
		- Normalmente são valores numéricos
	- **List partitioning**
		- Particionado por uma lista de valores, exemplo: Cidade, departamento, etc…
	- **Hash partitioning**
		- A partição se dá por valor de hash
- **work_mem**
	- Variável que indica o valor da memória de trabalho do PostgreSQL
	- Por padrão vem configurada para 4MB

# Resiliência e Recuperação de Desastres

- Write-ahead Logging (WAL)
	- Toda alteração é escrita primeiro no log, antes de sua efetivação física
	- Antecipa o commit
- **Replication**
	- **Tipos**
		- **Async** → A transação é confirmada assim que for concluída no master e sincronizada com o slave posteriormente 
		- **Sync** → A transação só é confirmada depois que for sincronizada em todos os nós
		- **Straming → **As alterações são transmitidas em tempo real para os nós secundários
		- **Logical → **A replicação é feita somente em partes específicas do banco
	- **Modelos**
		- Shared Disk Failover
			- Hardware compartilhado
		- File System
			- Replicação baseada no sistema de arquivos
		- Write-Ahead log Shipping
			- Para servidores warm e hot standby
			- O WAL é enviado para os nós secundários
		- Logical Replication
			- Funciona como mensageria
			- Os comandos de alteração são enviados simultaneamente a todos os servidores
		- Trigger-Based Primary-Standby Replication
		- SQL-Based Replication Middleware
			- As consultas são interceptadas e enviadas a todos os servidores
		- Asynchronous Multimaster Replication
		- Synchronous Multimaster Replication
- Point-in-time-recovery (PITR)
	- active standbys → Banco de dados em stand-by prontos para assumir
- Tablespaces

## Backup

- Formas
	- DUMP
		- Backup a frio
		- Gera um arquivo de comandos SQL
		- Pode ser feito por banco ou cluster (para cluster, somente superusuário) - `pg_dumpall`
		- `pg_dump`
		- Pode ser restaurado via `pg_restore` ou `psql`
		- O `pg_dump` Não guarda informações como roles e tablespaces. Para isso, deve-se utilizar o `pg_dumpall`
	- Backup em nível de arquivos (Físico)
	- Arquivamento contínuo (WALs)

# PL/PGSQL

- A linguagem procedural padrão é a PL/PGSQL, porém existem mais 3 opções:
	- PL/Tcl
	- PL/Pelrl
	- PL/Python
- Utilizado para funções, procedimentos e gatilhos
- Instalado por padrão desde a versão 9

# Storage Engine

- Diferente do MySQL, o PostgreSQL possui apenas uma engine de armazenamento físico
- O MySQL, por sua vez, possui o InnoDB destinado a bases com alta concorrência e que necessitam manter as propriedades ACID e o MyISAM para projetos menores, com mais eficiência na leitura, porém com pouca concorrência e sem muita necessidade de manter as propriedades ACID

# Mapa Mental

![[PostgreSQL.png]]
