---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2024-08-26T17:59:00
Owner:
  - Eduardo Quinalha
---
# Servlet

```java
@WebServlet("/OlaMundo")
public class OlaMundo extends HttpServlet {
	private static final long serialVersionUID = 1L;

	protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
		response.getWriter().append("Olá Mundo!");
	}
}
```

Uma servlet é um **Singleton**: Apenas uma instância é carregada na memória

> [!note] 🔥
> Existem alguns métodos na classe HttpServlet que podem ser sobrescritos para implementar lógicas associadas ao ciclo de vida da servlet:
init()
service()
destroy()

## Projeto Web

<!-- Column 1 -->
src/main/java → Servlets, classes (conteúdo dinâmico)
src/main/webapp → JSP, conteúdo estático
src/main/webapp/WEB-INF → Não são acessíveis através do navegador. Também é nesta pasta que fica o web.xml

Arquivos .jsp dentro da pasta WEB-INF não são acessíveis via navegador, mas podem ser “renderizados” via encaminhamento interno feito por uma servlet.

<!-- Column 2 -->
> [!note] 🔥
> URL:

localhost:8080/<Nome_do_Projeto>/<Conteúdo_estático_e_JSP>

### Pasta WEB-INF

Ao empacotar o projeto em um .war, sua composição será a seguinte:


```java
// projeto.war
- index.html
- arquivo.jsp
- <outros conteúdos estáticos>
- WEB-INF
	- classes: (bytecode do seu projeto)
		- ola.class
		- teste.class
	- lib: (bibliotecas utilizadas pelo seu projeto)
		- log4j.jar
```

## Filter

Uma classe especial que implementa a interface **Filter**
Todas as requisições passarão por ele, mas apenas as URLs especificadas serão interceptadas

> [!note] 🔥
> **PEGADINHA!**
Os parâmetros request e response **NÃO SÃO HttpServletRequest/HttpServletResponse,** mas sim **ServletRequest e ServletResponse**

```java
@WebFilter("/*") // URL's interceptadas
public class SegurancaFilter implements Filter {

	@Override
	public void doFilter(ServletRequest request, ServletResponse response, FilterChain chain)
			throws IOException, ServletException {

//		System.out.println("antes da servlet");
		chain.doFilter(request, response);
//		System.out.println("depois da servlet");
	}
}
```

## Listeners

Classes especiais com métodos que serão invocados sempre que algum evento em específico ocorrer, por exemplo: Inicialização do container, finalização do container, etc…

```java
@WebListener
public class Bootstrap implements ServletContextListener {

	@Override
	public void contextInitialized(ServletContextEvent sce) {
		ServletContextListener.super.contextInitialized(sce);
		System.out.println("============= app iniciou====");
	}

	@Override
	public void contextDestroyed(ServletContextEvent sce) {
		ServletContextListener.super.contextDestroyed(sce);
		System.out.println("============= app finalizou====");
	}
}
```

## Escopos

**Requisição: **como http é stateless, os dados são perdidos a cada requisição

**Sessão: **o JSessionId aponta para o espaço de memória onde encontram-se os objetos do usuário.

**Application:** Todos os usuários têm acesso

> [!note] 🔥
> **Ordem de procura:
Expression language → **Página, requisição, sessão, aplicação

## Ciclo de vida

Init()

Service()

Destroy()
