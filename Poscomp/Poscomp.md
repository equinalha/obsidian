---

---
# Álgebra Linar

## Autovalores e Autovetores

$Az=\lambda v$

- Encontrando os autovalores:
	$det(A - \lambda I) = 0$
💡 Em matrizes triangulares (com zeros acima ou abaixo da diagonal), os autovalores são simplesmente os próprios números da diagonal principal.
- Encontrando autovetores:
	$(A - \lambda I)v = 0$
💡Use os autovalores encontrados com a primeira equação. O vetor é uma matriz no formato $\begin{bmatrix} x \\ y \end{bmatrix}$

## Projeção ortogonal

- Projeção de v sobre w:
	$proj_wv = (\dfrac{v.w}{w.w})w$
	⚠️ **Atenção:** Se o produto interno (v.w) der 0, os vetores já são perpendiculares e a projeção será nula (0,0)

- Processo de Gram-Schmidt
Algoritmo que transforma vetores genéricos em uma **base ortogonal** (onde todos formam 90 graus entre si), removendo iterativamente as projeções (sombras).

**Vetor 1 (Mantém intacto):**
    $u_1 = v_1$
    **Vetor 2 (Subtrai a projeção):**
    $u_2=v_2-proj_{u1}v_2$

## Extremos Condicionados (Multiplicadores de Lagrange)

- **Conceito Base:** Método para encontrar o ponto de **máximo ou mínimo** (extremo) de uma função objetivo (ex: Lucro) quando você está "preso" a uma **restrição** (ex: Orçamento).
- **A Ideia Geométrica:** No ponto de máximo ou mínimo permitido pela restrição, a curva da função e a curva da restrição se tangenciam.
- **O Vetor Gradiente **$\nabla$**:** A bússola matemática. O gradiente de uma função sempre aponta para a direção de crescimento mais rápido e é perpendicular às suas curvas de nível.
- **A Equação Fundamental de Lagrange:**
Como as curvas se tangenciam no ponto ótimo, seus vetores gradientes ficam perfeitamente **alinhados (paralelos)**. Um vetor é apenas múltiplo do outro.

$$
\nabla f(x,y) = \lambda \nabla g(x,y)
$$

*Onde:*

- f(x,y): A função que você quer maximizar/minimizar (ex: Lucro).
- g(x,y) = 0: A sua restrição (ex: Orçamento fixo).
- $\lambda$: O *Multiplicador de Lagrange* (o fator de escala entre os vetores).
- **Como Resolver (O Sistema):**
Você monta e resolve um sistema de equações usando a equação do gradiente e a restrição original:
1. $\nabla f=\lambda \nabla g$  *(Gera derivadas parciais em relação a x e y)*
2. $g(x,y) = 0$ *(A restrição original garante que você não estoure o orçamento)*

<!-- Column 1 -->
![[Poscomp/images/image.png]]


<!-- Column 2 -->
![[Poscomp/images/image 1.png]]

> [!note] ### Exemplo
> Imagine que você tem uma folha de papelão que mede $12 \text{ cm}^2$. Você quer construir uma caixa (sem tampa) com o maior volume possível usando exatamente essa quantidade de material.
> Quais devem ser as dimensões da caixa?
> 
> **A Função Objetivo (f):**
> 
> O que queremos maximizar? O Volume.
> O volume de uma caixa com largura x, comprimento y e altura z é:
> 
> $$
> f(x,y,z)=x.y.z
> $$
> 
> **A Restrição (g):**
> 
> O que nos limita? A área do material (12).
> A área da caixa sem tampa é a área do fundo $(x.y)$ mais as áreas das quatro paredes laterais $(2xz+2yz)$. O total deve ser 12: 
> 
> $$
> xy+2xz+2yz=12
> $$
> 
> $$
> g(x,y,z) = xy + 2xz + 2yz - 12 = 0
> $$
> 
> O gradiente é simplesmente o vetor formado pelas derivadas parciais (derivar em relação a uma variável enquanto trata as outras como números fixos).
> • **Derivadas de **$f(x,y,z) = x.y.z$**:**
>     ◦ Em relação a $x: f_x = yz$
>     ◦ Em relação a $y: f_y = xz$
>     ◦ Em relação a $z: f_z = xy$
> 
> $$
> \nabla f = (yz, xz, xy)
> $$
> 
> • **Derivadas de **$g(x,y,z) = xy + 2xz + 2yz - 12$**:**
>     ◦ Em relação a $x: g_x = y + 2z$
>     ◦ Em relação a $y: g_y = x + 2z$
>     ◦ Em relação a $z: g_z = 2x + 2y$
> 
> $$
> \nabla g = (y + 2z, x + 2z, 2x + 2y)
> $$
> 
> A equação fundamental de Lagrange nos diz que no volume máximo:
> 
> $$
> \nabla f = \lambda \nabla g
> $$
> 
> Igualando cada coordenada dos vetores que calculamos acima, obtemos três equações, mais a restrição original como a quarta:
> 1. $yz = \lambda(y + 2z)$
> 2. $xz = \lambda(x + 2z)$
> 3. $xy = \lambda(2x + 2y)$
> 4. $xy + 2xz + 2yz = 12$
> 
> A estratégia comum aqui é isolar o $\lambda$ ou usar simetria para relacionar as variáveis x, y e z.
> 
> Multiplique a equação 1 por x, a equação 2 por y e a equação 3 por z:
> 1. $xyz = \lambda x(y + 2z) = \lambda(xy + 2xz)$
> 2. $xyz = \lambda y(x + 2z) = \lambda(xy + 2yz)$
> 3. $xyz = \lambda z(2x + 2y) = \lambda(2xz + 2yz)$
> 
> Perceba que todos os lados esquerdos agora são iguais $(xyz)$. Logo, os lados direitos também devem ser iguais:
> 
> Comparando (1) e (2): 
> 
> $$
> \lambda(xy + 2xz) = \lambda(xy + 2yz)
> $$
> 
> Como $\lambda \neq 0$ (senão o volume seria zero), podemos cancelar o $\lambda$ e o $xy$ de ambos os lados: 
> 
> $$
> 2xz = 2yz \implies \mathbf{x = y}
> $$
> 
> *(Isso faz sentido: a base da caixa ideal deve ser quadrada para maximizar a área com o menor perímetro).*
> 
> Comparando (2) e (3), e já sabendo que $x = y$:
> 
> $$
> \lambda(y^2 + 2yz) = \lambda(2yz + 2yz)
> $$
> 
> $$
> y^2 + 2yz = 4yz
> $$
> 
> $$
> y^2 = 2yz
> $$
> 
> Como a medida não pode ser zero, cancelamos um y:
> 
> $$
> \mathbf{y = 2z}
> $$
> 
> Portanto, sabemos que $x = y = 2z$.
> 
> **Finalizando na restrição:**
> Agora substituímos x e y por 2z na equação (4):
> 
> $$
> xy + 2xz + 2yz = 12
> $$
> 
> $$
> (2z)(2z) + 2(2z)z + 2(2z)z = 12
> $$
> 
> $$
> 4z^2 + 4z^2 + 4z^2 = 12
> $$
> 
> $$
> 12z^2 = 12
> $$
> 
> $$
> z^2 = 1 \implies \mathbf{z = 1}
> $$
> 
> *(ignoramos o -1 porque não existe medida negativa).*
> Como sabemos que $x = 2z$ e $y = 2z$:
> • $x = 2$
> • $y = 2$
> • $z = 1$
> **A resposta:** Para obter o maior volume possível (4 cm³) gastando apenas 12 cm² de papelão, a caixa deve ter **2cm de largura, 2cm de comprimento e 1cm de altura**.

## Regra dos Trapézios

Método numérico para aproximar o valor de uma integral definida (área debaixo da curva). Em vez de tentar calcular a área exata, dividimos o espaço em formas geométricas simples (trapézios) e somamos as áreas deles.

### Passos

1. Definir o tamanho do passo $(\Delta x)$
Dividir o tamanho do intervalo pelo número de subintervalos $(n)$:
$$
\Delta x = \dfrac{b-a}{n}
$$
2. Identificar os pontos $(x_i)$
Começando em $a=0$ e dando passos de tamanho $\Delta x$
3. Calcular $f(x_i)$ para todos os pontos encontrados
4. Aplicar a fórmula da regra dos trapézios
As pontas (extremos) são multiplicadas por 1 e os pontos centrais multiplicados por 2. Exemplo:

$$
T=\frac{\Delta x}{2}.[f(x+0)+2f(x_1)+f(x_2)]
$$

## Baricentro de um triângulo

- Ponto de intersecção das três medianas: 
	- Segmento de reta que tem início em um vértice de um triângulo e termina no ponto médio do lado oposto
	- Para constar, mediatrizes são as retas perpendiculares que passam pelos pontos médio das laterais
- Pode ser calculado pela **média aritmética** das coordenadas dos três vértices

# Análise Combinatória

## **1. Permutação P**

$P_n=n!$

- Quando todos os elementos são utilizados
- Anagramas
- Caso existam elementos repetidos, adiciona-se o número de repetições no denominador. Exemplo: (ARARA)
	$P_n^{a,b} = \dfrac{n!}{a!b!} => P_5^{2,3} = \dfrac{5!}{2!3!}$

## 2. Arranjo A

$A_{n,p} = \dfrac{n!}{(n-p)!}$

🗣️ **Macete:** A ordem importa? **A**ham! → **A**rranjo.

## 3. Combinação C

$C_{n,p}=\dfrac{n!}{p!(n-p)!}$

💡**Método dos Espaços:**

Sempre que a questão disser *"elementos da mesma cor/tipo não podem ficar juntos"*, alinhe os outros elementos primeiro. Conte os espaços nas pontas e entre eles. Depois, faça uma **Combinação **do número de espaços pelo número de elementos que você precisa encaixar. 

Funciona para servidores, carros no estacionamento, pessoas em filas, etc!

# Lógica


# Técnicas de Detecção e Correção de erro

- **Paridade**
	- Utiliza um bit de controle
	- Possibilita apenas detectar o erro. Sem possibilidade de correção
	- Não consegue detectar em qual bit o erro ocorreu
	- Se um número par de bits com erros acontecerem, o erro pode passar despercebido
	- Paridade Par → Um número par de bits 1 foi transmitido
	- Paridade Ímpar → Um número ímpar de bits 1 foi transmitido
- **Checksum**
	- Muito utilizado na camada 4 (transporte)
	- Baixo processamento
		- Utilizado quando e dá a nível de software
	- Transmite a soma de duas palavras (binário) e a inversão desta soma
	- No RX, a soma com a inversão transmitida tem que resultar numa sequencia de 1`s
- **Verificação de redundância cíclica (CRC)**
	- Exige bastante processamento
	- Mais eficiente
	- Ocorre a nível de hardware (camada de acesso)
	- A quantidade de bits define o padrão
		- CRC 8, CRC 12, CRC 16 ou CRC 32 (usado no padrão ethernet)
- **Distância de Hamming**
	- Define a quantidade de bits a serem corrigidos
	- **O que é o Código de Hamming (7,4)?**
		- O Código de Hamming (7,4) é um dos algoritmos clássicos de detecção e correção de erros em transmissões de dados (muito usado em memórias RAM e redes de computadores).
		- Os números **(7,4)** significam o seguinte:
• **4** bits são os seus dados reais (a mensagem que você quer enviar).
• **3** bits são adicionados como "bits de paridade" (para verificação).
• **7** é o total de bits do "pacote" enviado (4 + 3).
		- **Como saber quantos erros ele detecta e corrige?**
Tudo no código de Hamming se baseia na **Distância de Hamming **$d_{min}$, que no código de Hamming tradicional é sempre **igual a 3**. 
		- Essa distância é a quantidade mínima de bits que precisam ser "invertidos" para que um pacote válido se transforme em outro pacote válido.
		- A partir dessa Distância d = 3, a teoria da informação nos dá duas regras fixas:
1. **Detecção de Erros:** Um código detecta até d - 1 erros.
	◦ 3 - 1 = **Detecta até 2 erros**. (Se 1 ou 2 bits inverterem durante o envio, o sistema avisa: "Opa, tem algo errado aqui!").
2. **Correção de Erros:** Um código corrige até $\frac{d - 1}{2}$ erros.
	◦ $\frac{3 - 1}{2} = \frac{2}{2} =$ **Corrige até 1 erro**. (Se apenas 1 bit inverter, além de perceber o erro, a matemática do código consegue descobrir exatamente qual bit falhou e consertá-lo sozinho).

# Estatística

## Séries estatísticas

- Sucessão de números referentes a uma variável qualquer
- Sucessão de dados estatísticos referidos a caracteres qualitativos

### Séries homogradas

- Um único elemento da série estatística apresenta variação
	- Temporal
		- *Exemplo:* Vendas de veículos em Curitiba (local fixo) de janeiro a dezembro (tempo variável)
	- Geográfica
		- *Exemplo:* Taxa de desemprego no ano de 2025 (tempo fixo) comparada entre os estados do Sul, Sudeste e Nordeste (local variável)
	- Específica
		- *Exemplo:* Matrículas em uma universidade em 2026 (tempo e local fixos) divididas por curso: Engenharia, Direito, Medicina (espécie variável)

### Séries heterógradas

- Nenhum dos elementos da série apresenta variação
- O fato ou fenômeno pode ser registrado em diferentes intensidades
- Nestas séries, o fenômeno sofre **gradações** ou subdivisões, variando em intensidade. 
- O exemplo mais clássico de série heterógrada é a **Distribuição de Frequências**, onde os dados são agrupados em classes ou intervalos de intensidade
	- *Exemplo:* O número de funcionários de uma empresa (fenômeno) agrupados por faixas salariais (variação em intensidade: de R$ 1.500 a R$ 3.000, de R$ 3.001 a R$ 4.500, etc.).

![[Poscomp/images/image 2.png]]

# Algoritmos

## Técnicas de Projeto de Algoritmos

### Algoritmo guloso (greedy)

- **Como funciona:** Constrói a solução passo a passo, escolhendo sempre a opção mais vantajosa no momento **(ótimo local)**. Não revisita decisões.
- **Problema clássico:** Algoritmo de Dijkstra (menor caminho em grafos), Algoritmo de Prim ou Kruskal (árvore geradora mínima), e o Problema do Troco (usando o menor número de moedas, desde que o sistema de moedas seja canônico).
- **Ponto de atenção:** Nem sempre encontram a solução perfeita (ótimo global). Por exemplo, no problema da mochila (Knapsack 0-1), a estratégia gulosa falha, sendo necessária a Programação Dinâmica.

### Força Bruta (pesquisa exaustiva)

- **Como funciona:** Testa absolutamente **todas** as combinações ou caminhos possíveis até encontrar a solução.
- **Uso:** É trivial de implementar, mas geralmente tem complexidade de tempo altíssima (ex: $O(2^n)$ ou $O(n!)$). 
- Só é útil para entradas muito pequenas.
- **Exemplo:** Caixeiro Viajante resolvido testando todas as rotas.

### Dividir e Conquistar

- **Como funciona:** Quebra o problema original em subproblemas *menores e independentes*, resolve cada um recursivamente e, no fim, combina as respostas.
- **Problemas clássicos:** *Merge Sort* e *Quick Sort* (ordenação), Busca Binária.

### Backtracking

- **Como funciona:** É uma **busca em profundidade (DFS)** que constrói candidatos à solução gradualmente. Assim que percebe que um candidato não pode gerar uma solução válida, ele "poda" esse caminho (pruning) e volta um passo atrás para tentar outra opção.
- **Problemas clássicos:** Problema das 8 Rainhas, resolução de Sudoku, labirintos (onde você *pode* voltar).

### Programação Dinâmica

- Ao contrário da técnica de Dividir e Conquistar (onde os subproblemas são independentes), na Programação Dinâmica os subproblemas se **sobrepõem**. 
- Para não recalcular a mesma coisa várias vezes, ela guarda os resultados em uma tabela (técnica de *Memoization* ou *Tabulation*).

### Heurísticas

- **Como funciona:** Quando um problema é intratável (demora milhares de anos para resolver exatamente, como os problemas *NP-Difícil* da sua ementa de Computabilidade), usamos heurísticas. 
- Elas não garantem a melhor solução matemática, mas encontram uma solução "boa o suficiente" em um tempo aceitável.
- **Exemplos famosos:** Algoritmos Genéticos, Simulated Annealing (Têmpera Simulada), e Busca Tabu.

## Classes de complexidade

- Um problema é considerado "tratável" se pode ser resolvido em tempo polinomial, como $O(n)$, $O(n^2)$ ou $O(n^3)$. 
- Quando um problema exige tempo exponencial, como $O(2^n)$ ou fatorial $O(n!)$, dizemos que ele é "intratável", pois para entradas moderadas, o universo acabaria antes do computador terminar o cálculo.

### P (Polinomial)

- Problemas "fáceis" de resolver. 
- O computador resolve rápido (em tempo polinomial, como $O(n)$ ou $O(n^2)$), mesmo para entradas grandes.
- **Exemplos:** Ordenar uma lista (Merge Sort), encontrar o menor caminho em um grafo (Dijkstra), busca binária.

### NP (Polinomial Não-Determinístico)

- Fáceis de checar. 
- Regra número um para um problema pertencer à classe **NP** é: **ele precisa ser verificável em tempo polinomial** (rápido)
- Montar um quebra-cabeça gigante de 10.000 peças pode demorar muito, mas se eu te entregar ele montado, você bate o olho (verifica) rapidamente e diz se está certo. 
- Todo problema P também é NP.
- **Exemplo:** Sudoku. Resolver um Sudoku gigante é muito difícil. Mas se eu te entregar a grade preenchida, você verifica rapidamente se há números repetidos nas linhas e colunas.

### NP Completo

- Eles são os problemas mais difíceis dentro do conjunto NP. 
- Se um problema é NP-Difícil e, por acaso, ele ***também***** for rápido de verificar** (ou seja, também pertence a NP), ele ganha o título especial de **NP-Completo**. 
- A classe NP-Completo é justamente a **interseção entre NP e NP-Difícil**
- todos os outros problemas de NP precisam poder ser transformados ("reduzidos") nele
- Eles têm uma propriedade mágica: se você conseguir descobrir um algoritmo rápido (polinomial) para resolver **um único** problema NP-Completo, você automaticamente resolve **todos** os problemas da classe NP.
- É "impossível" (até onde sabemos hoje) é resolvê-los de forma **rápida** e exata quando a quantidade de dados cresce. 
- Para resolvê-los, os computadores precisam apelar para a força bruta (que pode levar anos) ou usar as **heurísticas** (que dão uma resposta rápida, mas aproximada, lembra?).
- **Exemplos:** O problema SAT (Satisfatibilidade Booleana), Caixeiro Viajante (versão de decisão), Coloração de Grafos.

### NP-Difícil (NP-Hard)

- O topo da cadeia alimentar da dificuldade. 
- Inclui problemas de otimização pesados. Não sabemos resolvê-los rápido e, muitas vezes, nem verificar rápido.
- N**ão sabemos se existe um algoritmo eficiente (polinomial)** para resolvê-los. Na verdade, a maioria dos cientistas acredita que não existe.
- Eles não precisam ser problemas de decisão (aqueles que respondem "Sim" ou "Não"). 
- Podem ser problemas de otimização, como "qual a menor rota possível?".

# Algoritmos de Ordenação

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

# Estruturas de Dados

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
![[Poscomp/images/Untitled.png]]
- Árvore binária completa
	- Com exceção do último nível, todos os elementos tem 0 ou 2 filhos
![[Poscomp/images/Untitled 1.png]]
- Estritamente binária
	- Todos os elementos têm 0 ou 2 filhos
![[Poscomp/images/Untitled 2.png]]

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
![[Poscomp/images/Untitled 3.png]]
![[ADS Puc/images/Untitled 4.png]]
	- Direita Simples
		- Quando a subárvore mais à esquerda causar o desbalanceamento
		- O filho a direita da subárvore esquerda será o filho a esquerda do pai
		- O pai será filho a direita da subárvore esquerda
![[ADS Puc/images/Untitled 5.png]]
![[ADS Puc/images/Untitled 6.png]]
	- Esquerda Dupla
		- Quando a subárvore esquerda da direita causar o desbalanceamento
		- Simples **direita** na **subárvore direita** + simples **esquerda** na árvore **original**
			- Obs: Mesmo que o filho seja null
![[ADS Puc/images/Untitled 7.png|Desbalanceada]]
![[ADS Puc/images/Untitled 8.png|Passo 1: Desmembra a subárvore direita]]
![[ADS Puc/images/Untitled 9.png|Passo 2: Rotação à direita]]
![[ADS Puc/images/Untitled 10.png|Passo 3: Junta na árvore original]]
![[ADS Puc/images/Untitled 11.png|Passo 4: Rotação à esquerda]]
	- Direita Dupla
		- Quando a subárvore direita da subárvore esquerda causa o desbalanceamento
		- Esquerda simples na subárvore esquerda + direita simples na árvore original
![[ADS Puc/images/Untitled 12.png|Desbalanceada]]
![[ADS Puc/images/Untitled 13.png|Passo 1: Desmembra a esquerda]]
        Passo 2: Rotação à esquerda
        Passo 3: Junta na árvore original
        Passo 4: Rotação à direita
![[ADS Puc/images/Untitled 14.png]]
![[Concursos/images/nse-6779031373762075482-1000064235.jpg]]
![[Concursos/images/nse-3696523304561482442-1000064242.jpg]]
    ## Remoção
    ESTRATÉGIA 1
PASSO 1: IDENTIFIQUE O ELEMENTO QUE VOCÊ DESEJA RETIRAR DA ÁRVORE (EM VERMELHO)
PASSO 2: IDENTIFIQUE O MENOR ELEMENTO DE TODA SUBÁRVORE À DIREITA DO NÓ IDENTIFICADO NO
PASSO 1 (EM VERDE)
PASSO 3: COPIE O VALOR DO NÓ IDENTIFICADO NO PASSO 2 PARA O NÓ IDENTIFICADO NO PASSO 1
PASSO 4: REMOVA O ELEMENTO IDENTIFICADO NO PASSO 2.
![[ADS Puc/images/Untitled 15.png]]
    ESTRATÉGIA 2
PASSO 1: IDENTIFIQUE O ELEMENTO QUE VOCÊ DESEJA RETIRAR DA ÁRVORE (EM VERMELHO)
PASSO 2: IDENTIFIQUE O MAIOR ELEMENTO DE TODA SUBÁRVORE À ESQUERDA DO NÓ IDENTIFICADO NO
PASSO 1 (EM VERDE)
    PASSO 3: COPIE O VALOR DO NÓ IDENTIFICADO NO PASSO 2 PARA O NÓ IDENTIFICADO NO PASSO 1
PASSO 4: REMOVA O ELEMENTO IDENTIFICADO NO PASSO 2.
![[ADS Puc/images/Untitled 16.png]]

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
![[ADS Puc/images/Untitled 17.png]]
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

![[ADS Puc/images/Untitled 18.png]]

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

## Tipos

- Grafos Direcionados
	- Quando suas arestas possuem indicação de sentido
- Ponderados
	- Quando as arestas possuem um peso associado
- Cíclicos
	- Quando é possível sair de um vértice e retornar a ele, seguindo arestas sem repetir caminhos
- **grau de entrada** 
	- (número de arestas que chegam ao vértice) e o 
- **grau de saída** 
	- (número de arestas que partem dele)
- **fortemente conectado** 
	- é um jargão exclusivo de grafos *direcionados*. 
	- Para grafos *não direcionados*, dizemos apenas que o grafo é **conexo** se existe um caminho entre qualquer par de vértices.
- **Ordenação topológica**
	- Ordenação linear de todos os seus vértices tal que se G contém uma aresta (u,v), então “u” aparece antes de “v”, ou seja, pode ser vista como uma ordenação de seus vértices ao longo de uma linha horizontal de tal forma que todas as arestas estão direcionadas da esquerda para direita.

## Algoritmos de Busca

- **BFS - Busca em largura**
	- Explora o grafo em "camadas" (vizinhos próximos primeiro). 
	- Usa uma estrutura de fila (*Queue*). 
	- É perfeito para encontrar o caminho mais curto em grafos *não ponderados*.
- **DFS (Busca em Profundidade):** 
	- Vai o mais fundo possível em um caminho antes de voltar (backtracking). 
	- Usa uma estrutura de pilha (*Stack*) ou recursão. 
	- Ótimo para detectar ciclos e fazer ordenação topológica.
- **Caminho Mínimo (Grafos Ponderados):**
	- **Dijkstra:** 
		- O mais famoso. Encontra o caminho mais curto de um vértice para todos os outros. 
		- A pegadinha: **não funciona se houver pesos negativos**.
	- **Bellman-Ford:** 
		- Faz a mesma coisa que o Dijkstra, mas é um pouco mais lento. 
		- Sua vantagem? Consegue lidar com arestas de peso negativo e detecta ciclos negativos.
	- **Floyd-Warshall:** 
		- Encontra o caminho mais curto entre *todos os pares* de vértices possíveis na matriz.
- **Árvore Geradora Mínima (MST):**
	- Usada para conectar todos os vértices de um grafo com o menor custo total possível 
	- (ex: passar cabos de fibra ótica em um bairro gastando o mínimo de material).
	- **Kruskal:** 
		- Ordena todas as arestas pelo peso e vai adicionando as mais baratas, desde que não formem um ciclo.
	- **Prim:** 
		- Começa de um vértice qualquer e vai "crescendo" a árvore sempre anexando a aresta vizinha mais barata disponível.

## Matriz de adjacência

- Representação por matrizes
- Cada coluna representa um nó
- As linhas representam os mesmos nós
- Um valor da matriz Aij significa que há um arco ligando os nós i e j
- Se os arcos tiverem um peso associado, o valor representado na matriz será o peso do arco, caso contrário, será 1
- Se o grafo for direcional (cada arco tem um sentido definido) a matriz não será simétrica
- Valores representados na diagonal da matriz significam um laço (um arco que liga ao próprio nó)

![[Poscomp/images/image 3.png]]

- Ocupa espaços de memória desnecessários, porém é mais fácil de entender e mais rápida de ser consultada

## Lista de adjacência

- Economiza espaço de memória, especialmente para grafos muito grandes
- Cada nó possui uma lista com os demais nós conectados a ele
- Pode também representar os pesos

<!-- Column 1 -->
![[Poscomp/images/image 4.png]]

<!-- Column 2 -->
![[Poscomp/images/image 5.png]]

## Travessia

- Iniciando em um vértice, visitar todos os outros vértices possíveis
- Os dois algoritmos principais são
	- Depth First Search (DFS)
		- Normalmente implementando utilizando pilha ou recursão
		- Call Stack
	- Breadth First Search (BFS)
		- Normalmente implementado utilizando fila

## Shortest Path

![[Poscomp/images/image 6.png]]

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

5. **Consultas OLAP**: São muito eficientes em consultas que envolvem **operações de leitura intensiva** em **data warehouses**, onde se realiza a análise de grandes volumes de dados históricos.
6. **Colunas de baixa cardinalidade**: São mais eficazes em colunas com poucos valores distintos, como "Gênero", "Status", "Categoria", etc., onde o número de bits necessários para representar todos os valores distintos é pequeno.
7. **Consultas complexas**: São ideais para consultas complexas que envolvem múltiplas condições em colunas diferentes. Isso ocorre porque as operações lógicas (AND, OR, NOT) podem ser aplicadas diretamente nos bitmaps de forma eficiente.

## Resumo:

![[Poscomp/images/image 7.png]]

![[Poscomp/images/image 8.png]]

![[Poscomp/images/image 9.png]]

![[Poscomp/images/image 10.png]]

![[Poscomp/images/image 11.png]]

![[Concursos/images/image 12.png]]

![[Concursos/images/image 13.png]]

![[Concursos/images/image 14.png]]

![[Concursos/images/image 15.png]]

![[Concursos/images/image 16.png]]

![[Concursos/images/image 17.png]]

![[Concursos/images/image 18.png]]

![[Concursos/images/image 19.png]]

![[Concursos/images/image 20.png]]

![[Concursos/images/image 21.png]]

![[Concursos/images/image 22.png]]

![[Concursos/images/image 23.png]]

# Arquitetura de Computadores

## Mapeamento de Cache

- **Mapeamento Direto:** 
	- É o mais rígido. 
	- Cada bloco da memória principal tem um, e apenas um, "endereço fixo" para onde pode ir na cache (geralmente calculado por `Bloco RAM MOD Tamanho da Cache`). 
	- Se o processador precisar de dois blocos distintos que mapeiam para a mesma linha, ocorre um gargalo (colisão), e um bloco expulsa o outro, mesmo se o resto da cache estiver completamente vazio.
- **Mapeamento Totalmente Associativo:** 
	- É o oposto perfeito do direto. 
	- O bloco da memória principal pode ser guardado em **qualquer** lugar da cache. 
	- Evita colisões desnecessárias, mas custa muito caro em hardware: para saber se um dado está na cache, o processador precisa ler as *tags* (etiquetas de identificação) de todas as linhas da cache ao mesmo tempo.
- **Mapeamento Associativo por Conjunto:** 
	- É o "meio-termo" inteligente e o mais usado nos processadores modernos (como Intel e AMD). 
	- A cache é dividida em grupos (conjuntos). 
	- O bloco da memória principal é mapeado obrigatoriamente para um **conjunto específico**, mas lá dentro, ele pode ocupar **qualquer linha**.

## Máquinas de estado finito

| **Característica** | **Máquina de Moore** | **Máquina de Mealy** |
| --- | --- | --- |
| **Dependência da Saída** | Apenas do estado atual. | Do estado atual + entradas atuais. |
| **Velocidade de Reação** | Mais lenta. A saída só muda no próximo ciclo de *clock* (quando o estado muda). | Mais rápida. A saída muda imediatamente assim que a entrada muda, sem esperar o *clock*. |
| **Quantidade de Estados** | Geralmente precisa de **mais** estados para implementar a mesma lógica. | Geralmente consegue resolver o mesmo problema com **menos** estados. |
| **Segurança/Estabilidade** | Mais segura, pois as saídas são síncronas ao *clock*, evitando "ruídos" transitórios (*glitches*). | Pode gerar saídas falsas (*glitches*) se as entradas mudarem de forma assíncrona antes do *clock*. |

# Paradigmas de linguagem de programação

### 1. Paradigma Funcional (2)

> *( 2 ) Programação baseada na aplicação de funções matemáticas, enfatizando imutabilidade e ausência de efeitos colaterais.*

- **Palavras-chave para a prova:** Funções matemáticas, funções de alta ordem (First-class functions), imutabilidade, estado livre (stateless), sem efeitos colaterais (side-effects).
- **Exemplos de linguagens:** Haskell, Lisp, Clojure.

### 2. Paradigma Declarativo (5)

> *( 5 ) Foca no quê do problema, descrevendo o resultado desejado sem especificar explicitamente a sequência de passos para alcançá-lo.*

- **Palavras-chave para a prova:** O "quê" fazer (ao invés de "como" fazer), controle de fluxo implícito, foco no resultado.
- **Exemplo clássico:** SQL. Você diz ao banco de dados "SELECT nome FROM alunos" (o quê), sem precisar programar o laço de repetição e os ponteiros para buscar o dado (o como).

### 3. Paradigma Lógico (4)

> *( 4 ) Resolve problemas por meio de encadeamento de regras e fatos, utilizando mecanismos de inferência automática para encontrar soluções.*

- **Palavras-chave para a prova:** Fatos, Regras, Predicados, Resolução, Unificação, Motor de inferência. O paradigma lógico é, na verdade, um subconjunto do declarativo.
- **Exemplo de linguagem:** Prolog.

### 4. Paradigma Imperativo (1)

> *( 1 ) Programação centrada na modificação explícita de estados da memória através de comandos sequenciais e atribuições de variáveis.*

- **Palavras-chave para a prova:** Estados de memória, atribuição (`x = x + 1`), controle de fluxo explícito (loops, if/else), von Neumann (arquitetura base). É o oposto do declarativo, focando no "como" fazer passo a passo.
- **Exemplos de linguagens:** C, Pascal, Fortran.

### 5. Paradigma Orientado a Objetos (3)

> *( 3 ) Organização de programas em entidades que encapsulam dados e comportamentos, promovendo reúso e flexibilidade através de conceitos como herança e polimorfismo.*

- **Palavras-chave para a prova:** Classes, Objetos, Mensagens, Encapsulamento, Herança, Polimorfismo, Abstração.
- **Exemplos de linguagens:** Java, C++, Smalltalk (o pai da OO moderna).

## Semântica Formal

Enquanto a *sintaxe* define a gramática (se o código está escrito corretamente), a *semântica* define o **significado** (o que o código faz quando executa). A semântica formal usa matemática para provar propriedades de um programa, sendo dividida em três abordagens principais:

- **Semântica Operacional:** 
	- Descreve o significado do programa como uma sequência de passos de execução em uma máquina abstrata. 
	- Pense nela como a transição de estados de um sistema. 
	- É muito usada por quem escreve compiladores.
- **Semântica Denotacional:** 
	- Associa cada comando da linguagem a um objeto matemático (geralmente uma função matemática rigorosa). 
	- É a abordagem mais abstrata. 
	- O programa é visto como uma função que mapeia um estado inicial para um estado final.
- **Semântica Axiomática:** 
	- É focada em **provar a corretude** do programa. 
	- Utiliza a Lógica de Hoare (pré-condições e pós-condições). 
	- Você define o que deve ser verdade antes do comando executar e o que será verdade depois. 
	- Se as regras matemáticas forem satisfeitas, o programa está correto.

## Sistemas de Tipos e Verificação

Um sistema de tipos previne erros ao garantir que as operações só sejam aplicadas aos dados corretos. A banca adora cobrar a diferença entre os momentos em que essa checagem ocorre:

- **Verificação Estática (Static Typing):** 
	- Os tipos são checados em tempo de **compilação**. 
	- O compilador garante que não haverá erros de tipo antes do programa rodar (ex: Java, C++, C). 
	- Vantagem: execução mais rápida e código mais seguro.
- **Verificação Dinâmica (Dynamic Typing):** 
	- Os tipos são checados em tempo de **execução**. 
	- A variável pode mudar de tipo durante o funcionamento do programa (ex: Python, JavaScript). 
	- Vantagem: maior flexibilidade para o programador.
- **Tipagem Forte vs. Fraca:** 
	- Uma linguagem de tipagem *forte* (como Python ou Java) não permite conversões implícitas bizarras (ex: somar um número com uma string diretamente resulta em erro). 
	- Uma linguagem *fraca* (como JavaScript ou C) faz coerções automáticas por debaixo dos panos, tentando adivinhar o que você quer fazer (ex: `1 + "1" = "11"`).

## Inferência de Tipos

É a capacidade do compilador de **deduzir** automaticamente o tipo de uma expressão sem que o programador precise escrever explicitamente.

- **Exemplo:** 
	- Quando você digita `var x = 10;` no C# ou `auto x = 10;` no C++, o compilador infere estaticamente que `x` é um inteiro. 
	- Isso não é tipagem dinâmica; o tipo é fixado na compilação, mas você economizou digitação. 
	- Linguagens funcionais como Haskell levam isso ao extremo, inferindo tipos de funções inteiras via um algoritmo famoso chamado *Hindley-Milner*.

## Polimorfismo

É o conceito de que uma mesma interface ou nome pode ser usado para diferentes tipos de dados. No Poscomp, você precisa saber diferenciar as três categorias principais criadas pelo pesquisador Christopher Strachey:

- **Polimorfismo Paramétrico:** 
	- Ocorre quando uma função ou classe é escrita de forma genérica, de modo a lidar com valores de forma idêntica, independentemente de seus tipos. 
	- É o conceito de *Generics* em Java ou *Templates* em C++ (ex: criar uma `List<T>` que funciona igual para `int` ou `String`).
- **Polimorfismo de Inclusão (ou Subtipagem):** 
	- É o clássico da Orientação a Objetos. 
	- Uma função que espera receber um objeto do tipo `Animal` pode aceitar um objeto do tipo `Cachorro`, porque um `Cachorro` *é um* `Animal`.
- **Polimorfismo Ad-hoc (Sobrecarga / Overloading):** 
	- Ocorre quando funções com o **mesmo nome** têm comportamentos completamente diferentes dependendo do tipo ou quantidade de parâmetros que recebem. 
	- O operador `+` é um exemplo: ele soma números, mas concatena strings.

# Linguagens Formais

[Linguagens Formais e Automatos](https://www.youtube.com/playlist?list=PLqlIQgAFrQ14oDPZliY1-tyupYs0prBmW)

## Linguagem

- Tudo começa com um **Alfabeto** (geralmente representado por $\Sigma$), que é um conjunto finito de símbolos, como $\{0, 1\}$ ou $\{a, b\}$.
- $\Sigma ^*$ → Conjunto de todas as palavras possíveis sobre $\Sigma$
- $\varepsilon$ → Conjunto vazio
- $\Sigma ^+$ → Conjunto de todas as palavras possíveis sobre $\Sigma$ exceto o conjunto vazio
- W → Palavra
- Uma **Palavra** (ou *string*) é qualquer sequência formada por esses símbolos.
- Uma **Linguagem** é simplesmente um conjunto de palavras que seguem uma determinada regra.

## Linguagem Formal

- Subconjunto de $\Sigma ^*$
- Notação L
- Linguagem de programação
	- Conjunto de todos os programas (palavras) da linguagem
	- Conjunto de palavras chave de uma linguagem (if, while, do, int, integer …)

## **Derivação à Esquerda vs. Derivação à Direita**

Vamos imaginar a gramática:

- $S \rightarrow AB$
- $A \rightarrow a$
- $B \rightarrow b$
Se quisermos derivar a cadeia "ab", temos duas variáveis ($A$ e $B$) para resolver. Qual resolvemos primeiro?
- **Derivação mais à esquerda:** Você sempre substitui a variável que estiver mais à esquerda primeiro.

$S \Rightarrow AB \Rightarrow aB \Rightarrow ab$

- **Derivação mais à direita:** Você sempre substitui a variável que estiver mais à direita primeiro.

$S \Rightarrow AB \Rightarrow Ab \Rightarrow ab$

- Independentemente de você ter escolhido resolver pela esquerda ou pela direita, o "esqueleto" visual (a árvore de derivação) gerado por ambos os caminhos será exatamente o mesmo. 
- A ordem em que você escreve no papel não altera a estrutura lógica da palavra.

## Gramática

- Conjunto finito de regras
- Gramática de Chomsky:
	- $G = (V, T, P, S)$
	- V → Conjunto finito de símbolos, variáveis ou não terminais
	- T → Conjunto finito de símbolos terminais
	- P → Produções
	- S → Inicial

## Hierarquia de Chomsky

![[Concursos/images/image 24.png]]

![[Concursos/images/image 25.png]]

### Tipo 0

- Livre de regras

### Tipo 1

- Nenhuma das regras de produção pode reduzir o comprimento da forma sentencial que for reduzida
- Se $\alpha \rightarrow \beta$ então $|\alpha| <= |\beta|$
	- Certo: A → Aa
	- Errado: Aa → a

### Tipo 2

- As regras têm apenas uma variável do lado esquerdo
- Não pode ter terminal do lado esquerdo
	- Certo: A → $\beta$
	- Errado: Aa → $\beta$

### Tipo 3

- Deve ser linear à direita ou linear à esquerda
- Ou seja, a expressão gerada deve crescer somente para a direita ou para a esquerda. Não pode crescer para os dois lados
	- Certo: A → aB
	- Certo: B → Ba
	- Errado: A → ABa (combinação das duas anteriores)
- L é uma linguagem regular se e somente se existe pelo menos um autômato finito determinístico que aceite L
- Formalismos básicos da linguagem tipo 3
	- Autômato finito
	- Expressão regular
	- Gramática regular
- Limitações de expressividade
	- Devido à maior quantidade de regras
	- Não contempla duplo balanceamento:
		- $\{w^n v^n |\text{w é toda palavra em  }\{a,b\}\}$
		- Exemplo: Abertura e fechamento de parênteses (( ))
		- Linguagens de programação em geral não são regulares

### Autômato Finito

- Modelo matemático com entradas e saídas discretas
- Composto por entrada e estados
- Não tem memória
- Número finito e determinado de estados
- Somente um estado por vez
- Todo Autômato Finito é composto por 5 elementos matemáticos (uma quíntupla):
	- 1. **Alfabeto (**$\Sigma$**):** O conjunto de símbolos que a máquina entende (ex: {0, 1}).
	- 2. **Estados (Q):** A "memória" finita da máquina. Cada estado representa uma condição do sistema em um determinado momento.
	- 3. **Estado Inicial (**$q_0$**):** Onde a máquina sempre começa a leitura.
	- 4. **Estados de Aceitação/Finais (F):** Se a máquina terminar de ler a palavra e parar em um desses estados, a palavra é aceita.
	- 5. **Função de Transição (**$\delta$**):** O manual de regras que diz: "Se você está no estado X e ler o símbolo Y, vá para o estado Z".
- Exemplo: Elevador
![[Concursos/images/image 26.png]]
- Autômato finito
	- Determinístico
		- A partir de um determinado estado e do símbolo lido
		- Pode assumir um único estado
	- Não determinístico
		- A partir de um determinado estado e do símbolo lido
		- Pode assumir um conjunto de estados
	- Com movimentos vazios
		- A partir de um determinado estado e sem ler um símbolo
		- Pode assumir um conjunto de estados

### Autômato Finito Determinístico (DFA)

- A palavra-chave aqui é **previsibilidade e rigidez**.
- Em um DFA, para cada estado em que a máquina se encontra e para cada símbolo que ela lê, existe **exatamente um único caminho possível** a seguir.
- Você **não pode** ter duas setas saindo do mesmo estado com a mesma letra.
- Você **não pode** ficar sem uma seta para uma letra do alfabeto (a máquina sempre precisa saber o que fazer).
- É como programar um código linear simples com `if/else`: a máquina nunca precisa "adivinhar" para onde ir.
- É Composto por:
	- Uma fita
		- Dispositivo de entrada
		- Contém a informação a ser processada
	- Uma unidade de controle
		- Reflete o estado corrente da máquina
		- Possui uma unidade de leitura
		- Movimenta-se exclusivamente para a direita
		- Lê somente uma célula da fita por vez
![[Concursos/images/image 27.png]]
	- Programa, função programa ou transição
		- Comanda a leitura
		- Determina as transições
		- $\delta(P,a)=q$
			- Se o estado atual é p e o símbolo lido for a, vá para o estado q
![[Concursos/images/image 28.png]]
- Definição formal:
	- $M = (\Sigma,Q,\delta,q_0,F)$
		- $\Sigma$ → Alfabeto
		- Q → Conjunto de todos os estados possíveis
		- $\delta$ → Função de transição
		- $q_0$ → Estado inicial
		- F → Subconjunto de Q, estados finais
![[Concursos/images/image 29.png]]
![[Concursos/images/image 30.png]]
- Palavra aceita:
	- Após processar o último símbolo, parou no estado final
- Palavra não aceita:
	- Não parou no estado final
	- Função de transição não definida para algum estado

### Autômato Finito Não Determinístico (NFA)

- A palavra-chave aqui é **múltipla escolha (ou "poder de adivinhação")**.
- O NFA quebra as regras rígidas do DFA. Ele é uma máquina teórica que permite flexibilidade na construção:
	- De um mesmo estado, você pode ter **várias setas** com a mesma letra apontando para caminhos diferentes.
	- Você pode ter **nenhuma seta** para uma determinada letra (se a máquina ler essa letra ali, o caminho "morre").
	- Ele permite as famosas **transições vazias (**$\epsilon$** ou **$\lambda$**)**, o que significa que o autômato pode pular de um estado para outro de graça, sem ler nenhuma letra da palavra
		- Na linguagem informal ou em livros mais introdutórios (como o Sipser), nós costumamos dizer que o NFA (Autômato Finito Não Determinístico) possui transições vazias. 
		- Porém, na formalização clássica e mais rigorosa de Hopcroft e Ullman, existe uma separação estrita: 
			- existe o **AFND (NFA)**, que *não* pode ter transições vazias, 
			- e existe um modelo estendido chamado **$\epsilon$-AFND ($\epsilon$-NFA)**, construído especificamente para permiti-las. 
			- Por adotar essa separação rigorosa da literatura, a banca considera que um AFND puro não possui $\epsilon$-transições.
- Como um NFA pode se dividir em vários caminhos ao mesmo tempo, a regra de aceitação dele é: **se pelo menos um dos ramos possíveis terminar em um estado de aceitação, a palavra inteira é aceita.**

### DFA vs NFA

| **Característica** | **DFA (Determinístico)** | **NFA (Não Determinístico)** |
| --- | --- | --- |
| **Transições por símbolo** | Exatamente uma para cada símbolo do alfabeto. | Zero, uma ou múltiplas transições. |
| **Transições Vazias (**$\epsilon$**)** | Não permitidas. | Permitidas. |
| **Poder Computacional** | Reconhece Linguagens Regulares. | Reconhece Linguagens Regulares (têm o **mesmo** poder). |
| **Tamanho / Construção** | Geralmente tem mais estados e é mais difícil de desenhar. | Mais fácil e intuitivo de desenhar, costuma ter menos estados. |
| **Execução em Software** | Rápido e direto (O(N) tempo). | Mais lento, pois precisa simular todos os caminhos possíveis. |

- **A Maior Pegadinha de Prova:**
	- É muito comum a banca afirmar que "O NFA é mais poderoso que o DFA porque consegue fazer múltiplas escolhas e usar transições vazias".
	- **Isso é mentira.**
	- Existe um teorema provando que todo NFA pode ser convertido em um DFA equivalente que aceita exatamente a mesma linguagem (embora o DFA possa acabar tendo até $2^n$ estados). 
	- **Eles possuem exatamente o mesmo poder computacional.**

## Autômato com pilha

- Memória auxiliar
	- Independente da entrada
	- Não possui limite de tamanho
- Não determinístico
- ? → Teste de pilha vazia
- $\epsilon$ → movimento vazio da pilha ou da fita
- Novo critério de parada:
	- Consumir a fita toda
	- Finalizar em um estado final
	- **A pilha estar vazia**

![[Concursos/images/image 31.png]]

- $(b,B,\epsilon)$
	- b → Entrada
	- B → O que será desempilhado
	- $\epsilon$ → O que será empilhado
- $(?,?,\epsilon)$
	- ? → Poderia ser qualquer coisa. Significa que nenhuma entrada é consumida
	- ? → Consulta se a pilha está vazia
	- $\epsilon$ → Nada será empilhado

## Linguagem Regular

- Categoria mais simples e restrita de linguagens na famosa **Hierarquia de Chomsky** (onde ela é classificada como linguagem do Tipo 3). 
- O que a torna "regular" é o fato de que suas regras são tão simples que podem ser processadas por uma máquina com **memória finita e estritamente limitada**.
- Pode ser representada de três formas completamente equivalentes.
- Se você consegue construir uma, obrigatoriamente consegue construir as outras duas:
	- **A Máquina que Reconhece (Autômatos Finitos):**
		- Uma linguagem é regular se, e somente se, existir um **Autômato Finito** (seja ele Determinístico - DFA, ou Não Determinístico - NFA) capaz de ler a palavra símbolo por símbolo e dizer "Aceito" ou "Rejeito". 
		- Como o autômato tem um número fixo de estados, ele não tem como armazenar informações infinitas.
	- **A Fórmula que Descreve (Expressões Regulares):**
		- Como vimos nas questões anteriores, é a notação algébrica que descreve o padrão da linguagem usando apenas concatenação, união (+) e o fecho de Kleene (*).
	- **O Sistema que Gera (Gramáticas Regulares):**
		- São gramáticas extremamente restritas onde a regra de substituição só pode gerar um símbolo terminal (letra minúscula) seguido, no máximo, por um único símbolo não terminal (letra maiúscula) na mesma direção. 
		- Exemplo válido: $A \rightarrow aB$ ou $A \rightarrow a$.
- **O que elas NÃO conseguem fazer?**
	- Como as linguagens regulares rodam em máquinas sem uma memória auxiliar (como uma pilha infinita ou uma fita de Turing), elas **não sabem contar** quantidades arbitrárias ou rastrear estruturas aninhadas.
	- **Elas conseguem:** Checar se uma palavra tem um número par de 0s, procurar substrings, ou garantir que todo 'a' venha antes de um 'b'. (Padrões de repetição cíclica).
	- **Elas NÃO conseguem:** Validar se uma equação matemática tem os parênteses fechados corretamente, ou verificar se existe a mesma quantidade de $a$'s e $b$'s

## Lema do Bombeamento

- Em qualquer linguagem regular, se você pegar uma palavra que seja longa o suficiente, obrigatoriamente haverá um "pedaço" no meio dessa palavra que pode ser repetido (bombeado) infinitas vezes, ou até mesmo removido, e a nova palavra gerada continuará pertencendo à linguagem.
- É usado para **provar que uma linguagem NÃO é regular**

## Forma Normal de Chomsky

- Não reduz o poder de geração das gramáticas livres de contexto
- Usado por teoremas matemáticos e reconhecedores de linguagens
- Um gramática livre de contexto é dita na forma normal de Chomsky se todas as regras de produção estiverem nas formas:
	- A → BC ou
	- A → a
- Transformações:
	- A → Bd (não aceito)
		- A → BC
C → d
	- S → A==**BCD**==
		- S → AE
E → B**CD**
E → BF
F → CD

## Regex

| **Símbolo** | **Nome** | **O que faz** | **Exemplo** | **O que o exemplo encontra** |
| --- | --- | --- | --- | --- |
| `*` | Asterisco | Zero ou mais repetições do item anterior. | `ab*` | "a", "ab", "abb", "abbb" |
| `+` | Sinal de Mais | **Uma** ou mais repetições (nunca zero). | `ab+` | "ab", "abb" (mas nunca só "a") |
| `?` | Interrogação | Zero ou uma repetição (torna o item opcional). | `ca?sa` | "csa" ou "casa" |
| `.` | Ponto Final | Representa **qualquer** caractere único (exceto quebra de linha). | `a.c` | "abc", "a0c", "a-c", "a c" |
| `[ ]` | Classes | Define um conjunto de caracteres permitidos naquela posição. | `[a-z]` | Qualquer letra minúscula de 'a' a 'z' |

# Banco de Dados

## Escalonamento

- É como o banco lida com concorrência
- É a forma como o banco de dados lida com uma série de tarefas necessárias para completar uma alteração em seu estado
- **Escalonamento Serial:** 
	- As transações são executadas uma após a outra, sem intercalação. 
	- Isso é 100% seguro, mas tem péssimo desempenho.  
- **Escalonamento Não Serial:** 
	- As operações (leituras e escritas) de várias transações são intercaladas para melhorar o desempenho.
	- Se o escalonamento não serial mantiver a **mesma ordem cronológica **de operações conflitantes que existiria em um escalonamento serial, ele é seguro. 
	- É a forma que os SGBDs reais usam para garantir a serializabilidade.
- Um escalonamento não serial é chamado de **Serializável** quando:
	-  ele é "correto", ou seja, quando a sua execução intercalada produz um efeito que seja equivalente ao de alguma execução serial.
	- Se a execução intercalada das transações sempre levar **exatamente ao mesmo estado final** que uma execução serial levaria, **independentemente dos dados contidos no banco de dados no estado inicial**, então o escalonamento é perfeitamente seguro e, portanto, serializável. 

### Os três níveis de Equivalência

Em teoria de banco de dados, avaliamos o grau de "perfeição" de um escalonamento em três níveis (do mais fácil de checar para o mais difícil):

- **Serializabilidade de Conflito (Conflict Serializability):** 
	- Analisa apenas a sintaxe da ordem de Leituras (Reads) e Escritas (Writes). 
	- É resolvida verificando a ausência de ciclos em um grafo de precedência (Grafo de Serialização). 
	- É a técnica mais cobrada em provas!
- **Serializabilidade de Visão (View Serializability):** 
	- É uma definição mais branda que a de conflito. 
	- Todo escalonamento serializável em conflito é serializável quanto à visão, mas o inverso não é verdadeiro (especialmente por causa das *Blind Writes* – escritas cegas onde uma transação escreve sem ler antes). 
	- Identificar isso computacionalmente é um problema NP-Difícil, então os SGBDs evitam.
- **Equivalência de Resultado (Result Equivalence):** 
	- Como vimos na afirmativa III, é o nível mais alto. 
	- Para prová-la na prática, o SGBD precisaria entender a semântica (a matemática e a lógica da aplicação) das transações para todos os estados possíveis, o que é inviável no mundo real, ficando apenas como conceito teórico.

## Crash Recovery

### Políticas

- FORCE
	- Após o commit, todas as páginas modificadas são imediatamente gravadas no disco
- NO-FORCE
	- Após o commit, as páginas continuam na RAM
	- São gravadas em disco assincronamente depois
- STEAL
	- Uma transação que ainda não fez commit pode gravar dados em disco
- NO-STEAL
	- Uma gravação que ainda não fez commit não pode gravar dados em disco

| **Política de Buffer** | **Precisa de UNDO?** | **Precisa de REDO?** |
| --- | --- | --- |
| **No-Steal / Force** | Não (disco não tem lixo) | Não (tudo com commit já está no disco) |
| **Steal / Force** | Sim | Não |
| **No-Steal / No-Force** | Não | Sim |
| **Steal / No-Force** | Sim (disco pode ter lixo) | Sim (disco pode estar atrasado) |

- **O Padrão da Indústria:** 
	- Os bancos de dados comerciais (Oracle, PostgreSQL, SQL Server) utilizam a combinação **STEAL / NO-FORCE**. 
	- Isso maximiza o desempenho, pois o disco não vira um gargalo, mas exige um mecanismo complexo de recuperação caso o servidor desligue repentinamente (precisando tanto de UNDO quanto de REDO).

### Write Ahead Log

- *Antes* que uma página de dados modificada no cache seja gravada no disco (Steal), o registro detalhando essa alteração no arquivo de Log deve ser gravado no disco primeiro.
- Isso garante que, se o sistema falhar, o SGBD tenha o histórico no Log salvo no disco para saber como desfazer (UNDO) ou refazer (REDO) o que for necessário na página de dados.

### ARIES

- Algorithm for Recovery and Isolation Exploiting Semantics
- implementação prática do *Steal/No-Force*.
- 3 Fases:
	- **Fase de Análise:** 
		- Varre o log a partir do último *Checkpoint* para descobrir quais transações estavam ativas na hora da queda e quais páginas estavam sujas na memória.
	- **Fase de REDO:** 
		- Repete a história. 
		- Varre o log para frente, reaplicando todas as operações para colocar o banco de dados exatamente no estado em que estava no momento do crash (inclusive o lixo de transações não finalizadas).
	- **Fase de UNDO:** 
		- Varre o log de trás para frente, desfazendo apenas as operações das transações que não haviam recebido *commit* na fase de análise.

# Compiladores

[Compiladores - Aula 1 - Introdução à Compilação](https://www.youtube.com/watch?v=D60k4gxc9oI&list=PLzQ6XQkjUvZ-_oJbCrOplrsooavy1FqDj)

- Etapas
	- Análise / Frontend
	- Síntese / Backend
- No java (linguagem híbrida) o backend fica dentro da JVM

<!-- Column 1 -->
![[Concursos/images/image 32.png]]

<!-- Column 2 -->
![[Concursos/images/image 33.png]]

## Analisador Léxico

- **Usa Expressões Regulares**
- **Funções**
	- Leitura dos caracteres do código fonte
	- Remoção de caracteres irrelevantes
	- Agrupar caracteres em lexemas  e classificá-los em tokens
		- Detectar erros e relacionar com a posição no código
	- Gerar lista de tokens (marcas)
	- Manipular a tabela de símbolos
- **Leitura de caracteres**
	- Maior demanda de tempo de processamento
	- Em algumas situações é necessário ler caracteres para frente do final do operador para ter certeza de que ele terminou
	- São usados buffers e analisados
- Tabela de Símbolos
	- Armazena os identificadores e seus atributos
		- variáveis, funções, classes, objetos
			- tipo
			- espaço de memória alocado
			- escopo
			- quantidade de argumentos
			- tipo de argumentos
			- tipo de retorno
- Exemplo de análise léxica

![[Concursos/images/image 34.png]]

- Especificação dos tokens
	- Se dá por expressões regulares
- Reconhecimento de tokens
	- Autômatos finitos
	- Exemplos: 
![[Concursos/images/image 35.png|Reconhecimento de números]]
![[Concursos/images/image 36.png|Reconhecimento de identificadores (nomes de variáveis)]]
![[Concursos/images/image 37.png|Reconhecimento da palavra if (palavra reservada da linguagem)]]
	- No caso de palavras reservadas, praticamente existe um autômato para cada palavra
![[Concursos/images/image 38.png|Reconhecimento de todas as palavras reservadas da linguagem]]
	- Processo de reconhecimento de tokens:
![[Concursos/images/image 39.png]]
	- O `algoritmo de Thompson` converte a expressão regular em um autômato não determinístico
	- O `método dos subconjuntos` converte o autômato não determinístico em um autômato determinístico
	- O autômato determinístico pode ser convertido em programa

## Analisador sintático

- **Usa Gramática Livre de Contexto**
- Enquanto o analisador léxico analisa/reconhece os tokens, o analisador sintático verifica a ordenação destes
- De posse disso, monta a árvore de sintaxe. 
- Exemplo: `5 + 3 * 2` → tokens identificados: (`5`, `+`, `3`, `*`, `2`)

```plain text
      ( + )
      /   \
    (5)   ( * )
          /   \
        (3)   (2)
```

- Se, a partir da gramática, for possível criar uma árvore de derivação do mesmo tipo, a sintaxe está correta
- Eles se utilizam de uma **gramática livre de contexto**, definida por quatro componentes:
	- **Símbolos terminais:** Conjunto de símbolos pelos quais são formados os tokens (letras, números, símbolos)
	- **Símbolos não terminais:** Variáveis sintáticas
	- **Símbolo de partida:** Um não terminal usado como raiz da árvore
	- **Regras de produção**: Como terminais e não terminais se combinam para formar cadeias
- Classificação das GLC
![[Concursos/images/image 40.png]]
- **Ambiguidade**
	- Quando uma gramática permite que se crie mais de uma árvore de derivação para a mesma sentença
- **Recursividade à esquerda**
![[Concursos/images/image 41.png]]
- A classificação dos analisadores sintáticos gira em torno da **direção** em que eles tentam construir a Árvore de Sintaxe

### **Analisadores Top-Down (Descendente)**

- começam pela **raiz** da árvore (o símbolo de partida da gramática) e vão "adivinhando" e expandindo as regras até chegarem nas **folhas** (os tokens que você digitou no código)
- Parte-se de um símbolo não terminal, que é o símbolo inicial da gramática e tenta-se chegar na mesma estrutura dos tokens digitados.
- Se isso for possível, a sintaxe está correta.
- Exemplo:
![[Concursos/images/image 42.png|Exemplo de análise sintática usando árvore de derivação]]
- **Utilizam uma gramática LL (como o analisador *****LL(1)*****).**
	- **L** (*Left-to-right*): Leem o código da esquerda para a direita.
	- **L** (*Leftmost derivation*): Sempre tentam expandir o não-terminal mais à esquerda primeiro.
	- **1: **Analisam um símbolo a frente da cadeia de entrada
- São muito mais intuitivos para humanos
- Sofrem com um problema chamado **Recursão à Esquerda**. 
	- Se a gramática da linguagem tiver uma regra que chama a si mesma logo no início (ex: `Expressão -> Expressão + Numero`), um parser Top-Down entra em um *loop* infinito tentando expandir a `Expressão` para sempre. 
	- O compilador precisa modificar a gramática matematicamente antes de analisá-la.
- Tipos de análises topdown
	- **Análise Descendente Recursiva**
		- Faz backtracking
		- Testa diferentes produções para derivar um não terminal
		- Usa busca em profundidade
		- Desfaz o caminho quando não reconhece a cadeia para iniciar outra derivação
	- **Análise Descendente Preditiva**
		- Sem recursão
			- [Compiladores - Aula 10 - Análise Sintática Descendente](https://www.youtube.com/watch?v=pYb6lIO4p8o&list=PLzQ6XQkjUvZ-_oJbCrOplrsooavy1FqDj&index=11)
			- Precisa de uma gramática LL(1)
			- Usa uma pilha para simular a derivação à esquerda e um buffer de entrada que corresponde à expressão que está sendo analisada
			- Utiliza uma tabela de análise (Tabela M) para determinar a produção a ser utilizada em cada não terminal
			- Sempre que no topo da pilha tiver um símbolo terminal, este é comparado com o símbolo mais a esquerda da expressão.
			- Caso sejam iguais, ambos são removidos e a análise recomeça a partir do próximo símbolo, usando a pilha como ficou
![[Concursos/images/image 43.png]]

### **Analisadores Bottom-Up (Ascendente)**

- **Utilizam uma gramática LR(k)**
	- L: Leitura dos símbolos da esquerda para a direita
	- R: Construção da árvore com derivação à direita
	- k: Quantidade de símbolos a frente que precisam ser analisados para as decisões (0 ou 1 são suficientes)
- Começam pelas **folhas** (o seu código) e vão agrupando e reduzindo os pedaços até chegarem à **raiz** (o símbolo de partida que valida o código inteiro).
- Inicia-se pela lista de tokens digitados e vai se fazendo reduções com base nas regras da gramática até se chegar à raiz
- A leitura dos tokens (Cadeia de entrada) é feita da esquerda para a direita
- **A sigla clássica:** Eles pertencem à família **LR**.
	- **L** (*Left-to-right*): Também leem da esquerda para a direita.
	- **R** (*Rightmost derivation*): Constroem a derivação mais à direita, só que de trás para frente (reversa).
- Muito mais robustos matematicamente e reconhecem uma classe maior de linguagens do que os LL. 
- **Lidam perfeitamente com a recursão à esquerda** sem entrar em *loop*.
- Muito complexos e dependem de extensas tabelas de transição
- Analisadores ascendentes SLR(1)
	- Análise LR simples
	- Tabela Action
	- Tabela GoTo
- Analisadores ascendentes LR(1)
	- Análise LR canônica
	- Tabela Closure
	- Tabela GoTo
- Analisadores ascendentes LALR(1)
	- Análise LR com verificação a frente

### **Tradução dirigida pela sintaxe**

- Na prática, as etapas de frontend do compilador (análise léxica, sintática, semântica e geração de código intermediário) ocorrem quase que simultaneamente
- A tradução dirigida pela sintaxe possibilita a tradução de linguagens durante a análise sintática:
	- Verificação de tipos (análise semântica)
	- Geração de código intermediário
	- Definição de pequenas linguagens para tarefas específicas
- É feito através da adição de atributos e ações aos símbolos da gramática (gramática de atributos)
- Atributos herdados
	- Definido por regra semântica com base nos atributos do pai, irmãos ou do próprio nó
- Atributos sintetizados
	- Calculado com base nos atributos dos filhos deste nó
![[Concursos/images/image 44.png]]
![[Concursos/images/image 45.png]]
	- No exemplo acima forma-se uma dependência circular
	- Resolve-se pela construção de um grafo de dependência
	- Cada símbolo não terminal torna-se um vértice no grafo
	- **Definição S-Atribuída**
		- Só possui atributos sintetizados
	- **Definição L-Atribuída**
		- Pode ter atributos sintetizados
		- Para atributos herdados, o corpo das produções (arestas do grafo) podem ser direcionadas apenas da esquerda p/ a direita
- **Tradução dirigida pela sintaxe é **Implementado por:
	- Mais fáceis de implementar
	- Utiliza fragmentos de código anexados às regras
	- Mais eficientes
		- X.a → Símbolo não terminal X com um atributo a
![[Concursos/images/image 46.png]]
	- **Pós-fixado**
		- Todas as ações são colocadas no final da produção
		- São executadas durante a redução
		- Implementam SDD S-Atribuídas com gramáticas LR
	- **Com ações inseridas nas produções**
		- Ações em qualquer parte da produção
		- Executadas após a derivação do símbolo à esquerda
		- Implementam SDD L-Atribuídas com gramáticas LL
	- Utiliza atributos anexados à gramática para montar a notação pós-fixa final
![[Concursos/images/image 47.png]]

## Analisador Semântico

- Utiliza esquemas de tradução para determinar os tipos e tamanhos das variáveis
- Sistema de tipos
	- verificação de compatibilidade de tipos entre operadores e operandos
- Expressividade
	- Sobrecarga de operadores
- Eficiência em tempo de execução
	- Alocação de memória
- Aplicações de tradução
	- Determina a quantidade de memória para o armazenamento

## Geração de Código Intermediário

- Nível de abstração intermediário
- **Notações possíveis**
	- Árvores de sintaxe
	- Grafos acíclicos dirigidos
	- Código de três endereços
		- No máximo um operador por instrução

# Machine Learning e IA

[[NOTION_PAGE:a0b81576-ea77-4657-9469-3c3f2d3fa656]] 

## Árvores de decisão

- Dado um conjunto aleatório, o algoritmo testa parâmetros que gerem separação entre os objetos do conjunto
- Estes parâmetros vão sendo testados em etapas, gerando uma árvore
- Em cada etapa de separação na árvore (nó) o algoritmo tenta dividir o conjunto mais um pouco
- **Pureza**:
	- **Máxima **→ quando todos os itens foram classificados corretamente. Exemplo: Um nó só com maçãs e outro só com laranjas
	- **Mínima **→ Nenhum item classificado corretamente. Exemplo: Um nó com todas as laranjas e maçãs misturadas
- Escolha da melhor divisão
	- **Entropia**
		- Alta → pureza baixa
		- Baixa → pureza alta
		- Algoritmo ID3
	- **Índice de Gini**
		- Probabilidade de um elemento ser classificado incorretamente se rotulado aleatoriamente
		- Um índice 0 significa pureza máxima
		- Algoritmo CART
- **Overfitting**
	- Se a árvore crescer demais, pode sofrer Overfitting
	- Para evitar, existem duas alternativas
		- **Pré-poda** → Limita o grau de crescimento da árvore antes mesmo de iniciar o treinamento
		- **Pós-poda** → Deixa a árvore crescer até o fim e depois retiram-se galhos sem importância estatística
- **Árvores de classificação**
	- Usadas para variáveis categóricas
	- Sim/Não, Maçã/Laranja, etc…
- **Árvores de Regressão**
	- Utilizado para valores contínuos
	- Preço, distância, valor, etc…

# Pipeline Gráfico

- Série de 6 estágios

## 1- Estágio de Aplicação

- Antes de a placa de vídeo começar a desenhar, o processador (CPU) roda a lógica do programa. 
- Ele calcula a física, a inteligência artificial, a colisão e decide **quais** objetos precisam ser desenhados nesta exata fração de segundo. 
- Ele então envia uma lista de vértices (pontos 3D) para a placa de vídeo.

## 2- Processamento de Geometria (Vertex Shader)

- Aqui a placa de vídeo recebe os vértices puros e aplica as **Transformações Geométricas**. 
- Usando matrizes matemáticas complexas, o computador:
	- **Model:** Posiciona e rotaciona o objeto no mundo.
	- **View:** Move o mundo de acordo com a posição da câmera virtual.
	- **Projection:** Aplica a perspectiva (fazendo coisas distantes parecerem menores).

## 3- Montagem de Primitivas e Recorte (Clipping)

- Os vértices soltos são conectados para formar linhas ou triângulos (as primitivas). 
- Em seguida, ocorre o **Recorte** (Clipping). 
- Se um triângulo estiver inteiro nas costas da câmera ou fora da tela, ele é sumariamente descartado para economizar processamento.

### Algoritmos de recorte

- **Cohen-Sutherland**
	- Amplamente utilizado no pipeline gráfico para o recorte (clipping) de linhas 2D contra uma janela retangular. 
	- O método divide o espaço 2D em 9 regiões e atribui um código de 4 bits (conhecido como *outcode*) a cada extremidade da linha, baseado na posição do ponto. 
	- Considere que os bits representam as regiões Topo, Fundo, Direita e Esquerda (TBRL - Top, Bottom, Right, Left), onde o valor `1` indica que o ponto está fora da janela naquela direção.
- **Liang-Barsky (Recorte de Linhas)**
	- Enquanto o Cohen-Sutherland é ótimo se a maioria das linhas for trivialmente aceita ou rejeitada, o **Liang-Barsky** é matematicamente mais eficiente para linhas que realmente cruzam a tela.
	- Ele abandona a lógica de bits e usa a **equação paramétrica da reta** ( $P = P_0 + t \cdot \Delta P$, onde t varia de 0 a 1). 
	- Ele calcula os valores de t onde a reta cruza as 4 bordas infinitas da janela. 
	- Se a interseção for válida, ele recorta. 
	- Ele resolve interseções muito mais rápido que o Cohen-Sutherland porque faz menos divisões na CPU.
- **Sutherland-Hodgman (Recorte de Polígonos)**
	- Os dois algoritmos acima servem apenas para linhas. 
	- Se você precisa recortar um triângulo ou um quadrado (um polígono preenchido), você usa o Sutherland-Hodgman.
		- É um algoritmo em "cascata". 
		- Ele pega o polígono inteiro e recorta contra a borda Esquerda. 
		- O polígono resultante passa para a borda Direita, recorta. 
		- O resultado passa para o Topo, e assim por diante.
		- **Pegadinha de prova:** O Sutherland-Hodgman funciona perfeitamente para polígonos **convexos**, mas pode gerar linhas "fantasmas" indesejadas ligando buracos se for aplicado diretamente em polígonos **côncavos** complexos.

## 4- Rasterização

- Conversão 3D para 2D
- A placa de vídeo pega os triângulos matemáticos e descobre quais **pixels** da sua tela (do monitor 2D) estão dentro daquele triângulo. 

- Esses pixels "potenciais" gerados são chamados de *Fragmentos*.

## 5- Rendering

- Processamento de Fragmentos (Fragment/Pixel Shader)
- Para cada fragmento (pixel) gerado na etapa anterior, a GPU:
	- Aplica as **texturas** (como colocar um "papel de parede" no triângulo).
	- Executa o **Shading** (como Gouraud ou Phong) para calcular como a luz interage com aquela cor.
	- Executa o **Z-Buffer** (superfícies ocultas) para ver se esse fragmento está na frente ou atrás de outro objeto. Se estiver atrás, ele é descartado.

### Superfícies Ocultas

- **Z-Buffer**
	- **Faz a remoção de superfícies ocultas**
	- Para cada pixel na tela, ele guarda a profundidade (o eixo Z) do objeto que está sendo desenhado.
	- Se um novo objeto tentar ser desenhado naquele mesmo pixel, o algoritmo compara o Z novo com o Z guardado.
	- e o novo for mais raso (mais perto da câmera), ele sobrescreve a cor. Se for mais fundo (atrás do objeto atual), ele descarta, mantendo a superfície que estava oculta escondida.
- **Algoritmo do Pintor (Painter's Algorithm):** 
	- Resolve no nível do objeto. 
	- Ele simplesmente ordena todos os polígonos do mais distante para o mais próximo e desenha um por cima do outro. 
	- O problema? Falha miseravelmente se os polígonos se cruzarem (intersecção).
- **Árvores BSP (Binary Space Partitioning):** 
	- Divide o espaço 3D usando planos, criando uma estrutura de dados excelente para ambientes estáticos complexos (foi a grande revolução usada no jogo *DOOM* nos anos 90).

### Modelos de Tonalização (Shading)

- **Flat Shading (Tonalização Constante):** 
	- Calcula a luz apenas uma vez para o polígono inteiro. 
	- O resultado é um objeto todo facetado, parecendo um diamante ou um jogo antigo de PlayStation 1.
- **Método de Gouraud**
	- **Faz a tonalização e sombreamento (shading)**
	- Calcula como a luz bate nos vértices (nas pontas) do polígono e, a partir daí, simplesmente cria um gradiente de cores (interpola a cor) pelo meio do triângulo. 
	- É rápido, mas não lida bem com reflexos brilhantes no meio da superfície.

- **Método de Phong**
	- **Faz a tonalização e sombreamento (shading)**
	- É um modelo de tonalização mais avançado e realista. 
	- Em vez de interpolar cores, ele interpola as *normais* (vetores de inclinação matemática) ao longo de todo o polígono e recalcula a luz para **cada pixel** individualmente. 
	- Isso gera reflexos perfeitos e superfícies bem suaves, **exigindo mais processamento.**

### Aplicação de Texturas

- Quando o pixel da tela cai entre os *texels* da imagem, a placa de vídeo precisa decidir qual cor usar. 
- Ela faz isso utilizando um destes algoritmos:
	- **1. Nearest Neighbor (Vizinho Mais Próximo)**
		- É o algoritmo mais básico e barato. 
		- Ele simplesmente olha para a coordenada UV solicitada e pega a cor do *texel* que estiver mais perto do centro, ignorando os outros.
		- **Resultado visual:** Quando você chega perto do objeto, a textura fica "quadriculada" (pixelada). 
		- É o visual clássico do Minecraft ou dos jogos de PS1.
	- **2. Filtragem Bilinear**
		- Em vez de pegar uma única cor, o algoritmo captura os **4 texels** mais próximos da coordenada solicitada e faz uma interpolação (uma média suave) entre eles, baseada na distância exata.
			- **Resultado visual:** Elimina o aspecto quadriculado, deixando a textura com um leve "borrão" suave quando vista de perto.
	- **3. Filtragem Trilinear (Aqui o Mipmap entra em ação!)**
		- Lembra que o Mipmap cria várias versões menores da textura? O problema do filtro Bilinear é que, ao trocar de um mipmap maior para um menor (conforme a distância aumenta), cria-se uma "linha de corte" visível no chão.
		- O Trilinear resolve isso: ele pega os 4 texels do mipmap adequado, os 4 texels do mipmap imediatamente inferior, faz a média Bilinear em ambos, e depois tira uma **terceira média** entre os dois resultados.
		- **Resultado visual:** Transições de distância invisíveis e perfeitas.
	- **4. Filtragem Anisotrópica**
		- É o algoritmo mais avançado e pesado. 
		- Todos os algoritmos anteriores assumem que a textura está sendo esmagada em um formato perfeitamente quadrado. 
		- Mas quando você olha para uma estrada comprida, a textura sofre distorção oblíqua (ela é esmagada no eixo Z, mas não no eixo X). 
		- O filtro anisotrópico lê a textura em formatos retangulares que acompanham o ângulo de visão da câmera.

![[Concursos/images/image 48.png]]

## 6- Framebuffer (Blending)

- Os pixels que sobreviveram ao processamento de fragmentos sofrem os ajustes finais (como transparência e anti-aliasing) e são finalmente gravados na memória de vídeo (VRAM) para serem enviados ao seu monitor.

# Compressão de Dados

- O princípio fundamental da compressão é a eliminação de **redundância**:
	-  se um dado possui padrões repetitivos ou previsíveis, ele pode ser reescrito de forma mais enxuta sem perder seu significado.
- **Existem duas grandes categorias:**

## Compressão sem perdas (Lossless)

- O arquivo descompactado é idêntico ao original, sem perdas
-  Codificação de Huffman, 
- Algoritmos da família Lempel-Ziv (LZ77, LZ78, LZW) e 
- RLE (*Run-Length Encoding*).

### Princípios

- **A Entropia (H)**
	- Mede a **quantidade média de informação (em bits) contida em cada símbolo emitido por uma fonte de dados. **
	- Estabelece o** limite teórico mínimo de bits por símbolo **que uma compressão sem perdas consegue atingir.
	- **Teoria da Informação de Shannon**
		- Estabelece o limite teórico mínimo de bits por símbolo para uma compressão sem perdas
		- A fórmula para a entropia de uma fonte X com símbolos $x_i$ de probabilidade $P(x_i)$ é: 
$$
H(X) = -\sum_{i} P(x_i) \log_2 P(x_i)
$$
	- **Exemplo**:
		- Uma fonte de informação sem memória emite quatro símbolos distintos ($A, B, C, D$) com as seguintes probabilidades de ocorrência:
• $P(A) = 1/2$
• $P(B) = 1/4$
• $P(C) = 1/8$
• $P(D) = 1/8$

Qual é a entropia da fonte H(x)?

• $\log_2(1/2) = -1$
• $\log_2(1/4) = -2$
• $\log_2(1/8) = -3$
Agora, substituímos os valores dos nossos quatro símbolos na fórmula:
1. **Símbolo A:** $1/2 \cdot \log_2(1/2) = 1/2 \cdot (-1) = -0,5$
2. **Símbolo B:** $1/4 \cdot \log_2(1/4) = 1/4 \cdot (-2) = -0,5$
3. **Símbolo C:** $1/8 \cdot \log_2(1/8) = 1/8 \cdot (-3) = -0,375$
4. **Símbolo D:** $1/8 \cdot \log_2(1/8) = 1/8 \cdot (-3) = -0,375$
Somando os resultados parciais e aplicando o sinal negativo da fórmula:
$$H(X) = - ( -0,5 - 0,5 - 0,375 - 0,375 )$$
$$H(X) = - ( -1,75 ) = 1,75$$
	- **Regra de Ouro:** **Não é possível comprimir um arquivo de forma *****lossless***** para uma média de bits menor do que a sua Entropia.**
- **Códigos Prefixados (Código Livre de Prefixo)**
	- Para que uma mensagem codificada com bits de tamanho variável (como a Codificação de Huffman) possa ser lida pelo computador sem ambiguidade, nenhuma palavra-código pode ser o início (prefixo) de outra.
- **A Desigualdade de Kraft**
	- serve como um "teste de viabilidade" matemático para descobrir se é possível criar um dicionário de compressão válido antes mesmo de tentarmos construí-lo.
	- diz exatamente se um determinado conjunto de tamanhos de códigos consegue ou não respeitar a regra de códigos prefixados
	- É o teorema que garante a existência de um código prefixado para um determinado conjunto de comprimentos de palavra $l_i$: 
$$
\sum_{i} 2^{-l_i} \le 1
$$
	- **Se a soma for > 1:**
		- É matematicamente impossível construir um código livre de prefixo com esses tamanhos. 
		- Faltarão ramos na árvore binária.
	- **Se a soma for = 1:** 
		- É possível construir o código, e a árvore binária estará perfeitamente preenchida. 
		- Não sobrará nenhuma combinação de bits inútil (o algoritmo de Huffman sempre gera esse resultado).
	- **Se a soma for < 1:** 
		- É possível construir o código, mas a árvore terá "espaços sobrando". 
		- Você poderia adicionar mais códigos ou encurtar os existentes.
	- **Exemplo A: O Cenário Impossível**
		- Imagine que você quer criar um dicionário para 3 letras com os seguintes tamanhos de bits:
			- Letra X: 1 bit $(l_1 = 1)$
			- Letra Y: 1 bit $(l_2 = 1)$
			- Letra Z: 2 bits $(l_3 = 2)$
			- Aplicando a Desigualdade de Kraft: 
$$
2^{-1} + 2^{-1} + 2^{-2}
$$
$$
\frac{1}{2} + \frac{1}{2} + \frac{1}{4} = 1,25
$$

Como $1,25 > 1$, a desigualdade **falhou**.
*A prova lógica:* Se você usar o `0` para a letra X e o `1` para a letra Y, você esgotou todas as possibilidades de iniciar um código. Não há como criar a letra Z com 2 bits sem que ela comece com `0` ou `1` (quebrando a regra do prefixo).

### Os Três Paradigmas de Algoritmos *Lossless*

- **Baseados em Estatística/Frequência:** 
	- Analisam a frequência dos símbolos. 
	- Os símbolos mais comuns recebem códigos curtos e os raros recebem códigos longos (Ex: *Huffman*, *Shannon-Fano*, *Codificação Aritmética*).
- **Baseados em Dicionário:** 
	- Substituem sequências inteiras de caracteres que se repetem por referências a uma tabela ou janela deslizante criada dinamicamente 
	- (Ex: *LZ77*, *LZW* — a base do `.zip` e `.gif`).
- **Baseados em Repetição Contínua (RLE):** 
	- Identificam sequências consecutivas do mesmo caractere e as substituem por um contador 
	- (Ex: `AAAAABBB` vira `5A3B`).

### Algoritmos

- **Repetição**
	- **RLE (Run-Length Encoding)**
		- método mais rudimentar
		- substitui sequências contíguas de dados idênticos por um único valor de dado seguido por uma contagem
		- Por exemplo, a string "WWWWWWBBWW" é convertida em "6W2B2W”
		- muito eficiente para arquivos simples com grandes áreas de cor sólida (como logotipos ou o envio de fax), mas ineficiente para dados complexos ou textos naturais.
- **Estatísticos**
	- **Codificação de Huffman**
		- analisa a frequência de todo o arquivo e constrói uma **árvore binária de baixo para cima**, unindo **primeiro os elementos menos frequentes**
		- O resultado é um dicionário perfeito de prefixos onde os caracteres comuns ganham códigos muito curtos
		- **Processo:**
			- 1- Elaborar uma tabela com a frequência de cada letra
			- 2- Ir agrupando aos pares, das menores frequências para as maiores, formando uma árvore
			- 3- Descer a árvore, localizando cada letra, usando 0 para esquerda e 1 para direita
			- Exemplo: ABRACADABRA
```plain text
[C: 1]    [D: 1]    [B: 2]    [R: 2]    [A: 5]

			 [CD: 2]
       /     \
   (0)/       \(1)
[C: 1]         [D: 1]

(Ainda restam soltos: [B: 2], [R: 2] e [A: 5])

						 [CDBR: 6]
            /         \
        (0)/           \(1)
      [CD: 2]         [BR: 4]
      /     \         /     \
    /         \     /         \
 [C: 1]     [D: 1][B: 2]     [R: 2]

(Ainda resta: [A: 5])

								  [RAIZ: 11]
                 /          \
             (0)/            \(1)
               /              \
           [A: 5]          [CDBR: 6]
                          /         \
                      (0)/           \(1)
                        /             \
                   [CD: 2]           [BR: 4]
                   /     \           /     \
               (0)/   (1)/       (0)/   (1)/
                 /      /          /      /
              [C: 1] [D: 1]     [B: 2] [R: 2]
```
				- **Para achar o A:** Sai da raiz, vira para a esquerda (0) e já achou. Código: **0**.
				- **Para achar o R:** Sai da raiz, vira direita (1), direita (1) de novo, e direita (1) de novo. Código: **111**.
				- **Para achar o C:** Sai da raiz, vira direita (1), esquerda (0), esquerda (0). Código: **100**.
	- **Codificação de Shannon-Fano**
		- Predecessor do método de Huffman. 
		- funciona dividindo a lista de símbolos (ordenada por frequência) "de cima para baixo" em **duas metades com probabilidades o mais próximas possível**. 
		- Embora seja historicamente importante, foi provado que **Huffman gera árvores matematicamente mais otimizadas que o Shannon-Fano.**
	- **Codificação Aritmética**
		- Em vez de atribuir um código binário individual para cada símbolo (como faz o Huffman), a codificação aritmética representa a mensagem inteira como um único número fracionário hiperpreciso entre 0 e 1. 
		- Ela consegue alcançar taxas de compressão superiores, chegando ao limite teórico da Entropia, mas exige um processamento matemático consideravelmente mais pesado.
- **Algoritmos Baseados em Dicionário**
	- **LZ77 (Lempel-Ziv 1977)**
		- Utiliza uma técnica de "janela deslizante" (*sliding window*). 
		- O algoritmo olha para trás no fluxo de dados já processado. 
		- Se ele encontrar um padrão que se repete no momento atual, ele insere um ponteiro do tipo "volte X posições e copie Y caracteres" em vez de gravar a palavra de novo. 
		- É o coração do famoso algoritmo **DEFLATE**, motor dos arquivos `.zip`, `.gz` e imagens `.png`.
	- **LZW (Lempel-Ziv-Welch)**
		- Uma evolução dos métodos de Lempel e Ziv. 
		- Em vez de usar uma janela deslizante de tamanho fixo, o LZW constrói um dicionário dinâmico indexado na memória à medida que lê o arquivo. 
		- Ficou mundialmente famoso (e foi alvo de muitas brigas de patentes nos anos 90) por ser a tecnologia base do formato de imagem `.gif`.
- **Transformações de Bloco (Pré-compressão)**
	- **BWT (Burrows-Wheeler Transform):** 
		- O BWT não comprime os dados por conta própria. 
		- Ele é um algoritmo de ordenação que rearranja os caracteres de um arquivo em blocos para que letras idênticas fiquem agrupadas lado a lado. 
		- Ao criar longas repetições intencionais, o arquivo transformado pelo BWT torna-se um "banquete" perfeito para ser comprimido de forma devastadora por um algoritmo como o RLE ou o Huffman em seguida. 
		- É o cérebro por trás da excelente taxa de compressão do formato `.bz2` no Linux.

## Compressão com perdas (Lossy)

- Baseia-se nas limitações dos sentidos humanos
- O algoritmo descarta permanentemente dados que são imperceptíveis ou de pouca importância para a percepção humana (visão/audição), alcançando taxas de compressão altíssimas.
- Transformada Discreta de Cosseno (DCT), Quantização, Psicofísica e Psicoacústica.

### Processo

- **Transformação (A Preparação):** 
	- Os dados brutos são convertidos para o **domínio da frequência**
	- Usa a **DCT (Transformada Discreta de Cosseno)**. 
	- Separa o que é "detalhe genérico" (baixa frequência, que importa muito) do que é "detalhe minucioso" (alta frequência, que importa menos).
- **Quantização (A Perda Real):** 
	- Arredondamento matemático agressivo
	- Reduz ou agrupa as frequências separadas pela DCT
	- A informação original é destruída permanentemente neste passo.
- **Codificação de Entropia (O Polimento):** 
	- O algoritmo aplica uma compressão clássica *sem perdas* (como Huffman ou RLE) em cima do que sobrou para encolher o arquivo o máximo possível.

### JPEG

- O processo do JPEG não é um único algoritmo, mas sim um *pipeline* (uma esteira de produção) composto por várias etapas. 
8. **Preparação**
	- pega os pixels que estão no formato **RGB** (Vermelho, Verde e Azul) e os converte para o espaço de cor **YCbCr**, onde o **Y** é a Luminância (o brilho/preto e branco da imagem) e o **Cb/Cr** são a Crominância (as cores).
	- Comprime os canais Cb/Cr descartando cerca de 75% da informação de cores, mantendo o canal Y inalterado
9. **Separação dos blocos**
	- Separa a imagem em blocos de 8x8 pixels que serão processados individualmente
10. **Transformada Discreta de Cosseno (DCT)**
	- Converte cada bloco para o domínio da frequência
	- Transforma o bloco em um conjunto de frequências que o compõe
	- Até aqui, nenhuma informação foi descartada neste processo
11. **Quantização**
	- Aplica uma matriz de quantização de 8x8
	- Divide a matriz de DCT pela matriz de quantização
		- Quanto maior o valor na célula da matriz, menor o resultado da divisão
	- Após a divisão o resultado é arredondado para o inteiro mais próximo
12. **Compressão final**
	- A serialização da matriz é feita em zigue-zague, de forma que os valores mais próximos do canto inferior direito da matriz fiquem juntos
	- Como a matriz de quantização possui valores maiores nesta região, os valores da divisão tendem a zero
	- É aplicado o algoritmo RLE e depois ainda a codificação de Huffman

### MPEG

- introduz a **Compressão Temporal** (ou Inter-quadros).
- de um milissegundo para o outro, quase nada muda
- Faz a divisão de um vídeo em três "tipos" diferentes de imagens
	- Para cada bloco de 0,5s o algoritmo categoriza as imagens em 3 grupos
		- **Quadros I (*****Intra-coded Frames)***
			- imagens **estáticas** completas (muito parecidas com um JPEG padrão). 
			- Eles não precisam de nenhuma outra informação do vídeo para serem lidos ou renderizados na tela.
		- **Quadros P (*****Predictive Frames)***
			- Retém a informação do que mudou em relação ao último quadro I ou P
			- ocupam cerca de 50% do tamanho de um Quadro I
		- **Quadros B (*****Bi-directional Frames)***
			- Olham tanto para o quadro anterior quanto para o próximo quadro simultaneamente, e interpolam a diferença geométrica entre eles
			- **Oferecem a maior taxa de compressão**
		- **A compressão temporal atua nos quadros P e B!!**
- **Compensação de Movimento**
	- divide a imagem em **Macroblocos** (geralmente quadrados de 16x16 pixels).
	- Quando ele percebe que um objeto se moveu de um quadro para o outro, em vez de apagar os pixels antigos e renderizar novos, ele cria um **Vetor de Movimento**.
- **Montagem**
	- Aplica os vetores de movimento para gerar os Quadros P e B (Compressão Temporal).
	- Pega tudo o que sobrou e passa pela Transformada Discreta de Cosseno (DCT) e Quantização que vimos no JPEG (Compressão Espacial).
	- Usa o algoritmo de Huffman para varrer e empacotar todos os bits resultantes.