---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2024-09-05T15:05:00
Owner:
  - Eduardo Quinalha
---
# Componentes

- Instância
	- Processos em segundo plano
	- Memória que o SGBD utiliza para gerenciar operações do BD
- Arquivos
	- Onde os dados são armazenados
	- Dados
	- Redo Log
	- Controle
- Schema
	- Conjunto de objetos de BD que pertencem a um usuário
- Mecanismo SQL
	- Interpreta e executa instruções SQL
	- Oracle suporta SQL e PL/SQL
- Processos de fundo (Background)
	- Realizam tarefas de manutenção necessárias para operação do BD

# Instalação

- RAC (Real Application Clusters)
- Oracle Text

![[Untitled 157.png]]

## Oracle Universal Installer (OUI)

- OUI verifica automaticamente o computador
- Podem variam, dependendo de:
– Tipo de computador
– Sistema operacional
- MÌnimo de 1GB de memória física

![[Untitled 158.png]]

## Versões

![[Untitled 159.png]]

- **Enterprise Edition**
	- Versão robusta
	- Mais alto nível de funcionalidade e desempenho
	- Oferece
		- RAC
		- Oracle Data Guard
		- Oracle Advanced Security
		- Oracle Partitioning
	- Possibilita Data Warehouse
- **Standard Edition**
	- Versão simplificada
	- Recursos básicos a um custo menor
	- Suporta o RAC
- **Standard Edition One**
	- Descontinuada a partir do 12c
	- Versão ainda mais simplificada
	- Não trabalha em grid, apenas 1 servidor
- **Personal Edition**
	- Destinada a desenvolvedores individuais
	- Uso em única máquina, para fins pessoais ou educacionais
	- Inclui todos os recursos da Enterprise Edition, porém licenciada para uso em apenas um único computador

## Localização dos arquivos

- File System
	- Opção padrão
	- Arquivos gerenciados pelo sistema operacional
- Automatic Storage Management (ASM)
	- Arquivos em grupo de discos Oracle ASM
	- SGBD Oracle gerencia localização dos arquivos
	- Maior performance

## Identificadores de BD

- Identificador Global
	- Nome e identificação do BD (SID)

## Templates

- OLTP
- OLAP (DW)

# Autonomous Database

- Versão em nuvem
- Utiliza Machine Learning para facilitar o gerenciamento do SGBD
- solução 'self-driving', o que significa que ela realiza tarefas como provisionamento, correção de segurança, backup, recuperação e ajuste do banco de dados automaticamente
- Características
	- Autogestão
		- Atualizações
		- Ajuste de desempenho
		- Resolução de falhas
	- Autossegurança
		- Implementação automática das últimas atualizações de segurança
	- Autoreparo
		- Detecta e corrige automaticamente falhas
	- Elasticidade
	- Desempenho superior
	- Integração com ferramentas Oracle

# Estrutura Física

![[Untitled 160.png]]

## Datafiles

- Nível físico
- Extensão: `.dbf`
- Arquivo no sistema de arquivos do sistema operacional
- Armazenam todos os dados do usuário
- Podem existir em diferentes formatos
	- Tabelas
	- Índices
- Cada datafile pertence a um único tablespace
- Cada tablespace pode consistir de um ou mais datafiles
	- você pode ter um tablespace para dados de usuário, outro para dados do sistema e assim por diante, cada um com seus próprios conjuntos de datafiles.
- Características
	- Persistentes
	- Tamanho:
		- Pode ser determinado um tamanho fixo no momento da criação ou configurar para crescimento automático
	- Imutabilidade de localização
		- Uma vez criado um datafile, sua localização não pode mudar sem a interrupção do BD
- Comandos

```sql
CREATE TABLESPACE USERS_2 DATAFILE '/u01/oradata/users_2_01.dbf' SIZE 100m AUTOEXTEND ON NEXT 10g;

ALTER TABLESPACE USERS
	ADD DATAFILE '/u02/oracle/rbdb1/users03.dbf' SIZE 10M
	AUTOEXTEND ON
	NEXT 512K
	MAXSIZE 250M;
	
STORAGE (INITIAL 10G NEXT 1G)

CREATE BIGFILE TABLESPACE b1 DATAFILE 'd1.dbf' SIZE 40M AUTOEXTEND ON;

ALTER TABLESPACE tbs_03 ADD DATAFILE 'tbs_f04.dbf' SIZE 100K AUTOEXTEND ON;
```

## Arquivos de Log (ReDo Log)

-  usados para garantir a recuperação de dados em caso de falha
- **melhorar o desempenho do banco de dados.**
- arquivos **binários** que registram todas as mudanças feitas no banco de dados.
- não apenas as transações de usuários (como INSERT, UPDATE, DELETE), mas também ações que resultam em mudanças físicas e lógicas, como a criação e modificação de tabelas ou índices.
- Organizados em **grupos** de redundância
- as alterações de dados são primeiro escritas nos arquivos de Redo Log e, em seguida, escritas de maneira assíncrona nos datafiles
	- isso permite que o banco de dados responda a uma transação muito rapidamente, antes que todas as mudanças sejam refletidas nos datafiles.
	- Por isso melhora o desempenho do banco

### Multiplexação de Redo Logs

- O recurso de multiplexar um redo log (multiplexed redo logs) visa proteger contra uma falha envolvendo o próprio redo log. 
- Quando os redo logs são multiplexados, cópias idênticas das entradas de redo log são gravadas em vários membros de um grupo de redo log.
- Isso ajuda a garantir que, se um dos membros do grupo falhar, ainda haverá cópias válidas dos registros de redo log disponíveis nos outros membros
- Quando um redo log é multiplexado, é recomendado que todos os membros de um grupo sejam colocados em discos físicos distintos. Esta prática distribui a carga de E/S (entrada/saída) entre vários discos, reduzindo a probabilidade de falha em todos os membros do grupo devido a uma falha física em um único disco.
- 

## Arquivos de controle

- pequeno arquivo **binário** que registra o **estado físico** do banco de dados.
- Cada banco de dados Oracle tem pelo menos um arquivo de controle
	- normalmente há múltiplos arquivos de controle para proporcionar redundância.
- contêm várias informações sobre o SGBD, incluindo:
	- O nome do banco de dados e o timestamp de sua criação
	- Informações sobre os arquivos de dados e de redo log, incluindo o nome e o local de cada arquivo
	- O **SCN (System Change Number)** mais recente, que é um carimbo de data/hora que o Oracle Database usa para controlar as transações.
	- Informações sobre o backup e a recuperação, incluindo o RMAN (Recovery Manager) e informações sobre o arquivo de backup.
- são atualizados continuamente durante a sua operação
- **Se todos os arquivos de controle de um banco de dados forem perdidos, o banco de dados não poderá ser aberto.**

## Outros arquivos

- Trace Logs
	- Úteis para diagnóstico de problemas
- Arquivos de parâmetros
	-  contém as configurações
	- Tipos
		- SPFILE
			- Binário
			- Pode ser modificado dinamicamente com o BD em operação
		- PFILE
			- Texto
			- Modificado manualmente
			- Requer a reinicialização do SGBD

# Estrutura Lógica

![[Untitled 161.png]]

## Tablespaces

- Contêiner lógico para armazenar dados físicos
- Composto de um ou mais datafiles
- Fornece abstração entre os dados físicos e a forma como os dados são logicamente organizados\
- Tipos
	- `SYSTEM` 
		- Tablespaces de Sistema 
		- Obrigatória
		- **Armazena o dicionário de dados**
		- Dados de sistema
		- Metadados sobre a estrutura do BD
		- Todo banco tem um tablespace chamado SYSTEM
	- `SYSAUX`
		- Auxiliar para a System
	- `UNDO`
	- `TEMP`
	- Tablespaces de Usuário
		- Dados inseridos e gerenciados pelos usuários
		- Criados pelo DBA para armazenar objetos específicos como tabelas e índices
- Classificações
	- Tablespaces de dados
	- Temporários
- Podem ser gerenciados por SQL

## Segmento

- Divisão lógica de um tablespace que armazena um tipo específico de informação
- Permite a alocação de espaço de armazenamento para tipos de objetos específicos
- Tipos
	- Segmento de Dados
	- Segmento de Índices
	- Temporários
	- Undo (Rollback)

## Extensões

- Uma extensão é uma unidade contígua de espaço de armazenamento alocada para um segmento específico dentro de um tablespace
- O Objetivo é minimizar a fragmentação do armazenamento
- Quando um segmento é criado, ele é composto por pelo menos uma extensão.
- À medida que os dados são inseridos no segmento e o espaço disponível torna-se insuficiente, o Oracle automaticamente aloca extensões adicionais para o segmento a partir do espaço livre disponível no tablespace.
- Cada extensão é composta por um número contíguo de blocos de dados que têm o mesmo tamanho, o qual é definido quando o banco de dados é criado.

## Oracle Data Block

- menor unidade de armazenamento lógico
- Cada bloco consiste em um número específico de bytes de espaço em disco
- o tamanho do bloco é determinado no momento da criação do banco de dados
- geralmente é um múltiplo de 2 que varia entre 2KB e 32KB
- A escolha do tamanho do bloco pode ter um impacto significativo no desempenho do banco de dados e deve ser definida com base nos requisitos
de acesso aos dados.
- Cada bloco de dados é composto por três partes principais:
	- Cabeçalho do bloco
	- Diretório de tabelas
	- linhas

# Schema e Objetos de Schema

- Usuários e Schema são diferentes
- No entanto, cada usuário tem um schema com o mesmo nome que o nome do usuário

## Objetos de Schema

- Tabela
- Índice
- View
- Cluster
	- opção de armazenamento que permite armazenar várias tabelas juntas em um único bloco de dados, desde que essas tabelas compartilhem uma coluna comum
	- Melhora o desempenho de consultas que acessam dados de várias tabelas ao mesmo tempo
- Sinônimo

# Dicionário de Dados

- estrutura de metadados
- coleção de tabelas e visões de leitura que fornecem uma visão detalhada dos metadados do banco de dados
- acessível através de uma série de visões que começam com as letras **DBA_**, **ALL_** ou **USER_**
- permitem que você consulte os metadados do banco de dados usando o SQL padrão.
- Exemplo: `SELECT table_name FROM user_tables;`

## Visões do Dicionário de Dados

- **DBA_**
	- Informações sobre todos os objetos no BD
- **ALL_**
	- Objetos aos quais o usuário atual tem acesso, independente do schema ao qual pertencem
- **USER_**
	- Informações apenas sobre os objetos que residem no schema do usuário atual

# Tipos de Dados

## Nativos Oracle

- CHAR(N)
	- Máx 2000 Bytes
- VARCHAR(N)
	- Máx 4000 Bytes
- NCHAR(N)
- NVARCHAR2(N)
- NUMBER(p,s)
- NUMBER(N)
- NUMBER

### Char vs Varchar

- `CHAR` 
	- reserva um campo com o exato tamanho definido.
	- Caso o campo seja menor, o resto será ocupado com espaços
- `VARCHAR`
	- O tamanho do campo é flexível

## Complexos

- Coleções
	- VARRAY
		- Vetores de número especificado de elementos
	- Nested Tables
		- Tabelas armazenadas em uma linha de outra tabela
- LOB
	- BLOB
	- CLOB
	- NCLOB
	- BFILE
- Tipos de registro
	- Tipo de dados composto, personalizado
	- Número fixo de elementos, cada um com seu próprio tipo de dados
	- (Struct)

# Estrutura de Memória

- Composto de **SGA** (System Global Area), **PGA** (Program Global Area) e **UGA** (User Global Area)

![[Untitled 162.png]]

## SGA - System Global Area

- alocada quando um processo Oracle é iniciado.
- Existe uma SGA para cada instância
- **compartilhada** por todos os processos servidores
- contém informações necessárias para a execução do banco de dados
- Tem seu tamanho definido pelos parâmetros `SGA_MAX_SIZE` e `SGA_TARGET`
- Unidades de 4MB a 16MB
- Estruturas:
	- **Database Buffer Cache**
		- maior componente da SGA
		- armazena cópias dos blocos de dados mais recentes lidos dos datafiles
		- Armazenamento temporário dos dados trazidos do disco
		- Definido pelos parâmetros `DB_CACHE_SIZE` e `DB_NK_CACHE_SIZE`
	- **Shared Pool**
		- Library Cache: armazena as instruções SQL mais recentemente executadas
		- Data Dictionary Cache: 
			- Subconjunto das tabelas do dicionário de dados
		- Definido pelos parâmetros `SHARED_POOL_SIZE`
	- **Redo Log Buffer**
		- armazena informações de redo
		- Alterações mais recentes
	- **Large Pool**
		- Opcional
		- usado para operações que requerem grandes quantidades de memória
	- **Java Pool**
		- dados e instruções de sessão relacionados a **sessões Java** dentro do Oracle.
	- **Streams Pool**
		- bufferização de informações relacionadas a operações de fluxo de dados no Oracle
		- Armazena dados e estruturas de controle
		- **Usado em ambientes distribuídos**
		- Definido pelo parâmetro `STREAMS_POOL_SIZE`

## PGA - Program Global Area

- armazenar dados e informações de controle para processos do Oracle
- é particular para **cada processo de servidor**
- Contém uma área** para cada usuário** ativo na instância
- Estruturas
	- Área de classificação:
	- Sessão privada
	- Cursor

## UGA - User Global Area

- armazena informações de** sessão para um usuário específico.**
- cada usuário que se conecta a um banco de dados tem uma UGA associada a ele
- Em um sistema de arquitetura de **servidor compartilhado, a UGA é armazenada na System Global Area (SGA).**
- em um sistema de arquitetura de **servidor dedicado, a UGA é armazenada na Program Global Area (PGA)**

## In Memory

- Área opcional incorporada a SGA a partir da versão 12C
- Suplemento ao Buffer Cache
- Facilita consultas analíticas OLAP
- Funciona como um BD NoSQL Colunar

# Estrutura de Processos

- Todo usuário conectado executa dois módulos:
	- Aplicação ou ferramenta Oracle
		- Emite instruções SQL para o banco
	- Código do Servidor de BD
		- Código em execução em nome do usuário
		- Interpreta e processa informações SQL
![[Untitled 163.png]]

## Processos de Primeiro plano

- Interagem diretamente com os usuários e executam as tarefas solicitadas, como consultas e manipulações de dados.
- são responsáveis por executar as solicitações enviadas pelos usuários. 
- Esses processos **são criados a partir das sessões do usuário** e trabalham em conjunto com os processos de segundo plano para garantir o funcionamento adequado do banco de dados.
	- **User process**
		- Estes são os processos que os usuários iniciam ao se conectarem ao banco de dados. 
		- Eles lidam com a comunicação entre o banco de dados Oracle e as aplicações, gerenciando as solicitações dos usuários e enviando-as para os processos do servidor.
	- **Server process**
		- Criados para cada conexão de usuário, esses processos **tratam as solicitações de SQL enviadas pelos usuários. **
		- Eles leem os dados dos buffers de cache na SGA (System Global Area) ou, se necessário, do disco, e retornam os resultados para os usuários.
		- Dedicated
		- Shared

### **Processos de usuário**

- **Criados no momento em que o usuário se conecta ao banco**
- **Tipos**
	- Processo de servidor dedicado
		- Exclusivo por usuário
		- Adequado em aplicações em que o número de usuários simultâneos é pequeno
	- Processo de servidor compartilhado
		- Pool de processos servidor
		- Grande número de usuários simultâneos, com poucas requisições por usuário

### **Processos do Oracle Database**

- **Processos de Servidor**
	- Executam as solicitações dos usuários e retornam resultados
- **Processos de Segundo Plano**
	- Iniciados pelo SGBD
	- Executam tarefas como limpeza de memória e escrita em disco
	- Permanecem em execução enquanto o SGBD estiver em operação
- **Processos de Segundo Plano Obrigatórios**
	- Subconjunto dos processos de segundo plano
	- Essenciais para operação do BD
	- System Monitor SMON
	- Process Monitor PMON

## Processos de Segundo plano Obrigatórios

### PMON

- Inicializado junto com a instância
- Responsável por iniciar o rollback de transações quando um processo de usuário é interrompido
- Disponibiliza recursos em caso de um dos processos Oracle falhar

### SMON

- Trabalha em cima de arquivos de controle
- Atua a nível de sistema
- Abre conexão entre instância e o BD (físico)
- Verifica consistência e inicia a recuperação do BD

### DBWriter

- Responsável pela transferência dos dados do Database Buffer Cache para o disco

### LogWriter

- Gerencia o Redo Buffer
- Transfere as transações 

### CheckPointer

- Garante a consistência dos arquivos de dados e arquivos de controle
- Responsável pela SCN (system change number)
	- Número gerado a cada commit de uma transação bem sucedida
	- Representa o número da transação
- Atualiza cabeçalho das informações de status

### Recover Process

- Resolve falhas em transações distribuídas
- Mantém a consistência entre diversas instâncias de BD

## Processos de Segundo plano Opcionais

### ARC - Archive Process

- Persiste os Redo Logs em um storage offline

### CJQ - Job Queue Process

- Utilizado para gerenciar tarefas de usuário em segundo plano
- Em modo batch

### FBDA - Flashback Data Archiver Process

- Histórico de linhas de tabelas
- Utilizado para instruções DML

# Backup

- Físico
- Lógico

## Ferramentas

- Recovery Manager (RMAN)
	- Nativa
	- Backup físico e lógico
	- Permite duplicação do banco
- Data Pump
	- Movimentação de dados e metadados dentro e entre bancos de dados Oracle
	- Permite a criação de cópias de segurança lógicas
	- Suporta paralelização de tarefas
	- Suporta remapeamento (permite alterar a estrutura dos dados)

# Arquitetura Multitenant

- Criado a partir do 12c
- Permite a gestão centralizada de múltiplos bancos de dados
- O Oracle Multitenant permite que um Oracle Database funcione como um banco de dados de contêiner (CDB). 
- Suporta até 4096 PDB’s nas plataformas Exadata e Cloud
- Até 252 bancos nas demais plataformas

## Container Database (CDB)

- O **Container Database (CDB)** é um banco de dados que pode conter zero, um ou mais bancos de dados "plugáveis" (PDBs). 
- Ele serve como um contêiner que proporciona uma infraestrutura comum e compartilhada para múltiplos PDBs, permitindo o gerenciamento e operação de múltiplos bancos de dados de uma forma mais eficiente e consolidada.
- Um CDB é composto por três tipos de containers:
	1. **Root Container (CDB$ROOT)**: Este é o container raiz que contém as informações de configuração compartilhadas por todos os PDBs. Inclui metadados do sistema, dicionário de dados e outros componentes necessários para o funcionamento geral do CDB.
	2. **Seed Container (PDB$SEED)**: Este é um template de PDB pré-configurado usado para criar novos PDBs rapidamente. Ele não pode ser modificado diretamente, mas pode ser usado como base para criar outros PDBs.
	3. **Pluggable Databases (PDBs)**: Esses são os bancos de dados propriamente ditos que "plugam" no CDB. Cada PDB é um banco de dados isolado, com seu próprio conjunto de dados e esquema, mas que compartilha a infraestrutura do CDB.

## Pluggable Database (PDB)

- Um **Pluggable Database (PDB)** é um banco de dados independente que reside dentro de um CDB. 
- Cada PDB contém seus próprios dados de usuário, esquema, índices e outros objetos de banco de dados, mas compartilha os recursos de instância do CDB (como memória e processos de background).
- As principais características dos PDBs incluem:
	1. **Isolamento**: Cada PDB opera de forma isolada, o que permite um alto grau de segurança e controle sobre os dados e operações.
	2. **Facilidade de Gestão**: PDBs podem ser facilmente criados, clonados, plugados e desplugados de um CDB, permitindo uma gestão flexível e eficiente.
	3. **Economia de Recursos**: Compartilhando a infraestrutura do CDB, múltiplos PDBs podem ser operados com uma economia significativa de recursos em comparação com a execução de múltiplas instâncias de banco de dados separadas.
	4. **Movimentação Facilitada**: PDBs podem ser movidos entre diferentes CDBs com relativa facilidade, facilitando a administração e manutenção do ambiente de banco de dados.

# Replicação

## Data Guard

- Provê serviços para criar e gerenciar um ou mais bancos redundantes
- Faz o switch over
- Pode ser utilizado como backup tradicional também
- Oferece três tipos principais de bancos de dados standby: físico, lógico e snapshot

![[Untitled 164.png]]

### Primary Database

- Banco principal
- Pode ser:
	- Single Instance
	- Oracle Real Application (RAC) DB

### Standby Database

- Cópia da primary
- Podem existir **até 9 standby DB incorporados em uma config Data Guard**
- São mantidas pela transmissão do Redo Log
- Podem ser:
	- Físico
		- Cópia física idêntica ao banco principal
		- A nível de bloco físico no SO
	- Lógico
		- Contém a mesma informação lógica
		- A organização física pode ser diferente
		- A sincronização é mantida via SQL Apply, executando as transações SQL contidas no redo log

# Outros conceitos

## Pacote UTL_HTTP

O **UTL_HTTP** é um pacote PL/SQL que permite que o banco de dados realize chamadas HTTP para acessar recursos na web. Com este pacote, é possível enviar solicitações HTTP, receber respostas e manipular dados advindos dessas respostas. Sendo assim, ele é utilizado para interagir com serviços web e APIs, por exemplo.

## JSON

o Oracle Database 21c introduziu uma funcionalidade para armazenamento e manipulação de dados no formato JSON (JavaScript Object Notation). O tipo de dado **JSON** é uma extensão que permite armazenar documentos JSON diretamente em uma coluna de uma tabela da base de dados, facilitando operações com dados neste formato, que é amplamente utilizado para troca de informações entre sistemas e aplicações web.

## Sort Area

O Oracle  tem sua própria maneira de gerenciar o espaço de trabalho para operações de ordenação, conhecido como **sort area** ou *work area*.

é reservada durante a execução de operações que necessitam de dados ordenados, como `ORDER BY`, `GROUP BY`, criação de índices e merge joins. Se a quantidade de dados a ser ordenada excede a memória alocada para a *sort area*, o Oracle pode usar espaço em disco temporário para completar a operação.

 *sort area* é controlada por parâmetros de inicialização do Oracle, como `SORT_AREA_SIZE` e `SORT_AREA_RETAINED_SIZE`, que definem, respectivamente, o tamanho da área de ordenação e a quantidade de memória retida após a operação de ordenação.

As informações sobre o uso de espaço para operações de ordenação podem ser obtidas por meio de vistas de dicionário de dados do Oracle, como **V$SORT_SEGMENT** e **V$TEMP_SPACE_HEADER**, que fornecem detalhes sobre o uso de segmentos de ordenação e espaço temporário, respectivamente.

## SQLPlus

O comando **CONNECT** no SQLPlus é utilizado para estabelecer uma nova conexão com o banco de dados Oracle sem sair do ambiente atual do SQLPlus. Quando utilizado com a sintaxe `CONNECT username/password AS SYSDBA`, o comando permite que o usuário se conecte ao banco de dados com privilégios de administrador, conhecidos como **SYSDBA**. Este nível de acesso é necessário para realizar tarefas administrativas de alto nível, como iniciar ou parar a instância do banco de dados, criar e modificar usuários ou qualquer outra tarefa que requeira privilégios elevados.

## Archivelog

O modo **ARCHIVELOG** é uma configuração em um banco de dados Oracle que permite que todas as alterações feitas no banco sejam armazenadas em arquivos de log de arquivamento. Esse recurso é essencial para a recuperação de desastres, pois possibilita a restauração do banco de dados até o momento de uma falha, utilizando os arquivos de redo log mais os archives.

- O **modo Archivelog** é o que permite a realização de backups conhecidos como **hot backups**

## Package

Package no Oracle é composto por duas partes: a especificação (*specification*) e o corpo (*body*). A especificação é a parte visível para o usuário que chama os procedimentos ou funções do pacote, similar a um cabeçalho em linguagens de programação, pois declara quais procedimentos e funções estão disponíveis. Já o corpo do pacote contém a implementação desses métodos declarados na especificação, ou seja, o código por detrás das declarações.

os detalhes da implementação dos métodos (procedimentos e funções) e os atributos, especialmente aqueles designados como privados, não são visíveis ou acessíveis fora do pacote. Eles ficam "ocultos" no corpo do pacote, que é onde estão definidos. Esta abordagem permite que mudanças possam ser feitas na implementação sem afetar outros objetos que dependem da interface pública do pacote, que é definida pela especificação.

## Função COALESCE

Esta função é utilizada para retornar o primeiro valor não nulo em uma lista de valores.