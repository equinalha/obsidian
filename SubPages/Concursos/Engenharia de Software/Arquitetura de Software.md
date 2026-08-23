---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2024-10-01T20:02:00
Owner:
  - Eduardo Quinalha
---
# Coesão e Acoplamento

## Tipos de Acoplamento

- **Acoplamento por conteúdo**
	- Ocorre quando um módulo faz uso de estruturas de dados ou de controle mantidas no escopo de outro módulo
- **Acoplamento Comum**
	- Ocorre quando um conjunto de módulos acessa uma área global de dados
- **Acoplamento por Controle**
	- Módulos passam decisões de controle para outros módulos
	- Flags
- **Acoplamento por Carimbo (Stamp)**
	- Comunicação por parâmetros
	- Estruturas de dados
- **Acoplamento por Dados**
	- Uma lista de dados simples é passada como parâmetro de um módulo para outro
	- Correspondência um para um de itens

## Tipos de Coesão

- **Coesão coincidental**
	- Um módulo realiza um conjunto de tarefas frouxamente relacionadas
	- Deve ser evitada
- **Coesão lógica**
	- Um módulo realiza um conjunto de tarefas que estão logicamente relacionadas
	- Geralmente do mesmo tipo
- **Coesão temporal**
	- Um módulo realiza tarefas que devem ser executadas no mesmo decurso de tempo
	- Normalmente na inicialização ou término de funções
- **Coesão procedural**
	- Elementos de processamento do módulo são relacionadas
	- Devem ocorrer em uma ordem específica
- **Coesão de comunicação**
	- Todos os elementos de processamento do módulo se concentram em uma única área de uma estrutura de dados
	- Geralmente utilizam o mesmo parâmetro
- **Coesão sequencial**
	- Os dados de saída de uma atividade servem como dados de entrada para a próxima
- **Coesão funcional**
	- Um módulo realiza uma única tarefa procedural distinta