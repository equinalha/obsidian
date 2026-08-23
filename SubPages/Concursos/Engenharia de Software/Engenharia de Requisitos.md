---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2024-10-27T08:05:00
Owner:
  - Eduardo Quinalha
---
# Engenharia de Requisitos

## Etapas

- **Desenvolvimento de Requisitos**
	- Os requisitos acordados com os stakeholders formam a baseline de requisitos
		- Fontes de informação
		- **Elicitação de requisitos**
			- Investigação dos requisitos
			- Etapa de intensa comunicação com stakeholders
			- No caso de produto inovador ou disruptivo, cabe a utilização de brainstorming ou design thinking
		- **Análise de requisitos**
			- Aprofundamento do entendimento acerca dos requisitos
			- Encontrar conflitos, especialmente quanto aos requisitos não funcionais (voltados a qualidade)
			- sistemas complexos exigem uma análise mais aprofundade e pode se confundir com a etapa de design
		- **Especificação de requisitos**
			- Documentação dos requisitos
		- **Validação de requisitos**
			- Validação junto aos stakeholders
			- Checklist
			- Workshops
			- Protótipos
- **Gerenciamento de Requisitos**
	- Os novos requisitos acordados com stakeholders formam a nova baseline de requisitos
		- Mudanças: usuários, clientes, estratégias, leis, etc…
		- Identificação de mudanças: Mudanças ocorridas no contexto do projeto
		- Manutenção da rastreabilidade: Construção da rastreabilidade entre as fontes de informação
		- Análise de impacto: Avaliação do impacto das mudanças sobre os requisitos
		- Tomada de decisão: Decisão sobre a mudança

## Ciclo de vida de software

1. **Concepção**: Identificação da ideia inicial e nálise da viabilidade
	- Primeiros requisitos aparecem na forma de objetivos de negócio ou meta
	- Podem surgir também os **requisitos de projeto****:** restrições ao projeto em si que podem estar relacionados com prazos, recurços e orçamento
	- **Requisitos de processos** que podem impor restrições sobre a forma como o projeto será desenvolvido: Método, por exemplo
2. **Desenvolvimento**: Especificação, implementação e implantação
	- Todas as atividades necessárias para a produção do software, incluindo: requisitos, análise, design, implementação, testes, homologação e implantação
	- Engloba também as atividades de suporte e gestão do desenvolvimento
3. **Manutenção**: Manutenção corretiva e adaptativa do produto
	- Bugs
	- Melhorias
4. Descontinuação: Desativação do software quando ele se torna obsoleto ou não é mais necesário

# Requisitos de Software

- **Requisitos de Negócio e Regras de Negócio**
	- Representam os objetivos de negócio que precisam ser atendidos
	- Requisitos de alto nível que se desdobram nos demais níveis
	- Motivo pelo qual o sistema está sendo desenvovido
- **Requisitos de Usuário**
	- Tarefas que o usuário precisa executar
	- Características importantes para a satisfação do usuário
- **Atributos de Qualidade ou Não funcionais**
	- Características em outras dimensões que não as funcionalidades
	- representa o “como”
	- Desempenho, segurança, usabilidade
- **Interfaces Externas**
	- Interfaces com outros sistemas
- **Requisitos de Sistema**
	- Requisitos de sistema como um todo
	- Hardware e software
- **Restrições**
	- Requisitos de processo e de projeto que afetam como o produto será desenvolvido
- **Requisitos Funcionais**
	- Funcionalidades do sistema
	- Visa satisfazer às regras de negócio

A saída dos requisitos funcionais vai para a **especificação de requisitos**, que formaliza e documenta estes requisitos.

Já as restrições vão para o **plano de projeto**

## Priorização de Requisitos

- Potencial de valor agregado
- Dependência do requisito
- Requisitos implícitos que estavam invisíveis
- Experiência com a tecnologia
- Experiência no domínio de aplicação
- Relacionamento com outros sistemas
- Demandas de implementações para atender determinações legais
- Requisitos que não possuem alternativas manuais aceitáveis

## Critérios de Qualidade

- Ótica da escrita: o documento deve ser visto sob a ótica de quem lê
- Tamanho das frases: Priorizar frases curtas, concisas, objetivas
- Correção na escrita
- Uso da voz ativa
- Uso da forma positiva
- Evitar termos ambíguos : com alguns, melhor, muitos poucos, robusto, adequado, rápido, amigável
- Evitar acrônimos e jargões
- O que vs como

# Técnicas de Elicitação de Requisitos

- Entrevista
	- Adequado para
		- Existência de pessoas que detêm o conhecimento necessário e estão disponíveis
		- Captar informações subjetivas
		- Identificar o fluxo de trabalho e de documentos
- Reunião
	- Adequado para
		- Obter resposta rápida de várias pessoas
		- Quando existem questões a serem esclarecidas
		- Envolver o grupo na tomada de decisão
- Brainstorming
	- Adequado para
		- Ambiente descontraído e informal
		- Soluções inovadoras e criativas
		- Novos produtos
	- Assim como reunião, requer a participação de mais pessoas
	- Requer uma dinâmica inicial
	- Fases
		- Aquecimento (dinâmica)
		- Geração das ideias
		- Encerramento (agrupamento das ideias)
		- Pode ser realizado uma etapa adicional de votação das melhores ideias
- Observação
	- Adequado para
		- Fluxo de papéis e de trabalho é relevante
		- Forma de executar o trabalho
		- Influência do ambiente real é importante
	- Exame dos fatos e fenômenos
	- Confirmar informações obtidas das entrevistas, questionários ou documentos
- Questionário
	- Adequado para
		- Falta de tempo de entrevistar todas as pessoas
		- Fins estatísticos
		- Pessoas separadas geograficamente
	- Não recomendado para grupos pequenos de pessoas
	- Tipos de questões
		- Escala de valores → Normalmente de 1 a 5
		- Escalas de ranqueamento → Fornecida a lista de requisitos, é solicitado ao usuário elencar os mais importantes
		- Escalas de estimativa de magnitude → Dado um valor ao requisito menos prioritário, solicitado quantas vezes o requisto X é mais prioritário que o Y
		- Questões divididas ou desdobradas
		- Questões de afunilamento

Normalmente não se utiliza apenas uma técnica, mas todas que forem necessárias ou apropriadas para cada caso

![[Untitled 560.png]]

## Tipos de fontes de informação

- Stakeholders
- Documentos
- Sistemas em operação

## Classes de usuários

- **favorecidos**: diretamente relacionados com a satisfação dos objetivos
- **não favorecidos:** Não devem ter acesso ao produto (ex: hackers)
- **ignorados**: podem ter acesso, porém não são a razão de existir do produto
- **outras classes**

## Etapas

5. Compreender o contexto
6. Identificar as fontes de informação
7. Selecionar a técnica de elicitação
8. Preparar a elicitação de requisitos
9. Realizar  elicitação de requisitos
10. Organizar os reqisitos

# Requisitos não funcionais

| Qualidade externa | Descrição |
| --- | --- |
| Disponibilidade | Extensão na qual os serviços do sistema estão disponíveis<br>quando e onde são necessários |
| Instalabilidade | Quão fácil é instalar, desinstalar e reinstalar corretamente a<br>aplicação |
| Integridade | A extensão na qual o sistema protege contra imprecisão e<br>perda de dados |
| Interoperabilidade | Quão fácil o sistema pode interconectar e trocar dados com<br>outros sistemas e componentes |
| Desempenho | Quão rápido e previsivelmente o sistema responde às entradas do usuário e outros eventos |
| Confiabilidade | Por quanto tempo o sistema roda antes de apresentar uma falha |
| Robustez | Quão bem o sistema responde a uma condição inesperada<br>de operação |
| Proteção | Quão bem o sistema protege contra ferimentos e danos |
| Segurança | Quão bem o sistema protege contra acesso não autorizado à<br>aplicação e seus dados |
| Usabilidade | Quão fácil é para as pessoas aprenderem, lembrarem e<br>utilizarem o sistema |

| Qualidade Interna | Descrição |
| --- | --- |
| Eficiência | Quão eficientemente o sistema usa os recursos do computador |
| Modificabilidade | Quão fácil é manter, modificar, melhorar e reestruturar o sistema |
| Portabilidade | Quão facilmente o sistema pode ser colocado em operação<br>em outros ambientes operacionais |
| Reusabilidade | Em que extensão os componentes podem ser usados em<br>outros sistemas |
| Escalabilidade | Quão facilmente o sistema pode crescer para tratar mais<br>usuários, transações, servidores e outras extensões |
| Verificabilidade | Quão prontamente desenvolvedores e testadores podem<br>confirmar que o software foi implementado corretamente |

## Priorização

![[Untitled 561.png]]

---
# Processo de Requisitos

![[Untitled 661.png]]

## Tarefas

> [!note] 🔥
> **LEC VENG**

### 1. **Levantamento (Elicitação) de Requisitos:**

- É o processo de identificar e coletar as necessidades e expectativas dos stakeholders
- Este é o primeiro passo no processo de engenharia de requisitos.

### 2. **Especificação de Requisitos:**

- Documentação detalhada dos requisitos levantados. 
- Aqui, os requisitos são expressos de maneira clara, precisa e compreensível, muitas vezes usando linguagens de modelagem, como diagramas UML, ou especificações textuais.
- Esta etapa geralmente ocorre após o levantamento. 
- Ela formaliza os requisitos e assegura que todos os envolvidos tenham um entendimento comum sobre o que deve ser desenvolvido.

### 3. **Concepção (Análise) de Requisitos:**

- Processo de examinar e refinar os requisitos para garantir que sejam completos, consistentes e viáveis. 
- Isso pode envolver a decomposição de requisitos de alto nível em mais detalhados e a identificação de possíveis conflitos ou ambiguidades.
- Normalmente, esta etapa segue a especificação, pois é aqui que os requisitos são analisados em profundidade para garantir sua viabilidade técnica e alinhamento com os objetivos do projeto.

### 4. **Validação de Requisitos:**

- Verificação de que os requisitos especificados atendem às necessidades dos stakeholders e que estão livres de erros, incompletudes ou inconsistências. 
- Essa etapa pode envolver revisões, prototipagem ou testes de requisitos.

### 5. **Elaboração de Requisitos:**

- Envolve a construção de um entendimento mais profundo e detalhado dos requisitos. 
- Muitas vezes, isso inclui a criação de protótipos, modelos ou diagramas adicionais para explorar como os requisitos podem ser implementados.
- Este passo pode ocorrer de forma iterativa durante a especificação, análise e validação. 
- A elaboração permite que os requisitos sejam continuamente refinados e detalhados conforme o projeto avança.

### 6. **Negociação de Requisitos:**

- Resolução de conflitos entre requisitos de diferentes stakeholders ou entre as necessidades e as limitações técnicas do sistema. 
- É um processo de concessões e priorização para garantir que os requisitos mais críticos sejam atendidos.

### 7. **Gestão de Requisitos:**

- Acompanhamento e controle dos requisitos ao longo do ciclo de vida do projeto. 
- Isso inclui lidar com mudanças nos requisitos, mantendo a rastreabilidade e garantindo que os requisitos sejam consistentemente implementados e testados.

# Classificações de Requisitos

## Nível de Abstração

- Requisitos de Usuário
	- Descritos em linguagem natural
	- Alto nível de abstração
	- Desejos do usuário
- Requisitos de Sistema
	- Descrições detalhadas
	- Nível de abstração baixo
	- Mais técnico

## Qualidade

- Requisitos Normais
	- Objetivos e metas estabelecidos para o produto
- Requisitos Esperados (implícitos)
	- Não declarados expressamente
- Requisitos Fascinantes
	- Vai além da expectativa do cliente

## Evolução

- Permanentes (estáveis)
	- Derivados da atividade principal da organização
- Voláteis
	- Requisitos que se modificam durante o desenvolvimento ou quando o sistema está em uso
	- Por exemplo, políticas governamentais
- Mutáveis
	- Se modificam por causa do ambiente do sistema
- Emergentes
	- Surgem à medida que a compreensão do cliente aumenta
- Consequentes
	- Resultam da introdução do sistema no ambiente do usuário
- Compatibilidade
	- Dependem de outro equipamento ou processo

## Funcionalidade

- Funcionais
- Não funcionais
	- Devem ser quantificáveis
	- São relacionados às funcionalidades do sistema
	- Usabilidade
	- Confiabilidade
	- Desempenho
	- Manutenibilidade
	- Escalabilidade
	- Portabilidade
	- Tipos
		- Requisitos do Produto
			- Eficiência
			- Usabilidade
			- Confiabilidade
			- …
		- Requisitos Organizacionais
			- Políticas
		- Requisitos Externos
			- Legais
			- Normas
			- Outros sistemas
- De domínio

![[Untitled 662.png]]

# Quality Function Deployment (QFD)

- Disponibilização da Função de Qualidade
- Técnica de gestão da qualidade aplicada ao levantamento de requisitos que traduz as necessidades do cliente em requisitos técnicos buscando maximizar a satisfação do cliente e enfatizando o entendimento do que é valioso para o cliente.
- **Identifica 3 (três) tipos de requisitos**
	- **Normais**
		- objetivos e metas estabelecidos durante reuniões com o usuário,
		- funções específicas do software
	- **Esperados**
		- apesar de não serem claros para o usuário, estes requisitos estão implícitos no software
	- **Excitantes**
		- características que o software possui e que vão além das expectativas do usuário

# Etapas

## 1. Estudo de Viabilidade

- Avaliação rápida e barata de se determinar se as necessidades dos usuários podem ser satisfeitas por meio de um sistema de software
- Tomada de decisão
- Go / No Go
- Esse é o momento de fazer diversos questionamentos importantes: o sistema realmente agregará valor ao negócio? Ele será útil para a empresa? Ele será rentável? Qual é o retorno de investimento que ele será capaz de realizar? É viável tecnologicamente e financeiramente?

## 2. Elicitação e Análise de Requisitos

- Elicitação
	- Esclarecimento
	- Levantamento
	- Envolve vários stakeholders
	- Etapas:
		- Obtenção de Requisitos
		- Classificação
		- Priorização
		- Documentação

### 2.1. Obtenção de Requisitos - Técnicas

- Entrevistas
	- Formais ou informais
	- Podem ser entrevistas abertas ou fechadas (com ou sem roteiros)
	- Poucas pessoas envolvidas
	- As entrevistas não são tão úteis para compreender os requisitos do domínio da aplicação
	- Tipos de entrevistas formais
		- Pirâmide → Começa com perguntas mais detalhadas e termina com as mais genéricas
		- Funil → Começa com perguntas genéricas e evolui para detalhadas
		- Diamante →As perguntas genéricas são feitas no meio. Começa e termina com perguntas detalhadas
- Questionários
	- Quando envolve muitas pessoas
	- Baixo custo, fácil de aplicar e mais rápido
- Etnografia
	- Observação do fluxo de trabalho
	- Inserido no ambiente de trabalho
	- Em geral, essa é uma técnica utilizada em conjunto com outras técnicas.
	- Como ela é uma técnica de observação, isoladamente ela **não é muito eficaz na elicitação.**
	- Ajuda a descobrir requisitos implícitos
- Workshops
	- Reunião focada
	- Intensivo
	- Período longo (podendo ser mais de um dia)
	- Tem o papel do facilitador, responsável pela organização
	- Permite utilizar outras técnicas em conjunto como brainstorming ou interpretação de papéis
- Brainstorming
	- Ambientes informais
	- Curta duração, cerca de 15 minutos
	- Explora-se a capacidade criativa do grupo
	- Toda a ideia deve ser levada em consideração, sendo proibida a crítica a qualquer sugestão dada, e encorajada, inclusive, a criação de ideias que pareçam estranhas ou exóticas
- **Casos de Uso / Cenários**
	- Conjunto de cenários
	- Não confundir com o diagrama de casos de uso (UML)
	- Sempre a partir da perspectiva do usuário
	- Referem-se exclusivamente aos requisitos funcionais
	- O uso de cenários para descrever requisitos é parte integrante dos métodos ágeis, como a Extreme Programming.
- Prototipação
	- Utilizada **no estágio inicial do projeto**, ajudando stakeholders a desenvolverem uma forte noção sobre a aplicação a ser implementada
	- São frequentemente utilizadas quando os usuários são incapazes de expressar suas necessidades.
	- há um alto custo de investimento em relação a outra técnicas estudadas.
	- <u>**Protótipo de Baixa fidelidade:**</u> é simples e sem detalhes.
	- <u>**Protótipo de Alta fidelidade:**</u> o usuário enxerga melhor como ficará o software quando pronto
	- <u>**Protótipo Horizontal:**</u> cobre um conjunto amplo de finalidades porém não detalhadas.
	- <u>**Protótipo Vertical:**</u> procura demonstrar os requisitos + aprofundados de uma ou conj. pequeno de funcionalidades *(p/ momentos + adiantados)*
	- <u>**Protótipo Evolutiva:**</u> sofrerá constante evolução até se tornar o produto final
	- <u>**Protótipo Descartável:**</u> *(mais comum)*, será descartada após cumprir seus objetivos, feitos c/ ferramentas específicas.
- **Grupo Focal (Focus Group):** 
	- É um grupo de discussão informal e de tamanho reduzido (até 12 pessoas), com o propósito de obter informação qualitativa em profundidade. As pessoas são convidadas para participar da discussão sobre determinado assunto.
- JAD
	- *Joint Application Design*
	- promove cooperação, entendimento e trabalho em grupo entre os usuários desenvolvedores.
	- É bastante interativa e promove a participação ativa dos envolvidos – inclusive dos tímidos.
	- Fases
		- Customização
			- o analista prepara as tarefas para as sessões como organizar os times, preparar o material, entre outros.
		- Sessões
			- o analista marca uma ou mais reuniões com os stakeholders. No início da sessão, o engenheiro de requisitos provê uma visão genérica sobre o sistema
		- Agrupamento
			- todos os requisitos levantados nas fases anteriores são convertidos em documentos de especificação de requisitos.
	- Princípios:
		- Dinâmica de grupo
		- Uso de técnicas visuais
		- Processo organizado e racional: Análise top down e atividades bem definidas
		- Uso de documentação padronizada
- Histórias de Usuário
	- Introduzida pela XP
	- Linguagem do usuário final
	- Conciso o suficiente para caber num post-it
	- Padrão:
		- *“Como um <papel>, eu quero <meta> de modo que <benefício>”*

### 2.2. Análise de Requisitos

- Classificação
- Checagens
	- Consistência e ambiguidade
	- Omissões
	- Relacionamentos entre requisitos
- Priorização e negociação

### 2.3. Especificação de Requisitos

> [!tip] 💡
> Especificação é escrever formalmente o que foi obtido na etapa de análise e elicitação de requisitos
Os requisitos serão descritos de uma forma a funcionar como um contrato entre as partes.
Dessa forma, essa documentação deve servir tanto para engenheiros de requisitos quanto para os clientes

### Podem ser escrito das seguintes formas:

1. **Sentenças em linguagem natural: **os requisitos são escritos em linguagem natural (por­tuguês). Cada sentença representa um requisito.
2. **Linguagem natural estruturada: **os requisitos são escritos em linguagem natural, utilizando um padrão ou *template*, sendo permitido o uso de uma linguagem de programação caso necessário.
3. **Linguagem de descrição de projetos: **os requisitos são escritos em uma linguagem de programação com características abstratas, definindo-se um modelo operacional do sistema.
4. ** Notações gráficas: **Modelos gráficos apoiados por anotações. Os modelos de caso de uso e de sequência da UML são normalmente utilizados.
5. **Especificações matemáticas: **notações baseadas em máquinas de estado finito ou conjuntos, reduzindo a ambiguidade do sistema, mas dificultando a vida do cliente para entender a especificação.
- Pode ser:
	- Documento escrito
	- Gráfico (BPM, powerpoint)
	- Modelo matemático
	- Coleção de cenários
- A abordagem depende da necessidade do projeto
- Especificação do sistema
	- Produto final
	- Base para
		- Engenharia de software
		- Engenharia de hardware
		- Engenharia de banco de dados
	- Descreve requisitos funcionais e não funcionais
- Descreve a especificação detalhada dos requisitos e resumida da arquitetura

### 2.4. Validação de Requisitos

- Demonstrar que os requisitos levantados descrevem a necessidade do cliente
- Consistência e qualidade
- Entrada: documento de requisitos preliminar
- Saída:
	- Problemas
	- Ações para tratativa de problemas
	- Documento de requisitos aprovado
- Técnicas
	- Revisões/inspeções
		- Validade → Aceitação da especificação final pelas partes que contribuíram com o levantamento
		- Consistência → Examina a existência de conflitos **entre os requisitos identificados**
		- Compreensibilidade → Compreensão de forma inequívoca pelas partes interessadas
		- Completude → Todas as funcionalidades fazem parte da especificação?
		- Realismo → Viabilidade de implementação do sistema
		- Verificabilidade → É possível confirmar a implementação do requisito?
		- Rastreabilidade → Identificação da origem do requisito
		- Adaptabilidade → O requisito pode sofrer alteração sem produzir efeitos em outros requisitos??
		- Conformidade com normas → O requisito obedece as normas técnicas?
	- Prototipagem
		- Um modelo executável do sistema é apresentado para usuários finais e clientes
		- o tempo gasto na sua implementação pode não justificar o seu uso
		- Enquanto o uso de protótipos na fase de elicitação busca descobrir, levantar novos requisitos, na prototipagem da etapa de validação o objetivo é verificar se os requisitos elicitados estão de acordo com o que se esperava.
	- Geração de casos de teste

## 3. Gerenciamento de Requisitos

- Gerencia mudanças nos requisitos
- Requisitos são, inevitavelmente, incompletos e inconsistentes

### 3.1. Rastreabilidade

- Visa avaliar o impacto de mudanças
- Ligação do requisito com outros requisitos e elementos do projeto
- Matriz de rastreabilidade
	- Rastreabilidade de fonte
		- ligação do requisito com stakeholder
	- Rastreabilidade de requisitos
		- Entre requisitos
	- Rastreabilidade de projetos
		- Entre requisito e elementos do projeto (arquitetura, módulos, códigos)
	- Rastreabilidade Vertical
		- Rastreabilidade de um requisito à sua origem e desdobramentos
			- Rastreabilidade para trás (backward traceability) → Origem
			- Rastreabilidade para frente ( forward traceability) → Desdobramentos
	- Rastreabilidade Horizontal
		- Entre requisitos
		- Interferências
- Utiliza-se ferramentas CASE
	- Armazenar requisitos
	- Suporte ao gerenciamento de mudanças
	- Recuperação automática de ligação (rastreabilidade)

# Cartões CRC

Os cartões CRC (**Classes, Responsabilidades e Colaborações**) são uma ferramenta de **modelagem** usada no contexto de desenvolvimento de software e engenharia de software, especialmente na fase de **levantamento de requisitos** e **análise orientada a objetos.**

Os cartões CRC são usados em equipes colaborativas para ajudar a **identificar classes de objetos em um sistema**, as responsabilidades que cada classe tem e suas colaborações com outras classes. Eles são geralmente utilizados durante sessões de *brainstorming* ou discussões em grupo para capturar e organizar conceitos e interações no sistema em desenvolvimento.

Cada cartão CRC normalmente representa **uma classe de objetos** potencial no sistema. Nele, são listadas as responsabilidades dessa classe (ou seja, o que ela é responsável por fazer) e suas colaborações com outras classes (ou seja, como ela interage com outras classes no sistema).

Os cartões CRC podem ser organizados em uma parede ou quadro, onde os membros da equipe podem visualizá-los, movê-los e atualizá-los conforme a discussão avança. Eles ajudam as equipes a ter uma compreensão compartilhada do design do sistema e a identificar classes, responsabilidades e colaborações de forma iterativa e colaborativa. Essa técnica promove uma abordagem participativa e iterativa para o design de software, o que pode resultar em sistemas mais robustos e adaptáveis.

# Problemas Relacionados ao Levantamento de Requisitos

[https://www.devmedia.com.br/as-etapas-da-engenharia-de-requisitos/30220](https://www.devmedia.com.br/as-etapas-da-engenharia-de-requisitos/30220)

---

[[Engenharia de Software]]

# Mapa Mental

![[Requisitos.png]]