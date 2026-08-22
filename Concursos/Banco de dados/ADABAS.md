---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2024-10-23T06:56:00
Owner:
  - Eduardo Quinalha
---
[https://adabasmainframe.blogspot.com/2011/04/book-adabas.html](https://adabasmainframe.blogspot.com/2011/04/book-adabas.html)

# Características

- Adabas → Adaptable Data Base System
- SGBD otimizado para Big Data
- Utiliza a linguagem de programação “Natural 1”, semelhante à Java porém é interpretada
- organiza e acessa os dados de acordo com as relações entre os campos de dados
- As relações entre os campos de dados são expressas por arquivos (**files**)
- suporta ambientes e execução monousuário e multiusuários.
- Baseado no conceito de **Listas Invertidas**
	- Pode ser comparado como **Não relacional** ou **Quase Relacional**
- Usado extensamente nas aplicações que requerem um **volume muito grande de processamento de dados**, ou com grandes transações de processamento analítico online (**OLAP**).
- O Banco de dados Adabas armazena em forma de **comprimido** para reduzir o espaço necessário.

## Vantagens

- Alta disponibilidade
- Otimização do espaço de armazenamento
- Desempenho
- Tolerância a falhas

## Categorias

- O Adabas é dividido em duas categorias:
	- Adabas C: Usado em mainframes e plataformas baixas (Unix, Linux e Windows)
	- Adabas D: Banco de dados totalmente relacional, funciona em Windows, AIX, HP-UX, Suse e RHEL

## Replicação

- Suporta replicação
- Tanto para outras instâncias Adabas quanto para outros bancos relacionais

## SQL

- Adabas não é baseado em SQL, porém pode ser instalado um mecanismo de busca externo com SQL padrão

## Múltiplos Modelos de Dados

- Adabas permite escolher qualquer tipo de estrutura de dados
- Os mesmos dados podem ser visualizados sob múltiplas perspectivas
	- Relacionais
		- Incluindo aninhamento relacional
	- Relação entre entidades
	- Modelo de rede
	- Modelo hierárquico
	- Modelo geográfico
	- Texto

# Terminologia

- Alguns termos são diferentes do contexto de bancos relacionais

![[Untitled 156.png]]

- Registro
	- Conjunto de campos
	- Cada registro é associado a um número sequencial interno ISN
- Bloco
	- Conjunto de registros
- Extent
	- Conjunto de blocos físicos contíguos de disco
- 

# Estrutura do banco de dados

```plain text
+----------------------------+      +-----------------------------------------------------+
|    Banco de Dados Adabas   |      |                Outros tipos de Data Sets            |
|  +---------------------+   |      |  +---------------------+   +---------------------+  |
|  |                     |   |      |  |                     |   |                     |  |
|  |     ASSOCIATOR      |   |      |  |PROTECTION LOG (PLOG)|   |         TEMP        |  |
|  |                     |   |      |  |                     |   |                     |  |
|  +---------------------+   |      |  +---------------------+   +---------------------+  |
|                            |      |                                                     |
|  +---------------------+   |      |  +---------------------+   +---------------------+  |
|  |                     |   |      |  |                     |   |                     |  |
|  |    DATA STORAGE     |   |      |  |  COMMAND LOG (CLOG) |   |        SORT1        |  |
|  |                     |   |      |  |                     |   |                     |  |
|  +---------------------+   |      |  +---------------------+   +---------------------+  |
|                            |      |                                                     |
|  +---------------------+   |      |  +---------------------+   +---------------------+  |
|  |                     |   |      |  |                     |   |                     |  |
|  |        WORK         |   |      |  | RECOVERY  LOG (RLOG)|   |        SORT2        |  |
|  |                     |   |      |  |                     |   |                     |  |
|  +---------------------+   |      |  +---------------------+   +---------------------+  |
|                            |      |                                                     |
+----------------------------+      +-----------------------------------------------------+
```

- Entre os principais data sets, destacam-se:
	- **ASSO**
		- Cada registro armazenado recebe um ISN (Internal Sequence Number)
		- O ISN é único por arquivo
		- A informação do ISN fica armazenada no ASSO
	- **DATA** 
		- Onde ficam fisicamente armazenados os dados
		- São comprimidos
	- **WORK**
		- Armazenamento temporário para resultados intermediários durante operações de busca complexas
	- **PLOG**
		- Protection Log
		- Registra as imagens antes e depois dos registros, quando são feitas alterações nos dados
	- **CLOG**
		- Proporciona uma trilha de auditoria
		- Pode ser utilizado como depuração 
- Record Buffers
	- Estruturas de dados utilizadas para armazenar temporariamente registros que estão sendo passados para dentro ou para fora do banco de dados em operações de entrada e saída.
		- Quando uma *stored procedure* é chamada, os parâmetros necessários para a sua execução são passados através destes *record buffers*

# Interoperabilidade

- O ADABAS possui a capacidade de se comunicar com outros sistemas por meio de várias interfaces
- **ODBC**
	- Permite interação com bancos relacionais como MySQL, Oracle, SQL Server
	- Permite tanto **leitura quanto escrita **de dados
	- Pode gerenciar grandes volumes de dados distribuídos em **várias partições**

### **Adabas SQL Gateway**

- Permite o acesso a dados do ADABAS usando SQL, facilitando a integração com ferramentas de BI, data warehouses e aplicações que dependem de SQL para consultas. 

### **Adabas SOA Gateway**

- Permite que as funcionalidades do ADABAS sejam expostas como serviços web SOAP e REST, facilitando a integração com arquiteturas orientadas a serviços (SOA). 
