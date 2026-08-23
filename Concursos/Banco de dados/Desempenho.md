---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2026-07-27T06:36:00
Owner:
  - Eduardo Quinalha
---
> [!note]+ # Mapas Mentais
> ![[Otimizao_de_SQL.png]]

# Índices

[https://www.youtube.com/watch?v=Ujl67TEXRKs](https://www.youtube.com/watch?v=Ujl67TEXRKs)

[http://www.bosontreinamentos.com.br/bancos-de-dados/o-que-sao-indices-em-bancos-de-dados-indexacao-em-tabelas/](http://www.bosontreinamentos.com.br/bancos-de-dados/o-que-sao-indices-em-bancos-de-dados-indexacao-em-tabelas/)

A exclusão de índices desnecessários pode resultar em ganhos de desempenho, pois reduz a sobrecarga associada à manutenção e atualização desses índices. Além disso, a remoção de índices irrelevantes pode diminuir o tempo de atualização dos dados, acelerar as operações de inserção e exclusão e reduzir a quantidade de espaço em disco ocupada pelo banco de dados.

> [!tip] 💡
> No processo de análise de desempenho de um banco de dados, a análise de **planos de execução **pode revelar situações em que a exclusão de índices pode levar à melhoria do desempenho do banco de dados.

🔥O uso de índices em consultas SQL pode provocar melhoria no desempenho em cláusulas como:

1. **WHERE**: O uso de índices pode acelerar a busca por registros que atendam a determinadas condições especificadas na cláusula WHERE. Isso permite que o banco de dados localize os registros relevantes mais rapidamente, reduzindo a quantidade de dados a serem processados.
2. **JOIN**: Quando há operações de junção entre tabelas, o uso de índices nas colunas envolvidas nas condições de junção pode melhorar o desempenho das consultas. Os índices podem facilitar a correspondência entre os registros das tabelas envolvidas, evitando uma busca exaustiva e acelerando a operação de junção.
3. **ORDER BY:** Em consultas que requerem uma ordenação específica dos resultados, o uso de índices nas colunas de ordenação pode melhorar o desempenho. Os índices ordenados permitem que o banco de dados recupere e retorne os resultados na ordem desejada sem a necessidade de uma etapa adicional de ordenação.
4. **GROUP BY**: O uso de índices nas colunas envolvidas na cláusula GROUP BY pode melhorar o desempenho em consultas que requerem agregação de dados. Os índices podem ajudar a agrupar os registros com base nos critérios especificados e acelerar o processo de agregação.
5. **DISTINCT:** Índices podem ser utilizados para acelerar a consulta DISTINCT pois o banco pode utilizá-lo para identificar rapidamente valores únicos

> [!tip] 💡
> Por padrão, os SGBD’s criam índices automaticamente para campos:
> - Chave primária
> - Chave estrangeira
> - UNIQUE

## Categorias

### Clusterizados (Primário)

- Os Índices clusterizados **alteram a forma como os dados são armazenados em um banco de dados**, pois ele classifica as linhas de acordo com a coluna que possui o índice. 
- **Uma tabela só pode ter um índice clusterizado. **
- Geralmente ele está na coluna que é **chave primária** da tabela ou, em sua ausência, em uma coluna UNIQUE.
- **Caso uma tabela não possua um índice clusterizado, suas linhas são armazenadas em uma estrutura não-ordenada chamada de heap.**

### Não clusterizados (Secundário)

- Em um índice não-clusterizado a forma como os dados são armazenados em disco não é alterada, e um objeto separado é criado na tabela, apontando para as linhas da tabela original após a busca. 
- Este tipo de índice se baseia em valores-chave.
- Uma tabela pode ter vários índices não-clusterizados.
- Os índices secundários melhoram o desempenho das consultas que usam chaves diferentes da chave de procura do índice primário. 
- O projetista do banco de dados deve decidir quais índices não-clusterizados devem ser criados com base na estimativa da frequência de consultas e atualizações dos registros.

## Índices Ordenados

- **Primário**
	- Campo chave de ordenação
	- Pode ser
		- Esparso
			- Nem todas as entradas estão presentes no grupo
			- Normalmente cada entrada aponta para o início de um bloco, onde o valor desejado poderá ser encontrado
			- Por exemplo, ordem alfabética
		- Denso
			- Todos os valores de pesquisa estão presentes no índice
- **Agrupamento**
	- Repetição de valor no campo de agrupamento
- **Secundário**
	- Qualquer campo não ordenado
	- Denso

## Tipos de Índices (estruturas)

- B-Tree / B+-Tree
	- Árvores balanceadas
	- Tipo mais comum
	- Acesso eficiente para consulta de intervalos
	- Atualização relativamente eficiente
	- Seu desempenho pode degradar conforme o arquivo aumenta de tamanho
	- Valores de baixa cardinalidade (sim/não, masculino/feminino, cores, etc) não se beneficiam deste tipo de índice
![[Untitled 733.png]]
- Bitmap
	- Eficiente para conjunto de valores ou baixa cardinalidade
	- Menos eficiente para conjuntos grandes
	- Sua atualização é pouco performática
	- Emprega lógicas de comparação a nível de bits nos campos classificadores
- Hashing
	- Eficiente para acesso a linhas específicas (não intervalos)
	- Pode ser utilizado com eficiência em JOIN
- Funcional
	- Baseia-se no resultado da aplicação de uma função sobre os valores da linha

# Desempenho de BD

- Workload
	- Varia drasticamente de um dia para outro
	- Algumas vezes pode ser previsível outras não
- throughput
	- Capacidade do computador para processar os dados
	- Ligado ao hardware (CPU, IO, memória, capacidade de paralelismo)
- recursos
	- ferramentas de hardware e software disponíveis ao sistema
	- O aumento da **memória principal** (RAM) pode, de fato, melhorar a performance geral do sistema ao facilitar o armazenamento de mais páginas de dados em memória para acesso rápido, reduzindo as operações de entrada/saída com o disco.
	- Ao aumentar a memória principal, o sistema pode processar mais transações de modo mais rápido, o que consequentemente leva a um **maior volume de registros no *****log*****.**
	- Se o subsistema responsável pelo processamento de *log* não for adequado, ou seja, **se o disco for lento** ou se a banda passante do disco não for suficiente para a quantidade incrementada de dados para serem gravados no *log*, então isso se tornará um **gargalo de desempenho**.
- otimização
	- Recursos internos do próprio SGBD
	- Consultas SQL
- contenção
	- Acesso múltiplo a um único recurso de forma conflitante
	- Quando duas consultas tentam modificar o mesmo dado, o SGBD faz uma contenção
	- diminui o throughput

> [!tip] 💡
> O desempenho do DB pode ser definido como a **otimização** de uso dos **recursos** para aumentar o **throughput** e minimizar a **contenção**, permitindo a maior **carga de trabalho** possível

- Problemas de performance
	- Consultas SQL
		- **Cláusula WHERE:** Quando na cláusula where não houver alguma coluna que seja índice, é necessário fazer uma varredura completa da tabela
		- Falta de índices apropriados
		- Excesso de índices
		- Junção de tabelas em ordem não ideal
		- Junção feita pela aplicação e não por SQL
		- Subconsultas (exists, not exists)
		- Ordenação e filtros desnecessários (order by, group by, distinct, union)
- **Tunning**
	- Ajuste na metodologia
		- 1- Design do BD
			- Determinar se os componentes críticos precisam ser particionados ou realocados para diferentes diretórios/pastas (tablespaces, data files, logs)
		- 2- Aplicação de BD
			- Funcionamento adequado de stored procedures, triggers e a necessidade dos mesmos
		- 3- Gerenciamento de memória
		- 4- Gerenciamento de I/O
		- 5- Contenção
			- Como o BD lida com acessos simultâneos

# Otimização de consultas SQL

Algumas cláusulas SQL podem causar perda de desempenho em consultas, especialmente quando utilizadas de forma inadequada ou em cenários específicos. Aqui estão algumas cláusulas que podem afetar negativamente o desempenho:

6. LIKE: O uso da cláusula LIKE com padrões de busca que começam com caracteres curinga ("%") pode causar perda de desempenho. Por exemplo, o uso de "LIKE '%abc'" exigirá uma busca exaustiva em toda a coluna, pois não é possível utilizar um índice para essa operação.
7. ORDER BY: A cláusula ORDER BY pode causar perda de desempenho, especialmente quando aplicada a grandes conjuntos de dados. A ordenação requer uma etapa adicional de classificação dos resultados, o que pode ser custoso em termos de tempo e recursos, especialmente se não houver um índice adequado para a coluna de ordenação.
8. DISTINCT: A cláusula DISTINCT é usada para retornar apenas valores distintos em uma consulta. No entanto, isso pode levar a uma perda de desempenho, pois requer a remoção de duplicatas dos resultados, o que pode ser um processo intensivo em termos de recursos, especialmente em grandes conjuntos de dados.
9. Funções de agregação: O uso de funções de agregação, como SUM, COUNT, AVG, MAX, MIN, em consultas pode ter um impacto negativo no desempenho. Essas funções exigem o processamento de todo o conjunto de dados para calcular o resultado, o que pode ser lento em grandes tabelas.
10. JOINs complexos: O uso de JOINs complexos, envolvendo múltiplas tabelas e condições complexas, pode causar perda de desempenho. O banco de dados precisa executar operações de junção e filtragem em várias tabelas, o que pode exigir um processamento extenso e impactar o desempenho da consulta.

![[Untitled 734.png]]

- Plano de execução: encontrar o melhor caminho para os dados
- Forma mais segura de otimização pois não compromete outras aplicações e componentes
- Envolve principalmente melhorias nas cláusulas FROM e WHERE
- FROM → primeiro tabelas menores, por último as maiores
- JOIN → Idem
- WHERE → condições mais restritivas por último (o Otimizador lê a cláusula Where ao contrário, na maioria dos SGBD’s)

```sql
SELECT *
FROM  TABLE 1,
			TABLE 2,
			TABLE 3
WHERE TABLE1.COLUMN = TABLE3.COLUMN
	AND	TABLE2.COLUMN = TABLE3.COLUMN
	AND CONDITION 1
	AND CONDITION 2
```

- Índices (onde usar)
	- Chaves primárias e estrangeiras
	- Colunas frequentemente utilizadas para JOIN
	- Colunas frequentemente utilizadas como condições
	- Colunas que têm elevada porcentagem de valores exclusivos
- OR → A cláusula IN possui um desempenho maior
- Evitar a cláusula HAVING, ORDER BY, GROUP BY
- Stored Procedures: Cláusulas SQL são compiladas antes da execução. Stored procedures permanecem armazenadas já compiladas, o que agiliza a execução pelo SGBD
- Desativar índices para grandes operações de gravação em lote. Quando existe um índice e uma linha é modificada, são feitas duas operações de gravação, uma na própria tabela e outra no índice para manter este atualizado. Uma forma de aumentar o desempenho é desabilitar o índice durante uma grande operação de atualização em lote. Esta técnica também reduz a fragmentação dos índices

## Tipos de algoritmos de junção

- **Laço Aninhado:** 
	- Não requer índices e aceita qualquer condição de junção. Examina todos os pares das relações. O total de varreduras será $nr * ns$ (para cada registro de r, uma varredura completa de s)
	- É o pior em termos de eficiência
- **Loop único: **
	- Requer um índice ou chave de hash para um dos atributos de junção da tabela A. Recupera todos os registros de B e depois usa o índice para verificar os que atendem à condição
- **Sort-merge: **
	- Os atributos de junção A e B devem estar fisicamente ordenados
	- Varre ambas as tabelas R e S simultaneamente
	- Mais eficiente
- **Partição hash**
	- Os registros de A e B são separados em arquivos menores, utilizando-se uma função hash
	- Depois é feito o casamento dos registros correspondentes

---

# Formas de otimização de consultas SQL (segundo a CESPE)

- Transformar condições NOT em uma expressão positiva
- Evitar DISTINCT
- Evitar o uso de tabelas de resultados temporárias
- Ordenar corretamente as tabelas na cláusula FROM (primeiro tabelas menores, por último as maiores)
- Substituir UNION ALL por UNION (remoção de duplicatas)
- Utilizar equijoins
- Remover funções da cláusula WHERE
- Remover colunas desnecessárias do SELECT