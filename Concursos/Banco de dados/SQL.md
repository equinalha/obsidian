---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2026-08-03T15:50:00
Owner:
  - Eduardo Quinalha
---
> [!note] 🔥
> Conteúdos não triviais que mais caem!

> [!note] 🔥
> **os valores NULL não são considerados em nenhuma função agregada como **`**SUM()**`**, **`**AVG()**`**, **`**COUNT()**`**, **`**MAX()**`** e **`**MIN()**`**.** A exceção a esta regra é a regra `***COUNT***``**(*)**` que conta todas as filas, mesmo aquelas com valores NULL.

- Views
	- **CREATE VIEW nome AS <query>**
		- CREATE VIEW nome [coluna1, coluna2, …] as QUERY [WITH CHECK OPTION] (utilizado para restringir a inserção de dados na view)
	- São tabelas virtuais
	- Em regra, não atualizáveis
	- Não é necessário que tenha uma tabela base por baixo. A view pode ser construída em cima de outras views ou até mesmo em dados calculados.
- Semi JOINs
	- Pode-se utilizar subquerys no lugar de JOIN
	- **SELECT a1, a2 FROM t1 WHERE id IN (SELECT id FROM t2 WHERE …)**
- Updates em Querys com JOIN
	- É possível fazer update de uma tabela dentro de uma query com JOIN
	- **UPDATE t1 SET a=1 FROM tabela t1 JOIN tabela2 t2 ON **[**t1.id**](http://t1.id/)** = **[**t2.id**](http://t2.id/)** WHERE t1.col1 = 0 AND t2.col2 IS NULL**
- Índices
	- **CREATE INDEX idx_nome ON tabela(coluna)**
- TO_DATE
- COALESCE (col1, col2)
	- Retorna o primeiro valor não nulo

# Fundamentos

- Linguagem declarativa
- Não procedural
- Padrão ANSI, definido por norma
- Alguns SGBD’s implementam módulos declarativos adicionais ao SQL, chamados **dialetos**:
	- PL/SQL → Oracle
	- Transact → Microsoft
	- PL/pgSQL → PostgreSQL
- Dividida em sub-grupos
	- **DDL** → Data Definition Language
	- **DML** + **DQL** → Data Manipulation / Query Language
	- **DTL** → Data Transaction Language
	- **DCL** → Data Control Language

## Tipos de Dados

- CHAR(xx) - Ocupa exatamente a quantidade alocada. Caso faltem caracteres, preenche com espaço em branco.
	- Ex: ARTIST_NAME(60)
- VARCHAR - Alocado dinamicamente. Ocupa somente a quantidade de caracteres inseridos
- BLOB - Armazena tipos de arquivos binários. Tratado como strings binárias
	- Aponta para um local em disco onde ficam armazenados os arquivos
- CLOB - Grande quantidade de caracteres, até o valor especificado.
- **Numéricos**
	- Exatos
		- INTEGER
		- BIGINT
		- NUMERICAL(p,e)
			- Precisão
			- Escala
		- DECIMAL(p,e)
	- Aproximados
		- FLOAT
		- DOUBLE
		- REAL
- **Data**
	- TIME
	- DATETIME
	- TIMESTAMP
		- Com opcional WITH TIMEZONE
		- Campos DATE, TIME + 6 posições para a fração decimal de segundos
	- INTERVAL
- **NULL**
	- membro de todos os domínios 

## Outros Tipos

- ROW → Possibilita definir uma nova linha, dentro de um campo. Viola regras de Codd e formas normais
- ARRAY → Array de dados. Idem
- MULTISET → Conjunto de dados. Idem

# DML

São quatro os principais comandos (CRUD)

- **SELECT**
	- Somente FROM é obrigatório. As demais são opcionais
	- Se mais de uma tabela for especificada em FROM, é feito um produto cartesiano destas
![[Untitled 704.png]]
	- **Funções Agregadas (Group By Having)**
		- Operam sobre conjuntos de valores de uma coluna e retornam valores para cada conjunto:
			- COUNT()
			- SUM()
			- MAX()
			- MIN()
			- AVG()
		- Deve-se utilizar  GROUP BY para os atributos da cláusula SELECT que não apareçam como parâmetros nas funções agregadas
		- Pode-se aplicar HAVING para predicados após a formação dos grupos
	- UNION, INTERSECT e EXCEPT
		- Funcionam de forma semelhante às respectivas operações da álgebra relacional.
		- Estas operações eliminam duplicatas. Caso necessite das repetições é necessário especificar:
		- UNION ALL, INTERSECT ALL e EXCEPT ALL
	- Junções
		- INNER, LEFT, RIGHT FULL
		- Natural, ON, USING()
- **INSERT**
	- INSERT INTO TABELA VALUES (A1, A2, A3)
	- INSERT INTO TABELA (C1, C2, C3) VALUES (A1, A2, A3)
- **UPDATE**
	- UPDATE TABELA SET CAMPO=VALOR WHERE CONDIÇÃO
- **DELETE**
	- DELETE FROM TABELA WHERE CONDIÇÃO

# DDL

- View
	- **As permissões das views não são automaticamente herdadas das tabelas subjacentes**
- Index
	- Aumenta a eficiência para consultas SELECT
	- Degrada o desempenho para UPDATE, INSERT e DELETE
	- Pode ser denso ou esparso
	- CREATE INDEX idx_name ON tabela(coluna)
- TRUNCATE TABLE TABELA

# DCL

![[Untitled 705.png]]

- WITH GRANT OPTION permite que o usuário que recebeu o GRANT possa também conceder a mesma permissão a outros usuários

# Stored Procedures

```sql
CREATE PROCEDURE prc_nome
	(IN A1 CHAR(15), IN A2 DECIMAL(7,2), NO_SUBJECTS INT(3)) -- ENTRADA E SAÍDA DE DADOS
	LANGUAGE SQL MODIFIES SQL DATA
-- QUERY sql

-- CHAMANDO PROCEDURE
CALL prc_nome(parâmetros ...)
```

# Triggers

- São procedimentos armazenados executados automaticamente em resposta a eventos específicos.
- São utilizados para monitorar e restringir o acesso a dados de uma tabela.
- Podem ser acionados por INSERT, UPDATE ou DELETE.

Here's a basic syntax to create a trigger in SQL:

```plain text
CREATE TRIGGER trigger_name
{BEFORE | AFTER} {INSERT | UPDATE | DELETE}
ON table_name
[REFERENCING NEW AS new OLD AS old]
[FOR EACH ROW]
[WHEN (condition)]
BEGIN
    -- trigger logic goes here
END;

```

Here's an example of a trigger that automatically sets the modified date column to the current date and time every time a row is updated:

```plain text
CREATE TRIGGER update_modified_date
AFTER UPDATE ON my_table
FOR EACH ROW
BEGIN
    UPDATE my_table SET modified_date = NOW() WHERE id = NEW.id;
END;

```

This trigger will be executed after every UPDATE statement on the `my_table` table, and it will set the `modified_date` column to the current date and time for the row being updated.

Please note that the syntax and functionality of triggers may vary slightly depending on the specific database management system you are using.

# Transações

ACID:

- Atomicidade
- Consistência
- Isolamento
- Durabilidade

Principais comandos

- COMMIT
- SAVEPOINT
- ROLLBACK

Em SQL não existe BEGIN TRANSACTION

- Modo de acesso
	- READ ONLY
	- READ WRITE
- Tamanho da área de diagnóstico
	- DIAGNOSTIC SIZE n
- Nível de isolamento
	- READ UNCOMMITED (Leitura suja)
		- A leitura ocorre no meio de uma transação, porém ocorre ROLLBACK
	- READ COMMITED (Leitura não repetível)
		- 
	- REPEATABLE READ (Fantasmas)
	- SERIALIZABLE

```sql
EXEC SQL WHENEVER SQLERROR GOTO UNDO;
EXEC SQL SET TRANSACTION
	READ WRITE
	DIAGNOSTIC SIZE 5
	ISOLATION LEVEL SERIALIZABLE
EXEC SQL INSERT INTO EMPREGADO(PNOME, UNOME, SSN, DNO, SALARIO) VALUES ("Fulano", "Silva", 11123334, 2, 1200);
EXEC SQL UPDATE EMPREGADO SET SALARIO = SALARIO * 1.1 WHERE DNO = 2;
EXEC COMMIT
GOTO END;
UNDO: EXEC SQL ROLLBACK;
END: ...;
```

![[20230621_095930.jpg]]
