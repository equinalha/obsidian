---

---
# Java.lang

## String()

Strings são imutáveis. Se for necessário alterar algo na string, deve-se criar uma nova.

Se o objeto for reatribuído, na prática consome-se memória desnecessariamente, uma vez que somente a referencia é alterada e o objeto anterior permanece “perdido” na memória.

```java
String texto = "Socorram";
texto = texto.concat("-");
texto = texto.concat("me");
texto = texto.concat(", ");
texto = texto.concat("subi ");
texto = texto.concat("no ");
texto = texto.concat("ônibus ");
texto = texto.concat("em ");
texto = texto.concat("Marrocos");
System.out.println(texto);
```

Uma forma de trabalhar com Strings mutáveis é através da classe StringBuilder, a qual constrói strings que são mutáveis

```java
StringBuilder builder = new StringBuilder("Socorram");
builder.append("-");
builder.append("me");
builder.append(", ");
builder.append("subi ");
builder.append("no ");
builder.append("ônibus ");
builder.append("em ");
builder.append("Marrocos");
String texto = builder.toString();
System.out.println(texto);
```

Ambas são interfaces da classe **CharSequence**

## Classe Object

> [!tip] 💡
> É a classe mais alta na hierarquia.
Implicitamente, toda classe herda os comportamentos da classe Object.
Muitos de seus métodos podem (e devem) ser reescritos, por exemplo o método toString().

Quando utilizamos o System.out.println() (classe System, biblioteca java.lang), é automaticamente utilizado o método toString() da classe (se estiver disponível) ou a implementação básica disponível na classe Object.

## Arrays

- Em java, **arrays** são objetos
- **Arrays** tem tamanho fixo

```java
int[] idades = new int[5]; // válido
int idades[] = new int[5]; // válido também
int[] refs = {1,2,3,4,5}; // Forma literal, utiliza-se chaves, não precisa do new
```

# Java.util

## Arraylists

```java
// <> chamam-se generics
		ArrayList<Conta> lista = new ArrayList<Conta>();
```

```java
// Versão clássica de se interar em listas
		for(int i = 0; i < lista.size(); i++) {
			System.out.println(lista.get(i));
		}
		
		// Versão moderna
		for(Conta conta : lista) {
			System.out.println(conta);
		}
```

O método contains() do Arraylist usa (por baixo dos panos) o método equals() que é herdado da classe Object. Na prática, isto significa que, caso não tenha sido sobrescrito, a comparação será feita em cima da referência somente. Assim dois objetos com os mesmos valores de atributos retornaram falso para o equals() e consequentemente o método contains() irá retornar falso também.

Para solucionar isto, basta sobrescrever o método equals()

```java
@Override
    public boolean equals(Object obj) {
    	Conta cc = (Conta)obj;
    	
    	if(cc.getAgencia() != this.agencia)
    		return false;
    	if(cc.getNumero() != this.numero)
    		return false;
    	
    	return true;
    }
```

## LinkedList

Trata-se de uma lista duplamente encadeada

![[SubPages/Pessoal/images/Untitled 117.png]]

As classes *ArrayList* e *LinkedList* compartilham os mesmos métodos. Isto porquê ambas são implementações da interface List da classe java.util

![[SubPages/Pessoal/images/Untitled 118.png]]

## Vector

Normalmente a execução de uma aplicação Java se dá em apenas uma pilha, que começa com o método **main**. Porém é possível operar com n pilhas, conforme desejado.

A única estrutura de dados que pode ser acessada simultaneamente por mais de uma pilha é o **Vector**

As classes derivadas de **list** permitem dados duplicados e possuem dados sequenciados.

As classes derivadas de **set** possuem regras quanto a duplicação de dados

![[SubPages/Pessoal/images/Untitled 119.png]]

## Autoboxing / unboxing

Para cada tipo primitivo no java existe uma classe que o representa. Isto possibilita a interação por exemplo com collections. As classes que representam tipos primitivos chamam-se **wrapper**.

## Ordenação de Listas

O java dispõe de alguns métodos prontos para ordenação de lista

### Método sort da classe List

Este método está disponível na classe **List** e recebe como parâmetro um objeto da interface **Comparator:**

```java
// Chamada do método sort
lista.sort(new NumeroDaContaComparator());

// Implementação da interface Comparator
class NumeroDaContaComparator implements Comparator<Conta>{

	@Override
	public int compare(Conta c1, Conta c2) {
		return Integer.compare(c1.getNumero(), c2.getNumero());
	}	
}
```

Os valores de retorno do comparator são:

- **Negativo:** O primeiro objeto vem antes do segundo na lista;
- **Zero:** Os dois tem mesmo peso;
- **Positivo:** O segundo objeto vem antes na fila;

### Método sort da classe Collections

A classe **Collections **disponibiliza métodos estáticos para cumprir algumas tarefas, tais como ordenação. Por serem métodos estáticos, não considera-se esta uma solução orientada a objeto, mas pode ser utilizada sem problemas.

Para que o método funcione, a classe (que será ordenada) deverá implementar a interface **comparable** e sobrescrever o método **compareTo()** desta interface. Chama-se isto de ordenação natural.

```java
// Declaração da classe
public abstract class Conta implements Comparable<Conta> {
// (...)

// Método compareTo() da interface Comparable
@Override
	 public int compareTo(Conta outra) {
		 
		 return Double.compare(this.saldo, outra.getSaldo());
	 }
```
