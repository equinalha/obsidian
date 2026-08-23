---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2026-08-05T17:44:00
Owner:
  - Eduardo Quinalha
---
# Associações lógicas

- Resolver com tabelas de características

![[Untitled 263.png]]

# Diagramas Lógicos - (Euler Venn)

- Utilizado com quantificadores
	- Todo
	- Algum
		- Ao menos um
		- Pelo menos um
		- Existe (…)
	- Nenhum
- A partir desses quantificadores, podemos formar as seguintes proposições categóricas.
	- Todo A é B
	- Nenhum A é B
	- Algum A é B
	- Algum A não é B
- O verbo é o termo que separa as duas partes

![[Untitled 264.png]]

- Vale lembrar que: 
	- “Todo A é B” ≠ “Todo B é A”
	- “Nenhum A é B” = “Nenhum B é A”
	- “Algum A é B” = “Algum B é A”
- Exemplo:
	- **Todo A é B, todo B é C, todo C é D, logo, todo A é D**
		- A → B
		- B → C
		- C → D
	- Cortam-se os termos iguais que estejam em lados diferentes da seta
		- A →~~ B~~
		- ~~B~~ → ~~C~~
		- ~~C~~ → D
	- Sobra:
		- A → D

# Diagramas Lógicos - Argumentação

- Conjunto de premissas que acarretam uma conclusão

![[Untitled 265.png]]

# MMC e MDC

## MMC

![[Untitled 266.png]]

## MDC

![[Untitled 267.png]]

# Análise Combinatória

![[Untitled 268.png]]

## Anagramas

- Para calcular a quantidade de anagramas basta dividir o total de letras fatorial pelos fatoriais das repetições

$$
A(x) = \frac{n!}{r1!.r2!.(...)}
$$

- Exemplo:
	- Quantidade de anagramas da palavra ASSADO:
$$
A(x) = \frac{6!}{2!.2!}
$$

# Noções de Probabilidade

- Probabilidade de um evento: P(E) = <u>n(E) / n(Ω)</u>

# Juros

## Simples

- J = C.i.t
	- J = Juros
	- C = Capital (valor inicial)
	- t = Período
- M = C + J
	- M = Montante

## Composto

$$
M = C (1+i)^t
$$

- M = Montante
- C = Capital
- i = Taxa de Juros
- t = Período de Tempo

# Lógica

![[Raciocínio Lógico synced block]]
