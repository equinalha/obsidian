---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2024-09-08T10:05:00
Owner:
  - Eduardo Quinalha
---
 

# Definições

- Raw Data → Dados operacionais, forma bruta
- ETL → Extrai, transforma e carrega os dados no Data Warehouse
- BI:
	- Combinação de arquiteturas, ferramentas, BD, análises, técnicas e metodologias
	- Permite o acesso interativo, por vezes em tempo real
	- Suporte à decisões
	- Dados de diferentes fontes
- Tipos de Análise
	- **Descritiva (BI)**
		- O que aconteceu?
	- **Diagnóstica (BI)**
		- Por quê aconteceu?
	- **Preditiva (BI)**
		- O que provavelmente vai acontecer?
	- Prescritiva (Não provida por BI)
		- O que fazer caso algo aconteça

# Arquitetura de alto nível de BI

1. Data Warehouse
2. Análise de Negócios
3. BPM (Business Performance Management)
4. Interface de usuário (Dashboards)

# 4 Habilidades de BI

- Memória organizacional (DW)
- Integração de informação (centralizar informações de diversas fontes)
- Criação de conhecimento (insights)
- Apresentação

# Governança vs Gestão de Dados

## Governança de Dados

- Conjunto de políticas, procedimentos, funções, estruturas, padrões e medidas que garantem o uso eficaz, eficiente, e seguro dos dados dentro de uma organização
- Define quem tem autoridade e controle sobre os dados e recursos de informação
- Como estes dados são usados e protegidos

## Gestão de Dados

- Planejar, controlar e entregar dados e recursos de informação
- Coleta, armazenamento, processamento, análise e distribuição dos dados
- Mais focada no aspecto operacional

# Sistema de Apoio a Decisão (SAD)

- Também conhecido por Decision Support System (DSS)
- Suporte a tomada de decisões embasadas em dados
- Fornece relatórios, simulações, previsões e ferramentas analíticas
- Frequentemente integrado a outras soluções de **Business Intelligence** e **Data Warehouses**

## Componentes

- Banco de dados
	- Relacionais
	- Data Warehouses
	- Dados externos
- Modelo analítico
	- Análise quantitativa
	- Modelos estatísticos
	- Algoritmos de otimização
	- Simulações e previsões
- Interface do Usuário

# Sistema de Informações Gerenciais

- Management Information System (MIS)
- sistema de informação voltado para o gerenciamento e operação de uma organização
- Seu principal objetivo é coletar, processar e gerar relatórios baseados em dados transacionais que ajudam os gerentes a acompanhar o **desempenho das operações rotineiras** e a tomar **decisões táticas de curto prazo.**
- gera relatórios regulares e padronizados, como controle de estoque, relatórios de vendas, análise de desempenho financeiro, etc.
- coleta dados de sistemas transacionais, como ERP (Enterprise Resource Planning), e os organiza de forma a facilitar a visualização e o controle.

### Diferenças entre SIG e SAD:

| **Aspecto** | **SIG (Sistema de Informações Gerenciais)** | **SAD (Sistema de Apoio à Decisão)** |
| --- | --- | --- |
| **Objetivo** | Monitorar e gerenciar **operações diárias** | Apoiar decisões **complexas e estratégicas** |
| **Tipo de Decisão** | Decisões** estruturadas e repetitivas** | Decisões **semi-estruturadas ou não estruturadas** |
| **Relatórios** | **Padronizados**, com foco no controle de operações | **Customizados**, simulações, e análises de cenários |
| **Foco Temporal** | **Curto prazo** e operações correntes | **Médio a longo prazo**, com análises **preditivas** |
| **Usuários** | Gerentes de nível operacional e tático | Executivos, gestores estratégicos, analistas |
| **Interatividade** | **Pouca interatividade**; relatórios estáticos | **Alta interatividade**; permite ajustes e simulações |
| **Fontes de Dados** | Dados transacionais e operacionais | Dados de** múltiplas fontes**, inclusive externos e históricos |

# Sistema de Informações Executivas

- Fornece informações de alto nível e sumarizadas para os executivos e gestores seniores de uma organização
- Fornece uma visão geral das operações, tendências de mercado e indicadores-chave de desempenho (KPIs) da empresa.
- Parecido com o SAD, porém o foco não é a tomada de uma decisão estratégica envolvendo simulações, mas sim uma visão geral do estado atual

### Diferença entre SIE e outros sistemas (SIG e SAD):

| **Aspecto** | **SIE (Sistema de Informações Executivas)** | **SIG (Sistema de Informações Gerenciais)** | **SAD (Sistema de Apoio à Decisão)** |
| --- | --- | --- | --- |
| **Objetivo** | Oferecer uma **visão geral **estratégica para executivos | Gerenciar operações e decisões de curto prazo | Apoiar decisões complexas e semi-estruturadas |
| **Usuários** | Alta gestão e executivos | Gerentes operacionais e táticos | Gestores e analistas |
| **Informações** | **Sumarizadas**, focadas em KPIs e tendências | Detalhadas e operacionais | Variadas, com foco em análises e simulações |
| **Tomada de Decisão** | Estratégica, baseada em informações agregadas | Tática, baseada em dados operacionais | Estratégica e tática, com análises preditivas |
| **Interface** | Painéis visuais e gráficos, fácil de usar | Relatórios padronizados | Análises interativas e customizáveis |
| **Fontes de Dados** | Dados internos e externos, de várias fontes | Dados transacionais e de operações cotidianas | Dados históricos, transacionais e simulações |

# ERP

- Sistema de gestão empresarial integrado que automatiza e centraliza os processos e dados essenciais de uma organização
- O ERP visa otimizar e interligar diversas áreas de negócios, como finanças, compras, vendas, produção, recursos humanos, entre outras, em uma única plataforma, permitindo maior eficiência e melhor tomada de decisões.
- Promove uma visão holística da empresa
- Características
	- Integração de Módulos
	- Base de dados centralizada
	- Automatização de processos
	- Relatórios e Análises
