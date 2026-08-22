---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2026-07-24T12:39:00
Owner:
  - Eduardo Quinalha
---
# Conceitos básicos de SO

## Gerenciamento de:

- Processos;
- Dispositivos de E/S;
- Memória;

> [!note] 🔥
> **O SO Gerencia parcialmente a hierarquia de memória!** Não se pode dizer que gerencia toda a hierarquia, pois registradores, por exemplo, é controlado pela própria CPU

- Arquivos;

## Chamadas de Sistema

- Interface entre o SO e os programas de usuário
- Ex. Chamada de sistema para ler um arquivo

## Processo

- Instância de um programa em execução
- Cada um com seu espaço de memória (de 0 até N)
	- Programa executável
	- Dados do programa
	- Pilha
- Associado a cada processo
	- Conjunto de registradores
	- Outras informações necessárias
- O SO mantém uma tabela dos processos em execução
- Um processo possui uma área de memória dedicada a ele, que é dividida em duas áreas:
	- **Stack area:** contém a pilha de execução, onde são armazenadas os parâmetros, endereços de retorno e variáveis locais de funções. Pode variar de tamanho durante a execução do processo.
	- **Heap area:** contém áreas de memória alocadas a pedido do processo, durante sua execução. Varia de tamanho durante a vida do processo.

## Sistema de Arquivos

- Metadados
- Localização

## Arquitetura de SO

- Monolíticos
- Sistemas em camadas (THE)
- Máquinas Virtuais
- Exonúcleos (Exokernel)
- Cliente/Servidor

# Classificação quanto ao tipo de gerenciamento de processos

## Monotarefa

- Apenas um processo (programa) é executado por vez no processador

## Multitarefa

- Permite a execução de mais de um processo ao mesmo tempo.
- O compartilhamento de tempo no processador é distribuído, de modo que o usuário tenha a impressão que diversos processos estão sendo executados simultaneamente. 
- Os processos compartilham recursos comuns, como processador e memória.

## Multiprocessamento

- Os processos são distribuídos entre dois ou mais processadores.

## Multiprogramação

- O tempo de processamento entre vários processos é dividido com objetivo de manter o processador sempre ocupado.
- Mantém vários processos na memória ao mesmo tempo
- O SO suspende processos que estejam aguardando algum recurso como IO

# Tipos de Kernel

## Monolítico

- Controladores e extensões são executadas no mesmo espaço de kernel, com acesso completo ao hardware
- Se houver ocorrência de erro, todo o sistema pode ser afetado
- Melhor desempenho
- Um processo pode interagir com qualquer outro, livremente
- Exemplo: Linux, Unix

## Microkernel

- Kernel de tamanho reduzido
- Somente processos básicos do SO executam no espaço do kernel
- Os demais utilizam o espaço de usuário
- Se ocorrer erro, basta reinicializar o módulo que falhou
- Mais estável
- Exemplos: AIX, Minix

## Híbrido

- Combinação de Monolítico com Microkernel
- Existe um código não essencial rodando no espaço do kernel, que visa acelerar a execução de operações
- Exemplos: MacOS, Windows, Android

## Exokernel

- Permite aos aplicativos o controle quase total do hardware
- Reduz as abstrações do SO
- Fornece uma API de baixo nível
- Fornece um melhor desempenho aos aplicativos porém com uma complexidade maior de programação

# Gerência de Processos

## Processo

- Trata-se de **um programa em execução**
- Cada processo tem sua **CPU virtual**
- Durante o chaveamento, o estado dos registradores e conteúdo das variáveis é armazenado para que depois possa retornar do exato ponto em que parou
- Do ponto de vista de cada processo, ele tem uma CPU só para ele

### Criação de processo

- Criação de um processo se dá por quatro eventos possíveis:
	- Inicialização do sistema
	- Chamada de sistema (**fork()**)
	- Pedido de usuário
	- Início de uma tarefa em lote

### Metadados de um processo

- **Contexto de software:**
	- Nome do processo
	- Identificador (PID)
	- Proprietário
	- Prioridade
	- …
- **Contexto de Hardware**
	- Registrador de Status
	- Registrador SP
	- Registrador PC
	- Registradores gerais
- **Espaço de endereçamento**

![[Untitled 518.png]]

### **Hierarquia**

- Cada processo possui apenas 1 pai
- 0 ou n filhos

![[Untitled 519.png]]

### Estados de Processos

- **Executando**: realmente está utilizando a CPU
- **Pronto**: temporariamente parado. Pode estar na fila aguardando executar novamente
- **Bloqueado**: incapaz de continuar a execução até que um determinado evento ocorra. Ao sair deste estado, o processo não volta a execução, mas sim, vai para a fila, no estado pronto, até chegar sua vez novamente.

![[Untitled 520.png]]

### Classificação quanto ao uso de recursos

- **CPU-Bound: **Processos que passam a maior parte do tempo processando (utilizando CPU)
- **I/O Bound:** Processos que dependem em sua maior parte de dispositivos de E/S

## Threads

- Fluxos de controle **dentro de um mesmo processo**
- Permite **execução em paralelo** como se fossem processos separados
- **O chaveamento entre Threads é mais rápido**
- **Compartilham a**** mesma área de memória (Espaço de endereçamento)**
- **Possuem**** pilhas e registradores de estados diferentes**
- **Itens compartilhados** por threads: 
	- Espaço de endereçamento, Variáveis globais, Processos-filhos, Arquivos abertos, Alarmes pendentes, Sinais e tratadores de sinais, Informação de contabilidade.
- **Itens privados** por threads: 
	- Contador de programa, Registradores, Pilha, Estado.

### **Escalonamento de Threads**

- Threads em nível de usuário
- Threads em nível de núcleo
- O algoritmo de escalonamento pode ser qualquer um dos mesmos utilizados por processos

## Comunicação entre processos

### **Condições de corrida**

- Ocorre quando dois ou mais processos ou threads precisam acessar e manipular um recurso compartilhado simultaneamente.
- Pode levar a resultados inconsistentes

### **Seção crítica**

- Parte do código que manipula ou acessa um recurso compartilhado
- Para evitar condições de corrida, é necessário garantir que apenas um processo por vez execute esta seção do código

### **Semáforos**

> [!note] 🔥
> **Usado na comunicação a nível de processos**

- Variáveis especiais que fazer o controle de acesso às seções críticas do código
- Tipos
	- Binário → 0: recurso ocupado, 1: recurso disponível
	- Contador → Tem um valor inteiro positivo. Quando um processo utilizar o recurso, decrementa seu valor. Quando liberar incrementa.

### **Mutex**

> [!note] 🔥
> Tipo mais simples de semáforo, utilizado a** nível de Threads**

- Mutual Exclusion
- Tipo de semáforo binário.
- O processo ou thread que obter o mutex pode adentar à seção crítica enquanto os demais ficam bloqueados agurdando sua liberação
- Tipos de algoritmos Mutex
	- Centralizado
		- Um processo é eleito coordenador
		- Qualquer outro processo que deseje acesso à seção crítica, vai enviar uma mensagem para o coordenador
		- Caso disponível, o coordenador irá conceder o acesso
		- É do tipo FCFS
		- Os processos não conseguem distinguir um coordenador inativo de uma permissão negada
![[Untitled 521.png]]
	- Distribuído
		- Os próprios processos controlam o acesso aos recursos
		- As mensagens de solicitação são enviadas a todos os processos com um marcador timestamp
		- Em caso de conflito, o desempate é feito pelo menor timestamp
		- O processo solicitante deve receber um OK de todos os outros processos para ter acesso ao recurso
![[Untitled 522.png]]
	- Token Ring
		- Funcionamento padrão do token ring
		- Quando um processo termina de usar o recurso, passa a ficha adiante

## Preempção

- Capacidade de retirar um processo em execução para dar espaço a outro.
- Fundamental para o uso de escalonamento
- Sistemas não preemptivos, executam um processo até o fim, antes de dar lugar a outro

## Starvation

- Ocorre quando um processo aguarda sua vez na fia porém devido às regras de escalonamento sempre perde sua vez em detrimento de outros mais prioritários
- Também ocorre em sistemas não preemptivos quando um processo não libera a CPU e o processo que está agurdando permanece indefinidamente na fila
- Alguns algoritmos que favorecem a ocorrência de starvation
	- Shortest Job Next
	- Não preemptivo

## Escalonamento

- Escalonador de Curto Prazo
	- Também conhecido como Escalonador de CPU ou dispatcher
	- Seleciona o processo da fila de prontos que será executado na CPU
	- Frequência Alta
- Escalonador de Médio Prazo
	- Faz a alocação de processos na memória principal
	- Swapping
- Escalonador de Longo Prazo
	- Decide quais processos serão aceitos pelo SO para irem p/ memória principal
	- Menor frequência
- Categorias de Algoritmos
	- Lote:
		- Sistemas de grande porte
		- Aceita algoritmos não-preemptivos ou preemptivos com grande intervalo de tempo para cada processo
		- Menor quantidade de trocas melhora o desempenho
	- Interativo:
		- Fundamental o uso de preempção
		- Sistemas que interagem com o usuário
	- Tempo real:
		- Aplicações críticas sem interação com o usuário
		- Exemplo: CLP

### Escalonamento em sistemas em lote

- **FCFS** (First Come, First Served)
	- **Não preemptivo**
	- FIFO
	- Execução na sequencia de chegada
- **SJF** (Shortest Job First)
	- **Não preemptivo**
	- Tarefas menores são executadas primeiro
	- São executadas por completo até darem lugar à próxima tarefa
- **SRT** (Shortest Remaining Time Next)
	- **Versão preemptiva do SJF**
	- Menor tempo de execução restante
	- Na chegada de um processo menor, o atual é suspenso

### Escalonamento em sistemas interativos

- **Round-Robin**
	- Rodízio simples
	- Os processos são despachados como FIFO
	- **Quantum** (fatia de tempo da CPU)
	- Excesso de chaveamentos causa perda de desempenho
	- **Não tem prioridade!**
- **Prioridade**
	- Semelhante ao rodízio, porém processos com maior prioridade ganham quantums maiores ou mais quantums
- **Múltiplas filas**
	- Processo evolui por filas em que cada uma tem quantidade de quantums diferentes.
- **Escalonamento Garantido**
	- Em um sistema com N usuários, cada um recebe 1/N do poder de CPU
- **Escalonamento por sorteio**

### Escalonamento Cooperativo

- Escalonamento Preemptivo
- O próprio processo em execução verifica periodicamente a fila de processos prontos e pede para liberar o uso da CPU em detrimento de outro
- Usado nas primeiras versões do Windows
- Multitarefa cooperativa

## Tabela de processos

- Região de memória do kernel que guarda a lista de processos e seus estados:
	- Program Counter
	- Ponteiro de pilha
	- Alocação de memória
	- Estado dos arquivos abertos
	- Contabilidade
	- escalonamento
	- Registradores
	- Prioridade
	- Id, parent ID
	- Sinais
	- Tempo de uso de CPU
	- Diretório raíz
	- Dentre outras

## Starvation

- Quando um processo aguarda na fila para entrar em execução, mas sempre perde a vez, devido a alguma peculiaridade do algoritmo de escalonamento

## Deadlock

- Também conhecido como **impasse**
- Dois ou mais processos diferentes bloqueando recursos enquanto aguarda o outro, de forma cruzada
- **Condições necessárias (todas)**
	- Exclusão mútua
	- Posse e espera
	- Ausência de preempção
	- Condição de espera circular
![[Untitled 523.png]]
- **Algoritmos para tratamento de deadlocks**
	- **Avestruz**
		- Estratégia mais adotada
		- Simplesmente não faz nada
		- O custo para a CPU para detecção e tratamento de deadlocks é alto e não compensa, visto que a frequência de ocorrência é baixa
	- **Detecção e recuperação**
		- Detecta a ocorrência
		- Mata um dos processos. Se não resolver, mata outro, e assim por diante
	- **Prevenção de impasses**
		- Monitora continuamente em busca das quatro condições
		- Quando estiver próximo da ocorrência das quatro simultaneamente, interrompe um dos processos
	- **Evitação de impasses**
		- A alocação de recursos é mais cuidadosa

## Encerramento de Processos

- De forma voluntária
	- Saída normal → Conclusão do trabalho
	- Saída por erro → Erro de sintaxe
- Involuntária
	- Erro fatal → Instrução ilegal, divisão por zero
	- Cancelamento por outro processo

# Gerenciamento de E/S

- **Dispositivos de bloco**
	- Armazenam em blocos de tamanho fixo (de 512 B até 32KB)
	- Cada bloco tem um endereço
	- Exemplo discos
	- Permitem leitura e escrita independente
- **Dispositivos de caractere**
	- Fluxo de dados contínuo
	- Não é endereçável
	- Não tem operação de busca
	- Ex: impressoras, mouses, interfaces de rede
- **Controladoras de dispositivo**
	- Adaptador
	- Exemplo: Placa de vídeo, rede

## SystemCalls

- As chamadas de sistema são responsáveis por estabelecer uma interface entre o sistema operacional e os processos do usuário.
- Essas instruções permitem aos aplicativos em execução, interagir com os componentes do sistema operacional e dispositivos a ele conectados.

## Operações de E/S

- **E/S programada**
	- A CPU pergunta aos periféricos se estão aptos a receber/transmitir dados
	- **Via de regra, a CPU fica bloqueada, esperando o dispositivo completar a tarefa**
	- Tipos
		- Modo bloqueado (busy wait)
			- Bloqueia a CPU até que a transmissão seja completada
		- Polling
			- A CPU pergunta a cada dispositivo se alguém tem algo a transmitir
		- Interjeição
			- Melhoria do polling
			- Antes de perguntar a cada dispositivo, verifica um sinal resumido (porta OU) se alguém tem algo a transmitir
- **Interrupções**
	- As controladoras mandam um sinal de interrupção para avisar que tem alguma operação pronta ou algum dado a receber
	- **Não bloqueia a CPU mas é intermediado pela CPU**
- **Acesso direto a memória (DMA)**
	- **Não bloqueia a CPU**
	- **Não há sequer envolvimento da CPU na operação**
	- Necessita de um hardware (controladora de DMA)
	- Tem acesso direto ao barramento de memória (**independente da CPU**)
	- Contém registradores que podem ser lidos/escritos pela CPU
	- Deixa a CPU mais livre, tratando menos interrupções
