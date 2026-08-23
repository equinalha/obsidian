---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2025-04-29T14:41:00
Owner:
  - Eduardo Quinalha
---
# Conceitos Básicos

> [!note] 🔥
> ** tudo é objeto em Python**

- **Tipagem Forte**
	- Não permite operações entre tipos diferentes
- **Tipagem dinâmica**
	- O tipo de dado é inferido
	- As variáveis são criadas simplesmente atribuindo um valor a ela
	- No caso de ambiguidade, pode-se forçar o tipo com a sintaxe de conversão: 
```python
x = str(3)
y = int(3)
z = float(3)
```
- Gerenciamento automático de memória
	- Utiliza Garbage Collector
- **Suporta Herança múltipla**
- **doc strings**
	- São strings inseridas geralmente no início do código-fonte com o intuito de fornecer uma explicação sobre seu funcionamento
- Variáveis globais
	- Definidas fora de qualquer escopo interno
	- Pode-se criar uma variável global, a partir de um escopo interno usando o operador `gobal `
```python
def myfunc():
	global x
	x = 'teste'
```

# Tipos de dados

![[Untitled 748.png]]

## String

- arrays de bytes que representam caracteres unicode
- Python não possui um tipo de dados de caractere único
- Operadores
	- `len()`
	- `in`
		- `if c in “concursos”`

## Booleano

- Função de cast `bool()`
	- A função bool() permite avaliar qualquer valor e dar a você True ou False em troca. A maioria dos valores são verdadeiros. 
	- Quase qualquer valor é avaliado True se tiver algum tipo de conteúdo.** **
		- **Qualquer string é True,** **exceto strings vazias.** 
		- **Qualquer número é True, exceto 0 (zero)**. 
		- **Qualquer lista, tupla, conjunto e dicionário são True, exceto os vazios.**
```python
bool(False) # False
bool(None)  # False
bool(0)     # False
bool("")    # False
bool(())    # False
bool([])    # False
bool({})    # False
```

## Casting

- No Python, tudo é objeto
- Os tipos primitivos também
- A casting de dados é feito utilizando-se os construtores
	- `int()`
	- `float()`
	- `str()`

# Estruturas de dados

## Listas

- Mutáveis: Podem ser alteradas em tempo de execução
- Ordenadas: A ordem dos elementos não vai mudar
- Indexadas
- Aceita elementos repetidos
- Heterogêneas

```python
lista1 = ["maçã", "banana", "cereja"]
lista2 = ["abc", 34, True, 40, "masculino"]
lista3 = ["maçã", "banana", "cereja", "laranja", "kiwi", "melão", "manga"]
print(lista1 [2:5]) #imprime na tela ['cereja', 'laranja', 'kiwi']
```

- Métodos:
	- `append()`
	- `insert()`
	- `pop()`

## Tuplas

- Imutável: Não se pode alterar um elemento, **nem mesmo adicionar ou remover**
- **Ordenada**
- Indexada
- Aceita valores repetidos

```python
tupla1 = ("maça", "banana", "laranja","maça")
tupla4 = ("abc", 34, True, 40, "masculino") #tupla de diversos tipos
```

- É possível multiplicar tuplas

```python
frutas = ("maçã", "banana", "laranja")
tupla1 = frutas * 2
print(tupla1)
# imprime ('maçã', 'banana', 'laranja', 'maçã', 'banana', 'laranja')
```

## Conjuntos (Sets)

- Não ordenado
- Mutável: Pode-se adicionar e remover elementos de um conjunto após tê-lo criado. No entanto, os **elementos individuais dentro de um conjunto devem ser imutáveis**
- Não indexado
- Usam uma tabela de hash para armazenar seus elementos
- Não aceitam valores repetidos
- Não é possível acessar itens em um conjunto fazendo referência a um índice ou a uma chave. Mas você pode percorrer os itens do conjunto usando um loop for ou perguntar se um valor especificado está presente em um conjunto, usando a palavra-chave in

```python
conjunto1 = {"maça", "banana", "cereja"}
print(conjunto1)
```

## Dicionários

- Ordenado
- Mutável
- Não permite repetições (de chave)
- Chave:valor

```python
carros = {
 "marca": "Toyota",
 "modelo": "Corolla Cross",
 "ano": 2022
}
```

## List Comprehension

- sintaxe mais curta quando você deseja criar uma nova lista com base nos valores de uma lista existente.
- Equivalente ao `map()` do javascript

```python
# Sem list comprehension
frutas = ["maçã", "banana", "laranja", "kiwi", "mango"]
novalista = []
for x in frutas:
 if "a" in x:
 novalista.append(x)
print(novalista)

# Com list Comprehension
frutas = ["maçã", "banana", "laranja"]
novalista = [x for x in frutas if "a" in x]
```

# Lambda

- Pode receber qualquer número de argumentos
- Só pode ter uma expressão

```python
x = lambda a, b: a * b
print(x(5, 6))
```

# Classes e Objetos

- A função `__init__()` quando definida funciona como construtor

```python
class Person:
	def __init__(self, name, age):
		self.name = name
		self.age = age
	def myfunc(self):
		print("Hello my name is " + self.name)
p1 = Person("John", 36)
p1.myfunc()
```

- `self` faz referência ao objeto instanciado da classe. Não precisa se chamar **self**, pode ser atribuído qualquer nome
- A função `__str__()` quando definida controla o que será retornado quando o objeto foi impresso

## Herança

- Qualquer classe pode ser pai
- Para herdar os métodos e propriedades da classe pai, faz referência a ela entre parênteses na criação da classe

```python
class Student(Person):
 pass
```

- `pass` faz com que a classe não tenha nenhuma definição de propriedade ou método

# Iteradores

- Permite percorrer todos os elementos de um objeto iterável
	- listas, tuplas, dicionários, conjuntos e strings
- Métodos
	- `**__iter**``__()`
	- `**__next**``__()`

```python
minhatupla = ("maça", "banana", "cereja")
meuiterador = iter(minhatupla)
print(next(meuiterador))
print(next(meuiterador))
print(next(meuiterador))
```

# File Handling

- `open(``*filename*``, ``*mode*``)`
	- Modos
		- Primeira parte
			- r - Read
			- a - Append
			- w - Write
			- x - Create
				- Retorna um erro caso o arquivo já exista
		- Segunda parte
			- t - Texto
			- b - Binário
		- Default: `rt`
	- Exemplo
		- `f = open("demofile.txt", "rt")`
	- Retorno
		- O retorno do método Open é um objeto do tipo **file**
		- Métodos presentes no objeto file
			- `read()`
				- Sem parâmetros retorna todo o conteúdo do arquivo
				- Com parâmetro, pode-se especificar o número de caracteres a serem lidos: `read(5)`
			- `readline()`
				- Leitura linha a linha
			- `close()`

## Trabalhando com arquivos grandes

- Ao carregar um aquivo grande para leitura a memória principal pode ficar sobrecarregada
- Uma forma mais leve é trabalhando com geradores

```python
def ler_linhas_grandes_arquivos(nome_arquivo):
    with open(nome_arquivo, 'r') as arquivo:
        for linha in arquivo:
            yield linha

# Usar o gerador para ler as linhas do arquivo
for linha in ler_linhas_grandes_arquivos('arquivo.txt'):
    print(linha.strip())
```

# Questões típicas

- `range()`
	- O primeiro número do parâmetro faz parte do intervalo
	- O último não
```python
for i in range(2, 5):
	print(i)

# 2, 3, 4
```
- Utilizando índices e função `range()`

```python
for x in range(-1, -10, -1):
	print (x)

# -1 -2 -3 -4 -5 -6 -7 -8 -9
```

- função `zip()`
	- Itera simultaneamente sobre duas listas (lista1 e lista2) e imprime os valores correspondentes
```python
lista1 = ['I', 'N', 'P', 'I']
lista2 = [1, 2, 3, 4, 5, 6]

for x, y in zip(lista1,lista2): 
	print(x, y)
	
'''
I 1
N 2
P 3
I 4
'''
```
- `dict.fromkeys()`
	- Dado uma lista como parâmetro, irá montar um dicionário em que cada item da lista será uma chave e o valor delas será `none`
	- Como um dicionário não pode ter chaves repetidas, as duplicatas são eliminadas
```python
lista = ['I', 'N', 'P', 'I']
print(dict.fromkeys(lista))

# {'I': None, 'N': None, 'P': None}
```
- `json`
	- `json.load(file)`: Carrega dados de um arquivo **json** diretamente para um objeto python, onde `file `é um objeto de arquivo
	- `json.loads(file)`:
		- é utilizada para *deserializar* uma *string* contendo um objeto JSON para um objeto Python, como um dicionário, por exemplo. 
		- A palavra *loads* é uma abreviação de *load string*, o que significa que está carregando dados de uma string
	- `json.dumps()`:
		- converte objetos python para uma string no formato JSON
		- Pode converter os seguintes objetos
			- dict
			- list
			- tuple
			- string
			- int
			- float
			- True
			- False
			- None
- Operadores

| Operador | Desc | Exemplo |
| --- | --- | --- |
| **  | Exponenciação  | x ** y |
| // | Floor Division: arredonda o resultado para o número inteiro mais próximo | x // y |
| is | Retorna True se ambas as variáveis forem o mesmo objeto | x is y |
| in | Retorna True se uma sequência com o valor especificado estiver presente no objeto | x in y |
| @ | Produto matricial. **Para funcionar depende da importação da biblioteca Numpy** | print(u @ v)  |

- Iteradores
	- Obtidos pelo método iter()
	- É um objeto que implementa os métodos `__iter__()` e `__next__()`
	- São iteráveis: Listas, tuplas, dicionários, conjuntos e strings
	- A estrutura `for x in ...:` na verdade instancia um objeto iterador e executa o método `next()`
- Funções
	- **Tuplas: **É possível especificar funções com número indefinido de argumentos: `def my_function(*kids):`
		- Desta forma, os argumentos serão acessados pela função na forma de uma tupla: `print("The youngest child is " + kids[2])`
	- **Dicionários:** É possível também informar argumentos no formato `variável = "valor".` Se o número de argumentos for desconhecido, pode-se especificar da seguinte forma: `def my_function(**kid):`
		- Desta forma, os argumentos serão acessados pela função na forma de dicionário: `print("His last name is " + kid["lname"])`
	- Argumentos do tipo palavra chave vs posicionais
		- palavra chave: `myFunction(x = 3)`
		- posicional: `myFunction(3)`
		- Para restringir o uso apenas de argumentos posicionais, pode-se utilizar `, /` na definição da função: 
```python
def my_function(x, /):
  print(x)

my_function(3)      # OK
my_function(x = 3)  # Gera um erro
```
		- Para se restringir apenas ao uso de argumentos do tipo palavra-chave, utilizar `*,`
```python
def my_function(*, x):
  print(x)

my_function(x = 3)  # OK
my_function(3)      # Erro
```

# NumPy

- NumPy é uma biblioteca Python usada para trabalhar com arrays. 
- Além disso, possui funções para trabalhar no domínio da álgebra linear, transformada de Fourier e matrizes.
- O NumPy visa** fornecer um objeto array até 50x mais rápido que as listas tradicionais do Python.**
	- Os arrays são armazenados em um espaço contínuo de memória
- O objeto array no NumPy é chamado `ndarray`, ele fornece muitas funções de suporte que facilitam muito o trabalho.

## Tipos de dados

NumPy has some extra data types, and refer to data types with one character, like `i` for integers, `u` for unsigned integers etc.

Below is a list of all data types in NumPy and the characters used to represent them.

- `i` - integer
- `b` - boolean
- `u` - unsigned integer
- `f` - float
- `c` - complex float
- `m` - timedelta
- `M` - datetime
- `O` - object
- `S` - string
- `U` - unicode string
- `V` - fixed chunk of memory for other type ( void )

The NumPy array object has a property called `dtype` that returns the data type of the array:

```python
import numpy as np

arr = np.array([1, 2, 3, 4])

print(arr.dtype)
```

## Copy vs View

- Copy cria uma cópia do array. Alterações feitas no novo objeto, não afetam o original e vice-versa
- View cria uma referência para o objeto original. Alterações vão ter efeito nos dois

Every NumPy array has the attribute `base` that returns `None` if the array owns the data.

Otherwise, the `base`  attribute refers to the original object.

```python
import numpy as np

arr = np.array([1, 2, 3, 4, 5])

x = arr.copy()
y = arr.view()

print(x.base)
print(y.base)
```

## Principais métodos

- `shape()`
	- Retorna a dimensão do array. Exemplo: 
```python
arr = np.array([[1, 2, 3, 4], [5, 6, 7, 8]])
print(arr.shape) # (2, 4)
```
- `ndim()`
	- Retorna a quantidade de dimensões primárias.
	- Exemplo: 
```python
series = [[23,45,12,679], [14,48,69,38]]
new_series = np.array(series)
print(new_series.ndim)   # 2
print(new_series.shape)  # (2, 4)
```
- `reshape()`
	- Altera as dimensões do array
```python
arr = np.array([1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12])
newarr = arr.reshape(4, 3)

[[ 1  2  3]
 [ 4  5  6]
 [ 7  8  9]
 [10 11 12]]
```
	- `reshape(-1)`
		- Achata o array de n dimensões para um array de apenas 1 dimensão
- `ndtier()`
	- Facilita a iteração sobre arrays multidimensionais
	- Dispensa o uso de n loops aninhados
```python
arr = np.array([[[1, 2], [3, 4]], [[5, 6], [7, 8]]])
for x in np.nditer(arr):
  print(x)
```
- `std()`
	- retorna o valor do desvio padrão amostral do conjunto de dados
- `median()`
	- Retorna a mediana do conjunto de dados
```python

y = numpy.array([[1, 2], [2, 2], [3, 3]])
numpy.median(y, axis=0)

# axis= 0, são retornadas as medianas de cada c0luna: [2. 2.]
# axis= 1, são retornadas as medianas de cada l1nha: [1.5 2. 3. ]
# sem o axis , é retornada a mediana do conjunto de todos os dados: 2.0
```
- `ravel()`
	- Retorna uma versão unidimensional de um array, mantendo o conteúdo original. 
	- A ordem em que os elementos são organizados pode ser especificada como um argumento opcional.
- `linspace()`
```python
a1 = np.linspace(1,9,5)
a2 = np.linspace(3,7,5)

# a matriz a1 é criada com 5 valores igualmente espaçados entre 1 e 9, incluindo 1 e 9: [1, 3, 5, 7, 9]
# a2 é criada com 5 valores igualmente espaçados entre 3 e 7: [3, 4, 5, 6, 7.]

b = np.concatenate((a2 , a1)) # [3,4,5,6,7,1,3,5,7,9]
```
- **Filtros**
	- O NumPy pode utilizar um array auxiliar de booleanos para filtrar o array original
```python
arr = np.array([41, 42, 43, 44])

filter_arr = arr > 42      # [False False  True  True]
newarr = arr[filter_arr]   # [43 44]
```
- **ramdom**
	- NumPy tem um método para gerar números pseudo aleatórios

```python
from numpy import random

x = random.randint(100)                 # Número aleatório entre 0 e 100
x = random.rand()                       # Float aleatório entre 0 e 1
x = random.randint(100, size=(3, 5))    # Array 2D com inteiros entre 0 e 100
x = random.choice([3, 5, 7, 9])         # Escolha aleatória
# No exemplo abaixo, o primeiro vetor são as possíveis escolhas, o segundo são as probabilidades associadas a cada elemento do primeiro vetor
# O terceiro parâmetro é o tamanho do vetor que será gerado
x = random.choice([3, 5, 7, 9], p=[0.1, 0.3, 0.6, 0.0], size=(100))
```

## Broadcast

- Permite realizar operações entre vetores de diferentes dimensões
- O Array menor é difundido pelo array maior
- NumPy operations are usually done on pairs of arrays on an element-by-element basis.
- Regras
	- Os dois vetores tem o mesmo tamanho
	- Um deles tem uma das dimensões de tamanho 1
- A saída será sempre um array com as dimensões do maior deles
- Exemplos

```python
A      (2d array):  5 x 4
B      (1d array):      1
Result (2d array):  5 x 4

A      (2d array):  5 x 4
B      (1d array):      4
Result (2d array):  5 x 4

A      (3d array):  15 x 3 x 5
B      (3d array):  15 x 1 x 5
Result (3d array):  15 x 3 x 5

A      (3d array):  15 x 3 x 5
B      (2d array):       3 x 5
Result (3d array):  15 x 3 x 5

A      (3d array):  15 x 3 x 5
B      (2d array):       3 x 1
Result (3d array):  15 x 3 x 5
```

## ufuncs

- They are NumPy functions that operate on the `ndarray` object
- ufuncs are used to implement *vectorization* in NumPy which is way faster than iterating over elements.
- They also provide broadcasting and additional methods like reduce, accumulate etc. that are very helpful for computation.
- ufuncs also take additional arguments, like:
	- `where` boolean array or condition defining where the operations should take place.
	- `dtype` defining the return type of elements.
	- `out` output array where the return value should be copied.

```python
# Cria um novo vetor baseado na soma de dois outros
# Usa a ufunc add()

x = [1, 2, 3, 4]
y = [4, 5, 6, 7]
z = np.add(x, y)
```

- É possível criar uma ufunc personalizada:
	- The `frompyfunc()` method takes the following arguments:
		- `*function*` - the name of the function.
		- `*inputs*` - the number of input arguments (arrays).
		- `*outputs*` - the number of output arrays.

```python
def myadd(x, y):
  return x+y

myadd = np.frompyfunc(myadd, 2, 1)

print(myadd([1, 2, 3, 4], [5, 6, 7, 8]))
```

# Scikit-Learn

## Módulos

- Classificação
- Regressão
- Clustering
- Redução de dimensionalidade
- Seleção de modelo
- Pré-processamento

## Exemplos

### Árvore de decisão

```python
from sklearn.tree import DecisionTreeClassifier
from sklearn.metrics import accuracy_score

# Cria o objeto árvore de decisão
clf = DecisionTreeClassifier()

# Treina o modelo
clf.fit(X_train, y_train)

# Faz previsões utilizando o modelo treinado
y_pred = clf.predict(X_test)

# Finalmente, podemos avaliar o desempenho do modelo usando várias métricas, como precisão, recall e F1-score
accuracy = accuracy_score(y_test, y_pred)
```

### Regressão linear

```python
import numpy as np 
import sklearn.linear_model as skl 
base = np.array([1, 2, 3, 4, 5, 6]) 
x = base.reshape((-1, 1)) # Mesmo que transpose
y = base*2+3

model = skl.LinearRegression().fit(x, y) 
print('a', model.coef_[0]) 
print('b', model.intercept_)
```

# Pandas

- Utilizada para manipulação, limpeza e análise de dados
- Ferramentas para leitura e escrita de dados em diversos formatos, incluindo CSV, Excel, SQL e JSON.
- Series
	- São como colunas em uma tabela
- DataFrame
	- São o equivalente à tabela toda

## Limpeza de dados

- `dropna()`
	- remove linhas que contenham células vazias
	- Retorna um novo Data Frame (não modifica o original)
		- Para modificar o original: `df.dropna(inplace = True)`
- `fillna()`
	- Preenche células vazias
	- `df.fillna(130, inplace = True)`
	- `df["Calories"].fillna(130, inplace = True)`
		- Preenche células vazias com o valor 130 apenas na coluna “Calories”
```python
df = pd.read_csv('data.csv')

x = df["Calories"].mean()

df["Calories"].fillna(x, inplace = True)  # Preenche as células vazias da coluna "Calories" com a média dos valores da coluna
```
- `corr()`
	- Analisa a correlação entre colunas do data frame
	- Como resultado, fornece uma matriz quadrada n x n (onde n = número de colunas)
	- Cada célula da matriz resultante apresenta a correlação entre as respectivas colunas
	- Só funciona com valores numéricos. Colunas não numéricas são ignoradas
```python
df.corr()

            Duration     Pulse  Maxpulse  Calories
  Duration  1.000000 -0.155408  0.009403  0.922721
  Pulse    -0.155408  1.000000  0.786535  0.025120
  Maxpulse  0.009403  0.786535  1.000000  0.203814
  Calories  0.922721  0.025120  0.203814  1.000000
```
- `describe()`
	- Quando o método `describe()` é invocado em uma Série, ele retorna um resumo estatístico que inclui:
		- **count**: a contagem de elementos não nulos na série,
		- **mean**: a média dos valores,
		- **std**: o desvio padrão,
		- **min**: o valor mínimo,
		- **25%**: o primeiro quartil (mediana do primeiro meio dos dados),
		- **50%**: o segundo quartil, também conhecido como a mediana,
		- **75%**: o terceiro quartil (mediana do segundo meio dos dados), e
		- **max**: o valor máximo.

## Recuperação de dados

- `loc()`
	- baseado nas labels da colunas,
	- quando nenhum item é encontrado ele retorna um *KeyError*
	- Primeiro argumento são as linhas e o segundo as colunas a serem buscadas.
		- `df.loc[<linhas>, <colunas>]`
```python
#podemos chamar uma linha pelo seu índice
df.loc[5]
#ou com um array de índices
df.loc[[0,1,2]] 

# uma fatia, do quarto ao sétimo elemento (note que diferente do python puro, neste método a chave inicial e final estarão presente no resultado)
df.loc[4:8]

# tambem podemos chamar diretamente pela linha
df.loc[‘ Justise Winslow’]

# Adicionando um índice
df2 = df.set_index('Player')

# Buscando pelo índice
df2.loc['Justise Winslow']

#array de índices das linhas e colunas, 3 jogadores (as linhas) e 2 colunas
df2.loc[[‘Karl-Anthony Towns’, ‘Stanley Johnson’, ‘D`Angelo Russell’], [‘Position’, ‘ID’]] 

# Utilizando condições para exibir as linhas desejadas
df.loc[(df['Superstar']*100) >= 10]

#Mudando os 5 primeiros registros para o ano de 2018
df2.loc[0:5, 'Draft Year'] = 2018
df2.head(5)
```
- `iloc()`
	- seleciona por números inteiros das linhas, arrays ou por slice.
	- Como o **loc**, ele funciona desta maneira: `df.iloc[<linhas>, <colunas>]`
	- quando solicitamos a o **iloc **uma linha ele retorna um Pandas Series, já múltiplas retorna um Pandas DataFrame,
```python
# Linhas:
df.iloc[0]  # Selecionado a primeira linha do dataset
df.iloc[-1] # Selecionando a última linha

# Colunas:
df.iloc[:,0] # Todos os dados da primeira coluna do dataset
df.iloc[0:5,-1] # Do primeiro ao quinto dado da última coluna

# Seleção de múltiplas linhas e colunas:
df.iloc[0:3] # resgatando as primeiras três linhas do dataset
df.iloc[:, 1:3] # todos os dados da segunda e terceira coluna
df.iloc[[0,2,4], 5:8] # 1º,3º e 5º elementos e 6ª a 8ª colunas
```