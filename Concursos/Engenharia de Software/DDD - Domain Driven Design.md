---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2024-12-04T11:17:00
Owner:
  - Eduardo Quinalha
---
# Introdução

- Desenvolvimento de software cujo design é centrado com um domínio de negócio
- Defende que os desenvolvedores têm que ter um profundo conhecimento do domínio do sistema
- O design é definido pelo domínio e não por frameworks, arquiteturas, linguagens, etc.
- Separação expressa entre domínio e tecnologia
- Padrões utilizados:
	- [Arquitetura em camadas](/75449757e45f4c5aa7930e54aff430ac)
	- [Arquitetura hexagonal](/7b77fe8edc674d4bbfe8953d279081a2)
	- [Arquitetura limpa](/a72149fde2644d91b7735527fa0b4d09)

# Linguagem Ubíqua

- Conjunto de termos que deverão ser entendidos tanto por desenvolvedores quanto por especialistas no negócio

![[Untitled 362.png]]

- Possibilita nomear entidades do código como classes, atributos, pacotes, módulos, tabelas de banco, rotas de API, etc.

# Objetos de Domínio

- DDD foi desenvolvido para linguagens **orientadas a objeto**
- Sendo assim, utiliza alguns conceitos de OO como blocos básicos (building blocks):

## **Entidades**

- Objeto de **identidade única**
- Exemplo: Usuário

## **Objetos de Valor (Entidade fraca)**

- **Não possuem identificador único**
- Caracterizados **apenas por seu estado**
- Exemplo: Endereço
	- Não tem um ID de endereço.
	- Dois endereços que possuam os mesmos valores dos atributos serão idênticos

## **Serviços**

- Objetos que **realizam operações**
- Não se encaixam no contexto de entidades e nem de objetos de valor

## **Agregados**

- Coleções de **entidades** e **objetos de valor**
- Possui um **objeto raiz**, que deve ser uma **entidade**
- A raiz, por sua vez, referencia os objetos internos do agregado.
- Porém, esses objetos internos não devem ser visíveis para o resto do sistema, ou seja, apenas a raiz pode referenciá-los.
- Como formam uma unidade coerente, agregados são persistidos em conjunto em bancos de dados. 
- A deleção de um agregado, da memória principal ou de um banco de dados, implica na deleção da sua raiz e de todos os objetos internos.

> [!tip] 💡
> **Exemplo**: No sistema de bibliotecas, um `Empréstimo` possui um `Usuário` (que é uma entidade) e uma lista de `ItemEmpréstimo`. Cada `ItemEmpréstimo` contém informações sobre um certo `Livro` que foi emprestado.
> Logo, `Empréstimo` e `ItemEmpréstimo` formam um agregado, como mostrado na figura. Isto é, uma entidade única do ponto de vista conceitual. `Empréstimo` é a raiz do agregado e `ItemEmpréstimo` é a classe dos objetos internos, os quais não podem ser manipulados sem passar antes pela raiz.

![[Untitled 363.png]]

## **Repositórios**

- Objeto usado para recuperar outros objetos de domínio de um banco de dados.
- Provê uma abstração que blinda os desenvolvedores de preocupações relacionadas com acesso a bancos de dados.
- Permite manipular objetos de domínio como se eles fossem listas (ou coleções) armazenadas na memória principal.

# Contextos Delimitados (Bounded Contexts)

- Conforme a complexidade e tamanho do software aumenta faz-se necessário quebrar o domínio complexo em domínios menores

> [!tip] 💡
> **Exemplo:** Suponha que a nossa biblioteca tenha um setor financeiro. Esse setor tem necessidades específicas, que começam a justificar um projeto separado, com uma linguagem própria. Por exemplo, nesse domínio financeiro, a classe `Usuário` pode, inclusive, ser chamada de `Cliente` e ter novos atributos.

- têm regras e responsabilidades claramente definidas
- representam áreas específicas do domínio de negócio com suas próprias regras, terminologias e modelos conceituais

## Context Maps

- ferramenta que ajuda a entender como os diferentes Bounded Contexts interagem e se relacionam entre si.
- Ele serve para identificar áreas de sobreposição, inconsistências e oportunidades de refatoração
- visualiza e descreve as relações entre diferentes Bounded Contexts

# Camada Anticorrupção

- Utilizada quando é necessário integrar sistemas de domínios diferentes
- A linguagem ubíqua é diferente

> [!tip] 💡
> **Exemplo:** um sistema A precisa usar serviços de um sistema B, que pode inclusive ser um sistema externo, isto é, de uma outra organização. Para evitar que A tenha que se adaptar e usar, mesmo que parcialmente, a linguagem ubíqua de B, pode-se usar uma **Camada Anticorrupção** para mediar essa comunicação.

- É composta por 3 tipos de classes:
	- **Classes de Serviço:** contém os métodos que serão chamados por A
	- **Classes de Adaptadores: **convertem os modelos e tipos de dados de B para A
	- **Classe de Fachada:** usada para acessar B. Facilita o uso de B.
	`Sistema A -> [ Serviços -> Adaptadores -> Fachada ] -> Sistema B`

![[image 101.png]]
