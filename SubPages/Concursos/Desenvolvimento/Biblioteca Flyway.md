---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2024-11-10T08:56:00
Owner:
  - Eduardo Quinalha
---
# Flyway

- Automatização e controle de versão de scripts SQL executados em bancos de dados
- Sincroniza o banco de dados com a versão da aplicação
- Automatiza a execução de scripts
- Criação da estrutura do banco do zero
- Mantém um controle das alterações feitas no banco via aplicação
- Possibilita um rollback
- Ferramenta para Java. Existem similares para outras linguagens e frameworks
- Processo inicial
	- Cria uma tabela chamada `flyway_schema_history`
	- Faz um scan no classpath buscando por migrations que podem ser escritas em SQL ou Java
	- As migrações são organizadas em ordem crescente de versão e aplicadas uma a uma

# Flyway no Java

```java
import org.flywaydb.core.Flyway;

public class App {
    public static void main(String[] args) {
        // Create the Flyway instance and point it to the database
        Flyway flyway = Flyway.configure().dataSource("jdbc:h2:file:./target/foobar", "sa", null).load();

        // Start the migration
        flyway.migrate();
    }
}
```

- Os scripts ficam na pasta `src/resources/db/migration/`
- Eles seguem uma convenção de nomenclatura que inclui um número de versão e uma descrição.

```java
V1__create_table.sql
V2__add_column.sql
V3__modify_data.sql
```

# Migrations

- Podem ser escritas em scripts SQL ou em Java
- Usando classes Java, é possível executar alterações mais complexas do que aquelas expressas em SQL
- Em java, as classes deverão implementar a interface `JavaMigration `

```java
import org.flywaydb.core.api.migration.BaseJavaMigration;
import org.flywaydb.core.api.migration.Context;
import java.sql.Statement;

public class V1__Create_users_table extends BaseJavaMigration {
	@Override
	public void migrate(Context context) throws Exception {
		try (Statement stmt = context.getConnection().createStatement()) {
			stmt.execute("CREATE TABLE users (" +
				"id SERIAL PRIMARY KEY, " +
				"username VARCHAR(50) NOT NULL UNIQUE, " +
				"email VARCHAR(100) NOT NULL UNIQUE, " +
				"password_hash VARCHAR(255) NOT NULL, " +
				"created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP, " +
				"updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP ON UPDATE
				CURRENT_TIMESTAMP" +
				")");
		}
	}
}
```

- O Flyway controla pela tabela `flyway_schema_history` todas as migrations que foram aplicadas
- Inclusive com checksum dos arquivos e, caso haja alguma alteração, gera um erro
- No processo de aplicação, ele varre a pasta que contém os scripts e aplica aqueles que ainda não foram registrados na tabela, em ordem

# Configuração

- As configurações podem ser feitas pelo arquivo `flyway.conf` ou diretamente no código java 

```java
flyway.url=jdbc:postgresql://localhost:5432/meubanco
flyway.user=meuusuario
flyway.password=minhasenha
flyway.locations=classpath:db/migration
```

# CLI

- O gerenciamento das migrations pode ser feito via CLI
- Comandos básicos:

![[image 132.png]]

![[image 133.png]]