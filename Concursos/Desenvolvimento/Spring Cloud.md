---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2024-10-14T14:38:00
Owner:
  - Eduardo Quinalha
---
> [!note]+ # Mapa Mental
> ![[SpringCloud.png]]

# Spring Cloud

## Características

- Construir aplicações cloud native
	- Versionadas
	- DDD
	- Configurações externalizadas
	- Containers
	- Microsserviços
- Aplicações distribuídas
- Cloud Agnostic
- Configuração distribuída
- Service Discovery
- Routing
- Load Balancer
- Mensageria

## Principais Componentes

### Spring Cloud Config

- Provê injeção de configurações para os conteineres
- Pode carregar de várias fontes:
	- Sistema de arquivos local
	- Repositório Git
	- Servidores de configuração externos
	- Bancos de dados
- Pode fazer criptografia
	- Dados sensíveis podem ser criptografados na fonte e abertos na leitura
- A configuração pode ser atualizada no servidor de configuração, e o serviço cliente pode buscar a nova configuração sem a necessidade de reinicialização.
- O Spring Boot automaticamente busca por um config server em` `[`http://localhost:8888`](http://localhost:8888/)
- **Configurações básicas do config server**
	- Dependência: `spring-cloud-config-server`
	- application.properties
```java
spring.application.name=config-server
server.port=8888

spring.cloud.config.server.git.uri=<URL do repositório Git>
spring.cloud.config.server.git.clone-on-start=true
```
- **Configuração básica de uma aplicação cliente**
	- Dependência: `spring-cloud-starter-config`
	- application.properties
```java
spring.application.name=my-application
spring.cloud.config.uri=http://localhost:8888
```
	- Usando as propriedades
```java
@RestController
public class MyController {

    @Value("${my.property}")
    private String myProperty;

    @GetMapping("/my-property")
    public String getMyProperty() {
        return myProperty;
    }
}
```
	- As propriedades dentro do repositório ficam armazenadas como arquivos `.properties` ou YAML
```java
/my-application-dev.properties
/my-application-prod.properties
/my-application-dev.yml
/my-application-prod.yml
```

### Eureka (Netflix Eureka)

- Service Discovery
- Também conhecido como netflix-eureka
- permite que os microsserviços se registrem e se descubram dinamicamente
- facilita o balanceamento de carga e a comunicação entre os serviços
- A funcionalidade central do Eureka é o registro dos serviços. 
	- Cada microsserviço, ao iniciar, registra-se no servidor do Eureka, informando seu nome, endereço IP, porta e outras informações relevantes. 
	- O servidor Eureka mantém um registro atualizado dos serviços disponíveis e suas instâncias.
	- Quando um serviço deseja se comunicar com outro serviço, ele consulta o servidor Eureka para obter a lista atualizada de instâncias do serviço de destino. 
	- Isso permite que o serviço de origem faça chamadas diretamente às instâncias disponíveis do serviço de destino, sem precisar conhecer os detalhes específicos de endereçamento.
- O Eureka oferece recursos adicionais, como tolerância a falhas, monitoramento e segurança, que podem ser configurados e personalizados de acordo com as necessidades do seu aplicativo.
- Uma vez que as bibliotecas estejam no CLASSPATH, qualquer aplicação Spring Boot com a anotação `@EnableEurekaClient` tentará se comunicar com um servidor Eureka em `http://localhost:8761`
- Na aplicação cliente, basta solicitar o serviço desejado com a URL: `http://<nome da aplicação>/(…)` 
- **Configurações básicas do Eureka Server:**
	- Dependência `spring-cloud-starter-netflix-eureka-server`
	- application.properties
```java
server.port=8761
eureka.client.register-with-eureka=false
eureka.client.fetch-registry=false
```
	- A configuração `**eureka.client.register-with-eureka**` é definida como `**false**` para que o servidor não se registre em si mesmo. 
	- A configuração `**eureka.client.fetch-registry**` também é definida como `**false**` para que o servidor não busque informações de registro de outros servidores.
	- Classe de configuração
```java
@SpringBootApplication
@EnableEurekaServer
public class EurekaServerApplication {
    public static void main(String[] args) {
        SpringApplication.run(EurekaServerApplication.class, args);
    }
}
```
- **Configurações básicas de um Eureka Client**
	- Dependência `spring-cloud-starter-netflix-eureka-client`
	- application.properties
```java
spring.application.name=my-client
server.port=8080
eureka.client.service-url.defaultZone=http://localhost:8761/eureka/
```
	- `**eureka.client.service-url.defaultZone**` é configurada com a URL do servidor Eureka.
	- Classe de configuração
```java
@SpringBootApplication
@EnableEurekaClient
public class MyClientApplication {
    public static void main(String[] args) {
        SpringApplication.run(MyClientApplication.class, args);
    }
}
```

### Zuul (Netflix Zuul)

- Desacopla o frontend do backend
- É um proxy reverso
- Desonera o backend do tratamento de segurança
- Rotear e filtrar o tráfego entre os clientes e os microsserviços
- Ponto de entrada único para todas as solicitações externas, redirecionando-as para os serviços apropriados com base em determinadas regras de roteamento.
	- Equivalente ao ingress do kubernetes
- **Configurando um servidor zuul básico**
	- Dependência: `spring-cloud-starter-netflix-zuul`
	- application.properties
```java
spring.application.name=zuul-gateway
server.port=8080

zuul.routes.api-a.url=http://localhost:8081
zuul.routes.api-a.path=/api/a/**

zuul.routes.api-b.url=http://localhost:8082
zuul.routes.api-b.path=/api/b/**
```
	- Classe de configuração
```java
@SpringBootApplication
@EnableZuulProxy
public class ZuulGatewayApplication {
    public static void main(String[] args) {
        SpringApplication.run(ZuulGatewayApplication.class, args);
    }
}
```
	- A anotação `**@EnableZuulProxy**` habilita a aplicação como um servidor proxy Zuul.

# Componentes principais do Spring Cloud

[https://github.com/ryanjbaxter/beginners-guide-to-spring-cloud/tree/master](https://github.com/ryanjbaxter/beginners-guide-to-spring-cloud/tree/master)

![[Untitled 798.png]]

- Service Discovery:
	- Netflix Eureka
	- Zookeeper
	- Consul
- Rounting and Messaging
	- Routing and Load Balancing
		- Netflix Ribbon
		- Open Feign
	- Messaging
		- RabbitMQ
		- Kafka
- API Gateway
	- Netflix Zuul
	- Spring Cloud Gateway

![[Untitled 799.png]]

- Circuit Breakers
	- Proteção dos microsserviços
	- Netflix Hystrix
- Tracing
	- Utilizado para diagnósticos e debugging
	- Spring Cloud Sleuth and Zipkin
- CI Pipelines and Testing
	- 