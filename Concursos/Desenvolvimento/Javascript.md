---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2024-10-01T17:16:00
Owner:
  - Eduardo Quinalha
---
[[✨ Different ways to create Objects in Javascript✨]]

[[Spread and Rest Operators in JavaScript]]

# Javascript

> [!note] 🔥
> ECMA Script é a especificação implementada pelo Javascript, dentre algumas outras.
Ao invés de usar as versões, visto que novas versões são quase anuais, adotou-se a nomenclatura ES.Next

> [!note] 🔥
> O **var** se usado dentro de uma função, passa a ser local
var por default é global

> [!note] 🔥
> Objetos em javascript são mutáveis, ou seja, mesmo depois de instanciado por uma classe, pode-se incluir novos métodos e atributos

> [!tip] 💡
> Em JavaScript, funções são consideradas objetos especiais, o que significa que elas possuem todas as características dos objetos normais em JavaScript, como a capacidade de serem armazenadas em variáveis, passadas como argumentos para outras funções e retornadas como valores de outras funções.
> Uma das principais diferenças entre funções e outros tipos de objetos em JavaScript é que as funções podem ser invocadas, o que significa que elas podem ser executadas como um bloco de código. Além disso, funções em JavaScript também podem ter propriedades e métodos, assim como objetos comuns.
> 
> Ao criar uma função em JavaScript, você está criando um objeto do tipo função. Isso significa que você pode atribuir propriedades e métodos a essa função, assim como faria com qualquer outro objeto. Por exemplo, você pode adicionar uma propriedade a uma função que armazena uma mensagem ou algum tipo de informação adicional.
> 
> Em resumo, funções em JavaScript são objetos especiais que possuem a capacidade de serem invocadas e de terem propriedades e métodos, tornando-as muito flexíveis e poderosas na linguagem.

<!-- Column 1 -->
## Escopo

<!-- Column 2 -->
## Atualização de variáveis

<!-- Column 1 -->
| **identificador** | **Escopo** |
| --- | --- |
| **var** | Window (global)<br>Local somente se declarado dentro de uma função |
| **let** | Por bloco |
| **const** | Por bloco |

<!-- Column 2 -->
| **identificador** | **Escopo** |
| --- | --- |
| **var** | Sim |
| **let** | Sim |
| **const** | Não |

## Redefinição de variáveis

| **identificador** | **Escopo** |
| --- | --- |
| **var** | Sim |
| **let** | Não |
| **const** | Não |

```javascript
// Analise estas situações:
// 1- --------------------------------
console.log(teste); // Erro: teste is not defined

// 2- --------------------------------
var teste;
console.log(teste); // undefined.

// 3- --------------------------------
console.log(teste); // undefined.
var teste;

// Este código não dá erro, pois o Javascript faz o hoisting (joga as declarações de variáveis para o início do arquivo)
// Atenção, somente a declaração. As atribuições continuam no lugar original

// 4- -------------------------------
var teste = "teste";
console.log(teste); // teste

// 5- -------------------------------
console.log(teste); // undefined.
teste = "teste"
```

## Classes

```javascript
class Aluno {
	constructor(id, nome, email) {
		this.id = id;
		this.nome = nome;
		this.email = email;
	}
}
```

## Métodos getters e setters

```javascript
get id(){
	return this._id;
}

get nome(){
	return this._nome;
}

// isso possibilita:
console.log(aluno.id) // Ele chama o "get id()" por baixo dos panos

set nome(novoNome) {
	 this._nome = novoNome;
}

// isso possibilita
aluno.nome = "Novo Nome";
```

## for … in / for … of

- **for … in**
	- Interação sobre as chaves em um objeto
		- objeto[chave]
	- Elementos de um array (sem ordem garantida)
- **for … of**
	- Iteração sobre elementos de um objeto iterável:
		- Array
		- String
		- Maps

## fetch()

Obtém um objeto do servidor, async. Substitui o XMLHttpRequest()

## Symbol()

Define um identificador único, oculto, que não pode ser acessado acidentalmente.

```javascript
let id = Symbol('id');
person[id] = 140353;
// Now person[id] = 140353
// but person.id is still undefined
```

## Promises

```javascript
// Criando uma Promise

// O Objeto Promise recebe como parâmetro duas funções, que vão ser especificadas no momento da chamada (then ou catch). Aqui vai apenas uma
// referencia do tipo, vai existir esta função res e rej
myPromise = new Promise((res, rej) => {
	faz_alguma_coisa
	if(deu_bom) {
		res(parametro)
	} else {
		rej(parametro)
	}
}

// Usando a Promise
// Como foi chamado o método then, aqui está se definindo a função res. Para a chamada anterior, então ela vai ser chamada com val = parametro
// O mesmo vale para catch
myPromise.then( val => {
		console.log(val)
	}
)
```

## O operador opcional de encadeamento de propriedade (`**?.**`)

- Usado para evitar erro de referência quando uma propriedade não está definida

```javascript
x = {}; // Cria um objeto vazio e atribui à variável 'x'
firstName = x.name?.first; // Não causa exceção ao acessar a propriedade não definida, porém o valor de firstName será undefined
```

# Objetos

Com exceção dos tipos primitivos, tudo em javascript é objeto

## Criando um objeto

- Literal
```javascript
const person = {
firstName: "John",
lastName: "Doe",
age: 50,
eyeColor: "blue"
};
```
- Usando operador `new`
```javascript
const person = new Object();
person.firstName = "John";
person.lastName = "Doe";
person.age = 50;
person.eyeColor = "blue";
```
- Definindo um construtor
- Usando `Object.create()`

## Prototype

- Equivalente a `super`
- É a classe superior, da qual o objeto herda as propriedades
- O operador `delete `não exclui propriedades herdadas

## This

- Pode se referir a diferentes objetos, dependendo de como é invocado
	- Em um objeto, refere-se a ele próprio
	- Sozinho, refere-se ao objeto global (window no caso de um navegador)
	- Em uma função em modo estrito, é `undefined`
	- Em um evento, refere-se ao elemento que recebeu este evento

## call(), apply() e bind()

- Permite aplicar um método utilizando propriedades de outro objeto

```javascript
const person = {
  fullName: function() {
    return this.firstName + " " + this.lastName;
  }
}
const person1 = {
  firstName:"John",
  lastName: "Doe"
}

// This will return "John Doe":
person.fullName.call(person1);
```

```javascript
const person = {
  fullName: function() {
    return this.firstName + " " + this.lastName;
  }
}

const person1 = {
  firstName: "Mary",
  lastName: "Doe"
}

// This will return "Mary Doe":
person.fullName.apply(person1);
```

- Quando utilizar argumentos, `call()` recebe estes separadamente enquanto `apply()` recebe através de um array

```javascript
const person = {
  fullName: function(city, country) {
    return this.firstName + " " + this.lastName + "," + city + "," + country;
  }
}

const person1 = {
  firstName:"John",
  lastName: "Doe"
}

person.fullName.apply(person1, ["Oslo", "Norway"]);
person.fullName.call(person1, "Oslo", "Norway");
```

- `bind() `é utilizado quando deseja-se preservar o `this` isto é útil, por exemplo, em funções de callback

## Construtores e Prototype

- Funcionam exatamente como uma função, porém toda vez que for criado um objeto, pelo operador `new `irá criar uma nova instância, seguindo o construtor como molde

```javascript
function Person(firstName, lastName, age, eyeColor) {
  this.firstName = firstName; 
  this.lastName = lastName;
  this.age = age;
  this.eyeColor = eyeColor;
  this.changeName = function (name) {
    this.lastName = name;
  };
}
const myFather = new Person("John", "Doe", 50, "blue");
const myMother = new Person("Sally", "Rally", 48, "green");
```

- Por convenção, utiliza-se a primeira letra maiúscula
- Não é possível adicionar uma nova propriedade para um construtor

```javascript
Person.nationality = "English";
```

- Para isso, é necessário utilizar `prototype`

```javascript
Person.prototype.nationality = "English";

Person.prototype.name = function() {
  return this.firstName + " " + this.lastName;
};
```

# Array

- Criando um novo array de 5 posições

```javascript
let cores = Array(5);
```

- 

# DOM

- Trata-se de uma árvore de objetos

![[Untitled 433.png]]

- Por Javascript é possível alterar: 
	- todos os elementos html da página
	- todos os atributos html
	- todos os estilos css
	- remover/adicionar elementos e atributos
	- reagir a todos os eventos html da página
	- criar novos eventos html
- Todos os elementos html são definidos como objetos
- Métodos para encontrar elementos dentro do DOM
```javascript
document.getElementById("id")
document.getElementsByTagName("p")
document.getElementsByClassName("classe")
document.querySelectorAll("p.intro") // Usa seletores do CSS

// Outros que retornam arrays de elementos correspondentes
document.anchors
document.body
document.documentElement
document.embeds
document.forms
document.head
document.images
document.links
document.scripts
document.title
```

# Generators

- São funções que podem ser pausadas e retomadas.
- são definidos pela função* (asterisco) e a palavra-chave **yield**

```javascript
function* myCounter(){
    var i = 0;
    while(true){
        yield i++;
    }
}

var counter = myCounter();
```

- O `*` denota que a função é um generator
- `yield` funciona como o `return`, no entanto, logo após retornar o valor ele pausa a função
- Note que eu disse que a função foi pausada, e não finalizada.
- O retorno da função, no entanto, não é o valor diretamente retornado por `yield`
- O retorno será um objeto que, dentre suas propriedades, poderá informar o valor e se o generator foi finalizado

```javascript
var counterValue = counter.next();
```

## Podem existir vários yields

```javascript
function* myGenerator(){
    yield 5;
    console.log("we’re back!");
    yield 10;
}
```

- Ao executar o Generator, a função irá parar no primeiro `yield`. 
- Ao executar `next()` pela primeira vez, obteremos o valor 5. 
- Ao executar `next()` pela segunda vez, a mensagem “we’re back!” será impressa e receberemos o valor 10.

## Lista de retornos

```javascript
function* myGenerator1(){
    yield [1,2,3,4,5];
}

function* myGenerator2(){
    yield* [1,2,3,4,5];
}
```

- No `myGenerator1`, ao executar o `next()` receberemos um array. 
- Mas no `myGenerator2`, receberemos primeiro o 1, depois o 2, depois o 3, etc, conforme formos executando o `next()`. 
- Para esse comportamento, basta colocar o `*` junto ao comando `yield`.

# Export e Import

## Named Exports

- Variáveis são exportadas individualmente

```javascript
// in-line
export const name = "Jesse"
export const age = 40

// Botton
const name = "Jesse"
const age = 40

export { name, age }
```

## Default Exports

- É permitido apenas um `default export` por módulo

```javascript
const message = () => {
  const name = "Jesse";
  const age = 40;
  return name + ' is ' + age + 'years old.';
};

export default message;
```

## Import

- Existem duas sintaxes possíveis a serem utilizadas dependendo do tipo de export do módulo

```javascript
// Named exports
import { name, age } from "./person.js";

// Default export
import message from "./message.js";
```
