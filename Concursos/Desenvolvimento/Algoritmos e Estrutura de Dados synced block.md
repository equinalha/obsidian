---

---
## Classificação

- Estabilidade
> [!note] 🔥
> Algoritmos **estáveis** **mantém a ordem relativa entre dois elementos idênticos**

	- **Estáveis**
		- Bubble
		- Insertion
		- Merge
	- **Instáveis**
		- Selection
		- Quick
		- Heap
		- Shell

| **Algoritmo** | **Características** | **Estável** | **Pior caso** | **Caso médio** | **Melhor caso** |
| --- | --- | --- | --- | --- | --- |
| **Bubble*** | Comparação de elementos **adjacentes** | **Sim** | **O(n2)** | **O(n2)** | **O(n)** |
| **Selection** | Seleciona o menor valor, joga na primeira posição. | **Não** | **O(n2)** | **O(n2)** | **O(n2)** |
| **Insertion** | Ordenação à esquerda, jogadores de carta | **Sim** | **O(n2)** | **O(n2)** | **O(n)** |
| **Quick*** | Divisão com uso de pivô, paralelismo, recursividade | **Não** | **O(n2)** | **O(nLogN)** | **O(nLogN)** |
| **Merge** | Divisão sem pivô, paralelismo, merge de arrays, recursividade | **Sim** | **O(nLogN)** | **O(nLogN)** | **O(nLogN)** |
| **Shell** | Gap. Otimização do **insertion** | **Não** | **O(n2)** | **O(n)**** | **O(nLogN)** |
| **Heap** | Uso de estrutura paralela (heap) normalmente árvore | **Não** | **O(nLogN)** | **O(nLogN)** | **O(nLogN)** |

- mais pedidos em prova

** Depende do tamanho do gap

*** A CESPE considera que apenas o Bubble e o Quick são algoritmos de troca

> [!note] 🔥
> Como construir a tabela na prova:

Coluna 1- **BSIQMSH (BSI que Mexe)** - nome dos algoritmos
Coluna 2- A estabilidade é boa? Não, é **BIM
**Coluna 3 - Pior caso → Tudo n2. Só Merge e Heap que são nLogN → **Pior é MH** (logN)
Coluna 4 - Caso médio → Só muda Quick e Shell → **No meio entra Quick Shell**
Coluna 5 - Melhor caso → n2n (o resto é nLogN) → **N2N**

Resumindo:
1- **BSI que mexe**
2- **Estabilidade BIM**
3- **Pior é MH**
4- **No meio entra o Quick Shell**
5- **N2N**

## Bubble Sort

> [!note] 🔥
> Palavras / Expressões chave: **Comparação de elementos adjacentes, ****troca**

- Compara o elemento da posição x com a posição x+1
- Programação simples
- Funciona bem para arrays pequenos
- Percorre o array várias vezes
- Pouco eficiente, mesmo com array já ordenado
- **Complexidade**
	- Pior caso: **O(n2)**
	- Caso médio:** O(n2)**
	- Melhor caso: **O(n)**

## Selection Sort

> [!note] 🔥
> **Selection** → **Seleciona** o menor valor a cada varrida e coloca na posição mais a esquerda

- Faz a busca pelo menor elemento, em seguida o segundo menor elemento, etc…
- Percorre todo o array uma primeira vez, **seleciona o menor valor** e coloca na primeira posição
- Percorre novamente, **buscando pelo segundo menor** valor e coloca na segunda posição
	- Na primeira iteração, o algoritmo faz n-1 comparações, pois compara o segundo elemento com o primeiro elemento, o terceiro elemento com o primeiro elemento, e assim por diante.
	- Na segunda iteração, o algoritmo faz n-2 comparações, pois compara o terceiro elemento com o segundo elemento, o quarto elemento com o segundo elemento, e assim por diante.
	- Na última iteração, o algoritmo faz 1 comparação.
> [!note] 🔥
> Número de comparações = (n-1) + (n-2) + ... + 1
> = n(n-1)/2
> 
> = (n^2-n)/2
- Simplicidade
- Usa pouca memória
- Complexidade igual em todos os casos
- Pior performance
- **Complexidade**
	- Em todos os casos: O(n2)

## Insertion Sort

> [!note] 🔥
> **Insertion** → Divide o array em duas partes: A esquerda fica a parte ordenada, a direita a parte não ordenada

- Ao invés de buscar pelo menor elemento, em seguida o segundo menor, tal qual o selection, ele caminha elemento por elemento e o compara com os elementos da parte ordenada do vetor, inserindo-o já na posição correta.
- **Método preferido dos jogadores de carta**
	- A primeira posição é considerada ordenada
	- Começa a partir da segunda posição
	- Compara a posição atual com os elementos ordenados à esquerda
	- Se o elemento atual for menor que algum elemento anterior:
		- Desloca todos os elementos maiores para a direita
		- Insere o elemento atual na posição desocupada
- Simples e eficiente
- Se o array estiver parcialmente ordenado, a complexidade cai bastante
- Alto número de operações
- **Complexidade**
	- Pior caso: **O(n2)**
	- Caso médio:** O(n2)**
	- Melhor caso: **O(n)**

## Quick Sort

> [!note] 🔥
> **Quick****  → Dividir para conquistar. **Utiliza **pivô.****
**Outras palavras chave: **Recursividade, paralelismo**

- Como divide o array, pode usufruir dos benefícios de paralelismo para organizar dois arrays
- Em resumo:
	- Escolhe um pivô
	- Todos os elementos do array menores que o pivô vão para o lado esquerdo, todos os maiores vão para o lado direito
	- Escolhe outro pivô
- Funciona em duas etapas:
	- Partição
		- Escolha do pivô
		- Reorganize o array em duas subpartições:
- Uma subpartição contendo elementos **menores** que o pivô.
- Outra subpartição contendo elementos **maiores** que o pivô.
- Durante o particionamento, elementos iguais ao pivô podem ser colocados em uma subpartição separada (opcional).
	- Aplique recursivamente o Quick Sort nas duas subpartições (elementos menores e maiores que o pivô).
- Possibilita o paralelismo
- Muito eficiente
- Usa muita memória (muitas chamadas recursivas)
- **Complexidade**
	- Pior caso: O(n2)
	- Caso médio: O(nlogN)
	- Melhor caso: O(nLogN)

## Merge Sort

> [!note] 🔥
> Também trabalha com divisão, porém sem o elemento pivô

- Divide em sub-arrays para depois juntá-los (merge)
- Melhor que o quick no pior caso
- Pode ser paralelizado
- Relativamente simples e eficiente
- Consome muita memória (recursividade)
- **Complexidade**
	- Em todos os casos: O(nLogN)

## Shell Sort

> [!note] 🔥
> **Gap → Comparação de elementos distantes
Otimização do insertion**

- Otimização do insertion sort
- Compara elementos que não são adjacentes
- Começa executando exatamente igual ao insertion, mas com um gap entre os elementos.
- A medida que varre o vetor, o gap vai diminuindo
- Desempenho pode depender do gap
- Melhor desempenho dentre os algoritmos de complexidade O(n2)
- Não permite paralelismo
- **Complexidade**
	- Pior caso: O(n2)
	- Caso médio: O(n)
	- Melhor caso: O(nlogN)

## Heap Sort

> [!note] 🔥
> **Utiliza uma estrutura paralela (heap) - de suporte - (árvore)**

- Algoritmo generalista (inserção, seleção)
- Muito performático
- Alto processamento
- **Complexidade**
	- Todos os casos: O(nLogN)