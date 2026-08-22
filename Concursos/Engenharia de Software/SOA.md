---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2024-11-05T10:45:00
Owner:
  - Eduardo Quinalha
---
> [!note] 🔥
> SOA é um paradigma para organização e utilização de recursos distribuídos que estão sob controle de diferentes domínios proprietários, permitindo que funcionalidades implementadas sejam disponibilizadas na forma de serviços fracamente acoplados

> [!note] 🔥
> SOA pode ser realizada através de uma variedade de tecnologias e padrões.

# Service-Oriented Architecture

> [!tip] 💡
> **Estilo de arquitetura de software que promove a interoperabilidade entre diferentes sistemas e componentes**

- Independente de linguagem de programação utilizada
- Independente do protocolo de mensagem utilizado
	- clientes e componentes podem se comunicar uns com os outros usando diferentes formatos de mensagens, como SOAP, REST, JSON, XML, entre outros.
- Serviços são agnósticos, ou seja, não são vinculados a um único processo de negócio. Suas capacidades são genéricas
- Grande potencial de reuso
- Características dos serviços
	- Reutilizáveis
	- Compartilham um contrato formal
	- Baixo acoplamento
	- Abstraem a lógica
	- Capazes de se comporem
	- Autônomos
	- Evitam alocação de recursos por longos períodos
- Objetivos
	- maior interoperabilidade intrínseca;
	- maior federação;
	- maior diversificação de fornecedores.

## SOA vs Web Services

**SOA:** Modelo de arquitetura agnóstico

**Web Services:** Realiza o modelo SOA. Plataforma de tecnologia

**Outras tecnologias associadas:**

- DCOM
- CORBA
- RPC
- DDS
- WCF

## **Pilares**

- **Visibilidade entre provedores de serviços e consumidores de serviços**
- **Interação entre provedores e consumidores de serviços**
- **Efeitos no mundo real da interação com um serviço**

## Conceitos

- **Descrição do serviço** é um conjunto de informações necessários para utilizar um serviço, facilitando a interação e a visibilidade.
- **Contratos e políticas** são restrições ou condições de uso de um serviço
- **Contexto de execução** é um caminho estabelecido entre os participantes, constituído por participantes, infraestrutura, etc
- **Troca de mensagens**
	- Utiliza formatos como XML, JSON, SOAP

## Modelos de Implementação

![[Untitled 364.png|Modelo Triangular]]

## Modelo Triangular

- Antigamente, havia um Modelo End-To-End, isto é, os prestadores de serviços notificavam os solicitantes de serviços sobre serviços disponíveis; os solicitantes de serviços, então, invocavam os serviços. 
- Esse modelo foi substituído por um Modelo Triangular, que fornece uma estrutura subjacente para criação, registro, descoberta e composição de serviços distribuídos.
- Papéis
	- Prestador de Serviços → Publica serviços em um registro de serviços
	- Registro de serviços → Registra e organiza os serviços publicados
		- Possui duas interfaces:
			- Publicação de serviços
			- Busca por serviços
		- **o provedor determina o comportamento daquele que está disponibilizando o serviço, isto é, é considerado o dono do serviço**
		- **o registro determina o comportamento que a organização deve ter para divulgar seu serviço e o do cliente que deve proceder para localizar o serviço desejado.**
	- Solicitante de serviços →Se conecta ao prestador de serviço, e remotamente invoca o serviço do prestador
		- Se um solicitante de serviço estiver ciente de um prestador de serviço apropriado, ele já pode decidir se conectar diretamente ao prestador de serviço sem sequer consultar o registro de serviços. A vantagem do registro é que se pode procurar e descobrir serviços
apropriados.
		- Um consumidor pode ser representado por uma pessoa, uma organização, uma máquina ou um componente de software.
- Além dos 3 acima (provedor e consumidor) destacam-se:
	- **Consultor de Negócios:** Responsável pelo mapeamento dos processos de negócio da organização
	- **Arquiteto SOA: **Responsável pela modelagem dos serviços, além da construção, instalação e manutenção
- Implementações
	- Publish-Find-Bind
		- Registro de Serviços → Broker de Serviços
	- Find-Bind-Execute
		- Caso o consumidor encontre o serviço desejado, é criado um contrato e devolve-se um endereço (comumente chamado de endpoint) para utilização do serviço

## Princípios de Design

> [!note] 🔥
> Incidência alta em prova

- **Contrato de Serviço Padronizado**
	- Trazem detalhes da funcionalidade provida por um serviço
	- Pode conter SLA
	- Expõe as características e funcionalidades
- **Baixo Acoplamento de Serviços**
	- Para diminuir dependência entre serviços, utiliza-se ESB:
		- **ESB (Enterprise Service Bus)**
			- Abstrai a forma de troca de mensagens feitas pelos sistemas
			- Pacote de estilos diferentes de mensagens, combinadas com serviços de registro e de segurança
			- **Existe ESB sem SOA e SOA sem ESB!**
![[Untitled 365.png]]
- **Abstração de Serviços**
	- Trata serviços como uma caixa preta
	- Entrada e saída são imutáveis (definidos em contrato)
	- A implementação pode ser alterada
- **Reusabilidade de Serviços**
	- é uma consequência do Princípio do Baixo Acoplamento.
	- Um serviço reutilizável é aquele que não carrega particularidades técnicas de uma implementação ou regra de negócio específica e é genérico o
suficiente para atender outros projetos.
	- Essa autonomia é medida e disponibilizada nos contratos formais, tendo como finalidade esclarecer o nível de independência aos seus consumidores.
- **Autonomia de Serviços**
	- É a capacidade de um serviço se auto-administrar
	- independe de um elemento externo para executar sua lógica
- **Independência de Estados de Serviços**
	- Serviços são stateless
	- Não guardam o estado
- **Visibilidade de Serviços**
	- Service Discovery
	- Objetivo é tornar o serviço visível a todos
- **Composição de Serviços**
	- Serviços são projetados para atuar como participantes eficazes de uma composição, independentemente do tamanho e complexidade desta
	- As capacidades de um serviço podem ser combinadas várias vezes
	- Pequenos serviços se compõem para formar serviços maiores
![[Untitled 366.png]]

### Enterprise Service Bus (ESB)

- Integra sistemas **Heterogêneos**
- Oferece um conjunto abrangente de capacidades que são essenciais para o gerenciamento de interações de serviços em uma arquitetura orientada a serviços (**SOA**).
- **Funções**
	- Transformação de modelos de dados
	- Manuseio de conectividade e mensagens
		- Aspectos como transporte, formatação e protocolos
	- Execução de roteamento
		- Baseado em regras de negócio ou conteúdo das mensagens
	- Conversão de protocolos
	- Gerenciamento das requisições

## Orquestração de serviços

- **Processo centralizado** que controla e coordena as interações entre diferentes serviços
- **WS-BPEL**
	- Web Services Business Process Execution Language
	- Linguagem executável com variáveis e tratamento de exceções
	- Segue o Padrão OASIS
	- Especifica o fluxo de ações de processos de negócios e orquestra os serviços

## Coreografia de Serviços

- Não possui um coordenador central, como na orquestração
- Cada serviço sabe seu momento de execução e com quem interagir
- Distribuído, descentralizado
- **WS-CDL**
	- Web Services Choreography Description Language
	- Linguagem descritiva
- SCA - Service Component Architecture
	- Modelo de construção de aplicativos com base em SOA
	- Modelo de composição de serviços para criação de componentes

# Mensageria

- Maneira de resolver problemas complexos de integração de sistemas por meio de comunicação indireta entre as partes
- Indireta = middleware
- Padrão de comunicação assíncrona utilizado em sistemas distribuídos

# CORBA

- **Arquitetura padrão de software baseada em objetos**
- Com o CORBA, os objetos distribuídos podem ser acessados de forma transparente, **como se fossem objetos locais,** independentemente de onde estejam executando.
- utiliza o Protocolo **IIOP **(Internet Inter-ORB Protocol)
- Sua adoção diminuiu com o tempo em favor de tecnologias mais recentes, como WS e SOA.
- utiliza um modelo **cliente/servidor**
- Estabelece e simplifica a troca de dados entre sistemas distribuídos heterogêneos
- Gerenciamento de objetos distribuídos

## Componentes Principais

### **ORB (Object Request Broker)**

- Módulo intermediário entre cliente e objeto
- Aceita requisições e encaminha ao objeto correto

### IDL

- Interface Definition Language
- Descreve as interfaces das implementações dos objetos
- **Similar ao WSDL**
- Descreve o formato das chamadas e parâmetros de entrada ou saída necessários para efetuar a operação

### POA

- Portable Object Adapter
- Gerencia a criação, destruição e associação de objetos servidores ao ORB
- Permite que os objetos sejam ativados e desativados
- Otimiza os recursos do ORB

### Serviços CORBA

- Define um conjunto de serviços que suportam operações distribuídas comuns como transações, segurança e persistência
- Estendem as capacidades do ORB

# Modelo de Maturidade SOA

Um modelo de maturidade da SOA (Service-Oriented Architecture) é uma ferramenta que ajuda as organizações a avaliar o **nível de maturidade **de sua implementação da SOA. Ele fornece um conjunto de critérios que podem ser usados para medir o progresso da organização em direção à adoção completa da SOA.

Existem vários modelos de maturidade da SOA disponíveis, cada um com seu próprio conjunto de critérios. Alguns dos modelos mais populares incluem:

- **SOAMM (Service-Oriented Architecture Maturity Model)**: Este modelo foi desenvolvido pela OMG (Object Management Group) e é um dos modelos mais abrangentes disponíveis. O SOAMM define cinco níveis de maturidade: inicial, definido, gerenciado, otimizado e inovador.
- **OSIMM (Open SOA Maturity Model)**: Este modelo foi desenvolvido pela SOA Consortium e é um modelo mais leve que o SOAMM. O OSIMM define quatro níveis de maturidade: inicial, repetível, gerenciado e otimizado.
- **Zachman Framework for Enterprise Architecture**: Este modelo não é específico da SOA, mas pode ser usado para avaliar a maturidade da SOA de uma organização. O Zachman Framework define seis níveis de maturidade: contexto, conceitos, sistema, tecnologia, detalhes e funcionamento.
- **Nível 1 - Processo de desenvolvimento tradicional**: determina um processo de desenvolvimento que não utiliza uma abordagem orientada a serviços como modelo de solução tecnológica. Nesse nível, a organização não está interessada em utilizar soluções SOA como estratégia de alinhamento.
- **Nível 2 - Processo de desenvolvimento orientado a serviços, apoiado por soluções de TI simples: **determina um processo de desenvolvimento SOA apoiado por soluções e serviços Web dentro de uma arquitetura composta por serviços simples sem a colaboração esperada em soluções de grande porte (sincronismo de dados, serviços de autenticação e funcionalidades simples).
- **Nível 3 - Processo de desenvolvimento orientado a serviços, apoiado por soluções de TI compostas: **determina um processo de desenvolvimento SOA apoiado pela colaboração e orquestração de sistemas e serviços de TI que interagem para fornecer soluções lógica e semanticamente complexas.
- **Nível 4 - Processo de automação do negócio pelo uso de soluções de TI compostas: **determina um processo de desenvolvimento onde a organização utiliza todo o potencial fornecido pelas soluções orientadas a serviços compostas para automatizar e otimizar o alinhamento estratégico entre a TI e o negócio.