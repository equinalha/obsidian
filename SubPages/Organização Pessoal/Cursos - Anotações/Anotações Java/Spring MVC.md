---

---
O Spring MVC funciona como uma camada acima do Servlet, facilitando o desenvolvimento de aplicações web MVC com controllers

# Inicio

- Criar uma aplicação com o spring initializer: start.spring.io
	- Maven project
	- Adicionar as dependências:
		- Spring Web
		- Thimeleaf
		- DevTools
- Importar no Eclipse utilizando a opção Maven Project

## Abaixo do pacote principal, criar um package controller

```java
@Controller
public class HelloController {
	
	@GetMapping("/hello")
	public String hello(HttpServletRequest request) {
		request.setAttribute("nome", "World");
		return "hello";
	}
}
```

Para facilitar, pode-se substituir o HttpServletRequest por um objeto Model

```java
@Controller
public class HelloController {
	
	// Action
	@GetMapping("/hello")
	public String hello(Model model) {
		model.addAttribute("nome", "World");
		return "hello"; // O valor de retorno corresponde ao nome da view
	}
}
```

## Abaixo de src/main/resources adicionar a view como um arquivo .html

```java
<html>
	<head>
	<meta charset="UTF-8" />
	</head>
	<body>
		Hello! <span th:text="${nome}">  </span>
	</body>
</html>
```

A tag th:text será processada no backend e substituída pelo nome da variável especificada na expression language (EL)
