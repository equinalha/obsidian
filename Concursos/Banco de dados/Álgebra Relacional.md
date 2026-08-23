---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2024-09-05T15:05:00
Owner:
  - Eduardo Quinalha
---
<!-- Column 1 -->
[https://www.estrategiaconcursos.com.br/blog/banco-dados-descomplicado-algebra-relacional/](https://www.estrategiaconcursos.com.br/blog/banco-dados-descomplicado-algebra-relacional/)

<!-- Column 2 -->
[https://www.macoratti.net/13/06/sql_arcb.htm](https://www.macoratti.net/13/06/sql_arcb.htm)

# Resumo

| **Operação** | **Primitiva** | **Símbolo** | **Comutativa** | **Tipo** | **Finalidade** | **SQL** |
| --- | --- | --- | --- | --- | --- | --- |
| **Seleção** | SIM | **σ**<cond>(T1) | SIM | Unária | Seleciona as linhas que satisfaçam uma condição | WHERE |
| **Projeção** | SIM | **Π**<att>(T1) | NÃO | Unária | Exibe apenas os atributos especificados **e elimina repetições** | SELECT |
| **Rename** | SIM | **ρ**(A, T1) | NÃO | Unária | Atribui um nome diferente ao resultado da operação | AS |
| **Prod Cartesiano** | SIM | T1 **X** T2 | SIM | Binária | Combina todas as ocorrências de T1 com todas as ocorrências de T2 | FROM T1, T2 |
| **União** | SIM | T1 **⋃** T2 | SIM | Binária | Todas as linhas de T1 e T2, porém remove repetições |   |
| **Diferença** | SIM | T1 **-** T2 | NÃO | Binária | Todas as linhas de T1 que não estejam em T2 |   |
| **Junção** | NÃO | T1 **⋈** T2 | SIM | Binária | Idem ao produto cartesiano, porém desde que satisfaçam a uma condição | JOIN … ON … |
| **Intersecção** | NÃO | T1 **⋂** T2 | SIM | Binária | Todas as linhas comum de T1 e T2. As tabelas devem ser “união compatíveis” |   |
| **Divisão** | NÃO | T1 **/** T2 | NÃO | Binária | Todos os elementos de T1 que se relacionam (em T1) com todos os elementos de T2 |   |

> [!note] 🔥
> Álgebra relacional → Linguagem procedural (especifica a ordem em que as operações acontecem)
SQL → Não procedural

# Operações Fundamentais

1. **Seleção**
2. **Projeção**
3. **Produto cartesiano**
4. **União**
5. **Diferença entre conjuntos**
6. **Renomear**

## **Unárias**

- **Aplicadas sobre uma relação**

### **Select - σ (sigma)**

- diferente do select do SQL, corta horizontalmente (Algumas tuplas do conjunto)
- Filtra as linhas de uma relação que satisfazem um conjunto de condições ou predicados
- **σ **<predicado> (nome da relação)
- Conectivos: ∨ (ou), ∧ (e), ¬ (not)
- Macete: **S**eleção - **S**igma
- Exemplos: 
	- $σ  categoria = "suspense" ∧ paginas > 400 (livros)$
	- $σ  peso < 90 ∧ altura > 1,70 (candidatos)$
- **O operador de seleção é comutativo!**
	- $σ<condição1>(σ<condição2) = σ<condição2>(σ<condição1)$

### **Project - 𝛑**

- Corta verticalmente, aí sim, o select do SQL
- **Elimina redundância (linhas duplicadas)**
- Exibe apenas os atributos especificados pelo predicado
- Macete: **P**rojeção - **P**i
- Exemplos:
	- $𝛑 id, nome (professores)$
	- $𝛑 nome, cpf (σ sexo='M')$
- **O operador Projeção não é comutativo!**

### **Rename - ρ (Rho)**

- Atribui um nome diferente ao resultado da operação, AS do SQL
- Útil para trabalhar tabelas com atributos diferentes para na sequência fazer uma operação de união
- Útil também para reduzir ambiguidade no caso de selfjoin
- **ρ(<novo nome>, <expressão>)**

## **Binárias**

- **Aplicadas a duas relações**

### **Produto cartesiano**

- Resulta em uma nova relação com a combinação de todos os elementos da relação A com todos da relação B
- O número de tuplas é o produto da quantidade de tuplas das duas relações
- A quantidade de colunas (atributos) é a soma da quantidade de colunas das duas relações
- **Operador X**
- **Total de colunas do produto cartesiano : **Número colunas da primeira tabela + número de colunas da segunda tabela
- **Número de linhas do produto cartesiano: **Número de linhas da primeira tabela x número de linhas da segunda tabela

### **União**

- Enquanto o produto cartesiano faz uma concatenação horizontal, a união faz a concatenação vertical
- **Elimina as repetições**
- Produz como resultado uma Relação que contém todas as linhas da primeira Relação seguidas de todas as linhas da segunda tabela. 
- A Relação resultante possui a mesma quantidade de colunas que as relações originais, e tem um número de linhas que é no máximo igual à soma das linhas das relações fornecidas como operandos, já que as linhas que são comuns a ambas as relações aparecem uma única vez no resultado.
- *As relações devem possuir o mesmo número de atributos.*
- **A operação de união é comutativa**
	- $R1\cup R2 = R2\cup R1$

### Diferença

- Retorna as tuplas presentes em R1 e ausentes em R2
- requer como operandos duas relações união-compatíveis
- O resultado é uma relação que possui todas as linhas que existem na primeira relação e não existem na segunda.
- $R1 - R2$
- **A diferença NÃO É COMUTATIVA**

### Intersecção

- produz como resultado uma tabela que contém, sem repetições, todos os elementos que são comuns às duas tabelas fornecidas como operandos. 
- As tabelas devem ser união-compatíveis.
- $R1\cap R2$
- **A operação de intersecção é comutativa**
- $R1\cap R2 = R2\cap R1$

# Outras operações

## **Junção**

- Combina as linhas de uma relação A com as de uma relação B desde que satisfaçam uma condição
- Equivale a um produto cartesiano seguido de uma seleção
- **Operador ⋈**
	- relação A ⋈ <u>condição</u> relação B
	- Macete: O próprio símbolo remete a uma junção
- A junção natural pode ser vista como uma combinação de uma operação de seleção aplicada sobre uma operação de produto cartesiano
	- $\sigma<critério>(R1 \bowtie R2)$
- Subtipos
	- Junção Natural:
		- Procura nas duas relações atributos que tenham o mesmo nome e faz uma junção supondo a igualdade destes atributos
		- Se houver dois atributos com o mesmo nome, o SGBD levará em consideração a igualdade da composição destes dois atributos
![[Untitled 309.png]]

## **Divisão**

- Expressa a frase “para todos”
- Dado uma relação A e outra B1, a divisão de A por B1 resulta em todos os elementos de A que se relacionam (em A) com todos os elementos de B1
- Utilizada quando se deseja extrair de uma relação R1 uma determinada parte que possui as características (valores de atributos) da relação R2.

![[Untitled 310.png]]

# Tabela resumo

![[Untitled 311.png]]