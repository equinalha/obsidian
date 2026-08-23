---
base: "[[Simulados.base]]"
Desempenho: 0.5
Banca: CEBRASPE
Obs: ""
Tipo: Certo/Errado
Obj: TSE
"% Colocação": -100
Status: Done
Data: 2024-03-24
---
**As limitações dos bancos de dados relacionais que utilizam modelo entidade-relacionamento podem ser superadas por meio do uso de ferramentas OLAP (*****online analytical processing*****).**

*A afirmação está correta. Os bancos de dados relacionais tradicionais possuem algumas limitações, como por exemplo, eles não guardam históricos, eles são modelados para guardar registro a registro, e o histórico você tem que pensar em uma outra estrutura para o armazenamento dela. Outro exemplo de limitação é o fato de ele não ser projetado para grandes consolidações de dados. Por essas e outras, o OLAP foi criado, ele ajuda e muito a gestão de dados agregados.*

**Nas operações do OLAP, o *****drill-down***** aumenta o nível de detalhamento, ao passo que o *****drill-up***** diminui o nível de granularidade das dimensões em um *****data warehouse*****.**

Correto

***OPERAÇÕES OLAP***

***SLICE***

*Seleção de dados em 1 dimensão*

***DICE***

*Seleção de dados em 2 ou mais dimensões*

***ROLL-UP /DRILL-UP***

*Agregação de dados - maior generalização, menor detalhe*

***DRILL-DOWN***

*Desagregação de dados - menor generalização, ****maior detalhe***

***ROTATION / PIVOT***

*Permite visualizar os dados sob uma nova perspectiva, sem reduzir/aumentar o escopo dos dados. (Ex: inverter as dimensões entre linhas e colunas).*

**Os relacionamentos entre os elementos de um sistema podem ser expressos por meio de diagramas como o modelo entidade-relacionamento (MER), que permite organizar o sistema de banco de dados em entidades, atributos, relacionamentos e ****associações****.**

*Há algumas regras a serem seguidas no MER, dentre as quais destaca-se a vedação de ligações entre duas ou mais relações. Ocorre que, por vezes, é necessário haver essa ligação. Diante disso, surgem as ****ENTIDADES ASSOCIATIVAS**** ( losango dentro de um retângulo) que atua como uma entidade, mas que existe apenas para ligar duas relações.*

**O esquema de estrela é formado por uma tabela de fatos e várias tabelas auxiliares, denominadas tabelas dimensionais. A consulta ocorre inicialmente nas tabelas dimensionais e depois na tabela de fatos, por meio de uma estrutura de chaves estrangeiras.**

*A consulta em um esquema de estrela normalmente começa pelas tabelas dimensionais, onde o usuário define os filtros ou critérios de busca com base nas dimensões de interesse. Depois, a consulta procede para a tabela de fatos para recuperar os valores das métricas que correspondem aos critérios especificados. As relações entre a tabela de fatos e as tabelas dimensionais são feitas através das ****chaves estrangeiras**** presentes na tabela de fatos, que referenciam as chaves primárias nas tabelas dimensionais.*

*Este modelo é especialmente eficaz para realizar ****consultas analíticas complexas****, tais como as encontradas em ****OLAP (Online Analytical Processing)****. O esquema de estrela permite um processamento de consulta rápido, pois a estrutura simplificada minimiza o número de joins necessários durante a consulta, o que é crucial para o desempenho em grandes volumes de dados.*

**Quanto à alocação de recursos em uma rede de computadores, denomina-se controle de congestionamento a capacidade de impedir que um transmissor rápido envie uma quantidade excessiva de dados a um receptor mais lento.**

*A questão tenta induzir o candidato ao erro, invertendo os conceitos de controle de fluxo com o controle de congestionamento.*

*Enquanto o controle de congestionamento busca evitar a saturação do canal de comunicação para que a origem e o destino da conexão não fiquem nem ociosos nem saturados, o controle de fluxo  busca eliminar a possibilidade do remetente saturar o buffer do destinatário.*

***Controle de Fluxo:****  foco principal é impedir que o *<u>*receptor fique sobrecarregado*</u>* pelos dados enviados por um transmissor mais rápido. Atua na camada de ****enlace**** de dados junto com a camada de ****transporte.***

***Controle de Congestionamento:**** ele *<u>*se preocupa com a rede*</u>*. Se a rede vai ser capaz de suportar o tráfego de dados. É de responsabilidade da camada de ****rede**** e de**** transporte****.*

**No processo de inicialização de um sistema Linux, a função de carregar e descompactar a imagem do *****kernel***** é responsabilidade do carregador de***** boot***** de primeiro estágio.**

*Isso está errado. Vamos definir isso de forma simples, o boot de primeiro estágio tem por função primária encontrar o boot loader de segundo estágio e carregá-lo na memória. O segundo estágio em si carrega o kernel.*

