---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2024-08-26T17:59:00
Owner:
  - Eduardo Quinalha
---
# Java EE / Jakarta EE / J2EE

<!-- Column 1 -->
- Java SE = JRE / JDK
JRE → JVM
JDK → JRE + API`s

## Camadas

1. Cliente
2. Web
3. Negócio
4. Dados
- Java EE = Java SE + API`s:
	- JSP, 
	- JDBC, 
	- Servlet, 
	- JPA, 
	- JTA, 
	- JAX_RS (Rest API), 
	- JAX_WS (WebService), 
	- CDI, 
	- EJB

<!-- Column 2 -->
![[Untitled 768.png]]


## Implementações

Tanto o Java SE quanto o Java EE são especificações. No caso do Java SE, as implementações são como o OpenJDK, etc..
No Java EE, as implementações são os servidores de aplicação como:

- Wildfly
- Websphere
- Weblogic
- Jboss

**Tomcat:** Trata-se de um** ****servlet container** (Também conhecido como** Container Web**). Somente implementam as especificações** JSP e Servlet**

- Tomcat
- Jetty

![[Untitled 769.png]]

### Versões:

Atualmente o JavaSE está na versão 19 e o Jakarta EE na versão 10. O Java EE parou na 8

O nome correto é **Jakarta EE**, uma vez que a Oracle abandonou o suporte e passou a ser mantido pela comunidade, em sua maioria, da eclipse foundation

## Spring

Possibilita programar aplicações web, porém sem utilizar a especificação do Java EE / Jakarta EE

Por consequências, o Spring evolui muito mais rapidamente do que o Java EE

<!-- Column 1 -->
![[Untitled 770.png]]

<!-- Column 2 -->
![[Untitled 771.png]]

![[Untitled 772.png]]

# Micro-serviços

## Microprofiles

Aplicação java que já tem embutido um servlet container e cujo desenvolvimento é muito simples! Vc roda quase como se fosse uma aplicação java pura.
Esta arquitetura é otimizada para micro-serviços

<!-- Column 1 -->
```java
// Exemplo usando spark
import static spark.Spark.*;

public class HelloWorld {
    public static void main(String[] args) {
        get("/hello", (req, res) -> "Hello World");
    }
}
```

<!-- Column 2 -->
[https://sparkjava.com/](https://sparkjava.com/)

[https://www.alura.com.br/artigos/morte-a-sessao-entenda-esse-tal-de-stateless-session-com-tokens](https://www.alura.com.br/artigos/morte-a-sessao-entenda-esse-tal-de-stateless-session-com-tokens)

# Resumo da sopa de letrinhas

> [!note] 🔥
> **JPA**
Java Persistence API → API que define métodos para serem utilizados com POJOS para prover persistência. Não é o ORM em si, mas provê os métodos para implementação de um

*um framework utilizado na camada de persistência, define uma forma para mapear POJO (plain old Java objects) para um banco de dados.*

> [!note] 🔥
> **Facelets
**Subproduto do JSF → Renderização de páginas pelo servidor

*parte do projeto de JSF, utiliza XHTML como tecnologia de apresentação dos dados, possibilitando a separação entre as camadas de negócio e de controle.*

> [!note] 🔥
> **JNDI**
Provê um serviço de nomes para busca. Oculta, por exemplo, detalhes de conexão com o banco. Vc pode fornecer apenas o JNDI para a aplicação e o endereço do banco de dados ser controlado por fora. Semelhante ao TNS

*componentes da arquitetura J2EE, permitem localizar objetos, distribuí-los e integrá-los por meio dos mecanismos integração e localização de serviços de nome*

> [!note] 🔥
> **RMI
**Remote Method Invocation → Comunicação entre aplicações

> [!note] 🔥
> **EJB
**Objetos distribuídos entre aplicações web

# JMS

Troca de mensagens entre aplicações

As operações são feitas de forma assíncrona

# Implantação

Existem 3 tipos básicos de módulos. A extensão destes arquivos serve para o servidor diferenciar o que está sendo implantado

- EAR → META-INF/application.xml
	- Enterprise Application Archives
	- Aplicação completa com todos seu módulos e componentes
- Web Module (WAR) → WEB-INF/web.xml
	- Contém a aplicação Web
- EJB Module (JAR) → META-INF/ejb-jar.xml
	- Java Application Archive
	- Contém aplicação EJB
	- Aplicação cliente
- Connector Module  (RAR) → META-INF/ra.xml
	- Resource Adapter
	- Interfaces, classes, bibliotecas, etc..

# Annotations

## Principais

**@Generated**

Marca um código fonte que foi gerado automaticamente

@Resource

- Injeção de dependência. 
- Quando aplicada a um campo ou método, o contêiner injetará uma instância do recurso requisitado quando a aplicação foi inicializada.
- Se for aplicada a uma classe, declara um recurso que a aplicação vai procurar em tempo de execução

**@Resources**

Usada para declarar depedência de um conjutno de recursos

**@PostConstruct**

- Método que será executado após uma injeção de dependência terminar.
- Usada para inicialização

**@PreDestroy**

- Utilizado para liberar recursos