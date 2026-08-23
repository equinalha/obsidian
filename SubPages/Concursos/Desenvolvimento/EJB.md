---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2024-08-26T17:59:00
Owner:
  - Eduardo Quinalha
---
<!-- Column 1 -->
![[Untitled 546.png]]

<!-- Column 2 -->
![[Untitled 547.png]]

# O que é EJB?

EJB é uma camada de serviços, provido pelo servidor de aplicação

O descritor de implantação do EJB é o arquivo **ejb-jar.xml**

EJB é o núcleo da Tecnologia Java EE

Em outras palavras, ele deixa o programador livre para se concentrar na lógica de negócio e na resolução do problema. Assim, o desenvolvedor não precisa mais se preocupar com codificação envolvendo infraestrutura (segurança, escalabilidade, entre outros)

> [!note] 🔥
> - EJB fornece serviços e está disponível nos application servers
- Tem a possibilidade de fornecer gerenciamento de entidades, embora esteja em desuso pois esta especificação passou para o JPA
- Pode fornecer Autenticação, gerenciamento de transações, sessões, Data-sources, Injeção de dependência, pool de conexões
- Pode ser stateless ou stateful
- Servlet container + EJB = Application Server
- São executados no lado do servidor
- persistência, integridade transacional e controle de concorrência.

> [!note] 🔥
> Stateless = conversacional

> [!note] 🔥
> **JBoss Seam 2**: Integra JSF e EJB3

> [!note] 🔥
> Com EJB em uso na situação em que, no pool de contêiner, haja diversas instâncias de um bean sem estado de sessão, a invocação de um método por um cliente pode ser delegada a qualquer uma das instâncias

## Tipos

- Sessions Beans (SB): Objeto não persistente que implementa lógica de negócio. Representa um único cliente. Podem ser invocados localmente, remotamente ou via webservices. Permite receber mensagens JMS porém apenas de forma síncrona
	- Stateless
		- Pool de objetos
		- Pode ter variáveis de instância, porém estas serão compartilhadas com todos os usuários
	- Stateful
	- Singleton
- Entity Bean: 
	- Opcional a partir do EJB 3.2. Foi substituído pelo JPA
- Message Driven Beans (MDB): 
	- Objeto não persistente que combina SB com listener de mensagens. Podem ser apenas stateless e invocados por meio de programação por um cliente local ou remoto

## Callbacks

Acionados durante o ciclo de vida de um EJB

- @PostConstruct
- @PrePassivate
- @PostActivate

## DataSource

Retira a configuração de acesso de dentro da aplicação e leva para o servidor. Desta forma, a aplicação funciona igualmente em qualquer ambiente, sendo que o que determina a especificidade de acesso de cada caso é o próprio servidor.

A requisição de dataSource é feita por meio de **JNDI**

### Usando DataSources (Wildfly)

No arquivo standalone.xml, criar a nova DS, com URL do banco, usuário e senha. Esta DataSource terá um nome, por exemplo: TesteDS. Também é configurado o endereço JNDI para acesso a este recurso pela aplicação.

Obs: Pode ser necessário instalar o driver do banco específico no servidor de aplicação (Wildfly)

No persistence.xml, a configuração será alterada (pontos destacados)

```xml
<persistence-unit name="teste" transaction-type="JTA"> <-- Era RESOURCE_LOCAL -->
		<jta-data-source>java:jboss/datasources/TesteDS</jta-data-source>
 
		<properties>
			<!-- As propriedades de conexão com o banco, devem ser todas removidas -->
			<!-- <property name="javax.persistence.jdbc.driver" value="org.postgresql.Driver" /> -->
			<!-- <property name="javax.persistence.jdbc.url" value="jdbc:postgresql://172.17.0.2:5432/teste" /> -->
			<!-- <property name="javax.persistence.jdbc.user" value="teste" /> -->
			<!-- <property name="javax.persistence.jdbc.password" value="teste" /> -->
			<property name="hibernate.dialect" value="org.hibernate.dialect.PostgreSQLDialect" />
			<property name="hibernate.show_sql" value="true" />
			<property name="hibernate.hbm2ddl.auto" value="create" />
		</properties>
	</persistence-unit>
```

# Injeção de Dependência e Inversão de Controle

Traz a responsabilidade de instanciamento de dependências de classes para o container

Um exemplo são entidades do Hibernate. Não é necessário que a classe (POJO) implemente ou herde qualquer outra classe para adicionar as funcionalidades do framework. As anotações se encarregam da injeção de dependência.
