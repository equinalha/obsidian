---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2026-03-18T15:41:00
Owner:
  - Eduardo Quinalha
---
# Kanban

[https://www.alura.com.br/artigos/metodo-kanban](https://www.alura.com.br/artigos/metodo-kanban)

> [!note] 🔥
> **Kanban não é uma metodologia ágil para desenvolvimento de software!
Adéqua-se melhor ao conceito de gestão de mudança

**No entanto, pode ser utilizado como **ferramenta** dentro de outra metodologia para desenvolvimento de sistemas

- O Kanban é focado na **gestão visual do trabalho**, ajudando as equipes a visualizar o fluxo de tarefas e a identificar gargalos no processo de desenvolvimento.
- **Muito bom para gestão de mudanças**
- Um dos elementos-chave do Kanban é o estabelecimento de limites para os trabalhos em andamento, conhecidos como "Work In Progress" (WIP) limits.
- O modelo *Kanban para desenvolvimento de software* combina elementos do **pensamento Lean** com o **pensamento ágil** no processo de desenvolvimento de software.
- Conjunto de princípios e práticas que tem o objetivo de proporcionar uma evolução na forma que sua equipe (ou empresa) entrega valor nos serviços prestados.
- método “evolutivo” e “evolucionário”
- Não prescritivo
- É mais útil em manutenção do que em desenvolvimento de software
- No **Kanban**, não há a prática de ***timeboxes*** como no método Scrum. 
- No Scrum, o trabalho é organizado em iterações fixas chamadas de sprints, que são essencialmente *timeboxes*. 
- Já no Kanban, o foco está em um <u>fluxo contínuo de trabalho</u>. 
- No entanto, é comum que as equipes que utilizam Kanban adotem uma **cadência fixa** para atividades como planejamento, revisões e entregas. 
- Isso ajuda a manter um ritmo consistente de melhorias e entregas, embora não envolva o conceito de *timeboxing*.

![[Untitled 352.png]]

# Características

- **Produção nivelada:** Busca equilibrar demanda de trabalho em cada etapa, evitando gargalos
- **Redução do tempo de preparação:** Foco na mudança entre tarefas e processos (mudança de configuração, troca de ferramenta, etc)
- **Layout de máquinas: **Disposição física dos equipamentos de trabalho
- **Padronização dos trabalhos:** Elimina variações e inconsistências. Facilita o treinamento de novos membros.
- **Aperfeiçoamento contínuo das atividades:** Análise de dados e identificação de oportunidades. As equipes são estimuladas a resolver problemas.

# Tipos

- Kanban de produção
- Kanban de movimentação

# Regras

- **Começar com o que tem agora: **entender o fluxo de trabalho existente, visualizá-lo em um quadro Kanban e identificar as etapas e atividades envolvidas. 
- **Buscar mudanças graduais: **buscar mudanças graduais e constantes, visando aprimorar o fluxo de trabalho e os processos.
- **Respeitar o processo atual, papéis, títulos e responsabilidades: **O Kanban não impõe uma estrutura rígida, mas permite que as equipes trabalhem dentro do contexto e da cultura organizacional existentes.
- **Todas as pessoas liderando: **Cada pessoa é incentivada a assumir a responsabilidade pelo seu trabalho, tomar decisões e contribuir para o sucesso geral do projeto. A liderança não é restrita a cargos formais, mas é encorajada em todos os níveis, permitindo a colaboração e o empoderamento de cada profissional.

# Fases

- To Do
	- demandas são registradas e priorizadas.
	- As tarefas nesta fase podem estar esperando para serem iniciadas ou aguardando a disponibilidade de recursos.
- Doing
	- tarefas que estão sendo trabalhadas e em processo de execução
	- É importante limitar o número de tarefas em andamento, para evitar sobrecargas e manter o fluxo de trabalho equilibrado.
	- Limitar o WIP força a equipe a se concentrar em um número menor de tarefas, priorizando as mais importantes e evitando a dispersão de esforços.
	- O WIP ajuda a identificar gargalos e otimizar o processo de desenvolvimento, reduzindo o tempo de ciclo e aumentando a entrega de valor.
- Done
	- serve como um indicador visual das tarefas que foram concluídas com sucesso. 

# Princípios

- **Princípios Focados na Gestão de Mudanças**
	- Trata da própria evolução da utilização do método ao longo do tempo
	- Princípios:
		- Comece pelo que você faz agora;
		- Obtenha acordos;
		- Encoraje atos de liderança em todos os níveis.
- **Princípios Focados na Entrega de Serviços**
	- Refere-se ao andamento do trabalho no dia a dia.
	- Princípios
		- Compreender e focar nas **necessidades e expectativas dos e das clientes**;
		- Deixar as pessoas colaboradoras se **auto-organizarem**;
		- **Revisar regularmente** seu sistema e suas políticas.

# Práticas

1. Visualizar o trabalho
	- Criar um modelo visual
	- Quadro Kanban + cartões
2. Limitar o Trabalho em Progresso (WIP)
	- Pare de começar e comece a terminar
	- Priorizar a conclusão de trabalho em andamento
	- Uma das mais importantes métricas do método
	- WIP muito alto causa declínio de produtividade
3. Gerenciar o Fluxo
	- Movimento do trabalho, visualizado pelas métricas e quadro Kanban
	- Quanto mais contínuo e previsível, melhor gerenciado está
4. Tornar as políticas explícitas
	- Tudo o que se refere ao funcionamento do Kanban deve ser considerado política
	- Critérios para puxar/mover itens
	- Limites de WIP
	- Classes de Serviços
5. Estabelecer ciclos de feedback
	- Criar uma cadência de trabalho
	- Reuniões que definem o andamento do item
	- Facilita a visualização do trabalho pelo time
6. Melhorar colaborativamente, evoluir experimentalmente
	- Estabelecer um ambiente propício à experimentação e aos erros controlados

# **Métricas mais utilizadas no Kanban**

- **Tempo de Atendimento (*****Lead Time*****)**
	- tempo que leva para que um pedido (serviço) que atingiu o chamado “**ponto de compromisso”** chegue até o final do Sistema Kanban, a última coluna do quadro, que normalmente é a coluna “Finalizado” ou “Entregue”.
	- ponto de compromisso é o momento do fluxo de trabalho em que o ou a cliente entende que o serviço está sendo executado e isso pode ser “combinado”.
![[Untitled 353.png]]
	- Assim que o serviço for entregue e o cartão movido para a coluna “Finalizado”, fechamos a contagem do tempo.
	- as métricas devem ser **medidas várias vezes** e gerar **médias de contagem**, já que de uma contagem isolada para outra pode haver muita diferença.
- **Tempo de Ciclo (*****Cycle Time*****)**
	- Tempo de Ciclo ou *Cycle Time* é uma medida normalmente usada para **contar o tempo gasto para executar uma das etapas do processo**, como, por exemplo, o **tempo de ciclo de análise**.
> [!note] 🔥
> - Lead Time (#1) → Tempo decorrido entre a solicitação de um item e sua entrega final
- Delivery Rate → Média de entregas por período de tempo, por exemplo, entregas por semana
- Cycle Time (#2) → Tempo real gasto na execução da tarefa
> ![[Untitled 354.png]]
- **Trabalho em Progresso (*****Work-in-Progress*****)**
	- Por definição, todo cartão que já atingiu o ponto de compromisso e ainda não está terminado é um Trabalho em Progresso. 
	- Além disso, pode-se contar *WIP* por coluna. 
	- Por ciclo, considerar o *WIP* médio e outras variações deste indicador
- **Vazão (*****Throughput*****)**
	- quantidade de serviços (cartões) finalizados em um período. 
	- Esta é uma importante métrica da **velocidade com que o time entrega valor**.

![[Untitled 355.png]]

- O quadro possui 6 tarefas: Fazer, Desenvolver, Fila p/ Teste, Teste, Implantar e Feito. A coluna anterior à Teste (Fila p/ teste) é denominada Buffer. No Buffer estão as tarefas que estão aguardando para serem testadas.
- Os defeitos estão sempre acima e são prioridade. Após eles as tarefas recebem um peso intermediário e por último, os recursos.
- Os números indicam o limite de itens que a coluna pode receber. No caso, Fazer só pode ter 6 itens.
- As duas tarefas de cima possuem prioridade maior do que a de baixo.
- Pode ter uma linha horizontal para cada projeto, por exemplo. Ou uma linha para cada tipo de item (defeitos, tarefas)
