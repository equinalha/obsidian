---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2024-11-12T07:41:00
Owner:
  - Eduardo Quinalha
---
[http://epweb2.ph.bham.ac.uk/user/bracinik/Joeal/Galowicz_STL_cookbook.pdf](http://epweb2.ph.bham.ac.uk/user/bracinik/Joeal/Galowicz_STL_cookbook.pdf)

> [!tip] 💡
> **Cálculo de range de armazenamento de variável:
de **==- [ 2 ^ (b - 1) ]== **a **==[ 2 ^ (b - 1)] - 1==

Onde b = numero de bits

# Lógica de Programação

## Tipagem

**Dinâmica:** O tipo da variável é definido na inicialização da mesma **Tempo de Execução**. Não é necessário definir o tipo na declaração (ex. JavaScript)
**Estática: **O tipo da variável é definido na declaração **Tempo de Compilação**.
**Forte: **A variável não pode mudar de tipo
**Fraca: O cast de tipos de variáveis é implícito (você pode multiplicar 2 * ‘2’ e obter o resultado 4)**

> [!tip] 💡
> Java é estaticamente tipada e fortemente tipada, porém pode-se converter o tipo de dado usando cast **explícito**

```javascript
i = 10
j = '10'

i == j // true
i === j // false
```

## Passagem por valor ou referência

> [!tip] 💡
> Ao fornecer no parâmetro da função um tipo primitivo, esta será sempre uma passagem por valor (não altera o valor da variável após a execução)

Já ao fornecer um objeto, a passagem se dá sempre por referência, neste caso, qualquer operação dentro da função, altera o valor também fora desta.

**Referência**** → **Endereço de memória
**Valor**** →** Cópia da variável

## Função vs Procedimento

**Função**** → **Retorna um valor
**Procedimento**** →** Não retorna valor

## Strings

> [!tip] 💡
> Assim como no **JAVA, **na maioria das linguagens, uma string é imutável

```javascript
nome = 'Eduardo Quinalha'
nome.toUpperCase()
console.log(nome) // Eduardo Quinalha **** Não altera, pois a string é imutável

nome = nome.toUpperCase() 
console.log(nome) // EDUARDO QUINALHA -> Agora sim

nome.indexOf('du') // 1 -> Posição em que foi encontrado
nome.search('du') // 1 -> Mesma coisa, porém aceita expressões regulares
nome.replace('a', 'A') // EduArdo Quinalha -> Substitui apenas a primeira ocorrência
nome.replace(/a/g, 'A') // Com espressão regular, eu consigo substituir todas as ocorrências
```

**Operadores de concatenação (pesquisar para cada linguagem do edital)**

- JavaScript: **+**
- PHP: **.**
- .NET: **&**
- Python: **+**
- Java: **+**

## Array

```javascript
for(i of array.entries()) {
	console.log(i)   // Retorna um sub array do tipo: [chave, valor] ex: [0, 10]
}

array.keys() // somente as chaves (no caso de um array: [0, 1, ..., n]
array.values() // somente os valores

reduce(a,b) => a+b // soma de todos os valores (a vira um acumulador, b, próximo valor)
```

## Paradigmas de linguagens de programação

- **Imperativas**
- **funcionais**
- **lógicas**
- **Orientado a Objeto**
- **Orientado a Eventos**

# Orientação a Objeto

> [!note] 🔥
> **Ligação Tardia →** Ligação em tempo de execução.
Dentro do conceito de polimorfismo, significa que o método a ser invocado é definido em tempo de execução, ao contrário de ligação prematura, onde o mesmo é definido em tempo de compilação.

> [!note] 🔥
> **Sobrecarga e sobreposição** são implementações específicas de polimorfismo.
**Sobreposição** → Ligação tardia, definida em tempo de execução
**Sobrecarga** → Ligação prematura, definida em tempo de compilação

> [!tip] 💡
> **Classe abstrata → **Não instancia (não aceita new)

> [!tip] 💡
> **Método abstrato →** Não tem corpo e nem retorno. As classes **concretas** herdeiras deverão implementar o método.
**Uma subclasse abstrata não precisa implementar.**

> [!tip] 💡
> Interface não implementa interface
Interface não implementa classe
classe não extende interface
interface não extende classe

interface PODE extender outra interface

> [!tip] 💡
> Por default, todos os métodos definidos em uma interface são public e abstract