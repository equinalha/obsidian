---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2026-07-22T17:34:00
Owner:
  - Eduardo Quinalha
---
[https://www.w3schools.com/dsa/dsa_intro.php](https://www.w3schools.com/dsa/dsa_intro.php)

# Algoritmos de Ordenação

![[Algoritmos e Estrutura de Dados synced block]]

# Estruturas de Dados

## List

- Estrutura linear, baseada em índice
- Aceita elementos repetidos
- Baixa performance para pesquisa
- Alta performance de inserção

## Set

- Não baseado em índice (não acessível por posição)
- Não aceita repetição
- Aceita operações como union, disjunction, etc…
- Pode ou não ser ordenado, depende da implementação
- Rápida consulta
- Baixo desempenho para inserção (aumenta com o tamanho do Set)

## Map

- chave - valor
- **A chave é única** (não pode repetir) mas o valor aceita repetições em chaves diferentes

## Árvore

- Estrutura não linear
- Um nó pode ter vários filhos (depende da implementação)
- Um nó, em regra, deveria ter somente 1 pai (novamente, depende da implementação)
- A raiz pode ou não ser considerada um nó (depende do autor)
	- Não tem pai
- Nós folhas (não tem filhos)

### **Conceitos**

- Nível
	- Relacionado aos nós
	- Distância a partir da raiz (nível 0)
- Grau
	- Relacionado ao nó
	- Quantidade de filhos que um nó tem
- Altura
	- Relacionado à árvore
	- Distância da raiz até a folha
	- Grau = Maior nível + 1
- Balanceada
	- A diferença de **níveis** entre a sub-árvore esquerda e direita não pode ser maior do que 1
- **Pré-Ordem**
	- Raiz → Esquerda → Direita
- **Ordem**
	- Se a árvore estiver ordenada, resulta na sequência em ordem crescente
	- Esquerda → Raiz → Direita
- **Pós-Ordem**
	- Esquerda → Direita → Raiz
- Árvore binária cheia
	- Todos os elementos têm 2 filhos, com exceção das folhas
![[Untitled 749.png]]
- Árvore binária completa
	- Com exceção do último nível, todos os elementos tem 0 ou 2 filhos
![[Untitled 750.png]]
- Estritamente binária
	- Todos os elementos têm 0 ou 2 filhos
![[Untitled 751.png]]

### Quantidade de nós

- Árvore binária cheia (todas as folhas completas)
	- N = 2^n - 1
	- Onde:
		- n = total de níveis
		- n = h + 1 (Sendo o primeiro nível (raíz) h=0)

### Balanceamento

- **O percurso em Ordem deve ficar inalterado em relação à árvore desbalanceada**
- Rotações
	- Esquerda Simples
		- Quando a sub-árvore mais à direita causar o desbalanceamento
		- O **filho à esquerda** da subárvore direita será **filho a direita do pai (da própria subárvore)**
		- **O pai vira filho à esquerda da subárvore**
![[Untitled 752.png]]
![[Untitled 753.png]]
	- Direita Simples
		- Quando a subárvore mais à esquerda causar o desbalanceamento
		- O filho a direita da subárvore esquerda será o filho a esquerda do pai
		- O pai será filho a direita da subárvore esquerda
![[Untitled 754.png]]
![[Untitled 755.png]]
	- Esquerda Dupla
		- Quando a subárvore esquerda da direita causar o desbalanceamento
		- Simples **direita** na **subárvore direita** + simples **esquerda** na árvore **original**
			- Obs: Mesmo que o filho seja null
![[Untitled 756.png|Desbalanceada]]
![[Untitled 757.png|Passo 1: Desmembra a subárvore direita]]
![[Untitled 758.png|Passo 2: Rotação à direita]]
![[Untitled 759.png|Passo 3: Junta na árvore original]]
![[Untitled 760.png|Passo 4: Rotação à esquerda]]
	- Direita Dupla
		- Quando a subárvore direita da subárvore esquerda causa o desbalanceamento
		- Esquerda simples na subárvore esquerda + direita simples na árvore original
![[Untitled 761.png|Desbalanceada]]
![[Untitled 762.png|Passo 1: Desmembra a esquerda]]
        Passo 2: Rotação à esquerda
        Passo 3: Junta na árvore original
        Passo 4: Rotação à direita
![[Untitled 763.png]]
![[Concursos/images/nse-6779031373762075482-1000064235.jpg]]
![[Concursos/images/nse-3696523304561482442-1000064242.jpg]]
    ## Remoção
    ESTRATÉGIA 1
PASSO 1: IDENTIFIQUE O ELEMENTO QUE VOCÊ DESEJA RETIRAR DA ÁRVORE (EM VERMELHO)
PASSO 2: IDENTIFIQUE O MENOR ELEMENTO DE TODA SUBÁRVORE À DIREITA DO NÓ IDENTIFICADO NO
PASSO 1 (EM VERDE)
PASSO 3: COPIE O VALOR DO NÓ IDENTIFICADO NO PASSO 2 PARA O NÓ IDENTIFICADO NO PASSO 1
PASSO 4: REMOVA O ELEMENTO IDENTIFICADO NO PASSO 2.
![[Untitled 764.png]]
    ESTRATÉGIA 2
PASSO 1: IDENTIFIQUE O ELEMENTO QUE VOCÊ DESEJA RETIRAR DA ÁRVORE (EM VERMELHO)
PASSO 2: IDENTIFIQUE O MAIOR ELEMENTO DE TODA SUBÁRVORE À ESQUERDA DO NÓ IDENTIFICADO NO
PASSO 1 (EM VERDE)
    PASSO 3: COPIE O VALOR DO NÓ IDENTIFICADO NO PASSO 2 PARA O NÓ IDENTIFICADO NO PASSO 1
PASSO 4: REMOVA O ELEMENTO IDENTIFICADO NO PASSO 2.
![[Untitled 765.png]]

## Outros Tipos de Árvores

### Árvores B

- Semelhante às árvores rubro-negra
- Utilizada principalmente para minimizar tempo de operações de E/S em dispositivos de armazenamento secundário
- A árvore normalmente é mantida na memória principal e seus nós contêm uma quantidade de blocos da memória secundária
- A altura da árvore é O(log n) onde n é o número de nós da árvore
- Características
	- Cada nó armazena um **conjunto de chaves e registros** e é chamado de **página**
	- **Chaves e Registros são armazenados em todos os nós (páginas) da árvore**
	- Cada página pode ter um número diferente de chaves, maior que 1
	- Cada **chave** referencia duas **páginas** filhas, onde a página da esquerda contém chaves menores e a da direita chaves maiores
	- Logo, uma **página** com k **chaves** terá k+1 **páginas** **filhas**
![[Untitled 766.png]]
	- Complexidades (Pior caso)
		- Inserção O(log n)
		- Busca O(log n)
		- Remoção O(log n)
		- Espaço O(n)

### Árvores B+

- Utilizado no NTFS, ReiserFS e XFS
- Permite o acesso sequencial de chaves mesmo por páginas diferentes
- Características
	- **As chaves são armazenadas em todos os nós da árvore**
	- **Os registros são armazenados apenas nas folhas**
	- Cada página folha contém uma referência para a sua sucessora, mesmo não havendo relação de parentesco (lista duplamente encadeada)
	- Isto permite que o acesso em sequência ocorra naturalmente, uma vez que, ao procurar pela chave k+1, pode-se ir para a próxima chave na mesma página ou pular para a página ao lado
	- Na árvore B, seria necessário reiniciar a busca a partir da raiz

![[Untitled 767.png]]

### AVL

- Árvore binária de busca auto-balanceada
- A diferença nas alturas das subárvores esquerda e direita não pode ser maior do que 1
- O fator de balanceamento de cada nó é sempre 0, 1 ou -1.
	- Diferença entre as alturas de suas subárvores esquerda e direita. 

### Árvore Rubro-Negra

- Tipo de árvore binária de busca **balanceada**
- Os nós folha são irrelevantes e não contém dados (null)
- Cada nó tem um atributo de cor: vermelho ou preto
- A raiz é preta
- Todas as folhas (null) são pretas
- Os filhos de um nó vermelho são pretos
- Todo caminho de um dado nó para qualquer um de seus nós folhas, tem o mesmo número de nós pretos
- Complexidades (Pior caso)
	- Inserção O(log n)
	- Busca O(log n)
	- Remoção O(log n)
	- Espaço O(n)

# Grafos

[https://www.dcc.fc.up.pt/~pribeiro/aulas/pc2021/material/grafos_intro.pdf](https://www.dcc.fc.up.pt/~pribeiro/aulas/pc2021/material/grafos_intro.pdf)

## Matriz de adjacência

- Representação por matrizes
- Cada coluna representa um nó
- As linhas representam os mesmos nós
- Um valor da matriz Aij significa que há um arco ligando os nós i e j
- Se os arcos tiverem um peso associado, o valor representado na matriz será o peso do arco, caso contrário, será 1
- Se o grafo for direcional (cada arco tem um sentido definido) a matriz não será simétrica
- Valores representados na diagonal da matriz significam um laço (um arco que liga ao próprio nó)

![[image 127.png]]

- Ocupa espaços de memória desnecessários, porém é mais fácil de entender e mais rápida de ser consultada

## Lista de adjacência

- Economiza espaço de memória, especialmente para grafos muito grandes
- Cada nó possui uma lista com os demais nós conectados a ele
- Pode também representar os pesos

<!-- Column 1 -->
![[image 128.png]]

<!-- Column 2 -->
![[image 129.png]]

## Travessia

- Iniciando em um vértice, visitar todos os outros vértices possíveis
- Os dois algoritmos principais são
	- Depth First Search (DFS)
		- Normalmente implementando utilizando pilha ou recursão
		- Call Stack
	- Breadth First Search (BFS)
		- Normalmente implementado utilizando fila

## Shortest Path

![[image 130.png]]

- Os dois principais algoritmos são:
	- Dijkstra’s
	- Bellman-Ford

# Hashing - Tabelas de dispersão

- Tipo de estrutura Chave x valor
- Aplica-se uma função de hash que, quando aplicada ao valor que se deseja armazenar, vai gerar o valor da chave
- **Podem acontecer colisões**
- Tratamento de colisões:
	- Endereçamento Aberto (**Sondagem Linear)**
		- No caso de colisão, pode adotar alguma das seguintes ações
			- Percorrer linearmente até a próxima posição vazia
			- Incremento exponencial do índice
			- Encadeamento de funções de dispersão
	- Encadeamento
		- O registro em colisão vai apontar para uma estrutura de dados auxiliar que pode ser lista encadeada ou uma árvore, por exemplo
		- Aumenta a complexidade
		- Diminui o desempenho
- A principal vantagem das tabelas hash é sua capacidade de realizar inserções, deleções e buscas de maneira muito **eficiente**, geralmente em tempo **O(1)** no melhor caso.

# Bitmap

- Usados em bancos de dados, especialmente em sistemas de **data warehousing** e em consultas que envolvem grandes volumes de dados.
- Eficientes para consultas de baixa cardinalidade
- armazena **um vetor de bits** (bitmap) para cada valor distinto de uma coluna
- Exemplo simples:
Suponha que temos uma coluna "Gênero" em uma tabela com três valores possíveis: **Masculino**, **Feminino** e **Outro**. Para cada valor, um bitmap é criado:

| Gênero | Masculino | Feminino | Outro |
| --- | --- | --- | --- |
| Registro 1 | 1 | 0 | 0 |
| Registro 2 | 0 | 1 | 0 |
| Registro 3 | 1 | 0 | 0 |
| Registro 4 | 0 | 0 | 1 |

Nesse exemplo, cada coluna (Masculino, Feminino, Outro) tem um **bitmap**, e um **bit** é usado para indicar se o valor da coluna corresponde à linha específica da tabela. O vetor de bits é altamente compacto e eficiente para operações que envolvem grandes conjuntos de dados.

### Utilização de Índices Bitmap

Índices bitmap são utilizados principalmente em cenários onde:

1. **Consultas OLAP**: São muito eficientes em consultas que envolvem **operações de leitura intensiva** em **data warehouses**, onde se realiza a análise de grandes volumes de dados históricos.
2. **Colunas de baixa cardinalidade**: São mais eficazes em colunas com poucos valores distintos, como "Gênero", "Status", "Categoria", etc., onde o número de bits necessários para representar todos os valores distintos é pequeno.
3. **Consultas complexas**: São ideais para consultas complexas que envolvem múltiplas condições em colunas diferentes. Isso ocorre porque as operações lógicas (AND, OR, NOT) podem ser aplicadas diretamente nos bitmaps de forma eficiente.

# Programação Dinâmica

- Resolve problemas complexos ao quebrá-los em subproblemas menores e mais simples.
- **Armazena os resultados** de subproblemas já resolvidos em uma tabela (ou matriz), de modo a **evitar recomputações desnecessárias**.
- Isso frequentemente reduz a complexidade exponencial para **complexidade polinomial**

### Exemplos Clássicos:

4. **Fibonacci**: O cálculo dos números de Fibonacci é um exemplo clássico, onde a abordagem ingênua de recursão simples tem complexidade exponencial, enquanto a programação dinâmica pode resolver em tempo linear armazenando resultados intermediários.
5. **Problema da Mochila (Knapsack Problem)**: Determinar a combinação de itens para maximizar o valor total sem exceder a capacidade da mochila pode ser resolvido eficientemente com programação dinâmica.
6. **Caminho Mínimo (Shortest Path)**: Algoritmos como o de Floyd-Warshall utilizam programação dinâmica para encontrar o caminho mais curto entre todos os pares de vértices em um grafo ponderado.

# Método Ganancioso (Greedy method)

- Faz a escolha localmente ótima em cada etapa com a esperança de encontrar a solução globalmente ótima
- Não armazena resultados de subproblemas
