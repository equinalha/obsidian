---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2024-08-26T17:59:00
Owner:
  - Eduardo Quinalha
---
```java
Class AlunoDAO {
	private EntityManager em;

	public AlunoDAO () {
		this.em = new JPAFactory().getEm();
	}

	public void salvar(Aluno aluno) {
		em.getTransaction().begin();
		em.persist(aluno);
		em.getTransaction().commit();
	}
}

// Um problema do código acima é que, no construtor é aberto uma nova conexão com o banco. Não existe um local adequado para o fechamento 
// desta.

// O resultado é um alto acoplamento e baixa coesão. A classe AlunoDAO depende de EntityManager, porém para obter esta é necessário
// outro acoplamento com JPAFactory

// Outro problema é que, caso o método salvar seja utilizado para salvar mais de uma entidade na sequência, será inicializado e finalizado
// vários contextos transacionais. Não é possível obter um contexto único para várias operações

// Um terceiro problema será a repetição de código para cada um dos métodos da classe: remove, update, delete.
```

# IoC e CDI

- O Desenvolvedor não é mais o responsável por controlar a infraestrutura (conexão com o banco, transação, etc…)
- Estes recursos são providos pelo container
- O container vai injetar as dependências e controlar o ciclo de vida delas
- Para habilitar o CDI na aplicação, utiliza-se o arquivo `beans.xml`
- Uma vez habilitado, o CDI vai gerenciar o ciclo de vida de todas as classes concretas da aplicação

```java
Class AlunoDAO {
	private EntityManager em;

	public AlunoDAO (EntityManager em) {  // Dependência de EntityManager
		this.em = em;
	}

	public void salvar(Aluno aluno) {
	
		em.persist(aluno);

	}
}

// Neste caso, teria-se que criar um EntityManager e fornecê-lo à alunoDAO
// Nesta classe, o controle de injeção de dependência é manual
```

- O objetivo é terceirizar para o container a injeção de dependências
- Este é o objetivo da especificação CDI (Context Dependency Injection)
- Como CDI é uma especificação, depende de uma implementação.
	- A impelmentação mais comum é a `Weld`

```java
Class AlunoDAO {

	private EntityManager em;

	@Inject
	public AlunoDAO (EntityManager em) {  // Dependência de EntityManager
		this.em = em;
	}

	public void salvar(Aluno aluno) {
	
		em.persist(aluno);

	}
}

// Outra classe
public static void main (String[] args) {
	
	@Inject
	AludoDAO alunoDAO;        // A criação do objeto é feita automaticamente pelo container

	// (...)

}
```

- Anotações
	- `@Inject`
	- `@Produces`
	- `@Disposes`
- Escopos
	- `@RequestScoped`
	- `@SessionScoped`
	- `@ApplicationScoped`
	- `@ConversationScoped`
	- `@Dependent`
- **AmbiguousDependencyInjection**
	- Ocorre quando a injeção é da interface, porém existem mais de uma implementação possível para esta
![[Untitled 552.png]]
	- Neste contexto, usam-se os **Qualificadores**
		- Criam-se novas anotações, anotadas com a anotação `@Qualifier`
```java
@Qualifier
@Interface JPADao {

}

@Qualifier
@Interface JDBCDao {

}
```
		- Nas classes DAO que serão injetadas, acrescentam-se também as anotações
![[Untitled 553.png]]
		- E na chamada, anota-se qual é a dependência que deverá ser injetada
![[Untitled 554.png]]
- Interceptors
	- Intercepta chamadas às classes, podendo executar código antes ou depois
	- Usado para criar o ambiente transacional na persistência
	- Tem característica transversal às das classes, ou seja, pode executar uma mesma funcionalidade que será disparada para várias classes
	- **Não executam lógica de negócio!**
	- **Pode ser um padrão usado por múltiplas aplicações!**
- Observer
	- Usado para disparar eventos que podem ser utilizados por outras classes
- Decorators
	- Adiciona funcionalidades a uma classe de forma dinâmica
	- **Pode ser usado para lógica de negócio!**
	- **É específico de uma aplicação particular!**

![[CDI.png]]
