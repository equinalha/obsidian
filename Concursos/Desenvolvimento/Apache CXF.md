---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2024-12-02T08:22:00
Owner:
  - Eduardo Quinalha
---
# Características

- Framework Open Source para desenvolvimento de serviços web
- Suporta SOAP e REST
- Também suporta CORBA
- Facilita a criação de serviços SOAP que seguem o padrão WSDL (Web Services Description Language).
- Permite a criação de serviços RESTful que utilizam HTTP e padrões como JSON ou XML.
- Implementa as especificações JAX-RS e JAX-WS além de acrescentar funcionalidades
- inclui suporte a várias tecnologias de segurança, como **WS-Security,** **OAuth**, **SSL**, além de capacidades de logging e monitoramento de desempenho.
- suporta múltiplos protocolos de transporte, como HTTP, JMS, entre outros.

## Características específicas

- Permite que os clientes chamem serviços SOAP ou REST como se fossem métodos locais, usando proxies dinâmicos.
- Suporte multitransporte e multiprotocolo
	- HTTP, JMS, UDP, Websocket
- Integração avançada com segurança
	- **WS-Security**: Suporte a criptografia, assinatura e tokens de segurança para serviços SOAP.
	- **OAuth** e **OAuth2**: Para autenticação e autorização em serviços RESTful.
	- **SAML (Security Assertion Markup Language)**: Para troca de informações de autenticação e autorização entre serviços.
	- **SSL/TLS**: Suporte a certificados digitais e comunicação segura entre clientes e servidores.
- Configuração flexível
	- Arquivos de configuração XML
		- Mais detalhado e granular
	- Configuração via Spring
		- Baseado em anotações
- Ferramentas
	- **WSDL2Java**
		- Gera código Java automaticamente a partir de arquivos WSDL
	- **Java2WSDL**
		- Gera automaticamente os arquivos WSDL a partir de classes java
	- **WSDL2js**
		- gera código JavaScript a partir de um WSDL
	- **WSDL2rest**
		- converte um WSDL em uma estrutura RESTful
	- **WSDL2idl**
		-  gera arquivos de suporte em forma IDL, a partir de uma arquivo WSDL
- Suporte avançado a REST
	- HATEOAS
	- Filtros e interceptadores

# Anotações

## JAX-WS

- `@``**WebService**`
	- Define que a classe ou interface anotada representa um serviço web SOAP
	- Quando aplicada a uma **classe**, ela transforma essa classe em um **Service Implementation Bean (SIB),** que pode ser **publicado** como um serviço web
	- Quando aplicada a uma **interface**, ela define uma** Service Endpoint Interface (SEI)**, que **especifica as operações (métodos)** que o serviço oferece.
	- **Atributos**
		- **name**
			- Nome do serviço web
			- Usado no WSDL gerado
			- Se não for especificado, será utilizado o nome da classe
		- **targetNamespace**
			- Especifica o nameSpace do XML
		- **serviceName**
			- define o nome do serviço no WSDL
		- **portName**
			- nome da porta associada ao serviço no WSDL
		- **endpointInterface**
			- Especifica a interface (SEI) que a implementação está cumprindo
		- **wsdlLocation**
			- Especifica a localização do arquivo WSDL
			- Utilizado quando o WSDL é predefinido, e não gerado automaticamente
	- Exemplo
```java
@WebService
public interface MeuServicoInterface {
	String dizerOla(String nome);
}
@WebService(endpointInterface = "com.exemplo.MeuServicoInterface")
public class MeuServicoImpl implements MeuServicoInterface {
	public String dizerOla(String nome) {
		return "Olá, " + nome;
	}
}
```
- `**@WebMethod**`
	- Utilizada para expor métodos da classe como operações SOAP.
```java
@WebMethod
public String sayHello(String name) { ... }
```
- `**@WebParam**`` `
	- Define parâmetros dos métodos que são passados via SOAP.
```java
public String sayHello(@WebParam(name = "name") String name) { ... }
```
- `**@WebResult**`
	- Especifica o valor de retorno de uma operação SOAP.
```java
@WebMethod
@WebResult(name = "greetingMessage")
public String sayHello(String name) { ... }
```

## JAX-RS

- `@Path`
	- Define a URL base ou endpoints de um recurso RESTful.
```java
@Path("/users")
public class UserService { ... }
```
- `**@GET, @POST, @PUT, @DELETE**`
	- Especificam o método HTTP que um endpoint deve atender.
- `@PathParam`
	- Indica que um parâmetro de método deve ser extraído da URL.
```java
@GET
@Path("/{id}")
public User getUser(@PathParam("id") int id) { ... }
```

## Anotações de segurança e outras utilizadas

- `**@RolesAllowed**`
	- Define permissões de acesso, especificando quais roles de usuário podem acessar um determinado método.
- `**@Provider**`
	- Marca uma classe como um provedor JAX-RS, usada para manipulação de respostas, serialização e desserialização de entidades.

# Arquitetura

## frontends

- Diferentes APIs usadas para criar e expor os Web Services
- JAX-WS, JAX-RS, Simples e JavaScript

### API Dispatch

- Interface de baixo nível que permite aos desenvolvedores interagir diretamente com mensagens SOAP ou XML no desenvolvimento de serviços web
- interface genérica (javax.xml.ws.Dispatch) que permite a execução direta de operações em serviços web, manipulando explicitamente as mensagens SOAP ou XML
que são trocadas entre o cliente e o servidor

## barramento

- Bus
- Componente central da arquitetura
- Provedor de recursos compartilhados para a execução do CXF

## interceptadores

- Oferecem uma maneira de adicionar funcionalidades transversais, como logging, segurança, manipulação de cabeçalhos, e validação, sem modificar diretamente a lógica
principal do serviço web

## endpoint factories

- Endpoints: 
	- são pontos de acesso de rede onde um serviço web está disponível para ser consumido por clientes
	- é uma URL ou endereço
- endpoint factory
	- são componentes responsáveis pela criação e configuração de endpoints para serviços web
- **ServerFactoryBean**
	- Utilizada para criar e configurar servidores que expõem serviços web SOAP
	- Permite definir a classe de serviço, o endereço do endpoint e outros parâmetros essenciais para a publicação de um serviço SOAP
- **JAXWsServerFactoryBean**
- **JAXRSServerFactoryBean**
- **Spring Configuration **
	- Facilita a integração com o Spring Framework
- **ClientProxyFactoryBean**
	- Utilizada para criar proxies de cliente para consumir serviços web SOAP

## trasnportadores

- Gerenciam o transporte de mensagens entre clientes e servidores
- Definem o protocolo e o meio de comunicação que será utilizado para enviar e receber mensagens, seja em serviços SOAP ou RESTful.
- Permite que a transmissão de dados binários seja feita por meio de mensagens MIME
	- A vantagem de utilizar MIME ao invés de BASE64 é que este aumenta o tamanho da mensagem
	- O MIME, em conjunto ao MTOM, permite que dados multimídia sejam transmitidos em formato binário e de forma eficiente, quebrando a mensagem em múltiplas partes.

## ferramentas

- Utilitários que facilitam o desenvolvimento, a geração, o teste e a manutenção de serviços web.