---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2024-10-25T16:29:00
Owner:
  - Eduardo Quinalha
---
# Power BI

- o Power BI é um serviço de nuvem fornecido pela Microsoft como Software as a Service (SaaS)
- O Power BI possui diversas funcionalidades, sendo uma ferramenta poderosa tanto no ***back-end*** quanto no ***front-end***.
- ***Front-end*** refere-se à parte da aplicação que interage diretamente com o usuário. No Power BI, isso inclui interfaces de relatórios, dashboards e outros elementos visuais.
- ***Back-end*** refere-se à parte da aplicação que lida com o processamento de dados, armazenamento e outras operações não visíveis para o usuário final.
- O *front-end* do Power BI é acessível via plataforma web ou aplicações móveis, e os usuários interagem diretamente com ele. 
- Os microsserviços e gateways são mais relevantes para o *back-end*, onde ocorrem processos de integração e manipulação de dados.
- O Power BI é composto por três componentes principais: 
	- **Power BI Desktop**, utilizado para a criação de relatórios e dashboards; 
	- o **serviço Power BI** (ou Power BI Pro), que é um serviço online (SaaS) onde os relatórios e dashboards podem ser publicados e compartilhados; 
	- e o **Power BI Mobile**, disponível para dispositivos móveis, que permite o acesso às informações e relatórios de qualquer lugar.
- Blocos de construção básicos
	- **visualizações**, **relatórios**, **conjuntos de dados** (*datasets*), e **painéis** (*dashboards*).

## Arquitetura do Power BI em nuvem

A funcionalidade de backend do Power BI é fornecida por microsserviços em execução em computadores diferentes, dentro da infraestrutura de nuvem gerenciada da Microsoft. Esses microsserviços não são diretamente acessíveis externamente, mas podem ser interagidos através do serviço de gateway, APIs do Power BI, e do portal Power BI na web.

- **Microsserviços**: O Power BI é composto por uma arquitetura baseada em microsserviços, que são pequenos serviços independentes que trabalham juntos para fornecer as funcionalidades do Power BI. Esses microsserviços podem ser responsáveis por várias funções, como processamento de dados, armazenamento, autenticação, entre outros.
- **Execução em computadores diferentes dentro da rede virtual do cluster**: Esses microsserviços são distribuídos e executados em diferentes máquinas dentro de um ambiente de nuvem gerenciado, geralmente utilizando clusters para escalar conforme necessário.
- **Acessibilidade**: Os microsserviços que compõem o backend do Power BI **não são diretamente acessíveis externamente.** Eles são protegidos e gerenciados dentro da infraestrutura da Microsoft.
- **Serviço de gateway e API Azure**: O Power BI tem várias formas de interação externa, como o Power BI Gateway (para dados on-premises), APIs do Power BI (para automação e integração), e diretamente através do portal Power BI na web.

## Componentes

- **Visualizações**: Uma representação visual dos dados, às vezes chamadas de visuais. 
- **Conjuntos** de Dados: Uma coleção de dados que o Power BI usa para criar visualizações.
- **Relatórios**: Uma coleção de elementos visuais de um conjunto de dados, abrangendo uma ou mais páginas.
- **Dashboards**: Uma coleção de página única de visuais, criada a partir de um relatório.
- **Blocos**: Uma visualização única em um relatório ou dashboard.

## **DirectQuery**

- Permite que você conecte diretamente ao banco de dados fonte sem necessidade de importar os dados para o modelo do Power BI.
- **DirectQuery não é uma linguagem**, mas sim um modo de conexão.
- As consultas são feitas em SQL ou em outra linguagem suportada pelo banco de dados fonte e, então, os resultados são retornados ao Power BI.

## DAX

- **Data Analysis Expressions (DAX): **linguagem de consulta própria do Power BI é o , usada para criar expressões em relatórios, como medidas calculadas e colunas calculadas no modelo de dados.
- especialista em matemática e análise
- Aplicações:
	- **Criar medidas:** Calcule indicadores-chave de desempenho (KPIs), métricas personalizadas e análises avançadas.
	- **Filtrar e segmentar:** Explore seus dados em diferentes ângulos, focando em grupos específicos ou períodos de tempo.
	- **Criar relacionamentos:** Estabeleça conexões entre tabelas para realizar análises multidimensionais.
	- **Calcular datas e horas:** Manipule datas e horários com precisão para obter insights temporais relevantes.

### Medidas Rápidas

- **Medida rápida** - uma ferramenta no Power BI que facilita a criação de cálculos através de comandos DAX automaticamente gerados.

## Power Query

- utilizada principalmente para a conexão, transformação e carregamento de dados (ETL).
- Com Power Query, os usuários podem importar dados de diversas fontes, limpar e transformar esses dados antes de carregá-los no modelo de dados do Power BI para análise e visualização. 
- Após a conexão com mais de uma fonte de dados, é possível transformar e combinar os dados coletados no Power BI, conforme a necessidade, em uma consulta útil. 
- Há duas formas de combinar consultas:
	- *mesclando* 
		- Quando se tem uma ou mais **colunas** para adicionar a outra consulta, é preciso **mesclar** a consulta. 
	- *acrescentando *
		- Quando se tem **linhas** adicionais de dados para serem adicionadas a uma consulta existente, é preciso ***acrescentar*** as consultas.

## Linguagem M

- ETL
- Na ferramenta Microsoft Power BI, a linguagem utilizada para realizar transformações de dados, personalizações e para conectar-se a diferentes fontes de dados é conhecida como **M**
- A linguagem M, também chamada de **Power Query Formula Language**, é utilizada principalmente no Editor de Consultas do Power BI, onde o usuário pode realizar operações de etl (Extract, Transform, Load) para preparar os dados para análise.
- Aplicações:
	- **Conectar e importar:** Traga dados de diferentes fontes, como Excel, CSV, SQL Server, Salesforce e APIs.
	- **Limpar e preparar:** Elimine inconsistências, trate valores ausentes e normalize seus dados para uma análise precisa.
	- **Transformar e modelar:** Crie novas colunas, combine tabelas e molde seus dados de acordo com suas necessidades.
	- **Agrupar e resumir:** Agrupe dados por categorias, calcule totais e médias, e obtenha insights valiosos.

## Dashboards

- No contexto do **Power BI**, um *dashboard* é uma página única que apresenta visualizações importantes, como gráficos e relatórios, de forma consolidada.
- Características:
	- Personalização: Permitem que os usuários ajustem as visualizações conforme suas necessidades específicas.
	- Visualização em uma única tela: Facilitam o acesso rápido a múltiplos indicadores de desempenho (KPIs) em um só lugar.
	- Atualização em tempo real: Muitos *dashboards* podem ser configurados para mostrar dados em tempo real, o que é essencial para decisões imediatas.
- O Power BI permite que os usuários copiem os *dashboards* compartilhados
- Mesmo sendo criadores do aplicativo, os usuários não podem simplesmente copiar os *dashboards* de aplicativos compartilhados
- O Power BI permite que os criadores publiquem e compartilhem aplicativos, mas não oferece a funcionalidade de copiar diretamente esses *dashboards* como aplicativos por outros usuários, mesmo que sejam os criadores.

## Aplicativos

- Um dos recursos valiosos do Power BI é a capacidade de criar aplicativos, ou seja, coletâneas de painéis e relatórios que podem ser compartilhados com os usuários finais de forma simplificada e organizada.
- Quando você cria um aplicativo no Power BI, você essencialmente está agrupando elementos como relatórios e painéis em uma única interface que pode ser facilmente acessada e navegada pelos usuários.
- **Espaço de trabalho**: É um local onde você pode colaborar com colegas, criar coleções de painéis e relatórios, e publicá-los como um aplicativo.
- **Aplicativo**: Uma maneira de agrupar e distribuir conteúdo para os usuários finais, oferecendo uma navegação mais simples e intuitiva.

## Modelo Semântico

- Estrutura que define como os dados são organizados e como eles se relacionam.
- Permite que os usuários finais interajam com os dados de uma maneira significativa, facilitando a criação de relatórios e dashboards.
- inclui **relações**, **medidas** e **cálculos** que definem como os dados são interpretados e apresentados. 
- Ele vai além de simplesmente agrupar fontes de dados.
- pode ser utilizado para criar **múltiplos relatórios e dashboards**

## Workspaces

- Quando falamos de uso em grupo e de forma colaborativa, o Power BI oferece os **"workspaces"**, que são espaços de trabalho onde equipes podem compartilhar e colaborar em conjuntos de dados, relatórios e dashboards.
- Para o uso ilimitado e com todos os recursos disponíveis, especialmente em uma organização grande, é necessário adquirir uma **capacidade dedicada** por meio do serviço **Power BI Premium**. 

## Extrair dados da web

- permite extrair dados de páginas da web, incluindo tanto dados em tabelas como dados não tabulares

# Power Apps

- Plataforma no-code para criação de aplicativos
- Integra-se com outros serviços microsoft
- Dataverse
	- Plataforma para armazenamento e gerenciamento de dados usados pelos aplicativos
	- Permite a modelagem dos dados e criação de relacionamentos entre entidades
- Permite o uso de APIs e conectores para integrar dados de diversas fontes, como SharePoint, SQL Server, Excel e outras APIs externas
- Pode ser utilizado em conjunto com Power Automate
	- Automatização de fluxos de trabalho e processos de negócios
- Os aplicativos são multi-plataforma (Android e IOS) e também navegadores web

# Power Automate

- Criação de fluxos de trabalho automatizados entre aplicativos e serviços
- No-code
- Exemplos:
	- Envio de notificações
	- Mover dados entre sistemas
	- Geração de relatórios
- Oferece conectores pré-construídos
- Fluxos baseados em eventos
	- Criação de itens
	- Recebimento de e-mail
	- Atualização em um BD
- Possui recursos de IA e RPA

# Power Virtual Agents

- permite criar chatbots inteligentes e personalizáveis 
- No code
- Pode ser combinado com power automate
- **Multicanal:** Os chatbots podem ser implantados em vários canais de comunicação, incluindo websites, aplicativos móveis, Facebook Messenger, Microsoft Teams e muitos outros, proporcionando uma experiência de atendimento ao cliente consistente.
- **Capacidades de IA:** Utiliza inteligência artificial para entender a intenção do usuário e fornecer respostas apropriadas, além de aprender com as interações para melhorar continuamente a precisão e a relevância das respostas.
- **Escalabilidade:** É projetado para escalar conforme necessário, permitindo que empresas de todos os tamanhos, desde pequenas startups até grandes corporações, beneficiem-se de suas capacidades.
