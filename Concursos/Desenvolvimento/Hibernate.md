---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2024-12-07T10:06:00
Owner:
  - Eduardo Quinalha
---
# Características

> [!tip] 💡
> **Hibernate ORM**
> trabalha com banco de dados relacional
> 
> **Hibernate OGM**
> 
> trabalha com bancos de dados NoSQL

- Baseado em nomenclatura JavaBean para as classes de entidades
- Apesar de o padrão JavaBeans especificar getters and setters, o Hibernate pode acessar os atributos diretamente
- O atributo id é necessário
- O setter do atributo id deve ser privado
- O construtor sem argumentos é necessário para todas as entidades
- Trabalha com consultas em:
	- SQL
	- HQL
	- Criteria API
- `@GeneratedValue` - **ISTA**
	- **GenerationType.IDENTITY - **O valor da chave primária será gerado automaticamente pelo banco. Funciona em MySQL e SQL Server
	- **GenerationType.SEQUENCE - **O valor será gerado por uma sequence de banco. O nome da sequence deve ser especificado pelo parâmetro `generator`
	- **GenerationType.TABLE - **Valor gerado por meio de uma tabela especial no banco. O nome deve ser especificado no parâmetro` generator`
	- [**GenerationType.AUTO**](http://generationtype.auto/)** - **Geração do valor delegado para o próprio JPA com auxílio do banco.

## Arquitetura

![[Untitled 826.png]]

- As classes, interfaces e outros componentes são definidos no pacote **org.hibernate**
- Existem 3 arquivos de configuração
	- `hibernate.cfg.xml`
		- Informações sobre conexões com o banco, usuários, senha, etc.
		- Tipo de cache utilizado
		- caminho para o arquivo` hbm.xml`
		- Sobrescreve o `hibernate.properties`, caso os dois estejam configurados
```xml
<?xml version="1.0" encoding="UTF-8"?>
http://www.hibernate.org/dtd/hibernate-configuration-3.0.dtd">
<hibernate-configuration>
<session-factory>
 <property name="hibernate.connection.driver_class">com.mysql.jdbc.Driver</property>
 <property name="hibernate.connection.url">jdbc:mysql://localhost/banco_dados</property>
 <property name="hibernate.connection.username">usuario</property>
 <property name="hibernate.connection.password"/>senha</property>
 <property name="hibernate.dialect">org.hibernate.dialect.MySQLDialect</property>
 <property name="show_sql">true</property>
 <property name="hibernate.format_sql">true</property>
 <property name="hibernate.generate_statistics">true</property>
 <mapping resource="classePOJO.hbm.xml"/>
</session-factory>
</hibernate-configuration>
```

	- `hibernate.properties`
	- `hbm.xml`
		- Responsável pelo mapeamento relacional - objeto
```xml
<?xml version="1.0" encoding="UTF-8"?>
http://hibernate.sourceforge.net/hibernate-mapping-3.0.dtd">
<hibernate-mapping>
 <class name="aplicacao.exemplo" table="tabela_exemplo">
 <id column="id" name="id" type="java.lang.Long">
 <generator class="native"></generator>
 </id>
 <property column="nome" name="nome" length="50" type="java.lang.String"/>
 <property column="email" name="email" length="50" type="java.lang.String"/>
 <property column="data_nascimento" name="data_nascimento" type="java.util.Date"/>
 </class>
</hibernate-mapping>
```

## Ciclo de Vida

![[Untitled 827.png]]

- Transiente
	- Não associada a um contexto de persistência
	- Não tem Id
- Persistente
	- Associada a um contexto de persistência
	- Tem dados gravados no BD
	- Qualquer alteração no objeto será automaticamente sincronizada com o banco
- Desanexado
	- Esteve associado a um contexto de persistência, porém este foi removido
	- O objeto pode ser alterado e eventualmente, pode novamente ser persistido, porém depende de um comando para isso
- O objeto que descreve a entidade a ser persistida deve ser um POJO, anotado com `@Entity`
	- **Deve conter um construtor sem argumentos que seja visível com o menor escopo de proteção.**

## Componentes

- Session `org.hibernate.Session`
	- Objeto leve
	- Single Threaded
	- Vida curta
	- Representa uma comunicação
	- É criado pelo SessionFactory
- SessionFactory` org.hibernate.SessionFactory`
	- Thread Safe
	- Representa a coleção de objetos-relacional para um único banco de dados
	- É uma fábrica de sessões é necessário um SessionFactory por banco de dados utilizando um arquivo de configuração separado – semelhante ao EntityManagerFactory do JPA.
- Transaction `org.hibernate.Transaction`
	- Single Threaded
	- Vida curta
	- Transações
- Configuration `org.hibernate.Configuration`
	- Definições como driver, dialeto, etc.

## Tipos de dados

Os tipos declarados e utilizados nos arquivos de mapeamento **não são tipos de dados Java nem tipos de dados SQL** – eles são denominados **Tipos Hibernate** e podem traduzir do Java para SQL e vice-versa.

## Transações e Estratégia de Bloqueio

1. **Estratégia de bloqueio otimista: **
	- Nesse tipo de estratégia, o Hibernate utiliza mecanismos como colunas de versão (versioning) para detectar conflitos de atualização.
	- Cada registro possui uma versão associada, e antes de realizar um update no registro, o Hibernate verifica se a versão atual no banco de dados coincide com a versão que a transação possui.
	- Se não coincidir, significa que outro processo já atualizou o registro, e a transação atual pode ser cancelada ou manipulada de acordo com a política de resolução de conflitos definida.
2. **Estratégia de bloqueio pessimista: **
	- Essa estratégia envolve o bloqueio explícito de registros durante o acesso.
	- Quando uma transação acessa um registro, ela bloqueia o registro para impedir que outras transações façam alterações simultaneamente.
	- Isso pode ser feito usando bloqueios de leitura ou bloqueios de escrita, dependendo das necessidades da transação.

No Hibernate, ambas as estratégias são possíveis e podem ser configuradas conforme a necessidade da aplicação. O Hibernate permite que os desenvolvedores escolham entre as estratégias de bloqueio otimista e pessimista dependendo do caso de uso específico e dos requisitos de concorrência da aplicação.

## Herança

Existem 4 estratégias de herança:

- SINGLE TABLE (tudo numa tabela só),
- MAPPED SUPER CLASS (só existe no modelo O.O e não no relacional),
- JOINED TABLE (as tabelas possuem somente seus atributos específicios e uma chave do pai pra fazer join)
- TABLE por classe (tabelas com todos os atributos)

# Hibernate Envers

> [!note] 🔥
> Funciona tanto com o Hibernate ORM quanto JPA

- Usado para log e auditoria
- Trabalha com versionamento de entidades
- Possui uma API que permite consultar as revisões de cada entidade e verificar seus atributos
- Basta adicionar a anotação `@Audited` nos atributos auditados ou na class
	- Quando a anotação vai na classe, todos os atributos serão auditados
	- Quando a anotação vai nos atributos, apenas os atributos anotados serão auditados
- Faz o snapshot das entidades

```java
@Entity
public class Person {
    @Id
    @GeneratedValue
    private Integer id;

    @Audited
    private String name;

    @Audited
    private String surname;

    @Audited
    @ManyToOne
    private Address address;
}
```

- A leitura das revisões pode ser feita da seguinte maneira

```java
public void testBasicUsage() {
    ...
    AuditReader reader = AuditReaderFactory.get( entityManager );
    Event firstRevision = reader.find( Event.class, 2L, 1 ); //reader.find(classe, Id, rev)
    ...
    Event secondRevision = reader.find( Event.class, 2L, 2 );
    ...
}
```

- Cria automaticamente mais duas tabelas, além da entidade original:
	- <Entidade>_AUD
	- <Entidade>_REVINFO
```sql
create table Customer (
    id bigint not null,
    created_on timestamp,
    firstName varchar(255),
    lastName varchar(255),
    primary key (id)
)

create table Customer_AUD (
    id bigint not null,
    REV integer not null,
    REVTYPE tinyint,
    created_on timestamp,
    firstName varchar(255),
    lastName varchar(255),
    primary key (id, REV)
)

create table REVINFO (
    REV integer generated by default as identity,
    REVTSTMP bigint,
    primary key (REV)
)

alter table Customer_AUD
   add constraint FK5ecvi1a0ykunrriib7j28vpdj
   foreign key (REV)
   references REVINFO
```
