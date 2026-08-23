---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2024-10-10T12:28:00
Owner:
  - Eduardo Quinalha
---
# JDBC

![[JDBC.png]]

JDBC é uma especificação, uma API. O objetivo é padronizar métodos de conexão com banco de dados diferentes. Cada desenvolvedor de banco é responsável por implementar os drivers compatíveis com JDBC.

Os objetivos do JDBC são compatibilidade e portabilidade, além de independência da camada de dados.

A API **JDBC** está no **Java SE** (por consequência, também no Java / Jakarta EE)

> [!note] 🔥
> **Especificação** → JDBC
**Implementação** → Drivers

> [!note] 🔥
> **Trabalhando com Datas:

**O Java tem problemas com datas. A primeira API para trabalhar com datas foi [java.util.date](http://java.util.date/) que disponha de poucos métodos. Então surgiu java.util.calendar, também depreciado atualmente, e deu lugar a java.time após o Java 8.
java.time.LocalDate
java.time.LocalTime
java.time.LocalDateTime

Porém, o JDBC possui sua própria classe para trabalhar com datas: java.sql.Date

> [!note] 🔥
> **Possível questão de concurso!

**No Java SE, ao instanciar uma conexão JDBC, o driver respectivo é automaticamente carregado na memória, bastando para isso estar no class path (build Path) da aplicação.
No Java EE, isto não acontece! É necessário carregar a classe do driver (.jar) manualmente. Para isso, pode-se utilizar o recurso de **reflection**, conforme exemplo abaixo:

```java
public Connection getConexão() {
	try {
		Class.forName("org.postgresql.Driver"); // Reflection
		Connection conn = DriverManager.GetConnection("jdbc:postgresql://localhost:5432/banco", "usuario", "senha");
		return conn;
	} catch (SQLException | ClassNotFoundException e) {
		throw new IllegalStateException(e);
	}
}
```

## Passos para conectar-se com o banco e executar uma query

```java
// Registering the Driver - Opcional no Java SE
DriverManager.registerDriver(new com.mysql.jdbc.Driver());

// Getting the connection
String mysqlUrl = "jdbc:mysql://localhost/sampleDB";
Connection con = DriverManager.getConnection(mysqlUrl, "root", "password");

// Creating the Statement
Statement stmt = con.createStatement();
String sql = "SELECT * FROM DADOS";

// Executando
boolean resultado = stmt.execute(sql);
```

> [!note] 🔥
> DriverManager → Connection
Connection → Statement

## Diferença entre os métodos de execução de um Statement

- **execute() →** Retorna um boleano que indica se existem ou não resultados a serem recuperados (resultSet)
- **executeQuery() →** Retorna um resultSet
- **executeUpdate() →** Retorna um inteiro que indica o número de linhas afetadas pelo comando. Pode ser usando para insert, update e delete

## Métodos mais utilizados da classe Connection

- createStatement()
- prepareStatement()
- CallableStatement()

## Failover de conexões

É possível configurar um pool de conexões como estratégia de failover. Exemplo:

```java
jdbc:mysql://[primary host][:port],[secondary host 1][:port][,[secondary host 2][:port]]...[/[database]]»
[?propertyName1=propertyValue1[&propertyName2=propertyValue2]...]
```

## Pool de conexões

Pode ser adquirido, em JDBC, através do uso de Data Sources (application Servers), ou bibliotecas como c3p0, hikari, entre outras.

```java
// Usando Data Source
Connection con_object = DBCPDataSource.getConnection();

// Usando o c3P0
Connection con_object = C3p0DataSource.getConnection();
```