---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2024-09-27T14:46:00
Owner:
  - Eduardo Quinalha
---
# MER e UML

> [!note] 🔥
> Modelo conceitual → Independente de SGBD

> [!tip] 💡
> Em ER não pode existir um relacionamento associado a outro relacionamento. Caso necessário, utiliza-se entidades associativa (agregação)

> [!note] 🔥
> Modelo Entidade Relacionamento Estendido (EER) → Herança, especialização/Generalização

# Conceitos

## **Entidade Fraca**

- Não existe sem uma outra entidade forte que o identifique. 
- Também não possui um atributo chave próprio. 
- É caracterizado por um retângulo de bordas duplas.

## **Atributo Composto ou Complexo**

- Atributo composto por outros menores. 
- Exemplo: Endereço

## **Atributos multivalorados **

- Permite múltiplos valores. 
- Exemplo: Telefones. 
- É representado por uma elipse de borda dupla

## **Atributos derivados**

- Podem ser calculados a partir de outros, em tempo de execução.
- É representado por uma elipse de borda tracejada

## **Atributo chave**

- Permite identificar univocamente uma entidade. 
- Exemplo: Id, CPF. 
- Representado por um traço abaixo do nome do atributo

## **Domínio **

- Conjunto de valores básicos aceitos para um atributo. 
- Não são representados no modelo ER

## **Grau de relacionamento **

- Número de entidades que participam de um relacionamento.
- Relacionamento unário é um relacionamento com a própria entidade (ex. Supervisor). 
- Podem ser unários, binários, ternários, etc…

## **Papel**

- Função que a entidade desempenha em um relacionamento. 
- Exemplo: Supervisiona, supervisionado

## **Restrição de participação **

- Parcial / total. 
- Se a cardinalidade mínima for** 0 - parcial**, se for **maior que 0 - total.** 
- Pode ser representada por uma linha dupla no relacionamento quando for total

## **Generalização / Especialização **

- Segue mesmo padrão de herança e polimorfismo em OO. 
- Simboliza por um arco cortando a linha do relacionamento e um círculo de onde partem as especializações com a letra d.
- Na entidade especializada, aparecerão apenas os atributos especializados

## **Disjunção e sobreposição **

- Uma entidade genérica pode ser ao mesmo tempo duas ou mais de suas entidades especializadas.

## **Especialização Total ou parcial **

- Quando a entidade genérica não pode existir sozinha (não pode ser instanciada) é uma especialização total.
- Caso a entidade genérica possa existir por ela mesma, é especialização parcial

## **Relacionamentos contingentes**

- Quando um dos relacionamentos existe, obrigatoriamente o outro também.
- É representado por duas linhas transversais às linhas dos relacionamentos contingentes

## **Relacionamento mutuamente exclusivo **

- Quando um relacionamento existe, o outro não. 
- É representado por uma linha cruzando as linhas dos relacionamentos mutuamente exclusivos

<!-- Column 1 -->
![[Untitled 683.png]]

![[Untitled 684.png|Especialização por disjunção]]

![[Untitled 685.png]]

![[Untitled 686.png]]

<!-- Column 2 -->
![[Untitled 687.png]]

![[Untitled 688.png|Especialização por sobreposição]]

![[Untitled 689.png]]

![[Untitled 690.png]]

# Outras notações

## Bachman

Notação de setas.

## James Martin

Notação de pé de galinha

As entidades já são representadas de forma mais parecida com o diagrama de classes

**Relacionamento obrigatório - |**

**Relacionamento opcional - O**

## Barker

Segue a notação pé de galinha para cardinalidade

Linhas contínuas ou tracejadas denotam a obrigatoriedade (cardinalidade mínima)

> [!note] 🔥
> Atenção! A notação é invertida. O tracejado ou linha contínua lê-se a partir da entidade mais próxima. A notação de cardinalidade (pé de galinha) lê-se no lado oposto.

![[Untitled 691.png]]

## IDEF1X

A parte de cima do diagrama é a chave primária

![[Untitled 692.png|Cantos vivos → Idependente
Cantos arredondados → Dependente (sua PK contém a PK de outra entidade)]]

> [!note] 🔥
> Questões que perguntam sobre cardinalidade entre duas entidades, considera-se a cardinalidade máxima! (1:1), (0:1), (1:n), n:m

No IDEF1X, os relacionamentos podem ser do tipo identificado ou não identificado. Independente de sua cardinalidade, um relacionamento identificado ocorre quando a FK que relaciona com outra entidade também faz parte da chave primária da entidade do lado N. Ao contrário, quando não faz parte da chave primária, temos um relacionamento não identificado.

![[Untitled 693.png|à esquerda, relacionamento não identificado (pontilhado)
à direita, relacionamento identificado (linha cheia)]]

![[Untitled 694.png]]
