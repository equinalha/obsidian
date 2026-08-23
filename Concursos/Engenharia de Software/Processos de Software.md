---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2024-10-01T17:15:00
Owner:
  - Eduardo Quinalha
---
![[Processos_de_Software.png]]

# Modelos de ciclo de vida

![[Lista de Bizus synced block]]

- Abstração do processo de desenvolvimento de software
- A partir de uma perspectiva específica (pessoas, projeto, etc…)
- Contem
	- Esqueleto do processo
	- ordem das atividades
	- artefatos gerados

# Fases do desenvolvimento de software

- Planejamento
- Análise e especificação de requisitos
- Projeto
- Implementação
- Testes
- Implantação, Operação e Manutenção

# Metodologias de Desenvolvimento

## Modelos Prescritivos

### Modelo em cascata

- Modelo clássico
- Composto por várias etapas sequenciais
- Só passa de uma etapa para outra quando todas as tarefas da etapa anterior forem completadas

<!-- Column 1 -->
![[Untitled 604.png|Modelo em cascata do Pressman]]

<!-- Column 2 -->
![[Untitled 605.png|Modelo em cascata Sommerville]]

- Nome das Etapas variam conforme o autor:

| Sommervile | Royce | Pressman (4a Ed) | Pressman (6a Ed) |
| --- | --- | --- | --- |
| Análise e Definição de Requisitos | Requisitos de Sistema | Modelagem e Engenharia do Sistema/Informação | Comunicação |
| Projeto de Sistema e Software | Requisitos de Software | Análise de Requisitos de Software | Planejamento |
| Implementação e Teste de Unidade | Análise | Projeto | Modelagem |
| Integração e Teste de Sistema | Projeto | Geração de Código | Construção |
| Operação e Manutenção | Codificação | Teste e Manutenção | Implantação |
|   | Teste |   |   |
|   | Operação |   |   |

- Características
	- Minimiza o planejamento, organiza as atividades em sequência com entregas bem definidas
	- Mais antigo e mais simples
	- Também conhecido como ciclo de vida clássico
	- Funciona bem para requisitos **estáveis** e bem compreendidos
	- Facilmente aplicável em equipes inexperientes
	- Acumula riscos ao longo do projeto
	- Pode atrasar a entrega por conta disso
![[Untitled 606.png]]
	- Não tem feedback entre as etapas

![[Untitled 607.png]]

### Modelo em V

- Separa o fluxo de desenvolvimento do fluxo de testes
- O lado esquerdo do V representa o desenvolvimento e o lado direito os testes

![[Untitled 608.png]]

## Modelos Iterativos

- Dividem-se em **Incrementais **e **Evolutivos**
- Divide os requisitos em grupos menores
- Cada grupo passa por uma iteração que é como um mini-projeto
- Existe algum tipo de priorização
- Mais receptivo às mudanças

> [!note] 🔥
> No Modelo em **Cascata**, caso haja cem requisitos, analisam-se os cem requisitos, projetam-se os cem requisitos, codificam-se os cem requisitos, testam-se os cem requisitos, e assim
por diante sequencialmente;

No Modelo **Incremental**, caso haja cem requisitos, dividem-se os cem requisitos em vinte miniprojetos de cinco requisitos cada e utiliza-se o modelo em cascata para cada miniprojeto;

No Modelo **Iterativo**, caso haja cem requisitos, analisam-se, projetam-se, codificam-se, testam-se os cem requisitos, porém os requisitos são entregues incompletos e eu repito esse ciclo de refinamento até chegar ao produto final.

### Modelo RAD (Rapid Application Development)

> [!note] 🔥
> Conceitos Chave:
- Reuso de componentes
- Ciclo de desenvolvimento curto (60 a 90 dias)
- Uso de ferramentas automatizadas
- Aplicações standalone

- Iterativo e incremental
- Ciclos curtos (60 a 90 dias)
- Recursos de componentes à exaustão
- Uso de linguagens visuais
- Forte paralelismo das atividades, requerendo, assim, módulos bastante independentes. 
- Aqui os incrementos são desenvolvidos ao mesmo tempo, por equipes diferentes.
- Na obtenção dos requisitos, costumam-se optar por **metodologias mais dinâmicas** e rápidas, como workshops ao invés de entrevistas.
- Os sistemas desenvolvidos no ciclo RAD **tendem a ter uma padronização de telas muito forte,** devido a bibliotecas reutilizáveis e templates, porém tendem a perder em desempenho do sistema e na análise de risco (atividades estas que demandam tempo em qualquer projeto). Assim, é preferível seu uso para **softwares de distribuição pequena.**
- Fases
	- Modelagem de negócio
	- Modelagem de dados
		- Atributos e relacionamentos
	- Modelagem de Processo
		- Descreve o processamento para o CRUD
	- Geração da aplicação
		- Uso de ferramentas automatizadas para a construção do SW
		- Uso de linguagens de auto nível (4a geração)
		- Uso de componentes prontos (drag n drop), ex: delphi, apex
	- Teste e modificação
		- Como o modelo enfatiza o reuso, muitos componente já foram testados anteriormente
- Quando usar?
	- Aplicação standalone (não depende de softwares auxiliares)
	- Uso de classes pré-existentes
	- Performance não é o mais importante
	- Escopo restrito
	- Risco de mudança tecnológica é baixo
- Vantagens
	- Desenvolvimento rápido
	- Desenvolvimento de alto nível de abstração
	- Uso de wizards
	- Top-down
- Desvantagens
	- Custo elevado das ferramentas
	- Perda de precisão científica
	- Pode construir funções desnecessárias

## Modelos Evolucionários

- Versão inicial que evolui por meio de versões
- Lida bem com mudanças pois tem feedback entre as atividades
- Cada versão incorpora as mudanças necessárias e refina a versão anterior
- Podem ser consideradas como modelos iterativos
- **Desvantagens**
	- Processo não é visível
	- O sistema podem ficar mal estruturados (as mudanças corrompem o modelo inicial)

## Prototipagem

- Pode ser considerado um ciclo de vida ou pode ser usado como ferramenta em outros ciclos de vida.

### Prototipagem Evolucionária

- Novas funcionalidades são adicionas a medida que o cliente as propõem
- Inicia com os requisitos mais bem compreendidos
- Então **evolui **o protótipo até alcançar a forma do produto final
- **Desvantagens**
	- Falta de visibilidade
	- Sistemas pobremente estruturados
	- Documentação pode ser esquecida
	- Padrões de qualidades relaxados

### Prototipagem Descartável

- Inicia pelos requisitos mais difíceis
- Constrói um pequeno protótipo para **testar e compreender um caso de uso**
- Objetivo de entender os requisitos
- Ao final descarta-se

## Modelo em Espiral

- **Evolutivo**, entrega versões do software, não necessariamente a final
- **Cada volta na espiral representa uma fase no processo**
- Primeiro a acrescentar aspectos gerenciais
- Seu diferencial está na introdução da análise de risco, que neste caso é um ponto de decisão
- As atividades técnicas, como desenvolvimento, testes, etc. estão no quadrante de Engenharia
- **Utiliza a prototipação como mecanismo de redução de riscos**

![[Untitled 609.png|Setores segundo Pressman]]

![[Untitled 610.png]]

- O modelo foi proposto originalmente, em 1988, por Boehm
- **No modelo original (de Boehm) existem 4 setores:**
	- **Determinar Objetivos, Alternativas e Restrições**
	- **Avaliar Alternativas, Identificar e Resolver Riscos**
	- **Desenvolver e Testar**
	- **Planejar próximas fases**

## Modelo baseado em componentes

- Reuso com peça principal
- Base de componentes reusáveis e framework de integração
- Redução de custos
- entregas mais rápidas
- **Componentes**
	- Bloco de código
	- independente
	- Possui entradas e saídas definidas
	- Importável
	- Padronizado
	- Reutilizável
	- Coeso
- Etapas
	- Especificação de requisitos
	- Análise de componentes
	- **Modificação de requisitos (para que se adeque aos componentes)**
	- Projeto baseado em reuso
	- Desenvolvimento e integração
	- Validação do sistema

## Métodos Formais

- Baseado em técnicas matemáticas para especificar, desenvolver e verificar software
- Transformado em código somente após a prova da especificação
- Gera programas mais corretos e completos de alta confiabilidade
- Usado para códigos muito críticos
- Muito caro e complexo
- Difícil entendimento para quem não é especialista na área

## Modelo orientado a aspectos

- Separação de interesses
	- Principais → Negócio
	- Ortogonais
- Aspectos
	- Propriedades de um sistema que envolvem diversos componentes funcionais
	- Exemplos: Sincronização, persistência, distribuição, logging
	- Ao contrário de componentes, que tratam uma única funcionalidade, aspectos envolvem diversas unidades de um sistema
- O modelo orientado a aspectos pede que aspectos fiquem separados do código principal
- **Uma forma de fazer isso em Java é por meio de anotações**

# Metodologias de Análise

## Análise Estruturada

- Método de modelagem clássico
- Utiliza as seguintes Ferramentas:
	- **Dicionário de Dados (DD)**
		- Descreve os objetos (itens) criados ou utilizados pelo software
		- É composto por:
			- Nome
			- Sinônimo
			- Onde é usado/como é usado
			- Descrição do conteúdo
			- Informação suplementar
	- **Diagrama Entidade-Relacionamento (DER)**
		- Descreve objetos, atributos e relações
	- **Diagrama de Fluxo de Dados (DFD)**
		- Descreve transformações que os dados sofrem por funcionalidades presente no software a media que trafegam pelo sistema
![[Untitled 611.png]]
		- Os quadrados descrevem entidades externas, enquanto que as bolhas demonstram os processos de transformação
		- Pode ser divido, criando diferentes DFD’s para cada nível de detalhe
			- DFD 0 - Nível mais alto, com maior abstração de detalhes
				- Conhecido por Modelo (ou diagrama) de Contexto
				- Representa todo o software como uma única bolha, com suas entradas e saídas de dados gerais
			- DFD 1 - Representa o conjunto de entidades externas, funcionalidades e depósitos
	- **Diagrama de Transição de Estados (DTE)**
		- Modela como o software reage a eventos externos

## Análise Orientada a Objeto

- Aborda o domínio do problema como um conjunto de objetos que têm atributos e comportamentos específicos. 
- Os objetos são manipulados com uma coleção de funções, denominadas métodos, operações ou serviços e 
- comunicam-se uns com os outros através de mensagens.
- incentiva a criação de componentes (reuso) vinculada ao modelo de processo evolutivo
- Tem a finalidade de definir as classes que são importantes ao problema a ser resolvido, descobrindo seus atributos e operações, as relações existentes entre elas e o comportamento exibido por elas.
- O principal método de modelagem é a UML
	- possui 5 visões:
		- **Usuário**
			- o sistema é representado sob o ponto de vista do usuário, denominado ator, e utiliza a abordagem de casos de uso, que descrevem os cenários de uso do sistema a partir da perspectiva do usuário
		- **Modelo Estrutural**
			- estrutura estática do sistema (classes, objetos e relacionamentos) visando os dados e funcionalidades do sistema.
		- **Modelo comportamental **
			- representa os aspectos dinâmicos ou comportamentais do sistema, bem como mostra as interações ou colaborações entre os vários elementos estruturais apresentados nas visões do modelo do usuário e do modelo estrutural
		- **Modelo de implementação **
			- representa como os aspectos estruturais e comportamentais devem ser construídos
		- **Modelo do ambiente**
			- representa os aspectos estruturais e comportamentais do ambiente no qual o sistema será implementado

# Projeto Orientado a Objetos

- pode ser apresentado mediante o conceito de pirâmide de projeto para software
- Esta pirâmide é dividida em 4 (quatro) camadas:
	- **Camada de subsistema**: apresenta cada um dos subsistemas que satisfazem as necessidades dos usuários;
	- **Camada de classes e objetos:** contém hierarquias de classes para a criação do sistema usando generalizações e especializações, além das representações dos objetos;
	- **Camada de mensagens:** estabelece a interface externa e interna do sistema, detalhando como cada objeto se comunica com seus colaboradores;
	- **Camada de responsabilidades**: descreve as estruturas de dados de todos os atributos e os algoritmos de todas as operações de cada objeto.
