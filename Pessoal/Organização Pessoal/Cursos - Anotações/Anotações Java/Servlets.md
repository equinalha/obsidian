---

---
# Requisitos

- Instalar o eclipse para Java EE
- Baixar e descompactar o Apache Tomcat
- Configurar o Tomcat no Eclipse

```java
@WebServlet(urlPatterns = "/hello")
public class HelloWorldServlet extends HttpServlet{

	private static final long serialVersionUID = 1L;
	
	@Override
	protected void service(HttpServletRequest req, HttpServletResponse resp) throws IOException {

		PrintWriter out = resp.getWriter();
		out.println("<html>");
		out.println("<body>");
		out.println("Hello World!");
		out.println("</body>");
		out.println("</html>");
	}
}
```

> [!tip] 💡
> O método *service *atende os métodos **GET **e **POST **do **HTTP**. Para atender a um verbo específico, podemos usar os métodos específicos, conforme exemplo abaixo

```java
protected void doPost(HttpServletRequest request, HttpServletResponse response) {
	// Corpo do método
}
```

# Java Server Pages

```java
<%
	String nomeEmpresa = "Alura";
	System.out.println(nomeEmpresa);
%>

<html>
	<body>
		Empresa <% out.println(nomeEmpresa); %> cadastrada com sucesso!
	</body>
</html>
```

Pode-se substituir o trecho de saída por:

```java
Empresa <%=nomeEmpresa %> cadastrada com sucesso!
```

# Como chamar o JSP dentro de um Servlet

```java
//chamar o JSP
		Banco banco = new Banco();
		List<Empresa> lista = banco.getEmpresas();
		request.setAttribute("empresas", lista);
		
		RequestDispatcher rd = request.getRequestDispatcher("/listaEmpresas.jsp");
		rd.forward(request, response);
```

```java
<%@ page language="java" contentType="text/html; charset=ISO-8859-1"
	pageEncoding="ISO-8859-1"%>
<%@ page import="java.util.List, br.com.alura.gerenciador.servlet.Empresa" %>
<!DOCTYPE html>
<html>
<head>
<meta charset="ISO-8859-1">
<title>Lista de empresas cadastradas</title>
</head>
<body>

	<ul>
		<%
		List<Empresa> lista = (List<Empresa>)request.getAttribute("empresas");
		for (Empresa empresa : lista) {
			%>
			<li>
				<%=empresa.getNome() %>
			</li>
			<%
		}
		%>
	</ul>

</body>
</html>
```

# Usando Expression Language (EL)

```html
<html>
	<body>
<!-- 		Busca diretamente o atributo passado pela requisicao -->
		Empresa ${ empresa } cadastrada com sucesso!
	</body>
</html>
```

# Usando JSTL

JSTL adiciona tags funcionais no html que são renderizadas no server side.

é necessário:

- Adicionar a lib ao projeto
- Importá-la no JSP
- Definir um prefixo para ser usando no JSP de forma que o renderizador entenda de onde vem a tag

Primeiro, adicionar o .jar do JSTL para a pasta WEB-INF/lib

```html
<%@ page language="java" contentType="text/html; charset=ISO-8859-1"
	pageEncoding="ISO-8859-1"%>
<%@ taglib uri="http://java.sun.com/jsp/jstl/core" prefix="c" %>
<!DOCTYPE html>
<html>
<head>
<meta charset="ISO-8859-1">
<title>Lista de empresas cadastradas</title>
</head>
<body>

	<ul>
		<c:forEach items="${empresas}" var="empresa">
<!-- 		equivalente a empresa.getNome() -->
			<li>${ empresa.nome }</li>
		</c:forEach>
	</ul>

</body>
</html>
```

# jstl Core

tag **c:url**

```html
<%@ page language="java" contentType="text/html; charset=UTF-8"
	pageEncoding="UTF-8"%>
<%@ taglib uri="http://java.sun.com/jsp/jstl/core" prefix="c" %>
<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<title>Cadastra nova Empresa</title>
</head>
<body>
<c:url value="/novaEmpresa" var="linkServletNovaEmpresa" />
	<form action="${linkServletNovaEmpresa}" method="post">

        Nome: <input type="text" name="nome" />

        <input type="submit" />
    </form>
</body>
</html>
```

tag c:if

```html
<%@ page language="java" contentType="text/html; charset=UTF-8"
    pageEncoding="UTF-8"%>

 <%@ taglib uri="http://java.sun.com/jsp/jstl/core" prefix="c" %>
<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<title>Confirmação</title>
</head>
<body>
	<c:if test="${ not empty nome }">
		Empresa ${ nome } criada com sucesso
	</c:if>
	
	<c:if test="${ empty nome }">
		Informe o nome da empresa!
	</c:if>
</body>
</html>
```

# jstl fmt

```java
	<li>${empresa.nome} - <fmt:formatDate value="${empresa.dataAbertura}" pattern="dd/MM/yyyy"/></li>
```

<!-- Column 1 -->
![[SubPages/Pessoal/images/Untitled 122.png|Funciona, mas caso o cliente atualize a página, múltiplas requisições idênticas serão geradas, podendo replicar as informações armazenadas no banco.]]

<!-- Column 2 -->
![[SubPages/Pessoal/images/Untitled 123.png|Correto! Não repete as requisições quando atualiza a página, porém, os objetos anexados na requisição original não existem mais.]]

# Servlet com MVC

<!-- Column 1 -->
![[SubPages/Pessoal/images/Untitled 124.png]]

<!-- Column 2 -->
Para adequar ao modelo MVC, as seguintes ações foram tomadas:

- Apenas um servlet (controlador), chamado entrada, que recebe as diferentes ações por meio do parâmetro “acao”;
- O controlador, chama a classe de ação correspondente, as quais são classes comum do java, que retornam uma string com o tipo e o caminho da próxima ação;
- O controlador, com base no retorno da classe de ação, redireciona para a view correspondente;
- Os JSP’s correspondentes às views, passam a ficar em uma subpasta dentro de WEB-INF, de forma que tornam-se inacessíveis diretamente pelo navegador.

```java
protected void service(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
		
		String paramAcao = request.getParameter("acao");
		String returnAction = null;
		
		switch(paramAcao) {
		case "listaEmpresas":
			returnAction = listaEmpresas.executa(request, response);
			break;
		case "criaNovaEmpresa":
			returnAction = criaNovaEmrpesa.executa(request, response);
			break;
		case "mostraEmpresa":
			returnAction = mostraEmpresa.executa(request, response);
			break;
		case "alteraEmpresa":
			returnAction = alteraEmpresa.executa(request, response);
			break;
		case "excluiEmpresa":
			returnAction = excluiEmpresa.executa(request, response);
				break;
		case "novaEmpresa":
			returnAction = "forward:formNovaEmpresa.jsp";
			break;
		}
			
		String action = returnAction.split(":")[0];
		String view = returnAction.split(":")[1];
		
		if(action.equals("forward")) {
			RequestDispatcher rd = request.getRequestDispatcher("WEB-INF/view/" + view);
			rd.forward(request, response);
		}
		else {
			response.sendRedirect(view);
		}
	}
```

```java
public static String executa(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {

		String nomeEmpresa = req.getParameter("nome");
		String paramDataAbertura = req.getParameter("data");
		
		Date dataAbertura = null;
		
		try {
			SimpleDateFormat sdf = new SimpleDateFormat("dd/MM/yyyy");
			dataAbertura = sdf.parse(paramDataAbertura);
		} catch (ParseException e) {
			throw new ServletException(e);
		}
		
		Empresa empresa = new Empresa();
		empresa.setNome(nomeEmpresa);
		empresa.setDataAbertura(dataAbertura);
		
		Banco banco = new Banco();
		banco.adiciona(empresa);	
		
		req.setAttribute("nome", nomeEmpresa);
		
		return "redirect:entrada?acao=listaEmpresas";
	}
```

# Generalizando o controlador

```java
@WebServlet("/entrada")
public class EntradaServlet extends HttpServlet {
	private static final long serialVersionUID = 1L;

	protected void service(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
		
		String paramAcao = request.getParameter("acao");
		String nomeClasse = "br.com.alura.gerenciador.acoes." + paramAcao;
		String returnAction = null;
		
		// Carrega a classe com o respectivo nome
		Class classe;
		Acao acao = null;
		try {
			classe = Class.forName(nomeClasse);
			acao = (Acao)classe.newInstance();
		} catch (ClassNotFoundException | IllegalAccessException | InstantiationException e) {
			// TODO Auto-generated catch block
			throw new ServletException(e);
		}
		
		returnAction = acao.executa(request, response);
			
		String action = returnAction.split(":")[0];
		String view = returnAction.split(":")[1];
		
		if(action.equals("forward")) {
			RequestDispatcher rd = request.getRequestDispatcher("WEB-INF/view/" + view);
			rd.forward(request, response);
		}
		else {
			response.sendRedirect(view);
		}
	}
}
```

Utilizando este controlador mais genérico, novas ações podem ser adicionadas apenas criando novas classes no pacote “acoes” e que implementam a interface acao:

```java
// Este padrão implementa o Design Pattern chamado Command
// Design Patterns: Elements of Reusable Object-Oriented Software
public interface Acao {

	public String executa(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException;
	
}
```

# Autenticação e Autorização

> [!tip] 💡
> O Tomcat cria automaticamente um objeto HttpSession e envia um cookie para o navegador com o valor JSESSIONID.
Pelo lado do java, podemos adicionar atributos ao objeto session sem precisar fazer nada, o que permite que informações sejam persistidas entre múltiplas requisições.

```java
String login = request.getParameter("login");
		String senha = request.getParameter("senha");
		
		Banco banco = new Banco();
		Usuario usuario = banco.validaUsuario(login, senha);
		
		if(usuario != null) {
			HttpSession sessao = request.getSession();
			// session persiste por múltiplas requisições
			sessao.setAttribute("usuarioLogado", usuario);
			return "redirect:entrada?acao=listaEmpresas";
		}
		
		return "forward:formLogin.jsp";
```

```html
<title>Emrpesas Cadastradas</title>
</head>
<body>
	<!-- O Expression language busca primeiramente em request.getParameters(). Se não encontrar, ele busca em session.getParameters -->
	Usuario Logado: ${usuarioLogado.login}
	<br>
	<br>
	<c:url value="/entrada?acao=novaEmpresa" var="novaEmpresa" />
	<c:if test="${ not empty nome }">
		Empresa ${ nome } criada com sucesso
		</c:if>

	<h2>Lista de Empresas:</h2>
	<ul>
(...)
```

```java
public class logout implements Acao {

	@Override
	public String executa(HttpServletRequest request, HttpServletResponse response)
			throws ServletException, IOException {
		
		HttpSession sessao = request.getSession();	
		// Apaga os atributos e apaga o cookie
		sessao.invalidate();
		
		return "redirect:entrada?acao=formLogin";
	}
}
```

# Filtros

> [!tip] 💡
> Os filtros são posicionados antes do controlador. Tem funções diversificadas, segurança, auditoria, etc..
Funcionam exatamente como um servlet. O filtro deve ser configurado com o mesmo urlPatterns do WebServlet para o qual vai funcionar. Ele é chamado antes do servlet, repassado o controle e retomado depois do final da execução.

```java
@WebFilter(urlPatterns = "/entrada")
public class MonitoramentoFilter implements Filter {

	@Override
	public void doFilter(ServletRequest req, ServletResponse res, FilterChain chain)
			throws IOException, ServletException {
		long antes = System.currentTimeMillis();
		
		// Executa a ação
		chain.doFilter(req, res);
		
		long depois = System.currentTimeMillis();
		System.out.println("Tempo decorrido - " + req.getParameter("acao") + ": " + (depois - antes) + " ms");
	}
}
```

> [!tip] 💡
> Podem existir múltiplos filtros para um único **urlPattern, **no entanto, usando apenas anotações, não é possível garantir a ordem de execução destes filtros.
Para especificar a ordem de execução dos filtros, é necessário utilizar o ***web.xml***

![[SubPages/Pessoal/images/Untitled 125.png]]

# WebServices

Para trabalhar com JSON e/ou XML, é necessário importar as respectivas bibliotecas

- JAR da biblioteca GSON: [gson-2.8.5.jar.zip](https://caelum-online-public.s3.amazonaws.com/1001-servlets-parte2/06/gson-2.8.5.jar.zip)
- JARs da biblioteca XStream: [xstream-1.4.10-jars.zip](https://caelum-online-public.s3.amazonaws.com/1001-servlets-parte2/06/xstream-1.4.10-jars.zip)

```java
@WebServlet("/empresas")
public class EmpresasService extends HttpServlet {
	private static final long serialVersionUID = 1L;

	protected void service(HttpServletRequest request, HttpServletResponse response)
			throws ServletException, IOException {

		List<Empresa> empresas = Banco.getEmpresas();
		Gson gson = new Gson();
		String json = gson.toJson(empresas);

		response.setContentType("application/json");
		response.getWriter().print(json);
	}
}
```

```java
@WebServlet("/empresas")
public class EmpresasService extends HttpServlet {
	private static final long serialVersionUID = 1L;

	protected void service(HttpServletRequest request, HttpServletResponse response)
			throws ServletException, IOException {

		List<Empresa> empresas = Banco.getEmpresas();
		
		XStream xstream = new XStream();
		xstream.alias("empresa", Empresa.class);
		String xml = xstream.toXML(empresas);

		response.setContentType("application/xml");
		response.getWriter().print(xml);
	}
}
```

```java
@WebServlet("/empresas")
public class EmpresasService extends HttpServlet {
	private static final long serialVersionUID = 1L;

	protected void service(HttpServletRequest request, HttpServletResponse response)
			throws ServletException, IOException {

		String tipo = request.getHeader("Accept");
		List<Empresa> empresas = Banco.getEmpresas();
		
		if(tipo.contains("xml")) {
			XStream xstream = new XStream();
			xstream.alias("empresa", Empresa.class);
			String xml = xstream.toXML(empresas);
			response.setContentType("application/xml");
			response.getWriter().print(xml);
		}
		else if(tipo.contains("json")) {
			Gson gson = new Gson();
			String json = gson.toJson(empresas);
			response.setContentType("application/json");
			response.getWriter().print(json);
		}
		else {
			response.setContentType("application/json");
			response.getWriter().print("{ \"message\": \"no-content\"}");
		}
	}
}
```

> [!tip] 💡
> Criando um webclient em java (para testes).
Importar as bibliotecas:
*- httpclient
- fluent-hc
- httpcore
- commons-logging*

```java
public class ClienteWebService {
	public static void main(String[] args) throws ClientProtocolException, IOException {
		String conteudo = Request.Post("http://localhost:8080/gerenciador/empresas")
				.addHeader("Accept", "application/json")
				.execute()
				.returnContent()
				.asString();

		System.out.println(conteudo);
	}
}
```
