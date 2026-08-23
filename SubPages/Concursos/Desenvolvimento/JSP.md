---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2024-08-26T17:59:00
Owner:
  - Eduardo Quinalha
---
## JSP

A parte dinâmica do JSP é código JAVA
Pode ser inserido no meio do html
Um JSP, quando executado, transforma-se em uma servlet. (é compilada)
**Diretivas: **informações globais, normalmente no início do código. Servem para, por exemplo, importação de bibliotecas como JSTL

```java
// Esta notação é chamada scriptlet
<%

%>

// Esta é uma diretiva
<%@page (...) %>

// Expression Language
// No JSP, existem atalhos para chamar os getters
${aluno.nome} // Equivale a aluno.getNome()
```

O JSP funciona como uma camada acima do servlet. Por baixo dos panos ele é convertido para .java, posteriormente compilado em .class, instanciado em objeto e inicializado como servlet.

![[Untitled 558.png]]

```java
<%@ page language="java" contentType="text/html; charset=UTF-8"
    pageEncoding="UTF-8"%>
<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<title>Minha aula de JSP</title>
</head>
<body>
	<h1>Olá Mundo</h1>
	<%
		System.out.println("Teste"); // Console
		response.getWriter().println("Teste 2"); //Browser
		out.println("Teste 3"); // Browser
	%>
	<%="Teste 4" %> <!-- Browser -->
</body>
</html>
```

> [!note] 🔥
> Dentro do JSP ou até mesmo de uma servlet, existem duas formas de se obter dados vindos das requisições:

**request.getAttribute**(”nome”); // Para se obter um atributo que foi anexado à requisição. É um objeto
r**equest.getParameter(**”nome”); // Dado enviado por um formulário, por exemplo. É string

```java
// Scriplet para impressão de valores no navegador
<%= nomeDaVariável %>

// Equivale a
<% out.print(nomeDaVariável) %>
```

> [!note] 🔥
> O JSP possui alguns objetos auto-instanciados, disponíveis para uso:

| **out** | jspWritter |
| --- | --- |
| **request** | HttpServletRequest |
| **response** | HttpServletRespone |
| **config** | ServletConfig |
| **session** | HttpSession |
| **pageContext** | PageContext |
| **page** | Object |
| **exception** | Throwable |

### Elementos do JSP

| Declarações | <%! … %> | Declaração de compenentes ou variáveis utilizadas pela página |
| --- | --- | --- |
| Expressões | <%= … %> | São convertidas em uma String. Não tem ; no final |
| Scriptlets | <% … %> | Lógica em Java |
| Comentários | <%— … —%> |   |
| Ações | <jsp:Ação /> | Comportamento e regras de negócio. |
| Diretivas | <%@ … %> | Parâmetros passados ao compilador que irá gerar a Servlet correspondente |

- **Diretivas:** <%@ diretiva atributo1=”valor” atributo2 = “valor” atributoN = “valor” %>
	- Instruções importantes para o processamento do JSP. Controle do JSP
	- page: Importação de classes, content-type, etc.
	- include: Inclusão de arquivos no servlet
	- taglib: uso de tags JSP
	- buffer: Se configurado como “none”, a resposta é enviada imediatamente para o cliente. Quando configurado um valor, a resposta é bufferizada no servidor antes de ser enviada para o cliente final
- **Declarações: **<%! Atributos, métodos, classes internas%>
	- São transcritas diretamente para o corpo da servlet (fora de qualquer método)
- **Expressões: <%= ... %>**
	- Código java que tem um valor de retorno
	- Toda expressão será escrita no html resultante
	- equivale ao argumento de um out.write() no corpo da servlet correspondente
- **Scriptlets: <% … %>**
	- Código java executado sempre que a página for processada
	- É transcrito literalmente para o corpo da servlet dentro do método _jspService()
- **Comentários: <%— texto —%>**
- **Ações: <jsp:useBean …/>**
- **Texto livre**

## Ciclo de vida

![[Untitled 559.png]]

- Compilação
	- Ocorre na primeira vez que o JSP é chamado ou após ter sido modificado
	- Transforma o JSP em um .java e posteriormente em um .class
- Inicialização → jspInit()
	- Ocorre apenas uma vez
	- Inicializa conexões com banco de dados e abertura de arquivos
- Execução → _jspService()
	- Este método não pode ser sobrescrito
	- é ele que lida com os objetos HttpServletRequest e HttpServletResponse
```javascript
void _jspService(HttpServletRequest request, HttpServletResponse response) {
   // Service handling code...
}
```
	- Atende a todos os verbos HTTP (GET, POST, DELETE, …)
- Cleanup → jspDestroy()
	- Pode ser sobrescrito
	- Especialmente para encerrar conexões com banco de dados
