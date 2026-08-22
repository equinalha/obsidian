---
base: "[[Simulados.base]]"
Desempenho: 0.825
Banca: CEBRASPE
Obs: ""
1o Colocado: 0.65
Tipo: Múltipla Escolha
Obj: TSE
"% Colocação": 27
Status: Done
Data: 2024-10-25
---
62 - Considerando que, para implantar uma aplicação em um JBoss, foi identificada a necessidade de configurar um datasource para uma conexão em um banco de dados MySQL, assinale a opção em que é apresentado o arquivo de configuração que deve ser modificado para adicionar o referido datasource.
A persistence.xml
B host.xml
C jboss-ejb3.xml
**D standalone.xml**
E jboss-web.xml


`**persistence.xml**`: É usado para definir a configuração de JPA e a unidade de persistência, como entidades, gerenciadores de entidade e outros aspectos relacionados à persistência. Ele não é projetado para **gerenciar conexões de datasource em nível de servidor.**

```xml
<datasources>
    <datasource jndi-name="java:/jdbc/MySQLDS" pool-name="MySQLDS" enabled="true" use-java-context="true">
        <connection-url>jdbc:mysql://<host>:<port>/<database></connection-url>
        <driver>mysql</driver>
        <security>
            <user-name><username></user-name>
            <password><password></password>
        </security>
    </datasource>
    <drivers>
        <driver name="mysql" module="com.mysql">
            <xa-datasource-class>com.mysql.cj.jdbc.Driver</xa-datasource-class>
        </driver>
    </drivers>
</datasources>
```

O `persistence.xml` é parte do pacote da aplicação e pode variar de uma aplicação para outra. Em contraste, os datasources são geridos pelo servidor de aplicações, permitindo uma configuração centralizada que pode ser compartilhada entre diferentes aplicações.

Embora o `persistence.xml` não configure datasources diretamente, ele pode referenciar um datasource JNDI configurado no JBoss. Por exemplo

```xml
<persistence xmlns="http://xmlns.jcp.org/xml/ns/persistence"
             xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
             xsi:schemaLocation="http://xmlns.jcp.org/xml/ns/persistence
             http://xmlns.jcp.org/xml/ns/persistence/persistence_2_1.xsd"
             version="2.1">
    <persistence-unit name="MyPersistenceUnit">
        <jta-data-source>java:/jdbc/MySQLDS</jta-data-source>
        <class>com.example.MyEntity</class>
        <!-- Outras configurações -->
    </persistence-unit>
</persistence>
```

Ao utilizar DataSources diretamente, não é necessário uso de PU. Neste caso, no código Java, pode-se fazer a conexão diretamente com o datasource configurado no JBoss, geralmente usando JNDI. Isso requer um pouco mais de código para gerenciar a conexão.

```java
import javax.naming.InitialContext;
import javax.naming.NamingException;
import javax.sql.DataSource;
import java.sql.Connection;
import java.sql.SQLException;

public class MyApplication {
    public void execute() {
        try {
            InitialContext ctx = new InitialContext();
            DataSource ds = (DataSource) ctx.lookup("java:/jdbc/MySQLDS");
            try (Connection conn = ds.getConnection()) {
                // Operações com o banco de dados
            }
        } catch (NamingException | SQLException e) {
            e.printStackTrace();
        }
    }
}
```
