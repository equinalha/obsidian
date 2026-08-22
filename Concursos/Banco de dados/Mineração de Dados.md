---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2024-11-10T11:04:00
Owner:
  - Eduardo Quinalha
---
# Introdução

- Mineração de dados trata da solução de problemas, analisando dados já presentes
- Descoberta de padrões nos dados
- O processo deve ser automático ou (mais comumente) semiautomático.
- Os padrões descobertos devem ser significativos, pois levam a alguma vantagem competitiva
- Área ligada ao aprendizado de máquina
- é um processo, é iterativo, **requer supervisão.**
- Utiliza técnicas
	- Estatísticas
	- Aprendizado de máquina
	- Baseadas em crescimento-poda-validação

> [!note] 🔥
> Aprender sem propósito é apenas treinar

- Definição: 

> *é um conjunto de processos, métodos, teorias, ferramentas e tecnologias ****open-end**** utilizadas para explorar, organizar e analisar de forma semiautomática uma grande  quantidade de dados brutos com o intuito de**** identificar, descobrir, extrair, classificar e agrupar informações implícitas desconhecidas****, além de avaliar correlações, tendências e padrões consistentes de comportamento potencialmente úteis – como regras de associação ou sequências temporais – de forma não-trivial por meio de técnicas ****estatísticas e matemáticas****, como redes neurais, algoritmos genéticos, inteligência artificial, lógica nebulosa (fuzzy), análise de conglomerados (clusters), entre outros.*

- Mineração de dados multidimensional = mineração de dados multidimensional exploratória

# Objetivos 🔥

- **Previsão**
	- mostrar como certos atributos dos dados se comportarão no futuro
- **Identificação**
	- identificar a existência de um item, um evento ou uma atividade
- **Classificação**
	- particionar os dados de modo que diferentes classes ou categorias possam ser identificadas com base em combinações de parâmetros
- **Otimização**
	- otimizar o uso de recursos limitados, como tempo, espaço, dinheiro ou materiais e maximizar variáveis de saída como vendas ou lucros sob determinado conjunto de restrições.

![[Concursos/images/Untitled 67.png]]

# Tarefas de Mineração de Dados

- Especificação do que queremos buscar nos dados

![[Concursos/images/Untitled 68.png]]

## Classificação das técnicas

- Preditivas
	- Classificação
	- Regressão
	- Detecção de desvios
- Descritivas
	- Clustering
	- Regra de Associação
- Top-down
	- Parte-se de hipóteses
	- Utiliza-se data mining para comprovar ou refutar
- Botton-up
	- Parte-se da análise dos dados
	- Com data mining, descobre-se padrões e chega-se a conclusões

## Descrição das Técnicas

- Técnicas estatísticas
- Técnicas de Machine Learning
- Técnicas baseadas em crescimento-poda-validação
	- Árvore de decisão
	- A medida que a árvore vai crescendo, podem surgir inconsistências
	- Estes ramos devem ser podados

# Características dos conjuntos de dados

- Impactam as técnicas de mineração

> [!note] 🔥
> **DRD**

- Características
	- **Dimensão**
		- Quantidade de atributos
	- **Resolução**
		- Granularidade dos atributos
	- **Dispersão**
		- Quando para um atributo relevante a maioria dos valores é NULL ou um valor padrão

# Processo KDD (Knowledge Discovery in Database)

- Processo interativo e iterativo
- Envolve várias etapas com decisões tomadas pelo usuário

![[Concursos/images/Untitled 69.png]]

## **Seleção**

- é necessário desenvolver um conhecimento sobre o domínio da aplicação
- Restringe o conjunto de dados originais
- Trabalha-se apenas com os dados necessários para a análise em questão

## **Pré-processamento**

- Resolve os problemas que existem nos dados
![[Concursos/images/Untitled 70.png]]

### Técnicas

- Dados sem qualidade podem gerar uma mineração sem qualidade, que por consequência vão levar a decisões sem qualidade
- Se os dados estiverem duplicados ou faltantes podemos gerar cálculos estatísticos incorretos.
- Esta fase tende a consumir uma parte significativa do tempo dedicado ao processo de KDD
- **Limpeza dos Dados**
	- Preenche valores faltantes
	- suaviza dados ruidosos
	- identifica ou remove “outliers”
	- resolve inconsistências.
- **Integração**
	- Dados de origens diferentes devem ser integrados.
- **Transformação**
	- Normalização e agregação dos dados.
- **Redução**
	- Tenta reduzir o volume dos dados sem provocar alterações no resultado
	- Técnicas de redução de dados podem ser aplicadas tanto para reduzir a quantidade de objetos da base quanto para reduzir a quantidade de atributos que os descrevem (dimensionalidade)
	- Dentre os métodos de redução de dados destacam-se
		- Seleção de atributos
			- Elimina atributos irrelevantes para a análise
		- Compreensão de atributos
			- Emprega transformação destes atributos
		- Redução do número de dados
			- Dados removidos ou estimados
			- Podem ser substituídos por modelos paramétricos
		- Discretização
- **Discretização**
	- Faz parte do processo de redução
	- Visa estabelecer valores discretos para variáveis contínuas

## **Transformação**

- dados são transformados e consolidados em formas apropriadas à mineração, sumarizando-os ou agregando-os.

## **Mineração de dados**

# Processo CRISP-DM

- modelo de processos genéricos, com o intuito de padronizar as etapas do processo de mineração de dados.
- Cross Industry Standard Process for Data Mining
- Repartição em 4 níveis (Hierarquia):
	- **Fases (6 fases)**
		- Entendimento do Negócio
		- Entendimento dos dados
		- Preparação dos dados
		- Modelagem
		- Avaliação
		- Entrega
	- **Tarefas Genéricas**
		- geral o suficiente para cobrir todas as situações possíveis de mineração de dados
		- o mais completas e estáveis possível
		- o modelo deve ser válido para desenvolvimentos de modelos imprevisíveis
	- **Tarefas Especializadas**
		- é o local para descrever como as ações das tarefas genéricas devem ser realizadas em determinadas situações específicas.
	- **Instâncias de processos**
		- Representa o que realmente aconteceu em um determinado engajamento, e não o que acontece em geral

### Entendimento do Negócio

- Fase do CRISP-DM que visa obter conhecimento sobre os **objetivos do negócio** e seus requisitos.
- Procura Esboçar uma lista de **necessidades e expectativas **dos indivíduos envolvidos
- Fazer um levantamento do hardware e software existentes
- Fazer um inventário das bases de dados disponíveis
- Verificar a existência de Data Warehouses

### Entendimento dos dados

- se inicia com uma coleta inicial de dados
- Familiarização com os **dados**
- Compreender o significado e perceber a **relevância dos atributos/ dados disponíveis.**
- Avaliar a **qualidade dos dados **disponíveis.
- Verificar se os dados estão disponíveis em quantidade suficiente para o processo de KDD

### Preparação dos Dados

- Ações de pré-processamento dos dados para a fase de modelagem propriamente dita
- Corresponde a um processo ETL
- **Selecionar** os dados que serão efetivamente analisados
- Promover a **limpeza** dos dados
- **Integração** dos dados
- **Adequar** o formato dos dados
- **Construir** novos atributos a partir de atributos existentes.

### Modelagem dos Dados

- Escolha e aplicação da(s) técnica(s) de modelagem (algoritmo(s) de mineração) sobre os dados a serem analisados.
- Corresponde à etapa de Mineração de Dados do Processo de KDD
- A maioria das técnicas de mineração de dados é baseada em conceitos de aprendizagem de máquina, reconhecimento de padrões, estatística.
- Projeto de testes

### Avaliação do processo

- garantir que o modelo gerado atenda às expectativas da organização
- Nesta etapa, verificamos se o modelo construído possui qualidade, sob uma perspectiva da análise de dados.
- Rever as etapas executadas para construir o modelo, para se certificar de que ele conseguirá alcançar os objetivos de negócio\

### Entrega

- Definição das fases de implantação do projeto de Mineração de Dados
- A criação do modelo não é o fim do projeto
- Ações a serem realizadas com o(s) modelo(s) de conhecimento gerado(s) pelas fases anteriores.
- A fase de entrega pode ser tão simples quanto a geração de um relatório, ou tão complexo quanto executar processos de mineração de dados repetidamente.

![[Concursos/images/Untitled 71.png]]

# Técnicas

## Classificação

- Tarefa de mineração
- descrevem o grupo ao qual o item pertence por meio do exame dos itens já classificados e pela inferência de um conjunto de regras.
- Utiliza técnicas como árvores de decisão e redes neurais
- Modelo de data mining preditivo
- Consiste em encontrar uma função f que seja capaz de atribuir uma classe a uma determinada tupla de dados T com base em seus atributos
- Utiliza técnicas de separabilidade ou entropia, utilizando árvores de decisão e variantes, e em particionamento usando SVM

## Regressão

- Busca predizer um valor numérico
- Estabelece uma função que, dados os atributos de uma entidade de entrada, resulta em um valor real
- É uma técnica estatística

## Regras de Associação

- Relacionam a presença de um conjunto de itens com outra faixa de valores de outro conjunto de variáveis
- é um padrão da forma X → Y, onde X e Y são conjuntos de valores
- Exemplo:
	- “clientes que compram pão também compram leite”
- Medidas
	- **Suporte**
		- medida objetiva para avaliar o interesse de uma regra de associação.
		- Representa a **porcentagem de transações (%) (em relação ao total) onde a regra se verifica.**
		- quão frequente a regra acontece no banco de dados?
	- **Confiança**
		- mede o grau de certeza de uma associação
		- **probabilidade condicional P (Y | X)**, isto é, a porcentagem de transações contendo os itens de X que também contêm os itens de Y.
		- **Porcentagem de relações contendo o item X que possuem o item Y (em relação ao total que possui o item X)**
	- Exemplo:
![[Concursos/images/Untitled 72.png]]
		- {Arroz, Cerveja} → {Leite}:
			- Suporte = 0/5 = 0%
			- Confiança = 0%
		- {Feijão, Leite} → {Arroz}:
			- Suporte = 2/5 = 40%
			- Confiança = 2/4 = 50%
- Conjunto de itens grande (itemset)
	- Conjunto de itens que esteja acima dos limites estabelecidos para o **suporte **de uma regra de associação
	- Como determinar:
		- **Fechamento para baixo**
			- Qualquer subconjunto de uma ocorrência que já é grande, também será grande (normalmente ainda maior)
			- Exemplo:
				- Conjunto dos itens (a, b, c, d, e) ocorrem em 30% dos registros
				- Ao retirar um dos itens, a probabilidade é que existam mais ocorrências ainda
		- **Antimonotonicidade**
			- É o contrário do fechamento por baixo
			- Dado um conjunto de itens que já tem um suporte pequeno, ao adicionar mais itens, o suporte do superconjunto formado também será pequeno

## Agrupamento / Clusterização

- Encontrar grupos de objetos tal que objetos em um grupo são similares (ou relacionados) uns aos outros e diferentes de (ou não relacionados) a objetos em outros grupos.
- consiste em identificar agrupamentos de objetos.
- Baseia-se das medidas entre os elementos:
	- Distância do elemento até os centroides de cada cluster
	- Densidade
	- Distribuição
- Os algoritmos podem ser particionais ou hierárquicos

![[Concursos/images/Untitled 73.png]]

## Abordagens para outros problemas de mineração

- Análise de padrões sequenciais
- Análise de padrões em séries temporais
- Predição
- Análise de Outliers
	- em algumas aplicações, tais como detecção de fraudes, estes eventos raros podem ser mais interessantes do que eventos que ocorrem regularmente.
- Regressão
	- aplicação especial da regra de classificação
	- É utilizada uma equação para sumarizar ou descrever o relacionamento de um conjunto de dados, onde a análise de regressão pode ser empregada para ajustar a equação.
	- A análise de regressão pode auxiliar no processo de seleção de variáveis eliminando aquelas cuja contribuição não seja importante;
	- **tem como objetivos a sumarização, a predição, o controle e a estimação**

# Mineração de Texto

- processo que utiliza técnicas de análise e extração de dados a partir de textos, frases ou apenas palavras
- auxilia na descoberta de conhecimento inovador a partir de documentos textuais
- A mineração de texto segue, em última instância **o mesmo conjunto de etapas da mineração de dados e utiliza-se de um conjunto de técnicas comuns.**

## Ações

- Thesaurus
	- mapeia termos variantes – sinônimos, abreviações, acrônimos, e ortografias alternativas – para um termo preferido único para cada conceito.
	- informa que termos índices devem ser usados para descrever cada conceito
	- auxilia no fornecimento de um vocabulário padrão para indexação e pesquisa
- Case Folding
	- processo de converter todos os caracteres de um documento no mesmo tipo de letra – ou todas maiúsculas ou minúsculas.
	- Isso tem a vantagem de acelerar comparações no processo de indexação.
- Stop Words
	- raramente contribuem para o significado dessa sentença
	- Ocorrem em cerca de 80% do documento
	- potencialmente inúteis
	- não contribuem muito para a relevância de um documento para uma pesquisa
	- a remoção de stopwords de um documento deve ser realizada antes da indexação
- Stemming ou Lematização (Raízes)
	- A raiz ou radical de uma palavra é definida como a palavra obtida depois de remover o sufixo e o prefixo de uma palavra original.
	- O processo de stemming é realizado considerando cada palavra isoladamente e tentando reduzi-la a sua provável palavra raiz
	- algoritmos de stemming empregam linguística e são dependentes do idioma
	- Erros no processo de Stemming
		- Overstemming: acontece quando a cadeia de caracteres removida não era um sufixo, mas parte do stem. Isto pode resultar na conflação de termos não relacionados.
		- Understemming: acontece quando um sufixo não é removido. Isto geralmente causa uma falha na conflação de palavras relacionadas

# Detecção de Anomalias

- Dados anômalos podem sinalizar incidentes críticos que ocorrem em detalhes técnicos, como uma falha de infraestrutura, uma alteração significativa de uma fonte upstream ou ameaças à segurança.
- Pode ser utilizada:
	- em finanças para detecção de fraude
	- na fabricação para identificar defeitos ou mau funcionamento de equipamentos
	- em [cibersegurança](https://www.ibm.com/br-pt/topics/cybersecurity) para detectar atividades incomuns de rede, 
	- na saúde para identificar condições anormais de pacientes.
- Anomalias de dados podem ter um impacto significativo no campo da [ciência de dados](https://www.ibm.com/br-pt/topics/data-science), levando a conclusões incorretas ou enganosas.
- Motivos para lidar com anomalia de dados:
	- **Melhor qualidade de dados**
	- **Tomada de decisão aprimorada**
	- **Desempenho otimizado de aprendizado de máquina**

## Tipos de anomalias

### Gerais

- Não intencionais
	- Pontos de dados que se desviam da normal devido a ruído no processo de coleta de dados
	- Podem ser sistemáticos ou aleatórios
- Intencionais
	- Pontos de dados que se desviam devido a ações ou eventos específicos
	- podem destacar ocorrências ou tendências exclusivas

### Anomalias de séries temporais

- Pontuais
	- pontos de dados individuais que estão muito fora do restante do conjunto de dados
	- podem ser intencionais ou não intencionais e podem resultar de erros, ruídos ou ocorrências únicas.
- Contextuais
	- são pontos de dados que se desviam da norma dentro de um contexto específico
	- não são necessariamente valores discrepantes quando consideradas isoladamente, mas se tornam anômalas quando vistas dentro de seu contexto específico.
- Coletivas
	- conjunto de instâncias de dados que juntas se desviam da norma, mesmo que as instâncias individuais possam parecer normais.

## Métodos de detecção de anomalias

### Visualização

- é uma ferramenta poderosa para detectar anomalias, pois permite que os cientistas de dados identifiquem rapidamente possíveis valores discrepantes e padrões.
- Ao plotar os dados usando tabelas e gráficos, os analistas podem inspecionar visualmente o conjunto de dados em busca de quaisquer pontos ou tendências incomuns.

### Testes estatísticos

- podem ser usados por cientistas de dados para detectar anomalias comparando os dados observados com a distribuição ou padrão esperado.
- Exemplos
	- **teste de Grubbs** pode ser usado para identificar valores discrepantes em um conjunto de dados, comparando cada ponto com a média e o desvio padrão dos dados.
	- o teste de **Kolmogorov-Smirnov** pode ser usado para determinar se um conjunto de dados segue uma distribuição específica, como uma distribuição normal.

### Testes de normalidade

- Existe uma gama de testes que podem ser aplicados para garantir que os dados seguem uma distribuição normal.
- **Amplitude interquartil**
	- $L_s = Q_3 +1.5(Q_3-Q_1)$
	- $L_s = Q_1 +1.5(Q_3-Q_1)$
	- Este é o método utilizado para calcular dados discrepantes nos gráficos de boxplot.
	- Por utilizar a mediana, este método não é afetado por anomalias já presentes no conjunto de dados.
- **Z-Score**
	- $Z=\frac{x-\mu}{\sigma}$
	- se baseia na **distância, em desvio padrão (σ), entre o valor medido e a média (μ) dos dados**
	- Considerando que numa distribuição normal, 99,73% dos dados estão, tradicionalmente, na faixa entre 3 desvios padrões abaixo ou 3 desvios padrões acima da média, os dados fora desse intervalo são considerados anômalos.
	- Por utilizar a média no seu cálculo, o Z-Score **sofre influência de possíveis outliers já presentes no conjunto de dados**
- **Z-Score Modificado**
	- método considerado [robusto](https://pt.wikipedia.org/wiki/Estat%C3%ADstica_robusta), uma vez que ele utiliza a mediana em vez da média.
	- seu score não depende do número de observações no conjunto de dados

### Algoritmos de aprendizado de máquina

- podem ser usados para detectar anomalias, aprendendo o padrão subjacente nos dados e, em seguida, identificando quaisquer desvios desse padrão
- Principais algoritmos utilizados:
	- Árvores de decisão
	- Máquinas de vetores de suporte de classe única
	- K-NN
	- Naive Bayes
	- Autoencoders
		- tipo de [rede neural](https://www.ibm.com/br-pt/topics/neural-networks) que utiliza dados com registro de tempo para prever padrões de dados e identificar anomalias que não se alinham com os dados históricos. 
	- **Fator de outlier local (LOF)**
		- algoritmo baseado em densidade que mede o desvio de densidade local de um ponto de dados em relação aos seus vizinhos. Pontos com densidade significativamente menor em comparação com seus vizinhos são considerados valores discrepantes.
	- K-means

## Técnicas de detecção de anomalias

- não supervisionadas
	- exigem conjuntos de dados massivos e poder computacional
- supervisionadas
	- mais frequentemente encontrado em cenários [deep learning](https://www.ibm.com/br-pt/topics/deep-learning), que dependem de rede neural artificial.
- semi-supervisionadas
	- maximizam os atributos positivos da detecção de anomalias não supervisionadas e supervisionadas

# Processamento de Linguagem Natural (PLN)

[https://medium.com/computando-arte/1-3-classificando-textos-vetorização-ec8772738f3d](https://medium.com/computando-arte/1-3-classificando-textos-vetorização-ec8772738f3d)

- área da Ciência da Computação que estuda o desenvolvimento de programas computacionais que analisam, reconhecem e/ou geram textos em linguagens humanas, ou naturais.
- desafia as máquinas a lidar com a ambiguidade, a gramática, o contexto e a riqueza semântica da linguagem humana
- Objetivos
	- recuperação de informações a partir de textos
	- tradução automática
	- interpretação de textos e a realização de inferências a partir de textos

## Funcionamento

- Pré-processamento
	- Remoção de stop-words
	- Case-folding
	- Stemming
	- Remoção de palavras desnecessárias como artigos e preposições
- Tokenização
	- O texto é dividido em unidades menores, chamadas tokens
	- Podem ser palavras, frases e subpalavras
- Análises morfológicas, sintáticas ou semânticas

## Níveis de Reconhecimento

- Após o processamento inicial podem ser feitas análises no conjunto de dados. 
- **As análises praticadas no PLN estão relacionadas ao que chamamos de níveis de reconhecimento.**
- Níveis:
	- Morfológico
		- Palavras são examinadas para identificar sua forma básica (Lematização)
	- Sintático
		- É analisado a estrutura gramatical para entender o relacionamento entre as palavras e organização das frases
	- Semântico
		- Compreensão do significado das palavras e frases
		- Compreensão do contexto em que estão inseridos

## Usos

- traduzir texto de um idioma para outro
- responder a comandos digitados ou ditados
- reconhecer ou autenticar usuários com base na voz
- resumir grandes volumes de texto
- avaliar a intenção ou o sentimento do texto ou da voz
- gerar texto, gráficos ou outros conteúdos sob demanda

## Tarefas

- Reconhecimento de voz
- Marcação de trechos em voz
	- Determinação da classe gramatical baseado no contexto
- Desambiguação de sentido
- Named Entity Recognition (NEM)
	- Identifica palavras ou frases como entidades úteis
	- NEM identifica "Kentucky" como um local ou "Fred" como o nome de um homem
- Resolução de correferência
	- Identifica se duas palavras diferentes referem-se à mesma entidade
- Análise de sentimento
	- Extrai qualidades subjetivas do texto
	- Emoções, sarcasmo, confusão, suspeita
- Geração de linguagem natural

## Métodos

### Bag of Words (BoW)

- consiste em simplesmente definir a frequência em que cada palavra **do seu vocabuláro inteiro** estão presentes em **cada frase**
- Vocabulário
	- Todas as N palavras distintas na base de treinamento
- Para cada frase é contado quantas vezes cada palavra do vocabulário aparece na frase

![[Concursos/images/Untitled 74.png]]

- É comum que se limite o dicionário às M palavras mais frequentes da base
- No python, utilizando **scikit**, existe a função `CountVectorizer`

### Term-Frequency Inverse-Document-Frequency (TF-IDF)

- O TF-IDF, de forma automática, pondera as palavras mais importantes.
- Cria um espaço de contagem **baseado na relevância dos termos**, considerando o contexto
- permite que a representação vetorial tenha um peso com base da frequência em que as palavras aparecem em todas as frases da base
- **uma palavra que está presente em todas as frases da base, não carrega informação, e portanto terá um peso baixo**.
- **Term Frequency,** seria a mesma ideia do BoW, considerar a frequência com que cada palavra **p** aparece na frase **f**.
	- $TF(p,f)=quantidade\ de\ vezes\ que\ a\ palavra\ p\ aparece\ na\ frase\ f$
- **Inverse-Document-Frequency**, é onde a palavra será ponderada quanto a sua capacidade de diferenciar as frases.
	- $FD(p)=\frac{quantidade\ de\ frases\  da\ base\ que\ possuem\ a\ palavra\ p}{quantidade\ de\ frases\ totais\ N}$
	- portanto seu inverso será: $IDF(p)=\frac{N}{FD(p)}$

### GloVe (Global Vectors for Word Representation)

- baseia-se em **estatísticas globais das coocorrências**
- transforma palavras em vetores de alta dimensão que capturam a semântica das palavras e suas relações contextuais
- A principal característica do GloVe é que ele é baseado em **estatísticas globais de coocorrência de palavras de um grande corpus de texto**
- O treinamento é feito de maneira que o **produto escalar** de dois vetores de palavras seja igual ao **logaritmo da probabilidade de co-ocorrência** dessas palavras
- **Funcionamento**
	- Matriz de Concorrência
		- começa construindo uma matriz de coocorrência X, onde cada entrada $X_{ij}$ representa o número de vezes que a palavra j aparece no contexto da palavra i em um corpus de texto.
		- O contexto pode ser definido de várias maneiras, como palavras que aparecem dentro de uma janela de tamanho fixo ao redor da palavra de interesse.
	- Objetivo do modelo
		- O objetivo do GloVe é encontrar vetores de palavras wi e wj de tal forma que o produto escalar desses vetores (ou a similaridade dos vetores) se aproxime do logaritmo da probabilidade de coocorrência.
- Aplicações
	- Análise de sentimentos
	- Classificação de texto
	- Tradução automática

### Características Importantes do GloVe

1. **Estatísticas Globais**: Diferente do Word2Vec, que trabalha com janelas de contexto local, o GloVe utiliza informações **globais** de coocorrência no corpus inteiro, aproveitando relações de longo alcance.
2. **Relações Lineares e Analogias**: O GloVe é projetado para capturar padrões semânticos lineares, o que facilita a identificação de analogias. Por exemplo, vetores de palavras como “rei” e “homem” terão uma diferença vetorial semelhante à diferença entre os vetores de “rainha” e “mulher”, capturando a relação de gênero.
3. **Eficiência Computacional**: Como a técnica se baseia em uma matriz de coocorrência, o GloVe pode ser mais eficiente para certos tipos de representações, especialmente quando se utiliza uma matriz pré-computada em vez de treinamento intensivo em um grande corpus.
4. **Interpretação de Dimensões**: Em embeddings GloVe, as dimensões podem capturar atributos específicos, como gênero ou país, embora essas interpretações não sejam explícitas nem garantidas para todas as dimensões.

### Word2Vector

- transforma palavras em vetores de alta dimensão que capturam semântica e relações contextuais entre palavras. 
- cria <u>representações vetoriais de palavras</u> em um espaço vetorial, onde palavras com significados semelhantes têm vetores próximos.
- baseado em **redes neurais de duas camadas** treinadas para reconstruir contextos linguísticos de palavras
- possui dois modelos principais: 
	- **Continuous Bag of Words (CBOW)**
		- Capaz de predizer uma palavra-alvo (target word) a partir de um conjunto de palavras de contexto (context words) que aparecem ao seu redor.
		- A entrada da rede neural é uma média das representações das palavras de contexto, e a saída é a palavra-alvo.
	- **Skip-gram**
		- Capaz de Predizer palavras de contexto a partir de uma palavra-alvo.
		- A entrada da rede neural é a palavra-alvo, e a saída é um conjunto de palavras de contexto.
- Ambos os modelos, CBOW e Skip-gram, utilizam uma rede neural simples de uma camada oculta.
- Aplicações
	- Análise de Texto
	- Tradução automática
	- Resumo de texto
	- Perguntas e respostas

### N-Gramas

- Usado para dividir uma sequência de palavras em subsequências contíguas de n palavras
- Por exemplo, em um unigrama (n=1), cada palavra na frase é considerada individualmente.
- Em um bigrama (n=2), as palavras são emparelhadas, e em um trigrama (n=3), as palavras são agrupadas em conjuntos de três, e assim por diante.
- Ajudam a capturar a estrutura linguística, como as frases tendem a ser construídas e a predizer a próxima palavra de uma sequência de palavras, entre outras coisas.
- Eles são particularmente úteis quando a ordem das palavras é importante para o significado, porque capturam a informação da sequência que os unigramas ignoram.
- Usos:
	- correção ortográfica, 
	- sugestão de palavras, 
	- reconhecimento de fala, e 
	- tradução automática