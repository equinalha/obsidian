---

---
# var

No java é possível declarar uma variável como sendo do tipo **var, ** um tipo genérico que na prática vai definir o tipo da variável conforme a inicialização.

Não pode ser utilizada para atributos de classes

É obrigatório a inicialização na mesma linha

```java
var carros = new ArrayList<Carro>();
var nome = "Orientação à Objetos";

//São equivalentes à:

ArrayList<Carro> carros = new ArrayList<>();

String nome = "Orientação à objetos";
```

## Código Estático

Assim como numa classe, atributos estáticos permanecem nela, é possível criar um bloco de código estático dentro da classe

Este bloco será executado assim que a VM carregar a classe.

```sql
public class Teste {
	private static String nome;

	static {
		nome = "Teste";
	}	

}
```

---

```java
// Estrutura:
// Packages -> Pastas, containeres ou namespaces para classes que tenham algo em comum
// EntryPoint -> Classe especificada na criação do projeto. Deve conter o método main

java NomeDaClasse // Invoca a JVM e obrigatoriamente deve-se passar uma classe como parâmetro. Sendo assim, não se especifica a extensão .class
javac NomeDoArquivo.java // Invoca o compilador. Deve-se especificar um arquivo de código fonte com a extensão .java

// Variáveis:
// int: negativos e positivos, pode-se utilizar _ para melhorar a leitura. Ex: 10_000
// Caso não sejam inicializadas:
// int -> 0
// double -> 0.0
// string -> null
// booolean -> false

// Constantes:
// atribuídas pela instrução "final"
final double pi = 3.1415;

// Operador ternário
z = (y > x) ? x : y;

// Enhanced loops
String [] names = {"Bob", "Mike", "Jack"};

for(String name: names){
	System.out.println(name);
}

// modificador static
// Uma variável ou método definidos como static pertence à classe, e não aos objetos instanciados a partir da mesma
// Seu valor é compartilhado entre todos os objetos instanciados a partir daquela classe
// Pode ser acessado mesmo sem inicializar (instanciar - new)
// Métodos declarados como estáticos somente têm acesso aos valores das variáveis da classe. Não conhecem e nem têm
// acesso aos valores instanciados a partir da classe

// Exceptions
// Quando ocorrem, quebram o fluxo normal do código. Se não houver um bloco try/catch, Ocorrerá uma exceção (trhow()), e
// o fluxo será redirecionado da linha onde efetivamente ocorreu para o final do bloco principal do programa (main(), por exemplo)
// O try/catch pode ser usado da seguinte forma:

try {
	Clothing[] items = new Clothing[10];
	items[0].description = "Blue T-Shirt";
} catch (NullPointerException e){                   // Tratamento somente de exceção do tipo NullPointerException
	String errMessage = e.getMessage();
	e.printStackTrace();
} catch (Exception e) { ... }                       // Tratamento de qualquer outro tipo de exceção que possa ocorrer

// Herança
// Superclasse
public Class Clothing {
	private double price;
	public double getPrice() {
		return price;
	}
}

// Classes herdeiras
public Class Tailored extends Clothing {
	private double fee;
	@Override
	public double getPrice(){                     // sobresreve o método da superclasse, personalizado para este tipo de objeto
		return super.getPrice()+fee;
	}
}

public Class Standard extends Clothing{               // Não sobrescreve nenhum método, apenas herda os da superclasse
}

// Polimorfismo
Clothing [] items = new Clothing[2];
item[0] = new Tailored();
item[1] = new Standard();
for (Clothing item: items){
	item.getPrice();
}

// Classes e métodos abstratos
abstract Class Clothing(){
	public abstract double refund();
}

// Uma classe abstrata não pode ser instanciada diretamente pelo operador new
// A subclasse deverá obrigatoriamente implementar todos os metodos abstratos da superclasse,
// atraves da annotation @Override

// Os objetos podem ser declarados como sendo do tipo da superclasse, instanciando uma subclasse
Clothing item1 = new Tailored();

// o método .toString() é um exemplo de método da classe Object (superclasse de todos os objetos em Java)
// que pode ser sobrescrito pela annotation @Override.
// Este método é automaticamente chamado quando usamos o System.out.println(objeto)

// Interfaces
// Trata-se de uma forma de implementar comportamentos semelhantes em classes que não tenham a mesma hierarquia (heranças)
// Não podem ser instanciadas
// Os métodos de instância são por padrão public abstract
// não pode haver variáveis
// Uma classe pode implementar quantas interfaces forem necessárias, simultaneamente

// Exemplo:
// <https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/lang/Comparable.html>

public class Clothing implements Comparable<Clothing>{

    // ...

    @Override
    public int compareTo(Clothing c) {
        return this.description.compareTo(c.description);
    }

}

```