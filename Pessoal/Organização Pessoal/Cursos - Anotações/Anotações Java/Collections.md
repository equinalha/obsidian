---

---
<!-- Column 1 -->
![[SubPages/Pessoal/images/Untitled 121.png]]

<!-- Column 2 -->
- **List**
	- Permitem múltiplas inserções de um mesmo dado
	- Mantém a ordenação
	- Busca por valor implica em percorrer a lista O(n)
	- **ArrayList:**
		- Implementação de um array tradicional. 
		- Acesso rápido por índice O(1), 
		- rápida inserção e remoção no final da lista, 
		- porém lento para remover e inserir no meio ou início da lista
	- **LinkedList:**
		- Listas duplamente encadeadas.
		- Rápida inserção/remoção em qualquer posição
		- Lento para percorrer ou acessar por índice

- **Vector**
	- Permite acesso em múltiplas pilhas
- Set
	- Não mantêm ordenação
	- Não permitem duplicação
	- **HashSet**
		- Acesso por valor é imediato O(1)
		- Não existe acesso por índice
		- Na prática, cada valor (objeto) tem seu hash calculado e convertido no índice que representa sua posição na memória

# Método *contains()*

Este método utiliza por baixo dos panos os seguintes métodos, herdados da classe **Object()**, para avaliar se um elemento está presente na collection:

- **equals()** para objetos do tipo **List()**
- **hashCode()** para objetos do tipo **Set()**

Se não forem reescritos, estes métodos farão a comparação com base na referência ao objeto e mesmo dois objetos que possuam seus atributos idênticos retornaram sempre **false.**

==**Via de regra, sempre que um destes métodos for sobrescrito, o outro deverá ser sobrescrito também.**==

```java
@Override
	public boolean equals(Object obj) {
		Aluno outro = (Aluno) obj;
		return this.nome.equals(outro.getNome());
	}
	
	@Override
	public int hashCode() {
		return this.nome.hashCode();
	}
```

No eclipse é possível gerar estes métodos automaticamente, sendo que ele leva em consideração outros pontos importantes também.

Para isso basta fazer o seguinte:

- **Pressionar ctrl + 3**
- **Buscar por equals**
- **Clicar em *****“Generate hashCode() and equals()”***

```java
@Override
public int hashCode() {
    final int prime = 31;
    int result = 1;
    result = prime * result + ((nome == null) ? 0 : nome.hashCode());
    result = prime * result + numeroMatricula;
    return result;
    }
	@Override
	public boolean equals(Object obj) {
		if (this == obj)
			return true;
		if (obj == null)
			return false;
		if (getClass() != obj.getClass())
			return false;
		Aluno other = (Aluno) obj;
		return Objects.equals(nome, other.nome) && numeroMatricula == other.numeroMatricula;
	}
```

# Iteradores

Todos objetos descendentes de **Collections, **implementam a interface **Iterable** e por consequencia possuem um método chamado **iterator()** que devolve um objeto do tipo **Iterator<>() **

Este objeto permite a iteração em qualquer tipo de coleção.

```java
// Usando Iterator()
		Set<Aluno> alunos = javaColecoes.getAlunos();
		Iterator<Aluno> iterador = alunos.iterator();
		
		while(iterador.hasNext()) {
			Aluno proximo = iterador.next();
			System.out.println(proximo);
		}
```