---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2024-10-23T07:46:00
Owner:
  - Eduardo Quinalha
---
> [!tip] 💡
> **OLTP está para bases transacionais (Operacionais)** assim como
**OLAP está para datawarehouses (bases analíticas)**

# Mapa Mental

![[DW.png]]

# OLTP

- **Transacional**
- **Associado às bases de dados operacionais**
- Foco no nível operacional
- Alta velocidade na manipulação
- Ineficiente para análises gerenciais
- Dados estruturados em modelo relacional normalizado
- Armazenamento em SGBD’s convencionais
- Dados voláteis, passíveis de exclusão e modificação

# OLAP

- **Analítico**
- **Associado ao datawarehouse**
- Foco no nível estratégico
- Otimização para leituras e geração de relatórios gerenciais
- Dados estruturados em modelagem dimensional
- Armazenamento em datawarehouses
- Tomada de decisão
- Dados não voláteis
- É permitido apenas inserção e leitura dos dados

## Categorias

- MOLAP
	- Dados armazenados em formato multidimensional
	- Pré-agregados para acelerar o desempenho
	- **otimizado para consultas e análises rápidas**
- ROLAP
	- Os dados são armazenados em bases relacionais tradicionais
	- As visões multidimensionais são criadas virtualmente
	- Possibilita maior flexibilidade
	- Menor desempenho em consultas analíticas (OLAP)
	- apresentam um **desempenho de carga** mais eficiente
	- O desempenho das consultas em ROLAP depende do tipo de informação requisitada e da complexidade das consultas, pois utiliza o banco de dados relacional subjacente, que pode não estar otimizado para acessos analíticos.
- HOLAP
	- Híbrido
	- Visa combinar as melhores características dos dois modelos anteriores

ROLAP --> BD relacional

**MOLAP** --> BD multidimensional

HOLAP --> ROLAP + MOLAP

DOLAP --> Ferramenta desktop para consultas

WOLAP --> Ferramenta web para consultas

**SOLAP** --> Integração entre ferramenta que utiliza informações geográficas( como o GIS) e OLAP

GIS --> Ferramenta de BD que permite trabalhar com informações geográficas.

banco de dados multidimensional especializado em Sistema de Informações Geográficas -- > MOLAP e SOLAP

Data Warehouse implementado com banco de dados relacional  --> ROLAP  ( FALTOU ESSE NA QUESTÃO)

## Operações OLAP

- **SLICE**
	- Seleção de dados em 1 dimensão
- **DICE**
	- Seleção de dados em 2 ou mais dimensões
- **ROLL-UP / ****DRILL-UP**
	- Agregação de dados - maior generalização, menor detalhe
- **DRILL-DOWN**
	- Desagregação de dados - menor generalização, **maior detalhe**
- **ROTATION / PIVOT**
	- Permite visualizar os dados sob uma nova perspectiva, sem reduzir/aumentar o escopo dos dados. (Ex: inverter as dimensões entre linhas e colunas).

# DataWarehouse

- Conjunto de banco de dados relacionado de forma consolidada
- Banco de dados para fins analíticos
- Geralmente possui um número menor de usuários em comparação com as bases operacionais
- **Visão conceitual multidimensional**
	- Não existe limitações para a quantidade de dimensões
- Arquitetura cliente/servidor
	- Heterogeneidade no lado do cliente
- Níveis de agregação ilimitados
- Coleção de dados, orientada por assunto, não volátil, integrada
- Histórico de dados
- Não é a solução ideal para dados não estruturados
- Custo elevado
- Obsolescência acelerada
- Dados estáticos

![[Untitled 706.png]]

![[Untitled 707.png]]

## Características de DW

- Orientado por assunto
- Integrado
	- dados de várias fontes
	- Visão unificada e consistente dos dados
	- Dados de diferentes fontes são limpos, transformados  e integrados
- Variação no tempo
	- Dados armazenados ao longo do tempo
	- Permite análises históricas e de tendências
- Não volatilidade
- Granularidade
- Credibilidade dos dados

# Tipos de DW

## EDW

- Corporativo
- Abrange toda a corporação
- Atende todos os níveis de negócio

## ODS

- Operational Data Store
- **Armazenamento temporário dos dados que estão migrando das bases operacionais para o DW**
- Tem caráter temporário (curto prazo)
- Permite consultas sobre os dados mais recentes
- Tipo intermediário de banco de dados
- Integra dados de várias fontes
- Combina OLTP com OLAP
- Mantido a curto prazo
- Usado para
	- Integrar dados
	- Suportar decisões operacionais
	- Resolver conflitos de dados
	- Apoiar processos de negócio
- Atualizado em tempo real
- Contém apenas dados atuais
- Otimizado para leitura

### ODS vs Staging Area

- ODS é utilizado para realizar limpeza, integração e alinhamento dos dados de diversas fontes, antes de serem carregados no DW
	- Operações de baixa latência
	- Permite consultas
- SA é o local onde os dados são preparados para carga no DW
	- SA é temporária e não é projetada para consultas ou atualizações frequentes

## DM

- Data Mart
- Escopo **departamental**
- Pode ser um subconjunto do DW

### Vantagens dos Data Marts sobre DW

- Desempenho
- Relevância
- Facilidade de uso
- Implantação rápida

![[Untitled 708.png]]

Os dados são copiados das bases operacionais para a Staging area. Nesta fase, somente os dados de interesse são transferidos, por isto a staging area é uma base menor do que a base operacional. Esta fase é o **ETL.**

Em seguida, os dados podem ser transferidos a um ODS ou diretamente ao EDW.

![[Untitled 709.png]]

No processo de Datawarehousing, as chaves primárias das bases transacionais são convertidas

# Arquiteturas de DW

- **Data Marts independentes**
	- Podem ter definições de dados inconsistentes (unidades diferentes)
	- Níveis de granularidade diferentes
	- Arquitetura mais simples e barata
- **Barramento de Data Mart (Kimball) - Botton Up**
	- Não há independência entre Data Marts
	- DMs individuais são interligados por um middleware
	- Consistência nos dados (no nível de metadados)
	- O desempenho pode ser prejudicado
- **Hub and Spoke (Inmon) - Top down**
	- Infraestrutura escalável e sustentável
	- DW centralizado e vários DM dependentes do DW
	- Permite customização fácil de interfaces de usuário e relatórios
	- Os dados são alimentados a partir do hub central para os respectivos Data Marts.
- **DW Centralizado**
	- Similar ao Hub Spoke
	- Não há DMs dependentes
	- Reduz a quantidade de dados a ser transmitido
	- Simplifica o gerenciamento e administração dos dados
	- A desvantagem potencial de um DW centralizado é que ele pode ser mais difícil de escalar à medida que a quantidade de dados aumenta
- **DW Federado**
	- Junção de várias fontes que incluem DW, DM e sistemas legados
	- Junta os dados em um único DW normalizado
	- Garantir a consistência e qualidade dos dados entre os diferentes sistemas pode ser complexo

## Quanto ao tipo de aquisição de dados

- Arquitetura controlada pela fonte: As fontes de dados transmitem novas informações.
- Arquitetura controlada pelo destino: O DW envia periodicamente solicitação para novos dados as fontes.

# Modelagem Dimensional

- Cubos de dados ou hipercubos
- Eventos: entradas individuais, composta por várias dimensões. Fato. Obtida pelo cruzamento das dimensões que o compõem.
- Dimensões: Representam as perspectivas (na prática são atributos)
- Hierarquia: Granularidade da dimensão. Por exemplo, para a dimensão tempo, a hierarquia é Ano → Semestre → Meses → dia → Hora → ….
	- Possibilidades de agregação

## Tabelas Fato e Dimensões

![[Untitled 710.png]]

![[Untitled 711.png]]

![[Untitled 712.png]]

### Tabela Fato

![[Untitled 713.png]]

- A tabela fato armazena as **medidas**
	- **Tipos de medidas**
		- **Aditivas**: Podem ser agrupadas em qualquer das dimensões. Por exemplo: total de vendas, média de vendas (por dia, mês, ano, etc…)
		- **Semi-aditivos: **Informações que não fazem sentido quando agrupadas em algumas das dimensões. Exemplo: soma do saldo da conta por 1 mês (não faz sentido). Soma do saldo das contas de todos os clientes em um dado instante (faz sentido)
		- **Não aditivas:** Não fazem sentido quando agrupadas em nenhuma das dimensões
- As dimensões estão em tabelas separadas
- A ligação entre a tabela fato e as dimensões é feita por meio de chaves estrangeiras (na tabela fato) que apontam para as tabelas dimensões

![[Untitled 714.png]]

- A chave primária da tabela fato é feita pela composição das chaves estrangeiras das tabelas dimensões: PK_F = (PK_T, PK_P, PK_G)
- **A cardinalidade entre as tabelas dimensão e a tabela fato são 1:N**

![[Untitled 715.png]]

- Tabelas fato armazenam grande quantidade de registros
- **São normalizadas e sem hierarquia**
- Crescem verticalmente
- Geralmente os dados tem natureza quantitativa, valores numéricos
- **Podem existir tabelas fato, sem fato → Factless fact table. Onde o único registro é justamente o cruzamento entre as dimensões.**
- **Sempre haverá pelo menos uma dimensão tempo assciada a tabela fato**

### Tabela Dimensão

- Representam o contexto
- Descrevem medidas de uma tabela fato
- Possui, em geral, poucas linhas e muitas colunas (horizontal)
- Única coluna de chave primária, incorporada como chave estrangeira em qualquer tabela de fatos
- Descrições verbais
- **São desnormalizadas, grandes e com hierarquia**
- **Possuem chaves primárias simples**
	- **Não pode ser a chave primária natural**
		- Ligadas ao sistema de origem e sujeitas a regras de negócio
	- Não pode ser a chave do sistema operacional SGBD
	- Não podem ter ligação com as bases transacionais
	- Chaves artificiais, substitutas, artificiais ou sobrenaturais
	- Inteiros simples, incrementados a cada nova entrada
> [!note] 🔥
> Isto  é necessário porque um mesmo registro, na base operacional, pode sofrer atualizações ao longo do tempo. Na base analítica, os registros não podem ser atualizados, então uma nova entrada referente àquele registro será feita e, para não violar a unicidade da chave primária, uma nova chave substituta deverá ser gerada.

> [!note] 🔥
> Em geral em um SGBD as chaves são utilizadas para identificar uma linha distinta, única, de uma tabela. Com esta chave é possível criar referencias entre as tabelas, são as famosas “foreign key” ou “chave estrangeira”, “FK”. No “**Data Warehouse**” essa chave ganha o nome de **“Surrogate Key”** que é a chave utilizadas nas dimensões para se ligar a tabela fato. <u>Em resumo, a “Surrogate Key” é uma “Primary Key” localizada na dimensão</u>
> **Resumindo:** ela é a famosa sequence do banco de dados ou a sequência no Excel.
> 
> Uma Surrogate Key nada mais é que um campo com as características de uma Primary Key, e é gerada automaticamente na hora da carga, quando você carrega a dimensão no ETL.
> 
> Na fato, essa Surrogate Key vai ser uma Foreign Key, a chave que serve para relacionar os dados entre duas tabelas, sempre apontando para uma Primary Key em outra tabela, que no caso da , vai ser a Surrogate Key.
> 
> Assim, a tabela fato receberá apenas o código da Surrogate Key da linha que ela está referenciando e não os atributos.
> 
> **Conclusão:**
> 
> **A Surrogate Key**
> 
> ·        tem as características de uma Primary Key.
> 
> ·        é utilizada para referenciar a dimensão no fato
> 
> ·        é auto incremental
> 
> ·        é uma chave artificial
> 
> ·        é criada no Data Warehouse
> 
> ·        não pode se repetir
> 
> No entanto, é performático o uso de uma “Surrogate Key” em modelos transacionais para a conexão entre tabelas, sem a necessidade de chaves compostas que muitas vezes dificultam o entendimento e precisam ser pensadas para evitar erros em JOINS.
> 
> Outra vantagem é a utilização deste identificador principalmente para deleções ou atualizações, pois facilita muito a vida na montagem da clausula “WHERE”.
- Muitos atributos de texto e baixa cardinalidade (muitos atributos)
	- Descrições verbais
- Dimensão degenerada
	- Quando uma tabela dimensão não tem nenhum dado relevante além de sua própria chave, ela é colocada como um atributo simples na tabela fato, juntamente das demais chaves estrangeiras
![[Untitled 716.png]]
- **Flags, indicadores operacionais e abreviaturas devem ser complementadas nas tabelas dimensão com palavras de texto que têm significado quando visto de forma independente**
- Quando da ocorrência de múltiplos flags ou indicadores, de baixa cardinalidade, pode-se criar uma **dimensão junk** com as combinações destes.
	- Esta dimensão não precisa ter exatamente o resultado do produto cartesiano de todos os valores possíveis, mas somente aqueles para os quais existem ocorrências
- **Valores Nulos**
	- Na modelagem dimensional e no contexto de Data Warehouse, a presença de atributos NULL em tabelas dimensão é **possível, mas não recomendável**.
	**1. Motivos para evitar atributos NULL:**
	- **Inconsistência:** Atributos NULL podem dificultar a análise de dados e gerar resultados inconsistentes.
	- **Perda de informação:** A presença de NULLs representa a perda de informação potencialmente valiosa para a análise.
	- **Dificuldade na interpretação:** Dificulta a interpretação dos dados e a identificação de padrões e insights.
	**2. Exceções à regra:**
	Em alguns casos específicos, a presença de NULLs em tabelas dimensão pode ser aceitável, como:
	- **Atributos não aplicáveis:** Quando um atributo não se aplica a um registro específico da dimensão.
	- **Dados históricos incompletos:** Quando os dados históricos não foram completamente coletados ou registrados.
	**3. Estratégias para lidar com atributos NULL:**
	- **Exclusão:** Remover registros com atributos NULL da tabela dimensão.
	- **Imputação:** Preencher os valores NULL com valores estimados ou imputados, utilizando técnicas estatísticas ou de aprendizado de máquina.
	- **Criação de uma nova dimensão:** Criar uma nova dimensão para armazenar os valores NULL, separando-os da dimensão principal.
	**4. Considerações:**
	- A decisão de permitir ou não atributos NULL em tabelas dimensão deve ser tomada com cuidado, considerando os impactos na qualidade dos dados e na análise.
	- É importante documentar as razões para a presença de NULLs e as estratégias utilizadas para lidar com eles.
	- A análise de dados deve levar em consideração a presença de NULLs e seus impactos nos resultados.
- Snowflaked Dimension → Dimensão normalizda, associada a outras tabelas dimensões

![[Untitled 717.png]]

- Slowly Changing Dimension
	- Técnica de atualização da tabela dimensão
	- Tipo 0 - Alteração na base transacional não necessita atualizar a base analítica
	- Tipo 1 - A alteração na base transacional implica em uma **substituição** na tabela dimensão
		- Único caso de atualização de dado em DW
		- Perde-se o histórico
	- Tipo 2 - Inserção de uma nova linha na tabela dimensão
		- Mantém o histórico anterior
		- Novos registros na tabela fato vão apontar para o novo valor da tabela dimensão
		- Uma boa prática é associar cada novo registro relacionado com a data de início e fim de sua vigência
![[Untitled 718.png]]
	- Tipos 3, 4 e 6 (o 5 não existe)
		- Tipo 3 - Adiciona nova coluna
			- Permite manter as atualizações no mesmo registro
		- Tipo 4 - Tabela adicional para registro das alterações
		- Tipo 6 - Híbrido, combinação de todas as anteriores

## Esquemas

### Modelo Estrela

- Tabelas dimensão ligadas diretamente à tabela fato
- Maior simplicidade e desempenho
- **Tabelas dimensões desnomalizadas**
- Redundância de dados
- Cardinalidade 1:N com a tabela fato
- Ocupa mais espaço de armazenamento

![[Untitled 719.png]]

### Modelo Floco de Neve

- Reduz o espaço ocupado pelo armazenamento
- **Tabelas dimensão normalizadas**
- Complexidade de entendimento do modelo
- Menos performático para consultas

![[Untitled 720.png]]

### Modelo constelação / Multi estrela

- Algumas tabelas dimensão servem para mais de uma tabela fato

![[Untitled 721.png]]

## Tipos de tabela fato

- **Transacional**
	- Cada linha da tabela fato representa uma transação da base operacional. Pode ser de forma integral ou apenas os atributos de interesse.
	- Maior nível de granularidade
	- Evento de medição em um ponto do espaço e tempo
	- Granularidade atômica → Mais expressivas
	- Geralmente utilizam métricas aditivas
	- Exemplo: Tabela fato de vendas que armazena a ocorrência de uma venda
- Agregada
	- Acumula um número de transações em um registro da tabela fato
	- Acelera o desempenho das consultas
	- Sumariza dados de outra tabela fato
- Consolidada
	- Combina diversas relações de uma base operacional em um registro da tabela fato
	- As tabelas devem ter o mesmo nível de granularidade
	- Combina fatos de vários processos em uma única tabela fato consolidada
- **Snapshot periódico**
	- Resume eventos ao longo de um período
	- O nível de granularidade é o período e não o evento (transação)
	- Exemplo: Controle de estoque
- **Snapshot acumulado**
	- Resume os eventos que ocorrem em etapas de medição previsíveis entre o início e o fim de um processo
- Factless

## Implementações

- Um banco de dados multidimensional pode ser implementado de duas formas
	- Estrutura de dados multidimensional → Matrizes de n dimensões → Cubos OLAP
	- Estrutura de dados relacional → Tabelas → Star Schema

## Operações

- **Operação fatiar (“*****slice*****”)** - seleciona dados de uma única dimensão de um cubo OLAP;
- **Operação cortar um subcubo (“*****dice*****”)** - extrai um subcubo do cubo original executando uma operação de seleção em duas ou mais dimensões;
- **Operação de agregação (“*****roll-up*****”)** - é a combinação de células de uma ou mais dimensões definidas num cubo. Uma forma de agregação usa o conceito de associação hierárquica com uma dimensão para atingir um nível maior de generalização;
- **Operação de “*****drill-down*****” **- é o reverso da agregação (“*roll-up*”), implica em examinar dados com algum nível maior de detalhe;
- **Operação de rotação (“*****rotation*****”)** - permite visualizar dados de uma nova perspectiva."

# ETL

- **Conjunto de processos para trazer dados de sistemas OLTP para um data warehouse**
	- Atualmente considera-se que os dados são oriundos não só de bases OLTP, mas de fontes variadas
	- A principal função da integração de dados ou ETL é **obter dados** de onde eles residem atualmente, **alterando-os para que sejam compatíveis **com o formato desejado e **colocando-os no sistema de destino.**
- Trata-se do processo mais crítico e demorado na construção de um DW
- Consome o maior orçamento e tempo de desenvolvimento
- Pode ser feito de forma síncrona, assíncrona, física ou virtualmente
- Extract → Staging Area → Transform & Load → DW
![[Untitled 722.png]]
- Pode ser executado em lote ou tempo real
- De forma síncrona ou assíncrona

## Backroom

- A criação dos sistemas ETL é uma atividade de back room que não é muito visível para os usuários finais
- Ela consome facilmente 70% dos recursos necessários para a implementação e manutenção de um data warehouse típico.
- Na maioria dos casos, a “sala dos fundos” e a “sala da frente” estão em máquinas diferentes, dependem de estruturas de dados diferentes e são gerenciadas por diferentes equipes de TI.

![[Untitled 723.png]]

- **Nenhum serviço de consulta é fornecido no back room**

## Staging Area

- Local acessível apenas a profissionais experientes em integração de dados
- É onde é feito a preparação dos dados
- A preparação quase sempre implica em um** armazenamento físico temporário** dos dados.

![[Untitled 724.png]]

# Processo de ETL

## Extração

- 1- **Data profiling **
	- Análise dos dados a fim de descrever seu conteúdo, consistência e estrutura
	- Um simples exemplo de data profiling é um SELECT DISTINCT em uma tabela a fim de avaliar a variedade dos dados
- 2- **Sistema de captura das alterações nos dados**
	- Capacidade de transferir apenas alterações relevantes (CDC)
	- Técnicas utilizadas:
		- Audit Columns
		- Timed Extracts
		- Full Diff Compare
		- Database Log Scraping
		- Message Queue Monitoring
- 3-** Sistema de extração**
![[Untitled 725.png]]

## Limpeza e Conformidade de Dados

- **4 - Sistema de limpeza de dados**
	- Correção dos dados sujos
- **5 - Esquema de eventos de erro**
	- Esquema dimensional centralizado que registra eventos de erro em qualquer lugar do fluxo ETL
- **6 - Dimensão de auditoria**
	- Contexto de metadados no momento específico em que uma linha é criada
- **7 - Sistema de deduplicação**
	- Evitar redundâncias desnecessárias
- **8 - Sistema de conformidade**
	- Ajustes e verificações nos dados

### Técnicas

![[Datawarehouse e Modelagem Dimensional synced block]]

## Integração de dados (Data Integration)

- Data Mapping
	- Descreve qual campo de origem é mapeado para qual campo de destino
- ETL versus ELT
	- São duas abordagens
	- No ELT os dados são transformados já no destino
	- **No ELT o armazenamento de destino pode ser um data lake**
	- O ETL é mais adequado para grandes quantidades de dados
- Agendado e processado
	- As transformações podem ocorrer tanto em lote como em tempo real
- Master Data Management
	- Processo de unir os dados para criar uma versão única, através de múltiplas fontes

## Entrega

- **9 - Gerenciador da alteração lenta da dimensão (SCD - Slowly changing dimension)**
	- Determina como manipular um valor de atributo alterado e que já havia sido armazenado no DW
	- As respostas possíveis são:
		- Tipo 1 - overwrite
		- Tipo 2 - new row
		- Tipo 3 - new column
- **10 - Gerador de chave substituta (Surrogate key)**
	- Deve ser independente da instância do banco de dados
	- Deve ser capaz de atender clientes distribuídos
- **11 - Gerenciador de hierarquia**
	- As hierarquias coexistem na mesma dimensão, nos atributos dela
	- Podem ser fixas ou irregulares
		- Fixas: número consistente de níveis, preenchida como atributos de dimensão separados para cada um dos níveis
		- Irregulares: profundidade indeterminada. É necessário a utilização de uma tabela de ponte.
- **12 - Gerador de dimensões especiais**
	- Dimensões JUNK
		- Compostas por texto e flags deixadas na tabela fato depois de removidos os atributos críticos
	- Mini Dimensões
	- Shrunken (reduzidas)
- **13 - Construtor de tabelas fato**
	- Tabelas fato contém as medidas
	- Tipos
		- Transacional
			- Maiores e mais detalhadas
			- A granularidade está a nível de evento
		- Snapshot periódigo
			- A granularidade representa um período
			- Periodicidade diária, semanal ou mensal
			- Uso típico em saldos
		- Snapshot acumulado
			- Representa o status atual, em evolução, de um processo que tem início e fim definidos
- **14 - Pipeline de chave substituta**
	- As surrogate keys devem manter a integridade referencial
- **15 - Construtor de tabelas de ponto de dimensões multivaloradas**
	- Usadas principalmente quando a hierarquia é de profundidade variável ou desconhecida
- **16 - Manipulador de dados atrasados**
- **17 - Sistema de gerenciamento das dimensões**

# DSS e EIS/ESS

- DSS
	- Decission Support System
	- Informações que suportam a tomada de decisão
- EIS / ESS
	- Executive Information System / Executive Support System
	- Especialização do DSS

# BI

- Componentes
	- **Data Warehouse (DW) **com suas fontes de dados; 
	- **Business Analytics,** uma coleção de ferramentas para manipulação, mineração, análise de dados do DW; 
	- **Business performance management (BPM)** para monitoramento e análise de performancee
	- I**nterface com o usuário** (por exemplo, um dashboard).
- BPM
	- Business Performance Management (diferente do Business Process Modelling)
	- Evolução do conceito de BI
	- Permite medição e monitoramento
	- Baseado em BSC (Balanced Scorecard) e Dashboards
	- Aplicação top-down da estratégia corporativa.
