---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2024-09-05T15:05:00
Owner:
  - Eduardo Quinalha
---
# Arquitetura

![[Untitled 165.png]]

- **Conexão / Utility Layer**
	- Primeira etapa na arquitetura do MySQL. 
	- Ela é responsável por estabelecer a conexão com o cliente, autenticar os usuários, definir as configurações da sessão e lidar com a compressão do protocolo de rede, se necessário.
- **Query (SQL) Layer**
	- A camada de consulta é responsável por várias funções, como análise de consultas, otimização, armazenamento em cache e todo o trabalho relacionado à consulta em SQL, como junções e ordenações.
	- Esta camada também lida com controles de transação e armazenamento de procedimentos.
- **Storage Layer**
	- A camada de armazenamento é onde os dados são realmente armazenados e recuperados. 
	- O MySQL suporta vários mecanismos de armazenamento, cada um com suas próprias características. 
	- Os mecanismos de armazenamento mais comuns incluem: 
		- **InnoDB** (que suporta transações ACID e chaves estrangeiras) e o 
		- **MyISAM** (que é mais leve e rápido, mas não suporta transações).

# Configuração

- A configuração do MySQL é gerenciada através do arquivo my.cnf no Linux e Mac, ou my.ini no Windows.
- Este arquivo contém várias seções para diferentes aspectos da configuração, como o servidor MySQL (mysqld), o cliente MySQL (mysql), e assim por diante.
- Principais diretivas
	- **innodb_buffer_pool_size: **
		- Esta diretiva controla o tamanho do buffer de entrada/saída do InnoDB, que é o mecanismo de armazenamento padrão do MySQL.
		- determina o tamanho do buffer pool, que é o local onde o InnoDB armazena os dados e índices em cache. Uma regra geral comum é definir isto para cerca de 70-80% da memória RAM do seu servidor em um servidor dedicado ao MySQL.
	- **innodb_log_file_size:**
		- define o tamanho do log de transações do InnoDB.
		- Se você tem uma carga de trabalho com muitas gravações, pode ser benéfico aumentar este valor. 
		- No entanto, um valor maior também significa que a recuperação após uma falha pode levar mais tempo.
	- **max_connections: **
		- Esta diretiva controla o número máximo de conexões simultâneas que o servidor MySQL aceitará.
		- Se você tem muitos clientes se conectando ao seu servidor ao mesmo tempo, pode ser necessário aumentar este valor.
	- **query_cache_size: **
		- Esta diretiva controla o tamanho do cache de consultas.
		- O cache de consultas pode melhorar o desempenho armazenando o resultado de consultas SELECT na memória, 
		- é mais eficaz em um ambiente onde há um alto número de consultas idênticas.

# Mecanismos de Armazenamento

## InnoDB

- Mecanismo de armazenamento padrão para o MySQL a partir da versão 5.5.
- É um mecanismo de armazenamento transacional, o que significa que suporta características ACID
- InnoDB também suporta chaves estrangeiras e possui recursos avançados como o multiversion concurrency control (MVCC)
- Além disso, ele usa um buffer pool para caching, o que pode melhorar significativamente a performance das leituras.

## MyISAM

- Mecanismo de armazenamento mais antigo, que era o padrão antes do InnoDB
- Não suporta transações ou chaves estrangeiras, o que limita sua aplicabilidade em muitos cenários modernos.
- mais simples e usa menos recursos do sistema, o que pode torná-lo mais rápido em algumas situações, especialmente para operações de leitura intensiva.

## Memory

- armazena todos os seus dados na memória, o que significa que é extremamente rápido
- todos os dados são perdidos quando o sistema é reiniciado. 
- Ele é útil para dados temporários que não precisam ser persistidos.

## Outros Mecanismos

- CSV
- ARCHIVE
	- usado para armazenar grandes quantidades de dados que não necessitam de indexação
- FEDERATED
	- permite acessar dados de um banco de dados MySQL em outro servidor MySQL
- BLACKHOLE
	- aceita dados, mas não os armazena. 
	- Ele pode ser útil para fins de teste.

# Tipos de dados

- Numéricos

![[Untitled 166.png]]

- Data e Hora
	- Date
	- Time
	- DateTime
	- Timestamp
	- Year
- Texto
	- Char - Comprimento fixo
	- Varchar - Comprimento variável
	- Text - grande comprimento
	- BLOB - Binários
	- ENUM - Lista predefinida
	- SET - Similar ao ENUM, porém pode conter múltiplos valores

# Autenticação

## Plugins de autenticação

- **mysql_native_password:**
	- método tradicional de autenticação no MySQL
	- usa um hash de senha baseado em SHA-1
	- a partir do MySQL 8.0, o caching_sha2_password é o método padrão, mas mysql_native_password ainda é suportado.
- **caching_sha2_password:**
	- plugin de autenticação padrão a partir do MySQL 8.0.
	- usa um hash de senha baseado em SHA-256
	- armazena informações de autenticação em cache na memória, o que permite autenticação mais rápida em conexões subsequentes
- **sha256_password:**
	- igual ao caching_sha2_passord, porém não suporta o armazenamento em cache de informações de autenticação
	- mais seguro do que mysql_native_password, mas 
	- menos eficiente do que caching_sha2_password.

## Definição da autenticação utilizada pelo usuário

```sql
CREATE USER 'bob'@'localhost' IDENTIFIED WITH caching_sha2_password BY 'password';
```

# Índices

- B-Tree
	- Tipo mais comum no MySQL
	- Padrão
- Full Text
	- Utilizados em buscas FullText
	- Construídos com base no conjunto de palavras que aparecem na coluna indexada
- Hash
	- Consultas de igualdade

# Backup e Recuperação

## Backup

- **mysqldump**
	- gera um arquivo SQL que contém comandos para recriar o banco de dados a partir do zero
	- Exemplo:
		- `mysqldump -u [username] -p[password] [database_name] > backup.sql`
	- pode exportar múltiplos bancos de dados de uma só vez utilizando a opção --all-databases.
- **mysqlpump**
	- ferramenta de backup que foi introduzida no MySQL 5.7.8.
	- semelhante ao mysqldump, mas tem algumas melhorias, como:
		- capacidade de fazer backup de vários bancos de dados simultaneamente 
		- capacidade de fazer backup em paralelo, o que pode ser significativamente mais rápido.
	- Uso:
		- `mysqldump -u [username] -p[password] —databases [db1] [db2] > backup.sql` 

## Restauração

- Se foram utilizados o **mysqldump** ou **mysqlpump**, basta usar o próprio comando mysql para a recuperação:
	- `mysql -u [username] -p[password] [db_name] < backup.sql`
- O MySQL suporta a restauração através dos logs binários. Recuperação **point-in-time**
