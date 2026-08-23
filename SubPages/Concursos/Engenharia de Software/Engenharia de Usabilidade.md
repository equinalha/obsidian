---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2024-08-26T18:10:00
Owner:
  - Eduardo Quinalha
---
# Usabilidade

- Capacidade que um sistema interativo oferece a seu usuário, em determinado contexto de operação, para a realização de tarefas de maneira eficaz, eficiente e agradável
- Facilidade com que um usuário pode aprender a operar, preparar entradas para um sistema ou componente e interpretar suas saídas.

# Critérios de Qualidade Associados à Usabilidade

- **Learnability**
	- Intuitividade
	- O sistema deve ser de fácil aprendizado
- **Efficiency**
	- Uma vez que o usuário tenha aprendido, deve ser capaz de utilizar o sistema com alto nível de produtividade
- **Memorability**
	- Os comandos devem ser fáceis de se lembrar
- **Errors**
	- Baixo índice de erros
	- Devem ser de fácil recuperação
	- Erros catastróficos não devem ocorrer
- **Satisfaction**
	- Agradabilidade

# Ciclo da Engenharia de Usabilidade

- (1) Análise de Requisitos
- (2) Projeto, Testes e Implementação
- (3) Instalação

# Técnicas

- Observação do Usuário e da Tarefa
- Cenários de Uso
	- Espécie de prototipação para obter feedback sobre a usabilidade do sistema
- Verbalização Simplificada
	- Um usuário de teste por vez realizando um conjunto de tarefas no sistema
- Avaliações Heurísticas
	- Examina se a interface está de acordo com princípios reconhecidos de usabilidade (heurísticas).
	- Seguem 10 princípios gerais:
		- **Visibilidade do status do sistema**
			- O sistema deve sempre manter os usuários informados sobre o que está acontecendo
		- **Liberdade de controle do usuário**
			- Oferece saídas de emergência para casos de engano
		- **Prevenção contra erros**
			- Oferece ao usuário opções de confirmação antes do término de uma ação
			- Previne a ocorrência de erros
		- **Flexibilidade e Eficiência de Utilização**
			- Permitir aos usuários personalizar ações frequentes
		- **Auxiliar usuários a reconhecer, diagnosticar e resolver erros**
			- Mensagens de erro claras e precisas
		- **Compatibilidade entre o sistema e o mundo real**
			- Utilização de frases e conceitos familiares ao usuário
			- Seguir convenções do mundo real
		- **Consistência e padrões**
			- Manter a previsibilidade do sistema
		- **Reconhecimento em lugar de lembrança**
			- Minimizar a carga de memorização necessária ao usuário
		- **Projeto minimalista e estético**
			- Evitar informações irrelevantes ou raramente necessárias
		- **Ajuda e documentação**
			- Facilidade de pesquisa de informações

# Testes

> *A única maneira de determinar a usabilidade é por meio de testes e avaliações
(Pressman)*

- Tipo de teste não funcional
- Maneira de descobrir se um site alcançou determinado grau de usabilidade
- Foco no usuário, não no cliente
- Atividades de testes de usabilidade
	- Definir categorias de testes e identificar os objetivos de cada uma
	- Projetar testes
	- Selecionar os participantes
	- Fornecer instrumentos de participação

# Guias de Estilo de Usabilidade

- Estabelece padrões, na forma de diretrizes, para o desenho da interface com o usuário
- Garante a consistência interna e externa do desenho da interface com o usuário, sendo que consistência interna se refere aos elementos da interface de um produto e a consistência externa se refere à consistência com outros produtos de uma família de produtos de software. Em geral, o Guia é desenvolvido ou atualizado junto com o projeto da interface com o usuário
- Envolve:
	- princípios de design
	- diretrizes de usabilidade
	- diretrizes para o desenho da interface (cores, fundo, ícones, fontes, textos, etc).
	- Pode falar sobre os padrões específicos da família de produtos: 
		- aspectos gerais
		- padrões de comportamento da interface
		- elementos de interação
		- mensagens
		- dispositivos de interface de hardware
		- padrões específicos.

# e-PWG: Cartilha de Usabilidade do Governo Eletrônico

[https://epwg.governoeletronico.gov.br/cartilha-usabilidade.html](https://epwg.governoeletronico.gov.br/cartilha-usabilidade.html)

- Garantia do nível de qualidade
- Mensuração de resultados
- Facilita a contratação de equipes de desenvolvimento
- Diminui o tempo e o custo para manutenção de páginas
- Acelera o processo de adaptação e migração de tecnologias
- Fornece também requisitos para a correta contratação da equipe responsável por desenvolver o sítio, diminui o tempo, o custo de desenvolvimento e manutenção das páginas.

## Diretrizes

### Diretriz 1 - Contexto e Navegação

1.1 Página inicial clara.

1.2 Estrutura do sítio lógica e fácil.

1.3 Estruturar a informação de forma lógica e intuitiva para o cidadão.

1.4 O conteúdo mais importante antes da dobra.

1.5 Elementos da identidade visual localizados sempre no mesmo lugar.

1.6 A ferramenta de busca presente em todas as páginas

1.7 As páginas, seções ou serviços mais utilizados visíveis.

1.8 Não use páginas de transição.

1.9 Documentação, tutorial e ajuda.

1.10 Formatos especiais de arquivo e download.

1.11 Não use janelas pop-up ou abra links em nova janela.

1.12 Busca simples e depois, avançada.

1.13 Resultados da caixa de busca.

1.14 Formulários amigáveis.

### Diretriz 2 - Carga de Informação

- Até o menor elemento decorativo adiciona carga de informação. 
- Uma carga de informação alta confunde o cidadão

1.15 Não abarrote a página inicial com excesso de informações.

1.16 Elimine elementos desnecessários das páginas.

1.17 Elimine passos desnecessários em serviços e preenchimento de formulários.

1.18 **Em textos extensos, oferecer a opção de baixar o documento.**

1.19 Apenas peça os dados necessários.

1.20 Peça para o cidadão converter dados, medidas ou valores

1.21 Cidadão não deve necessitar memorizar dados.

1.22 A rolagem vertical ou horizontal de tela.

1.23 O bom senso no número de filtros e opções disponíveis.

### Diretriz 3 - Autonomia

- O comportamento e as funcionalidades do navegador não devem ser alterados para satisfazer páginas
- cidadão deve ter autonomia na utilização do sítio

1.24 Mantenha a função do botão de retrocesso (back/voltar) do navegador.

1.25 Não crie páginas que abram e funcionem em tela cheia.

1.26 Permitir ao cidadão marcar (favoritar) qualquer página de seu interesse.

1.27 Não usar expressões como “compatível com” “melhor visto na resolução...”.

1.28 Possibilitar ao cidadão interromper ou cancelar o processamento ou transação.

1.29 É do cidadão o controle sobre a navegação

1.30 Não usar plug-ins auto-instaláveis.

1.31 **Permitir a cópia de trechos de documentos.**

1.32 **Quando possível, oferecer a personalização da página.**

### Diretriz 4 - Erros

1.33 As ações do portal devem ser reversíveis. 

1.34 Permita erros de digitação em busca.

1.35 Avise toda indisponibilidade (Ex: troca de servidores).

1.36 Em formulários, mostre o formato desejado.

1.37 Em formulários, só deixe no campo o número de caracteres desejado.

1.38 As mensagens de erro devem ser sucintas e explicativas

1.39 **Não limpe o conteúdo do formulário inteiro por causa de um erro.**

### Diretriz 5 - Desenho

1.40 Utilizar um projeto padrão de páginas

1.41 Agrupar e hierarquizar, de forma clara, as áreas de informação.

1.42 Usar espaço em branco para separar conteúdos ou assuntos diferentes.

1.43 Usar fundos neutros, que não comprometam o objetivo do sítio.

1.44 Evitar caixa com opções ou de menus de cortina na navegação principal e persistente.

1.45 O desenho deve estar a serviço da informação

1.46 **Elementos do desenho não devem trabalhar em benefício de uma estética particular.**

1.47 Utilizar a animação com bom senso.

1.48 Conteúdo agradável de ser lido.

1.49 Texto alinhado à esquerda.

1.50 Esquema consistente de cores e fontes.

1.51 Respeitar a velocidade de conexão do público-alvo.

1.52 **Utilizar de forma consciente plug-ins e multimídia.**

### Diretriz 6 - Redação

1.53 Utilizar uma linguagem clara e familiar

1.54 O texto objetivo.

1.55 Dividir o texto em tópicos.

1.56 Títulos informativos e com destaque visual.

1.57 Título da página explanatório e único.

1.58 Utilizar termos simples e claros como rótulos de menu.

1.59 Gramática correta.

1.60 Use ênfase e negrito.

1.61 Evitar o uso de caixa alta

### Diretriz 7 - Consistência e Familiaridade

1.53 Utilizar uma linguagem clara e familiar

1.54 O texto objetivo.

1.55 Dividir o texto em tópicos.

1.56 Títulos informativos e com destaque visual.

1.57 Título da página explanatório e único.

1.58 Utilizar termos simples e claros como rótulos de menu.

1.59 Gramática correta.

1.60 Use ênfase e negrito.

1.61 Evitar o uso de caixa alta

# Métodos de Avaliação

## **Métodos de Investigação**

Identificam requisitos
	- Observações em campo
	- Entrevistas
	- Registro de uso
	- Questionários
	- Lista de verificação de características
	- Métodos de avaliação
	- Workshop
	- Grupos de foco

## Métodos de Inspeção

Avaliações baseadas em um conjunto de diretrizes
	- Percurso cognitivo
	- Avaliação heurística
	- Análise de tarefas
	- Lista de verificação de propriedades
	- Inspeção de padrões
	- Avaliação de peritos

## Testes de Usuário

Técnicas etnográficas
	- Arranjo de cartões (card sorting)
	- Co-descoberta
	- Avaliação cooperativa
	- Diário de incidentes
	- Experimentos controlados
	- Protocolo “Pensar Alto”
	- Registro de conversações

## Métodos Empíricos

> [!note] 🔥
> Utilizam **participantes** (usuários)

- **Card Sorting**
	- [https://brasil.uxdesign.cc/card-sorting-como-descobrir-o-modelo-mental-de-organização-de-conteúdo-18e9a50121aa](https://brasil.uxdesign.cc/card-sorting-como-descobrir-o-modelo-mental-de-organiza%C3%A7%C3%A3o-de-conte%C3%BAdo-18e9a50121aa)
	- se utiliza de cartões ou *post-its* com conteúdos onde o usuário vai fazendo agrupamento desses itens de acordo com sua percepção, ele organiza assim os temas por categorias que façam sentido pra ele, gerando uma experiência melhor de navegação no produto final.
- **Avaliação Cooperativa**
	- Avaliação conjunta envolvendo participantes e pesquisadores
	- Ocorrem perguntas das duas partes
- **Co-Descoberta**
	- Envolve dois participantes que trabalham juntos para explorar uma interface e descobrir como as tarefas são realizadas
	- O pesquisador obtém um entendimento das questões através das verbalizações destes participantes
- **Diário de Incidentes**
	- Mini-questionários emitidos para os participantes
	- Solicita-se que sejam anotados todos os problemas encontrados na utilização da interface
- **Entrevistas**
- **Grupo de Foco**
- **Experimentos Controlados**
- **Listas de Verificação de Características**
	- Emitidas aos participantes
	- Estes devem marcar as que foram utilizadas na interface avaliada
- **Observação em Campo**
- **Workshop de Usuário**
- **Protocolos “Pensar Alto”**
- **Questionários**
- **Registro de Conversações**
- **Registro de Uso (logging)**
	- Captura automática

## Métodos não Empíricos

> [!note] 🔥
> Não utilizam participantes

- **Análise de Tarefas**
	- consiste basicamente de decompor as tarefas em subtarefas, de forma que se torne possível entender melhor como as tarefas serão executadas, isso visa entender as etapas do processo de interação com o usuário.
	- a medição da complexidade de uma tarefa é feita através do número de passos necessários para completar a mesma.
	- O método de análise da tarefa pode ser utilizado para o desenvolvimento de predições sobre o quanto é fácil/difícil desempenhar uma determinada tarefa, ou quanto esforço é necessário para chegar ao final dela.
- **Avaliação Heurística**
	- Feita por peritos
	- Preferencialmente feito de forma individual e segregada por cada um
	- O objetivo é avaliar a interface segundo um conjunto de princípios gerais
- **Listas de Verificação de Propriedades**
	- As listas de verificação apresentam uma série de propriedades de projeto que, de acordo com as teorias do design, da ergonomia e do ergodesign, asseguram que uma interface é fácil de usar
	- Não envolve participantes
- **Percurso Cognitivo**
	- realizado por peritos
	- forma de avaliar uma interface sem a participação do usuário, na qual especialistas analisam cada passo necessário para executar uma tarefa
- **Inspeção de Padrões**
	- Avaliação feita por especialistas
	- Segundo um determinado padrão escolhido, exemplo: e-MAG
	- Avaliação de conformidade

# System Usability Scale (SUS)

[https://brasil.uxdesign.cc/o-que-é-o-sus-system-usability-scale-e-como-usá-lo-em-seu-site-6d63224481c8](https://brasil.uxdesign.cc/o-que-%C3%A9-o-sus-system-usability-scale-e-como-us%C3%A1-lo-em-seu-site-6d63224481c8)

- Forma de quantificar usabilidade em uma escala numérica
- Existem outras escalas: SUMI, SUPR-Q, QUIS, etc.
- Critérios avaliados
	- Efetividade
	- Eficiência
	- Satisfação
- Consiste de um questionário de 10 perguntas, pontuadas de 1 a 5
	- 1 - Discordo totalmente
	- 5 - Concordo totalmente
- Deve ser aplicado ao final de um teste de usabilidade mais qualitativo