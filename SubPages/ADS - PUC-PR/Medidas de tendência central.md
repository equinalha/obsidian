---
base: "[[ADS - PUC-PR.base]]"
Class: Matemática
Reviewed: false
Created: 2022-03-17T09:39:00
Type: Anotações
Status: Not started
Description: ""
---
## Média

$\overline {X} \rightarrow média\   amostral$

$\mu \rightarrow média \ populacional$

### Dados não agrupados

Calcula-se como média aritmética simples

### Dados agrupados sem classes

Calcula-se como média ponderada do elemento com sua frequência

$\overline X = \frac {\sum xifi}{n}$

### Dados agrupados com classes

Calculado com o valor médio de cada classe

$$
\overline X = \frac {\sum xifi}{n}
$$

onde

$$
xi = \frac {Li + Ls}{2}
$$

## Mediana

Divide o conjunto de dados no meio (metade das amostras acima e metade abaixo)

<!-- Column 1 -->
Numero ímpar de observações:

<!-- Column 2 -->
$P(md) = \frac {n+1}{2}$

<!-- Column 3 -->
**Posição da Mediana**

<!-- Column 1 -->
Numero par de observações:

<!-- Column 2 -->
$Md = md(P1) + md(P2)/2$

$P1(md) = n/2\ \   P2(md) = P1+1$

### Valores agrupados em classes

Baseado no n, encontrar a classe onde este encontra-se a posição da mediana (vale a regra do par/ímpar).

$$
Md = \frac {li+(\frac {n}{2}-fac(ant))h}{fi}
$$

li = Limite inferior da classe em que a posição da mediana está

fac(ant) = Frequência **acumulada** da classe anterior

h = amplitude da classe

fi = frequência absoluta da classe em que a posição da mediana está

## Moda

Dado que se repete com maior frequência. **Valor que possui a maior frequência absoluta**.

Se todos valores possuem a mesma frequência absoluta, a classe é **amodal.**

Se existe mais de um valor com a mesma frequência absoluta, trata-se de uma séria **multimodal (bimodal, trimodal, etc...)**
