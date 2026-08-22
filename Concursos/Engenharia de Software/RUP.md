---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2024-10-26T14:55:00
Owner:
  - Eduardo Quinalha
---
# Índice

# Mapa Mental

![[RUP.png]]

# Macetes

> [!tip] 💡
> Fases: I, É ConTra → Iniciação/Concepção - Elaboração - Construção - Transição

> [!tip] 💡
> Disciplinas: MoRAITI GGA → Modelagem de Negócio, Requisitos, Análise, Implementação, Teste, Implantação, Gerenciamento de config. e mudança, Gerenciamento de Projeto, Ambiente

# RUP

> [!tip] 💡
> **Plataforma de processos, iterativa e incremental, guiada por casos de uso, centrada na arquitetura, orientada a objetos e planejada por riscos.**

> [!tip] 💡
> O Framework é focado no **Desenvolvimento** de software, ou seja, não trata do ciclo de vida completo destes, envolvendo aspectos como operação, manutenção e aposentadoria.

- **Principal processo iterativo incremental**
	- A cada iteração, um incremento do produto final é criado
	- Cada iteração é composta por fases, que podem se repetir
	- **As disciplinas do RUP não são sequenciais, mas sim sobrepostas, ocorrendo simultaneamente ao longo do projeto.**
	- A conclusão de cada disciplina **não** é demarcada por um intervalo fixo de tempo entre dois marcos principais. Essa ideia se aplica mais diretamente às fases do projeto.
> [!note] 🔥
> Apesar de Interativo e Incremental, RUP não é framework Ágil
- Guiado por casos de uso
	- Suas atividades são conectadas e guiadas pelos casos de uso
	- Testes, requisitos, arquiteturas, riscos
- Centrado na arquitetura
	- Busca resolver os riscos arquiteturais logo no início
	- Arquitetura → Esqueleto do projeto
	- **Os casos de uso mais arriscados são implementados no início, ou pelo menos uma prova de conceito destes**
- Orientado a objetos
	- Modelagem
- **Planejado por Riscos**
	- Os riscos mais críticos são tratados primeiro
	- Entenda-se por maior riscos aqueles que **afetam a arquitetura**
- Atualmente pertence à IBM
- **Prescritivo **→ Muitos papéis e artefatos
- Antes era denominado apenas UP (desenvolvido pelos criadores da UML) e após ter sido adquirido pela Rational, foi chamado de RUP
- Trata-se de um Framework de processo ou Plataforma de processo
- **Adaptável**
	- Pode-se utilizar apenas os instrumentos que se fazem necessários para cada realidade
- Todo baseado em UML
- Modelo de caso de uso define o escopo do projeto e consequentemente o que será desenvolvido

# Gráfico das Baleias

- Duas dimensões
	- Horizontal → Dinâmica
		- Fases
		- Delimitada por marcos
	- Vertical → Estática
		- Disciplinas
- **Em cada fase, pode haver N iterações**
- **Ao FINAL de cada FASE, há o respectivo MARCO, onde ocorre a avaliação acerca do atingimento do objetivo.**
- **Ao final de cada iteração são entregues artefatos e/ou executáveis etc que serão melhorados a cada nova iteração.**

![[Untitled 599.png]]

![[Untitled 600.png]]

![[Untitled 601.png]]

# Metodologia baseada no RUP

> [!tip] 💡
> Co E ConTra MoRAITI GGA

- O RUP não é instanciado por si só
- Ele é utilizado para servir como base para a elaboração de metodologias próprias
- Papéis
	- Conjunto de responsabilidades
	- Não representam pessoas exclusivamente
	- **Uma mesma pessoa pode executar vários papéis**
	- Um papel pode ser desempenhado por várias pessoas

# RUP - Arquitetura

- Organização do sistema
	- Camadas
	- Monolítico
	- Distribuído
- Elementos estruturadores e interfaces
	- Autenticação
	- Persistência
- Requisitos não funcionais
	- Desempenho

> [!tip] 💡
> **O RUP recomenda que a arquitetura seja baseada em componentes: Frameworks, classes, etc…**

- São representados por visões arquiteturais, conhecidas como visões 4 + 1:
	- 4 Visões técnicas
	- 1 Visão voltada ao usuário (casos de uso)
![[Untitled 602.png]]
	- Casos de uso (obrigatória)
		- Cenários
	- Visão Lógica (obrigatória)
		- Classes mais importantes
		- Organização das classes em pacotes e subsistemas
		- Camadas
	- Visão de Implementação (opcional)
		- Deriva da visão lógica
	- Visão de processo (opcional)
		- Recomendado em sistemas com alto grau de paralelismo
	- Visão de implantação (opcional)
		- Demonstra os nós de implantação
		- Recomendado em sistemas que rodam em múltiplos nós
		- Sistemas com muitos hardwares associados

# RUP - Modelagem Visual

- UML
![[Untitled 603.png]]

# Princípios Chave

- Adaptar processos
	- RUP pode ser adaptado
	- Existem variantes do RUP
		- RUP for Small Projects
		- OpenRUP
			- Variante Ágil
- Balancear Prioridades dos Interessados
	- Apostar em padronizações do sistema
- Colaboração entre times
- Demonstrar o valor da iteratividade
	- Possibilita adaptar escopo, tempo e custo
	- Os riscos são tratados no início do projeto
- Elevar o nível de abstração
	- Ajuda a reduzir a complexidade
	- Reduz a quantidade de documentação do projeto
	- Procurar sempre utilizar frameworks, ferramentas de geração de código, automação de software, middlewares, open source
- Foco contínuo na qualidade
	- A qualidade permeia todo o projeto e não somente em uma fase específica

# Melhores práticas

- Terceira perspectiva, apenas de acordo com Sommerville
- São elas
	- Desenvolvimento iterativo
		- Ao final de cada iteração é gerado um build que já pode interagir com os usuários, gerando novos e melhores requisitos
	- Gerenciamento de requisitos
	- Uso da arquitetura de componentes
	- Modelagem visual (UML)
	- Contínua verificação da qualidade
		- Nenhuma tarefa é especificamente dirigida a qualidade
		- Cada membro da equipe é responsável pela qualidade ao longo de todo o processo
	- Gerenciamento de mudanças

# Fases

> [!note] 🔥
> Co É Con Tra

- As fases do RUP não coincidem com as atividades do processo
- Elas estão relacionadas mais estritamente aos negócios do que assuntos técnicos
- Cada fase consistem em um intervalo de tempo entre dois marcos principais
- **Fases**
	- **Concepção / Iniciação**
		- Estabelecer um caso de negócio para o sistema
		- Identificar as entidades externas e definir as interações
		- Avaliar a contribuição do sistema para o negócio
			- Go, no Go
		- Atividades:
			- Formular o escopo do projeto
			- Planejar e preparar um caso de negócio
			- Sintetizar uma possível arquitetura
			- Preparar o ambiente para o projeto
		- Artefatos
			- Documento de visão
			- Casos de negócio
			- Plano de desenvolvimento do software
			- Modelo de casos de uso
			- Glossário
		- Marco
			- Escopo ou objetivos do ciclo de vida.
	- **Elaboração**
		- Desenvolver um entendimento do domínio do problema
		- Estabelecer um framework de arquitetura para o sistema
		- Desenvolver o plano de projeto
		- Identificar os riscos
		- Ao concluir, deve-se ter:
			- Modelo de requisitos
			- Descrição da arquitetura
			- Plano de de desenvolvimento para o software
		- Atividades
			- Definir, validar e criar a baseline da arquitetura
			- Refinar a visão → Compreensão sólida dos casos de uso
			- Criar planos de iteração detalhados
			- Refinar a arquitetura e selecionar os componentes
		- Artefatos
			- Protótipos
			- Lista de riscos
			- Documento de arquitetura de software
			- Modelo de projeto
			- Modelo de dados
		- Marco
			- Arquitetura estabilizada
	- **Construção**
		- Desenvolver partes do sistema paralelamente e integradas durante esta fase
		- Durante essa fase, os modelos de análise e projeto são completados para refletir a versão final do incremento de software
		- Portanto, ajustes ou pequenas mudanças na arquitetura do software podem ocorrer nesta fase. 
		- Além disso, o PU é um processo iterativo e adaptativo de desenvolvimento, que aceita mudanças e adaptações como fatores inevitáveis
		- Isso inclui possíveis mudanças na arquitetura central
		- No final desta fase, tem-se
			- Sistema em funcionamento
			- Documentação associada
		- Atividades
			- Gerenciamento de recursos
			- Desenvolvimento e testes dos critérios de avaliação
			- Avaliação dos releases
		- Artefatos
			- Sistema executável
			- Conjunto de testes
			- Materiais de treinamento e suporte
		- Marco
			- Capacidade operacional inicial.
	- **Transição**
		- Colocar o sistema em funcionamento no ambiente real de uso
		- Ao final, deve-se ter um sistema de software documentado
		- Atividades
			- Executar os planos de implantação
			- Testar o produto liberado no local
			- Criar um release do produto
			- Obter feedback do usuário
			- Ajustar o produto com base no feedback
			- Disponibilizar o produto para os usuários finais
		- Artefatos
			- Notas de Release
			- Artefatos de instalação
		- Marco
			- Lançamento (ou Release) do produto

# Disciplinas

- Conjunto de atividades
- Cada disciplina possui um workflow
- Básicas (MoRAITI)
	- **Modelagem de Negócios (Não é obrigatória)**
		- Usa-se casos de uso de negócios
		- Bastante ligado ao Plano Estratégico da organização
	- **Requisitos**
		- Identificar os agentes que interagem com o sistema
		- Desenvolver os casos de uso até chegar em requisitos
		- Definir as fronteiras do sistema
		- Definir uma base para planejar o conteúdo técnico das iterações
		- Definir uma base para estimar custo e tempo de desenvolvimento do sistema
		- **Definir uma interface de usuário para o sistema, focando nas necessidades e metas dos usuários**
	- **Análise e Projeto / Design**
		- Criar e documentar um modelo de projeto
		- Adaptar o design para que corresponda ao ambiente
	- **Implementação**
		- Implementar classes e objetos em termos de componentes
		- Testar os componentes desenvolvidos como unidades (Testes de unidade)
		- Integras os resultados produzidos ao sistema execxutável
	- **Testes**
		- Processo iterativo
		- Localiza e documenta defeitos na qualidade
		- Validar funções do software
		- Verificar se os requisitos foram implementados de forma adequada
	- **Implantação**
		- Uma versão é criada, distribuída e instalada no local de trabalho
		- Desenvolver artefatos de instalação e materiais de treinamento
		- Liberar o sistema em produção para os usuários finais
- Suporte (GGA)
	- **Gerenciamento de Projeto**
		- Fornecer diretrizes práticas para montar a equipe, executar e monitorar o projeto
		- **Não é o PMBOK**
			- É uma simplificação
			- Atende apenas atividades básicas
		- Framework de gerenciamento de riscos
		- Não cobre:
			- Gestão de pessoal
			- Gestão de orçamento
			- Gestão de contratos
	- **Gerenciamento de Configuração e mudanças**
		- Restringir mudanças nos itens de configuração
		- Auditar mudanças
		- Evitar confusões de: atualização simultânea, notificação limitada e várias versões
	- **Ambiente**
		- Disponibilização de ferramentas e ambiente para a equipe de desenvolvimento
		- Atividades necessárias de configuração e hardware
