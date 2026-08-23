---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2024-08-26T17:59:00
Owner:
  - Eduardo Quinalha
---
# O que é

- Extensão da JSP
- Biblioteca de tags
- Funcionalidades
	- Controle de fluxo
	- Manipulação de XML
	- Internacionalização
	- Acesso a banco de dados
- Suportado pelo contêiner
- Áreas Funcionais
	- Core
	- XML
	- Banco de dados
	- Internacionalização
	- Funções
- Visam substituir os scriptlets

```java
<%@ taglib prefix="c" uri="http://java.sun.com/jsp/jstl/core" %>

<!DOCTYPE html>
<html>
<head>
    <title>Exemplo de Uso da JSTL</title>
</head>
<body>
    <h1>Exemplo de Uso da JSTL</h1>

    <c:set var="nome" value="João" />

    <c:if test="${not empty nome}">
        <p>O nome é: ${nome}</p>
    </c:if>

    <c:forEach var="i" begin="1" end="5">
        <p>Contador: ${i}</p>
    </c:forEach>
</body>
</html>
```

A JSTL fornece várias outras tags, como `**<c:choose>**`, `**<c:when>**`, `**<c:otherwise>**`, `**<c:out>**`, entre outras, que permitem a manipulação de estruturas condicionais, repetição e formatação de dados em páginas JSP.
