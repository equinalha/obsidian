---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2024-08-26T18:04:00
Owner:
  - Eduardo Quinalha
---
# JQuery

Framework que uniformizava o JavaScript para diferentes browser

Ganho de compatibilidade

> [!note] 🔥
> São utilizados os mesmos seletores do CSS para a função $()

**Outras características**

- admite programação encadeada, ou seja, cada método retorna um objeto;
- utiliza seletores CSS para localizar elementos componentes da estrutura de marcação HTML da página;
- Possui arquitetura compatível com instalação de *plug-ins *e extensões em geral.
- é indiferente às inconsistências de renderização entre navegadores;

```javascript
$.get(`https://my-json-server.typicode.com/raphaellacerda/estrategia/alunos`, (data) => {
    data.forEach(aluno => {
        let $linha = $('<tr>');
        $linha.append($('<td>').html(aluno.id));
        $linha.append($('<td>').html(aluno.nome));
        $linha.append($('<td>').html(aluno.email));
        $linha.append($('<td>').html(aluno.dataNascimento));
        $('#listaAlunos tbody').append($linha);
    });
});
```

### Métodos

- $.load() → Carrega techos de html de forma assíncrona
- #.noConflict() → possibilita outros scripts a utilizarem o atalho $
- $.parseJSON() → Converte uma string JSON em objeto JS
- $.offset() → Quando aplicado a um conjunto de elementos, retorna todos à posição do primeiro