---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2024-10-01T17:17:00
Owner:
  - Eduardo Quinalha
---
# AJAX

> [!note] 🔥
> Ajax visa possibilitar o disparo de requisições assíncronas de forma a apresentar a página enquanto busca recursos diferentes de forma paralela
O Ajax é um conjunto de tecnologias embutidos dentro do javascript, mas a principal classe é a própria função **XMLHttpRequest**() do javascript

*”O Ajax é um conjunto de tecnologias que tem a finalidade de tornar o navegador mais interativo com o usuário, permitindo realizar uma solicitação ao servidor web sem que para isso seja necessário recarregar a página que está sendo acessada.”*

## XMLHttpRequest

```javascript
var xhr = new XMLHttpRequest();

xhr.onreadystatechange = () => {
    console.log("Estado atual " +xhr.readyState); // 5 estados do request, ver abaixo
}

xhr.onprogress = () => {
    console.log("carregando");
}

xhr.onload = () => {
    console.log("Resposta chegou ");
    console.log(xhr.responseText);
}
console.log(`Abrindo conexão com o servidor`);
// open(Método, URL, Assíncrono? (true/false) Opcional) 
// -> O true é o default. Ao mudar para false, muda para síncrono e bloqueia o resto da página até que seja recebido o retorno
xhr.open("GET", `https://my-json-server.typicode.com/raphaellacerda/estrategia/alunos`, true);
xhr.send(); // Se o método for POST, aqui pode-se enviar os parâmetros
console.log(`terminei de enviar a requisicão`);

// O corpo da resposta fica disponível nas seguintes propriedades:
xhr.responseText;
xhr.responseXML
```

| **Valor** | **Estado** | **Descrição** |
| --- | --- | --- |
| 0 | UNSENT | Requisição criada localmente, não enviada |
| 1 | OPENED | Enviada open() |
| 2 | HEADERS_RECEIVED | Chamou o send(), cabeçalhos e status já estão disponíveis |
| 3 | LOADING | Efetuando download (responseText tem dados parciais) |
| 4 | DONE | Completo |