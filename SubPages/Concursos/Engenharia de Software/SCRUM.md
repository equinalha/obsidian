---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2026-03-18T15:59:00
Owner:
  - Eduardo Quinalha
---
# Definição do Scrum

[https://scrumguides.org/docs/scrumguide/v2020/2020-Scrum-Guide-PortugueseBR-3.0.pdf](https://scrumguides.org/docs/scrumguide/v2020/2020-Scrum-Guide-PortugueseBR-3.0.pdf)

- O framework Scrum é propositalmente incompleto, apenas definindo as partes necessárias para implementar a teoria Scrum.
- Em vez de fornecer às pessoas instruções detalhadas, as regras do Guia do Scrum orientam seus relacionamentos e interações.
- **Gestão** de desenvolvimento de produtos **complexos**
- Scrum são práticas de **GESTÃO** e não de **ENGENHARIA**
- **Iterativo e incremental**
- Não é uma metodologia
	- **É um framework**
- Não é prescritivo
	- Não diz “como” fazer
	- Diz apenas o que fazer e qual o objetivo
- Não é fácil de aplicar, ainda que simples

Scrum é um framework leve que ajuda pessoas, times e organizações a gerar valor por meio de soluções adaptativas para problemas complexos.

Em suma, Scrum requer um **Scrum Master** para promover um ambiente onde:

1. Um Product Owner ordena o trabalho para um problema complexo em um Product Backlog.
2. O Scrum Team transforma uma seleção do trabalho em um incremento de valor durante uma Sprint.
3. O Scrum Team e seus stakeholders inspecionam os resultados e se ajustam para a próxima Sprint.
4. Repita

# Benefícios

- Entregas frequentes
- Redução de riscos
- Maior qualidade
- Mudanças utilizadas como vantagem competitiva
- Visibilidade do progresso
- Redução do desperdício e aumento de produtividade

# Teoria da Complexidade

- Mostra o quão complexo é o ambiente do seu projeto
- Teoria Cynefin
- Dos quadrantes abaixo, o Scrum adequa-se **apenas a ambientes complexos**

![[Untitled 357.png]]

# Pilares

- Transparência
- Inspeção
- Adaptação

> [!note] 🔥
> Os artefatos devem ser **transparentes **a fim de permitirem a **inspeção**. A **inspeção**, por sua vez, é inútil sem a existência da **adaptação**, que é a capacidade de ajuste do processo de forma a levar algum aspecto de volta para dentro dos limites aceitáveis.

# Bases

- Empirismo
- Lean Thinking

# Valores

5. Compromisso,
6. Foco,
7. Abertura,
8. Respeito e
9. Coragem

# Papéis, artefatos e cerimônias

## **Papéis**

- PO
	- Desenvolver e comunicar explicitamente a meta do produto;
	- Define as funcionalidades do produto
	- É um representante do cliente do projeto (ou o próprio)
	- Decide as datas de lançamento (Releases)
	- Aceita ou rejeita os resultados dos trabalhos
	- Criar e comunicar claramente os itens do Product Backlog;
	- Ordenar os itens do Product Backlog; e,
	- Garantir que o Product Backlog seja **transparente, visível e compreensível.**
	- O papel do PO deve ser exercido por uma **única pessoa em um projeto**
	- No entanto, o PO pode trabalhar em mais de um projeto
	- Diz se a meta da sprint foi alcançada ou não
	- **Única pessoa com autoridade para cancelar uma Sprint**
- Scrum Master
	- **É um facilitador**
	- Responsável pela aplicação dos valores e práticas do Scrum
	- Remove obstáculos, facilita resultados
	- Garante a plena funcionalidade e produtividade da equipe
	- Escudo para interferências
	- Competente em Soft Skills
	- Pode, embora não recomendado, ser um dos desenvolvedores
	- **Não pode ser o PO**
	- Promove mudanças organizacionais
	- Garante o uso do Scrum
- Developers
	- Equipe multifuncional e auto-gerenciada
		- Programadores
		- Testadores
	- Criar um plano para a Sprint, o Sprint Backlog;
	- Introduzir gradualmente qualidade aderindo a uma Definição de Pronto;
	- Adaptar seu plano a cada dia em direção à meta da Sprint; e,
	- Responsabilizar-se mutuamente como profissionais.

## **Artefatos**

### Product Backlog

- Lista de tudo aquilo que precisa ser feito durante o projeto
- Ordenado por prioridade
	- Porém existem outras formas de ordenar
- Comprometimento: **Meta do produto**
- Pode conter
	- Necessidades ou objetivos de negócio
	- Questões arquiteturais e/ou técnicas
	- **Melhorias e correções a serem realizadas no produto**
- É um artefato vivo
- Normalmente os itens mais do topo (mais prioritários) são mais detalhados

![[Untitled 358.png]]

### Sprint Backlog

- Pertence aos desenvolvedores
- Lista de tarefas técnicas
- Derivado do backlog do produto
- 1 item do backlog do produto pode gerar várias tarefas dentro do backlog da sprint

### Definition of Done

- Acordo formal entre PO e Desenvolvedores
- Testes, documentações
- Normalmente criada no início do projeto, porém pode sofrer alterações/melhorias durante
- Meta de Negócio
- **Incremento de Produto**

### Incremento do Produto

- Resultado do trabalho de uma Sprint
- Todos os itens devem estar “Prontos” - Segundo a definição de pronto
- Espera-se que o incremento do produto seja implantável

### Meta da Sprint

- Meta de negócio
- Não é associado a números ou indicadores, mas sim associado a objetivo de negócio
- Negociada no planejamento da sprint
- Os desenvolvedores podem não entregar todos os itens do backlog da sprint, mas pode, mesmo assim, atingir a meta

## **Cerimônias**

### Sprint

- A Sprint é um contêiner para todos os outros eventos
- Todo o trabalho necessário para atingir a meta do Produto, incluindo Sprint Planning, Daily Scrums, Sprint Review e Sprint Retrospective, acontece dentro de Sprints.
- Uma nova Sprint começa imediatamente após a conclusão da Sprint anterior.
- Uma Sprint pode ser cancelada se a Meta da Sprint se tornar obsoleta. Apenas o Product Owner tem autoridade para cancelar a Sprint.
- Ocorrem em sequência, sem intervalos
- Duração fixa e ritmo regular
- Máximo 4 semanas
- Participantes: Todos (PO, Scrum Master, Developers)
- Saída: Incremento do produto

### Sprint Planning

- Dividida em 3 tópicos
	- Tópico 1: Por que esta sprint é valiosa? (Meta da Sprint)
		- Product Owner propõe como o produto pode aumentar seu valor e utilidade na Sprint atual
	- Tópico 2: O que pode ser feito nesta Sprint? (Itens do backlog)
		- Por meio de discussão com o Product Owner, os Developers selecionam itens do Product Backlog para incluir na Sprint atual
	- Tópico 3: Como o trabalho escolhido será realizado? (Plano de entrega)
		- Isso geralmente é feito decompondo itens do Product Backlog em itens de trabalho menores de um dia ou menos. 
		- A forma como isso é feito fica a critério exclusivo dos Developers
- Meta da Sprint + Itens do backlog selecionados + Plano de entrega = Sprint Backlog
- O que pode ser feito nesta Sprint?
	- PO apresenta os itens mais importantes do backlog
	- PO propõe uma meta de negócio
- Como o trabalho será feito?
	- Elaboração do Sprint Backlog
	- Participação do PO não é obrigatória
- Porquê o trabalho será feito
	- Razão do negócio ou benefício a ser atingido
	- Mantém o foco dos desenvolvedores
- Duração máxima 8h para um Sprint de 4 semanas
- Acontece** no primeiro dia da sprint**

### Daily Scrum

- A Daily Scrum não é o único momento em que os Developers podem ajustar seu plano. Eles costumam se reunir ao longo do dia para discussões mais detalhadas sobre a adaptação ou replanejamento do resto do trabalho da Sprint.
- Reunião curta, máximo 15 minutos
- **Entre os desenvolvedores**
- Presença do Scrum Master não é obrigatória
- Planejamento diário

### Sprint Review

- O propósito da Sprint Review é inspecionar o resultado da Sprint e determinar as adaptações futuras
- O Scrum Team apresenta os resultados de seu trabalho para os principais stakeholders e o progresso em direção a Meta do Produto é discutido.
- **Focada no produto**
- Demonstração funcional do produto
- PO confirma cada item do backlog que está sendo entregue “Pronto”
- Duração máxima de 4 horas para uma Sprint de 4 semanas
- Todos participam

### Sprint Retrospective

- O propósito da Sprint Retrospective é planejar maneiras de aumentar a qualidade e a eficácia
- indivíduos, interações, processos, ferramentas e sua Definição de Pronto. 
- **Focada no processo**
- Permite a melhoria durante o projeto
- Não se deve buscar melhorias no produto, não é este o objetivo
- Ocorre no último dia da Sprint
- Duração máxima 3h para uma Sprint de 4 semanas

## Cerimônias

- Sprint
- Sprint Planning
- Daily Scrum
- Sprint Review
- Sprint Retrospective

# Estimativas

- Tempo Real
	- Feita em horas
	- Baseado em cálculo
- Tempo Ideal
	- Considera que não haverá nenhuma interrupção
- Story Points (Pontos Ágeis)
	- Unidades relativas de tempo
	- Mais utilizado em metodologias ágeis
	- Baseia-se comparações: Dobro do tempo em relação a atividade X, metade do tempo da atividade Y, etc…
	- Um ponto ágil pode ser baseada em características da funcionalidade, por exemplo, número de campos
		- Tela com 8 campos → 8 pontos ágeis
- Pode utilizar escala Fibonacci (1, 2, 3, 5, 8, 13, …)
- T-Shirt Sizing: PP, P, M, G, GG, etc…
- **Estimativas são feitas exclusivamente pelos desenvolvedores**
- Planning poker
	- técnica de planejamento baseada no consenso entre as pessoas para determinar o tamanho de cada item do product backlog. Cada membro do time recebe um conjunto de cartas, com os valores seguindo a **sequência de Fibonacci**. Em seguida, para cada história de usuário analisada, cada membro da equipe joga uma carta com o valor que representa o esforço para implementar a história. Caso haja diferença entre as cartas jogadas, ocorrem novas jogadas, até se chegar a um consenso.

# Representação de itens de backlog

## Caso de uso

- Mais tradicional
- Considerado pesado

## História de usuários

- Mais utilizado por equipes ágeis
- Busca descrever um requisito de forma mais leve sob o ponto de vista do usuário

## Gráficos de acompanhamento

- O Scrum não especifica nenhuma ferramenta/gráfico de acompanhamento, mas recomenda que eles existam.
- O mais comum é o gráfico de burndown

![[Untitled 359.png]]

![[Scrum.png]]