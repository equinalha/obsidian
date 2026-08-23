---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2024-09-13T08:06:00
Owner:
  - Eduardo Quinalha
---
# O que é Java?

- Multi-plataforma
- Multi-paradigma
- Linguagem híbrida (compilado e interpretado)
- Compilação dinâmica

**Hotspot: **trechos de código do bytecode de uma aplicação que são executados com mais frequência. Neste caso, a JVM procede com o **JIT** (Just in Time) compilation, que trata-se de uma compilação diretamente para linguagem de máquina, poupando a JVM de fazer repetidas interpretações e ganhar desempenho.

> [!tip] 💡
> A JVM não roda Java! Ela roda bytecode

Atualmente, existem outras linguagens que compilam para bytecode e rodam também em cima da JVM:

- JavaScript
- Groovy
- Scala
- Ruby
- Kotlin

> [!note] 🔥
> **Pegadinha de concurso!****
**main() → Não é uma palavra reservada! Poderia ser qualquer nome para a classe principal.

# Temas que não vale a pena estudar*

- IO
- Threads
- Swing
- JavaFX
- Socket

## Tipos de dados

<!-- Column 1 -->
- Byte → 8bits
- short / char → 16 bits
- int → 4 bytes
- long → 8 bytes

> [!note] 🔥
> **Pegadinha!
**char em Java tem 16 bits pois é Unicode!


<!-- Column 2 -->
![[Untitled 773.png]]

# Passagem por valor vs Passagem por referência

> [!note] 🔥
> No java, toda passagem de parâmetros se dá por valor! Porém….

Em Java, todas as variáveis de objetos (isto é, não primitivas) são, na verdade, **referências a objetos**. Quando você passa uma variável de objeto como argumento para um método, está **passando a referência para o objeto, não o objeto em si.** Portanto, o método recebe uma cópia da referência, não uma cópia do objeto. Isso é o que causa confusão às vezes.
> No entanto, a passagem por valor em Java significa que o valor da referência (o endereço de memória para o objeto) é copiado para o parâmetro do método, não o próprio objeto. Portanto, **se você modificar o objeto dentro do método (por exemplo, alterar seus atributos), as alterações serão refletidas fora do método porque ambas as variáveis (a original e a cópia da referência) apontam para o mesmo objeto na memória.**
> 
> Por outro lado, **se você atribuir um novo objeto à variável dentro do método, isso não afetará a variável original fora do método, porque agora a variável local dentro do método aponta para um objeto diferente.**
> 
> Em resumo, em Java, os argumentos são passados por valor, mas para objetos, o "valor" que é passado é a referência ao objeto. Isso pode parecer semelhante à passagem por referência em outras linguagens, mas é importante entender que você está manipulando a referência ao objeto, não a própria referência.

# Orientação a Objeto

**Coesão:** A classe só faz o que está relacionado ao seu domínio
**Acoplamento:** O quanto uma classe é dependente de outra

# Strings

> [!note] 🔥
> **Pegadinha!**

```java
int idade = 12;
// Como primeiro tem uma string, por padrão o + passa a ser utilizado como concatenação
System.out.println("A idade é: " + idade + 1); // 121

// Aqui cabem as regras de precedência
System.out.println("A idade é: " + (idade + 1)); // 13

// Como primeiro tem uma operação aritmética, por padrão o + passa a ser utilizado como soma, depois concatenação
System.out.println(idade + 1 + " é a idade"); // 13
```

## Cast

O Java não permite cast entre int e String:

```java
// Não compila
		int value = 554;
		String var = (String)value;
		String temp = "123";
		int data = (int)temp;

// Compila
	  String var = Integer.toString(value);
		int data = Integer.parseInt(data);
```

# Operadores Lógicos

> [!tip] 💡
> **Qual a diferença entre &&, || e &, |?****

**O operador || analisa os dois operandos antes de retornar o resultado. O operador |, caso o primeiro operando seja True, já retorna True, dispensando a análise do segundo operando.
O mesmo vale para o &&

# Modificadores

Modificador Final:

- variável -> Constante
- método -> Não permite override
- classe -> Não permite herança

# Collections API

> [!note] 🔥
> Para percorrer um HashSet, ArrayList ou HashMap, pode-se usar o enhanced for, o qual consiste em um tipo, variavel, :  e o collection que ele vai analisar. 

for (String p : c) {System.out.println(p);}

[https://www.devmedia.com.br/java-collections-como-utilizar-collections/18450](https://www.devmedia.com.br/java-collections-como-utilizar-collections/18450)

<!-- Column 1 -->
![[Untitled 774.png]]

<!-- Column 2 -->
![[Untitled 775.png]]

Por padrão, listas em java são heterogêneas. Pode-se adicionar múltiplos tipos de dados em um mesmo ArrayList, porém isto é perigoso e pode causar exceções na execução do código. Para homogenizar a lista, usa-se os generics <>

```java
List<String> nomes = new ArrayList();
```

## List

- Elementos indexados
- Ordenados por ordem de inserção
- Aceita elementos repetidos
- Baixa performance para pesquisas
- Alta performance para inserção

## Set

```java
Set<String> nomes = new HashSet<>();
```

- **Não aceita elementos repetidos**
- Mais performático do que o list para pesquisas
- Baixa performance para inserção
- Não é indexado (os elementos não são acessíveis por índice)
- Você somente adiciona elementos no set, depois consulta se ele existe ou não
- **Tipos**
	- TreeSet:
		-  Armazena os elementos de forma ordenada
		- Árvores Rubro-Negra
		- Ordem natural ou por comparador personalizado
	- HashSet
		- Tabelas de dispersão
		- Não mantem ordenamento

## Map

- Agrupa dados de acordo com uma chave fornecida
- Não permite chaves duplicadas, mas chaves diferentes podem ter valores repetidos

```java
Map<String, List<Alluno>> mapaAlunosPorEstado = new HashMap<>();
mapaAlunosPorEstado.put("DF", Arrays.asList(new Aluno("Joao", "DF", 28, false)));
```

- **Tipos**
	- TreeMap
		- Estrutura de árvore balanceada
		- Árvore rubro negra
- Métodos
	- .values() → Retorna os elementos do set
	- .iterator() → Obtém um iterador que permite percorrer a lista, mesmo com modificações ocorrendo “online”
```java
List<Integer> numeros = new ArrayList<>();
numeros.add(1);
numeros.add(2);
numeros.add(3);

Iterator<Integer> iterator = numeros.iterator();
while (iterator.hasNext()) {
    int numero = iterator.next();
    if (numero % 2 == 0) {
        iterator.remove();
    }
}
```

<!-- Column 1 -->
![[Untitled 776.png]]


<!-- Column 2 -->
![[Untitled 777.png]]

## Queue

- Fila
- `add(element)`: Adds an element to the rear of the queue.
- `offer(element)`: Inserts an element into the queue **if it’s not full.**
- `remove()`: Removes the head of the queue.
- `poll()`: Removes and returns the head of the queue, or `null` if the queue is empty.
- `element()`: Returns the head of the queue.
- `peek()`: Returns the head of the queue without removing it.

## Deque

- Double Ended Queue
- Permite remoção e inserção pelas duas pontas da fila
- Permite acesso rápido e eficiente aos elementos

## Bags

## Records

# Java 8

[https://www.alura.com.br/artigos/o-minimo-que-voce-deve-saber-de-java-8](https://www.alura.com.br/artigos/o-minimo-que-voce-deve-saber-de-java-8)

## Date

Os itens mais cobrados são:

- LocalDate
- LocalTime
- LocalDateTime
- Duration.between()

## Interfaces

Agora as interfaces podem ter métodos concretos. São os default methods. Se a interface tiver todos os métodos default, a classe que irá implementar, não precisa sobrescrever estes métodos.

Também é possível a interface ter métodos privados e estáticos

> [!note] 🔥
> **O problema da ambiguidade:**

- Suponha uma interface A com o default method ola();
- Agora suponha duas novas interfaces, B e C, ambas implementando a interface A e sobrescrevendo o método ola();
- Por último, uma classe D, implementando as duas interfaces B e C;

Este código não compila! É gerada uma ambiguidade pois o compilador não pode decidir qual método será referenciado quando for chamado D.ola().

[https://www.devmedia.com.br/metodos-default-no-java/33012](https://www.devmedia.com.br/metodos-default-no-java/33012)

# Exceções (Assunto muito cobrado)

Tanto RuntimeException quanto Exception herdam de Throwable

Em um bloco Try/Catch com múltiplos catch, as exceções devem obrigatoriamente ser da mais específica para a mais genérica ou o código nem compila.

```java
// Não compila
		int x = 10;
		int y = 2;
		try {
			for (int z = 2; z >=0; z--) {
				int ans = x/z;
				System.out.print(ans + " ");
			}
		} catch (Exception e) {
			System.out.println("E1");
		} catch (ArithmeticException e2) {
			System.out.println("E2");
		}

// Compila
		int x = 10;
		int y = 2;
		try {
			for (int z = 2; z >=0; z--) {
				int ans = x/z;
				System.out.print(ans + " ");
			}
		} catch (ArithmeticException e2) {
			System.out.println("E1");
		} catch (Exception e) {
			System.out.println("E2");
		}
```

## Unchecked

São herdeiras da superclasse **RuntimeException **e não são verificadas pelo compilador, ou seja, não é obrigatório o tratamento da exceção

## Checked

São herdeiras de **Exception** e são verificadas pelo compilador. O tratamento destas exceções é obrigatório.

![[Untitled 778.png]]

# Outros conceitos

- JMX
	- Em resumo, o JMX é uma tecnologia Java que permite monitorar e gerenciar recursos Java em tempo de execução, fornecendo uma interface padronizada para gerenciamento de aplicativos Java.
	- Com JMX, é possível monitorar e gerenciar vários aspectos do aplicativo Java, como memória, threads, carga de trabalho, tempo de resposta, consumo de CPU e muito mais.

<!-- Failed to import synced block: Could not find block with ID: 2fe2bb33-a9ab-4490-89d6-c17fe28abbf9. Make sure the relevant pages and databases are shared with your integration "Obsidian". -->

PuProDePri

# Generics

- Utilizado pelo compilador para auxiliar o programador a não recorrer em erro type cast
- <?> → Cast genérico, atende a qualquer tipo de objeto
- Não suporta herança diretamente
- Pode ser utilizado tanto em classes comuns quanto estáticas

> [!tip] 💡
> Obs: 
Em classes o generics vai na declaração, **após o nome da classe. **
Em métodos, vai na declaração, **antes do tipo de retorno.**

```java
Set<Object> setOfObjects = new HashSet<String>(); //Erro de compilação
```

- Uma forma de trabalhar com herança é pela extensão.
	- Também conhecido como **Wildcard Limitado ou Bounded Type Parameter**

```java
Set<? extends Number> setDeNumbers = new HashSet<Integer>();
setDeNumbers = new HashSet<Float>();
setDeNumbers = new HashSet<String>(); // Erro de compilação. String não herda de Numbers
// A mesma lógica vale para <? super classe>

// Existem dois tipos: Upper Bounded Type Parameter e Lower Bounded Type Parameter

// Upper Bounded Type Parameters -> Restringir pela superior
public class Exemplo<T extends Number> {
    // Implementação da classe
		// T deve ser uma subclasse de Number ou implementar a interface Number.
}

// Lower Bounded Type Parameter -> Restringir pela inferior
public void exemplo(List<? super Integer> lista) {
    // Implementação do método
		// T deve ser uma superclasse de Integer ou a própria classe Integer
}
```

- Com generics não é mais necessário fazer type cast em operações que ele esteja envolvido. O cast é automático
- Não pode ser aplicado sobre tipos primitivos
- Operador “Diamond” <>:
	- Criado para reduzir redundância de código
	- O compilador utiliza a informação do generics na declaração da variável para inferir os tipos que iriam no generics da instanciação com o operador new
```java
Map<String, Set<Integer>> contacts = new HashMap<>();

// Equivale a:
Map<String, Set<Integer>> contacts = new HashMap<String, Set<Integer>>();
```
- **Tipo parametrizado**
	- Também conhecido como tipo genérico
	- É uma forma de criar classes, interfaces ou métodos que trabalham com tipo de dados genéricos
```java
//Exemplo
public class Lista<T> { // T define um tipo genérico
    private List<T> elementos;

    public Lista() {
        elementos = new ArrayList<>();
    }

    public void adicionar(T elemento) {
        elementos.add(elemento);
    }


public static void main(String[] args) {
        Lista<String> listaDeStrings = new Lista<>();
        listaDeStrings.adicionar("Exemplo 1");
        listaDeStrings.adicionar("Exemplo 2");
        listaDeStrings.adicionar("Exemplo 3");

        // Acessando os elementos da lista
        for (String elemento : listaDeStrings.getElementos()) {
            System.out.println(elemento);
        }
    }
```
- Erasure
	- O "erasure" é um mecanismo que preserva a compatibilidade com código legado, removendo as informações de tipos genéricos em tempo de compilação e substituindo-as por castings (conversões de tipos). Isso permite que o código genérico seja compilado em bytecode Java que é compatível com versões mais antigas da JVM e não afete a execução de códigos não genéricos preexistentes.

# Stream API

- O método Stream(), introduzido no Java 8, permite que todas as coleções possam ser fontes de dados para streams
- Adiciona o paradigma funcional na linguagem
- Possibilita o uso de paralelismo
- reduce()

```java
// Uso:
.reduce([acumulador/valor inicial], [lambda da operação])
// Na expressão lambda, são fornecidos dois argumentos, sendo o primeiro o próprio acumulador e o segundo o elemento atual do stream

// Exemplos:
.reduce(0, (x, y) -> x + y)
.reduce(0, (x, y) -> Integer::sum)
.reduce(1, (x, y) -> x * y)
```

- Existem métodos específicos para operações como soma, média, etc. Porém, eles só se aplicam apenas em streams de tipos primitivos, como `**IntStream**`, `**LongStream**` e `**DoubleStream**`.

```java
int sum = numbers.stream().filter(n -> n % 2 == 0).sum()
```

- sorted()

```java
// Utilizado para ordenar os elementos em um fluxo da Stram API de acordo com uma função fornecida ou com sua ordem natural.
// Exemplos:
List<String> strings = Arrays.asList("c", "a", "b");
List<String> sortedList = strings.stream()
                                .sorted()
                                .collect(Collectors.toList());

System.out.println(sortedList); // Saída: [a, b, c]

// Cuidado para não confundir com o método sort()!
// O método sort está disponível somente na classe List e é utilizado para ordenar os elementos no local, ou seja, ele modifica os elementos 
// dentro da própria lista

// Exemplo utilizando função de ordenamento
List<String> strings = Arrays.asList("apple", "banana", "cherry", "date");

// Ordenação em ordem decrescente de comprimento das strings
List<String> sortedList = strings.stream()
        .sorted(Comparator.comparingInt(String::length).reversed())
        .collect(Collectors.toList());

System.out.println(sortedList); // Output: [banana, cherry, apple, date]
```

- Concatenação de strings

```java
List<String> words = Arrays.asList("hello", "world", "java", "programming");
String result = words.stream().collect(Collectors.joining(""));
```

- Métodos genéricos
	- Uma forma de declarar um método que opera sobre um tipo de dado genérico
```java
public <T> void meuMetodo(T parametro) {
    // Implementação do método
}
```
![[image_2270efac-1069-4483-a37d-168bc9221c0720220715_095108.jpg]]

# Annotations

- São estruturas de dados utilizadas para armazenar metadados em tempo de execução
- também podem ser consideradas blocos de código executáveis em tempo de compilação.
	- geração automática de código,
	- validação de estruturas de dados,
	- geração de documentação ou relatórios
- são processadas em tempo de compilação ou em tempo de execução.
- são declaradas utilizando a palavra-chave `**@interface**`
	- A sintaxe completa para a declaração de uma annotation é semelhante à declaração de uma interface, pois uma annotation é uma forma especial de interface.
```java
public @interface MinhaAnnotation {
    // Elementos e definições da annotation
}
```
	- podem ter restrições adicionais em seus elementos, como serem obrigatórios ou permitirem apenas determinados tipos de valores.
	- `**@Retention**`
		- Retenção da annotation em tempo de execução:
			- `**RetentionPolicy.SOURCE**`: A annotation é descartada pelo compilador e não é incluída no bytecode.
			- `**RetentionPolicy.CLASS**`: A annotation é mantida no bytecode, mas não é acessível em tempo de execução.
			- `**RetentionPolicy.RUNTIME**`: A annotation é mantida no bytecode e pode ser acessada e processada em tempo de execução.
	- `**@Target**` 
		- Define os tipos de elementos de programa a que uma annotation pode ser aplicada
	- `**@Documented**`
		- Permite a inclusão na documentação automaticamente
- podem ser lidas e interpretadas por ferramentas de desenvolvimento, frameworks e bibliotecas.
- Para acessar informaçães de uma annotation em tempo de execução, usa-se o método **Annotation.getAnnotation()**

# Reflect

- **java.lang.reflect**
- Permite fazer operações sobre classes como:
	- Obter informações sobre métodos, campos, interfaces implementadas, anotações, etc.
	- Instanciamento de objetos
	- Acesso e modificação de campos e métodos
	- Invocação de métodos em tempo de execução
	- Criação dinâmica de classes e objetos

## Reflexão

Possibilita o instanciamento de classes arbitrárias em tempo de execução

```java
Class.forName("java.lang.String").newInstance().
```

# Funções Lambda

- Uma expressão lambda é uma função anônima que pode ser tratada como um valor e passada como argumento para métodos ou atribuída a variáveis.
- Permitir a passagem de comportamentos como argumentos de métodos.

```java
(parameters) -> { statements }
```

- Se `parameters` ou `statements` tiver apenas 1 argumento, os parênteses` () `ou chaves `{} `poderão ser omitidos
- Na prática, funções lambda são definidas por interfaces funcionais genéricas, com apenas um método abstrato cada. O compilador vai inferir o tipo do retorno e argumentos a partir da assinatura do método
	- a interface funcional `**Predicate**` é uma das mais comumente usadas ao trabalhar com expressões lambda.
	- Representa uma função que recebe um argumento e retorna um booleano
```java
Predicate<Tipo> predicate = (parâmetros) -> {
    // código da expressão lambda
    return resultado;
};
```
- Variáveis externas podem ser capturadas por meio da interface `final`

```java
int x = 10;
final int y = 20;

Runnable r = () -> {
    System.out.println(x);  // Captura a variável 'x'
    System.out.println(y);  // Captura a variável 'y'
};

/*
A variável 'x' é uma variável local e a variável 'y' é final. 
Ambas podem ser acessadas dentro do corpo da expressão lambda, 
mesmo que a expressão lambda seja definida fora do escopo onde 
as variáveis foram declaradas.

No entanto, se tentarmos modificar a variável 'x' após a captura, 
ocorrerá um erro de compilação, pois ela não é final ou efetivamente 
final.
*/
```

# Date & Time

- **LocalDateTime**
	- Utilizada para representar uma data e hora específica sem considerar o fuso horário
	- Combinação de `LocalDate()` com `LocalTime()`
```java
// Obtendo a data e hora atual
LocalDateTime dataHoraAtual = LocalDateTime.now();
System.out.println("Data e hora atual: " + dataHoraAtual);

// Criando uma data e hora específica
LocalDateTime dataHoraEspecifica = LocalDateTime.of(2022, 6, 15, 10, 30);
System.out.println("Data e hora específica: " + dataHoraEspecifica);
```
	- Também permite realizar operações de adição ou subtração de dias, horas, minutos, etc.
```java
LocalDateTime dataHoraAtual = LocalDateTime.now();
LocalDateTime dataHoraFutura = dataHoraAtual.plusDays(7).plusHours(2);
System.out.println("Data e hora futura: " + dataHoraFutura);
```
- Java 8
	- No Java 8 foi introduzida uma nova classe para trabalhar com datas, a `java.time`, em substituição à `java.util.Date` e `java.util.Calendar`
	- Representação de datas e horas:
		- `**LocalDate**`: Representa uma data, sem levar em conta a hora do dia.
		- `**LocalTime**`: Representa um horário, sem levar em conta a data.
		- `**LocalDateTime**`: Representa uma data e hora combinadas.
	- `**DateTimeFormatter**` permite formatar objetos de data em strings com um padrão específico e analisar strings em objetos de data.
	- Cálculos de duração e período:
		- A classe `**Duration**` representa uma quantidade de tempo em termos de horas, minutos, segundos e nanossegundos.
		- A classe `**Period**` representa uma quantidade de tempo em termos de anos, meses e dias.

# Threads

No Java, o método `**start()**`** **é usado para *iniciar uma nova thread*. Este método chama automaticamente o método `**run()**` que contém as instruções a serem executadas pela thread. As threads são usadas para executar tarefas simultaneamente, permitindo que partes do seu programa sejam executadas de forma assíncrona.

Para usar o método** **`**start()**`, ***você precisa criar uma classe que estenda a classe ***`***Thread ***`***ou implemente a interface ***`***Runnable***`. Aqui estão dois exemplos de como usar o método `start()` com ambas as abordagens:

Exemplo usando uma classe que estende a **classe Thread**:

```java
public class MinhaThread extends Thread {

  public void run() {

    // Código a ser executado em uma nova thread

    System.out.println("Minha thread está sendo executada.");

  }

  public static void main(String[] args) {

    MinhaThread minhaThread = new MinhaThread();

    minhaThread.start(); // Inicia a nova thread

  }

}
```

Exemplo usando uma classe que implementa a **interface Runnable:**

```java
public class MinhaRunnable Runnable {

  public void run() {

    // Código a ser executado em uma nova thread

    System.out.println("Minha thread está sendo executada.");

  }

  public static void main(String[] args) {

    MinhaRunnable minhaRunnable = new MinhaRunnable();

    Thread thread = new Thread(minhaRunnable);

    thread.start(); // Inicia a nova thread

  }

}
```

# Garbage Collection

## Ciclo de vida dos objetos

Sete estados

1. **Criado (Created)**
2. **Em Uso (In use)**
3. **Invisível (Invisible)**
4. **Inalcançável (Unreachable)**
5. **Coletado (Collected)**
6. **Finalizado (Finalized)**
7. **Desalocado (Deallocated)**

# Manipulação de Strings em Java

```java
String s1 = "Teste";
String s2 = "Teste";
String s3 = new String("Teste");

System.out.println(s1==s2); //true
System.out.println(s1==s3); //false
System.out.println(s2==s3); //false
System.out.println(s1.equals(s3)); //true
System.out.println(s1.equals(s2)); //true
System.out.println(s2.equals(s3)); //true
```

![[Untitled 779.png]]

> [!note] 🔥
> Strings são imutáveis!
StringBuilder são mutáveis

## Métodos importantes

- `indexOf(int str, int fromIndex)`: Retorna o índice da **primeira ocorrência,** 0 se nenhuma string for passada ou -1 se não localizado
- `toCharArray()`: Cria um vetor de caracteres contendo a string
- `substring()`: Retorna uma nova string a partir de um “pedaço” da string original
- `split()`
- `compareTo()`
- `strip()`
- `contains()`
- `isEmpty()`
- `join()`
- `repeat()`
- `startsWith()/endsWith()`
- `toLowerCase()/toUpperCase()`
- `ident()`
