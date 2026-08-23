---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2025-04-29T14:41:00
Owner:
  - Eduardo Quinalha
---
# Introdução

- Linguagem compilada
- Gera executáveis para o SO utilizado
- Assim como no C e Java, o ponto de entrada de um programa escrito em Rust é a função `main()`

```rust
fn main() {
    println!("Hello, world!");
}
```

- o uso do `!` significa que está sendo chamado uma **macro **e não uma **função**

## Variáveis

- Em Rust, as variáveis são declaradas com `let `e são imutáveis por padrão
- Para que a variável seja mutável, deve-se declarar como: `let mut`
- Rust possui tipagem forte, porém usa inferência
- Para tipos numéricos inteiros, o default é `i32` que é um número de 32 bits
- Já para ponto flutuante, o default é `f64`
	- Obs: Todos os tipos de ponto flutuante são `signed`
- Outros tipos
	- `u32`
	- `i64`
	- `u64`

## Constantes

- Declaradas com `const`
- São avaliadas no tempo de **compilação**
- Isso significa que o valor da constante precisa ser conhecido e definido durante a compilação do programa.
- Não é possível calcular ou atribuir um valor a uma constante em tempo de execução.
- O escopo das constantes é global
- Sempre **precisam ter seu tipo explicitamente especificado**, e a convenção é que seus nomes estejam em letras maiúsculas com underscores separando as palavras.

```rust
const MAX_POINTS: u32 = 100_000;
```

## Shadowing

- Rust possibilita que variáveis sejam re-declaradas

```rust
    let mut guess = String::new();

    io::stdin()
        .read_line(&mut guess)
        .expect("Failed to read line");

    let guess: u32 = guess.trim().parse().expect("Please type a number!"); // Aqui a variável gues foi re-declarada

    println!("You guessed: {guess}");

    match guess.cmp(&secret_number) {
        Ordering::Less => println!("Too small!"),
        Ordering::Greater => println!("Too big!"),
        Ordering::Equal => println!("You win!"),
    }
```

## Match e Result

```rust
let guess: u32 = match guess.trim().parse() {
            Ok(num) => num,
            Err(_) => continue,
        };
```

- O método parse(), que pertence ao tipo string, retorna um objeto do tipo `Result`
- `Result` por sua vez é um enum que pode conter variantes do tipo `Ok` e `Err`
- No exemplo acima a expressão `match` é utilizada para verificar a variante retornada pelo método `parse()`
- Caso o valor retornado pelo Parse seja `Ok`, o próprio número resultante da operação será passado como parâmetro para a função `Ok() `que por sua vez está definida aqui para retornar este número
- Caso o resultado seja `Err` esta função deverá ser definida com o tipo de erro que se deseja capturar. Neste caso, `_` significa qualquer erro.

## Tipos compostos

- **Tuplas**
	- Tamanho fixo
	- Uma vez declarado, não pode ter seu tamanho alterado
	- Pode conter tipos diferentes
```rust
fn main() {
    let tup: (i32, f64, u8) = (500, 6.4, 1);
    
    let (x, y, z) = tup;

    println!("The value of y is: {y}");
}
```
	- Os elementos de uma tupla também podem ser acessados utilizando a notação de ponto `.`
```rust
n main() {
    let x: (i32, f64, u8) = (500, 6.4, 1);

    let five_hundred = x.0;
    let six_point_four = x.1;
    let one = x.2;
}
```
- **Arrays**
	- Todos os elementos devem ser do mesmo tipo
	- O tamanho do array é fixo
```rust
fn main() {
    let a = [1, 2, 3, 4, 5];

    // Outra forma
    let a: [i32; 5] = [1, 2, 3, 4, 5];
    
    // Array de 5 posições todas contendo o número 3
    let a = [3; 5];
}
```

## Funções

- O valor de retorno é indicado com o operador `->` 
```rust
fn five() -> i32 {
    5
}

fn main() {
    let x = five();

    println!("The value of x is: {x}");
}
```
- Quando uma linha não tem o `;` no final ela é tratada como uma expressão e retorna um valor

## Controle de fuxo

- `if` é tratado como expressão e não precisa de parênteses
```rust
n main() {
    let number = 6;

    if number % 4 == 0 {
        println!("number is divisible by 4");
    } else if number % 3 == 0 {
        println!("number is divisible by 3");
    } else if number % 2 == 0 {
        println!("number is divisible by 2");
    } else {
        println!("number is not divisible by 4, 3, or 2");
    }
}
```
- Também é possível utilizar `if `diretamente a atribuição de valores para uma variável
```rust
fn main() {
    let condition = true;
    let number = if condition { 5 } else { 6 };

    println!("The value of number is: {number}");
}
```
- `loop`
```rust
// básico
loop {
	  println!("again!");
}

// Com retorno de valor
let mut counter = 0;

let result = loop {
    counter += 1;

    if counter == 10 {
        break counter * 2;
    }
};

println!("The result is {result}");

// Desambiguação:
// Quando utilizados loops aninhados, as expressões break e contiue referem-se sempre ao loop mais interno
// Em Rust, é possível especificar labels para que estas expressões refiram-se a loops mais externos, quando necessário

let mut count = 0;
'counting_up: loop {
    println!("count = {count}");
    let mut remaining = 10;

    loop {
        println!("remaining = {remaining}");
        if remaining == 9 {
            break;
        }
        if count == 2 {
            break 'counting_up;
        }
        remaining -= 1;
    }

    count += 1;
}
println!("End count = {count}");
```
- `while`
```rust
// While é um loop condicional
let mut number = 3;

while number != 0 {
    println!("{number}!");

    number -= 1;
}

println!("LIFTOFF!!!");
```
- `for...in`
```rust
let a = [10, 20, 30, 40, 50];

for element in a {
    println!("the value is: {element}");
}
```

# Cargo

- Sistema de construção e gerenciamento de pacotes
- Criando um novo projeto com cargo: 
	- Com este comando, é criado:
		- um novo diretório
		- o arquivo `Cargo.toml` que gerencia as dependências
		- um subdiretório `main `com um arquivo `main.rs`
		- Um repositório git com um `.gitignore`

```shell
$ cargo new hello_cargo
$ cd hello_cargo

# Para compilar o código
$ cargo build

# Para compilar e executar o código com o Cargo
$ cargo run

# Para verificar o código sem compilar
$ cargo check

# Compilar otimizado para produção
cargo build --release
```

# Áreas de armazenamento

- Rust utiliza dois tipos de área de memória para armazenamento de dados:
	- Stack
		- Todos os dados devem possuir o mesmo tamanho
		- Mais eficiente
	- Heap
		- Dados de tamanhos variados
		- Menos eficiente

# Strings

- Strings utilizam um esquema especial de armazenamento
- Elas utilizam simultaneamente as duas estruturas: stack e heap
- Na stack é armazenado uma estrutura que contém:
	- o tamanho da string, 
	- a capacidade da área de armazenamento reservada para ela
	- um ponteiro para uma área da heap, onde a string está efetivamente armazenada 
![[SubPages/Concursos/images/image 7.png]]
- Quando se faz uma cópia de uma string, a única coisa que é copiada é a estrutura da stack
![[SubPages/Concursos/images/image 8.png]]
- No entanto, devido aos mecanismos de ownership do Rust, quando se faz isso, a primeira referência (neste caso s1) é invalidada
- Caso se deseje realizar uma cópia completa de uma string, deve-se utilizar o método `clone`
```rust
let s1 = String::from("hello");
let s2 = s1.clone();

println!("s1 = {s1}, s2 = {s2}");
```

### Templates

- Usa-se `{}` como placeholders

```c++
let x = 5;
let y = 10;

println!("x = {x} and y + 2 = {}", y + 2);
```

# Ownership

- Rust não tem garbage collector
- Ao invés disso, ele controla alocação de memória dinamicamente pelo mecanismo de ownership
- Cada valor deve ter um único ownership por vez
- Valores sem ownership ou cujo ownership esteja fora do escopo, serão apagados da memória
