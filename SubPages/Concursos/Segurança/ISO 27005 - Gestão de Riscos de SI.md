---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2024-11-07T06:25:00
Owner:
  - Eduardo Quinalha
---
# ISO 27005

- Integra os objetivos das ISO 27001 e 27002
- Diretrizes
- Não é um procedimento
- **Contempla todos os tipos de organizações**
- Última revisão: 2019
- Prevê **iterações**. Estas podem acontecer várias vezes
- Obedece o ciclo PDCA

## Definições

- Risco
	- Efeito da incerteza nos objetivos. 
	- Trata-se de um desvio em relação ao esperado, tanto positivo quanto negativo.
	- Associado à probabilidade de ocorrência e impactos ou consequências
![[SubPages/Pessoal/images/image 71.png]]

## 1. Estabelecimento de Contexto

- Entrada
	- Todas as informações sobre a organização que sejam relevantes
- Ação
	- Definição do escopo
	- Limites de aceitação
- Saída
	- Especificação dos critérios básicos
	- Escopo e limites
	- Organização
- Propósitos
	- Suporte a um SGSI
	- Conformidade legal (LGPD, por exemplo)
	- Preparação de um PCN
	- Preparação de um plano de resposta a incidentes
	- Descrição dos requisitos de SI para um produto ou serviço

## 2. Processo de Avaliação de Riscos em SI

- Macro-atividade
	- Entrada (saída da etapa 1)
		- Especificação dos critérios básicos (etapa 1)
		- Escopo e limites
		- Organização
	- Ação
		- Identificação
		- Quantificação
		- Qualificação
	- Saída
		- Lista de riscos avaliados, ordenados por prioridade, de acordo com os critérios

### 2.1. Identificação de Riscos

> [!note] 🔥
> **AA CVC** (Identificação de **A**lcóolicos **A**nônimos na **CVC**)

- Identificação de Ativos
	- Entrada
		- Inventário de ativos
	- Saída
		- Lista de ativos e processos de negócio relacionados
> [!note] 🔥
> **Ativos Primários:
**- Processo e Atividades de Negócio
- Informação

**Ativos Secundários (Suporte e Infraestrutura):
**- Hardware
- Software
- Rede
- RH
- Instalações Físicas
- Estrutura da Organização
- Identificação das Ameaças
	- Fonte que gera uma ação e que possa acarretar em uma consequência
	- Entrada
		- Informações sobre ameaças obtidas a partir de análise crítica de incidentes, **por tipo de ativo**
		- Pode ser obtido internamente ou externamente, via catálogos externos
	- Saída
		- Lista de ameaças por tipo e fonte
- Identificação dos Controles Existentes
	- Entrada
		- Documentações, planos
	- Ação
		- Controles identificados e planejados sejam implementados
	- Saída
		- Lista de controles planejados e implementados
		- Status de utilização
- Identificação das Vulnerabilidades
	- Entrada
		- Lista de ameaças conhecidas
		- Lista de ativos
		- Lista de controles
	- Ação
		- Identificação das vulnerabilidades que possam ser exploradas pelas ameaças identificadas
	- Saída
		- Lista de vulnerabilidades associadas a ameaças existentes
		- Lista de vulnerabilidades que não se refere a nenhuma ameaça identificada para a análise
- Identificação das Consequências
	- Resultado do encontro de ameaça com vulnerabilidade
	- Entrada
		- Lista de ativos e processos
		- Lista de ameaças
		- Lista de vulnerabilidades relacionadas aos ativos e relevância
	- Ação
		- Identificação das consequências resultantes
	- Saída
		- **Lista de cenários **de incidentes com suas consequências associadas aos ativos e processos

### 2.2. Análise dos Riscos

- Metodologias
	- Análise qualitativa
		- mais simples
		- **aspectos subjetivos**
		- considera magnitude das consequências (pequena, média, grande)
		- considera probabilidades (baixa, media, alta)
		- Desvantagem: subjetividade
	- Análise quantitativa
		- Escala precisa de valores numéricos
		- Busca dados de diversas fontes
		- Depende da exatidão e integralidade dos valores numéricos
		- Utiliza dados históricos
		- Desvantagem: ausência de dados históricos para novos riscos
- Avaliação das consequências
	- Entrada
		- **Lista de cenários**
	- Ação
		- Avaliação das consequências, baseados nos cenários
	- Saída
		- Lista de consequências avaliadas
- Avaliação das probabilidades
	- Entrada
		- **Lista de cenários**
		- Listas com os controles existentes
	- Ação
		- Avaliação das probabilidades
	- Saída
		- Lista de consequências avaliadas referentes a cada cenário
- Determinação do nível de risco
	- Entrada
		- Lista de cenários com suas consequências associadas e suas probabilidades
	- Ação 
		- Estimativa do risco
	- Saída
		- Lista de risco com níveis de valores designados

### 2.3. Avaliação de riscos

- Entada
	- Lista de riscos com níveis de valores designados
	- Critérios para avaliação de riscos
- Ação
	- Comparação dos riscos com os critérios para aceitação
- Saída
	- Lista de riscos priorizados de acordo com os critérios

## 3. Tratamento do Risco

- Entrada
	- Lista de riscos priorizada
- Ação
	- Controles para tratamento
- Saída
	- Plano de tratamento de riscos
	- Lista de riscos residuais
- As quatro opções de tratamento **Não são mutuamente exclusivas**

### 3.1. Tratamentos Possíveis

> [!note] 🔥
> **MORA COM:**
- **MO**dificação do risco
- **R**etenção do risco
- **A**ção de evitar o risco
- **COM**partilhamento do risco

- Modificação do Risco
	- Inclusão, exclusão ou alteração de controles
	- Correção
	- eliminação
	- prevenção
	- minimizar o impacto
	- dissuasão
	- detecção
	- recuperação
	- monitoramento
	- conscientização
- Retenção do Risco
	- Quando o risco atende ao critério de aceitação existente
- Ação de evitar o Risco
	- Evitar a condição de origem da ameaça
- Compartilhamento do Risco
	- Transferência do risco para um terceiro, que tenha expertise no gerenciamento
	- **Este compartilhamento pode alterar outros riscos existentes**

## 4. Aceitação de riscos

- Entrada
	- Plano de tratamento de risco
	- Avaliação dos riscos residuais
- Ação
	- Decisão formal e registrada de aceitação dos riscos
- Saída
	- Relação de riscos aceitos
	- **Justificativa de aceitação dos que não satisfaçam os critérios**

## Processo de suporte: Comunicação e consulta do risco

- Entrada
	- Todas as informações de riscos obtidas das atividades de gestão
- Ação
	- Informações compartilhadas entre os tomadores de decisão e partes interessadas
- Saída
	- Entendimento contínuo do processo e resultados obtidos

## Processo de suporte: Monitoramento e análise crítica

### Monitoramento

- Entrada
	- Todas as informações de riscos obtidas das atividades de gestão
- Ação
	- Riscos e **fatores** sejam avaliados criticamente
- Saída
	- Alinhamento com os objetivos de negócio

### Melhoria contínua

- Entrada
	- Todas as informações de riscos obtidas das atividades de gestão
- Ação
	- Monitoramento e melhoria dos **processos**
- Saída
	- Garantia permanente de relevância
	- Atualização do processo

# ISO 31000

- Fornece princípios e diretrizes para implementação eficaz de um sistema de gestão de riscos
- Qualquer organização
- O núcleo da 31000 é o processo de gestão de riscos
	- Abordagem iterativa que auxilia na definição de estratégias, alcance de metas e tomada de decisões fundamentadas
- Fornece princípios, estrutura e processos que servem como base para essa gestão de riscos

![[Untitled 278.png]]

- **Gerenciar riscos considera tanto o contexto externo quanto o interno da organização, o que inclui fatores como o comportamento humano e os aspectos culturais.**

## Definições importantes

- Risco
	- Efeito da **incerteza** nos objetivos. 
	- Pode ser positivo, negativo ou ambos, abordando oportunidades e ameaças.
- Gestão de Riscos
	- **Atividades coordenadas** para direcionar e controlar uma organização em relação ao risco.
- Evento
	- **Ocorrência ou mudança de um conjunto específico de circunstâncias.**
	- Pode ter uma ou mais ocorrências, várias causas e consequências.
	- **Também pode ser algo esperado que não ocorre**, ou algo não esperado que ocorre. 
	- Um evento pode ser uma fonte de risco.
- Consequência
	- **Resultado de um evento** que afeta objetivos. 
	- Pode ser certo ou incerto, com efeitos diretos ou indiretos positivos ou negativos. 
	- As consequências podem ser expressas** qualitativa ou quantitativamente,** e qualquer consequência pode escalar através de efeitos cascata e cumulativos.
- Controle
	- Medida que **mantém e/ou modifica o risco**
	- Os controles incluem, mas não se limitam a, qualquer processo, política, dispositivo, prática ou outras condições e/ou ações que mantenham e/ou modifiquem o risco.
	- Os controles podem não sempre exercer o efeito modificador pretendido ou assumido

## Princípios

- Elementos da gestão de riscos eficaz

![[Untitled 279.png]]

- Integrada
	- A gestão de riscos é parte integrante de todas as atividades organizacionais.
- Estruturada e abrangente
	- Uma abordagem estruturada e abrangente para a gestão de riscos contribui para resultados consistentes e comparáveis.
- Personalizada
	- A estrutura e o processo de gestão de riscos são personalizados e proporcionais aos contextos externo e interno da organização relacionados aos seus objetivos.
- Inclusiva
	- O envolvimento apropriado e oportuno das partes interessadas possibilita que seus conhecimentos, pontos de vista e percepções sejam considerados. 
	- Isso resulta em melhor conscientização e gestão de riscos fundamentada.
- Dinâmica
	- Riscos podem emergir, mudar ou desaparecer à medida que os contextos externo e interno de uma organização mudem. 
	- A gestão de riscos antecipa, detecta, reconhece e responde a estas mudanças e eventos de uma maneira apropriada e oportuna.
- Melhor informação disponível
	- As entradas para a gestão de riscos são baseadas em informações históricas e atuais, bem como em expectativas futuras. 
	- A gestão de riscos explicitamente leva em consideração quaisquer limitações e incertezas associadas a estas informações e expectativas. 
	- Convém que a informação seja oportuna, clara e disponível para as partes interessadas pertinentes.
- Fatores Humanos e culturais
	- O comportamento humano e a cultura influenciam significativamente todos os aspectos da gestão de riscos em cada nível e estágio.
- Melhoria contínua
	- A gestão de riscos é melhorada continuamente por meio do aprendizado e experiências.

## Estrutura

<!-- Column 1 -->
![[Untitled 280.png]]

<!-- Column 2 -->
![[Untitled 281.png]]

- Integração
	- Gestão de riscos integrada a todas as atividades da organização
- Concepção
	- Entendimento da organização e seus contextos
	- Atribuição de papéis
	- Comunicação eficaz
- Implementação
	- Aplicação da prática de gestão de riscos
	- Escolha de opções de tratamento
	- Planos de execução
- Avaliação
	- Análise crítica dos riscos identificados
	- Considerar consequências e probabilidades
- Melhoria
	- Adaptação contínua da gestão de riscos
	- Lições aprendidas
- Liderança e comprometimento
	- Participação ativa e apoio da liderança
	- Assegurar comprometimento
		- Personalização e implementação
		- Declaração ou política
		- Alocação de recursos
		- Atribuição de autoridades e responsabilidades
	- A Alta Direção **assume a responsabilidade** pela gestão de riscos, enquanto os órgãos de supervisão têm a incumbência de **supervisionar** esse processo.

## Processos

![[Untitled 282.png]]

### Comunicação e Consulta

![[Untitled 283.png]]

### Escopo, contexto e critério

![[Untitled 284.png]]

![[Untitled 285.png]]

### Processo de avaliação de riscos

![[Untitled 286.png]]

![[Untitled 287.png]]

![[Untitled 288.png]]

![[Untitled 289.png]]

### Tratamento de riscos

![[Untitled 290.png]]

> [!note] 🔥
> **O tratamento de riscos também pode introduzir novos riscos que precisem ser gerenciados**

![[Untitled 291.png]]

### Monitoramento e análise crítica

![[Untitled 292.png]]

![[Untitled 293.png]]

![[Untitled 294.png]]

# ISO 31010

- Fornece técnicas, ferramentas e métodos a serem utilizados para a avaliação e análise de riscos
- Descreve como escolher a técnica mais adequada dependendo do contexto, objetivos e recursos disponíveis.
- A escolha da técnica depende de fatores como a natureza da atividade, os tipos de riscos, a complexidade e a criticidade das decisões a serem tomadas.

### Técnicas de Identificação de Riscos

1. **Brainstorming**: Técnica de geração de ideias em grupo para identificar riscos potenciais.
2. **Entrevistas Estruturadas ou Semiestruturadas**: Coleta de informações de especialistas por meio de entrevistas.
3. **Listas de Verificação**: Uso de listas de verificação predefinidas para identificar riscos comuns.
4. **Análise SWOT (Forças, Fraquezas, Oportunidades, Ameaças)**: Identificação de riscos com base nos pontos fortes e fracos da organização e nas oportunidades e ameaças do ambiente externo.
5. **Análise de Cenários**: Desenvolvimento de cenários futuros possíveis para identificar riscos associados.
6. **Revisão de Literatura e Documentos**: Análise de documentos e literatura para identificar riscos históricos ou teóricos.
7. **Análise Preliminar de Risco (APR)**

### Técnicas de Análise de Riscos

8. **Análise de Modos e Efeitos de Falha (FMEA)**: Identificação de modos de falha e seus efeitos para determinar a criticidade.
9. **Análise de Árvore de Falhas (FTA)**: Representação gráfica das várias combinações de falhas que podem resultar em um evento indesejável.
10. **Análise de Causa Raiz**: Identificação das causas principais de um problema ou evento.
11. **Análise de Consequências**: Avaliação das consequências potenciais dos riscos identificados.
12. **Análise de Impacto nos Negócios (BIA)**: Avaliação do impacto dos riscos nas operações de negócios.
13. **Análise de Monte Carlo**: Uso de simulação estocástica para avaliar a variabilidade e a incerteza dos riscos.

### Técnicas de Avaliação de Riscos

14. **Matrizes de Risco**: Classificação de riscos em uma matriz de probabilidade e impacto para priorização.
15. **Árvores de Decisão**: Uso de diagramas de árvore para representar decisões e suas possíveis consequências.
16. **Análise Custo-Benefício**: Avaliação dos custos e benefícios das opções de tratamento de risco.
17. **Análise de Sensibilidade**: Avaliação da sensibilidade das conclusões aos dados de entrada.

### Técnicas de Tratamento de Riscos

18. **Plano de Mitigação de Riscos**: Desenvolvimento de planos para reduzir a probabilidade ou impacto dos riscos.
19. **Transferência de Risco**: Uso de seguros ou outros instrumentos para transferir o risco para terceiros.
20. **Aceitação de Risco**: Decisão de aceitar o risco sem tomar medidas específicas para mitigá-lo.
21. **Evitação de Risco**: Modificação dos planos para evitar o risco completamente.

### Técnicas de Monitoramento e Revisão

22. **Auditorias e Inspeções**: Revisões sistemáticas e estruturadas para garantir a eficácia dos controles de risco.
23. **Indicadores Chave de Risco (KRIs)**: Desenvolvimento de métricas para monitorar os riscos em tempo real.
24. **Revisões Periódicas de Riscos**: Revisão regular dos riscos e das estratégias de mitigação para garantir a relevância e eficácia contínuas.

### Técnicas Adicionais

25. **Diagrama de Causa e Efeito (Diagrama de Ishikawa ou Espinha de Peixe)**: Identificação de causas potenciais de um problema ou evento de risco.
26. **Análise de Redes Bayesianas**: Uso de redes probabilísticas para modelar a incerteza e a interdependência dos riscos.
27. **Análise de Decisão Multi-Critério (MCDA)**: Avaliação de alternativas com base em múltiplos critérios.
28. **Benchmarking**: Comparação com práticas de referência para identificar riscos e oportunidades de melhoria.

### **Análise Preliminar de Riscos (APR)**

A APR é uma técnica amplamente utilizada no gerenciamento de riscos. Seu objetivo principal é identificar **quais são os riscos mais significativos** e discernir os riscos **menos significativos** no início do processo de análise. Isso permite que os recursos destinados ao controle de riscos sejam alocados de maneira mais eficiente, focando nos riscos que podem ter os maiores impactos negativos.

Além disso, a APR não ignora os riscos que ocorrem com frequência, mesmo que individualmente possam parecer menos significativos. Ela reconhece que esses riscos podem ter um **efeito cumulativo importante** e, portanto, devem ser levados em consideração no planejamento e execução das estratégias de mitigação.

É importante destacar que a APR é uma ferramenta preventiva, sendo utilizada nas fases iniciais de um projeto ou processo. Ela ajuda a criar uma base sólida para a gestão de riscos, garantindo que **nenhum risco relevante seja negligenciado**.

### **Estudo de Perigos e Operabilidade (HAZOP)**: 

Enfoca a identificação de perigos e problemas operacionais específicos em sistemas complexos. É mais detalhado e utilizado em fases posteriores.

### **Análise de Árvore de Falhas (FTA)**: 

Técnica voltada para a análise de falhas e suas causas. Foca na identificação das causas-raiz através da aplicação de lógica booleana.

### **Análise de Impactos nos Negócios (BIA)**: 

Avalia os potenciais impactos de interrupções nos processos de negócios. É mais aplicada em continuidade de negócios e menos na identificação inicial de riscos.

### **Análise de Causa-Raiz (RCA)**: 

Técnica que se concentra em identificar as causas subjacentes de problemas ou falhas após a ocorrência dos mesmos.

### Análise de Monte Carlo:

- Variáveis incertas são modeladas como uma distribuição de probabilidades (normal, triangular, uniforme)
- São feitas simulações com valores diferentes destas variáveis, compondo o cenário total da simulação para gerar uma distribuição global, onde pode-se estimar o custo mais provável e os limites superiores e inferiores

### Exemplo Prático

Imagine que estamos estimando o custo de um projeto, que depende de três variáveis: custo de mão-de-obra, custo de materiais e custo de equipamentos. Essas variáveis apresentam uma certa incerteza, representada pelas seguintes distribuições:

- **Custo de Mão-de-Obra**: Distribuição Normal, média de $50,000, desvio padrão de $5,000.
- **Custo de Materiais**: Distribuição Triangular, com mínimo de $20,000, mais provável $25,000, e máximo de $30,000.
- **Custo de Equipamentos**: Distribuição Uniforme, entre $10,000 e $15,000.

Para realizar a Análise de Monte Carlo:

29. **Configurar o Modelo**: Definimos o modelo de custo total como a soma das três variáveis: `Custo Total = Custo de Mão-de-Obra + Custo de Materiais + Custo de Equipamentos`.
30. **Simulações**: Executamos milhares de simulações, onde em cada uma:
	- Extraímos um valor para cada variável de acordo com suas distribuições.
	- Calculamos o custo total para cada conjunto de valores.
31. **Análise dos Resultados**: Ao final, obtemos uma distribuição dos custos totais simulados. Com esses dados, podemos calcular:
	- **Média do custo total**: Valor esperado do custo.
	- **Percentis (e.g., P90)**: Valor máximo que o custo total provavelmente não ultrapassará em 90% das simulações.
	- **Probabilidade de Exceder o Orçamento**: Se houver um orçamento definido, a porcentagem de simulações que excedem esse valor.

![[SubPages/Pessoal/images/image 72.png]]
