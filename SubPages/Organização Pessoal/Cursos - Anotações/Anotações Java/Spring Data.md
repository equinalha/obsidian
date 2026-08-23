---

---
# Primeiros passos

> [!tip] 💡
> Framework que visa facilitar a integração com o banco de dados

1- Para iniciar o projeto, utilizar a ferramenta ***spring initializer***

[https://start.spring.io/](https://start.spring.io/)

![[SubPages/Pessoal/images/Untitled 128.png]]

2- Importar como Maven Project

3- Adicionar a dependência para conexão com o banco no pom.xml

4- Configurar as variáveis para conexão com o banco no application.properties

```java
spring.datasource.url=jdbc:mariadb://172.17.0.2:3306/springjpa

spring.datasource.username=root
spring.datasource.password=springjpa

spring.datasource.testWhileIdle=true
spring.datasource.validationQuery=SELECT 1

spring.datasource.driver-class-name=org.mariadb.jdbc.Driver

spring.jpa.show-sql=false
spring.jpa.hibernate.ddl-auto=update
spring.jpa.hibernate.naming-strategy=org.hibernate.cfg.ImproveNamingStrategy
spring.jpa.properties.hibernate.dialect=org.hibernate.dialect.MariaDBDialect
```

5- Criar uma interface ***Repository**** *que estende a classe ***CrudRepository***

```java
@Repository
public interface CargoRepository extends CrudRepository<Cargo, Integer> {
}
```

6- Na classe SpringDataApplication, utilizar o repository para persistir os dados

```java
@SpringBootApplication
public class SpringDataApplication implements CommandLineRunner {

	private final CargoRepository repository;
	
	// Injeção de dependência
	public SpringDataApplication(CargoRepository repository) {
		this.repository = repository;
	}
	
	public static void main(String[] args) {
		SpringApplication.run(SpringDataApplication.class, args);
	}

	@Override
	public void run(String... args) throws Exception {
		Cargo cargo = new Cargo();
		cargo.setDescricao("Desenvolvedor de Software");
		repository.save(cargo);
	}
}
```

# Usando Derivated Queries

> [!tip] 💡
> Pela composição do nome do método declarado na interface repository, o spring data automaticamente gera as queries, sem precisar digitá-las.

```java
@Repository
public interface FuncionarioRepository extends CrudRepository<Funcionario, Integer> {
	List<Funcionario> findByNome(String nome);
	List<Funcionario> findByNomeAndSalarioGreaterThanAndDataContratacao(String nome, Double salario, LocalDate data);
}
```

É possível também pesquisar pelo atributo de um relacionamento, da seguinte forma:

```java
List<Funcionario> findByCargoDescricao(String descricao);
```

ou:

```java
List<Funcionario> findByUnidadeTrabalhos_Descricao(String descricao);
```

Mais possibilidades:

[https://docs.spring.io/spring-data/jpa/docs/current/reference/html/#appendix.query.method.subject](https://docs.spring.io/spring-data/jpa/docs/current/reference/html/#appendix.query.method.subject)

# Usando JPQL

```java
@Repository
public interface FuncionarioRepository extends CrudRepository<Funcionario, Integer> {
	List<Funcionario> findByNome(String nome);
	
	@Query("SELECT f FROM Funcionario f WHERE f.nome = :nome AND f.salario >= :salario AND f.dataContratacao = :data")
	List<Funcionario> findNomeDataContratacaoSalarioMaior(String nome, Double salario, LocalDate data);
}
```

# Usando queries nativas

```java
// Query Nativa (nomes dos campos do banco de dados)
	@Query(value = "SELECT * FROM funcionarios f WHERE f.data_contratacao >= :data", nativeQuery = true)
	List<Funcionario> findDataContratacaoMaior(LocalDate data);
```
