---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2024-10-31T14:46:00
Owner:
  - Eduardo Quinalha
---
> [!note]+ # Mapa Mental
> ![[Spring.png]]

<!-- Column 1 -->
![[nse-4664056658700873756-springAnnotCheet.pdf.pdf]]

<!-- Column 2 -->
> [!note] 🔥
> Anotações que são obrigatórias saber:

@Autowired
@Controller
@Repository
@Service
@PropertySource
@Component
@ComponentScan
@Bean
@Configuration
@Value

# Spring Framework

## Características

- Principal característica do Framework Spring é a inversão de controle por meio de injeção de dependências
	- Provido pela interface `BeanFactory` e sua principal implementação `ApplicationContext`
- Configurações podem ser feitas por arquivos XML, anotações ou código java
- Anotações **têm precedência sobre XML**
- Programação orientada a aspectos
	- Separa funcionalidades transversais do código de negócio principal

## Configurações

- As configurações básicas de uma aplicação spring podem ser feitas pelos seguintes arquivos, que são lidos na ordem abaixo:
	- [bootstrap.properties](http://bootstrap.properties/) (ou bootstrap.yaml)
	- [application.properties](http://application.properties/) (ou application.yaml)

## Anotações

- `@Autowired`
	- Marca um construtor, campo, método setter ou método de configuração para ser conectado automaticamente pelos recursos de injeção de dependência do Spring.
	- `@Primary`
		- Anotação utilizada para desambiguação em caso de injeção de dependências
	- `@Qualifier`
		- Também utilizado para desambiguação
- `@Repository`
	- Camada de dados (DAO)
	- Anota classes na camada de persistência, que atuará como um repositório de banco de dados.
	- o Spring converte exceções específicas do provedor de persistência (como Hibernate, JPA, JDBC) em exceções de Spring DataAccessExceptions mais genéricas, facilitando o tratamento consistente de erros.
	- Faz integração com o Framework Spring Data
		- O Spring Data fornece recursos adicionais, como geração automática de consultas, paginação, ordenação e outros recursos de acesso a dados, que podem ser utilizados em conjunto com a anotação `**@Repository**`.
- `@Service`
	- Especialização do `@Component` Camada de serviço / lógica de negócio
	- Compatibilidade com ferramentas e convenções: A anotação `**@Service**` é reconhecida pelas ferramentas e convenções do ecossistema Spring. Isso significa que IDEs, frameworks e outras ferramentas que trabalham com o Spring podem identificar e tratar adequadamente classes anotadas com `**@Service**`, oferecendo recursos adicionais, como geração de código, análise estática, sugestões de autocompletar, entre outros.
- `@Component`
	- É um estereótipo genérico para qualquer componente gerenciado pelo Spring. 
	- Declara uma classe com esta anotação e assim ela será gerenciada pelo container de **IoC/DI** do Spring. 
	- Assim, a classe será instanciada e registrada no container e enfim pronta para uso.
	- O Spring utiliza o contrutor da classe como ponto de injeção, mas podem existir outros como um método, setter ou a própria variável de instância
- `@RequestMapping`
	- Usada na classe `@Controller` para mapear a requisição feita a uma URL
	- Pode-se utilizar também `@GetMApping` e `@PostMapping`
- `@ResponseBody`
	- Em uma classe anotada com `@controller` o Spring espera que o método anotado com `@RequestMapping` retorne uma String que irá corresponder ao nome do arquivo JSP (ou html) da camada view, de forma a efetivar o server render (Aplicações MVC)
	- Quando uma classe possui a anotação `@ResponseBody` junto de `@RequestMapping` e suas equivalentes (GetMapping, PostMapping), o Spring enviará o retorno da classe direto para o navegador, funcionando como uma aplicação REST
	- Na prática, a própria anotação `@RestController` é a junção de `@Controller` + `@ResponseBody`
- `@Transactional`
	- Usada em classes da camada de negócio
	- Não são utilizadas em classes DAO porque as operações da classe DAO são operações genéricas e isoladas
	- As operações da lógica de negócio agrupam várias operações da camada DAO e de outras também
```java
Bean de Negócio
  @Autowired BeanDAO1
  @Autowired BeanDAO2

  @Transactional  
  meu método de negócio() {
     consulta algo do DAO1
     faz um processamento
     insere algo no DAO2
     faz um update no DAO1
  }
```
	- Pode ser aplicado a um método individual ou a uma classe. Quando aplicado a classe, denota um padrão que será utilizado em todos os métodos da classe
	- Modos de propagação
		- `REQUIRED → Default`
			- Cria um novo contexto caso nenhum exista
			- Reaproveita o contexto existente
		- `MANDATORY`
			- Cria um novo caso não exista
			- Gera uma exception caso nenhum exista
		- `REQUIRES_NEW`
			- Cria um novo contexto
			- Suspende o atual, caso exista
		- `NOT_SUPPORTED`
			- Não cria nenhum novo (Sempre executa sem contexto transacional)
			- Suspende o atual caso exista
		- `NEVER`
			- Só executa em contexto não transacional
			- Gera uma exception caso um contexto atual exista
	- O controle transacional pode ser veito via anotação (@Transactional) o que facilita o controle fino e distribuído do comportamento de cada classe ou também pode ser feito de forma global no arquivo `applicationContext.xml`. Quando feito via XML, pode-se definir um comportamento global para todas as classes, ou delimitá-las por nome (prefixo), por exemplo. Assim todas as classes que iniciarem com um nome específico como `busca*`respeitarão as mesmas regras transacionais globais definidas neste arquivo. Também é possível determinar contextos específicos por pacotes, por exemplo.
```xml
<tx:advice id="txAdvice">
    <!-- the transactional semantics... -->
    <tx:attributes>
        <!-- métodos que começam com 'get' ou 'busca' são read-only -->
        <tx:method name="get*" read-only="true" />
        <tx:method name="busca*" read-only="true" />
        <!-- demais métodos são transacionais por padrão -->
        <tx:method name="*" propagation="REQUIRED" />
    </tx:attributes>
</tx:advice>
```
- `@RestController`
	- Combinação das anotações `@Controller `e `@ResponseBody`
	- garante que todos os métodos da classe sejam tratados como controladores e que o retorno de cada método seja automaticamente serializado em JSON ou em outro formato desejado, dependendo das configurações do Spring.
- `@PropertySource`
	- Permite carregar arquivos de propriedades externos (.properties)
	- Usada em classes de configuração, em conjunto com a anotação `@Configuration`
```java
@Configuration
@PropertySource("classpath:config.properties")
public class AppConfig {
// (...)   
}
```
	- O arquivo de propriedades deve estar localizado no diretório de recursos (`**src/main/resources**`) do projeto.
	- Para injetar os valores carregados, utiliza-se a anotação `@Value`
```java
@Service
public class MyService {
    @Value("${my.property}")
    private String myProperty;
    // (...)
}
```
- `@ComponentScan`
	- usada para configurar e especificar os pacotes que devem ser escaneados em busca de componentes do Spring, como classes anotadas com `**@Component**`, `**@Service**`, `**@Repository**`, `**@Controller**` e outras anotações relacionadas.
	- Usada em conjunto com a anotação `@Configuration` que determina uma classe de configuração do Spring ou na classe de inicialização principal `@SpringBootApplication`
- `@Bean`
	- usada para declarar métodos de criação de beans em classes de configuração do Spring.
	- geralmente usada em classes de configuração do Spring, que são anotadas com `**@Configuration**`.
- `@Scope`
	- Utilizada em conjunto com `@Configuration` e `@Bean` para determinar o escopo do ciclo de vida do componente no contexto do CDI
		- `**singleton**` (padrão): Cria uma única instância do bean por contêiner.
		- `**request**`: Cria uma nova instância do bean para cada requisição HTTP.
		- `**session**`: Cria uma nova instância do bean para cada sessão do usuário.
		- `**application**`: Cria uma única instância do bean para toda a aplicação.

## Interfaces

- `Validator`
	- Utilizado para validação de dados de formulário
	- Equivalente ao HIbernate Validator
```java
@Entity
public class User {
    
    @Id
    @GeneratedValue(strategy = GenerationType.AUTO)
    private long id;
    
    @NotBlank(message = "Name is mandatory")
    private String name;
    
    @NotBlank(message = "Email is mandatory")
    private String email;
    
    // standard constructors / setters / getters / toString
        
}
```
	- Provê anotações para validação de dados
		- `@NotBlank`

# Spring Boot

## Características

- Extensão do framework spring
- Visa fornecer configuração automática
	- Varre o CLASPATH em busca de bibliotecas e componentes específicos e gera a configuração de forma automatica
- Embedes Servlet Container, permite gerar um .jar standalone da aplicação (**fat jar**)
	- Tomcat
	- Jetty
	- Undertow
- Fornece um conjunto de dependências padrão que são usadas comumente
- `@SpringBootApplication`
	- Combinação de 3 anotações:
		- `@EnableAutoConfiguration`
		- `@ComponentScan`
		- `@Configuration`
	- Não é necessário usar as 3. O `@SpringBootApplication `invoca as 3 com valores default
- Recursos embutidos de monitoramento e métricas (**Actuator**)
	- /info → Informações gerais sobre a aplicação: Nome, versão, descrição etc.
	- /health → Informações sobre a saúde da aplicação
	- /metrics → métricas de performance, uso de memória, threads
	- /env → informações sobre ambiente e “runtime”
- Versões atuais dispensam o uso de arquivos XML para configuração
- Cria automaticamente as classes de acesso ao banco de dados
- Logging
	- Padrão Logback
		- Do mesmo criador do Log4j
	- logback-spring.xml
	- logback.xml

## Spring Boot + Docker

[https://spring.io/guides/topicals/spring-boot-docker](https://spring.io/guides/topicals/spring-boot-docker)

- A construção de uma aplicação em Spring Boot resulta em um arquivo jar executável
- Para executar este jar em um container, basta ter uma imagem com uma JVM e executar a chamada desta no entrypoint: 
	- `ENTRYPOINT ["java","-jar","/app.jar"]`
- Desde a versão **2.3.0** do Spring Boot, o arquivo jar gerado inclui informações sobre os layers da aplicação
	- Isto ajuda a construir e subir uma aplicação mais rapidamente em um ambiente de containeres
	- Partindo da premissa de que é provável que o código mude com mais frequência do que suas dependências, esta prática permite que as maiores camadas sejam guardadas em cache
	- A informação de layer do jar pode ser extraída da seguinte forma
```shell
mkdir target/extracted
java -Djarmode=layertools -jar target/*.jar extract --destination target/extracted
docker build -t myorg/myapp .
```
	- O Dockerfile poderia ser assim: 
```docker
FROM eclipse-temurin:17-jdk-alpine
VOLUME /tmp
ARG EXTRACTED=/workspace/app/target/extracted
COPY ${EXTRACTED}/dependencies/ ./
COPY ${EXTRACTED}/spring-boot-loader/ ./
COPY ${EXTRACTED}/snapshot-dependencies/ ./
COPY ${EXTRACTED}/application/ ./
ENTRYPOINT ["java","org.springframework.boot.loader.launch.JarLauncher"]
```

# Spring Data

## Características

- Trabalha com bases relacionais e NoSQL
- Acesso a dados, consultas baseadas no nome do método
- Interfaces de repositório
	- CrudRepository
	- JpaRepository
- Suporte a paginação e classificação
- Auditoria de entidades
- Interfaces
	- CrudRepository
		- save()
		- findOne()
		- findAll()
		- count()
		- delete()
		- exists()
- Anotações
	- `**@Transactional**`
	- `@Query`
		- Consultas personalizadas baseadas em SQL ou CriteriaAPI
	- `@NamedQuery`
		- Consulta nomeada para utilização em diferentes métodos
	- `@Param`
		- Configura os parâmetros em uma PreparedStatement
```java
@Repository
public interface UserRepository extends JpaRepository<User, Long> {

    @Query("SELECT u FROM User u WHERE u.firstName = :firstName AND u.lastName = :lastName")
    List<User> findByFullName(@Param("firstName") String firstName, @Param("lastName") String lastName);

}
```
	- `@Modifying`
		- Força um commit na base
		- Denota uma query que faz inserções ou modificações de dados no banco
	- `@Repository`
	- `@NoRepositoryBean`

# Spring Security

- Utiliza 3 bibliotecas
	- spring-security-core
	- spring-security-web
	- spring-security-cofing
- **applicationContext-security.xml **ou **spring-security.xml** na mesma pasta do **web.xml**
- Também pode ser configurado via Bean

```java
@Configuration 
public class ApplicationConfig extends WebSecurityConfigurerAdapter { 
   @Bean 
   public PasswordEncoder passwordEncoder() { 
      return new BCryptPasswordEncoder(); 
   } 
   @Override 
   protected void configure(HttpSecurity http) throws Exception { 
      http 
      .csrf().disable()
      .authorizeRequests().antMatchers("/register**")
      .permitAll() .anyRequest().authenticated() 
      .and() 
      .formLogin() .loginPage("/login")
      .permitAll() 
      .and() 
      .logout() .invalidateHttpSession(true) 
      .clearAuthentication(true) .permitAll(); 
   }
}
```

- Baseado em **servlet filters**
- Suporta diversos métodos de autenticação. Vem configurado por default com uma autenticação em memória
	- Para esta configuração, precisa-se sobrescrever alguns métodos da interface `UserDetailsService`
```java
@Service
public class SecurityUserDetailsService implements UserDetailsService { 
   @Autowired 
   private UserRepository userRepository; 
   
   @Override 
   public UserDetails loadUserByUsername(String username) 
   throws UsernameNotFoundException { 
      User user = userRepository.findUserByUsername(username) 
         .orElseThrow(() -< new UsernameNotFoundException("User not present")); 
         return user; 
   } 
   public void createUser(UserDetails user) { 
      userRepository.save((User) user); 
   } 
}
```
	- Também é necessário definir um provedor de autenticação, sobrescrevendo o método `authenticate` da interface `AuthenticationProvider`
```java
@Component public class AuthProvider implements AuthenticationProvider {
   private static final int ATTEMPTS_LIMIT = 3; 
   
   @Autowired 
   private SecurityUserDetailsService userDetailsService; 
   @Autowired private PasswordEncoder passwordEncoder; 
   @Autowired private AttemptsRepository attemptsRepository; 
   @Autowired private UserRepository userRepository; 
   @Override 
   public Authentication authenticate(Authentication authentication) 
   throws AuthenticationException {
      String username = authentication.getName();

import com.tutorial.spring.security.formlogin.repository.UserRepository; 

@Component public class AuthProvider implements AuthenticationProvider { 
   private static final int ATTEMPTS_LIMIT = 3; 
   @Autowired private SecurityUserDetailsService userDetailsService; 
   @Autowired private PasswordEncoder passwordEncoder; 
   @Autowired private AttemptsRepository attemptsRepository; 
   @Autowired private UserRepository userRepository; 
   @Override 
   public Authentication authenticate(Authentication authentication) 
   throws AuthenticationException { 
      String username = authentication.getName();
      Optional<Attempts> 
      userAttempts = attemptsRepository.findAttemptsByUsername(username); 
      if (userAttempts.isPresent()) { 
         Attempts attempts = userAttempts.get();
         attempts.setAttempts(0); attemptsRepository.save(attempts); 
      } 
   } 
   private void processFailedAttempts(String username, User user) { 
      Optional<Attempts> 
      userAttempts = attemptsRepository.findAttemptsByUsername(username); 
      if (userAttempts.isEmpty()) { 
         Attempts attempts = new Attempts(); 
         attempts.setUsername(username); 
         attempts.setAttempts(1); 
         attemptsRepository.save(attempts); 
      } else {
         Attempts attempts = userAttempts.get(); 
         attempts.setAttempts(attempts.getAttempts() + 1); 
         attemptsRepository.save(attempts);
      
         if (attempts.getAttempts() + 1 > 
         ATTEMPTS_LIMIT) {
            user.setAccountNonLocked(false); 
            userRepository.save(user); 
            throw new LockedException("Too many invalid attempts. Account is locked!!"); 
         } 
      }
   }
   @Override public boolean supports(Class<?> authentication) { 
      return true; 
   }
}
```
- passwordEncoder
	- Pode utilizar vários algoritmos disponíveis
	- BCryptPasswordEncoder é o mais comum
		- Utiliza um salt para prevenção de ataques por rainbowtables
		- Possui função daptativa com contador de tentativas a fim de evitar ataques de força bruta
			- A cada tentativa mal sucedida o tempo do algoritmo aumenta, tornando-o mais lento
	- NoOpPasswordEcoder
		- Grava em texto claro
		- usado para contextos de desenvolvimento
- Autenticação e Autorização
- Endereça todas as camadas de segurança dentro da aplicação
- Pode ser utilizado em conjunto com aplicações web ou standalone
- Protege contra os principais ataques web
- Configurações realizadas dentro do arquivo **WEB-INF/applicationContext-security.xml**
- Suporta
	- Username and Password
	- OAuth2
	- SAML 2.0
	- Remember Me
	- JAAS
	- OpenID
	- X509
- Anotações
	- `@Secured`
		- Usada em métodos de classes de:
			- Services
			- Controllers
			- Outros componentes 
		- Restringe o acesso aos métodos baseado em papéis
```java
@Secured("ROLE_ADMIN")
public void deleteOrder(Long orderId) {
    // Implementação da lógica de exclusão de pedido
}
```
		- A segurança deve ser habilitada via `@EnableWebSecurity`
	- `@PreAuthorize`
		- Restringe o acesso a métodos com base em expressões
```java
@PreAuthorize("hasRole('ROLE_USER') and #orderId == authentication.principal.orderId")
public void viewOrder(Long orderId) {
    // Implementação da lógica de visualização de pedido
}
```
	- `@EnableWebSecurity`
		- Usada em classes de configuração
		- Habilita a segurança na aplicação Spring
		- A classe deve estender `WebSecurityConfigurerAdapter`

## Thymeleaf

- Template Engine
- Similar ao pug
- HTML, XML, JS, CSS

[[Enviando por email Spring Annotations.pdf]]

[[Spring Boot Annotations .pdf]]

# Spring Web MVC

- Também chamado de Spring MVC
- Construído em cima da ServletAPI
- Utiliza o padrão Front Controller onde a principal Servelt é a `DispatcherServlet`

# GraalVM

*GraalVM* é uma máquina virtual poliglota capaz de executar aplicações escritas em diversas linguagens, como Java, JavaScript, Python, entre outras. Uma de suas características mais notáveis é a capacidade de compilar aplicações em código nativo através do uso de *native images*. Essas imagens nativas são versões compiladas de uma aplicação que podem ser executadas diretamente pelo sistema operacional, sem a necessidade de uma JVM.

Imagens nativas geradas pelo *GraalVM* são conhecidas por ter **menor consumo de memória** e **tempo de inicialização mais rápido**. Isso ocorre porque elas contêm apenas o código necessário para executar a aplicação, sem a sobrecarga de uma JVM inteira. Além disso, como o código já está pré-compilado para a plataforma de destino, não há a necessidade de um tempo de aquecimento (warm-up) que é típico em ambientes JVM tradicionais.