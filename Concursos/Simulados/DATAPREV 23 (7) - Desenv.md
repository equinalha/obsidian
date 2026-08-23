---
base: "[[Simulados.base]]"
Desempenho: 0.69
Banca: CEBRASPE
Obs: Apenas específica
1o Colocado: 0.69
Tipo: Certo/Errado
Obj: TSE
"% Colocação": 0
Status: Done
Data: 2024-11-24
---
52 De acordo com o Clean Code, o programador deve ter o cuidado de declarar todas as variáveis locais em um único ponto, no início do código, como forma de facilitar a compreensão do código escrito.

> [!note] 🔥
> *Um dos princípios fundamentais do clean code é a legibilidade do código. Neste sentido, sugere-se que as variáveis sejam ****declaradas tão próximo possível do primeiro uso.****

Algumas linguagens mais antigas exigiam este tipo de declaração, no entanto, linguagens mais modernas permitem a declaração de variáveis em qualquer ponto do código*

55 A principal diferença entre uma intranet e uma extranet é que a primeira é uma rede de uso restrito, enquanto a segunda é uma rede de uso público.

> [!note] 🔥
> *Intranet:
- Privada e restrita
- Uso interno

Extranet:
- Extensão da intranet que permite colaboração e compartilhamento de informações com parceiros, fornecedores, clientes.
- Restrita, porém permite o uso externo*

56 Os registros UDDI podem estar disponíveis de forma pública ou privada.

> [!note] 🔥
> *Os registros UDDI (Universal Description, Discovery, and Integration) são utilizados para armazenar informações sobre serviços da web. Esses registros podem estar disponíveis de forma pública ou privada, dependendo das configurações de acesso e das políticas de segurança implementadas no ambiente de uso.

UDDI*
> - *Serviço de diretório, baseado em XML, em que é possível registrar e localizar Web Services*
> - *É um repositório de interfaces de Web Services descritas por WSDL.*
> - *O UDDI é uma especificação técnica, ou protocolo e um serviço de diretório onde empresas podem registrar, publicar, descrever, buscar,
> descobrir e integrar serviços web.*
> - *Faz metáfora com Lista telefônica. É dividido em ****Páginas Brancas****, ****Páginas Verdes ****ou ****Páginas Amarelas***

58 No XSLT, o processo de transformação do documento XML usa XPath.

> [!note] 🔥
> *O XSLT é uma linguagem que especifica uma definição para transformações de dados XML. É usada para converter documentos XML em documentos XHTML ou em outros documentos XML. O XPath é usado dentro do XSLT para percorrer elementos e atributos em documentos XML.

****XSLT***
> - *Usado para transformar XML em outro documento*
> - *Pode ser outro XML, HTML ou outro formato interpretado por browser*
> - *Usa um XML como template e outro como dados*
> - *Utiliza XPATH para navegar entre os elementos do documento*
>     - *Sintaxe utilizada para definir partes de um documento XML*
>     - *Contém uma biblioteca de funções padrão*
>     - ***XPath é um elemento importante em XSLT e em XQuery***

60 Na metodologia de pontos de função, qualquer função que apresente informação para o usuário por meio de processamento lógico é considerada uma saída externa (SE).

> [!question] ❓
> De acordo com IFPUG 4.3, olha a definição de uma saída externa (SE):
> *"É um processo elementar que envia dados ou informações de controle para fora da fronteira da aplicação e que inclui um processamento ****adicional**** ao de uma consulta externa."*
> 
> Esse processamento **adicional**, como bem pontuou o colega, pode ser um cálculo, fórmula matemática ou criação de dados derivados.
> 
> Veja que o enunciado falou em "(...) por meio de processamento **lógico** (...)"

62 Na aplicação do Kanban, é necessário que se estabeleça limites de trabalhos em andamento.

> [!note] 🔥
> *Correto.

WIP é uma das métricas do Kanban e é definido pelo número de tarefas que atingiram o ****ponto de compromisso**** mas ainda não evoluíram até a coluna ****pronto ****ou ****entregue.

****Ponto de compromisso, por sua vez, é definido como etapa (ou visualmente a coluna do quadro) em que foi acordado com o cliente que ****o trabalho iniciou****.

Estatisticamente comprova-se que excesso de WIP provoca declínio de produtividade e qualidade.*

63 O reuso de software no nível de componentes pode exigir que se faça adaptações e ampliações do componente com código próprio.

> [!note] 🔥
> *Sim

**Às vezes pode ser necessário a adaptação de componentes a fim de permitir que trabalhe em um novo ambiente*

68 O uso de PWA traz praticidade e velocidade à interação com o usuário, estando restrito a alguns browsers específicos.

> [!note] 🔥
> *Falso.

Embora utilize recursos avançados que podem não estarem disponíveis em todos os navegadores, isto não deve inviabilizar o funcionamento de uma PWA*

75 (ISO 27001/2) No gerenciamento de informações, deve ser evitado o uso de mensagens de correio eletrônico de terceiros para o fornecimento de informações temporárias de autenticação secreta de usuários.

> [!note] 🔥
> *Verdadeiro

E-mail é considerado por natureza um meio de comunicação inseguro. Sendo de terceiros, torna-se mais crítico ainda o uso deste meio para o tráfego de informações secretas.

****ISO 27002:2022 - 5.17 - Informações de Autenticação****

c) (convém que…) informações de autenticação, incluindo informações de autenticação temporária, sejam transmitidas aos usuários de forma segura (…) e que ****o uso de mensagens eletrônicas desprotegidas é evitado;***

83 (Ciclo de vida de desenvolvimento seguro) A fase de design prevê a definição da estrutura geral do software relacionado à segurança e a realização de revisões de código.

> [!note] 🔥
> *Errado. Revisões de código estão na fase de Desenvolvimento*

84 Na fase de suporte e manutenção, deve ser estabelecido um time ou grupo responsável por respostas a incidentes de segurança.

> [!note] 🔥
> *Errado. Questão polêmica!*

86 O processo de análise estática envolve a identificação de problemas na sintaxe do código-fonte.

> [!note] 🔥
> *Um dos aspectos verificados durante a análise estática é a ****sintaxe do código-fonte****. *

No que se refere a OWASP Top 10, julgue os seguintes itens.


89 Security misconfiguration indica que a aplicação pode estar vulnerável devido à utilização de contas e senhas default que estão habilitadas e ainda não foram alteradas.

> [!note] 🔥
> 

90 Insecure design recomenda o uso de LIMIT e outros controles SQL para prevenir a divulgação em massa de registros em caso de injeção de SQL.

> [!note] 🔥
> 

91 Cryptographic failures tem como diretiva de prevenção bloquear o acesso a recursos internos de um ambiente, exceto aos recursos que realmente necessitem ser públicos, como websites disponíveis para a Internet.

> [!note] 🔥
> 

96 No MER, a entidade associativa é utilizada para representar um relacionamento entre relacionamentos.

> [!note] 🔥
> *Errado.

Entidade associativa é utilizada para representar relacionamentos de cardinalidade N:N ou relacionamentos com atributos.

Uma limitação do modelo E-R é justamente a ****impossibilidade de se representar relacionamentos entre relacionamentos.****

Uma alternativa para isso é o uso de agregação (add-on do modelo E-R, ou E-R estendido) onde uma agregação é tratada como uma abstração através da qual relacionamentos são tratados como entidades de nível superior.*

> ![[Untitled 852.png]]

Julgue os próximos itens, referentes ao **Scrum 2020.**


111 Um dos princípios do Scrum é reduzir o desperdício, assim convém que, na sprint, o Scrum team se subdivida em subtimes, de modo a maximizar o paralelismo de execuções.

> [!note] 🔥
> *Errado
No Scrum, os times não são divididos em subgrupos permanentes para trabalhar em paralelo, pois isso poderia criar silos dentro da equipe, prejudicando a comunicação e a colaboração, que são essenciais para o sucesso do método ágil. Em vez disso, o Scrum Team colabora diariamente na Daily Scrum, que é uma cerimônia destinada a promover o alinhamento e a transparência entre todos os membros da equipe.*

112 No Scrum, que é um framework que aborda soluções adaptativas para problemas complexos, o product owner ordena o trabalho para um problema complexo, enquanto o Scrum team e seus stakeholders inspecionam os resultados.

> [!note] 🔥
> *Correto. Está logo na definição:

Em suma, Scrum requer um ****Scrum Master**** para promover um ambiente onde:*
> 1. *Um Product Owner ordena o trabalho para um problema complexo em um Product Backlog.*
> 2. *O Scrum Team transforma uma seleção do trabalho em um incremento de valor durante uma Sprint.*
> 3. ***O Scrum Team e seus stakeholders inspecionam os resultados e se ajustam para a próxima Sprint.***

114 Na gestão de riscos, o nível de risco refere-se à significância de um risco, demonstrada pela combinação das consequências e de seu impacto.

> [!note] 🔥
> 

Considerando a** ITIL 4**, julgue os itens a seguir.


115 A solicitação de um usuário que inicia uma ação de serviço acordada como parte regular da entrega de serviço deve ser gerenciada pela prática de gerenciamento de incidente, de modo que se restaure a operação normal do serviço o mais rápido possível.

> [!note] 🔥
> 