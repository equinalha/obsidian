---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2026-07-30T16:36:00
Owner:
  - Eduardo Quinalha
---
[https://refactoring.guru/pt-br/design-patterns/catalog](https://refactoring.guru/pt-br/design-patterns/catalog)

[https://www.youtube.com/watch?v=aiSAO2AXa9g](https://www.youtube.com/watch?v=aiSAO2AXa9g)

# Definições

- **Camada cliente:** interface do usuário ou de serviços. Tipicamente representa uma aplicação independente ou browser rodando applets ou páginas HTML
- **Camada Web:** consiste de servlets e páginas JSP com o objetivo de capturar requisições e processar respostas para a camada do cliente
- **Camada EJB: **contém toda a lógica da aplicação e representa o modelo de negócio implementado em EJBs.
- **Camada de integração: **contém lógica de acesso ao EIS
- **Camada de dados (EIS): **consiste de sistemas de bancos de dados, transações e outros recursos legados

# Objetivos

- Reduzir o tráfego de rede, aumentando a eficiência e facilitando a escalabilidade
- Reduzir o acoplamento entre as camadas e os componentes

# Padrões

## Padrões da Camada de Apresentação

(1) Intercepting Filter: Viabiliza pré- e pós-processamento de requisições.

(2) Front Controller: Oferece um controlador centralizado para gerenciar o processamento de uma requisição

(3) Context Object: Encapsula estado de forma independente de protocolo para compartilhamento pela aplicação

(4) Application Controller: Centraliza e modulariza gerenciamento de Views e de ações

(5) View Helper: Encapsula lógica não-relacionada à formatação

(6) Composite View: Cria uma View composta de componentes menores

(7) Service To Worker e

(8) Dispatcher View: Combinam Front Controller com um Dispatcher e Helpers. O primeiro concentra mais tarefas antes de despachar a requisição. O segundo realiza mais processamento depois

## Padrões da Camada de Negócios

(9) Business Delegate: Desacopla camadas de apresentação e de serviços 

(10) Service Locator Encapsula lógica de consulta e criação de objetos de serviço

(11) Session Facade Oculta complexidade de objetos de negócio e centraliza controle

(12) Application Service Centraliza e agrega comportamento para oferecer uma camada de serviços uniforme

(13) Business Object Separa dados de negócios e lógica usando modelo de objetos

(14) Composite Entity Implementa Business Objects persistentes combinando Entity beans locais e POJOs* 

(15) Transfer Object Antigamente chamado de Value Object ou DTO Reduz tráfego e facilita transferência de dados entre camadas 

(16) Transfer Object Assembler Antigamente chamado de Value Object Assembler Constrói um Value Object composto de múltiplas fontes

(17) Value List Handler Lida com execução de queries, caching de resultados, etc.

## Padrões da Camada de Integração

(18) Data Access Object Abstrai fontes de dados e oferece acesso transparente aos dados

(19) Service Activator Facilita o processamento assíncrono para componentes EJB

(20) Domain Store Oferece um mecanismo transparente de persistência para objetos de negócio

(21) Web Service Broker Expõe um ou mais serviços usando XML e protocolos Web

# Principais Padrões da Camada de Apresentação (Web)

## Intercepting Filter

<!-- Column 1 -->
![[Untitled 538.png|Problema]]

<!-- Column 2 -->
![[Untitled 539.png|Solução]]

- Centraliza controle com processadores fracamente acoplados
- Como um controlador, um filtro fornece um ponto centralizado para processamento de requisições 
- Podem ser removidos, adicionados, combinados em cascata
- Melhora reuso
- Filtros são destacados do controlador e podem ser usados em outros contextos
- Configuração declarativa e flexível
- Serviços podem ser reorganizados sem recompilação
- Compartilhamento ineficiente de informações
- Se for necessário compartilhar muitas informações entre filtros, esta solução não é recomendada
- Um filtro é um componente Web que reside no servidor
- Intercepta as requisições e respostas no seu caminho até o servlet e de volta ao cliente
- Sua existência é ignorada por ambos. É totalmente transparente tanto para o cliente quanto para o servlet
- Filtros podem ser concatenados em uma corrente
- Neste cenário, as requisições são interceptadas em uma ordem e as respostas em ordem inversa

![[Untitled 540.png]]

### Como funciona

Quando o container recebe uma requisição, ele verifica se há um filtro associado ao recurso solicitado. Se houver, a requisição é roteada ao filtro.  Container é o FilterManager (configurado via web.xml). O filtro, então, pode:

1. Gerar sua própria resposta para o cliente
2. Repassar a requisição, modificada ou não, ao próximo filtro da corrente, se houver, ou ao recurso final, se ele for o último filtro
3. Rotear a requisição para outro recurso
4. Na volta para o cliente, a resposta passa pelo mesmo conjunto de filtros em ordem inversa

```java
javax.servlet.Filter
	void init(FilterConfig),
	void doFilter(ServletRequest,
						ServletResponse,
						FilterChain)
	void destroy()
javax.servlet.FilterConfig
	String getFilterName()
	String getInitParameter(String name)
	Enumeration getInitParameterNames()
	ServletContext getServletContext()
javax.servlet.FilterChain
	void doFilter(ServletRequest, ServletResponse)
```

### Como Escrever um filtro simples:

5. Escreva uma classe implementando a interface Filter e todos os seus métodos
`init(FilterConfig)`
`doFilter(ServletRequest, ServletResponse, FilterChain)`
`destroy()`
6. Compile usando o JAR da Servlet API
7. Configure o filtro no deployment descriptor (web.xml) usando os elementos `<filter>` e `<filter-mapping>`
•Podem ser mapeados a URLs, como servlets
•Podem ser mapeados a servlets, para interceptá-los
•A ordem dos mapeamentos é significativa
8. Instale o filtro da maneira usual no servidor (deploy)

```xml
<filter>
	<filter-name>UmFiltro</filter-name>
	<filter-class>filtros.HelloFilter</filter-class>
</filter>
<filter-mapping>
	<filter-name>UmFiltro</filter-name>
	<url-pattern>/filtro</url-pattern>
</filter-mapping>
```

```xml
<filter-mapping>
	<filter-name>UmFiltro</filter-name>
	<servlet-name>UmServlet</servlet-name>
</filter-mapping>
```

## Front Controller

- ponto de acesso centralizado para processamento de todas as requisições recebidas pela camada de apresentação para:
	- Controlar a navegação entre os Views
	- Remover duplicação de código
	- Estabelecer responsabilidades mais definidas para cada objeto, facilitando manutenção e extensão: JSP não deve conter código algum ou pelo menos não código de controle
- Controle centralizado
	- Facilidade de rastrear e logar requisições
	- Melhor gerenciamento de segurança
	- Requer menos recursos. Não é preciso distribuir pontos de verificação em todas as páginas
	- Validação é simplificada
	- Melhor possibilidade de reuso
	- Distribui melhor as responsabilidades

## Application Controller

- Funciona em conjunto com o Front Controller. 
- Gerencia ações e Views.
- Centraliza operações relacionadas com o processamento e despacho de requisições, tais como redirecionamento para comandos (ações) e viewws para opermitir o reuso do Front Controller

## Context Object

- O objetivo é encapsular estado de um objeto independente do protocolo usado pela aplicação. 
- Permite que aplicação use uma API que isole detalhes do protocolo (HTTP, por exemplo), permitindo que os mesmos dados possam ser lidos em outros objetos.

**Problema:**

- Precisamos evitar usar métodos específicos do protocolo utilizado
- Outros componentes e serviços precisam de informações do sistema e não conhecem a API servlet
- Apenas APIs relevantes ao contexto em questão devem ser expostas

## View Helper

- Separa o código e responsabilidade de formatação da interface do usuário do processamento de dados necessários para a construção da View. 
- Evita que se coloque lógica de programação dentro da view. 
- Permite a divisão de papéis entre desenvolvedores e web designers
- podem guardar modelo de dados intermediário usado pelo View e servir como adaptadores para dados oriundos da camada de negócios
- Algumas tecnologias:
	- Struts
	- JSTL

## Composite View

- Cria um componente de View a partir de views menores (estilo REACT)

![[Untitled 541.png]]

## Service To Worker

- Combinação de Front controller com View Helper
- O Front Controller irá recepcionar a requisição e então invocar um ou mais helpers para:
	- Traduzir a requisição
	- Consultar o banco
	- Selecionar a próxima view
- Então será chamado o dispatcher que fará o redirecionamento para a view selecionada

## Dispatcher View

![[Untitled 542.png]]

# Principais padrões da camada de Negócios (EJB)

## Business Delegate

- Isola o cliente de edetalhes acerca da camada de negócios
- Funcionam como proxies ou fachadas para cada session bean
- Pode realizar cache e outros controles
- Pode permitir a integração entre sistemas diferentes
- Reduz acoplamento

## Service Locator

- Isola o cliente de serviços de localização de recursos (JNDI)
- Abstrai o uso de JNDI
- Centraliza todo o acesso ao servidor JNDI
- Melhora a performance da pesquisa oferecendo um cache para as pesquisas mais frequentes

## Session Facade

- Introduz uma camada controladora entre camada de negócios e de clientes
- Ao invés de o cliente invocar diversos Entity Beans para a execução de uma lógica de negócio que envolva estes, uma **fachada **é criada, de modo que para o cliente apenas uma entidade será envocada. Esta fachada será responsável por invocar todas as entidades envolvidas.
- Expõe uma interface uniforme
- Reduz o acoplamento
- Melhora a performance
- Centraliza o controle de segurança e transações
- Reduz a interface visível aos clientes

## Application Service

- Centraliza a lógica de negócio através de diversos componentes de negócio e serviços
- Usado por session facades
- Funciona como uma sub-fachada, usada pelos sessions facades

## Business Object

- Entity Beans
- Separa os dados da camada de negócio
- POJO

![[Untitled 543.png]]

## Transfer Object

- Reduz a quantidade de requisições necessárias para recuperar um objeto
- Encapsula em um objeto um subconjunto de dados utilizável pelo cliente, utilizando apenas uma requisição para transferi-lo

# Padrões da camada de Integração

## Data Access Object (DAO)

- Encapsula todo o acesso a uma fonte de dados
- Gerencia a conexão com a fonte de dados para obter e armazenar os dados

![[Untitled 544.png]]

- Define uma interface comum de acesso a dados e esconde características de uma implementação específica
- Não mantêm estado nem cache de dados

## Service Activator

- Recebe requisições e mensagens **assíncronas** do cliente.
- Localiza e chama os métodos de negócio necessários para atender a requisição
- Na prática, é um **listener JMS **
	- Pode ser um message driven bean ou aplicação standalone

## Domain Store

- Oferece um mecanismo transparente de persistência para objetos de negócio

## Web Service Broker

- Expõe um ou mais serviços usando XML e protocolos web através de uma interface de baixa granularidade
- Fachada para Web Services
- Integração de aplicações heterogêneas
- Pode ser implementado pela exposição de um documento WSDL