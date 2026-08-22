---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2024-08-27T17:01:00
Owner:
  - Eduardo Quinalha
---
# Noções de Amostragem

- **parâmetro:** medida que descreve alguma característica numérica da população
	- Os mais importantes são:
		- Média: $\mu$
		- Variância: $\sigma²$
		- Desvio padrão: $\sigma$
- **estimadores:** construído em cima de uma população amostral
	- o estimador é uma função, uma fórmula, uma maneira de cálculo.
	- É uma expressão matemática obtida a partir dos elementos de uma amostra.
	- Principais:
		- **média amostral: **$\overline{x}$
		- **variância amostral: **$s²$
		- **desvio padrão amostral: **$s$

![[Concursos/images/Untitled 48.png]]

- **Erro amostral**
	- Como a amostra não inclui todos os elementos da população, a estimativa difere do parâmetro
	- Erro amostral é a diferença entre o estimador e o parâmetro populacional
	- $\epsilon=\^{\theta}-\theta$
- **Tamanho da população**
	- Limite superior - Limite inferior + 1

## Tipos de amostragem

- Amostragens podem ser:
	- **Probabilísticas**
		- não há interferência do entrevistador na seleção da amostra, ou seja, o entrevistador é imparcial.
		- Exemplos:
			- **aleatória simples**
				- Cada elemento da população tem a mesma chance de ser escolhido.
			- **amostragem por estratos**
				- Classificar a população em, ao menos dois estratos e extrair uma amostra de cada um.
			- **amostragem por conglomerados**
				- Dividir em seções a área populacional, selecionar aleatoriamente algumas dessas seções e tomar **todos os elementos dela**.
				- Difere da estratificação no sentido de que esta toma apenas algumas amostras de cada estrato. Na conglomeração, todos os integrantes do conglomerado são tomados.
			- **sistemática**
				- Escolher cada elemento de ordem k
	- **Não probabilística**
		- Exemplos:
			- **Amostragem por conveniência**
				- Utilizar resultados de fácil acesso
			- **Amostragem por julgamento**
				- A escolha dos entrevistados é feita a partir do julgamento do entrevistador
				- O entrevistador buscará por elementos que possuem características definidas de acordo com o seu interesse.
			- **Amostragem por cotas**
				- Selecionamos uma amostra por cotas proporcionais com características semelhantes da população sem critérios probabilísticos.

# Estatística Descritiva

### Medidas de posição

- **moda**: 
	- valor mais frequente no conjunto de amostra
- **mediana:** 
	- **valor central** de uma distribuição amostral, após ter sido organizada do menor para o maior
	- Caso o número de amostras seja par, trata-se da média dos dois valores centrais
- **média**
	- Aritmética
	- Ponderada
- **separatrizes**
	- Separam os dados em quantidades iguais
	- Quartis
![[Concursos/images/Untitled 49.png]]
	- Decis
![[Concursos/images/Untitled 50.png]]
	- Percentis
![[Concursos/images/Untitled 51.png]]

### Medidas de dispersão

- **variância**
	- descreve a dispersão dos dados
	- é uma medida de desvio de uma variável em relação à sua média
$$
s² = \frac{\sum(x_i-\overline{x})^2}{n-1}
$$
- **desvio padrão**
	- conserva as unidades do desvio e dos dados
$$
s = \sqrt{s²}
$$
- **Coeficiente de variância**

$$
CV = \frac{s}{\overline{x}}*100\% 
$$

### **Correlação**

- quantifica como as mudanças em uma variável estão associadas às mudanças em outra variável
- Tipos
	- Correlação de Pearson
![[Concursos/images/Untitled 52.png]]
		- Mede a força e a direção da relação **linear** entre duas variáveis.
		- O coeficiente de correlação de Pearson (r) varia de -1 a 1:
			- r = 1 indica correlação positiva perfeita
			- r = -1 indica correlação negativa perfeita
			- r = 0 indica ausência de correlação linear
	- Correlação de Spearman
		- Mede a força e a direção da relação monotônica entre duas variáveis, que **não necessariamente precisam ser linear.**
		- Útil para dados que não seguem uma distribuição normal ou para dados ordinais.

## Divisão do conjunto de dados

- Quartil
	- Divide os dados segundo a quantidade de ocorrências em grupos de 25% de ocorrência
	- A diferença entre os quartis superior e inferior chama-se amplitude interquartil
![[Concursos/images/Untitled 53.png]]

## Análise de outliers

### Usando métodos gráficos

- Utilizando-se da divisão em quartis, pode-se identificar um outlier como dados que estão a 1,5 vezes a distância do intervalo interquartil abaixo ou acima de Q1 e Q3
- **Fórmulas**:
	- Limite Inferior: Q1−1.5×IQR
	- Limite Superior: Q3+1.5×IQR

### Usando estatística descritiva

- **Z-Score**: 
	- O Z-score mede a distância de um valor da média em termos de desvios padrão. 
	- Valores de Z-score além de +3 ou -3 são geralmente considerados outliers.
![[Concursos/images/Untitled 54.png]]

### Tratamento

- Transformação: Aplica transformações, como logaritmo, para reduzir o impacto
- Remoção
- Uso de métodos robustos: Normalmente utilizam a mediana ao invés da média

## Análise de dados categorizados

### **Teste Qui-Quadrado**

- **Definição**: Teste estatístico utilizado para determinar se existe uma associação significativa entre duas variáveis categorizadas.
- **Utilização**: Verifica a independência ou associação entre variáveis categorizadas.
- **Exemplo**: Teste para verificar se a preferência por um tipo de produto está associada ao gênero.

# Séries Estatísticas

- Conjunto de dados organizados de acordo com determinada variável ou critério
- Permite observar a variação dos dados ao longo do tempo ou em diferentes locais ou categorias
- Tipos
	- **Séries temporais: **permite a análise da evolução da variável ao longo do tempo
		- Exemplo: Evolução do preço do petróleo
	- **Séries geográficas:** dados organizados de acordo com a localização geográfica
		- Exemplo: Taxa de desemprego em diferentes estados
	- **Séries específicas:** Dados organizados de acordo com categorias
		- Exemplo: Distribuição da população por faixa etária
	- **Séries contínuas:** Dados que variam continuamente
		- Exemplo: Temperaturas registradas ao longo do dia
	- **Séries discretas:** Dados que variam em passos definidos e só podem assumir valores específicos
		- Exemplo: Número de filhos por família

# Organização de variáveis

## **Tabelas de Frequência**: 

- Utilizadas para dados categóricos e numéricos discretos. Elas mostram a frequência (número de ocorrências) de cada categoria ou valor.

Exemplo de Tabela de Frequência Simples:

| Categoria | Frequência |
| --- | --- |
| A | 10 |
| B | 15 |
| C | 5 |

## **Classes de Intervalo**: 

- Utilizadas para dados contínuos, onde os dados são agrupados em intervalos de valores.
	Exemplo de Classes de Intervalo:

| Intervalo | Frequência |
| --- | --- |
| 0-10 | 7 |
| 11-20 | 12 |
| 21-30 | 9 |
- Para cálculo da média em classes de itervalo: 

$$
\overline{X} = \frac{\sum{fr.pm}}{\sum{fr}}
$$

- onde: 
	- fr = freq relativa (%)
	- pm = Ponto médio do intervalo
- Para o cálculo da mediana, deve-se observar a frequência acumulada, sendo que a mediana é o valor central ou valor da classe onde encontra-se a ocorrência que está no meio
	- Para casos onde o total de observações for par, a mediana será a média dos dois valores centrais

### Formas de calcular o número e a amplitude dos intervalos

- O número de classes pode ser determinado usando diferentes regras empíricas. Uma das mais comuns é a **Regra de Sturges**:
	- $k = 1 + 3.322 \log_{10}n$
		Onde:
		- k é o número de classes
		- n é o número total de observações
- Outra abordagem é a **Regra da Raiz Quadrada**:
	- $k=\sqrt{n}$
- A amplitude das classes pode ser calculada simplesmente dividindo a amplitude total pelo numero de classes
	- h = A/k
- **Forma de apresentação das frequências**
	- **Absoluta**: simples contagem do número de observações
| Intervalo | Frequência Absoluta (f) |
| --- | --- |
| 150-159 | 5 |
| 160-169 | 5 |
	- **Relativa**: Porcentagem do total de observações em cada classe
| Intervalo | Frequência Absoluta (f) | Frequência Relativa (fr) |
| --- | --- | --- |
| 150-159 | 5 | 510×100=50% |
| 160-169 | 5 | 510×100=50% |
	- **Acumulada**: Soma das frequências absolutas das classes anteriores
| Intervalo | Frequência Absoluta (f) | Frequência Acumulada (Fa) |
| --- | --- | --- |
| 150-159 | 5 | 5 |
| 160-169 | 5 | 5 + 5 = 10 |

# Análise Exploratória de Dados

- é uma abordagem usada para análise de conjuntos de dados de modo a **resumir suas características** principais
- consiste em **aplicar tratamentos gráficos e numéricos **de forma a **compreender o comportamento** dos dados
- 🔥**O modelo é criado após a análise dos dados**🔥
- frequentemente com **métodos visuais**
- tem como objetivo observar o que os dados podem nos dizer além da modelagem formal ou do processo de teste de hipóteses.
- vai além do uso descritivo da estatística

![[Concursos/images/Untitled 55.png]]

- A AED emprega grande variedade de técnicas gráficas e quantitativas
- Sua finalidade é **examinar os dados previamente à aplicação de qualquer técnica estatística**

## Etapas

- Para realizar uma AED recomenda-se seguir as seguintes etapas
	- preparar os dados para serem acessíveis a qualquer técnica estatística;
	- realizar um exame gráfico da **natureza** das variáveis individuais a analisar e uma análise descritiva que permita **quantificar** alguns aspectos gráficos dos dados;
	- realizar um exame gráfico das **relações entre as variáveis **analisadas e uma análise descritiva que **quantifique** o **grau de inter-relação** entre elas;
	- identificar os possíveis casos atípicos (outliers);
	- avaliar, se for necessário, a presença de dados ausentes (missing values);

## Escalas de mensuração

- Tipos
	- **Nominal**
		- as variáveis são medidas em **classes discretas**, mas não é possível estabelecer ordem.
		- Não se pode deduzir uma classe como maior ou menor do que outra, apenas igual ou diferente
		- Qualitativo
	- **Ordinal**
		- as variáveis são medidas em** classes discretas** entre as quais é possível **definir uma ordem**, segundo uma relação descritível, mas não quantificável.
		- Também não há como se dizer que uma classe é maior ou menor a outra, no entanto há relação hierárquica entre elas
		- Qualitativo
		- Em alguns casos, pode ser transformado em quantitativo
		- Um atributo é denominado ordinal quando as **variáveis podem ser colocadas em ordem**, mas **não é possível quantificar a diferença entre os resultados**
	- **Intervalar**
		- as variáveis assumem** valores quantitativos**, **não possuem zero absoluto**, i.e., não possuem uma medida de ausência de atributo.
		- os dados nesse nível não têm um ponto inicial zero natural
	- **Razão**
		- as variáveis assumem **valores quantitativos**, cuja relação exata entre estes é possível definir porque esta escala **possui um zero absoluto**
- A depender do tipo da escala a ser mensurada, técnicas e medidas diferentes podem ser adotadas

![[Concursos/images/Untitled 56.png]]

![[Concursos/images/Untitled 57.png]]

## Variáveis e tipos de variáveis

![[Concursos/images/Untitled 58.png]]

- **Qualitativas**:
	- Características não numéricas
	- **Nominal**: 
		- ex. sexo, cor dos olhos
	- **Ordinal**: 
		- ex. classe social, grau de instrução
- **Quantitativas**:
	- Números
	- Contínuas: ex. peso, altura
	- Discreta: ex. núm de filhos, qtde de carros
- **Medidas**
	- de posição: moda, média, mediana, percentis, quartis
	- de dispersão: amplitude, intervalo interquartil, variância, desvio padrão
- **Dependentes**
	- O que é determinado
- **Independentes**
	- O que varia e determina a variável dependente
	- São os coeficientes da equação
- **Controlada**
	- O que se deseja manter em um patamar pré-determinado

# Visualização de Dados

- Também chamado de **recuperação dos dados**

## Gráfico de barras

- valores da variável no eixo das abscissas
- suas frequências ou porcentagens no eixo das ordenadas
- interessante para as variáveis qualitativas ordinais ou quantitativas discretas
- Não existe uma ordem para que os valores sejam colocados nas barras

## Diagrama circular (pizza)

- repartimos um disco em setores circulares correspondentes às porcentagens de cada valor
- calculadas multiplicando-se a frequência relativa por 100
- adapta-se muito bem para as variáveis qualitativas nominais.

## Histograma

- retângulos contíguos com **base nas faixas de valores** da variável e com **área igual à frequência relativa** da respectiva faixa.
- A altura de cada retângulo é denominada densidade de frequência
- Para construir um histograma dividimos a **amplitude dos dados em intervalos**, preferencialmente de tamanhos iguais, e contamos o número de observações que estão em
cada um dos intervalos

![[Concursos/images/Untitled 59.png]]

- Permite descobrir o centro da distribuição, a amplitude e simetria

## Boxplot

- Similar ao gráfico de velas
- A caixa tem seu nível superior no Q3 e o inferiror no Q1
- A mediana (Q2) é representada por uma linha dentro da caixa
- As linhas vão até os valores máximos e mínimos

![[Concursos/images/Untitled 60.png]]

![[Concursos/images/Untitled 61.png]]

### Interpretação

- Q2 = Mediana
- Se a mediana estiver mais próxima de Q3, significa que os dados estão inclinados à esquerda (negativamente inclinados)
- Mediana mais próxima de Q1, dados inclinados à direita (positivamente inclinados)
- Mínimo = Q1 - 1.5 IIQ (intervalo inter quartil)
- Máximo = Q3 + 1.5 IIQ

## Gráfico de linha ou sequências

- Adequados para apresentar observações medidas ao longo do tempo, enfatizando sua tendência ou periodicidade.

## Polígono de frequências

- Similar ao histograma
- Para a sua construção, localiza-se o ponto cuja abcissa é igual ao ponto médio da classe e a ordenada é a correspondente à frequência da classe.
- Unem os sucessivos pontos formando um polígono. 

![[Concursos/images/Untitled 62.png]]

## Diagrama de dispersão

- Adequado para descrever o comportamento conjunto de duas variáveis quantitativas.
- Cada ponto do gráfico representa um par de valores observados.
- Também conhecido por scatterplot

![[Concursos/images/Untitled 63.png]]

## Gráficos de contorno

- Útil quando um atributo contínuo é medido em uma grade espacial,
- Exemplos comuns:
	- Mapas de calor
	- Curvas de nível

# Agregação dos dados

## Dashboard

- **Não é conhecimento, é informação**
- Traz uma visualização dos dados, compilados, preferencialmente em uma única tela
- Conjunto ou grupo de visões analíticas
- Generalista e operacional

![[Concursos/images/Untitled 64.png]]

![[Concursos/images/Untitled 65.png]]

## Cockpit

- Normalmente traz informações de um subdomínio específico
- Focado e Tempo real
- Normalmente traz uma série de KPI’s, representados como indicadores, assemelhando-se ao painel de uma aeronave (cockpit)

![[Concursos/images/Untitled 66.png]]

## Scorecard

- Visualização de indicadores (KPI)
- Traça o progresso em relação às metas e objetivos estratégicos
