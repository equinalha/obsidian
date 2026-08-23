---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2024-08-26T17:59:00
Owner:
  - Eduardo Quinalha
---
Funciona em conjunto com EJB

> [!tip] 💡
> JTA usa o EJB para a criação de contextos transacionais

Uma anotação `@Transactional` na declaração do bean sinaliza para o EJB que o controle de transações será feito pelo application server

- **Mandatory**
	- **Não há Transação JTA: **Joga exceção
	- **Transação JTA Pré Existente: **Herda a transação
- **Required**
	- **Não há Transação JTA:** Cria uma nova transação
	- **Transação JTA Pré Existente:** Herda a transação existente
- **RequiredNew**
	- **Não há Transação JTA:** Cria uma nova transação
	- **Transação JTA Pré Existente: **Joga uma exceção
- **Supports**
	- **Não há Transação JTA:** Continua sem transação
	- **Transação JTA Pré Existente:** Herda transação pré-existente
- **NotSupported**
	- **Não há Transação JTA: **Continua sem transação
	- **Transação JTA Pré Existente: **Suspende a transação
- **Never**
	- **Não há Transação JTA:** Continua sem transação
	- **Transação JTA Pré Existente: **Joga uma exceção

Existem 2 modos de gerenciamento:

- @TransactionManagement(TransactionManagementType.CONTAINER): As transações são gerenciadas automaticamente pelo app server. Valor default
- @TransactionManagement(TransactionManagementType.BEAN): Gerenciamento manual dentro do Bean:

```java
em.getTransaction().begin();

// (...)

em.getTransaction().commit();
```

## @Transactional vs @TransactionAttribute

As anotações `**@TransactionAttribute**` e `**@Transactional**` são usadas em diferentes contextos e tecnologias Java para gerenciar transações, e suas diferenças principais são:

1. **Contexto de Uso**:
	- `**@TransactionAttribute**`: Esta anotação faz parte do Java EE ou Jakarta EE e é usada principalmente em Enterprise JavaBeans (EJBs) para definir o comportamento de transação de métodos de negócios dentro de um container EJB.
	- `**@Transactional**`: Esta anotação faz parte do Java Persistence API (JPA) e é usada em classes e métodos de aplicativos Java SE ou Java EE para gerenciar transações em operações que envolvem acesso a banco de dados por meio de JPA.
2. **Finalidade**:
	- `**@TransactionAttribute**`: Ela define o comportamento de transação para métodos de negócios em EJBs, como quando uma transação deve ser iniciada, como ela deve ser propagada e se o método deve participar de uma transação existente ou criar uma nova. Ela é usada principalmente em EJBs stateless ou stateful.
	- `**@Transactional**`: Ela define o escopo de transação para métodos que usam JPA para interagir com bancos de dados. Você pode usá-la para marcar métodos de serviço ou repositório que acessam o banco de dados e especificar se a operação deve ser realizada dentro de uma transação.
3. **Tecnologia Relacionada**:
	- `**@TransactionAttribute**`: Relacionada ao Java EE ou Jakarta EE, especificamente aos EJBs e ao gerenciamento de transações dentro desse ambiente.
	- `**@Transactional**`: Relacionada ao Java Persistence API (JPA) e ao gerenciamento de transações em operações de banco de dados usando JPA.
