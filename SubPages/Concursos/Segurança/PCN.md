---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2024-10-25T08:27:00
Owner:
  - Eduardo Quinalha
---
# Gestão de Continuidade de Negócios

> [!tip] 💡
> Principal princípio de SI associado: DISPONIBILIDADE

> [!tip] 💡
> PCN ≠ Plano de Contingência

- Envolve investimentos e recursos
- Controles de SI como resultado de ampla análise de riscos

# ISO 15999 - Gestão de Continuidade de Negócio

> [!note] 🔥
> A norma sugere que **a alta direção seja responsável pela gestão e governança**, mantendo as estratégias e planos de recuperação para garantir a continuidade dos negócios. Isso é crucial para assegurar que a organização esteja preparada para enfrentar possíveis interrupções, sejam elas relacionadas a incidentes de segurança da informação ou a outros eventos que possam afetar a operação do negócio.

- **Etapas Básicas - PDCA**
	- **Entendimento dos Requisitos de CN da organização**
		- Análise de **impacto **no negócio
		- Identificação de **atividades críticas**
		- Determinando **requisitos **de continuidade
		- Avaliando ameaças a atividades críticas (**avaliação de riscos**)
		- Determinando **escolhas**
			- Resultado da avaliação de riscos
			- Determinação de medidas que reduzam a chance de interrupção, reduzam o período de interrupção, limitem o impacto
		- **Aprovação**
			- Da alta direção
	- **Determinação das estratégias de GCN**
		- **Opções **de estratégia
> [!note] 👉🏻
> Avaliar fatores como:

			- Período máximo de interrupção tolerável
			- Custos de implementação da estratégia
			- Consequência de não agir
> [!note] 👉🏻
> Considerar contextos diferenciados em termos de recursos, como:

			- Pessoas
			- Instalações
			- Tecnologia
			- Informação
			- Suprimento
			- Partes Interessadas
		- Obter **aprovação **das escolhas
	- **Desenvolvimento e Implementação de GCN: Resposta e Recuperação**
		- Estrutura de **Resposta a Incidentes**
			- Confirmar a natureza e extensão
			- Tomar controle da situação
			- Controlar o incidente
			- Comunicar-se com partes interessadas
		- **Desenvolvimento do PCN**
	- **Exercício, Teste, Manutenção e Análise Crítica de GCN**
		- Programa de testes
		- Testando os preparativos
			- Testes realistas, planejados e acordados
			- O teste deve minimizar a chance de que ocorra um incidente como resultado deste
- **Documentação**
> [!note] 👉🏻
> Os indivíduos responsáveis por manter a continuidade de negócios devem criar e manter a documentação de continuidade de negócios, incluindo os seguintes documentos:

	- Política de GCN
		- Declaração do escopo de GCN
		- Termos de Referência de GCN
	- Análise de impacto dos negócios
	- Avaliação de riscos e ameaças
	- Estratégias de GCN
	- Programa de Conscientização
	- Programa de treinamento
	- Planos de gerenciamento de incidentes
	- Planos de continuidade de negócio
	- Planos de recuperação de negócios
	- Agenda de testes e relatórios
	- Contratos e acordos de níveis de serviço

# Atualização - ISO 22301 e ISO 22313

A norma foi substituída em 2015 por outras duas:

15999-1 → 22313:2020 - Código de prática - Recomendações para o **estabelecimento** **de GCN**

15999-2 → 22301:2020 - Requisitos - Estabelece requisitos para estabelecer e gerir GCN (SGCN)

## Ciclo de Vida

GCN possui um ciclo de vida composto por 6 elementos:

1. **Gestão do programa de GCN**
2. **Entendendo a Organização**
3. **Determinando a Estratégia de Continuidade de Negócios**
4. **Desenvolvendo e Implantando uma Resposta de GCN**
5. **Testando, Mantendo e Analisando Criticamente os Preparativos de GCN**
6. **Incluindo a GCN na Cultura Organizacional**

![[Untitled 295.png]]

## Modelo PDCA

![[Untitled 296.png]]

**Plan (Estabelecer): **Estabelecer uma política de continuidade de negócios, objetivos, metas, controles, processos e procedimentos pertinentes para a melhoria da continuidade de negócios, de forma a ter resultados alinhados com os objetivos e políticas gerais da organização.
**Do (Implementar e operar): **Implementar e operar a política de continuidade de negócios, controles, processos e procedimentos. 

**Check: Monitorar e analisar criticamente):** Monitorar e analisar criticamente o desempenho em relação aos objetivos e à política de continuidade de negócios, reportar os resultados à direção para análise critica e definir e autorizar ações de melhorias e correções.
**Act (Manter e melhorar):** Manter e melhorar o SGCN, tomando ações corretivas e preventivas, baseadas nos resultados da análise crítica pela Direção e reavaliando o escopo do SGCN e as políticas e objetivos de continuidade de negócios.

## Definições

- **Continuidade de Negócios:** 
	- Capacidade da organização em continuar a entrega de produtos ou serviços em um nível aceitável previamente definido após incidentes de interrupção.
- **Gestão de Continuidade de Negócios (GCN): **
	- Processo abrangente de gestão que **identifica ameaças **potenciais para uma organização e os **possíveis impactos** nas operações de negócio caso estas ameaças se concretizem. 
	- Este processo fornece uma estrutura para que se desenvolva uma resiliência organizacional que seja capaz de responder eficazmente e salvaguardar os interesses das partes interessadas, a reputação e a marca da organização e suas atividades de valor agregado.
- **Sistema de Gestão de Continuidade de Negócios (SGCN):**** **
	- **Parte do sistema global de gestão** que estabelece, implementa, opera, monitora, analisa criticamente, mantem e melhora a continuidade de negócios.
- **Plano de Continuidade de Negócios: **
	- **Procedimentos documentados** que orientam as organizações a responder, recuperar, retomar e restaurar a um nível predefinido de operação após interrupção.

# Plano de Continuidade de Negócios de TI - ISO/IEC 27035-1

- Conjunto de estratégias e planos de ação
- Serviços essenciais → identificados e preservados após a ocorrência de um desastre

## Pilares

Três pilares são essenciais ao elaborar o Plano de Continuidade de Negócios (PCN):

7. **Análise de risco**: o que de ruim pode vir a acontecer? Ou seja, quais as principais ameaças?
8. **Análise de impacto: **de que forma eventuais ameaças podem impactar o negócio da
organização?
9. **Planejamento Estratégico:** se uma ameaça se apresentar, quais atitudes e ações se fariam necessárias para a retomada das operações da empresa?

## Componentes

**O plano de Continuidade de Negócios deve conter:**

- Papéis e Responsabilidades
- Processo para ativar a estrutura de resposta a incidentes
- Detalhes para gerenciar impactos imediatos
- Plano de comunicação (funcionários e familiares, contatos de emergência, etc)
- Plano de recuperação das atividades prioritárias dentro de um prazo definido
- Comunicação externa (imprensa, mídia, etc…)
- Processo de retorno à normalidade

**Dentro de cada plano, deve existir os seguintes elementos:**

- propósito e escopo;
- objetivos;
- critérios e procedimentos para sua ativação;
- procedimentos de implementação;
- papéis, responsabilidades e autoridades;
- requisitos e procedimentos de comunicação;
- Interdependências internas, externas e suas interações;
- recursos necessários; e
- fluxo de informações e processos documentados.

## Fases do processo de resposta

> [!note] 🔥
> **I AConteceu CAGada**

- **I**dentificação de incidentes
- **A**valiação e qualificação
- **C**oleta de inteligência
- **C**ontenção, erradicação e recuperação
- **A**nálise
- **G**eração de relatórios

## Subplanos

- **Plano de Contingência (Emergência) - PC**
	- Usado em último caso, quando as **prevenções tiverem falhado**
	- Ações mais imediatas **PARA MANUTENÇÃO DA CONTIUIDADE DO NEGÓCIO**
- **Plano de Administração de Crises - PAC**
	- Define funções e responsabilidades
	- Acionamento das ações de contingência
	- Antes, durante a após a ocorrência
- **Plano de Recuperação de Desastres - PRD**
	- Após o controle da contingência
	- Retomada dos níveis originais de recuperação
- **Plano de Continuidade Operacional - PCO**
	- Acionado por primeiro, antes do PC
	- garanti**r a continuidade das operações críticas da organização durante uma crise**
	- Restabelecer os principais ativos
	- Redução de tempo de queda e impacto
![[Untitled 297.png]]

## Outros Conceitos

- BIA - Business Impact Analysis
	- Análises negociais
- RTO - Recovery Time Objective
	- Meta
	- Olhar p/ frente
	- Considera os sistemas críticos
- RTA - Recovery Time Actual
	- Temporizador desde a falha até o momento atual
- RPO - Recovery Point Objective
	- Delta de tempo entre o último backup e uma provável falha
- MAO / MTPD - Maximum Acceptable Outage / Maximum Tolerable Period of Disruption
	- Meta de tempo tolerável, acima do RTO
- WRT - Work Recovery Time
	- Tempo de recuperação considerando todos os sistemas
- MTTR
- MTBF

![[Untitled 298.png]]

![[Untitled 299.png]]

- Dupla abordagem
	- Por exemplo, dois links com trajetos físicos diferentes
- **Hot Site***
	- Permanece aitvo, compartilhando recursos.
	- No caso de falha de algum deles, não há qualquer prejuízo de dados
	- Há sincronismo entre os sites e inclusive podem estar atendendo demandas em conjunto no modelo de balanceamento de carga
- **Cold Site**
	- O segundo ambiente possui a infraestrutura necessáira, suficiente para o reestabelecimento dos serviços
	- Porém não fica ligado, e não compartilha informações de forma online
	- Em caso de necessidade, vai precisar ser preparado, inclusive com recuperação de backup, o que pode levar algum tempo
- **Mirror Site***
	- Algumas bancas (CESPE), considera que o modelo de Hot Site com o sincronismo completo **seria na verdade um Mirror Site**
	- Nestes casos, Hot Site seria então uma estrutura completa, pronta para assumir, no entanto, sem o sincronismo dos dados
	- Como vantagem, é mais barato que o Mirror Site e pode restaurar os serviços em um tempo razoável

# Programas/Exercícios de GCN

## 1 - Funcional

- Simula um cenário real
- Visa testar a capacidade da organização de responder e se recuperar
- Pode ser realizado das seguintes formas:
	- Em escala
	- Total
	- Parcial

## 2 - Experimental

- Mais abrangente que o funcional
- Implementação prática de cenário de emergência
- Pode incluir a participação de diversas equipes e utilização de recursos reais
- Testa um novo procedimento, tecnologia ou ferramenta
- Menos disruptivo para as operações da organização

## 3 - De Mesa

- Simula um cenário através de discussões e análises
- Permite que os participantes discutam seus papéis e responsabilidades
- Permite identificar áreas de melhoria
- Tipo de exercício menos dispendioso que pode ser realizado com mais frequência

## 4 - De Interrupção Parcial

- Interrompe uma parte específica das operações para testar a resposta e capacidade de recuperação
- Permite o teste de planos específicos
- Pode ser realizado com impacto mínimo nas operações

## 5 - De Interrupção Total

- Simula uma interrupção completa
- Tipo mais disruptivo e realista

## 6 - Outros tipos

### De Conscientização

- Treinam os funcionários sobre seus papéis e responsabilidades

### De Treinamento

- Treinam as equipes de resposta a incidentes como responder a diferentes cenários

### De Comunicação

- Testa a capacidade de se comunicar durante uma interrupção

![[PCN.png]]

> 8.7 Conteúdo do PCN
> 8.7.2 Planos de ação/Listas de tarefas
> 
> **Convém que o plano de ação inclua uma lista estruturada de ações e tarefas em ordem de prioridade**, destacando-se:
> 
> **a) como o PCN é ativado;**
> 
> b) as pessoas responsáveis por ativar o plano de continuidade de negócios;
> 
> c) o procedimento que esta pessoa deve adotar ao tomar esta decisão;
> 
> d) as pessoas que devem ser consultadas antes desta decisão ser tomada;
> 
> e) as pessoas que devem ser informadas quando a decisão for tomada;
> 
> f) quem vai para onde e quando;
> 
> g) quais serviços estão disponíveis, aonde e quando, incluindo como a organização mobilizará seus recursos externos e de terceiros;
> 
> h) como e quando esta informação será comunicada; e
> 
> i) se relevante, procedimentos detalhados para soluções manuais, recuperação dos sistemas etc.
> 
> 8.7.3 Recursos necessários
> 
> Convém que os recursos necessários para a continuidade e recuperação dos negócios sejam identificados em diferentes pontos no tempo. Estes podem incluir:
> 
> a) pessoas, o que pode incluir:
> 
> ⎯ segurança,
> 
> ⎯ logística de transporte,
> 
> ⎯ necessidades de bem-estar e
> 
> ⎯ gastos de emergência;
> 
> b) instalações;
> 
> c) tecnologia, incluindo comunicações;
> 
> d) informações, o que pode incluir:
> 
> ⎯ detalhes financeiros (por exemplo, folha de pagamento),
> 
> ⎯ registros de contas de clientes,
> 
> ⎯ detalhes de fornecedores e partes interessadas,
> 
> ⎯ documentos legais (por exemplo, contratos, apólices de seguro, escrituras etc.), e
> 
> ⎯ outros documentos de serviços (por exemplo, acordos de nível de serviços);
> 
> e) suprimentos; e
> 
> f) gestão das partes interessadas e da comunicação com estas.
> 
> 8.7.4 Responsáveis
> 
> Convém que a organização identifique e designe um responsável para gerenciar as fases da continuidade e da recuperação dos negócios que ocorrem após uma interrupção de serviços.
> 
> 8.7.5 Formulários e anexos
> 
> Quando apropriado, convém que o PCN possua detalhes de contato atualizados das agências pertinentes internas e externas, organizações e fornecedores que possam ser necessários para o suporte da organização.
> 
> Convém que o plano de continuidade de negócios inclua um registro de incidentes ou formulários para o registro
> 
> de informações vitais, principalmente como conseqüência de decisões tomadas durante sua execução.
> 