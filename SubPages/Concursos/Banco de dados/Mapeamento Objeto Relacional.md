---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2024-10-01T20:52:00
Owner:
  - Eduardo Quinalha
---
# Regras para mapeamento Objeto-Relacional

- Todas as tabelas devem ter chave primária → OID

## Mapeamento de atributos

- Simples → Colunas
- Compostos → Várias colunas
- Multivalorados → Tabela auxiliar onde a chave primária é composta pela chave primária da tabela que contém o atributo multivalorado e pela chave primária do atributo multivalorado

![[Untitled 580.png]]

## Herança: Pode-se mapear de 3 formas

- **1 - criar uma tabela para cada classe.**
	- os atributos da tabela são os atributos **específicos** da classe e mais uma coluna de **chave estrangeira** que referencia a chave primária da tabela pai.
	- As desvantagens do uso dessa técnica é que são geradas muitas tabelas no banco de dados, fazendo com que haja uma demora maior para ler e gravar os dados.
	- algumas consultas acabam sendo bastante dificultadas, obrigando a criação de views para agilizar o processo.
![[Untitled 581.png]]
- **2 - criar uma única tabela para toda a hierarquia de classes.**
	- a classe raiz é tomada por base, pois é nela que todos os atributos são armazenados. 
	- Essa técnica facilita as consultas, pois os dados de um objeto estão em uma única tabela 
	- O principal problema é que, potencialmente, há um desperdício de espaço no banco de dados. Além disso, a performance pode ser prejudicada.
![[Untitled 582.png]]
- **3 - criar uma tabela para cada classe concreta**
	- incluir em cada tabela tanto os atributos específicos, quanto os atributos herdados da classe que ela representa. 
	- Como os dados de uma classe ficam todos em uma única tabela, as consultas são facilitadas.
![[Untitled 583.png]]

## Associações

### N:N

- Criar uma tabela associativa em que a chave primária é composta pelas chaves primárias das tabelas associadas

![[Untitled 584.png]]

- Associações Muitos-para-Muitos com Classe de Associação
	- Aplica-se a regra da associação muitos-para-muitos e os atributos da classe associativa **permanecerão na tabela que é gerada para mapear a associação.**
![[Untitled 585.png]]

### 1:N

- a tabela cujos registros podem ser endereçados diversas (lado Muitos do relacionamento) vezes é a que herda a referência da tabela cuja correspondência é unitária.
- Ou seja, a referência está no lado N

![[Untitled 586.png]]

- Associações Um-para-Muitos com Classe de Associação:
	- aplica-se a regra da associação um-para-muitos e os atributos da classe associativa são herdados como atributos normais pela tabela que herda a chave estrangeira
![[Untitled 587.png]]

### 1:1

- única tabela no modelo relacional
	- os atributos da classe agregada devem ser colocados na mesma tabela da classe agregadora.
	- Melhor performance
	- O cascade é implícito
- duas tabelas (uma para cada classe)
	- uma delas deve herdar como um atributo normal (chave estrangeira) a chave primária da outra tabela.
	- Facilita a manutenção das tabelas e torna a estrutura do banco de dados mais flexível.
	- É necessário [**implementar triggers**](https://www.devmedia.com.br/introducao-a-triggers/1695) ou rotinas especiais na aplicação para o cascade