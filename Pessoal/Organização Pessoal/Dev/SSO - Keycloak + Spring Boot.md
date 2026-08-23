---

---
[https://jarmx.blogspot.com/2022/04/single-sign-on-with-keycloak-and-spring.html](https://jarmx.blogspot.com/2022/04/single-sign-on-with-keycloak-and-spring.html)

## Single Sign-On with Keycloak 17.0.1 and Spring Boot 2.6 or later.

### Single Sign-On (SSO)

[Single Sign-On](https://www.techtarget.com/searchsecurity/definition/single-sign-on) Is an authentication method that permits a user to use one set of login credentials with multiple application.

### Keycloak

Keycloak is an open source identity and access management for modern applications and services, no need to deal with storing users or authenticating users. it's all available out of the box.

You'll even get advanced features such as user federation (LDAP or Kerberos) and social login.

The Documentation keycloak mentioned the following with respect [SSO](https://www.keycloak.org/): Users authenticate with Keycloak rather than individual applications. This means that your applications don't have to deal with login forms, authenticating users, and storing users. Once logged-in to Keycloak, users don't have to login again to access a different application.

This also applied to logout. Keycloak provides single-sign out, which means users only have to logout once to be logged-out of all applications that use Keycloak.

### Downloading and installing keycloack by Docker

For Install [keycloak by docker](https://www.keycloak.org/getting-started/getting-started-docker) you just need the next command:

```plain text
docker run -p 8080:8080 -e KEYCLOAK_ADMIN=admin -e KEYCLOAK_ADMIN_PASSWORD=admin quay.io/keycloak/keycloak:17.0.1 start-dev
```

This will start Keycloak exposed on the local port **8080**. It will also create an initial admin user with username **admin** and password **admin**.

### Setting Up a keycloack server.

Open a browser http://localhost:8080 or http://127.0.0.1:8080 result this.

We can now proceed to the Administrative Console.

![[sso1.png]]

![[sso2.png]]

### Creating a Realm

For default the console opens up Master realm, Let's navigate left corner Add realm button.

![[sso3.png]]

For this example I created realm **demo**. we'll click the button create.

![[sso4.png]]

![[sso5.png]]

Add a new client with the name **spring-boot-keycloak** with openid-connect. click button save.

![[sso6.png]]

Add Valid Redirect URIs.

![[sso7.png]]

![[sso8.png]]

Add next role, **user**.

![[sso9.png]]

### Creating a Users

Add next user: **user1** password **user1** and role **user**.

![[sso10.png]]

![[sso11.png]]

![[sso12.png]]

![[sso13.png]]

## Creating a Spring Boot Application

In this examples we're integration Spring Boot and keycloack.

- Configuration Spring boot, Spring Data and keycloack.
- Define Data Models, Repository.
- Spring Controllers

### Technology

- Java 17
- Spring Boot 2.6.6
- HyperSQL 2.5.2
- Maven 3.6.3
- Thymeleaf 2.6.6
- IntelliJ IDEA

![[AVvXsEjWnTJWGTI77IUYj3T_qh_cmhGstobUWU-FP1RdiM7NjuBfEsr1XipghgXT3enHMVJ_M68LykCHwvsGqLCL-NHvuZ1LgLa7px4j82P6LD0_6co4vLMhnCHyXuJFnp2BjUyXyaml0NgKArnYEp_c.bin]]

### **pom.xml**

```plain text
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
   xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 https://maven.apache.org/xsd/maven-4.0.0.xsd">
   <modelVersion>4.0.0</modelVersion>
   <parent>
      <groupId>org.springframework.boot</groupId>
      <artifactId>spring-boot-starter-parent</artifactId>
      <version>2.6.6</version>
      <relativePath/> <!-- lookup parent from repository -->
   </parent>
   <groupId>com.henry</groupId>
   <artifactId>sso-spring-boot-keycloak</artifactId>
   <version>0.0.1-SNAPSHOT</version>
   <name>sso-spring-boot-keycloak</name>
   <description>Demo project for Spring Boot</description>
   <properties>
      <java.version>17</java.version>
      <keycloak-adapter-bom.version>17.0.1</keycloak-adapter-bom.version>
   </properties>
   <dependencyManagement>
      <dependencies>
         <dependency>
            <groupId>org.keycloak.bom</groupId>
            <artifactId>keycloak-adapter-bom</artifactId>
            <version>${keycloak-adapter-bom.version}</version>
            <type>pom</type>
            <scope>import</scope>
         </dependency>
      </dependencies>
   </dependencyManagement>
   <dependencies>
      <dependency>
         <groupId>org.springframework.boot</groupId>
         <artifactId>spring-boot-starter</artifactId>
      </dependency>
      <dependency>
         <groupId>org.keycloak</groupId>
         <artifactId>keycloak-spring-boot-starter</artifactId>
      </dependency>
      <dependency>
         <groupId>org.springframework.boot</groupId>
         <artifactId>spring-boot-starter-data-jpa</artifactId>
      </dependency>
      <dependency>
         <groupId>org.springframework.boot</groupId>
         <artifactId>spring-boot-starter-test</artifactId>
         <scope>test</scope>
      </dependency>
      <dependency>
         <groupId>org.springframework.boot</groupId>
         <artifactId>spring-boot-starter-security</artifactId>
      </dependency>
      <dependency>
         <groupId>org.springframework.boot</groupId>
         <artifactId>spring-boot-starter-web</artifactId>
         <exclusions>
            <!-- Exclude the Tomcat dependency -->
            <exclusion>
               <groupId>org.springframework.boot</groupId>
               <artifactId>spring-boot-starter-tomcat</artifactId>
            </exclusion>
         </exclusions>
      </dependency>
      <!-- Use Jetty instead -->
      <dependency>
         <groupId>org.springframework.boot</groupId>
         <artifactId>spring-boot-starter-jetty</artifactId>
      </dependency>
      <dependency>
         <groupId>org.hsqldb</groupId>
         <artifactId>hsqldb</artifactId>
         <scope>runtime</scope>
      </dependency>
      <dependency>
         <groupId>org.springframework.boot</groupId>
         <artifactId>spring-boot-starter-thymeleaf</artifactId>
      </dependency>
      <dependency>
         <groupId>org.projectlombok</groupId>
         <artifactId>lombok</artifactId>
         <optional>true</optional>
      </dependency>
      <dependency>
         <groupId>org.springframework.security</groupId>
         <artifactId>spring-security-test</artifactId>
         <scope>test</scope>
      </dependency>
   </dependencies>

   <build>
      <plugins>
         <plugin>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-maven-plugin</artifactId>
         </plugin>
      </plugins>
   </build>

</project>

```

```plain text

server:
  port: 8081
keycloak:
  auth-server-url: http://127.0.0.1:8080
  realm: demo
  resource: spring-boot-keycloak
  public-client: true
  principal-attribute: preferred_username
package com.henry.ssospringbootkeycloak.configuration;

import org.keycloak.adapters.springsecurity.KeycloakConfiguration;
import org.keycloak.adapters.springsecurity.authentication.KeycloakAuthenticationProvider;
import org.keycloak.adapters.springsecurity.config.KeycloakWebSecurityConfigurerAdapter;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.context.annotation.Bean;
import org.springframework.security.config.annotation.authentication.builders.AuthenticationManagerBuilder;
import org.springframework.security.config.annotation.web.builders.HttpSecurity;
import org.springframework.security.core.authority.mapping.SimpleAuthorityMapper;
import org.springframework.security.core.session.SessionRegistryImpl;
import org.springframework.security.web.authentication.session.RegisterSessionAuthenticationStrategy;
import org.springframework.security.web.authentication.session.SessionAuthenticationStrategy;

@KeycloakConfiguration
class SecurityConfig extends KeycloakWebSecurityConfigurerAdapter {
    /**
     * Registers the KeycloakAuthenticationProvider with the authentication manager.
     */
    @Autowired
    public void configureGlobal(AuthenticationManagerBuilder auth) throws Exception {

        KeycloakAuthenticationProvider keycloakAuthenticationProvider = new KeycloakAuthenticationProvider();
        keycloakAuthenticationProvider.setGrantedAuthoritiesMapper(new SimpleAuthorityMapper());
        auth.authenticationProvider(keycloakAuthenticationProvider);
    }

    /**
     * Defines the session authentication strategy.
     */
    @Bean
    @Override
    protected SessionAuthenticationStrategy sessionAuthenticationStrategy() {
        return new RegisterSessionAuthenticationStrategy(new SessionRegistryImpl());
    }

    @Override
    protected void configure(HttpSecurity http) throws Exception {
        super.configure(http);
        http.authorizeRequests()
                .antMatchers("/customers*", "/home*", "/info*")
                .hasRole("user")
                .anyRequest()
                .permitAll();
    }
}

package com.henry.ssospringbootkeycloak.configuration;

import org.keycloak.adapters.springboot.KeycloakSpringBootConfigResolver;
import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.Configuration;

@Configuration
public class KeycloakConfig {

    @Bean
    public KeycloakSpringBootConfigResolver keycloakConfigResolver() {
        return new KeycloakSpringBootConfigResolver();
    }
}

Data class model
package com.henry.ssospringbootkeycloak.model;

import javax.persistence.*;

import lombok.AllArgsConstructor;
import lombok.Data;
import lombok.NoArgsConstructor;

@AllArgsConstructor
@NoArgsConstructor
@Data
@Entity
@Table
public class Customer {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private long id;
    private String name;
    private String serviceRendered;
    private String address;


}

Repository Interface

package com.henry.ssospringbootkeycloak.repository;

import com.henry.ssospringbootkeycloak.model.Customer;
import org.springframework.data.repository.CrudRepository;

public interface CustomerDAO extends CrudRepository<Customer, Long> {

}


package com.henry.ssospringbootkeycloak.controller;

import com.henry.ssospringbootkeycloak.model.Customer;
import com.henry.ssospringbootkeycloak.repository.CustomerDAO;
import org.springframework.stereotype.Controller;
import org.springframework.ui.Model;
import org.springframework.web.bind.annotation.GetMapping;

import javax.servlet.http.HttpServletRequest;
import java.security.Principal;
import java.util.Date;

@Controller
public class SsoController {

    private final CustomerDAO customerDAO;

    public SsoController(CustomerDAO customerDAO) {
        this.customerDAO = customerDAO;
    }

    @GetMapping(path = "/")
    public String index() {
        return "redirect:/home";
    }

    @GetMapping(path = "/home")
    public String home(Model model) {
        model.addAttribute("date", new Date());
        return "home";
    }

    @GetMapping(path = "/info")
    public String info(Principal principal, Model model) {
        model.addAttribute("username", principal.getName());
        model.addAttribute("birthday", -1);
        return "user";
    }

    @GetMapping("/logout")
    public String logout(HttpServletRequest request) throws Exception {
        request.logout();
        return "redirect:/";
    }

    @GetMapping(path = "/customers")
    public String customers(Principal principal, Model model) {
        addCustomers();
        Iterable<Customer> customers = customerDAO.findAll();
        model.addAttribute("customers", customers);
        model.addAttribute("username", principal.getName());
        return "customers";
    }

    // add customers for demonstration
    public void addCustomers() {

        Customer customer1 = new Customer();
        customer1.setAddress("123");
        customer1.setName("pharmaceutical Industries");
        customer1.setServiceRendered("Important services");
        customerDAO.save(customer1);

        Customer customer2 = new Customer();
        customer2.setAddress("1234");
        customer2.setName("technologies Industries");
        customer2.setServiceRendered("Important services");
        customerDAO.save(customer2);


    }
}


Run Spring Boot application with command: mvn spring-boot:run. by console or IntelliJ etc.



Open a browser  http://localhost:8081 or http://127.0.0.1:8081 result this.










Set usernameuser1 and passworduser1 ,keycloak suggest to you to change the password,In this example I set the same password.

















































https://www.keycloak.org/getting-started/getting-started-docker






```

![[AVvXsEhNYb8CunHRS-yKdCVQadeIGCpLBOlDFqazATxEMCXE04RfP2AL91RIuuJ6WEDUYh4of3eyTMnQka_v5YyO0a7dRWIAJRu6CK3EXOauWXJK8fK6iIlY7uhBgxs3vySXFctVRuYRoUA0uzDneG5X.bin]]

![[AVvXsEgXTK467XC8zfZxVP9X7y88qCPb65KphrvJKSpjiBRhOYKgZfTIgsJecmZa5tp_aX7EJ4aMNujXrdoCyfLRrqhCJYArqCFhCIqjB8dGbX8UkrwdE3OqADdfsIRhTheUhIw0e1B6HKJtlw6StcMW.bin]]

![[AVvXsEjO8VRwdE9l39xuRqIjhNdV6D0NiEo-sELsFIxtKNWAIDEw02tOxdUWfvv9PhAjxRKNOVPqVI0grU3V9MDpAvpJc1QDBvZXjs8hjSpY4n-JY-gpI5-w_BSNTbZOzf4F57Vsr03K6USx4Gp4tyLF.bin]]

![[AVvXsEiWZ4NXub2pisc0auk9IzyLv3g5q57GZaJtSKuh3NtQSSWYE-41wdjInMgRwYWUdZHwwfEdkeE1uqxi0S3qQCSvRc_XK7Irrok_nPQ6BWxiJNnEVJGI2PX_oY02hg8EKEaEbvy5uxw8Op7nBJQ8.bin]]

![[AVvXsEgtqyg2eI0aq0SYvywbScswDalnlutfIPbkSNAEAoYaBuDd19QQC0JdFgEvi6WC_e2kT65wEgV_4qyJhfzKj03GnmoR0P3jfOYorACXRYsCiBkwHc6lnCbGUPjIHj3rIrmxgr5IdJARcRU_SJ84.bin]]