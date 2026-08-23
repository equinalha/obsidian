---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2024-10-25T09:54:00
Owner:
  - Eduardo Quinalha
---
## Formas de importação

```html
<style rel="stylesheet" type="text/css"> @import url("aleap.css"); </style>
<link rel="stylesheet" type="text/css" href="aleap.css"/>
<link rel="stylesheet" media="screen and (max-width: 600px)" href="a001.css">
```

### Principais seletores

- tags do html:
	- nome_da_tag - Seleciona elementos desta tag
	- tag.class - Elementos desta tag que pertençam a classe
	- tag1,tag2 - Seleciona as duas tags
	- tag1 tag2 - Seleciona todas as tag2 que esteja dentro de uma tag1
	- tag1>tag2 - Seleciona as tag2 cujo pai seja uma tag1
	- tag1+tag2 - Seleciona tag2 que venham logo após uma tag1
	- tag1~tag2 - Seleciona tag2 que venha imediatamente antes de uma tag1
	- ul > li:gt(1) - Seleciona todos os <LI> depois do segundo, de dentro de um <UL>
- **classes: .**
- **Id #**
- Atributos
	- [att] - Todas as tages que contenham o atributo att
	- [att=val] - Todas as tags que possuam o atributo att e cujo valor seja val
	- [att~=val] - Todas as tags que possuam o atributo att e que contenha val
	- [att^=val] - Todas as tags que possuam o atributo att iniciado por val
- MediaQuery
	- @media only screen and { condições }

### Unidades de medida

- vw e vh → 1% da largura/altura da janela do browser, respectivamente

### Hierarquia

<!-- Column 1 -->
1 - Arquivo CSS via tag <link>

2 - interno no próprio html via tag <style>, dentro da seção <head>

3 - inline (atributo style)

**Resolução de conflito:**

| **Seletor** | **Valor** |
| --- | --- |
| tag | 1 |
| .classe | 10 |
| #id | 100 |
| inline | 1000 |

Exemplo

| p | 1 |
| --- | --- |
| p.test | 1 + 10 = 11 |
| p#demo | 1 + 100 = 101 |
| p.test1.test2 | 1 + 10  + 10 = 21 |
| #navbar p#demo | 100 + 1 + 100 = 201 |

<!-- Column 2 -->


## Spacing / Box Model

Exemplo:

```css
/* A ordem é T R B L (sentido horário)*/
padding: 40px 30px 20px 10px
```

## Sass

- O SASS (Syntactically Awesome Style Sheets) é amplamente reconhecido por introduzir características avançadas no universo do CSS, tais como variáveis, mixins, funções e aninhamento de regras, que não estão disponíveis no CSS padrão. 
- Uma das **maiores vantagens do SASS** é, de fato, o uso de **variáveis**, que permitem a reutilização de valores de forma eficiente e ajudam a manter a consistência em todo o projeto. 
- A capacidade de definir uma cor, tamanho de fonte ou qualquer outro valor uma única vez e reutilizá-lo em vários lugares reduz a repetição desnecessária de código e facilita a manutenção.

## Nova API do HTML5

- Geolocation
- Drag n Drop
- Local Storage
- App Cache
- Web Workers
	- Scripts que rodam em background independente do resto da página
- SSE
	- Server sent events
	- O servidor pode atualizar elementos na página que já está no cliente

# Responsividade

## viewport

- Propriedade que se refere à largura do display do dispositivo

```html
<meta name="viewport" content="width=device-width, initial-scale=1.0">
```

```css
.container {
    width: 50vw; /* 50% da largura do viewport */
    height: 50vh; /* 50% da altura do viewport */
}
```

## Grid view

- Divide o viewport em colunas
- **tipicamente 12**
- Para definir as colunas, é necessário criar as classes

```css
.col-1 {width: 8.33%;}
.col-2 {width: 16.66%;}
.col-3 {width: 25%;}
.col-4 {width: 33.33%;}
.col-5 {width: 41.66%;}
.col-6 {width: 50%;}
.col-7 {width: 58.33%;}
.col-8 {width: 66.66%;}
.col-9 {width: 75%;}
.col-10 {width: 83.33%;}
.col-11 {width: 91.66%;}
.col-12 {width: 100%;}
```

- Todas as classes de colunas devem estar alinhadas à esquerda

```css
[class*="col-"] {
  float: left;
  padding: 15px;
  border: 1px solid red;
}
```

- Utilizando: 

```html
<div class="row">
  <div class="col-3">...</div> <!-- 25% -->
  <div class="col-9">...</div> <!-- 75% -->
</div>
```

## Media Query

- Permite responsividade

```css
/* Significa que a regra abaixo só se aplica a dispositivos cuja tela tenha no máximo 992 pixels */
@media screen and (max-width: 992px){
	body {
		background-color: blue;
	}
}

/* Significa que a regra abaixo só se aplica a dispositivos cuja tela tenha no máximo 600 pixels */
@media screen and (max-width: 600px){
	body {
		background-color: green;
	}
}

```

# Animações

- Mudança gradual de um estilo para outro
- Utiliza `transform()`
- Não há necessidade de javascript

```css
div {
  width: 100px;
  height: 100px;
  background-color: red;
  animation-name: example;
  animation-duration: 4s;
}

@keyframes example {
  from {background-color: red;}
  to {background-color: yellow;}
}

/* Também é possível utilizar porcentagem */
@keyframes example {
  0%   {background-color: red;}
  25%  {background-color: yellow;}
  50%  {background-color: blue;}
  100% {background-color: green;}
}

/* The element to apply the animation to */
div {
  width: 100px;
  height: 100px;
  background-color: red;
  animation-name: example;
  animation-duration: 4s;
}
```

## Transições

- Especifica o tempo que o elemento vai levar para alterar seu aspecto

```css
<style> 
div {
  width: 100px;
  height: 100px;
  background: red;
  transition: width 2s, height 4s;
}

div:hover {
  width: 300px;
  height: 300px;
}
</style>
```

# Pseudoelementos

- Pseudoelementos no CSS3 são palavras-chave que permitem definir estilos para partes específicas de um elemento, sem a necessidade de adicionar classes ou IDs adicionais no HTML. 
- Eles são usados para selecionar e estilizar elementos virtuais, ou partes de um elemento, que não são representados diretamente no DOM. 
- Os pseudoelementos não criam novos elementos no DOM; eles apenas permitem estilizar partes de elementos existentes.
- Os pseudoelementos mais comuns são:
1. `**::before**`: Insere conteúdo antes do conteúdo real de um elemento. Ele é frequentemente usado para adicionar ícones ou outros elementos decorativos
2. `**::after**`: Insere conteúdo após o conteúdo real de um elemento. Assim como `::before`, pode ser usado para adicionar elementos decorativos.
3. `**::first-line**`: Aplica estilos à primeira linha de um bloco de texto. Isso é útil para dar destaque ou formatar a introdução de um parágrafo.
4. `**::first-letter**`: Aplica estilos à primeira letra de um bloco de texto, permitindo efeitos visuais, como letras capitais ou decorativas.

```css
p::first-letter {
    font-size: 2em;
    float: left;
    margin-right: 0.1em;
}
```
