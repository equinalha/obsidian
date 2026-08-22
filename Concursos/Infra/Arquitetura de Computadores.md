---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2026-08-05T07:50:00
Owner:
  - Eduardo Quinalha
---
# Linguagens, Níveis e VM

**Tradução: **Transcrever uma instrução em uma linguagem L1 em n instruções em uma linguagem L0

**Interpretação:** “On the fly”. A instrução em L1 é um dado de entrada para as instruções em L0, que vão sendo executadas a medida que os dados vão entrando

![[Untitled 534.png]]

# Arquiteturas clássicas

- **Von Neumann**
	- Barramento único
	- Memória única para dados e instruções
	- Baixo custo
	- Desempenho limitado pelo barramento
- **Harvard**
	- Duas memórias separadas e independentes
		- Dados
		- Instruções
	- Por consequência, dois barramentos


> [!note] 🔥
> Para facilitar os cálculos com binário:

2^10 = 1k
2^20 = 1M
2^30 = 1G
(…)

> [!note] 🔥
> Na prática, o que usamos hoje é uma mistura, pois na memória cache, existe uma separação entre dados e instruções

# Arquitetura da CPU

> [!note] 🔥
> **Barramentos (Pegadinha da CESPE)**
> **Barramento Local**: que conecta o <u>processador</u> a uma <u>memória cache</u> e que pode aceitar um ou mais dispositivos locais.
> 
> **Barramento Interno do processador:** necessário para transferir dados entre vários <u>registradores e ALU</u>, porque a ALU na verdade opera apenas os dados que estejam na memória interna do processador.
> 
> Fonte: Stallings, 8ª edição

## Registradores de uso específico

- PC - Program Counter
	- Aponta para a próxima instrução a ser executada que encontra-se na memória principal
- IR - Instruction Register
	- Instrução atual que está sendo executada no processador
- MAR - Memory Adddress Register
	- O endereço da memória que está sendo apontado para a informação do MBR
- MBR - Memory Buffer Register
	- Armazena um dado que será gravado na memória ou foi lido da memória
- PSW - Program Status Word
	- Informações de controle da execução
	- Prioridade
	- Modo Kernel / User

## Registradores de uso geral

Utilizados para armazenar dados para a entrada da instrução e saída das operações lógicas e aritméticas

- Registradores de uso geral ou dados
- Registradores de segmento ou endereço
- Registradores de status ou flags

## Risc x Cisc

> [!note] 🔥
> CPI = Cycles Per Instruction

- **CISC**
	- Instruções complexas
	- Em geral não utiliza-se pipelining em CISC
	- Grande quantidade de instruções com **múltiplos modos de endereçamento**
	- **Uso de microcódigo** (Embutido na CPU)
		- Converte uma instrução Assembly em um conjunto de instruções internas da CPU
		- Fica armazenado em uma área de memória dentro da própria CPU, mais especificamente, dentro da UC (ROM)
		- Por consequência acaba faltando espaço para outras estruturas como registradores
		- Possibilita a inclusão de novas instruções dentro de uma nova versão do processador, sem mexer nas demais estruturas do projeto
	- **As instruções são completas e eficientes**
	- **Instruções de máquina de “Alto Nível”**
	- **Instruções com largura variável**
	- **Instruções que demandam múltiplos ciclos de clock**
	- **Poucos registradores**
	- **Há registradores especializados: controle, segmento, etc.**
	- Exemplos
		- x86, pentium, pentium MMX, etc…
	- Modos
		- Usados por instruções comuns (ADD, SUB, MULT)
		- Registrador para registrador
		- Registrador para memória (mais lento)
		- Memória para registrador (mais lento)
- **RISC**
	- Pelo fato de possuir uma arquitetura mais simples, pode rodar em frequências maiores
	- (Não é regra, mas as bancas costumam associar RISC com servidores)
	- Poucas instruções com largura fixa
	- Menor quantidade de modos de endereçamento
	- **Uso intenso de pipelining**
	- Execução rápida de cada instrução (uma por ciclo de relógio)
	- Não fazem o uso de microcódigos
	- **Menos acesso a memória principal**
		- **Somente pelas instruções LOAD e STORE**
	- **Maior quantidade de registradores**
	- Requer compiladores mais complexos

# Memória principal

> [!note] 🔥
> Em processadores atuais de 64 bits, apesar dos 64 bits, o barramento de endereços trabalha com no máximo 40 bits, possibilitando o endereçamento de até 1TB de memória RAM física. Para o endereçamento de memória virtual, 48 bits estão disponíveis, podendo teoricamente endereçar até 256 TB

> [!note] 🔥
> Operações de leitura/escrita são sincronizadas com o clock da CPU

## Tipos de memória

**Memória de rascunho** é composta basicamente pela Cache L1, que fica mais próxima ao processador. Em processadores CISC, este é o nível de memória acessível pelo micro programa.

**Memória principal** é composta pela RAM, normalmente mais barata e de maior capacidade que a cache, porém, mais lenta.

**MMU **é o componente da arquitetura responsável por trazer para a memória cache os dados utilizados com mais frequência pela CPU. Por análise estatística, definiu-se que os dados mais acessados tendem a estar próximos ao ultimo dado requisitado. Sendo assim, a MMU traz blocos de memória de uma vez para a cache.

## DRAM

- Dinâmica
- Armazenam dados em capacitores
- Necessita refresh periódico
- É a memória RAM de fato
- mais simples e menor, mais densa
- mais barata

## SRAM

- Estática
- Não necessita refresh
- Utiliza transistores e flip-flops
- Utilizado em memória cache
- Mais cara

## Memória Cache

### **Princípio da Localidade**

- **Espacial**
	- tendência de um programa acessar dados ou instruções que estão fisicamente próximos no espaço de memória.
	- Por exemplo, em arrays ou em blocos de código, acessar um endereço de memória pode indicar que endereços próximos serão acessados logo em seguida.
	- **Mapeamento direto**
		- cada bloco de memória principal só pode ser armazenado em uma posição específica da cache. 
		- Isso significa que a localização na cache para um bloco de memória é determinada por uma fórmula matemática, geralmente um cálculo do tipo "endereço da memória principal mod número de linhas da cache" (Hashing)
		- **Vantagens**
			- Simplicidade de implementação e baixo custo
			- Fácil de encontrar a localização dos dados
		- **Desvantagens**
			- Há um **alto risco de conflito**: se dois blocos diferentes da memória principal têm que ser armazenados na mesma posição da cache, o bloco atual será substituído pelo novo, resultando em uma maior taxa de *miss* (falhas de cache)
	- **Mapeamento associativo**
		- Permite que qualquer bloco de memória principal seja armazenado em qualquer linha da cache
		- Para identificar onde um dado bloco está na cache, cada posição da cache precisa de uma etiqueta (tag) para identificar o bloco correspondente
		- **Vantagens**
			- **Menos conflitos** de mapeamento, pois qualquer bloco de memória pode ser armazenado em qualquer posição da cache, aumentando a flexibilidade
		- **Desvantagens**
			- Mais **caro e complexo** de implementar, pois é necessário um mecanismo para **procurar por toda a cache** para localizar um bloco específico
			- Pode ser mais lento devido à necessidade de procurar a tag correspondente em várias linhas da cache
	- **Mapeamento associativo por conjuntos**
		- combinação dos métodos anteriores
		- A cache é dividida em grupos, chamados de conjuntos, e cada conjunto contém várias linhas (ou "vias")
		- Cada bloco de memória principal é mapeado para um conjunto específico (como no mapeamento direto), mas dentro desse conjunto, ele pode ser armazenado em qualquer uma das linhas disponíveis (como no mapeamento associativo). 
		- Por exemplo, uma cache *2-way set-associative* significa que cada conjunto tem duas vias, ou seja, duas posições para armazenar blocos de dados
		- **Vantagens**
			- Reduz o número de conflitos de mapeamento sem a complexidade total do mapeamento associativo.
			- Proporciona um bom equilíbrio entre complexidade e flexibilidade.
		- **Desvantagens**
			- É mais complexo que o mapeamento direto, pois requer uma lógica adicional para gerenciar a escolha das vias dentro de cada conjunto.
		- **Esquema de endereçamento**
			- A** memória principal** é dividida em **blocos de palavras**
				- Campo de endereçamento de bloco: **s**
				- Campo de endereçamento de palavras: **w**
				- Total de bits para endereçamento da memória: **s + w**
			- A **memória cache** é dividida em **conjuntos**
				- Campo de endereçamento do conjunto: **d**
				- A **Tag** serve para o processador verificar qual bloco exato da memória principal está atualmente ocupando aquele conjunto da cache. 
				- O campo s da memória principal é quebrado em duas partes na cache: a Tag e o índice do conjunto (d).
•** Tag = s - d**
- **Temporal**
	- se um dado ou instrução foi acessado recentemente, é provável que seja acessado novamente em breve
	- Por exemplo, em loops de um programa, o mesmo código e os mesmos dados são frequentemente reusados várias vezes em uma sequência de execução.
- A memória cache usa esses princípios para melhorar o desempenho do sistema. 
- Ela armazena cópias de dados e instruções frequentemente usados de forma temporária e rápida, permitindo que o processador acesse essas informações mais rapidamente do que se tivesse que buscá-las diretamente na memória principal.

### **Níveis de cache**

- L1
	- Dentro da CPU
	- Pode seguir a arquitetura de Harvard (dados / instruções)
- L2
	- Maior que a L1
	- Pode estar dentro da CPU ou fora dela
- L3
	- Na placa mãe (quando existir)
	- Se L2 já for na placa mãe, não existe L3
- **Algoritmos de substituição**
	- LRU (Least Recently Used)
	- FIFO (First in, First out)
	- LFU (Least Frequently Used)
	- Escolha aleatória
- **Política de escrita**
	- Write through
		- escrita imediata em todos os níveis de cache e na MP
		- Quando uma variável muda de valor, todos os níveis subsequentes (que contêm uma cópia da variável) são atualizados ao mesmo tempo
	- Write back
		- Atualiza quando o bloco for substituído
		- Quando a variável muda de valor, é atualizada na L1. Quando o bloco que a contém for substituído, é disparado a atualização nos demais níveis
		- Faz o uso do dirty bit
	- Write once
		- Mistura das duas anteriores
		- Na primeira atualização (write through), da segunda em diante (write back)
	- **Protocolo MESI**
		- Usado em sistemas multiprocessados
		- **Provê coerência de cache**
		- Utiliza o Write back
		- Cada linha pode estar em 1 dos 4 estados previstos
			- Modificada (dity bit)
			- Exclusiva (existe somente na memória cache)
			- Shared
			- Inválida

## Esquema de inicialização (BOOT)

- **BIOS**
	- Faz a inicialização do sistema
	- Faz o POST
	- Procura o dispositivo de boot no CMOS (pequena área de memória volátil que armazena as configurações do SETUP)
	- BIOS → POST → CMOS (Busca pelo dispositivo de boot)
	- O Setup é uma aplicação a parte (não está dentro do BIOS), mas também está gravado na memória RAM

# Memória secundária

## Disco rígido - Formatação

- Lógica → Definida pelo sistema operacional, tamanho do cluster
- Física → Definida pelo fabricante. Trilhas, cilindros, setores

##  RAID 

- Pode ser por software ou hardware
- RAID-0 (Striping)
	- Aumento de capacidade
	- Dados divididos em blocos e escritos sequencialmente
	- Leitura simultânea em todos os dispositivos (melhor desempenho)
	- Os blocos são alternados 1 em cada HD
	- Se um disco falhar, todos os dados são perdidos
	- Pode-se ler e gravar simultaneamente
	- Não tem redundância
- RAID-1 (Mirror)
	- Espelhamento
	- Dados duplicados em dois discos diferentes
	- Redundância
	- O custo é o dobro do RAID-0
- RAID-4
	- Necessário pelo menos 3 discos (um é utilizado como paridade)
![[Untitled 535.png]]
- RAID-5
	- Evolução do RAID-4
	- Paridade distribuída entre os discos
![[Untitled 536.png]]
	- No mínimo 3 discos
- RAID 6
	- Paridade múltipla e distribuída
	- Pelo menos 4 discos
	- Suporta a perda de 2 discos
	- Melhor performance
- RAID-10 (1 + 0)
	- 1 → Espelhamento
	- 0 → Stripping
	- Na prática são duas unidades estendidas espelhadas entre si
- RAID-50 (5 + 0)
	- 5 → Paridade
	- 0 → Estendido

## Escalonamento de Requisições de Acesso ao Disco

[http://lasdpc.icmc.usp.br/~ssc640/grad/ec2015/scheduling_simulator/simulator.html](http://lasdpc.icmc.usp.br/~ssc640/grad/ec2015/scheduling_simulator/simulator.html)

- Considera
	- Posicionamento do braço para o cilndro correto
	- Rotação do setor correto sob o cabeçote
	- Tempo real de transferência do dado\
- Políticas
	- FCFS (First come, first served)
		- Escolhe sempre a primeira posição do vetor de requisições
		- Independente da posição
	- SSTF (Shortest Seek Time First)
		- Escolhe a requisição de dado que esteja fisicamente mais próximo da posição atual do braço
		- Em situações de muitas requisições prejudica o acesso às informações mais periféricas do disco
	- Elevador
		- Prioriza as requisições de dados que estejam localizados na mesma direção em que o braço já esteja se movimentando
		- Similar ao algoritmo de priorização de elevadores
		- Mais eficiente dos 3 algoritmos

# Gerenciamento de E/S

- Os dispositivos de E/S, também conhecidos por periféricos, comunicam-se com a unidade central de processamento (UCP) por meio de interfaces e controladores. 
- Esta comunicação pode ocorrer de várias formas diferentes, seja pela UCP perguntando diretamente ao dispositivo ou pelo uso de áreas compartilhadas de memória.

## Técnicas de Gerenciamento de E/S

### E/S Programada

- A UCP espera enquanto a controladora de disco executa operações de leitura sequencialmente.

### Interrupções

- Permite que a CPU continue o programa enquanto operações assíncronas são executadas
- Ao receber uma interrupção o que a CPU faz é salvar o seu estado atual incluindo o valor do registrador de programa (PC), o registrador de pilha (SP) e outros registradores relevantes, para que possa posteriormente retomar a programação principal de onde parou.
- Com o estado do programa salvo, a CPU determina o vetor de interrupção apropriado para a interrupção recebida.
- Esse vetor indica o endereço inicial da rotina de tratamento de interrupção (RTI) correspondente, que é um código específico armazenado na memória e responsável por lidar com a interrupção.
- A CPU então pula para o endereço indicado pelo vetor de interrupção e executa a RTI. 
- Essa rotina realiza as ações necessárias para responder à interrupção, como transferir dados para um dispositivo periférico, atualizar o status do sistema ou notificar um programa em execução.
- Ao finalizar a RTI, a UCP restaura o estado do programa que foi salvo anteriormente, permitindo que ele continue sua execução a partir do ponto de interrupção.
- A classificação dos diversos tipos é chamada por alguns autores de taxonomia de interrupções.
- Provoca a troca de contexto
	- Direciona o processador para rotinas específicas para o tratamento de cada tipo de interrupção
	- Os endereços destas rotinas são chamados **vetores de interrupção **e ficam gravados na RAM
- **Taxonomia de Interrupções**
	- **Quanto à origem**
		- **Interrupções de Hardware:** 
			- Originadas por dispositivos periféricos, como teclados, impressoras, discos rígidos e outros componentes externos. 
			- Essas interrupções geralmente indicam a conclusão de uma operação, a necessidade de transferência de dados ou a ocorrência de um erro.
		- **Interrupções de Software:** 
			- Geradas por instruções específicas do software em execução, como estouros de pilha, divisão por zero ou solicitações de acesso a recursos indisponíveis. 
			- Essas interrupções permitem que o sistema lide com exceções e erros de forma controlada.
	- **Quanto ao nível de prioridade**
		- **Interrupções mascaráveis: **
			- Permitem que a CPU as desative temporariamente, priorizando outras tarefas. 
			- Essa funcionalidade é útil para evitar que interrupções de baixa prioridade interfiram em operações críticas.
		- **Interrupções não mascaráveis (NMI):**
			- Não podem ser desativadas pela CPU e possuem a mais alta prioridade no sistema. 
			- São utilizadas para eventos críticos que exigem atenção imediata, como falhas de hardware graves ou violações de segurança.
	- **Quanto à funcionalidade**
		- **Interrupções de entrada: **
			- Indicam a disponibilidade de dados de entrada para a CPU, como pressionamentos de tecla ou dados recebidos de um dispositivo de rede.
		- **Interrupções de saída:** 
			- Notificam a CPU sobre a necessidade de enviar dados para um dispositivo periférico, como imprimir um documento ou gravar dados em um disco rígido.
		- **Interrupções de tempo: **
			- Geradas por um temporizador interno do sistema em intervalos regulares, permitindo que tarefas periódicas sejam executadas, como atualizações da interface gráfica ou gerenciamento de memória.
	- **Outras**
		- **Inter-processor Interrupt (IPI)**
		- **Spurious Interrupt**
			- Evento indesejável como ruído

### DMA

> [!tip] 💡
> Nesta abordagem, uma controladora especial permite que periféricos como HD ou SSD leiam e gravem dados diretamente na memória principal do computador, sem a necessidade de intermediação da UCP.

- Esta controladora tem acesso ao barramento principal do computador e atua como um auxiliar da UCP.

![[Untitled 537.png]]

- Inicialmente a UCP informa à controladora DMA o endereço inicial do bloco (Address) e a quantidade de bytes a serem lidos (Count). 
- A controladora DMA inicia então sua operação enviando uma solicitação de leitura para a controladora do HD. 
- A cada operação de leitura, a controladora do HD vai gravar a informação de saída diretamente na memória principal. 
- A controladora DMA então vai incrementar em 1 byte o endereço (Address) e decrementar a quantidade (Count) e repetir o processo. 
- Este ciclo irá se repetir até que a quantidade chegue a 0.
- Quando toda a informação solicitada for transferida para a memória principal, a controladora irá então gerar uma única interrupção para informar a UCP de que os dados estão disponíveis na memória principal.
- Note que desta forma, a UCP **não intermedia a transferência dos dados**, ela apenas é informada quando toda a operação está concluída e disponível para seu uso.
- **Controladoras DMA podem ainda operar de duas formas:**
	- **Modo de transferência simples:** A controladora DMA transmite um byte de cada vez, obtendo o controle do barramento e liberando em seguida.
	- **Modo de transferência por bloco:** A controladora DMA obtém o controle do barramento e devolve somente após um bloco de dados ter sido transferido.

## Técnicas auxiliares

### **Caching**

- Esta é uma técnica que envolve o armazenamento temporário de dados frequentemente acessados em uma área de memória mais rápida e de acesso mais próximo da CPU, conhecida como cache. 
- Quando a UCP precisa acessar dados da memória principal, ela primeiro verifica se esses dados estão presentes no cache. 
- Se os dados estiverem em cache (ou seja, se ocorrer um cache "hit"), a UCP pode acessá-los diretamente, o que é muito mais rápido do que acessar os dados na memória principal.
- Por outro lado, se os dados não estiverem em cache (cache "miss"), a CPU precisará acessar os dados na memória principal e, opcionalmente, trazê-los para o cache para acessos futuros. Isso adiciona um pequeno atraso na primeira operação.

### **Spooling**

- Esta é uma técnica geralmente utilizada com dispositivos muito lentos, como impressoras, por exemplo. 
- Esta abordagem envolve o armazenamento temporário de dados de entrada/saída em uma área de memória antes que eles sejam processados pelo dispositivo periférico.
- Por exemplo, ao enviar um documento para impressão, em vez de enviar diretamente os dados para a impressora, o sistema operacional primeiro os coloca em uma fila de spool (também conhecida como spool de impressão). 
- Essa fila de spool pode ser armazenada em disco ou em memória temporária. A impressora então acessa os dados da fila de spool em sua própria velocidade, permitindo que o sistema operacional continue a operar sem aguardar a conclusão da impressão.
- O spooling é útil porque permite que múltiplos trabalhos de impressão (ou outras operações de E/S) sejam processados em paralelo, sem exigir que o sistema espere que cada trabalho seja concluído antes de iniciar o próximo. Isso melhora a eficiência do sistema, especialmente em ambientes onde a impressão de documentos ou outras operações de E/S são frequentes.
- Podem ser de hardware ou software (traps)
- Eventos assíncronos
- Tipos:
	- Mascaráveis (IRQ)
		- Podem ser utilizadas para ratamento de interrupções de alta, média ou baixa prioridade a depender da configuração de política de priorização
		- Podem ser habilitadas ou desabilitadas pelo sistema operacional ou programador
	- Não mascaráveis (NMI)
		- Não podem ser ignorados ou desabilitados pelo sistema
		- O fluxo atual é interrompido para tratamento da interrupção
		- As instruções e estado do processador são salvos na pilha

# Mapas Mentais

![[CPU.png]]

![[Memria.png]]