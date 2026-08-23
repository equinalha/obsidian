---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2024-11-17T18:56:00
Owner:
  - Eduardo Quinalha
---
# Modelo Relacional

## Conceitos Básicos

> [!note] 🔥
> Relação → Tabela (na verdade, tabela é uma forma de representar uma relação)
Tupla → Linhas, registros
Atributos → Colunas
Domínio → Restrição aos valores do atributo
A quantidade de colunas de uma relação é chamado de Grau ou Aridade da relação

- Baseado na teoria de conjuntos e lógica de predicados de primeira ordem
	- Simplicidade e base matemática
- Sucede os modelos de rede e hierárquico

![[Untitled 695.png]]

- **Aspectos manipuladores:**
	- **Restrição**
		- Restrição vertical
	- **Projeção**
		- Restrição horizontal
	- **Junção**
		- Opera sobre mais de uma relação (inclusive ela mesma)
- **Propriedades**
	- Cada tupla contém apenas um valor (do tipo apropriado) para cada atributo
	- Atributos não são ordenados
	- Tuplas não são ordenadas
	- Não existem tuplas duplicadas

![[Untitled 696.png]]

## Restrições de integridade

- Visam resguardar o estado do banco de dados contra danos acidentais e perda de consistência
- Restrições de integridade mais relevantes:
	- Domínio
		- Tipo de dados
		- Restringe os valores de determinado atributo
	- Chave
		- Uma tupla não pode ser duplicada
		- Por consequência, a chave primária não pode se repetir na relação
		- Cada esquema de relação pode ter mais de uma chave, chamadas chaves candidatas. Apenas uma delas será a chave primária.
		- Superchave: Chave primária composta de dois atributos
	- Vazio
		- Define se o atributo aceita ou não valores nulos
	- Entidade
		- Define que a chave primária é utilizada para identificar as tuplas de uma relação
		- **Define que a chave primária não pode ser nula**
	- Referencial
		- Chave estrangeira
		- Referências externas
		- A chave estrangeira pode apontar para uma chave candidata (não necessariamente precisa ser a chave primária da entidade referenciada)
	- Semântica
		- Regras de negócio
		- Pode ser definida pela aplicação ou …
		- … pelo próprio SGBD usando uma linguagem de especificação de restrição de uso geral
			- Triggers
			- Assertions

# Regras de Codd

![[Untitled 697.png]]

- **Regra Zero**
	- Um BD relacional deve se utilizar de recursos exclusivamente relacionais para o seu gerenciamento
- **1 - **Informação
	- Todos os valores em BD relacional são representados em colunas e linhas de uma tabela
- 2 - Acesso garantido
	- Cada valor atômico deve poder ser logicamente acessado (identificadores únicos - Chave primária e nome da coluna)
- 3 - Tratamento sistemático de valores nulos
	- Valores nulos ou em branco devem ser sistematicamente suportados para representar informações inexistentes
- 4 - Catálogo online dinâmico
	- Separação entre dados e metadados. As tabelas de metadados devem estar acessíveis utilizando a mesma linguagem dos dados
- 5 - Sublinguagem ampla dos dados: 
	- Sintaxe linear
	- Acesso de forma interativa
	- Operações de visão de dados
	- Administração de transações
- 6 - Atualização de visualizações: Todas as views são teoricamente atualizáveis
	- Uma mudança na visão, nem sempre gera uma atualização dos dados das tabelas
- 7 - Inserção, atualização e exclusão de alto nível
	- Regras para atualização dos dados
	- DCL, DML, DDL, DTL
- 8 - Independência física dos dados
- 9 - Independência lógica dos dados
- 10 - Independência de integridade
	- As aplicações não são afetadas quando ocorrem mudanças nas regras de restrições de integridade.
	- As regras de integridade devem ser definidas com linguagem relacional e **armazenadas no catálogo do sistema, e não na aplicação**
- 11- Independência de distribuição
	- No caso dos dados serem distribuídos por mais de um local, isto não deve ser percebido na perspectiva do usuário
- 12 - Não transposição de regras
	- Se o SGBD tem uma linguagem de baixo nível, esta linguagem não deve poder ser utilizada para sobrepor as restrições de integridade da linguagem de mais alto nível


# Visões, Índices

## Visão

- Consultas que são feitas muitas vezes, pode ser armazenada no banco
- É um objeto SQL
- Trata-se de um comando SQL armazenado e que possui um nome associado
- Normalmente envolve mais de uma tabela
- Todas as operações que incidem sobre uma tabela, podem ser feitas sobre uma visão
- No entanto, UPDATE e DELETE não vão refletir nas tabelas originais, somente sobre a view
- É também chamado de uma tabela temporária ou virtual

```sql
	CREATE VIEW NomeDaVisao AS <QuerySQL>
```

## Índices

- Arquivo de índice
	- **Único nível**
		- Contém pares chave → ponteiro
			- Primário: Usa a chave da tabela
			- De agrupamento (clustering): Usa campos não chave, aponta para todos os registros que contêm cada um dos valores
			- Secundário: Campos não ordenados, não chaves, com estruturas de acesso adicionais
	- **Multinível**
		- Árvores B e B+
		- Aponta para um endereço de bloco de disco onde a informação está gravada, além do deslocamento necessário dentro do bloco
		- Melhora a velocidade de acesso aos dados
![[Untitled 698.png]]
- Tipos de índices
	- Densos
		- Cada chave aponta para um registro físico
		- Muitos registros no índice
	- Esparsos
		- Cada chave aponta para o primeiro registro de um bloco
		- Poucos registros no índice

# Chaves e Relacionamentos

## Superchave

- Um conjunto de uma ou mais colunas que, **tomadas coletivamente**, podem identificar univocamente uma tupla da tabela
- Duas linhas não podem ter os mesmos valores de superchave

### Superchave Mínima

- Conjunto de atributos em uma tabela que, em conjunto, identifica unicamente cada registro **sem conter atributos redundantes. **
- Ou seja, é o menor conjunto de atributos que pode ser usado para identificar cada linha da tabela de forma única.
- **Características de uma superchave mínima:**
	- **Unicidade:** Cada combinação de valores dos atributos da superchave deve identificar um único registro.
	- **Irredutível**. A remoção de um dos atributos que compõem a superchave, faz com que essa deixe de ser uma superchave

## Chave

- Pode ser vista como uma superchave mínima
- Irredutível

## Chaves Candidatas

- As  chaves mínimas são chamadas de chaves candidatas. 
- Para um determinado projeto podemos ter várias chaves candidatas. Por exemplo, CPF e RG 
- O projetista do banco de dados tem que escolher uma das chaves candidata para usar efetivamente. 
- Essa chave escolhida será a **chave primária**. 
- As demais chaves candidatas são chamadas de **chaves alternativas.**

## Chave estrangeira

- **Referencia a chave primária de outra tabela**
- Pode apontar para um chave candidata

## Chave primária

- Servem também de campo de ordenação da tabela no modelo físico

# Normalização

> [!tip] 💡
> **Toda determinante é uma chave candidata!**
Chaves candidatas devem ser UNIQUE
Exemplo:
A ⟶ B C⟶ A C ⟶ D D ⟶ C
UNIQUE (A), UNIQUE(B) e UNIQUE(C) 

## Conceitos

- **Normalização**
	- Visa reduzir redundâncias e 
	- anomalia de atualização
		- efeitos colaterais quando se alteram os dados
	- normalmente aumenta a necessidade de junções em tempo de execução, pois segmenta os dados em tabelas diferentes
	- Favorece o crescimento da base de dados
- **Dependência funcional**
	- Todos os atributos de uma tupla dependem da chave
	- Dizemos que a chave determina os demais atributos
	- Dado um valor (chave), pode-se obter os valores dos demais atributos
	- X determina Y (X → Y) se existe no máximo um valor de Y para cada valor de X
	- **DF trivial**
		- O determinado faz parte dos atributos determinantes
	- **DF não trivial**
		- O determinado não faz parte dos atributos determinantes

---

## Resumo

![[Untitled 699.png]]

> [!note] 🔥
> **Chave simples** → Não haverá problemas com a 2FN

> [!note] 🔥
> Valores definidos como **unique** nem sempre podem ser chaves candidatas, pois ainda assim o valor pode assumir o valor **null**, e uma chave não pode ser nula.

---

## 1FN

- **Todos os atributos devem ser atômicos (indivisíveis)**
- **Não podem existir atributos compostos, multivalorados ou aninhados**
- Faz parte da definição do modelo relacional básico
	- Na prática, uma tabela que não esteja na 1FN nem pode se chamar relação

### Exemplo:

| **Código Aluno** | **Nome** | **Telefones** | **Endereço** |
| --- | --- | --- | --- |
| 001 | Fulano | 1111-222222<br>2222-333333 | Rua Matacavalos, 10, Rio de Janeiro, RJ, Pavuna, 61000-000 |

- No exemplo acima, temos um atributo multivalorado (telefones) e um atributo composto (endereço)

### **Versão normalizada**

| **Código Aluno** | **Nome** | **Logradouro** | **Número** | **Bairro** | **CEP** | **Cidade** | **UF** |
| --- | --- | --- | --- | --- | --- | --- | --- |
| 001 | Fulano | Rua Matacavalos | 10 | Pavuna | 61000-00 | Rio de Janeiro | RJ |

| **Cód Aluno** | **Telefone** |
| --- | --- |
| 001 | 1111-22222 |
| 001 | 222-33333 |

**Esquematizando:**

Forma não normal → **Alunos** (<u>Código Aluno,</u> Nome, Telefones, Endereço)

Forma normal → **Alunos** (<u>Código Aluno</u>, Nome, Logradouro, Número, Bairro, CEP, Cidade, UF), **Telefones** (<u>Código Aluno, Telefone</u>)

---

## 2FN

- **Não pode haver dependência funcional parcial (da chave)**
- Todo atributo não chave tem que depender totalmente da chave primária
- Ocorre quando existe chave composta (superchave) e algum dos atributos pode ser totalmente determinado por apenas uma parte da chave, e não por toda ela

### Exemplo

Forma não normal → **Compras **(<u>Cod_compra, CPF</u>, Nome, Endereço, Produto)
    Neste caso, CPF pode determinar nome e endereço, e Cod_compra pode determinar produto

Forma normal → **Cliente **(<u>CPF</u>, Nome, Endereço), **Vendas** (<u>Cod_compra, CPF</u>, Produto)

### Outro Exemplo

Forma não normal → **Vendas **(<u>Num_pedido, Cod_produto</u>, Nome_produto, Qtde, Valor_total)

Forma normal → **Vendas **(<u>Num_pedido, Cod_produto</u>, Qtde, Valor_total), **Produtos** (<u>Cod_produto</u>, Nome_produto)

---

## 3FN

- **Não deve haver dependência funcional transitiva**
	- O atributo chave determina um atributo não chave que este por sua vez determina outro atributo não chave
- Não se aplica a chaves candidatas
- **Não deve haver atributo derivado**
	- total
	- Idade,
	- etc…

### Exemplo

Forma não normal → **Alunos **(<u>CPF</u>, Nome, telResidencial, Endereco)
    Observe que, apesar de não ser um atributo chave, telefone residencial tem uma relação de 1:1 com endereço, ou seja, o endereço pode ser determinado a partir do telefone residencial

Forma normal → **Alunos **(<u>CPF</u>, Nome, telResidencial), **Endereco **(<u>telResidencial</u>, Endereco)

### Outro exemplo

Forma não normal → **Aluno **(<u>Id</u>, Nome, Data_Nascimento, Idade)

Forma normal → **Aluno **(<u>Id</u>, Nome, Data_Nascimento)
    Idade será determinado em tempo de execução, a partir da data de nascimento

---

## FNBC (Forma Normal Boyce Codd)

- Todo determinante é chave candidata
- Mais simples que a 3FN, porém mais rígida
- Quando um atributo não chave determina um atributo que faz parte da chave, este deverá tomar o seu lugar, e o atributo que antes era da chave vai para uma relação separada
- A forma normal *Boyce-Codd Normal Form* (BCNF) elimina toda a redundância que pode ser descoberta **com base nas dependências funcionais.**

### Exemplo

Forma não normal → **Ensina **(<u>Aluno, Disciplina</u>, Professor)

Forma normal → **Ensina **(<u>Professor, </u>Disciplina), **ProfessorAlunos **(<u>Professor</u>, Aluno)

## 4FN

- Lida com **dependências multivaloradas não triviais**
- Uma tabela está na 4FN se estiver na 3FN e não contiver dependências multivaloradas não triviais
- Representada como `A ->> B,` lida como "A determina multivalorado B"
- Exemplo:
| **Pizzaria** | **Sabor** | **Bairro** |
| --- | --- | --- |
| Pizzas da Itália | Margherita | Centro |
| Pizzas da Itália | Pepperoni | Centro |
| Pizzas da Itália | Margherita | Jardim |
| Pizzas da Itália | Pepperoni | Jardim |

    Para normalizar esta tabela para a 4FN, precisamos dividi-la em duas tabelas separadas:
	1. Tabela: Pizzaria_Sabores

| **Pizzaria** | **Sabor** |
| --- | --- |
| Pizzas da Itália | Margherita |
| Pizzas da Itália | Pepperoni |

	2. Tabela: Pizzaria_Bairros

| **Pizzaria** | **Bairro** |
| --- | --- |
| Pizzas da Itália | Centro |
| Pizzas da Itália | Jardim |

## 5FN

- Também conhecida por Forma Normal Projeção-Junção (PJ/NF)
- Uma tabela está na 5FN se e somente se toda dependência de junção não-trivial nessa tabela é implicada pelas chaves candidatas
- Uma tabela 5FN não pode ser decomposta em relações menores sem que haja perda de dados
- A maioria das tabelas em 4FN já está em 5FN
- É considerada a forma normal final em termos de remoção de redundância

## 6FN

- Considerado o nível mais avançado de normalização
- Uma tabela está na 6FN se e somente se satisfaz todas as **dependências de junção não triviais**
- Decompor as tabelas ao ponto em que cada tabela contenha apenas uma coluna dependente e uma ou mais colunas determinantes (chaves)
- Resulta em** tabelas com um número mínimo de atributos**,** geralmente apenas dois**: uma chave e um atributo não-chave
- Particularmente útil em bancos de dados temporais ou históricos
- Ideal para lidar com dados que mudam com frequência ou de forma imprevisível
- Resulta em um grande número de tabelas, o que pode tornar o esquema do banco de dados complexo
- Pode impactar negativamente o desempenho devido ao aumento no número de junções necessárias para consultas

# Modelagem Lógica

> [!note] 🔥
> Muito pedido em provas

## **8 Passos**

1. Mapear entidades fortes
	1. Decompor os atributos compostos em novos atributos atômicos
2. Mapear as entidades fracas
	2. A chave primária da entidade pai vai compor a chave primária da entidade filho, juntamente com a chave primária desta
3. Relacionamentos 1:1
	3. Chave estrangeira
	4. Relacionamento incorporado
	5. Relação de relacionamento 
		1. Tabela de ligação
		2. Otimiza espaço
		3. Interessante onde não é um relacionamento total (obrigatório)
4. Relacionamentos 1:N
	6. A chave primária do lado 1 vai como chave estrangeira no lado N
	7. Os atributos do relacionamento também vão para o lado N
5. Relacionamentos N:N
	8. Obrigatório o uso de tabela de ligação
6. Atributos Multivalorados/Compostos
	9. Os atributos compostos devem ser atomizados na etapa 1
	10. Criar uma tabela que inclui a chave primária da entidade como chave estrangeira
	11. A chave desta tabela será a composição da chave primária da entidade com o próprio atributo multivalorado
7. Relacionamentos N-ários
	12. Cria-se uma nova tabela para o relacionamento
	13. As chaves primárias dos N participantes, compõem a chave primária desta nova tabela
	14. Os atributos da relação tornam-se atributos da nova tabela.
8. Generalização e Especialização (EER)
	15. Cada entidade corresponde a uma tabela
		4. Nas entidades herdeiras, a chave primária da tabela superior entra como chave estrangeira
		5. Os atributos específicos das herdeiras aparecem nas respectivas tabelas
		6. Exemplo:
Aluno (<u>CPF</u>, Nome)
Aluno_Ensio_Medio (<u>CPF</u>, serie)
Aluno_Graduacao (<u>CPF</u>, tcc)
Aluno_Especializacao (<u>CPF</u>, dissertacao)
	16. As entidades herdeiras incorporam os atributos da entidade superior
		7. Não existe uma tabela correspondente à entidade superior
		8. Não existe uma instância direta da entidade superior
		9. Exemplo
Aluno_Ensio_Medio (<u>CPF</u>, nome, serie)
Aluno_Graduacao (<u>CPF</u>, nome, tcc)
Aluno_Especializacao (<u>CPF</u>, nome, dissertacao)
	17. Adiciona os atributos especializados na entidade superior
		10. Existirá somente uma entidade
		11. Especialização total, sem sobreposição
		12. Exemplo:
Aluno (<u>CPF</u>, Nome, Tipo_Aluno, seria, tcc, dissertacao)
---
![[Untitled 700.png]]

9. **Entidades Regulares**
Funcionario (<u>cpf</u>, Pnome, Minicial, Unome, Datanasc, Endereco, Sexo, Salario)
Departamento (Dnome, <u>Dnumero</u>)
Projeto (Projnome, <u>Projnumero</u>, Projlocal)
10. **Entidades Fracas****
**Dependente (<u>CpfFuncionario, Nome</u>, Sexo, DataNasc, Parentesco)
11. **Relacionamentos 1:1****
**Departamento (Dnome, <u>Dnumero</u>, Cpf_gerente, Data_Inicio_gerencia)
12. **Relacionamentos 1:N
**Funcionario (<u>cpf</u>, Pnome, Minicial, Unome, Datanasc, Endereco, Sexo, Salario, cpf_Supervisor, DptoNumero)
Projeto (Projnome, <u>Projnumero</u>, Projlocal, DptoNumero)
13. **Relacionamentos N:N
**Trabalha_Em (<u>cpf, Projnumero</u>, horas)
14. **Atributos multivalorados
**Localizacao_departamento (<u>Dnumero, Dlocal</u>)