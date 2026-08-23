---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2024-08-28T08:48:00
Owner:
  - Eduardo Quinalha
---
# Tipos de Erros

- Erro de Disco:
	- Falhas físicas ou lógicas relacionadas aos dispositivos de armazenamento.
	- Podem resultar em perda de dados ou indisponibilidade
- Erro de Integridade:
	- Violação das regras de integridade definidas no esquema
- Erro de sistema:
	- Falha de hardware, software ou infraestrutura que afetem a disponibilidade do BD
- Erro Lógico:
	- Condição interna
	- Entrada defeituosa, dados não encontrados, estouro de limite de recursos

# Tipos de processamento

- Online (OLTP)
	- Projetado para lidar com transações em tempo real
	- Interações individuais dos usuários com o sistema
	- Suporta operações CRUD de pequena escala
	- Foco:
		- Resposta rápida
		- Transações pequenas
		- Consistência
		- Atualizações contínuas
- Batch
	- Sem interação com o usuário
	- Grandes volumes de dados
	- Foco
		- Eficiência de processamento
		- Agendamento
		- Agrupamento de várias transações
		- Assíncrono

# Bloqueios

- Bloqueio compartilhado / Bloqueio para leitura
	- A transação pode apenas ler o dado
	- Mais de uma transação podem ter este bloqueio simultaneamente
- Bloqueio exclusivo / Bloqueio de escrita
	- A transação pode ler e escrever
	- Apenas uam transação pode ter este bloqueio em um período de tempo

# Concorrência

- A **execução concorrente de programas de usuário** em um SGBD permite que **várias transações ocorram simultaneamente**
- Nos sistemas de banco de dados, os **acessos a disco** são geralmente uma **operação lenta em comparação com a velocidade da CPU**. 
- Ao **manter a CPU trabalhando em vários programas de usuário concorrentemente,** é possível reduzir o tempo de espera causado pelos acessos a disco. 
- Enquanto um programa está esperando pela conclusão de uma operação de leitura ou gravação no disco, a CPU pode ser alocada para **executar outras tarefas**, mantendo-a ocupada e maximizando a utilização dos recursos do sistema.

# Estados de uma transação

## Ativa

-  a transação está em andamento. 
- As operações de leitura e escrita estão sendo realizadas sobre os dados. 
- Durante esse período, a transação pode ser abortada por decisão do usuário ou por um erro que comprometa a continuidade do processo.

## Parcialmente Confirmada

- Ocorre **após a última instrução** da transação ser executada, **mas antes de a transação ser efetivamente gravada** de forma permanente no banco de dados.
- Neste ponto, a transação **ainda pode ser abortada** se ocorrer alguma falha.

## Confirmada (commited)

- Persistidas no banco
- todas as mudanças realizadas por ela são permanentemente gravadas no banco de dados
- Após ser confirmada, a transação **não pode mais ser revertida.**

## Falha

- Se a transação encontrar um erro durante a execução ou se o sistema decidir abortá-la (por exemplo, devido a um deadlock ou outras condições de falha), ela entra no estado de falha.
- As alterações realizadas até o ponto de falha **precisam ser desfeitas **para garantir que o banco de dados volte a um estado consistente.

## Abortada

- **Depois que a transação falha, ela é abortada.**
- Neste estado, todas as operações realizadas por essa transação **são revertidas,** e o banco de dados é **restaurado ao estado anterior **ao início da transação. 
- A transação** pode ser reiniciada a partir deste ponto ou completamente descartada.**

## Gerenciamento de transações distribuídas

![[Gerência de Transações synced block]]

- 2PC
![[Untitled 701.png]]
![[Untitled 702.png]]
	- Todos os nós devem concordar com o commit antes dele ser efetivado, porém isto pode criar bloqueios ou espera excessiva, em casos de falha de um dos nós durante o processo ou até mesmo segmentação da rede. O 3PC visa solucionar este problema.
	- Fase 1
		- O nó coordenador (C1) registra no log o início da transação <prepare T> e envia a mensagem <prepare T> para os nós participantes;
		- Ao receber a mensagem, cada nó participante vai determinar se é possível efetivar sua porção da transação.
			- Caso afirmativo, registra em seu log a mensagem <ready T> e à devolve para C1;
			- Caso negativo, registra em seu log a mensagem <no T> e devolve uma mensagem <abort T> para o C1;
	- Fase 2
		- O nó coordenador (C1) recebe as mensagens dos nós participantes. 
		- Caso todas as mensagens tenham sido <ready T>, ele registra no log a mensagem <commit T> e envia para os nós participantes;
		- Caso alguma mensagem tenha sido <abort T>, registra a mensagem e envia o <abort T> para os sites participantes
	- Em algumas implementações, após o commit os sites ainda devolvem a mensagem <acknowledge T> para o coordenador, sinalizando que o commit local foi bem sucedido.
- 3PC
![[Untitled 703.png]]
	- Este método necessita que um número mínimo de sites participantes esteja ativo (ou seja, tem uma tolerância a falha de alguns nós)
	- A primeira fase é idêntica ao 2PC
	- Fase 2
		- Caso não recebe mensagem de um dos participantes ou recebe um <abort T> de algum deles, C1 fará o procedimento de abortagem
		- Se receber <ready T> de todos eles, C1 adicionará <precommit T> no log e enviará para todos os participantes
		- Os participantes recebem a mensagem <precommit T> acrescentam no log local e devolvem <acknowledge T> para o C1, caso não seja possível efetivar a transação localmente, devolvem um <abort T> para C1
	- Fase 3
		- C1 Aguarda pelo menos K mensagens de <acknowledge T>, caso positivo, registra o <commit T> e envia de volta aos nós participantes;

# Problemas decorrentes de falta de controle de concorrência

- Dirty Read
	- Uma transação lê dados modificados por outra transação ainda não confirmada
- Leitura não repetível (Non-repeatable Read)
	- Uma transação lê um mesmo dado mais de uma vez com valores diferentes
	- Ocasionado por modificações realizadas por outras transações concorrentes
- Leitura fantasma
	- Leitura de um valor que, ao final da transação, não existe mais
- Atualização fantasma
	- Idem à leitura fantasma.
	- A informação é atualizada, porém antes de ser confirmada, outra transação altera o valor

# Controle de concorrência

## Bloqueio de modo múltiplo

- Permite que diferentes transações coexistam e operem em paralelo, mesmo quando acessam os mesmos dados, através da atribuição de diferentes tipos de bloqueios com base nas necessidades específicas de cada transação.
- **Modos de Bloqueio:** O sistema define um conjunto de modos de bloqueio, cada um com características e restrições específicas de acesso. Os modos de bloqueio mais comuns são:
	- **Compartilhado (S):** Permite que múltiplas transações leiam os dados, mas nenhuma pode modificá-los.
	- **Exclusivo (X):** Permite que apenas uma transação leia e modifique os dados.
	- **Intenção Compartilhada (IS):** Indica que a transação pretende adquirir um bloqueio compartilhado no futuro.
	- **Intenção Exclusiva (IX):** Indica que a transação pretende adquirir um bloqueio exclusivo no futuro.
- **Gerenciamento de Conflito:** Se duas transações solicitarem o mesmo bloqueio em um dado, o sistema pode entrar em conflito. Para resolver o conflito, o sistema pode:
	- **Adiar a transação que solicitou o bloqueio:** A transação é colocada em espera até que o bloqueio seja liberado pela outra transação.
	- **Abortar uma das transações:** Uma das transações é abortada e precisa ser reiniciada posteriormente.
- **Liberação de Bloqueios:** Quando uma transação termina, ela libera todos os bloqueios que adquiriu. Isso permite que outras transações acessem os dados livremente.

## **Controle de Concorrência Baseado em Timestamps**

- Cada transação recebe um timestamp único no momento de sua criação.
- As transações são ordenadas por timestamp e executadas sequencialmente.
- Se uma transação tenta acessar um dado que está sendo modificado por outra transação com timestamp mais antigo, a primeira transação é abortada.

## **Controle de Concorrência Otimista**

- As transações assumem que podem acessar os dados livremente sem causar conflitos.
- As transações validam suas modificações antes de serem aplicadas ao banco de dados.
- Se uma transação tenta modificar um dado que foi modificado por outra transação, a primeira transação é abortada e reiniciada.

## **Controle de Concorrência Multiversão (MVCC)**

- O banco de dados armazena várias versões de cada dado.
- As transações leem a versão mais recente do dado que precisa acessar.
- As transações modificam uma nova versão do dado, sem afetar as versões existentes.

## Protocolo de Bloqueio de Duas Fases

- Protocolo de controle de concorrência utilizado em SGBD distribuídos
- Evita deadlocks e inconsistência de dados
- Divide a execução em duas fases distintas
	- **Fase de Expansão**
		- A transação solicita bloqueios dos recursos que precisa acessar
		- A transação **não pode liberar nenhum bloqueio nesta fase**
		- Terminada esta fase, a transação inicia a execução de seus procedimentos
	- **Fase de Encolhimento**
		- Ao concluir as operações da transação, entra na fase de encolhimento
		- A transação libera os bloqueios solicitados na fase anterior
		- Ela **não pode solicitar nenhum novo bloqueio nesta fase**