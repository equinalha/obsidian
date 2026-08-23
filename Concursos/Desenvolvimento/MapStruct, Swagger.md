---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2024-08-26T18:17:00
Owner:
  - Eduardo Quinalha
---
> [!note]+ # Mapas Mentais
> ![[MapStruct.png]]

# MapStruct

- Facilita o mapeamento de entidades para outras classes
- Exemplo: Model → DTO

## Utilização

```java
// Classe car.class
public class Car {
 
    private String make;
    private int numberOfSeats;
    private CarType type;
 
    //constructor, getters, setters etc.
}

// Classe carDTO.class
public class CarDto {
 
    private String make;
    private int seatCount;
    private String type;
 
    //constructor, getters, setters etc.
}

@Mapper
public interface CarMapper {
 
    CarMapper INSTANCE = Mappers.getMapper( CarMapper.class );
 
    @Mapping(source = "numberOfSeats", target = "seatCount")
    CarDto carToCarDto(Car car);
}
```

- Para possibilitar o mapeamento, deve-se implementar uma interface anotada com `@Mapper`
- Esta interface define como o mapeamento deve ser feito
- A anotação `@Mapping` se encarrega da conversão de nome dos atributos
- Para usar o mapper:

```java
		//given
    Car car = new Car( "Morris", 5, CarType.SEDAN );
 
    //when
    CarDto carDto = CarMapper.INSTANCE.carToCarDto( car );
```

## Características

- O mapeamento pode ser feito automaticamente desde que os nomes e tipos sejam compatíveis
- O mapeamento é feito em tempo de compilação

## Resumo

- Dependência:

```xml
<dependencies>
    <!-- Outras dependências do projeto -->
    <dependency>
        <groupId>org.mapstruct</groupId>
        <artifactId>mapstruct</artifactId>
        <version>1.4.2.Final</version>
    </dependency>
    <dependency>
        <groupId>org.mapstruct</groupId>
        <artifactId>mapstruct-processor</artifactId>
        <version>1.4.2.Final</version>
        <scope>provided</scope>
    </dependency>
</dependencies>
```

- Anotações
	- `@Mapper`
		- Anota a interface mapper que faz a conversão
	- `@Mapping`
		- Descreve o mapeamento de propriedades e deve ser anotado acima da declaração do método
		- O nome do método é livre
```java
@Mapping(target = "formattedPrice", expression = "java(formatPrice(product.getPrice()))")
ProductDTO productToProductDTO(Product product);
```
- Uso
	- Basta chamar o método definido na interface:
	- `ProductDTO productDTO = ProductMapper.INSTANCE.productToProductDTO(product);`

# Swagger

- É a principal implementação da especificação **OpenAPI**
- Formato para descrição de API’s
	- Formato JSON ou YAML
	- Descreve os endpoints disponíveis e as operações possíveis em cada um
	- Descreve as operações de input e output de dados
	- Métodos de autenticação
- Ferramentas podem gerar o código da API a partir da especifação em Swagger
- O programador fica responsável apenas por escrever a lógica dos métodos
- Também é possível gerar automaticamente o código que irá consumir a API
- Se integra a vários frameworks, o principal exemplo e o próprio Spring Boot
- Principais campos:
	- **Base URL (campo servers)**
		- Formado por Schema + host + port + path
		- `scheme://host:[port][/path]`
		- Pode-se declarar múltiplas base URL
	- **Server Templating**
		- Qualquer parte da URL / scheme pode ser substituído por uma variável entre chaves {}
			- `https://{customerId}.saas-app.com:{port}/v2`
			- `{protocol}://api.example.com`
```yaml
servers:
  - url: https://{region}.api.cognitive.microsoft.com
    variables:
      region:
        default: westus
        enum:
          - westus
          - eastus2
          - westcentralus
          - westeurope
          - southeastasia
```

## Ferramentas

- Swagger Editor
	- Ferramenta web que permite criar a especificação da API de forma interativa
- Swagger Codegen
	- Gera códigos tanto para cliente como servidor a partir da definição swagger
- Swagger UI
	- Visualização gráfica em web da API
	- parâmetros de solicitação podem ser inseridos e enviados diretamente na interface, e as respostas da API são exibidas de forma clara.
	- fornece recursos de teste, permitindo que os desenvolvedores enviem solicitações para a API e visualizem as respostas correspondentes
- Swagger Hub
	- Solução completa para colaboração que permite criar, documentar, testar e compartilhar API
	- Possui:
		- Swagger Editor
		- Swagger UI
		- Teste e Validação
		- Integração com o Github

## Swagger + Spring Boot

- Dependência:

```xml
<dependencies>
    <!-- Outras dependências do projeto -->
    <dependency>
        <groupId>io.springfox</groupId>
        <artifactId>springfox-boot-starter</artifactId>
        <version>3.0.0</version>
    </dependency>
</dependencies>
```

- Para que o swagger varra automaticamente todos os endpoints da API criadas no spring boot, é necessário criar uma classe de configuração

```java
@Configuration
@EnableSwagger2
public class SwaggerConfig {

    @Bean
    public Docket api() {
        return new Docket(DocumentationType.SWAGGER_2)
                .select()
                .apis(RequestHandlerSelectors.basePackage("com.example.api"))
                .paths(PathSelectors.any())
                .build()
                .apiInfo(apiInfo());
    }

    private ApiInfo apiInfo() {
        return new ApiInfoBuilder()
                .title("API Documentation")
                .description("Documentation for My API")
                .version("1.0")
                .build();
    }
}
```

- A docuemntação será gerada automaticamente e disponibilizada em uma URL específica: `**http://localhost:8080/swagger-ui/index.html**`.
- Outras anotações específicas poderão ser utilizadas:
	- `@Api`
		- Fornece informações gerais sobre uma classe ou grupo de endpoints
		- Atributos
			- value (ou tags): tags utilizadas para categorização do endpoint
			- description
			- produces/consumes: Ex: JSON, XML
			- protocols
			- authorizations
			- **hidden: **Oculta o endpoint na documentação
	- `@ApiOperation`
		- Informações detalhadas sobre o método da operação
	- `@ApiParam`
		- Informações detalhadas sobre um parâmetro de uma operação

```java
@RestController
@RequestMapping("/api")
@Api(tags = "Exemplo API")
public class ExemploController {

    @GetMapping("/hello")
    @ApiOperation(value = "Retorna uma saudação", notes = "Retorna uma saudação com base no nome fornecido")
    public String sayHello(
            @ApiParam(value = "Nome para saudação", required = true) @RequestParam String name) {
        return "Olá, " + name + "!";
    }
}
```
