---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2026-07-24T12:42:00
Owner:
  - Eduardo Quinalha
---
# Gerenciamento de memória

## Hierarquia de memória

- **Cache hit:**** **Quando o dado de que o processdor precisa encontra-se na memória cache
- **Cache miss:** Quando o dado não encontra-se na memória cache e o processador precisa buscá-lo na memória principal

## Gerenciador de memória

- Fica no kernel
- Monitora as partes da memória que estão** em uso ou não**
- Alocar e libera memória para os processos
- Swapping

## Swapping x Memória Virtual

- Swapping
	- Transfere o processo da memória para o disco para dar lugar a outro
	- Processo contrário no retorno à execução
- Memória Virtual
	- Permite a execução de programas maiores que a própria RAM
	- Divide em partes (overlay)
	- Os programas podem ser executados mesmo estando parcialmente na memória principal
	- **Em sistemas com memória virtual, os endereços de memória não vão diretamente para o barramento, mas sim para o MMU**

> [!note] 🔥
> **Segmentação e Paginação são formas de se implementar memória virtual**

## Overlay

- Técnica que exige que o programador se preocupe em dividir o código de forma que os módulos possam ser trazidos para a memória de forma independente
- Trabalhoso

## Mapas de Bits

- Memória dividida em unidades de alocação (tamanho fixo);
- Uma área da memória é reservada para o mapa de bits, onde cada bit representa uma unidade de alocação
- 0 → unidade livre, 1 → unidade ocupada
- É possível o uso de listas encadeadas para implementação do mapa de bits

## Paginação

- Espaço de endereçamento virtual
- O programa é dividido em unidades de tamanhos fixos: **páginas**
- A memória física é dividida em unidades capazes de alocar uma página: **Quadros (frames)**
- **Algoritmos de substituição de páginas**
	- Ótimo
		- Teórico
		- Adivinha quando uma página será referenciada e retira da memória principal a página que está mais longe de ser utilizada
	- NRU
		- Retira a página que não foi utilizada recentemente
	- FIFO
		- First In, First Out
		- Retira a página mais antiga para dar lugar a uma nova
	- Segunda Chance:
		- Tipo especial de FIFO, porém não retira uma página que esteja sendo muito utilizado
	- Algoritmo do Relógio
		- Outra variação do FIFO
	- LRU (Least Recently Used)
- **Falta de página**
	- Um programa tenta acessar uma página que não está mais na memória principal
	- Uma interrupção é disparada e a página é buscada na memória virtual
	- **É resposabilidade do Hardware (MMU) detectar uma falta de página Page Fault**
	- Uma Page Fault gera uma interrupção de CPU → **Page Interrupt**
	- O processo que sofre uma falta de página é colocado em espera até que a página seja carregada da memória virtual para a memória principal
	- Tal falta dispara o procedimento de substituição de páginas que vai copiá-la para a memória principal, atualizar a tabela de páginas e repetir a instrução que gerou a falta
	- A página que foi transferida para a memória principal não é deletada do disco. Caso ela tenha sido alterada na memória principal, é necessário o disparo de uma função de atualização de página, normalmente sinalizado com um Dirt Bit, e executado pela MMU
- **Tabela de Páginas**
	- Guarda informações sobre o espaço de endereçamento e todas as páginas presentes
	- Sinaliza, através de um bit de preseça/ausência, se a página encontra-se carregada na memória
	- Também sinaliza, através o bit “modificado” se a página foi alterada e por consequência, deve ser reescrita no disco (dirty bit)
	- O bit referenced, ajuda no processo de substituição de páginas
![[Untitled 500.png]]
	- **Tipos de tabelas de páginas para grandes espaços de memória virtual**
		- Tabelas de páginas multi-nível
			- Não mantém toda a tabela na memória o tempo todo
			- Uma página de primeiro nível faz referência para outras, que podem ou não estar na memória
			- Caso estejam no disco, são buscadas, da mesma forma que uma página comum, e daí sim, obtido a informação sobre a página desejada.
![[Untitled 501.png]]
		- Tabelas de páginas invertida
			- Neste modelo, ao invés de se ter uma tabela que guarda uma entrada por página do espaço de endereçamento virtual, tem-se uma entrada por frame da memória real.
			- Demandam mais processamento para localizar a página referenciada
- **Memory leak**
	- Excesso de memória alocada e não liberada ao final do código
- Fragmentação
	- Ocorre em decorrência de espaços vazios deixado no último frame de um programa.
- ==**A Paginação é Transparente para o programador**==

## Segmentação

- Alternativa à paginação
- Diferente da paginação, o tamanho dos segmentos é variável
- Divide a memória em segmentos específicos para cada tipo de estrutura de dados
- Resolve o problema de que espaços de memória possam crescer dinâmicamente para estruturas como vetores e pilhas
- Cada segmento consiste em um espaço linear de endereçamentos
- Torna a organização da memória bidimensional
- Tal como a paginação, faz-se necessário o uso de um algoritmo de substituição de segmentos
- Como os segmentos têm tamanhos variados, surge o problema da fragmentação externa (espaços vazios entre segmentos diferentes)
	- Compactação – Aproxima os diversos segmentos uns dos outros, deixando o espaço vazio para o final
- **Algoritmos de Alocação**
	- **First Fit**
		- Percorre a lista, a partir do incício da lista, até encontrar uma lacuna de tamanho suficiente para o processo a ser carregado
		- Se o tamanho da lacuna for maior que o processo, esta é dividida em 2 segmentos, um do tamanho do processo e outra que ficará disponível
		- Este algoritmo é rápido, uma vez que a busca termina assim que o espaço for encontrado
	- **Next Fit**
		- Igual ao First Fit, porém percorre a lista até encontrar e memoriza a posição
		- Na próxima ocorrência, continua a pesquisa de onde parou
		- O desempenho é pior do que o First Fit
	- **Best Fit**
		- Pesquisa a lista inteira e encontra a posição mais ajustada que caiba o processo
		- Costuma deixar muitos fragmentos pequenos que acabam não podendo ser utilizados por outros processos, ou seja, aumenta o problema de fragmentação
	- **Worst Fit**
		- Pega a maior lacuna
		- Como deixa fragmentos maiores, acaba disponibilizando mais memória para utilização posterior
	- **Quick Fit**
		- Mantém listas separadas de tamanhos mais comuns
		- Exemplo:
			- Uma lista de espaços de 32k
			- Outra lista somente com espaços de 16k
- **Algoritmos de Substituição de páginas**
	- NRU (Not Recently Used)
		- Cada página possui um conjunto de 2 bits: R → Referência e M → modificada
		- O Algoritmo NRU classifica as páginas em 4 categorias, de acordo com estes bits
		- O bit R é zerado a cada interrupção do relógio. O bit M não pode ser modificado pois é utilzado no sincronismo com o disco
		- Quando houver uma falta de página, uma página cujos bits R e M sejam 0 será escolhida para ser transferida ao disco, liberando espaço
	- LRU (Least Recently Used)
		- Mantém uma lista encadeada na memória com todas as páginas, ordenadas de forma que a mais recentemente usada estaja no início e a menos utilizada no fim
		- Tem um custo computacional alto
	- FIFO
	- Segunda Chance
		- Variação do FIFO que avalia o bit R.
		- Se o bit R for 1, ele é zerado e a página volta ao fim da fila para uma segunda chance
		- Ao chegar no início novamente, sendo o bit R ainda 0, será removida
	- Relógio
		- Lista ordenada circular
		- O ponteiro aponta para a página mais antiga
		- Se o bit R for 0, esta será removida quando da ocorrência de falta de página
		- Caso o bit seja 1, ele é zerado e o ponteiro vai para a próxima posição
- ==**A segmentação não é transparente para o programador**==

## Fragmentação Interna

- Ocorre em sistemas que utilizam a paginação
- Decorrência de espaços vazios deixados no último frame de cada programa, uma vez que quase 100% das vezes um programa não utilizará um número inteiro de páginas

## Fragmentação Externa

- Ocorre em sistemas que utilizam segmentação
- Como os segmentos tem tamanhos variados, surgem espaços vazios entre segmentos

## Memory Leak

- Blocos de memória que foram ateriormente alocados, porém não estão mais sendo referenciadas por nenhum objeto
- Estes blocos ficam indisponíveis tanto para o programa quanto para outros processos

## Translation Lookaside Buffer (TLB)

- Solução para acelerar o processo de pesquisa na tabela de páginas, uma vez que, se a cada acesso a memória fosse necessário um acesso à tabela, o desempenho seria reduzido pela metade
- Parte do princípio (comprovado) de que estatísticamente um programa em execução tende a centralizar o acesso à tabela em uma pequena porção da mesma
- Trata-se de um hardware (buffer) localizado dentro da MMU
- Possui um pequeno número de entradas (de 8 a 256)
- A pesquisa dentro do TLB é feita de forma paralela, simultânea, graças a um dispositivo de hardware também presente na MMU
- Como funciona:
	- Como o tempo de acesso ao TLB é muito pequeno, ao buscar uma página, sua localização na memória física será quase imediata, então o tempo de acesso será basicamente 1x o tempo de acesso à memória principal
	- Para as páginas que não estejam referenciadas no TLB, a CPU precisará fazer 2 acessos à MP, um para buscar a informação na tabela de páginas, e outro para acessar o endereço físico de onde a página esteja.
	- Imaginando que 75% das páginas acessadas por um processo estejam no TLB, o tempo de acesso à MP seja 200 ns, a média de tempo de acesso será:
		- 75% * 200 ns + 25% * 200 ns = 250 ns

[http://www.ic.uff.br/~boeres/slidesSOI/SOSI-aula5-memoriavirtual-completo.pdf](http://www.ic.uff.br/~boeres/slidesSOI/SOSI-aula5-memoriavirtual-completo.pdf)

# Modos de endereçamento

- **direto** - **Acesso direto à memória**. O valor atribuído ao registrador será o conteúdo daquele endereço. Ex: `mov R1, 1122h`
- **indireto** - O registrador atribuído ao operando contém o endereço de onde está o dado. Ex: `LOAD R1, (R2)`
- **imediato** - Atribuição do valor imediatamente, no operando. Ex: `mov R1, #2468h`
- **por registrador** - O registrador especificado contém o valor. Ex: `ADD R1, R2`
- **por deslocamento** - O endereço efetivo é obtido somando-se um endereço base com um deslocamento. Usado em array. Ex: `LOAD R1, (R3+8)`
