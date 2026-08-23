---

---
# JPA Básico

# Motivações

- O JDBC embora facilitou o trabalho com banco de dados, trouxe a complexidade para dentro das classes DAO.
- Alto acoplamento com o banco de dados (uma alteração no banco, pode quebrar vários pontos da aplicação)

## Hibernate

Simplificação do JDBC;

Direitos comprados pela Red Hat → JBOSS

Biblioteca de persistência, desenvolvida de forma livre, depois incorporada ao Java

## JPA

Java Persistence API

Camada de **abstração** entre a aplicação e a biblioteca de persistência

é a **ORM**

Visa simplificar a troca de uma biblioteca de persistência para outra (Hibernate é uma biblioteca de persistência)

![[SubPages/Pessoal/images/Untitled 126.png]]

## Configurando o ***persistence.xml***

```xml
<?xml version="1.0" encoding="UTF-8"?>
<persistence version="2.2"
	xmlns="http://xmlns.jcp.org/xml/ns/persistence"
	xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
	xsi:schemaLocation="http://xmlns.jcp.org/xml/ns/persistence http://xmlns.jcp.org/xml/ns/persistence/persistence_2_2.xsd">
	<persistence-unit name="loja"
		transaction-type="RESOURCE_LOCAL">
		<properties>
			<property name="javax.persistence.jdbc.driver" value="com.mysql.jdbc.Driver" />
            <property name="javax.persistence.jdbc.url" value="jdbc:mysql://172.17.0.2:3306/jpaloja" />
            <property name="javax.persistence.jdbc.user" value="root" />
            <property name="javax.persistence.jdbc.password" value="root" />
            
            <property name="hibernate.dialect" value="org.hibernate.dialect.MySQL8Dialect" />
            <property name="hibernate.show_sql" value="true" />
            <property name="hibernate.hbm2ddl.auto" value="update" />
		</properties>
	</persistence-unit>
</persistence>
```

## Criando uma entidade

```java
@Entity
@Table(name = "produtos")
public class Produto {
	@Id
	@GeneratedValue(strategy = GenerationType.IDENTITY)
	private long id;
	private String nome;
	@Column(name = "desc")
	private String descricao;
	private BigDecimal preco;
}
```

## EntityManager

> [!tip] 💡
> Equivale ao ***Connection ***do jdbc. É uma interface que faz a ponte entre as entidades (classes) e o banco de dados.
Como o ***EntityManager*** é uma interface, e não uma classe, não pode ser instanciado diretamente. É necessário criar um objeto da classe ***EntityManagerFactory. ***Para obter um objeto desta classe, solicita-se via método estático da classe ***Persistence, ***passando como parâmetro o nome da persistence-unit, criada no persistence.xml

```java
public class CadastroDeProduto {
	public static void main(String[] args) {

		Produto celular = new Produto();
		celular.setNome("Xiaomi RedMi");
		celular.setDescricao("Camera 40 MP");
		celular.setPreco(new BigDecimal("1500"));

		EntityManagerFactory factory = Persistence.createEntityManagerFactory("loja");
		EntityManager em = factory.createEntityManager();

		// Quando transaction-type="RESOURCE_LOCAL" na persistence-unit é necessário
		// gerenciar a transaction manualmente
		// Quando é utilizado algum servidor de aplicações, as transações são
		// gerenciadas automaticamente.
		
		em.getTransaction().begin();
		em.persist(celular);
		em.getTransaction().commit();
		em.close();
	}
}

```

![[SubPages/Pessoal/images/Untitled 127.png]]

## Ciclo de vida das Entidades no JPA

## No ***Insert***

- ***Transient:*** Objeto instanciado (new). Não tem sincronismo com o banco de dados. Funciona como um objeto normal do Java;
- ***Managed***: Ocorre após chamar o método persist(). Qualquer modificação nos atributos do objeto será sincronizado com o BD (Com a chamada dos métodos commit() ou flush());
- ***Detached:*** Ocorre após o método close() ou clear() do EntityManager. Neste estado, as alterações no objeto não serão sincronizadas com o banco.

### No *Update*

- Se a entidade estiver no estado DETACHED, pode-se utilizar o método merge() para trazê-la de volta ao estado MANAGED;
- No entanto, o método merge() não coloca a entidade imediatamente no modo MANAGED, ela retorna uma nova referência que, esta sim, encontra-se no estado MANAGED;

 

```java
Produto celular = new Produto("Celular", "Xiaomi"); // TRANSIENT
em.persist(celular); // MANAGED
em.close(); // DETACHED

celular = em.merge(celular); // MANAGED
celular.setMarca("One Plus");
```

### No *Delete*

- **Managed:** A entidade está sincronizada;
- **Removed:** Após o método remove(). Dispara um ***delete*** no banco de dados assim que for utilizado o ***commit() ***ou ***flush()***;

## Buscando dados no banco

```java
public Produto buscarPorId(Long id) {
		return em.find(Produto.class, id);
	}
	
	public List<Produto> listar(){
		// A Query é elaborada em JPQL
		String jpql = "SELECT p FROM Produto p";
		return em.createQuery(jpql, Produto.class).getResultList();
	}
```

### Usando filtros de entidades

```java
public List<Produto> buscarPorNome(String nome) {
		String jpql = "SELECT p FROM Produto WHERE p.nome = :nome";

		return em.createQuery(jpql, Produto.class)
				.setParameter("nome", nome)
				.getResultList();
	}
```

```java
public List<Produto> buscarPorNomeDaCategoria(String nome) {
																							// Aqui o JOIN ocorre automaticamente
		String jpql = "SELECT p FROM Produto WHERE p.categoria.nome = :nome";

		return em.createQuery(jpql, Produto.class)
				.setParameter("nome", nome)
				.getResultList();
	}
```

### Usando filtros de atributos

```java
public BigDecimal buscarPrecoDoProdutoPeloNome(String nome) {
		String jpql = "SELECT p.preco FROM Produto WHERE p.nome = :nome";

		return em.createQuery(jpql, BigDecimal.class)
				.setParameter("nome", nome)
				.getSingleResult();
	}
```

---

# JPA Avançado

### Relacionamento muitos para muitos

```java
@ManyToMany
	@JoinTable(name = "item_pedido")
	private List<Produto> produtos;
```

### Mapeamentos Bidirecionais

Se não for indicado o mappedBy, o JPA entende que é um novo relacionamento e cria uma nova tabela

```java
// Classe Pedido
	@Id
	@GeneratedValue(strategy = GenerationType.IDENTITY)
	private long id;
	private BigDecimal valorTotal;
	private LocalDate dataCadastro = LocalDate.now();
	
	@ManyToOne
	private Cliente cliente;
	
	@OneToMany(mappedBy = "pedido", cascade = CascadeType.ALL) // Aqui vai o nome do atributo que é mapeado do outro lado
																														 // O cascade é necessário para que o JPA faça automaticamente a persistência da entidade item_pedido
	private List<ItemPedido> itens;
```

```java
// Classe ItemPedido
	@Id
	@GeneratedValue(strategy = GenerationType.IDENTITY)
	private long id;
	private BigDecimal precoUnitario;
	private int quantidade;
	
	@ManyToOne
	private Pedido pedido; // Atributo mapeado pelo outro lado
	
	@ManyToOne
	private Produto produto;
```

```java
// Classe Produto
	@Id
	@GeneratedValue(strategy = GenerationType.IDENTITY)
	private long id;
	private String nome;
	private String descricao;
	private BigDecimal preco;
	private LocalDate dataCadastro = LocalDate.now();
	
	@ManyToOne
		private Categoria categoria;
```

### Trabalhando com relatórios

```java
public List<RelatorioDeVendasVo> relatorioDeVendas(){
		String jpql = "SELECT new br.com.alura.vo.RelatorioDeVendasVo("
				+ "produto.nome, "
				+ "SUM(item.quantidade),"
				+ "MAX(pedido.dataCadastro)) "
				+ "FROM Pedido pedido "
				+ "JOIN pedido.itens item "
				+ "JOIN item.produto produto "
				+ "GROUP BY produto.nome "
				+ "ORDER BY SUM(item.quantidade) DESC";
		
		return em.createQuery(jpql, RelatorioDeVendasVo.class).getResultList();
	}
```

### Named Query

É possível especificar a query dentro da própria entidade.

```java
@Entity
@Table(name = "produtos")
@NamedQuery(name = "Produto.produtosPorCategoria", query = "SELECT p FROM Produto p WHERE p.categoria.nome = :nome")
public class Produto {

	@Id
	@GeneratedValue(strategy = GenerationType.IDENTITY)
(...)
```

```java
public List<Produto> buscarPorNomeDaCategoria(String nome) {

		return em.createNamedQuery("Produto.produtosPorCategoria", Produto.class)
				.setParameter("nome", nome)
				.getResultList();
	}
```

### Performance: ***Eager vs Lazy***

> [!tip] 💡
> Todo relacionamento do tipo ***ToOne*** (ex: @*ManyToOne, @OneToOne*) é por padrão do tipo ***Eager***: quando o select busca a entidade, automaticamente faz o JOIN com os relacionamentos, trazendo estas entidades também.
Todo relacionamento do tipo ***ToMany*** (ex: *@ManyToMany, @OneToMany) *é por padrão do tipo ***Lazy***: quando o select busca a entidade, os relacionamentos não serão carregados via JOIN, a menos que alguma propriedade destes seja acessada.

Para alterar o comportamento, pode-se utilizar a propriedade **fetch. **O que é considerado uma boa prática a fim de melhorar o desempenho

```java
@ManyToOne(fetch = FetchType.LAZY)
	private Cliente cliente;
```

### Forçando o carregamento de relacionamento **Lazy** na consulta principal

```java
public Pedido buscarComCliente(Long id) {
		return em.createQuery("SELECT p FROM Pedido p JOIN FETCH p.Cliente WHERE p.id = :id", Pedido.class)
				.setParameter("id", id)
				.getSingleResult();
	}
```

### Select com parâmetros flexíveis

```java
public List<Produto> buscarPorParametros(String nome, BigDecimal preco, LocalDate dataCadastro){
		String jpql = "SELECT p FROM Produto p WHERE 1=1 ";
		
		if(nome != null && nome.trim().isEmpty()) {
			jpql += "AND p.nome = :nome ";
		}
		if(preco != null) {
			jpql += "AND p.preco = preco ";
		}
		if(dataCadastro != null) {
			jpql += "AND p.dataCadastro = :dataCadastro ";
		}
		
		TypedQuery<Produto> query = em.createQuery(jpql, Produto.class);
		

		if(nome != null && nome.trim().isEmpty()) {
			query.setParameter("nome", nome);
		}
		if(preco != null) {
			query.setParameter("preco", preco);
		}
		if(dataCadastro != null) {
			query.setParameter("dataCadastro", dataCadastro);
		}
		
		return query.getResultList();
		
	}
```

```java
public List<Produto> buscarPorParametrosComCriteria(String nome, BigDecimal preco, LocalDate dataCadastro){
		CriteriaBuilder builder = em.getCriteriaBuilder();
		CriteriaQuery<Produto> query = builder.createQuery(Produto.class);
		Root<Produto> from = query.from(Produto.class);
		
		Predicate filtros = builder.and(null);
		
		if(nome != null && nome.trim().isEmpty()) {
			filtros = builder.and(filtros, builder.equal(from.get("nome"), nome));
		}
		if(preco != null) {
			filtros = builder.and(filtros, builder.equal(from.get("preco"), preco));
		}
		if(dataCadastro != null) {
			filtros = builder.and(filtros, builder.equal(from.get("dataCadastro"), dataCadastro));
		}
		
		query.where(filtros);
		
		return em.createQuery(query).getResultList();
		
	}
```

### Atributos “Embutíveis”

Permite estender os campos de uma entidade com outra classe, a fim de melhorar a organização do código. Não será criado uma tabela extra para a classe embutida, os atributos serão considerados como sendo da entidade principal.

```java
@Embeddable
public class DadosPessoais {

	private String nome;
	private String cpf;

(...)
```

```java
@Entity
@Table(name = "clientes")
public class Cliente {

	@Id
	@GeneratedValue(strategy = GenerationType.IDENTITY)
	private Long id;
	@Embedded
	private DadosPessoais dadosPessoais;
	
	public Cliente(String nome, String cpf) {
		this.dadosPessoais = new DadosPessoais(nome, cpf);
		
	}
```

### Herança em JPA

```java
@Entity
@Table(name = "produtos")
@NamedQuery(name = "Produto.produtosPorCategoria", query = "SELECT p FROM Produto p WHERE p.categoria.nome = :nome")
@Inheritance(strategy = InheritanceType.SINGLE_TABLE)
public class Produto {

	@Id
	@GeneratedValue(strategy = GenerationType.IDENTITY)
	private long id;
	private String nome;
	private String descricao;
	private BigDecimal preco;
	private LocalDate dataCadastro = LocalDate.now();
	
	@ManyToOne(fetch = FetchType.LAZY)
	private Categoria categoria;
```

A anotação @Inheritance é utilizada apenas na classe mãe. A estratégia pode ser:

- SINGLE_TABLE: Todos os campos das classes filhas são criados na tabela mãe. Um campo adicional é criado para indicar o tipo do registro (classes filhas)
- JOINED: Cada classe filha tem uma tabela própria e é criado também uma tabela para a classe mãe. A conexão é feita pelo **id **de ambas as classes (mãe e filha)
- TABLE_PER_CLASS: Não cria a tabela para a classe mãe, apenas as classes filhas, com todos os atributos próprios e os herdados.

### Chaves Compostas

Deve ser criada uma classe separada, do tipo “embutível” com os atributos da chave composta

```java
@Embeddable
public class CategoriaId {
	private String nome;
	private String tipo;
(...)
```

```java
@Entity
@Table(name = "categorias")
public class Categoria {

	@EmbeddedId
	private CategoriaId id;
(...)
```
