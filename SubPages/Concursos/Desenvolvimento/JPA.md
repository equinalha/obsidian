---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2024-08-26T17:59:00
Owner:
  - Eduardo Quinalha
---
[https://www.baeldung.com/learn-jpa-hibernate](https://www.baeldung.com/learn-jpa-hibernate)

# JPA

JPA é uma especificação, baseada no hibernate. É um ORM.

A implementação de referência do JPA é a EclipseLink e também Open JPA

Por baixo dos panos, também usa JDBC

Para utilizar JPA ou Hibernate, utilizamos um arquivo chamado persistence.xml, onde ficam configurados as “persistence units”, que são depois referenciadas no código para se obter a conexão.

> [!note] 🔥
> É obrigatório a existência de um construtor padrão (sem argumentos)

<!-- Column 1 -->
```java
// Sem JPA / JDBC Puro
import java.sql.Connection;
import java.sql.SQLException;
import java.time.LocalDate;
import java.util.List;

import DAO.AlunoDAO;
import modelo.AlunoJDBC;
import utilJDBC.ConnectionFactory;

public class TesteJDBC {
	public static void main(String[] args) throws SQLException, ClassNotFoundException {
		Connection conn = ConnectionFactory.getConnection();
		
		AlunoJDBC aluno1 = new AlunoJDBC("Patricia", LocalDate.now(), "Rua dos Borracheiros, 15");
		AlunoDAO alunoDao = new AlunoDAO(conn);
		
		alunoDao.salvar(aluno1);
			
		List<AlunoJDBC> alunos = alunoDao.buscar("Joao");
		
		alunos.forEach(System.out::println);
		
		AlunoJDBC aluno2 = alunoDao.buscar(4);
		System.out.println("Achei " + aluno2);
	}
}
```

<!-- Column 2 -->
```java
// Com JPA
import java.time.LocalDate;

import javax.persistence.EntityManager;
import javax.persistence.EntityManagerFactory;
import javax.persistence.Persistence;

import model.Aluno;

public class Teste {

	public static void main(String[] args) {
		EntityManagerFactory emf = Persistence.createEntityManagerFactory("teste");
		EntityManager em = emf.createEntityManager();
		
		Aluno aluno = new Aluno("Joao", LocalDate.now(), "Rua Matacavalos, 10");
		
		em.getTransaction().begin();
		em.persist(aluno);
		em.getTransaction().commit();
		em.close();

	}

}
```


## Principais annotations

- `@Entity`
- `@Id`
- `@GeneratedValue`
- `@Table(name=”NomeTabela”)`
- `@Column(name=”Nome Coluna”)`
- `@Transient `   → Atributo que existe somente no OO e não no banco
- `@Embeded` → Em uma relação @OneToOne, a segunda entidade é colocada na mesma tabela da primeira
- `@Enumerated` → Usada para persistir um tipo enumerado

```java
@Enumerated(EnumType.STRING)
    private Gender gender;

(...)
public enum Gender {
    MALE, 
    FEMALE
}
```

> [!note] 🔥
> Em um relacionamento Um para Muitos, no lado Um, usamos a anotação **@OneToManny.
**No lado Muitos, se usarmos apenas a anotação **@MannyToOne**, o JPA vai criar uma tabela associativa a mais. Para evitar-se isso, utiliza-se a anotação da seguinte forma:
**@MannyToOne(mappedBy = “Nome do campo no lado One”);**

- `**@Basic**` → O atributo é um tipo primitivo mapeado diretamente na coluna correspondente da tabela. **Esta anotação diz respeito à entidade JPA e não à coluna da tabela**
	Normalmente esta anotação é suprimida, porém ela possui dois atributos default que, caso necessário alterar seu comportamento, deverão ser especificados. São eles
	- Optional: Define se o atributo pode ser null ou não
	- Fetch: Se o atributo é Eager ou Lazy
```javascript
@Entity
public class Course {
    
    @Id
    private int id;
    
    @Basic(optional = false, fetch = FetchType.LAZY)
    private String name;
    ...
}
```

- `**@Access**`** → **Define como acessar os atributos da entidade.
	- `@Access(AccessType.FIELD)`: A entidade será mapeada diretamente através de seus atributos.
	- `@Access(AccessType.PROPERTY)`: Serão utilizados os métodos getters e setters para acesso ao atributo.
- `@ElementCollection`
	- Especifica uma coleção de valores simples, usada pela entidade, e que não precisa ser armazenada em uma tabela separada, como no caso de uma relação oneToManny
- `@CollectionTable`
	- Usada em conjunto com `@ElementCollection` para indicar detalhes da tabela que fará o armazenamento dos valores da coleção
- `@Embeddable` vs `@Embedded`
	- `@Embeddable`** **define uma classe como sendo incorporável por outra
		- Isto é útil quando há um relacionamento de 1 para 1 entre duas entidades, porém queremos armazená-las na mesma tabela do banco
	- `@Embedded` faz a incorporação de uma classe `@Embeddable` na classe atual.
	- Exemplo:
```java
// gostaríamos disso:
@Entity
public class Company {
    private Integer id;
    private String name;
    private String address;
    private String phone;
    private String contactFirstName;
    private String contactLastName;
    private String contactPhone;
}

// Porém, contact e company devem ser entidades diferentes na aplicação. Então:
@Embeddable
public class ContactPerson {
    private String firstName;
    private String lastName;
    private String phone;
}

@Entity
public class Company {
    @Id
    @GeneratedValue
    private Integer id;
    private String name;
    private String address;
    private String phone;
    @Embedded
		@AttributeOverrides({
		  @AttributeOverride( name = "firstName", column = @Column(name = "contact_first_name")),
		  @AttributeOverride( name = "lastName", column = @Column(name = "contact_last_name")),
		  @AttributeOverride( name = "phone", column = @Column(name = "contact_phone"))
		})
    private ContactPerson contactPerson;
}
```

### Beans Validation

Biblioteca com anotações extras que permitem realizar validações nos atributos das entidades, por exemplo:

- @Email
- @Past (data no passado)
- @NotNull

No JPA, quem implementa o Beans Validation é o Hibernate Validations

## CRUD

> [!note] 🔥
> O JPA não tem um método para listar e obter vários registros de uma vez. Neste caso utiliza-se **JPQL**

SELECT a FROM ==Aluno== a (utiliza-se o nome da entidade ao invés do nome da tabela)

- CREATE → **em.persist(Entidade);**
- RETRIEVE → **entidade.find(Entidade.class, ValorChavePrimária)**; → Busca apenas pela chave primária
- UPDATE → Se a entidade estiver persistida, é automático
- DELETE → **em.remove(Entidade)**;

### Criteria Builder

Outra forma de fazer consultas elaboradas no banco de dados além dos métodos da JPA e JPQL, usando objetos.

## Estados e Mapeamentos

- **Transient:** Neste estado o objeto não possui Id e nem está no banco de dados. Ocorre logo após o instanciamento do objeto
- **Managed:** Neste estado o objeto possui Id, está no banco e é sincronizado com o banco
- **Detached: **Neste estado, o objeto possui Id, pode ou não estar no banco, porém as modificações não são sincronizadas com o banco. Ocorre quando chama-se o método detached(), quando se dá um Clear() EntityManager ou quando se fecha o EM.

Para se colcocar um objeto que estava Detached novamente no estado Managed, utiliza-se o método merge(). O merge vai criar uma nova instância, esta sim, no estado managed.

> [!note] 🔥
> **Merge vs Persist
**O persist() só funciona com entidades no estado **transient**, ou seja, sem Id definido. Mesmo que o Id seja setado manualmente, a entidade irá para o estado **detached** que não pode ser gerenciado pelo persist()

O merge() funciona tando com objetos no estado **transient** quanto **detached**. Porém, ele não passa o objeto para o estado **managed**. O que ele faz é criar uma nova instância do objeto, esta sim no estado **managed.** O que pode ser feito é uma reatribuição da instancia para o objeto original. Por exemplo:

aluno = em.merge(aluno);

![[Untitled 545.png]]

## Pool de Conexões

O pool de conexão o hibernate não é adequado para uso em produção

O mais utilizado atualmente é o Hikari, em substituição ao C3P0, que vem junto com o Hibernate

Os servidores de aplicação como Wildfly e servlet container como Tomcat, já possuem gerenciamento de pool de conexões.

## Hibernate puro vs JPA

> [!note] 🔥
> No JPA, as configurações fica no arquivo persistence.xml
No Hibernate puro, ficam no arquivo hibernate.cfg.xml

> [!note] 🔥
> Existem 3 arquivos de configuração no Hibernate puro:

hibernate.cfg.xml
hibernate.properties
hbm.xml

Os dois primeiros têm a mesma função, sendo que o primeiro sobrescreve o segundo se ambos existirem
o hbm.xml é o responsável por configurar os mapeamentos. Atualmente em desuso e deu lugar às configurações por anotações

> [!note] 🔥
> POJO:
Objeto simples, com apenas o construtor padrão, que não recebe argumentos
Também não devem estender classes e interfaces
Todo Javabean é um POJO, mas nem todo POJO é um javabean