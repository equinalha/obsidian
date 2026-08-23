---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2026-07-30T17:00:00
Owner:
  - Eduardo Quinalha
---
# Resumo: Tipos de algoritmos

- **Classificação**: KNN, SVM, Naive Bayes
- **Árvore de decisão**: CART, C4.5
- **Regra de associação**: Apriori, FP-Growth
- **Clusterização**: K-means

# Viés e Variância

![[SubPages/Concursos/images/Untitled 95.png]]

# Transformação dos dados

## Normalização

- Traz todos os dados para uma **escala comum**, sem distorcer as diferenças nos intervalos de valores

### Técnicas de Normalização

- **Padronização**
	- **Utiliza Z-Score**
![[SubPages/Concursos/images/Untitled 96.png]]
	- Onde μ é a média dos dados e σ é o desvio padrão.
	- Converte os dados de forma que eles tenham uma média de 0 e um desvio padrão de 1
	- Traz a média para a origem do plano cartesiano
	- A média é centrada em 0, a variação é entre 0 e 1
	- Usado quando a distribuição dos dados é desconhecida ou quando os dados não possuem limites claramente definidos
	- pode ajudar a **identificar outliers**, já que transforma os dados em termos de desvios padrão em relação à média
	- No entanto, ele ainda pode ser influenciado por outliers, uma vez que o cálculo do desvio padrão é sensível a valores extremos.
- **Min-Max**
	- Converte os valores para uma faixa entre 0 e 1. O valor mínimo da variável se torna 0 e o valor máximo se torna 1.
	- É útil quando se deseja manter a distribuição dos dados sem alterar a proporção entre os valores. 
	- Muito utilizado quando a escala dos dados é importante.
	- **Altamente sensível a outliers**
![[SubPages/Concursos/images/Untitled 97.png]]
![[SubPages/Concursos/images/Untitled 98.png]]
- **Normalização por Intervalo Percentil**
	- Baseia-se na distribuição percentil dos dados.
	- Converte os dados de acordo com seus percentis. 
	- Isso é útil quando se lida com distribuições não uniformes ou enviesadas, onde a concentração de valores em torno de certos intervalos precisa ser ajustada.
	- Usado principalmente em estatísticas robustas e em casos onde os dados contêm muitos outliers.
- **Transformação Logarítmica**
	- Aplica a função logarítmica aos dados para reduzir a amplitude de valores e tornar distribuições altamente assimétricas mais simétricas.
	- Muito útil quando os dados apresentam uma distribuição **fortemente enviesada** ou quando há **outliers extremos**

# Tipos de aprendizado

- **Aprendizado supervisionado**
	- O algoritmo é treinado com um conjunto de dados rotulados
- **Aprendizado não supervisionado**
	- O próprio algoritmo busca identificar padrões
- **Aprendizado por reforço**
	- Baseado em recompensa
	- Exemplo: Algoritmos de sugestão de filmes e videos
	- Veículo autônomo

![[SubPages/Concursos/images/Untitled 99.png]]

- Aprendizado online
	- O algoritmo é treinado a medida que novos dados vão chegando
	- Os modelos são atualizados continuamente
- Aprendizado em lote
	- Dados estáticos
- Aprendizado baseado em instância
	- O sistema armazena exemplos de treinamento e faz previsões para novos exemplos com base na similaridade
	- Exemplo: k-Nearest Neighbors (k-NN) que classifica um ponto de dados com base na maioria dos seus k vizinhos mais próximos
- Aprendizado baseado em modelo
	- O sistema detecta padrões nos dados de treinamento e constrói um modelo abstrato

# Paradigmas de Aprendizado de Máquina

## Simbólico

- Expressa a hipótese (conceito) em uma linguagem de fácil interpretação
- **Árvores de decisão**
	- Aprendizado supervisionado
	- As folhas correspondem aos rótulos
- **Indução de regras**
	- Podem ser ordenadas ou não-ordenadas
	- As regras (if-else) são induzidas a partir dos rótulos dos dados de treinamento

## Estatístico

- **Aprendizado Bayesiano**
- São utilizados modelos estatísticos para encontrar uma boa aproximação do conceito induzido
- Baseado em abordagens probabilísticas

## Baseado em exemplos

- **K-NN**
- Baseado em experiências passadas

## Conexionista (Redes Neurais)

- Canais de comunicação que estão associados a um peso
- RNA

## Evolutivo

- **Algoritmos genéticos**
	- Baseiam-se em **codificação do conjunto das soluções possíveis** e não nos parâmetros da otimização em si
	- Os resultados são apresentados como uma população de soluções (não como uma única solução)

# Fontes de erro em modelos preditivos

- Algoritmos diferentes têm desempenho quase idêntico em um problema complexo, quando treinados com dados suficientes
- Dados importam mais do que algoritmos

# Aprendizado supervisionado

- É necessário segmentar os dados em 3 categorias distintas:
	- **Treinamento**
		- Usado para treinar o algoritmo
		- Descoberta de padrões
	- **Validação**
		- Valida o desempenho do modelo durante o treinamento
		- Fornece feedback sobre o treinamento
	- **Teste**
		- Testa o modelo após o treinamento
- Diretrizes de divisão
	- Não existe regra exata
	- Depende do tamanho do conjunto de dados
	- Algumas diretrizes comuns
		- 70/30
		- 80/20
		- 60/20/20
		- **k-fold**
			- Divide os dados em k dobras (k folds)
			- Executa o treinamento do modelo k vezes
			- Em cada treinamento um conjunto é utilizado como validação, os demais (k-1) como treinamento
> [!note] 🔥
> A validação cruzada K-fold é um dos métodos que podem ser utilizados na detecção da ocorrência de sobreajuste.

# Avaliação de desempenho do modelo

- Neste ponto, os dados de validação são utilizados para avaliar o quão distante os valores previstos estão dos valores reais
- Calcula-se a perda ou loss. Também conhecida por distância (especialmente em mineração de dados)
- Principais abordagens para cálculo da distância:
	- Distância de Manhatan
	- Distância euclidiana
	- Ambas calculam a distância entre dois pontos em um plano multidimensional
	- Porém diferem na maneira de como é calculado e na interpretação dos dados

## Distância de Manhatan

- Soma das diferenças absolutas entre as coordenadas dos pontos em cada dimensão.
- Se assemelha à distância que uma pessoa percorreria em uma cidade em que os quarteirões são organizados em uma grade.
- $Distância de Manhatan = |x2 - x1| + |y2 - y1|$

## Distância Euclidiana

- Linha reta entre dois pontos
- Teorema de pitágoras
- $Distância Euclidiana = \sqrt{(x2-x1)^2+(y2-y1)^2}$

# Algumas técnicas de avaliação de desempenho

- Pontuação $R^2$
- Erro médio absoluto (EMA)
- Erro médio quadrático (EQM)
- Erro médio logarítmico quadrático (ELMQ)
- Matriz de confusão
	- Para modelos de classificação
	- Estruturada da seguinte forma: 

| **Verdadeiros positivos** | **Falsos positivos** |
| --- | --- |
| **Falsos negativos** | **Verdadeiros negativos** |

	- **Falsos positivos = Erros do tipo 1**
	- **Falsos negativos = Erros do tipo 2**

## Acurácia

- Somente é adequado para dados balanceados
	- Por exemplo: considere um estudo em que apenas 5% da população apresenta uma determinada doença. Logo, temos um conjunto de dados desbalanceado. Se o modelo escolhido conseguir classificar corretamente todas as pessoas que não têm a doença e errar a classificação de todos os doentes, teremos uma acurácia de 95%, dando uma falsa impressão de que o modelo treinado tem uma ótima previsão. Porém, o modelo não consegue classificar corretamente a classe de interesse.

![[Untitled 100.png]]

## Valor Preditivo Negativo (VPN)

![[Untitled 101.png]]

## Precisão ou Valor Preditivo Positivo (VPP)

![[Untitled 102.png]]

## Recall (Sensibilidade)

- Proporção de verdadeiros positivo dentre o total

![[Untitled 103.png]]

## Precision (Especificidade)

- Proporção de verdadeiros negativos dentre todas as observações que realmente são negativas

![[Untitled 104.png]]

## F1 - Score

- Avalia o equilíbrio entre precisão e sensibilidade

![[Untitled 105.png]]

## Curva ROC

- Curva formada pelo plano cartesiano de (1 - Especificidade) x Sensibilidade
- Especificidade
	- Representa a capacidade do modelo prever a classe negativa corretamente
- (1 - Especificidade)
	- Representa a capacidade do modelo de prever a classe negativa incorretamente
	- Quanto menor este valor, melhor
- Sensibilidade
	- Capacidade do modelo de prever a classe positiva corretamente
	- Quanto maior este valor, melhor

![[Untitled 106.png]]

- AUC
	- Área abaixo da curva
	- Varia entre 0 e 1
	- Quanto maior o AUC, melhor o modelo

# Hiperparâmetros vs parâmetros

![[Untitled 107.png]]

- **Hiperparâmetros**
	- Configurações que não são aprendidas pelo modelo durante o treinamento
	- Taxa de aprendizado em redes neurais, número de árvores em modelo de floresta aleatória
	- São os parâmetros de nível superior que você define manualmente antes de iniciar o treinamento, que se baseiam em propriedades como as características dos dados e a capacidade de aprendizado do algoritmo
- **Parâmetros**
	- Valores aprendidos pelo modelo
	- Pesos em redes neurais, coeficientes em regressão linear

# Generalização vs overfitting

- **Generalização**
	- Capacidade do modelo se sair bem com dados não vistos
	- Capacidade de extrapolação para além dos dados utilizados no treinamento
- Overfitting
	- Ocorre quando o modelo se ajusta demais aos dados de treinamento
	- Captura inclusive ruídos e detalhes irrelevantes
	- Leva a um mal desempenho em dados não vistos

# Modelos

- **Regressão linear**
	- Busca estabelecer uma relação linear entre uma variável de entrada e uma de saída
	- Usadas para prever **valores contínuos**
- **Regressão logística**
	- Semelhante à regressão linear
	- Utilizada para problemas de **classificação binária**
	- Exemplo: Anti-SPAM
- **Árvores de decisão**
	- Dividem os dados em segmentos menores com base em regras de decisão simples
	- Utilizado em problemas de **classificação e regressão**
- **Florestas aleatórias**
	- Cria várias árvores de decisão e combina suas previsões para obter uma previsão final
	- Ajuda a **reduzir o overfitting**
- **Máquinas de vetores de suporte (SVM)**
	- Encontra o hiperplano que melhor separa as classes em um espaço de alta dimensão
	- Usado em problemas de **classificação** com conjunto de **dados complexos**
- **Redes neurais artificiais (ANN)**
	- Usadas em uma ampla variedade de problemas
- **Redes neurais convolucionais (CNN)**
	- Usado em dados com **estrutura de grade** (imagens)
	- Usado em visão computacional
- **Redes neurais recorrentes**
	- Projetado para lidar com dados sequenciais como **séries temporais ou texto**
	- Conexões que formam loops
![[Untitled 108.png]]

# Underfitting, overfitting e técnicas de regularização

- Técnicas para evitar overfitting
	- Simplificar o modelo: menor número de parâmetros
	- Aumentar o conjunto de treinamento
	- Reduzir ruído no conjunto de treinamento: Remover erros, remover outliers
	- **Validação cruzada**
		- Consiste em dividir o conjunto de dados em duas partições
		- 70/30
		- 80/20
		- 60/20/20
		- **k-fold**
			- Divide os dados em k dobras (k folds)
			- Executa o treinamento do modelo k vezes
			- Em cada treinamento um conjunto é utilizado como validação, os demais (k-1) como treinamento
- Técnicas para evitar o underfitting
	- Utilização de um modelo mais poderoso, com mais parâmetros
	- Engenharia de recursos: melhores dados de entrada para treinamento
	- Redução de restrições do modelo

![[Untitled 109.png]]

# Algoritmos de aprendizado

## KNN

- Algoritmo de aprendizado supervisionado
- Concentra-se em encontrar os k vizinhos mais próximos de um dado valor

![[Untitled 110.png]]

- Na ilustração, S seria o conjunto de estrelas e triângulos já classificados. A interrogação representa um elemento do conjunto R que será classificado. Precisamos decidir se classificá-lo como um elemento da classe A (estrela) ou classe B (triângulo). Para isso, precisamos de um valor de K. Se K for igual a 1, o elemento mais próximo da interrogação determinará a classe à qual o novo elemento será classificado
- Para determinar os vizinhos mais próximos, calcula-se a distância
	- Distância euclidiana (linha reta)
	- Distância de hamming (soma das arestas)
	- Distância manhatan

## Árvores de Decisão

- C4.5 ou ID3
- semelhante a um monte de instruções if-else
- É adequado para uso em grandes quantidades de dados
- quando a árvore fica complexa, há uma grande chance de que o modelo se ajuste demais aos dados de treinamento (Overfitting)
- Alguns dos hiperparâmetros podem ajudar a reduzir essa complexidade
- cada nó representa uma pergunta ou uma condição sobre os dados
- cada galho representa o resultado dessa pergunta
- terminando em folhas que indicam as decisões finais ou classificações.
- **Entropia**
	- quantidade de desordem ou incerteza
	-  usada para determinar o quão bem uma pergunta ou condição separa os dados em diferentes classes
	- mede o **grau de incerteza** associado aos dados e quantifica o valor da informação contida nas respostas das perguntas formuladas.

## Florestas Aleatórias

- combina várias árvores de decisão para criar uma "floresta".
- vários modelos não correlacionados (as árvores de decisão individuais) têm um desempenho muito melhor como um grupo do que sozinhos
- cada árvore dá uma classificação ou um “voto”
- A floresta escolhe a classificação com a maioria dos “votos”
- Ao usar Random Forest para regressão, a floresta escolhe a média dos resultados de todas as árvores.
- cada árvore na floresta é treinada em uma **amostra aleatória dos dados** e considera apenas um **subconjunto das características em cada divisão**, é menos sensível a valores extremos do que métodos lineares, por exemplo.
- Para gerar árvores aleatórias, se o processo de construção for **determinístico:**
	- podem ser obtidas por meio do bootstrap dos dados
	- O **bootstrap** é uma técnica estatística que envolve amostragem com reposição. 
	- Ou seja, ao criar diferentes conjuntos de dados de treinamento, as amostras são selecionadas aleatoriamente e permitem repetições, formando novos conjuntos de dados chamados *bootstrap samples*.
	- Cada árvore na floresta é treinada com um desses conjuntos amostrados, resultando em variações que contribuem para a robustez e precisão do modelo final.
- O algoritmo Random Forest **não atribui a mesma importância para todas as variáveis ao fazer predições**. 
- Ele utiliza uma técnica chamada "feature importance" (importância das variáveis) para determinar **quais variáveis têm maior influência nas predições do modelo.**
- Vantagens:
	- Fácil de usar
	- Eficiência
	- Precisão
	- Versatilidade - pode ser usado para classificação ou regressão
	- Mais amigável para iniciantes do que algoritmos de precisão semelhante, como redes neurais
	- capacidade de lidar com valores atípicos ou outliers de forma robusta

## Máquinas de Vetores de Suporte (SVM)

- Combinação de KNN com regressão linear
- Separa os pontos em duas regiões homogêneas, separadas por um hiperplano
- Em duas dimensões, a tarefa do algoritmo SVM é identificar uma linha que separa as duas classes.
- Utilizados para classificação binária

![[Untitled 111.png]]

- Quando existe mais de uma possibilidade de criação do hiperplano, o algoritmo irá buscar pelo hiperplano que crie a maior separação entre as classes: **Hiperplano de margem máxima (MMH)**

![[Untitled 112.png]]

- Vetores de suporte são caracterizados pelos pontos de cada classe que encontram-se mais próximos do MMH

![[Untitled 113.png]]

- O desempenho do algoritmo Support Vector Machines (SVM) pode ser influenciado pela escala dimensional dos conjuntos de dados. Portanto, a padronização e o pré-processamento dos dados são geralmente recomendados ao usar o SVM.
- **Kernels**
	- funções matemáticas utilizadas para transformar dados não linearmente separáveis em um espaço de dimensionalidade mais alta onde se tornam linearmente separáveis.
	- A ideia central dos kernels é aplicar uma transformação não linear aos dados, permitindo que o SVM encontre um hiperplano de separação ótima em um espaço de dimensão mais alta.
	- Tipos comuns
		- kernel linear
		- kernel polinomial
		- kernel gaussiano
		- kernel sigmoide
- A técnica que auxilia na prevenção do overfitting em máquinas de vetor de suporte (SVM) é a utilização de um kernel linear.
- Um kernel linear é uma opção simples que pode ajudar a evitar o overfitting, especialmente quando os dados são linearmente separáveis ou aproximadamente linearmente separáveis.

## Redes Neurais

- Perceptron: Rede neural de camada única

![[Untitled 114.png]]

- Universalidade das redes neurais:
	- Pode representar qualquer problema que possa ser descrito por uma função matemática
- Altamente escalonável e flexível
- São compostas por:
	- Uma camada de entrada
	- Uma camada de saída
	- Uma quantidade arbitrária de camadas ocultas
	- Um conjunto de pesos e vieses entre cada camada
	- Uma função de ativação
- Etapas do processo de treinamento:
	- Cálculo da saída prevista y (Feedforward)
	- Atualização dos pesos e vieses (Backpropagation)
![[Untitled 115.png]]

### Tipos de Redes Neurais

- **Perceptron simples**
	- uma única camada de nós (neurônios)
	- Cada nó usa uma função de ativação para transformar uma combinação linear dos inputs em uma saída.
	- Utilizado para problemas de classificação binária simples
- **Perceptron multicamadas (MLP)**
	- Consiste em uma ou mais camadas ocultas entre a camada de entrada e a camada de saída.
	- Cada camada é totalmente conectada à próxima.
	- **Aplicação**: Classificação, regressão e outras tarefas onde é possível mapear entradas para saídas através de **funções não lineares**.
- **Redes Neurais Convolucionais (CNN)**
	- Especialmente eficazes para processamento de dados estruturados em grade, como **imagens**.
	- processam imagens como **tensores** e **tensores** são matrizes de números com várias dimensões
	- Utilizam camadas de convolução e pooling para extrair características dos dados.
	- **Aplicação**: Visão computacional, reconhecimento de imagem, processamento de vídeo.
- **Redes Neurais Recorrentes (RNN)**
	- Projetadas para processar dados sequenciais, onde a saída de uma etapa é usada como entrada para a próxima etapa.
	- RNNs têm "memória" ao longo das sequências.
	- Ao contrário das redes **feedforward**, em que as saídas dos neurônios de uma camada conectam-se apenas com os neurônios da próxima camada, nas RNN as saídas dos neurônios de uma camada podem conectar-se com ela mesma ou até mesmo com a camada anterior
	- O sinal percorre a rede nas duas direções, o que provê capacidade de memória
	- **Aplicação**: Processamento de** linguagem natural**, tradução automática, previsão de **séries temporais**.
- **Long Short-Term Memory (LSTM)**
	- Tipo especial de RNN com memória de longo prazo
	- **Aplicação**: Processamento de linguagem natural, tradução automática, previsão de séries temporais, reconhecimento de fala.
- **Redes Neurais de Contra propagação (Backpropagation Networks)**
	- Algoritmo de treinamento para redes neurais feedforward, onde os erros são retro propagados através da rede para ajustar os pesos.
	- Utilizado em MLPs para ajustar os pesos durante o **treinamento**.
- **Redes Neurais Generativas Adversariais (GAN)**
	- Consiste de **duas redes** (uma geradora e a outra discriminadora) que competem entre si
	- A geradora cria dados falsos tentando enganar a discriminadora
	- **Aplicação**: **Geração de imagens, síntese de texto, geração de música, aprimoramento de imagens.**
- **Transformers**
	- Utilizam mecanismos de atenção para processar dados sequenciais, permitindo a captura de dependências de longo alcance sem a necessidade de processamento sequencial.
	- aprende o contexto e, assim, o significado com o monitoramento de relações em dados sequenciais como as palavras desta frase.
	- É uma arquitetura de deep learning
	- tornaram possível o aprendizado **autossupervisionado**
	- Antes da chegada dos transformers, os usuários tinham que treinar redes neurais com grandes conjuntos de dados rotulados caros e demorados para produzir.
	- Ao encontrar padrões entre elementos matematicamente, os transformers eliminam essa necessidade, disponibilizando os trilhões de imagens e petabytes de dados de texto na web e em bancos de dados corporativos.
	- a matemática que os transformers usam pode ser usada também no processamento paralelo para que esses modelos sejam executados rapidamente.
	- Tradução automática, processamento de linguagem natural, tarefas de visão computacional.

### Treinamento de redes neurais

- [https://guiadehospedagem.com.br/glossario/o-que-e-backpropagation-vs-stochastic-gradient-descent/](https://guiadehospedagem.com.br/glossario/o-que-e-backpropagation-vs-stochastic-gradient-descent/)
- Aprendizado Hebbiano
- Aprendizado competitivo
- **Backpropagation**
	- Permite que as RNP aprendam a partir de dados de treinamento e melhorem seu desempenho
	- Atualiza os pesos das conexões entre os neurônios visando minimizar a diferença entre as saídas previstas e as reais
	- Baseado no princípio do **gradiente descendente** ou **descida de gradiente estocástica**

### Funções de Ativação

- **ReLU**
	- é uma das funções de ativação mais usadas em redes neurais artificiais, especialmente em redes neurais profundas.
	- Para qualquer valor de entrada x, se x for positivo, a função retorna x (ou seja, o valor é mantido).
	- Se x for negativo ou zero, a função retorna 0.
	- Embora pareça simples, a ReLU introduz uma **não linearidade **nas redes neurais, o que é essencial para que a rede aprenda e represente funções complexas
- **Sigmoid**
![[image 55.png]]
	- Mapeia os valores de entrada para um intervalo entre 0 e 1
	- usada principalmente em problemas de classificação binária, onde a saída precisa ser interpretada como uma probabilidade.
- **Tanh**
![[image 56.png]]
	- Mapeia os valores de entrada para um intervalo entre -1 e 1
	- É semelhante à função sigmoide, mas centrada em torno de zero, o que ajuda a tornar o aprendizado mais eficiente em alguns casos.
- **Leaky ReLU**
	- Uma variação da ReLU, que permite um pequeno gradiente para valores negativos de x. 
	- Isso mitiga o problema de "neurônios mortos" encontrado na ReLU.

### Outros conceitos

- **Dropout:** técnica de regularização usada em redes neurais para evitar o sobreajuste (overfitting) durante o treinamento

## Naive Bayes

- Baseado em probabilidade condicional (teorema de Bayes)
- O algoritmo Naïve Bayes é frequentemente usado para **classificação **e tarefas de **análise de texto**, mas não é especificamente voltado para mostrar ou prever a relação entre duas variáveis. 
- **Naive Bayes pode ser aplicado a qualquer tipo de atributo, incluindo categóricos, binários e contínuos.**
- Ele é mais adequado para tarefas de classificação baseadas em probabilidade condicional.
- Probabilidade de um evento ocorrer dado que outro já ocorreu
- O modelo classificador de Bayes é chamado ingênuo porque ignora correlações entre os recursos
- Usado em filtros de SPAM, sistemas de recomendação, análise de sentimento
- O objetivo do Naive Bayes é classificar instâncias de dados com base nas probabilidades dos atributos observados.
- Para isso, considera 3 tipos de eventos
	- **Eventos independentes**: Não afetam a probabilidade de ocorrência um do outro
	- **Eventos dependentes**: A ocorrência de um afeta a probabilidade de ocorrência do outro
	- **Eventos mutuamente exclusivos**
- Tipos de classificadores
	- **Multinomial Naive Bayes**
		- Classificação de documentos
		- Os recursos normalmente são a frequência das palavras existentes no documento
	- **Bernoulli Naive Bayes**
		- Semelhante ao multinomial, porém os preditores são variáveis booleanas
	- **Gaussian Naive Bayes**
		- Usado quando os preditores assumem valores contínuos (não discretos)
		- Assumem que a distribuição dos preditores assumem uma distribuição normal (gaussiana)

# Regressão

## Regressão linear

- Relação entre uma variável dependente (resposta) e N variáveis independentes (preditoras)
- A regressão linear supõe que a relação entre as variáveis seja uma linha reta (linear)
- $Y=β0+β1X1+β2X2+...+βnXn+ϵ$, onde Y é a variável dependente, $\beta_0$ é o intercepto, $\beta_1, \beta_2, ..., \beta_n$ são os coeficientes das  variáveis independentes $X_1, X_2, ..., X_n$ e $\epsilon$ é o termo de erro.
- $β0 = Coeficiente Linear$
- $βn = Coeficiente Angular$ ou intercepto
- O objetivo da regressão linear é estimar os valores dos coeficientes $\beta$ que minimizem a diferença entre os valores observados e os valores previstos pelo modelo
- Utiliza técnicas de otimização
- Quando tempos mais de uma variável independente (coeficiente $\beta$) é dito **regressão linear múltipla**

### Correlação vs Causalidade

- O fato de duas variáveis terem uma correlação (seja ela positiva ou negativa) **não significa que a mudança em uma variável seja a causa da mudança na outra**. 
- Este princípio é fundamental porque, em Machine Learning, pode-se identificar facilmente padrões correlacionais, mas isso **não atesta uma relação de causa e efeito **entre as variáveis. 
- A interpretação dos coeficientes angulares (os pesos atribuídos às variáveis independentes em uma regressão linear, por exemplo) é complicada pela necessidade de considerar que podem **existir outros fatores não incluídos no modelo** que influenciem as variáveis de interesse.

## Regressão Logística

- A variável dependente é categórica (binária)
- Prevê a probabilidade de ocorrência de um evento

## Regressão Linear Polinomial

- São utilizados polinômios de grau maior que 1

## Regressão Ridge e Lasso

- Técnicas que permitem a regularização para evitar overfitting
- Ridge adiciona penalidades baseado na magnitude dos coeficientes individuais
- Lasso adiciona penalidades baseado na soma da magnitude dos coeficientes

## Redes Neurais para regressão

- Camadas de entrada: O número de neurônios na camada de entrada deve ser igual à quantidade de variáveis independentes
- Camadas ocultas: Mais camadas aumentam a capacidade da rede modelar relações complexas, porém aumenta o risco de overfitting
- Camada de saída: Corresponde à variável dependente, normalmente 1 neurônio

# Ensamble

- Combinação de múltiplos modelos de base para melhorar o desempenho preditivo
- A ideia central do ensemble é que, ao combinar os resultados de múltiplos modelos (que podem ter diferentes pontos fortes e fracos), o desempenho geral pode ser melhorado em comparação com qualquer modelo individual.

## Técnicas

### Bagging (bootstrap Aggregation)

- Envolve a criação de múltiplas versões de um modelo de aprendizado ao treinar cada versão em um subconjunto aleatório do conjunto de dados original.
- As previsões finais são obtidas pela média (em regressão) ou votação majoritária (em classificação) das previsões de todos os modelos.
- Exemplo: Random Forest é um algoritmo popular que utiliza bagging com árvores de decisão.

## Boosting

- Constrói modelos sequencialmente, onde cada modelo novo tenta corrigir os erros cometidos pelos modelos anteriores.
- Os modelos são treinados de forma a dar mais peso aos exemplos que foram preditos incorretamente pelos modelos anteriores.

## Stacking

- Combinação de múltiplos modelos base (nível 0) usando um modelo meta (nível 1).
- As previsões dos modelos base são usadas como entradas para o modelo meta, que faz a previsão final.

---

# Aprendizado Não Supervisionado

- Por que usar?
	- Rotular grandes conjuntos de dados é caro
	- Pode haver casos em que não se sabe em quantas/quais classes os dados podem estar divididos
- Categorias
	- Paramétrico
		- Assume uma distribuição paramétrica dos dados
		- Se a média e desvio padrão são conhecidos, a probabilidade de qualquer observação futura pode ser estabelecida
	- Não paramétrico
		- Dados agrupados em clusters

## Redução da dimensionalidade

- Muitos recursos (dimensões) dificultam o treinamento
- Retira atributos que não são relevantes para a análise
- Melhora a compreensão dos dados e a sua estrutura
- Ao reduzir o número de recursos, o problema torna-se mais facilmente tratável
- Normalmente esta redução causa alguma perda de informação (exemplo: compactação de imagens JPEG)
- Porém também é útil para filtragem de ruído

### Projeção

- Abordagem de redução de dimensionalidade
- Muitas vezes os dados não estão bem distribuídos em todas as dimensões, em uma delas, tendem a estar bem próximos, formando uma superfície.
- Ao remover ou transformar esta dimensão, temos uma projeção dos dados nas demais dimensões

### Principal Component Analysis (PCA)

- Algoritmo de redução de dimensionalidade mais popular
- não é usada para agrupamento, mas sim para encontrar uma representação de menor dimensionalidade dos dados, preservando ao máximo a variância original.
- A PCA transforma as variáveis em novos eixos ortogonais (não correlacionados) que capturam a maior variação possível nos dados. 
- É também conhecida como **transformada de ****Karhunen-Loève (KLT)** ou **transformada ortogonal de Hotelling**. 
- Ele **não é adequado para agrupamento de dados sem rótulos.**
- Identifica o hiperplano mais próximo dos dados e os projeta nele
- Para a escolha da quantidade de dimensões a serem reduzidas, deve-se escolher o número de dimensões que somem a maior parte da variância dos dados, por exemplo, 95%
- A primeira componente principal captura a maior parte da informação contida nos dados (**Variância**), permitindo reduzir a dimensionalidade do conjunto de dados mantendo o máximo de informação possível.
- Exemplo:
	- A quilometragem de um carro pode estar fortemente correlacionada com sua idade, então o algoritmo de redução de dimensionalidade irá mesclá-los em um recurso que representa o desgaste do carro. Esse método é chamado de extração de recurso.
- A redução da dimensionalidade **produz novos dados** que capturam as informações mais importantes contidas nos dados de origem. Em vez de agrupar dados em clusters enquanto retêm os dados originais, esses algoritmos transformam os dados com o objetivo de usar menos recursos para representar as informações originais.

## Clusterização

- Organizar dados em grupos cujos membros sejam semelhantes de alguma forma
- As distâncias internas (dentro do cluster) devem ser pequenas, ou seja, os membros dos clusters são próximos/semelhantes entre si.
- As distâncias externas devem ser grandes, ou seja, os membros de diferentes clusters são diferentes.
- Os 4 algoritmos de clustering mais utilizados são:
	- k-means
	- Fuzzy k-means
	- Agrupamento hierárquico
	- Mistrura de Gaussianos

### K-means

- Agrupa os dados em k clusters
- A ideia principal é definir os centros de cada cluster, de forma que estejam o mais longe possível um dos outros
- Uma maneira popular de começar é escolher aleatoriamente k das amostras.
- Para isso é feito um loop composto dos seguintes passos
	- 1 - Cada dado é associado ao centro mais próximo
	- 2 - k novos centróides são calculados como baricentros (médias - mean) dos clusters resultantes da etapa anterior
	- 3 - Volta ao passo 1
- Este loop é executado indefinidas vezes até que os centróides parem de se move entre uma rodada e outra

### Fuzzy K-means

- Semelhante ao k-means, porém a divisão não é discreta: cada ponto tem uma probabilidade de pertencer a cada cluster
- A distância é substituída por probabilidade
- Os clusters resultantes são distribuições probabilísticas

### Agrupamento hierárquico

- Começa atribuindo a cada item do conjunto um cluster individual
- Em seguida, encontra o par de clusters mais próximos e os mescla em um único
- As distâncias são recalculadas
- Repetem-se os dois passos anteriores até sobrar um único cluster
- Esse método é especialmente útil quando se deseja identificar estruturas hierárquicas nos dados, subdividindo grupos em subgrupos menores

![[Untitled 116.png]]

### Mistura de Gaussianas

- Similar ao Fuzzy K-means
- Os clusters são definidos como distribuições gaussianas
- Cada ponto irá receber uma probabilidade de estar em um cluster ou em outro

### Problemas associados a agrupamento (clustering)

- Alta complexidade ao se lidar com muitas dimensões
- A eficácia depende da definição de distância
- O resultado do algoritmo pode ser interpretado de diferentes maneiras

# Aprendizado por Transferência Transdutiva

- Utiliza o aprendizado adquirido em um domínio em outro, para uma mesma tarefa
- Une os conceitos de dois tipos de aprendizado:
- **Aprendizado Transdutivo**: 
	- Refere-se a cenários onde o objetivo é fazer previsões em um conjunto específico de exemplos de teste, em vez de generalizar para novos exemplos não vistos. 
	- Em aprendizado transdutivo, os dados de teste estão disponíveis durante o treinamento, mas sem rótulos. 
	- O modelo é treinado de forma a otimizar seu desempenho nos exemplos de teste conhecidos.
- **Aprendizado por Transferência**: 
	- Consiste em utilizar o conhecimento adquirido em uma tarefa ou domínio (fonte) para melhorar o desempenho em uma tarefa ou domínio diferente (alvo).
- **Aprendizado por Transferência Transdutiva**: 
	- Combina esses conceitos, aplicando técnicas de aprendizado por transferência em um contexto transdutivo. 
	- O modelo tenta transferir o conhecimento de um domínio fonte para o domínio alvo, enquanto ajusta suas previsões com base nas informações disponíveis nos exemplos de teste do domínio alvo.
- **Domínios Fonte e Alvo**: 
	- Em aprendizado por transferência transdutiva, os dados de treinamento (domínio fonte) e de teste (domínio alvo) podem ter distribuições diferentes, mas a tarefa (por exemplo, classificação) permanece a mesma.
- **Vantagens**:
	- Permite que o modelo aproveite conhecimento previamente adquirido, economizando recursos computacionais e dados rotulados.
	- Pode melhorar a performance em domínios onde há poucos dados rotulados disponíveis.
- **Desafios**:
	- A transferência de conhecimento pode ser difícil se as distribuições de dados entre os domínios forem muito diferentes.
	- Requer métodos sofisticados para garantir que a adaptação do modelo para o domínio alvo seja eficaz.

# Stable Diffusion

- Modelo de aprendizado misto entre supervisionado e não supervisionado
- É capaz de gerar imagens a partir de texto ou de outras imagens
- Utiliza redes neurais convolucionais (CNN), recorrentes (RNN) e transformers

# Visão computacional

- Visão computacional vs Processamento de imagens
	- O processamento de imagens usa algoritmos para alterar imagens, incluindo nitidez, suavização, filtragem ou aprimoramento. 
	- A visão computacional é diferente, pois não altera uma imagem, mas dá sentido ao que vê e realiza tarefas, como a rotulagem. 
	- Em alguns casos, você pode usar o processamento de imagem para modificar uma imagem para que um sistema de visão computacional possa entendê-la melhor. 
	- Em outros casos, você usa a visão computacional para identificar imagens ou partes de uma imagem e, em seguida, usa o processamento de imagem para modificá-la ainda mais.

# Ontologia

- representação formal de um conjunto de conceitos e suas relações dentro de um domínio específico.
- As ontologias são usadas para modelar o conhecimento de forma que possa ser compreendido e processado por sistemas de informação.

### Componentes de uma Ontologia em Ciência da Computação

1. **Classes (ou Conceitos)**: Representam conjuntos de entidades ou objetos no domínio de interesse.
2. **Indivíduos (ou Instâncias)**: Representam objetos específicos que pertencem às classes.
3. **Propriedades (ou Atributos)**: Características ou qualidades que os indivíduos podem ter.
4. **Relações**: Conexões entre as classes ou indivíduos que expressam como eles se relacionam.
5. **Axiomas**: Declarações que são sempre verdadeiras no domínio, usadas para definir regras e restrições sobre as classes e relações.

[https://carl-mcbride-ellis.github.io/TOBoML/TOBoML.pdf](https://carl-mcbride-ellis.github.io/TOBoML/TOBoML.pdf)

# Machine Learning vs Deep Learning

- Deep Learning é um subconjunto de Machine Learning
- Baseia-se em **redes neurais artificiais profundas**, que possuem muitas camadas (muitas vezes dezenas ou até centenas) e são capazes de aprender representações de dados em vários níveis de abstração.
- Exige **grandes quantidades de dados **e **poder computacional significativo** (como GPUs) para treinar modelos, mas é extremamente eficaz em lidar com grandes volumes de dados complexos, como imagens, vídeos e textos.
- As redes neurais profundas são capazes de **aprender automaticamente representações relevantes dos dados (features) **nas suas camadas intermediárias. Isso reduz ou até elimina a necessidade de engenharia de features manual.
- **Machine Learning Tradicional**: Funciona bem para tarefas específicas e relativamente simples, mas pode não ser eficaz para tarefas que envolvem dados **não estruturados** ou de **alta dimensionalidade**, como imagens, áudios e textos.
- **Deep Learning**: É particularmente potente em tarefas complexas e de alta dimensionalidade, como reconhecimento de voz, visão computacional, processamento de linguagem natural, onde modelos tradicionais podem falhar.
- **Deep Learning**: Utiliza métodos avançados de otimização, como **descida de gradiente** estocástica com **retropropagação**, e funções de perda que podem ser bastante complexas, considerando o grande número de parâmetros das redes neurais profundas.

## Descida do Gradiente

[https://www.deeplearningbook.com.br/aprendizado-com-a-descida-do-gradiente/](https://www.deeplearningbook.com.br/aprendizado-com-a-descida-do-gradiente/)

- É o **backpropagation tradicional**
- Ferramenta de **otimização** de funções complexas de forma **interativa**
- Basicamente envolve encontrar o **ponto de mínimo** de uma **função**
- Pode ser o mínimo global ou mínimo local
- Descida do Gradiente é um algoritmo de otimização usado para encontrar os valores de parâmetros (coeficientes ou se preferir w e b – weight e bias) de uma função que minimizam uma função de custo.
- É melhor usada quando os parâmetros não podem ser calculados analiticamente (por exemplo, usando álgebra linear) e devem ser pesquisados por um algoritmo de otimização.
- Procedimento
	- Você divide seus dados em amostras e a cada amostra (sample), você passa as entradas pela rede, multiplica pelos pesos, soma, e no final você vai ter sua saÍda (a previsão da rede). 
	- Você então compara a saída da sua rede com o a resposta certa, calcula o erro, e então retroage esse erro (backpropagation), ajustando os pesos de cada neurônio de cada camada. 
	- Quando você acabar de fazer a atualização dos pesos, uma nova amostra é introduzida e ela será multiplicada pelos pesos já atualizados. 
	- Esse processo de atualizar os pesos é que é chamado de “aprendizado”.

## Descida do Gradiente Estocástica (SGD)

- Usa apenas um subconjunto dos dados de treinamento em cada iteração (mini-batch)
- Calcula o gradiente da função de perda apenas para esse mini-batch.
-  Em seguida, ele atualiza os pesos da rede neural na direção oposta ao gradiente calculado, de forma a minimizar a perda
- Esse processo é repetido para diferentes mini-batches até que todos os dados de treinamento tenham sido utilizados
- O backpropagation (Gradiente Descendente Tradicional) pode ser computacionalmente mais caro, especialmente quando se trabalha com grandes conjuntos de dados, pois requer o cálculo do gradiente para todos os dados de treinamento em cada iteração.
- **Por outro lado, o SGD é mais eficiente, pois usa apenas um subconjunto dos dados de treinamento em cada iteração.**

# LLM

- São modelos que utilizam** Deep Learning** para processar e entender a linguagem dos seres humanos
- Modelos
	- GPT
		- são auto-regressivos, gerando texto palavra por palavra
	- BERT
		-  (Bidirectional Encoder Representations from Transformers), são auto-encoders, que consideram todo o contexto ao mesmo tempo.
- Têm um grande número de parâmetros (milhões ou até bilhões), o que lhes permite capturar uma ampla gama de informações sobre a linguagem.
- Esses modelos são treinados em vastas quantidades de dados de texto, como livros, artigos, páginas da web, etc. 
- O treinamento é feito usando técnicas de aprendizado profundo, como redes neurais transformer.
- Contam ainda com um mecanismo de **atenção** que permite a eles **focar seletivamente em partes do texto**, de modo a identificar os trechos mais relevantes para fazer resumos, por exemplo.
- A arquitetura mais comum usada em LLMs é a de **transformers**, que utiliza mecanismos de atenção para processar e relacionar palavras em diferentes partes de um texto. 
- Essa arquitetura permite que os modelos capturem dependências de longo alcance e contextos complexos.

## Hiperparâmetros

### Temperature

- Controla a aleatoriedade ou a criatividade na geração de texto. 
- Ele afeta a distribuição de probabilidade das palavras que o modelo pode escolher durante a geração de texto.
- **Temperature Alta (>1)**: 
	- Aumenta a aleatoriedade. 
	- O modelo terá mais probabilidade de escolher tokens menos prováveis. 
	- Isso resulta em texto mais criativo e variado, mas também aumenta o risco de gerar **sequências menos coerentes.**
- **Temperature Baixa (<1)**: 
	- Diminui a aleatoriedade. 
	- Faz com que o modelo tenha maior propensão a escolher os tokens mais prováveis. 
	- Isso resulta em um **texto mais previsível e conservador**.
- **Temperature = 1**: 
	- Não altera a distribuição original das probabilidades, e o modelo seleciona palavras exatamente conforme as probabilidades calculadas.

### **Top-k Sampling**

- Controla a quantidade de **palavras mais prováveis** que são consideradas para escolha na geração de texto.
- Restringe suas opções às k palavras com as maiores probabilidades. 
- Um valor de **k = 50** significa que o modelo só pode escolher entre as 50 palavras mais prováveis.

### **Top-p Sampling (Nucleus Sampling)**

- Controla o conjunto de palavras a ser considerado durante a geração, com base em uma probabilidade acumulada.
- Em vez de fixar um número de palavras como no top-k, o top-p considera todas as palavras até que a soma das probabilidades atinja o valor de **p** (ex: 0,9). 
- Isso significa que o modelo só escolhe entre palavras que, juntas, somam 90% da probabilidade total.

### **Learning Rate (Taxa de Aprendizado)**

- **Defin**e o tamanho dos passos que o modelo dá ao ajustar os pesos durante o treinamento.
- Uma taxa de aprendizado alta pode acelerar o treinamento, mas arrisca saltar por cima do ótimo global, enquanto uma taxa de aprendizado baixa oferece um ajuste mais fino, porém mais lento. 
- Ajustar adequadamente a learning rate é crucial para a convergência do modelo.

### **Dropout Rate**

- Técnica de regularização que desativa aleatoriamente um percentual dos neurônios durante o treinamento para evitar overfitting.
- Um dropout rate mais alto ajuda a prevenir overfitting, mas pode dificultar o aprendizado se for excessivo. 
- Um valor comum está entre 0,1 e 0,5.

# MLOps

- Prática e conjunto de processos que combinam o desenvolvimento de modelos de aprendizado de máquina (ML) com operações de TI para gerenciar, implantar, monitorar e escalar modelos de ML de forma eficiente e sustentável em ambientes de produção.

### Principais Componentes e Conceitos do MLOps:

6. **Integração Contínua (CI) e Entrega Contínua (CD)**:
	- **CI/CD**: 
		- Processo de automação de testes e integração de novos códigos, dados e modelos em um repositório comum. 
		- A entrega contínua (CD) envolve a automação do processo de implantar novos modelos em produção de forma consistente e confiável.
7. **Gerenciamento de Modelos**:
	- **Versão de Modelos**: 
		- Assim como com o software, as versões dos modelos de ML precisam ser gerenciadas, especialmente à medida que novos dados e algoritmos são usados para melhorar os modelos existentes.
	- **Repositórios de Modelos**: 
		- Ferramentas específicas permitem armazenar, versionar e acessar diferentes versões de modelos, facilitando a rastreabilidade e o rollback, se necessário.
8. **Gerenciamento de Dados**:
	- **Pipeline de Dados**: 
		- MLOps envolve a construção de pipelines robustos para ingestão, processamento, e limpeza de dados. 
		- Dados precisos e atualizados são fundamentais para o sucesso dos modelos de ML.
	- **Data Versioning**: 
		- Versionar conjuntos de dados permite rastrear quais dados foram usados para treinar qual modelo, o que é crucial para auditorias e reproduzibilidade.
9. **Monitoramento e Manutenção de Modelos**:
	- **Monitoramento de Performance**: 
		- Uma vez que um modelo está em produção, é crucial monitorar sua performance ao longo do tempo, garantindo que ele continue a funcionar conforme o esperado. 
		- Mudanças nos dados de entrada (data drift) podem degradar a qualidade do modelo.
	- **A/B Testing e Shadow Deployment**: 
		- Técnicas para testar novos modelos em produção antes de substituir completamente o modelo existente, minimizando riscos de deploys errados.
10. **Automação e Orquestração**:
	- **Automatização de Pipelines**: 
		- Automatizar processos de treinamento, validação, e deploy de modelos permite uma iteração mais rápida e eficiente.
	- **Orquestração de Tarefas**: 
		- MLOps utiliza ferramentas de orquestração para gerenciar a execução de diferentes tarefas no pipeline, garantindo que as dependências sejam respeitadas e que as etapas ocorram na ordem correta.
11. **Segurança e Conformidade**:
	- **Gestão de Acessos**: 
		- Controle de acesso rigoroso para garantir que apenas usuários autorizados possam acessar dados sensíveis ou implantar modelos.
	- **Conformidade com Regulamentações**: 
		- As práticas de MLOps garantem que os modelos de ML estejam em conformidade com as regulamentações e políticas de privacidade de dados, como GDPR.
12. **Escalabilidade**:
	- **Escalabilidade Horizontal e Vertical**: 
		- MLOps aborda a necessidade de escalar o treinamento e a inferência de modelos de ML à medida que a demanda cresce.
	- **Gestão de Recursos**: 
		- Ferramentas de MLOps ajudam a gerenciar recursos computacionais de forma eficiente, otimizando o uso de hardware e software.
13. **Feedback e Iteração Contínua**:
	- **Ciclo de Vida do Modelo**: 
		- MLOps promove uma abordagem iterativa, onde os modelos são continuamente avaliados e atualizados com base em novos dados e feedback, assegurando que permaneçam eficazes ao longo do tempo.

### Ferramentas e Plataformas Comuns em MLOps:

- **Kubernetes**: Usado para orquestração de contêineres, essencial para implantar e escalar modelos de ML em produção.
- **TensorFlow Extended (TFX)**: Um conjunto de ferramentas para construir e gerenciar pipelines de ML.
- **MLflow**: Uma plataforma para gerenciar o ciclo de vida de modelos de ML, incluindo rastreamento de experimentos, versionamento de modelos, e deploy.
- **Kubeflow**: Plataforma para automatizar, gerenciar e escalar pipelines de ML em Kubernetes.
- **Data Version Control (DVC)**: Ferramenta para versionamento de dados e gestão de pipelines de ML.

# Algoritmos de Regularização

- Usados em Machine Learning para prevenir overfitting e melhorar a generalização
- Especialmente em regressão
- Adiciona um termo de penalização à função de custo do modelo, limitando a complexidade

## Principais Algoritmos

- Regressão Ridge (Regularização L2)
- Regressão Lasso (Regularização L1)
	- Pode forçar alguns coeficientes a zero, simplificando o modelo
- Elastic Net
	- Combinação de L1 e L2
- Regressão Least-Angle (LARS)
	- Similar ao Lasso, porém mais eficiente
