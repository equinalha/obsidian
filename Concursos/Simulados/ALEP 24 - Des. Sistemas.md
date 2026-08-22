---
base: "[[Simulados.base]]"
Desempenho: 0.675
Banca: FGV
Obs: ""
Tipo: Múltipla Escolha
Obj: MP-PR
"% Colocação": -100
Status: Done
Data: 2024-04-08
---
*33 - Queremos construir uma aplicação WEB em JAVA em três camadas.
Sobre a utilização do padrão de projeto MVC nesta aplicação, assinale a afirmativa correta.*

*(A) A primeira camada, ou camada de apresentação, e a segunda camada, ou camada de negócios, ambas implementam uma versão do MVC.*

*(B) A camada de apresentação corresponde a View do MVC além de implementar as classes do Model.*

*(C) A camada de apresentação corresponde a View do padrão MVC, o Controler é implementado na segunda camada utilizando o Model que é implementado na terceira camada.*

*(D) A primeira camada corresponde a View do padrão MVC e a terceira camada implementa o Controler e o Model do padrão MVC.*

*(E) A camada de apresentação corresponde ao frontend e o backend coresponde unicamente a View e o Controler do padrão MVC.*

> [!note] 🔥
> 
> - As camadas VIEW e CONTROLLER do MVC equivalem à camada de apresentação do modelo de 3 camadas
> - A lógica de negócio no MVC encontra-se na camada MODEL, enquanto no 3 camadas encontra-se em uma camada própria
> - A camada de dados do modelo de 3 camadas não tem equivalência no MVC, uma que a camada MODEL também é responsável por esta persistência e não há separação

*34 - Analise o script java a seguir: *

```java
public class HelloJEE {
	public static void main(String args[]){
		System.out.println("JEE v8 & JDK 17: " + sum(5, 3));
		}
		
	static int sum(int a, int b){
		return a + b;
		}
	}
}
```

*Ao executar o script acima, a saída no console será
(A) JEE v8 & JDK 17: 5.
(B) JEE v8 & JDK 17: 3.
(C) JEE v8 & JDK 17: 8.
(D) JEE v8 & JDK 17.
(E) Erro de compilação.*

> [!note] 🔥
> A questão tenta fazer confusão com a restrição quanto ao **static.
**Sendo o main um método estático, ele não poderia chamar o sum() caso este fosse não estático. Não há problema quando às diferenças de visibilidade, neste caso o main é **public** e o sum() tem a visibilidade **default**.

*49 - Em otimização de consultas expressas em álgebra relacional, é possível considerar, para alguns casos, a transformação de expressões, a fim de que produzam resultados equivalentes. *

*Sejam:*

![[Untitled 858.png]]

*No que se refere ao operador de PROJEÇÃO (π), assinale a opção que apresenta uma propriedade de equivalência válida.*

![[Untitled 859.png]]

> [!note] 🔥
> Na prova eu marquei letra E, no entanto, a operação de projeção não é cumulativa. Por outro lado, a união é. Sendo assim, a alternativa B é verdadeira.

*52 - O processo de integração de dados demanda um conjunto de ações envolvendo tarefas no contexto do que usualmente se chama “limpeza de dados” (ou data cleansing). E um dos desafios enfrentados nesse processo é a forma pela qual serão tratados os dados ausentes.
A ausência de um dado atende a um mecanismo específico. O mecanismo conhecido como MAR (Missing at Random) é aquele no qual a ausência*

*(A) causa a remoção de linhas completas de dados que apresentam qualquer coluna com dado ausente.*

*(B) elimina os registros de dados segundo algum critério, como sua matriz de correlação.*

*(C) está relacionada aos dados observados na coluna do conjunto de dados na qual a ausência ocorre. *

*(D) está relacionada aos demais dados das demais colunas do conjunto de dados, que não a coluna sendo observada. *

*(E) não tem relação alguma com os dados do conjunto de dados, acontecendo de forma aleatória.*

> [!note] 🔥
> Questão de ciência de dados. Aguardar o edital para ver se é relevante.

*53 - O processo de tomada de decisão conta com ferramentas computacionais que otimizam e auxiliam gestores em diferentes níveis de
atuação organizacional. No que se refere ao suporte de dados, os armazéns de dados (ou data warehouses) representam uma importante
alternativa para o armazenamento de dados por conta de suas características estruturais.
Assinale a opção apresenta uma característica que diferencia um data warehouse de uma base de dados com suporte ao processamento
OLTP.
(A) Dimensões e níveis de agregação ilimitados.
(B) Operações restritas em dimensões.
(C) Tratamento estático da matriz esparsa.
(D) Visão conceitual unidimensional.
(E) Volatilidade dos dados armazenados.*

> [!note] 🔥
> (A) - CORRETA
> - **Data warehouse:** Dimensões e níveis de agregação ilimitados, estrutura multidimensional, agregação de dados, grande volume de dados.
> - **Base de dados OLTP:** Operações em dimensões restritas, estrutura relacional, foco em CRUD, menor volume de dados.
> 
> (B): 
> 
> - É possível realizar diversas operações em dimensões, como:
>     - **Filtragem:** Selecionar dados de acordo com uma ou mais dimensões.
>     - **Agregação:** Calcular medidas como soma, média, contagem, etc., para diferentes níveis de granularidade em uma ou mais dimensões.
>     - **Drill-down e drill-up:** Navegar pelos dados em diferentes níveis de granularidade em uma ou mais dimensões.
>     - **Criação de novas dimensões:** Combinar ou transformar dimensões existentes para criar novas perspectivas dos dados.
> 
> (C):
> 
> - Uma matriz esparsa em um data warehouse é uma matriz com muitos elementos vazios.
> - Isso ocorre porque nem todos os valores de todos os atributos estão presentes para todos os registros.
> - **Exemplos de motivos para a matriz esparsa:**
>     - Dados não coletados.
>     - Dados inconsistentes.
>     - Dados ausentes.
> - O tratamento da matriz esparsa em um data warehouse **não é estático**.
> - Diversas técnicas podem ser utilizadas para lidar com a matriz esparsa, como:
>     - **Exclusão de linhas ou colunas com muitos valores ausentes.**
>     - **Imputação dos valores ausentes com base em outros valores conhecidos.**
>     - **Armazenamento da matriz esparsa em um formato otimizado.**
> 
> (E):
> 
> - A volatilidade de dados se refere à frequência com que os dados mudam.
> - Em um data warehouse, os dados são **historicamente estáveis**.
> - Ao contrário do OLTP (Online Transaction Processing), que é orientado para transações online e possui alta volatilidade de dados, o data warehouse é orientado para análise de dados históricos e possui baixa volatilidade de dados.

*60 - Considere o seguinte trecho de código, desenvolvido utilizando-se a linguagem de programação Python:*

```python
l = [1,'oi',2.5]
l *= 4
print(l, 4 in l, 'oi' in l)
```

*Assinale a opção que indica a saída impressa pela função print().
(A) [1, 'oi', 2.5, 1, 'oi', 2.5, 1, 'oi', 2.5, 1, 'oi', 2.5] False True
(B) [4, 'oioioioi', 10.0] True False
(C) [1, 'oi', 2.5] False True
(D) [4, ' oioioioi', 10.0, 4, 'oioioioi', 10.0, 4, ' oioioioi', 10.0, 4, ' oioioioi', 10.0] True False
(E) [4, ' oi', 10.0, 4, 'oioi', 10.0, 4, 'oioioi', 10.0, 4, 'oioioioi', 10.0] True True*

> [!note] 🔥
> Ao multiplicar por 4 a lista, como não é homogênea, o que o python faz e repeti-la 4 vezes:
`[1, 'oi', 2.5, 1, 'oi', 2.5, 1, 'oi', 2.5, 1, 'oi', 2.5] `
Neste caso, `4 in l` irá retornar `False` e `‘oi’ in l `irá retornar `True`

61 - Seja o seguinte código escrito em linguagem C:

```c
#include <stdio.h>
int main()
{
int i;
for (i=0; i<5; i++) printf("%u\n",++i<<2);
return 0;
}
```

Assinale a opção que indica o que será impresso no console padrão de saída pelo programa.
(A) 0 0 1
(B) 0 1 2 3 4
(C) 0 4 8 12 16
(D) 0 8 16
(E) 4 12 20

> [!note] 🔥
> O operador `++i` irá incrementar o valor de i antes de considerá-lo no resto da expressão. Neste caso, inicia-se com `i=1`. Após o deslocamento de duas casas à esquerda, o valor `00000001` passará a ser `00000100` que é 4 em decimal.

No próximo ciclo, `i `que já tem valor 1 será incrementado para 2. Novamente, o operador `+``**+**``i` irá incrementá-lo para 3 antes de considerar o resto da expressão, ou seja, `i` será, em binário: `000001100` que é 12 em decimal.

E assim por diante…

*62 - Em uma Casa Legislativa, considere um cenário restrito, no qual parlamentares submetem proposições (propostas legislativas) para avaliação das instâncias do Parlamento. O modelo de conceitual de classes a seguir modela tal situação:*

![[Untitled 860.png]]

*Em um contexto no qual o modelo conceitual será mapeado segundo a abordagem Mapeamento Objeto-Relacional (ORM), e que a classe “Proposição” foi mapeada para um banco de dados relacional da seguinte forma: *

`*Proposição ( {cod_proposicao} <PK>, identificacao, ementa, indexacao, tipo )*`* *

*sendo o atributo “cod_proposicao” a chave primária da tabela (PK) e os demais atributos simples*

*Seja o atributo “identificacao” aquele que necessita, para implementar a semântica do caso, a demanda de não permissão de valores
repetidos – ou seja, somente aceita valores únicos.
No contexto do modelo relacional de banco de dados, ele é considerado um(a)
(A) atributo alternativo.
(B) atributo multivalorado.
(C) chave estrangeira.
(D) chave secundária.
(E) superchave mínima.*

> [!note] 🔥
> A questão provavelmente está com o gabarito errado ou será anulada.
> ## Superchave
> 
> - Um conjunto de uma ou mais colunas que, **tomadas coletivamente**, podem identificar univocamente uma tupla da tabela
> - Duas linhas não podem ter os mesmos valores de superchave
> - Pode haver atributos a mais do que o necessário
> 
> ### Superchave Mínima
> 
> - Conjunto de atributos em uma tabela que, em conjunto, identifica unicamente cada registro **sem conter atributos redundantes. **
> - Ou seja, é o menor conjunto de atributos que pode ser usado para identificar cada linha da tabela de forma única.
> - **Características de uma superchave mínima:**
>     - **Unicidade:** Cada combinação de valores dos atributos da superchave deve identificar um único registro.
>     - **Irredutível**. A remoção de um dos atributos que compõem a superchave, faz com que essa deixe de ser uma superchave
> 
> ## Chave
> 
> - Pode ser vista como uma superchave mínima
> - Irredutível
> 
> ## Chaves Candidatas
> 
> - As  chaves mínimas são chamadas de chaves candidatas. 
> - Para um determinado projeto podemos ter várias chaves candidatas. Por exemplo, CPF e RG 
> - O projetista do banco de dados tem que escolher uma das chaves candidata para usar efetivamente. 
> - Essa chave escolhida será a **chave primária**. 
> - As demais chaves candidatas são chamadas de **chaves alternativas.**
> 
> ## Chave estrangeira
> 
> - **Referencia a chave primária de outra tabela**
> - Pode apontar para um chave candidata

*69 - O modelo de classes de análise a seguir, especificado utilizando a UML, possui a seguinte configuração:*

![[Untitled 861.png]]

*Assinale a opção que reflete uma interpretação correta da semântica de leitura do diagrama.
(A) A classe “Imagem” possui um total de seis atributos.
(B) Existe um relacionamento de composição entre as classes “Preparo” e “Imagem”.
(C) Existe uma classe associativa entre as classes “Paciente” e “Exame”.
(D) O modelo carece de multiplicidades entre as classes “Exame” e “Imagem”.
(E) Um paciente pode não estar associado a um objeto “Exame”.*

> [!note] 🔥
> *(A) A classe “Imagem” possui um total de seis atributos.
*Sim, a classe Imagem é uma especialização de Exame, ou seja, herda seus atributos `codigo, nome, data_coleta` e ainda adiciona mais três: `tipo_regiao, area_regiao, qualidade_imagem
`*(C) Existe uma classe associativa entre as classes “Paciente” e “Exame”.*`*
*`Não existe. 
> - Entidades associativas representam um tipo especial de entidade que surge da necessidade de associar **mais de duas entidades** entre si, caracterizando-se por:
>     - **Participação em Relacionamentos N:N:**
>     - **Atributos Próprios:**
> - No MER, as entidades associativas são representadas por **retângulos** com **dois ou mais losangos** conectando-as às entidades relacionadas.

*70 - Seja o modelo multidimensional representado a seguir, refletindo uma dinâmica de vendas de produtos por vendedores e por região.*

![[Untitled 862.png]]

*Ao analisar a semântica do modelo, é correto inferir que
(A) a dimensão tempo está representada como tabela oculta.
(B) a menor granularidade de tempo é data da venda.
(C) existem quatro tabelas fato e uma tabela dimensão.
(D) implementa o esquema multidimensional estrela.
(E) um registro específico de venda pode se relacionar a várias cidades.*

> [!note] 🔥
> *(A) a dimensão tempo está representada como tabela oculta.
*Não, pois neste caso deveria haver uma <FK> representada.

*(D) implementa o esquema multidimensional estrela.
*Não pois uma das dimensões (Região) está normalizada, consequentemente associada a outra tabela (cidade) caracterizando o modelo floco de neve.

*(B) a menor granularidade de tempo é data da venda.
*Sim, pois é a única