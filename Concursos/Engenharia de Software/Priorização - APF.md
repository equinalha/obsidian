---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2024-11-01T11:09:00
Owner:
  - Eduardo Quinalha
---
# Conceitos básicos

- Tamanho **funcional** de um software
- Métrica: Composição de uma ou mais medidas
- **Estimar esforço de desenvolvimento**
	- No atendimento a novos requisitos
	- No estudo de viabilidade
- Acompanhar o progresso do projeto
	- Controlando e corrigindo problemas
	- Cronograma, esforço, etc
- Tomar decisões
- Análise “make or buy”
- Apoiar contratos
	- Medir o produto entregue
	- Remuneração do resultado

# O que medir?

- Recursos e custos
- Qualidade
- Cronograma
- Progresso
- **Tamanho funcional **→ Pontos de função

# Ponto de Função

- Padrão para medição funcional de software
- Mede **exclusivamente** o tamanho funcional do software
- Mede as funcionalidade **do ponto de vista do usuário**
- **Não depende de tecnologia usada**
- Mede o que o software faz, e não como
- **Não reflete diretamente o esforço, produtividade ou custo**
	- Porém é possível deduzir estes a partir da análise
	- Além da produtividade, é possível realizar outros cálculos baseado em pontos de função como esforço,** tempo, custo, qualidade, entre outros.**

> [!note] 🔥
> Análise de Pontos de Função não mede diretamente esforço, produtividade, custo, qualidade, ENTRE OUTROS. No entanto, ela pode ser usada em conjunto com outras grandezas e dados históricos da organização para medir essas variáveis. Por exemplo: determinado programador desenvolve uma funcionalidade específica em 10 Horas/PF.

- Para medir custo e esforço, faz-se necessário o uso de dados históricos para traçar um perfil horas / ponto de função
- Como estimar?
	- Existem repositórios públicos
	- O International Software Benchmarking Standards Group (ISBSG), por exemplo, contém mais de 6.000 projetos de diferentes tamanhos,
complexidades, linguagens de programação, domínios de informação, entre outros.
	- Dessa forma, é possível utilizá-lo para estimar futuras produtividades – sempre considerando o contexto de como os números foram obtidos.
- Padronizado e mantido por duas principais instituições, com suas respectivas técnicas:
	- **IFPUG**
		- Contagem detalhada
	- **NESMA**
		- Contagem detalhada
		- Contagem Indicativa
		- Contagem Estimativa

## Técnica NESMA

- Além da contagem detalhada, que é a mesma do IFPUG, inclui também:
- **Contagem Indicativa**
	- Baixa precisão
	- Rápido
	- Usado para estimativas
	- Geralmente utilizada na fase inicial da proposta
	- Útil na análise de viabilidade de um projeto
	- Só considera 2 tipos de dados
		- ALI - Arquivo lógico interno:** 35 PF**
		- AIE - Externo:** 15 PF**
- **Contagem Estimativa**
	- Média precisão
	- Usado quando não existe uma precisão do nível de complexidade das funções existentes
	- Considera tipos de dados e de transação
		- Dados: ALI, AIE →** Complexidade baixa**
		- Tipos de transação: EE, SE, CE → **Complexidade média**

## Pontos por caso de uso

- Só pode ser utilizado em projetos que utilizam casos de uso
- Não pode ser empregada antes da análise de requisitos
- Contagem de atores e casos de uso
- Calcular os PCU não ajustados
- Calcular os PCU de acordo com a “Complexidade técnica” e a “complexidade ambiental” da aplicação
- Não existe um grupo coeso de usuários

# Análise de Ponto de Função

> [!tip] 💡
> **Considera apenas o conceito lógico! Não interessa como os dados são armazenados**

- Baseia-se primariamente no projeto lógico
- É possível fazer antes deste, dependendo das informações disponíveis, porém a precisão será menor
- Pode ser aplicado a todos os domínios funcionais (áreas de negócio)
	- Pela IFPUG, pode haver diferenças nos valores de PF por domínio funcional
	- Calibrados de acordo com diferentes complexidades

## Processo de Medição

![[Priorização - APF synced block]]

### 1. **Reunir a documentação disponível**

- Requisitos
- Pode ser requirido acesso a especialistas
- Diagrama de entidades (BD)
- Modelo de dados e objetos
- Telas, relatórios, guias, manuais de uso

### 2. **Determinar escopo e a fronteira de contagem**

- Deve ser conduzida para responder a uma questão de negócio
- O propósito da contagem determina seu escopo
	1. Tamanho de uma release
	2. Tamanho de uma aplicação como um todo
- Identificar o tipo da contagem
	- Conforme o propósito identificado, a contagem pode ter diferentes tipos:
		- **Projeto de desenvolvimento**
			- Primeira versão de um software
			- Medir o que vai ser entregue
			- Contagem ocorre múltiplas vezes e é estimada
		- **Projeto de melhoria ou manutenção**
			- Manutenções de um software existente
			- Mede-se funcionalidades adicionadas, alteradas ou removidas
			- Para o IFPUG, considera-se apenas manutenções evolutivas, que irão adicionar funcionalidades novas no software
				- Descarta-se corretivas e preventivas
		- **Contagem da aplicação**
			- Um software existente e já instalado
-  **Identificar a fronteira da aplicação**
	- Define o que está dentro ou fora
	- Deve ser considerada a visão do usuário, e não arquitetura de software
		- Considera-se usuário uma pessoa, hardware ou software, externo à aplicação mas que interage com ela
- **Identificar os requisitos funcionais**
	- Descarta os requisitos não funcionais

## 3. Medições

![[Untitled 589.png]]

![[Untitled 590.png]]

### 3.1. Medir funções de dados

> [!tip] 💡
> A intenção primária de AIE e ALI é armazenar dados, e não alterar comportamento

- Identificar funções de dados (ALI e AIE)
	- ALI (Arquivo Lógico Interno)
		- Mantém um conjunto de dados dentro da aplicação, por exemplos, dados de um usuário
		- Reconhecidos pelo usuário
		- Em geral, um arquivo lógico interno é uma tabela ou conjunto de tabelas físicas armazenadas em um banco de dados.
	- AIE (Arquivo de Interface Externa)
		- Troca dados (Envia e/ou recebe) de entidade fora da fronteira da aplicação, por exemplo, outro sistema
		- **Um AIE é sempre um ALI de outra aplicação**
- Contar DERs e RLRs para cada função de dados
	- DER - Dado Elementar Referenciado
		- Atributo único, reconhecido pelo usuário, dentro de um ALI
		- Campos de uma tabela, por exemplo
		- Atributos de um objeto
	- RLR - Registro Lógico Referenciado
		- Subgrupo de dados elementares referenciados
		- Todo ALI tem pelo menos um RLR
		- Quando um atributo pode ser considerado um agrupamento de dados, por exemplo, endereço (pode ser decomposto em tipo, logradouro, número e complemento)
		- Se todos os atributos forem atômicos, então têm-se um RLR por ALI/AIE
		- Caso um dos atributos seja um outro subgrupo (endereço, por exemplo), têm-se então 2 RLR’s
- Determinar a complexidade funcional de cada função de dados

![[Untitled 591.png]]

- **Determinar o tamanho funcional de cada função de dados**

> [!tip] 💡
> Para efeitos de concurso, esta tabela tem que ser memorizada

![[Untitled 592.png]]

### 3.2. Medir funções de transação

- Identificar cada processo elementar requerido pelo usuário
	- Processo elementar
		- menor atividade significativa para o usuário
		- Ao final da execução, deixa a aplicação em um estado consistente
		- Ex: Incluir, alterar, excluir, etc
- Classificar cada processo elementar como EE, SE, ou CE
	- EE → Entrada externa. 
		- Dados recebidos de fora da fronteira da aplicação
		- Intenção primária: Manter ALI ou alterar comportamento da aplicação
		- **Implica em alguma alteração de estado do sistema!**
> [!note] 🔥
> São EE:
> Operações de inclusões e alterações de registros em arquivos da aplicação, janelas que permitem adicionar, excluir e alterar registros em arquivos de dados.
> 
> Não são EE:
> 
> Menus, **telas de login**, **telas de filtro de relatórios e consultas,** múltiplos métodos de se executar uma mesma lógica de entrada, entre outros.
	- SE → Saída externa
		- Envia dados para fora da fronteira da aplicação
		- Inclui funções de processamento
		- Seu objetivo é exibir informações recuperadas através de processamento lógico **que envolva cálculos ou criação de dados derivados e não apenas uma simples recuperação de dados**
> [!note] 🔥
> São SE:
> **Dados transferidos para outra aplicação**; **relatórios**; relatórios online; formatos gráficos; gerador de relatórios.
> 
> Não são SE:
> 
> Telas de ajuda; literais; data, hora, controles de paginação, etc; relatórios múltiplos com a mesma lógica e formato; relatórios criados pelo usuário de forma dinâmica pelo usuário usando uma linguagem como SQL.
	- CE → Consulta externa
		- Recuperação e apresentação de dados
		- Não inclui funções de processamento
		- Entrada online que resulta na geração de alguma resposta imediata
		- A lógica de processamento **não deve conter cálculo matemático, criar dados derivados, atualizar nenhum arquivo lógico interno e/ou alterar o comportamento do sistema**
> [!note] 🔥
> São CE:
> **Telas de logon**, telas de help, telas de alteração/remoção que mostram o que será alterado ou removido antes de sua efetivação; tela de menus que permitem informar parâmetros para a consulta na tela escolhida.
> 
> Não são CE:
> 
> Dados derivados; documentação online; sistema de teste; sistemas tutoriais; relatórios e consultas (c/ cálculo).
![[Untitled 593.png]]
- Contar ALRs e DERs
	- ALR → Arquivo lógico referenciado
		- Uma transação pode depender simultaneamente de mais de um ALI ou AIE
	- DER → Dado Elementar Referenciados
		- Campos referenciados pela transação
- Determinar a complexidade funcional de cada função de transação

<!-- Column 1 -->
![[Untitled 594.png]]

<!-- Column 2 -->
![[Untitled 595.png]]

- Determinar o tamanho funcional de cada função de transação

![[Untitled 596.png]]

### 4. Cálculo do tamanho funcional

- Projeto de desenvolvimento
	- DFP = ADD + CFP
		- DFP → Development Funcion Points
		- ADD → Tamanho das funções entregues (incluídas)
		- CFP → Funcionalidades de conversão de dados
			- Carga inicial
			- Popular banco
			- No momento da instalação da aplicação
- Contagem de melhoria
	- EFP = ADD + CHGA + CFP + DEL
		- CHGA → Funções alteradas
		- DEL → Funções excluídas
- Contagem de aplicação
	- AFP = ADD

### 5. Documentar e reportar

- Memória de cálculo
- Auxilia em auditorias
- Minimiza os erros
- Deve-se registrar
	- Propósito
	- escopo
	- data
	- Lista de funções
	- resultado da contagem

### 6. Fator de ajuste

- A saída do processo até aqui trata apenas de valores brutos
- Não considera requisitos não funcionais
- Considera características técnicas
- Níveis de influência
	- São 14 características consideradas, as CGS (características gerais do sistema)
![[Untitled 597.png]]
	- Cada uma, pontua de 0 a 5
	- VAF = (TDI x 0,01) + 0,65
		- VAF → Fator de ajuste
		- TDI → Somatório dos CGS (máximo 70 pontos: 5 x 14)
		- Ou seja, no maior caso, o ajuste será de 1,35
		- No pior caso, 0,65
		- 35% a mais ou a menos

![[AFP.png]]