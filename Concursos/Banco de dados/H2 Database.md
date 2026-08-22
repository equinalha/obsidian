---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2024-09-05T15:05:00
Owner:
  - Eduardo Quinalha
---
# Mapa Mental

![[H2.png]]

# Características

## Básicas

- Escrito em Java
- Suporta SQL e JDBC API
- Modo embutido ou Servidor
- Suporte a clusterização
- Funciona com o Driver ODBC do PostgreSQL
- Possui MVCC

## Avançadas

- Formas de operação
	- Em disco
	- Em memória
	- Read Only
	- Tabelas temporárias
- Suporte a transações
	- RU, RC, RR, SS e 2PC
- Possui bloqueio a nível de registro
- Suporte a criptografia
	- AES
	- SHA-256
	- SSL
- Compatibilidade de linguagem com:
	- MS SQL
	- Oracle
	- PostgreSQL
	- MySQL
- Possui uma solução built-in para prevenção de SQL Injection
- Autenticação com SHA-256 e Salt
- Multi-thread safe

## Modos

- Embedded
	- A base de dados funciona na mesma JVM
	- **Conexão se dá por JDBC**
	- Funciona com base em memória ou disco
	- Número de conexões simultâneas ilimitado
- Server
	- Servidor separado da JVM para banco de dados
	- Pode ser em outra máquina
	- **Conexões por JDBC ou ODBC**
	- Suporta múltiplas conexões
- Mixed
	- Combinação de Embedded com Server mode
	- Funciona embutido dentro de uma aplicação mas também aceita conexões externas

## URL´s de conexão

| Tipo de banco | URL e Exemplos |
| --- | --- |
| [Embedded (local) connection](https://www.h2database.com/html/features.html#embedded_databases) | jdbc:h2:[file:][<path>]<databaseName>
<br>jdbc:h2:~/test
<br>jdbc:h2:file:/data/sample
<br>jdbc:h2:file:C:/data/sample (Windows only) |
| In-memory | jdbc:h2:mem:<databaseName>
<br>jdbc:h2:mem:test_mem |
| Server mode (remote connections)
<br>using TCP/IP | jdbc:h2:tcp://<server>[:<port>]/[<path>]<databaseName>
<br>jdbc:h2:tcp://localhost/~/test
<br>jdbc:h2:tcp://dbserv:8084/~/sample
<br>jdbc:h2:tcp://localhost/mem:test |
| Server mode (remote connections)
<br>using TLS | jdbc:h2:ssl://<server>[:<port>]/[<path>]<databaseName>
<br>jdbc:h2:ssl://localhost:8085/~/sample; |
| [Only open if it already exists](https://www.h2database.com/html/features.html#database_only_if_exists) | jdbc:h2:<url>;IFEXISTS=TRUE
<br>jdbc:h2:file:~/sample;IFEXISTS=TRUE |

## Criptografia

- São suportados 3 algoritmos para criptografia **da base de dados**
	- AES-128
	- XTEA
	- FOG - Tipo de pseudo criptografia. Útil apenas para esconder os dados de um editor de texto
- Conectando-se a uma base criptografada:

```java
String url = "jdbc:h2:~/test;CIPHER=AES";
String user = "sa";
String pwds = "filepwd userpwd";
conn = DriverManager.
    getConnection(url, user, pwds);
```

- Uma base de dados existente pode ser criptografada ou descriptografada
	- Isso pode ser feito a partir do console h2 ou via linha de comando
```java
java -cp h2*.jar org.h2.tools.ChangeFileEncryption -dir ~ -db test -cipher AES -encrypt filepwd
```

## Criação de Base de Dados

- Por padrão, no modo embedded, quando um nome de banco é especificado na URL e ele não existe, o H2 irá criar o banco com o nome especificado.
- Para evitar este comportamento, é necessário acrescentar o parâmetro `IFEXISTS=TURE`
- Deste modo, se a base não existir, uma exceção será jogada

## Backup

- A forma recomendada de backup do H2 é via backup lógico.
- Pode ser feito via linha de comando ou de forma online via SQL

```bash
# Efetuando o backup -- Comando Script
java org.h2.tools.Script -url jdbc:h2:~/test -user sa -script test.zip -options compression zip

# Recuperando o backup -- Comando RunScript
java org.h2.tools.RunScript -url jdbc:h2:~/test -user sa -script test.zip -options compression zip
```

```sql
-- Backup no SQL
BACKUP TO 'backup.zip';
```

## Shell

- O H2 possui um CLI que pode ser utilizado via shell

```bash
java -cp h2*.jar org.h2.tools.Shell
```

- O Shell pode ser utilizado para rodar comandos SQL

## Fulltext Search

- O H2 dispõe de duas implementações de funções de busca por texto:
	- Apache Lucene
	- Nativo
- Para utilizar o suporte nativo, deve-se criar índice especificando as colunas

```sql
CALL FT_CREATE_INDEX('PUBLIC', 'TEST', NULL);

-- PUBLIC = Schema
-- TEST = BD
-- NULL -> todas as colunas da tabela
```

- Para realizar a busca, utiliza-se a sintaxe

```sql
SELECT * FROM FT_SEARCH('Hello', 0, 0);
```

- Usando o Apache Lucene

```sql
-- Criando o índice
CALL FTL_CREATE_INDEX('PUBLIC', 'TEST', NULL);

-- Realizando a busca
SELECT * FROM FTL_SEARCH('Hello', 0, 0);
```

## Tipos de dados

- Caracteres
	- Character
	- Character Varying
	- **Character Large Object**
		- Sequencias de texto muito longas
		- Não são carregadas de uma só vez na memória, ao invés disso, são tratadas como um streaming
		- Usadas para XML, HTML, documentos
	- Varchar_ignorecase
- Binários
	- binary
	- binary varying
	- binary large object
	- Boolean
- Numéricos
	- tinyint
	- smallint
	- integer
	- bigint
	- numeric
	- real
	- double
	- **decfloat**
		- Decimais de ponto flutuante
		- **não recomendados para moedas**
- date/time
	- date
	- time
	- time with time zone
	- timestamp
	- timestamp with zone
	- interval
- diversos
	- **java_object**
		- Armazenamento de objetos java serializados
	- enum
	- geometry
	- json
	- uuid
	- array
	- row

## Segurança

> [!note] 🔥
> Não é adequado para uso em produção exposto à internet

## SQL Injection

- O H2 permite forçar o uso de prepared statements

```sql
SET ALLOW_LITERALS NONE;
```
