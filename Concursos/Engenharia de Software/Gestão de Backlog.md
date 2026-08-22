---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2024-12-06T19:34:00
Owner:
  - Eduardo Quinalha
---
# Gestão de Backlog

[https://www.gp4us.com.br/backlog-do-produto/](https://www.gp4us.com.br/backlog-do-produto/)

## Requisitos de Backlog

- Para um requisito entrar para o backlog, ele precisa:
> [!note] 🔥
> **INVEST
(I)ndependent - (N)egociable - (V)aluable - (E)stimated - (S)mall - (T)estable**

	- **Ser independente**
		- atender a necessidade ou situação futura informada pelo cliente, sem depender de outro requisito
		- Muitas vezes este requisito não pode ser atendido plenamente
	- **Ser negociável **
		- Deve permitir alterações como
			- Mudança de prioridade
			- Aumento/redução de abrangência
			- Desdobramento em outros requisitos
	- **Ser priorizado (Valuable)**
		- Assegurar entrega de valor para o cliente
		- De acordo com o valor agregado ao negócio
	- **Ser estimado**
		- Deve apresentar condições para que possa ter seu prazo de desenvolvimento/entrega estimado
		- Caso seja muito grande, deverá ser desdobrado em requisitos menores
	- **Ser pequeno**
		- A duração prevista para seu desenvolvimento não deverá ultrapassar uma sprint
	- **Ser inspecionável (Testable)**
		- Sua descrição deve prover informações necessárias para que possa ser inspecionado/testado pelo cliente final
		- Requisitos que não podem ser validados, elevam os níveis de risco do projeto

## User Story

- Contêm uma descrição detalhada dos requisitos de cada solicitação a ser implementada
- Deve conter as **necessidades** dos usuários ou dos clientes, e não as funcionalidades do sistema.
- Uma story pode conter:
	- Id
	- Nome
	- Importância
	- Estimativa inicial
		- A unidade utilizada é pontos por história ou **story points**
		- Corresponde aproximadamente a homem/dias
		- 3 desenvolvedores fulltime por 4 dias → 12 storypoints
	- A estimativa dada por homens-hora chama-se** Tempo Ideal**
	- Demonstração
		- Descrição em alto nível
		- Especificação do teste
	- Notas
- Exemplo:

![[Concursos/images/Untitled 17.png]]

# Priorização de Backlog

- Descartar histórias que não estejam mais alinhadas à visão do produto
- Dar importância à definição de pronto
- Conhecimento, Incerteza e Risco
	- Histórias com baixo conhecimento e alta incerteza deve ter uma prioridade alta

## Valor de Negócio x Risco

- Um dos métodos mais comuns de priorização
- É um método relativamente simples, pois não envolve fórmulas complexas.

![[Concursos/images/image 28.png]]

- **Risco de valor**: O usuário vai utilizar? Vai ser bom pra ele?
- **Risco de usabilidade**: O usuário conseguirá utilizar?
- **Risco de viabilidade técnica**: O time conseguirá desenvolver isso com a tecnologia, tempo e habilidades que possui?
- **Risco de viabilidade de negócio**: Isso está de acordo com as regulamentações do setor e não conflita com funcionalidades já existentes?

## Testes de Suposição

- define a prioridade a partir dos resultados da validação de uma hipótese ou suposição, e também da relevância para o usuário final.
- É necessário definir os valores das escalas de cada critério

**T = O quanto a suposição foi testada**

**U = Relevância para o usuário**

- A prioridade é o resultado da soma destes dois critérios.

![[Concursos/images/image 29.png]]

## Método BUC

- analisa os benefícios para o **negócio** e para o **usuário** enquanto mantém um **olhar para o custo**
- Para cada critério deve ser definida uma escala de valor (ex.: 1 a 5).

**Benefícios de negócio (Business Benefits)**: Quanta receita essa funcionalidade poderá gerar? Reduzirá os custos da empresa? Trará mais clientes?

**Benefícios para o usuário (User Benefits)**: A experiência do usuário será melhor? Ele ficará mais satisfeito? Ele quer utilizar essa funcionalidade? Ele conseguirá utilizar essa funcionalidade?

**Custo (Cost)**: Quanto tempo será necessário? Quanto dinheiro irá custar? Quantos recursos irá precisar?

![[Concursos/images/image 30.png]]

## Scorecard

- Priorização de acordo com critérios pré-definidos com as partes interessadas
- Deve-se definir critérios e atribuir peso a eles
- Os pesos somados devem totalizar 100%
- **Prioridade = SOMA (Nota do critério * (peso/100))**

![[Concursos/images/image 31.png]]

## MoSCoW

- As categorias são 
	- Must-Haves
		- Itens críticos responsáveis direta ou indiretamente pela entrega de valor
		- Não deve conter mais de 60% do backlog
	- Should-Haves
		- Itens secundários que não afetam a entrega, porém são importantes
	- Can-Haves
		- Itens desejados mas de menor importância que as duas categorias anteriores
		- Baixo impacto se não for entregue
		- Não deve conter mais de 20% do backlog
	- Won’t-Haves
		- Atividades inviáveis de se entregar no momento
		- Existe a possibilidade de ser desenvolvido em momento futuro

![[Concursos/images/image 32.png]]

## Kano Model

- Analisa a satisfação do cliente
- Categoriza atividades como:
	- Atrativos
	- Desempenho
	- Obrigatórios
	- Indiferentes

![[Concursos/images/image 33.png]]

## Story Mapping

- Utilizado principalmente nas fases iniciais do projeto
- Focado na experiência do usuário
- O mapa possui a jornada do usuário no eixo horizontal
- As atividades são organizadas por prioridade no eixo vertical e separadas por releases

![[Concursos/images/image 34.png]]

# Estimativa de Stories

## Tempo Ideal

- Considera o tempo necessário para completar uma tarefa em **condições ideais**, ou seja, **sem interrupções e distrações**. 
- Neste método, o foco é no esforço puro que a tarefa exige, supondo uma execução contínua e eficiente. 
- Ele oferece uma **visão simplificada** do esforço necessário e é útil para dar uma estimativa "**teórica**", mas precisa ser ajustado para condições reais, pois desconsidera fatores externos.

## Tempo Real

- Estimativa com base no tempo que uma tarefa leva para ser completada na prática, **considerando as condições reais de trabalho. **
- Aqui, são levados em conta **interrupções, reuniões, imprevistos **e qualquer elemento do dia a dia que possa afetar a conclusão das tarefas. 
- Esse método é **mais realista,** pois se aproxima do tempo exato em que o *story* deve ser entregue, embora possa ser** difícil de prever **com precisão.

## Tempo Ampliado

- O tempo ampliado é uma forma de estimativa onde se adiciona um **"colchão" de tempo extra ao tempo real **para compensar incertezas e variáveis desconhecidas que podem afetar o andamento da tarefa. 
- Dessa forma, busca-se minimizar o risco de ultrapassar o tempo estimado. 
- Esse método é útil quando a equipe precisa ter **segurança na entrega**, mas pode levar a margens mais folgadas e menos precisão.

## Nimbly Timing

- Combina métodos de **tempo real e ideal,** estabelecendo** intervalos de tempo ajustados** para a realidade da equipe e otimizando a produtividade. 
- Ele utiliza** tempos ajustados** com base em **dados históricos** e métricas de produtividade anteriores para fazer estimativas mais ágeis. 
- O objetivo é minimizar a sobrecarga de planejamento e estimar de forma otimizada, adaptando-se ao contexto da equipe.

## Story Points

- Representam uma **estimativa** **relativa** de esforço para concluir um *story*, baseada em seu tamanho, complexidade e incerteza. 
- Em vez de medir tempo, a equipe atribui um valor numérico relativo a cada tarefa para indicar a quantidade de trabalho que ela exige. 
- Esse método evita depender de estimativas de tempo absoluto, pois foca mais no esforço geral. 
- *Story points* são muito populares em equipes ágeis, pois incentivam uma visão mais ampla do trabalho, considerando esforço em vez de tempo direto.
- Pode utilizar diferentes técnicas para essa estimativa:

### Planning Poker

- Cada membro da equipe recebe um conjunto de cartas numeradas, geralmente baseadas na sequência de Fibonacci (1, 2, 3, 5, 8, 13, 21, etc.).
- O Product Owner (PO) apresenta uma user story, e a equipe discute brevemente a história.
- Após a discussão, todos os membros escolhem uma carta que representa a estimativa de Story Points para aquela user story, sem revelar suas escolhas imediatamente.
- Quando todos estiverem prontos, as cartas são reveladas ao mesmo tempo.
- Se houver discrepâncias significativas nas estimativas, a equipe discute os motivos e refaz a estimativa até chegar a um consenso.

### T-shirt Sizing

- utiliza metáforas simples, como tamanhos de camisetas (P, M, G, GG, etc.)
- Uma vez categorizadas, essas estimativas podem ser convertidas em Story Points, dependendo das definições específicas da equipe.

### Bucket System

- útil quando há muitas histórias para estimar em um curto período de tempo
- A equipe cria diferentes "baldes" (buckets) que representam diferentes intervalos de Story Points, por exemplo: 1-2, 3-5, 8-13, etc.
- Cada user story é colocada no bucket correspondente de acordo com o esforço estimado pela equipe.
- Após todas as histórias serem colocadas nos buckets, a equipe revisa para verificar se as estimativas estão consistentes.

### Estimativa Relativa

- funciona comparando uma nova user story com histórias que já foram completadas ou que possuem uma estimativa conhecida.
