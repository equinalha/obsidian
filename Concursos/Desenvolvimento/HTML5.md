---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2024-10-01T17:16:00
Owner:
  - Eduardo Quinalha
---
# HTML 5

## Semântica

<!-- Column 1 -->
![[Untitled 430.png]]

**Elementos semânticos do HTML5:**

<!-- Failed to import synced block: Could not find block with ID: 438d3469-f9d6-4b5b-8942-f3d85e2be18d. Make sure the relevant pages and databases are shared with your integration "Obsidian". -->

<!-- Column 2 -->
Novas tags introduzidas a partir do HTML 5 com o objetivo de facilitar a acessibilidade

Além destas, também são muito cobradas em concurso as tags <audio> e <video> com seus atributos

**Section: **Agrupamento temático de conteúdo, tipicamente com um cabeçalho

**Article: **Conteúdo independente, auto-contido. Posts, comentários, cards de produtos, artigo de notícia

**figure:** Uma espécie de container que envolve elementos ilustrativos. Não substitui o img. Mas pode conter também <figcaption>

```html
<figure>
  <img src="pic_trulli.jpg" alt="Trulli">
  <figcaption>Fig1. - Trulli, Puglia, Italy.</figcaption>
</figure>
```


> [!note] 🔥
> A partir do HTML 5, a declaração DocType passou a ser apenas:

`**<!DOCTYPE html>**`

## HTML5 - Elementos Semânticos

![[Untitled 431.png]]

## Mapas para Imagens

```html
<img src="workplace.jpg" alt="Workplace" usemap="#workmap">
<map name="workmap">
 <area shape="rect" coords="34,44,270,350" alt="Computer" href="computer.htm">
 <area shape="rect" coords="290,172,333,250" alt="Phone" href="phone.htm">
 <area shape="circle" coords="337,300,44" alt="Coffee" href="coffee.htm">
</map>
```

## Atributos Globais

São atributos padrões que existem para todas as tags do html.

- Accesskey: Define uma tecla de atalho para o recurso
- contenteditable
- dir: direção (horizontal, vertical)
- spellcheck
- style
- tabindex
- title
- translate

## datalist

Tag utilizada para definir opções de autopreenchimento para um campo do tipo input. O link entre o input e o datalist é feito pelo atributo id

```html
<form action="/action_page.php" method="get">
  <label for="browser">Choose your browser from the list:</label>
  <input list="browsers" name="browser" id="browser">
  <datalist id="browsers">
    <option value="Edge">
    <option value="Firefox">
    <option value="Chrome">
    <option value="Opera">
    <option value="Safari">
  </datalist>
  <input type="submit">
</form>
```

## Armazenamento de dados

<!-- Column 1 -->
![[Untitled 432.png]]

<!-- Column 2 -->
A partir do HTML 5 foi disponibilizado o recurso de API do armazenamento local

- Local Storage → Persiste
- Session Storage → Volátil

> [!note] 🔥
> O armazenamento é segmentado por origem/protocolo. Todas as páginas de uma mesma origem compartilham o mesmo armazenamento (independente de aba)

## Utilizando o Cache local

As políticas de cache são definidas dentro de um arquivo especial, o cache manifest, disponibilizado na página inicial da aplicação

> [!note] 🔥
> **Nome do arquivo: **cache.appcache
A primeira linha deve ser CACHE MANIFEST

Exemplo

<!-- Column 1 -->
```markdown
CACHE MANIFEST
index.html
jquery-3.4.1.min.js
pure-min.css
ico.png
counter.jpeg
counter2.jpeg
```


<!-- Column 2 -->
O Cache Manifest é composto por 4 seções

- CACHE:
	- Arquivos que serão cacheados
- NETWORK:
- FALLBACK:
	- Caso a conexão esteja indisponível
- SETTINGS:
	- Prefer-online → Sempre busca no servidor primeiro
	- fast

<!-- Column 3 -->
Para utilizar o cache, no arquivo HTML deve-se fazer a importação do mesmo:

```html
<!DOCTYPE html>
<html manifest="cache.appcache">
```


## Tags principais (cobradas em concurso)

Obs: Em negrito estão as novas tags do HTML 5

- <wbr> → Word Break Opportunnity - Separação de sílabas para quebra de linha
- Listas
	- <ol>
	- <ul>
- **<header>**
- **<nav>**
- **<aside>**
- **<article>**
- **<section>**
- **<footer>**
- <canvas>
	- Permite desenhar gráficos utilizando javascript

# SVG

- Define graficos 2D em XML
- Baseado em XML
- Se os atributos são definidos, o browser renderiza automaticamente

# WSDL

- Linguagem baseada em XML para descrever webservices
