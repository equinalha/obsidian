---

---
Ferramentas mais antigas:

- Apache Ant → Build e configs
- Apache Ivy → Dependências

Maven = Ant + Ivy + Testes + etc…

> [!tip] 💡
> Pode ser utilizado via linha de comando ou diretamente na integração com a IDE
As configurações ficam no arquivo pom.xml

Para iniciar um novo projeto Maven, pode-se utilizar a opção correspondente no Eclipse (inicialmente utilizar a opção create a simple project).

### Pastas:

- **src/main/java:** Classes do projeto;
- **src/main/resources:** Configurações, arquivos xml, arquivos .properties;
- **src/test/java: **Classes de teste do Junit;
- **src/test/resources: **Configurações das classes de teste

# Repositório local

> [!tip] 💡
> ~/.m2/repository

## Adicionando dependência e repositórios

```xml
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 https://maven.apache.org/xsd/maven-4.0.0.xsd">
	<modelVersion>4.0.0</modelVersion>
	<groupId>br.com.alura</groupId>
	<artifactId>loja</artifactId>
	<version>0.0.1-SNAPSHOT</version>

	<dependencies>
		<dependency>
			<groupId>junit</groupId>
			<artifactId>junit</artifactId>
			<version>4.12</version>
			<scope>test</scope>
		</dependency>

		<!-- https://mvnrepository.com/artifact/com.thoughtworks.xstream/xstream -->
		<dependency>
			<groupId>com.thoughtworks.xstream</groupId>
			<artifactId>xstream</artifactId>
			<version>1.4.19</version>
		</dependency>

	</dependencies>

	<repositories>
		<repository>
			<id>spring-repo</id>
			<url>http://repo.spring.io/release</url>
		</repository>
	</repositories>
	
</project>
```

# Configurações globais do Maven

> [!tip] 💡
> Algumas configurações como: proxy, repositório global (aplicado a todos os projetos), podem ser feitas no arquivo **$HOME/.m2/settings.xml**

# Criando uma aplicação web com Maven no Eclipse

1. Criar um novo projeto Maven Simples
2. Configurar a localização do workspace
3. No Archetype digitar: **maven-archetype-webapp**
4. Configurar o grupo e o nome do artefato
5. Adicionar as dependências no pom.xml

```xml
		<!-- https://mvnrepository.com/artifact/javax.servlet/servlet-api -->
		<dependency>
			<groupId>javax.servlet</groupId>
			<artifactId>javax.servlet-api</artifactId>
			<version>3.1.0</version>
			<scope>provided</scope>
		</dependency>
		<!-- https://mvnrepository.com/artifact/javax.servlet.jsp/javax.servlet.jsp-api -->
		<dependency>
			<groupId>javax.servlet.jsp</groupId>
			<artifactId>javax.servlet.jsp-api</artifactId>
			<version>2.3.3</version>
			<scope>provided</scope>
		</dependency>
```

6. Clicar com o botão direito no projeto → Maven → Update project (selecionar a opção Force Update)
