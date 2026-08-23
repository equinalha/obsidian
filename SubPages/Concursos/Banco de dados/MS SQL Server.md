---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2024-11-22T08:59:00
Owner:
  - Eduardo Quinalha
---
# Características do SQL Server 2019

- **Big Data Clusters**: Integração com o **Hadoop e Apache Spark**, permitindo a criação de clusters de big data para análise e gerenciamento de grandes volumes de dados.
- **Intelligent Query Processing**: Melhoria no desempenho de consultas através de **otimizações automáticas **e novas técnicas de processamento de consultas.
- **Segurança Avançada**: Recursos de segurança como criptografia Always Encrypted com enclaves seguros, autenticação de banco de dados, e auditoria aprimorada.
- **Desempenho e Escalabilidade**: Suporte para maior capacidade de armazenamento e processamento, bem como otimizações de desempenho para cargas de trabalho intensivas.
- **PolyBase**: Habilidade de executar consultas em dados externos, como Hadoop, Azure Blob Storage, e outros bancos de dados relacionais.
- **Data Virtualization**: Permite que os dados sejam consultados de várias fontes sem necessidade de movê-los ou copiá-los, proporcionando uma visão unificada dos dados.
- **Suporte para Contêineres**: Implementação e execução do SQL Server em** contêineres Docker**, facilitando a portabilidade e a escalabilidade.
- **Inteligência Artificial e Machine Learning**: Integração com serviços de IA e machine learning, permitindo a criação de modelos preditivos diretamente no banco de dados.

# Componentes

## Database Engine

- Principal componente do SQL Server
- Corresponde a uma instância do SQL Server
- Mecanismo de Banco de Dados do SQL Server
- Serviço principal para armazenamento, processamento e proteção de dados
- replicação, pesquisa de texto completo, ferramentas para gerenciar dados XML e relacionais, na integração da análise de banco de dados e na integração do PolyBase
para acesso ao Hadoop e a outras fontes de dados heterogêneas
- servidor Data Quality Services (DQS)

## Analysis Services

- Ferramentas para criação e gerenciamento de aplicativos OLAP e Mineração de Dados

## Reporting Services

- Componentes de servidor e cliente por criar, gerenciar e implantar relatórios tabulares, de matriz, gráficos e de forma livre

## Integration Services

- Conjunto de ferramentas gráficas e objetos programáveis para mover, copiar e transformar dados.
- Também inclui o componente Data Quality Services (DQS) para o Integration Services.

## Master Data Services

- Solução do SQL Server para gerenciamento de dados mestre.
- Pode ser configurado para gerenciar qualquer domínio (produtos, clientes, contas) e inclui hierarquias, segurança granular, transações, controle de versão de dados e regras de negócio, bem como um Suplemento para Excel que pode ser usado para gerenciar dados.

## Machine Learning Services

- Suporte a soluções escalonáveis de aprendizado de máquina por meio de fontes de dados empresariais
- Suporte à R e Python

## Machine Learning Server

- Suporte à implantação de soluções de aprendizado de máquina distribuídas e escalonáveis em várias plataformas,

# Particionamento

- No SQL Server, você pode distribuir fisicamente dados em discos dividindo-o, ou separando em partes distintas e independentes,
- O particionamento não só melhora o desempenho das consultas, mas também simplifica o processo de gerenciamento e manutenção de seus dados.

# T-SQL

- T-SQL: implementação da Microsoft da linguagem padrão SQL ANSI com recursos adicionais
- Equivalente ao PL/SQL
- Inclui estruturas de controle de fluxo:
	- **BEGIN...END**: Delimitação de blocos de código.
	- **IF...ELSE**: Condicionais para controle de fluxo.
	- **WHILE**: Laços de repetição.
	- **GOTO**: Desvio incondicional para um rótulo.
```sql
IF EXISTS (SELECT * FROM Employees WHERE EmployeeID = 1)
BEGIN
    PRINT 'Employee exists.';
END
ELSE
BEGIN
    PRINT 'Employee does not exist.';
END

DECLARE @Counter INT = 0;
WHILE @Counter < 10
BEGIN
    PRINT 'Counter: ' + CAST(@Counter AS NVARCHAR(10));
    SET @Counter = @Counter + 1;
END
```
- Funções específicas para transações
	- **BEGIN TRANSACTION**: Inicia uma transação.
	- **COMMIT TRANSACTION**: Confirma todas as operações realizadas na transação.
	- **ROLLBACK TRANSACTION**: Reverte todas as operações realizadas na transação.
- Tratamento de erros
	- **TRY...CATCH**: Blocos de código para capturar e tratar erros.
- As aplicações escritas em linguagens de programação tais como Visual Basic e C# .NET podem enviar consultas T-SQL das aplicações para o Database Engine.

## Terminador de Comandos

- Na maioria dos SGBDs, utiliza-se ;
- No T-SQL também existe um comando especial com esta finalidade: `GO`

## Depurador T-SQL

- O depurador Transact-SQL é uma ferramenta fundamental para desenvolvedores que trabalham com SQL Server.
- Ele permite a **depuração interativa** de *stored procedures*, ou procedimentos armazenados, proporcionando uma visão detalhada da execução do código.
- Ele oferece recursos como:
	- **Mostrar a sequência de chamadas SQL**: Permite visualizar passo a passo as instruções SQL que estão sendo executadas.
	- **Exibir variáveis locais/globais**: Durante a depuração, é possível monitorar o valor das variáveis utilizadas dentro das *stored procedures*.
	- **Controlar pontos de interrupção** (breakpoints): O desenvolvedor pode definir pontos específicos no código onde a execução será interrompida, permitindo a análise detalhada do estado do sistema naquele ponto.
	- **Visualizar parâmetros associados aos procedimentos**: Permite observar os valores dos parâmetros que são passados para as *stored procedures*.

# Subsistema de Segurança

- Recursos de autenticação e criptografia nativas
- Microsoft incluiu a capacidade de criar usuários dentro de um banco de dados sem a necessidade de criar um login no servidor, conhecido como bancos de dados autocontidos

# Replicação

- Pode ser baseada em snapshot ou transacional

# SQL Server Agent

- executado como um serviço separado em uma instância do SQL Server.
- Cada instância do SQL Server tem um serviço SQL Agent
- O principal uso do SQL Server Agent para executar tarefas agendadas, como a reconstrução de índices, o backup de bancos de dados, o carregamento (load) do armazém de dados, e assim por diante.
- permite que você configure operadores e alertas

# HA e Disaster Recovery Tools

## AlwaysOn

- Recurso de alta disponibilidade e recuperação de desastres
- Baseado na tecnologia de **Clustering de Failover do Windows Server (WSFC**) e oferece uma evolução em relação a tecnologias anteriores como **Database Mirroring** e **Log Shipping**, combinando e aprimorando suas funcionalidades.
- Oferece opções de replicação **síncrona para alta disponibilidade local **e **assíncrona** para recuperação de desastres em locais **remotos**
- Permite que as réplicas secundárias sejam utilizadas para **operações de leitura**, como geração de relatórios e backups
- Utiliza compressão para reduzir o consumo de banda na transferência de dados entre as réplicas

### Availability Groups

- Permite replicar um conjunto lógico de bancos de dados como uma única unidade para múltiplas instâncias do SQL Server
1. **Disponibilidade e Failover Automático**:
	- Permite a configuração de grupos de disponibilidade com réplicas primárias e secundárias. 
	- As réplicas secundárias podem ser configuradas para failover automático ou manual em caso de falha da réplica primária.
2. **Replicação de Dados**:
	- Dados são replicados de forma síncrona ou assíncrona entre a réplica primária e as réplicas secundárias, garantindo a consistência dos dados.
3. **Leitura Escalável**:
	- Réplicas secundárias podem ser usadas para operações de leitura, melhorando o desempenho e distribuindo a carga de trabalho.
4. **Suporte a Vários Data Centers**:
	- Réplicas secundárias podem ser distribuídas em diferentes locais geográficos para proteção contra desastres.

### Database Mirroring

- **Espelhamento de Banco de Dados**:
	- Fornece alta disponibilidade ao manter uma cópia espelhada do banco de dados em um servidor secundário.
- **Modos de Operação**:
	- **High-Safety Mode**: Garantia de zero perda de dados com sincronização completa.
	- **High-Performance Mode**: Permite uma operação assíncrona para melhorar o desempenho com possível perda mínima de dados.
- **Failover Automático ou Manual**:
	- O failover pode ser automático (em modo de segurança total) ou manual (em modo de alto desempenho).

### Log Shipping

5. **Transferência de Logs de Transações**:
	- Os logs de transações são copiados periodicamente de um servidor primário para um ou mais servidores secundários.
6. **Recuperação de Falhas**:
	- Em caso de falha do servidor primário, o servidor secundário pode ser restaurado e trazido online como o servidor primário.
7. **Planejamento de Backups**:
	- Backups automáticos de logs e restaurações agendadas garantem a continuidade das operações.

### Failover Clustering

8. **Clusters de Failover do Windows**:
	- Integração com o Windows Server Failover Clustering (WSFC) para fornecer alta disponibilidade e failover automático.
9. **Instância de Cluster de Failover do SQL Server (FCI)**:
	- Fornece redundância a nível de instância do SQL Server. Se o nó ativo falhar, outra instância no cluster assume o controle.
10. **Armazenamento Compartilhado**:
	- Utiliza armazenamento compartilhado entre nós do cluster para garantir a consistência dos dados.

### Backup e Recuperação

11. **Backups Completos, Diferenciais e de Logs**:
	- Estratégias de backup robustas para proteger os dados e garantir a capacidade de restaurar o banco de dados a um ponto específico no tempo.
12. **Recuperação em Nível de Ponto**:
	- Permite a recuperação do banco de dados para um ponto específico no tempo usando backups de logs de transações.
13. **Backup em Nuvem**:
	- Integração com serviços de nuvem, como Azure Blob Storage, para backups e restaurações fora do local.

### Stretch Database

14. **Extensão para a Nuvem**:
	- Permite que as partes menos acessadas dos dados de uma tabela sejam armazenadas na nuvem (Azure), reduzindo a carga no armazenamento local e melhorando a disponibilidade e a recuperação.
15. **Acesso Transparente**:
	- Os dados estendidos para a nuvem são acessíveis da mesma forma que os dados locais, proporcionando uma experiência contínua para os aplicativos.

### Transparent Data Encryption (TDE)

16. **Criptografia de Dados em Repouso**:
	- Protege os dados armazenados no disco criptografando os arquivos de banco de dados, logs e backups.
17. **Proteção contra Acesso Não Autorizado**:
	- Garante que os dados estejam protegidos mesmo em caso de roubo ou perda de hardware.

# Ferramentas de Gerenciamento

### SQL Server Management Studio (SSMS)

- **Interface Gráfica**: Ferramenta principal para administração de SQL Server com uma interface gráfica de usuário (GUI) completa.
- **Desenvolvimento de Consultas**: Ambiente integrado para escrever, executar e depurar consultas T-SQL.
- **Gestão de Instâncias**: Permite gerenciar múltiplas instâncias do SQL Server, configurar segurança, realizar backups e restaurações, entre outras tarefas.
- **Monitoramento de Desempenho**: Oferece recursos como o Activity Monitor e o SQL Server Profiler para monitorar e otimizar o desempenho do servidor.

### Azure Data Studio

- **Desenvolvimento e Gerenciamento**: Ambiente de desenvolvimento leve e moderno, focado em análise de dados e administração de banco de dados.
- **Extensibilidade**: Suporte para extensões que adicionam funcionalidades adicionais.
- **Multi-Plataforma**: Disponível para Windows, macOS e Linux.
- **Jupyter Notebooks**: Suporte para notebooks Jupyter com integração de consultas SQL, scripts de Python e visualizações de dados.

### SQL Server Data Tools (SSDT)

- **Desenvolvimento de Banco de Dados**: Ambiente integrado no **Visual Studio** para desenvolver, testar e implantar projetos de banco de dados.
- **Design de Esquema**: Ferramentas de design para criação e modificação de esquemas de banco de dados.
- **Controle de Versão**: Integração com sistemas de controle de versão para gerenciar alterações no banco de dados.
- **Desenvolvimento de BI**: Suporte para desenvolvimento de projetos de Integration Services (SSIS), Analysis Services (SSAS) e Reporting Services (SSRS).

### SQL Server Profiler

- **Monitoramento de Eventos**: Ferramenta para **capturar e analisar eventos do SQL Server**, útil para diagnosticar problemas de desempenho e segurança.
- **Análise de Desempenho**: Ajuda a identificar consultas lentas e gargalos no sistema.

### Database Engine Tuning Advisor (DTA)

- **Otimização de Desempenho**: Analisa cargas de trabalho e recomenda índices, particionamento e outras otimizações para melhorar o desempenho do banco de dados.
- **Análise de Consultas**: Identifica possíveis melhorias com base no histórico de consultas executadas.

### SQL Server Configuration Manager

- **Configuração do Servidor**: Ferramenta para configurar serviços, protocolos de rede e outros parâmetros do SQL Server.
- **Gerenciamento de Serviços**: **Iniciar, parar, pausar e configurar instâncias do SQL Server e seus serviços associados.**

### SQL Server Agent

- **Automação de Tarefas**: Gerencia e executa trabalhos agendados, como backups, manutenção do banco de dados e execução de scripts.
- **Alertas e Notificações**: Configuração de alertas para monitorar eventos específicos e notificar administradores sobre problemas potenciais.

### SQL Server Management Objects (SMO)

- **Automação e Scripting**: Biblioteca de programação que permite a automação de tarefas administrativas usando scripts de PowerShell ou outras linguagens de programação compatíveis com .NET.

### Extended Events

- **Monitoramento Avançado**: Sistema para coletar e analisar eventos e diagnósticos do SQL Server, com menor sobrecarga em comparação com o SQL Server Profiler.
- **Personalização**: Permite a criação de sessões de eventos personalizadas para monitorar atividades específicas do servidor.

### PowerShell

- **Automação de Administração**: Conjunto de cmdlets específicos para SQL Server que permite automatizar tarefas administrativas e de gerenciamento.
- **Script de Gerenciamento**: Criação de scripts para operações repetitivas e complexas de gerenciamento de banco de dados.

# Internal Views

- são componentes críticos que fornecem uma visão sobre a estrutura interna e o comportamento do banco de dados.

### Principais Categorias de Internal Views

18. **Dynamic Management Views (DMVs) e Functions (DMFs)**:
	- **Função**: Fornecem informações dinâmicas sobre o estado do servidor, incluindo desempenho, atividades de consulta, alocação de memória, e utilização de recursos.
	- **Exemplos**:
		- `sys.dm_exec_requests`: Exibe informações sobre as solicitações que estão atualmente em execução.
		- `sys.dm_os_wait_stats`: Mostra estatísticas de espera, úteis para identificar gargalos de desempenho.
19. **Catalog Views**:
	- **Função**: Oferecem informações sobre os objetos e metadados do banco de dados, como tabelas, índices, colunas e permissões.
	- **Exemplos**:
		- `sys.tables`: Lista todas as tabelas do banco de dados.
		- `sys.indexes`: Detalha informações sobre os índices existentes no banco de dados.
20. **System Views**:
	- **Função**: Fornecem informações gerais sobre o estado do servidor e do banco de dados.
	- **Exemplos**:
		- `sys.databases`: Exibe informações sobre todos os bancos de dados do servidor.
		- `sys.sysprocesses`: Mostra informações sobre os processos que estão sendo executados no servidor.
21. **Performance Views**:
	- **Função**: Focam em fornecer dados de desempenho específicos, ajudando a monitorar e otimizar o desempenho do servidor.
	- **Exemplos**:
		- `sys.dm_exec_query_stats`: Contém estatísticas de desempenho para consultas executadas.
		- `sys.dm_io_virtual_file_stats`: Fornece estatísticas de I/O para arquivos de banco de dados.

### Considerações

- **Permissões**: Acesso às internal views geralmente requer permissões de administrador ou roles específicos, como `VIEW SERVER STATE`.
- **Impacto no Desempenho**: Consultas complexas em internal views podem impactar o desempenho do sistema, especialmente em ambientes de produção. É importante usar essas consultas com cuidado.

```sql
-- Identificar as consultas que estão em execução e consumindo mais recursos
SELECT 
    r.session_id,
    r.status,
    r.start_time,
    r.cpu_time,
    r.logical_reads,
    r.reads,
    r.writes,
    r.wait_time,
    q.text
FROM 
    sys.dm_exec_requests r
CROSS APPLY 
    sys.dm_exec_sql_text(r.sql_handle) AS q
ORDER BY 
    r.cpu_time DESC;
```

# Bases de dados de sistema

- Existem várias bases de dados de sistema que são essenciais para o funcionamento do servidor.
- Essas bases de dados contêm informações críticas sobre a configuração do sistema, segurança, operações e metadados.

### Considerações Gerais

- **Backup e Recuperação**: É fundamental realizar backups regulares das bases de dados de sistema, especialmente `master`, `msdb` e `model`, para garantir que o servidor possa ser restaurado em caso de falha.
- **Monitoramento e Manutenção**: Monitorar o desempenho e o espaço em disco dessas bases de dados é crucial para evitar problemas de desempenho e garantir a operação contínua do SQL Server.
- **Segurança**: Assegurar que essas bases de dados estejam protegidas contra acessos não autorizados, pois contêm informações sensíveis sobre a configuração e operação do servidor.

### master

- **Função**: A base de dados `master` é a mais importante, pois armazena todas as informações a nível de servidor, incluindo:
	- Metadados do sistema
	- Configurações de servidor
	- Informações de logins
	- Localização de outras bases de dados

### model

- **Função**: A base de dados `model` serve como um modelo para todas as novas bases de dados criadas no servidor. 
	- Todas as novas bases de dados herdam a estrutura e as configurações da `model`.
	- Pode ser personalizada para incluir objetos e configurações padrão que você deseja em todas as novas bases de dados.
- **Considerações**: Modificações na `model` afetam todas as futuras bases de dados criadas.

### msdb

- **Função**: A base de dados `msdb` é utilizada pelo **SQL Server Agent **para agendamento de tarefas e armazenamento de informações sobre:
	- Trabalhos e agendamentos
	- Alertas e operadores
	- Backups e histórico de restaurações
	- Planos de manutenção

### tempdb

- **Função**: A base de dados `tempdb` é uma base de dados temporária usada para:
	- Armazenamento de tabelas temporárias e variáveis de tabela
	- Ordenações e operações de hash temporárias
	- Reconstruções de índices
	- Processamento de consultas e operações de classificação
- **Considerações**: É recriada cada vez que o servidor SQL é iniciado. O tamanho e o desempenho da `tempdb` são cruciais para o desempenho geral do sistema, especialmente em operações intensivas de E/S.

### Resource (mssqlsystemresource)

- **Função**: A base de dados `Resource` armazena todos os objetos de sistema que são fornecidos com o SQL Server, como stored procedures e funções de sistema.
	- É uma base de dados somente leitura que não é visível diretamente no SQL Server Management Studio (SSMS), mas pode ser acessada em cenários de recuperação.
- **Considerações**: Não deve ser modificada pelo usuário. Atualizações do SQL Server podem modificar esta base de dados.

### distribution (para replicação)

- **Função**: Usada em configurações de replicação, a base de dados `distribution` armazena metadados e histórico de replicação.
	- Mantém dados de status e logs de replicação para distribuidores, publicadores e assinantes.
- **Considerações**: Necessária apenas se a replicação estiver configurada. Deve ser monitorada e mantida para garantir a integridade e o desempenho da replicação.

### ReportServer e ReportServerTempDB (para Reporting Services)

- **Função**: Usadas pelo SQL Server Reporting Services (SSRS), estas bases de dados armazenam metadados e informações temporárias sobre relatórios:
	- `ReportServer`: Contém metadados de relatórios, configurações, agendamentos e históricos.
	- `ReportServerTempDB`: Usada para armazenamento temporário de dados de relatórios em execução.
- **Considerações**: Necessárias apenas se o SSRS estiver instalado e configurado. Devem ser mantidas e monitoradas para garantir a funcionalidade dos relatórios.

### SSISDB (para Integration Services)

- **Função**: Utilizada pelo SQL Server Integration Services (SSIS), a base de dados `SSISDB` armazena informações sobre pacotes de integração, execuções, logs e configurações do SSIS.
- **Considerações**: Necessária apenas se o SSIS estiver instalado e configurado. Deve ser monitorada e mantida para garantir a integridade e o desempenho dos pacotes de integração.

# Estrutura do banco

### Tipos de Arquivos

22. **Arquivos de Dados Primários (.mdf)**
	- **Função**: Contêm os dados e objetos do banco de dados, como tabelas, índices, procedimentos armazenados, etc. Cada banco de dados tem exatamente **um arquivo de dados primário.**
	- **Nome Padrão**: Por convenção, o arquivo de dados primário possui a extensão `.mdf`.
23. **Arquivos de Dados Secundários (.ndf)**
	- **Função**: Usados para dividir dados em vários arquivos, principalmente quando um banco de dados cresce muito e precisa ser distribuído em vários discos para melhorar o desempenho. Não é obrigatório e pode haver nenhum, um ou vários arquivos de dados secundários.
	- **Nome Padrão**: Estes arquivos geralmente possuem a extensão `.ndf`.
24. **Arquivos de Log de Transações (.ldf)**
	- **Função**: Registram todas as transações e as alterações feitas nos dados. São essenciais para a recuperação de falhas, pois permitem a restauração do banco de dados ao seu estado consistente anterior em caso de falha.
	- **Nome Padrão**: Por convenção, os arquivos de log de transações possuem a extensão `.ldf`.

# Tipos de dados

- **sql_variant**
	- O propósito do **sql_variant** é armazenar valores de outros tipos de dados, exceto *text*, *ntext*, e *image*. Ele pode conter até 8.000 bytes,
- **varchar(max), nvarchar(max), e varbinary(max)**
	- podem armazenar respectivamente grandes quantidades de texto e dados binários até aproximadamente 2GB
- **tipos de dados de string**
	- **Tipos de tamanho fixo**: Char e NChar.
	- **Tipos de tamanho variável**: VarChar, VarChar(max), NVarChar e NVarChar(max).
	- **VarChar(max)** e **NVarChar(max)** podem armazenar até aproximadamente 2^(31) -1 caracteres para VarChar(max), que é cerca de 2 bilhões de caracteres, e 
	- **2^(30) - 1** caracteres para NVarChar(max), que é cerca de 1 bilhão de caracteres para dados Unicode.