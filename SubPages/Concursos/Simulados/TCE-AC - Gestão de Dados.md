---
base: "[[Simulados.base]]"
Desempenho: 0.77
Banca: CEBRASPE
Obs: ""
Tipo: Certo/Errado
Obj: TSE
"% Colocação": -100
Status: Done
Data: 2024-10-23
---
[https://www.qconcursos.com/questoes-de-concursos/provas/cespe-cebraspe-2024-tce-ac-analista-de-tecnologia-da-informacao-area-gestao-de-dados](https://www.qconcursos.com/questoes-de-concursos/provas/cespe-cebraspe-2024-tce-ac-analista-de-tecnologia-da-informacao-area-gestao-de-dados)

**60 - No que se refere ao banco de dados ADABAS, julgue o item abaixo.**

**O ADABAS permite a comunicação com outros sistemas gerenciadores de banco de dados por meio do driver ODBC, desde que essa comunicação seja exclusivamente de consultas para uma única partição.**

> O ADABAS possui a capacidade de se comunicar com outros sistemas por meio de várias interfaces
> - **ODBC**
>     - Permite interação com bancos relacionais como MySQL, Oracle, SQL Server
>     - Permite tanto **leitura quanto escrita **de dados
>     - Pode gerenciar grandes volumes de dados distribuídos em **várias partições**

**62 - A respeito de arquitetura e política de armazenamento de dados e engenharia de dados, julgue o item subsequente.**

**Na ingestão de dados do tipo *****streaming*****, os dados são coletados de forma incremental, ou seja, apenas os dados novos são processados.**

> 
Pela interpretação do CESPE, ele considera que a ingestão incremental é um subtipo da ingestão em lote, que é oposto à ingestão do tipo streaming

**63 - Os armazenamentos de pares chave-valor são os menos adequados para uso em sistemas que precisam consultar dados em diferentes armazenamentos de pares chave-valor. **

> 
Correto.

Apesar de serem muito eficientes para consultas diretas de chave: valor, porém apresentam um péssimo desempenho para consultas complexas, que envolvam múltiplas chaves.

Bancos de dados chave-valor não são otimizados para realizar consultas complexas, como junções (joins) entre diferentes conjuntos de dados ou buscas baseadas em atributos que não sejam a chave. 

**66 - Julgue o item a seguir, relativos ao modelo relacional de banco de dados e à normalização das estruturas de dados.**

**No modelo de dados relacional, é possível definir múltiplas chaves primárias em uma única tabela, permitindo que diferentes combinações de campos possam ser utilizadas para garantir a unicidade dos registros.**

> 
Errado

No modelo relacional de banco de dados, **não é possível definir múltiplas chaves primárias** em uma única tabela. A chave primária é uma restrição que garante a **unicidade** e **não nulidade** dos registros em uma tabela, identificando de forma exclusiva cada linha.
Em cada tabela, **somente uma chave primária** pode ser definida, e ela pode ser composta por um ou mais campos (conhecida como chave primária composta), mas ainda será considerada **uma única chave primária**.

**68 - Julgue o item seguinte, referente a integridade referencial, metadados e modelagem multidimensional. Metadados e dicionário de dados têm a mesma função: fornecem informações detalhadas sobre os dados armazenados em um banco de dados.**

> 
Errado

Metadados são dados sobre os dados. Eles descrevem e fornecem informações contextuais sobre os dados armazenados, como o formato, o tipo de dado, as regras de validação, as relações entre tabelas, o significado dos campos, entre outros.

O dicionário de dados é uma **ferramenta ou recurso técnico** dentro de um sistema de gerenciamento de banco de dados (SGBD) que contém informações estruturadas sobre os objetos do banco de dados, como tabelas, colunas, índices, triggers, views, e as permissões dos usuários.

**84 - Com base em modelos e integração de dados, julgue o item que se segue. Uma das técnicas utilizadas em ETL é a separação, conforme a qual um dado do tipo texto pode ser dividido em textos menores.**

> Correto.

Algumas técnicas utilizadas:

> ![[Datawarehouse e Modelagem Dimensional synced block]]

**87 - Utilizada na transformação de dados, a técnica de derivação vincula dados semelhantes de diferentes fontes de dados. **

> Errado

Derivação significa a criação de novos dados a partir dos campos existentes.

**91 - A IA generativa utiliza modelos de base treinados para realizar tarefas gerais, como, por exemplo, técnicas de distribuição de probabilidade.**

> Gabarito da banca: Certo

No entanto,

Os modelos generativos utilizam técnicas relacionadas a distribuições de probabilidade para prever a próxima parte de uma sequência de dados (como a próxima palavra em uma frase) ou para gerar novos dados que imitam a distribuição dos dados de treinamento. 

Ou seja,

> Questão mal redigida.
> 
> **Correto: **IA generativa utiliza técnicas de distribuição de probabilidade para realizar tarefas gerais e não o contrário.