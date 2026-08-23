---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2024-08-29T17:42:00
Owner:
  - Eduardo Quinalha
---
# Regras de formação

- Os dados devem ficar em pares `Chave: Valor`
- Dados separados por vírgula
- O objeto é delimitado por chaves `{ }` 
- Arrays são delimitados por colchetes `[ ]`
- Um par chave/valor consiste de um nome entre aspas, seguido de dois pontos `:` e um valor, também entre aspas:
`"firstName":"John”`
- **Não pode ter funções;**
- **Não pode ter comentários;**
- **Todo texto sempre tem aspas duplas;**
- **As propriedades sempre tem aspas duplas (somente String, as demais não precisa).**

> [!note] 🔥
> Nomes JSON requerem aspas, nomes de variáveis JavaScript não precisam!

# Tipos de dados

O JSON possui apenas quatro tipos básicos: 

- String** **`**"Uma String"**`
- Booleano `true`
- Nulo `null`
- Numérico (podendo ser inteiro ou real) `3.1415`

```json
{
    "texto" : "Brasil",
    "numero" : 23,
    "numeroReal" : 54.87,
    "booleano": true,
    "nulo": null
}
```

# Outros Formatos Derivados

Os formatos [geoJSON](http://geojson.org/) e [topoJSON](https://github.com/mbostock/topojson/wiki) são derivados do JSON para representação de coleções de características geográficas simples, junto com seus atributos não-espaciais. Dentre as características possíveis de serem armazenadas no padrão geoJSON/topoJSON estão "points", incluindo endereços e localidades; "line strings", incluindo ruas, rodovias e limites; "polygons", incluindo países, estados ou demarcações de terra; e coleções misturadas desses tipos. O diferencial do topoJSON em relação ao geoJSON é que ele armazena topologia geoespacial, gerando um arquivo final com tamanho frequentemente menor.

```json
{
  "type": "Feature",
  "geometry": {
    "type": "Point",
    "coordinates": [125.6, 10.1]
  },
  "properties": {
    "name": "Dinagat Islands"
  }
}
```

## JSON

JSON ≠ Objeto Java Script

**JSON é uma string**, uma notação textual que representa um objeto em Java Script
JSON não aceita comentários e nem funções/métodos

```json
{
	"nome": "Eduardo",
	"nota": 10,
	"nivel": 5
}
```

Para converter de JSON para um objeto é necessário invocar o método **JSON.parse()
**Para converter de objeto para um JSON, utiliza-se o método **JSON.stringify()**

```javascript
// Fazendo um for em um JSON parseado
let json = {'"nome": "Eduardo", "nota": 10'} // JSON
let aluno = JSON.stringify(json) // Objeto

for (chave in aluno) {
	console.log(chave)             // nome, nota
	console.log(aluno[chave])      // Eduardo, 10
}
```

**Valores permitidos**

- String
- Number
- Boolean
- Array dos mesmos valores acima

# Problema de domínios cruzados (CORS)

> [!note] 🔥
> O JSON permite resolver o problema de requisitar dados entre domínios diferentes através do JSONP.

[https://www.devmedia.com.br/forum/o-que-e-jsonp/579788](https://www.devmedia.com.br/forum/o-que-e-jsonp/579788)

- Problema de CORS ocorre quando um recurso de uma origem tenta acessar recursos de outra
- Os navegadores modernos aplicam a política de "mesma origem" (**same-origin policy**), que restringe como os recursos de uma página da web podem ser requisitados de outro domínio.
- Isso evita que um site malicioso acesse dados de outro site sem permissão.
- Por exemplo, se o site `http://example.com` tentar fazer uma requisição AJAX para o site `http://anotherdomain.com`, essa requisição será bloqueada pelo navegador, a menos que o servidor de `anotherdomain.com` permita explicitamente a requisição de origens diferentes (cross-origin).
- Quando uma aplicação web tenta requisitar dados em JSON de um servidor em um domínio diferente, a política de CORS entra em ação.
	- Quando uma aplicação web faz uma requisição AJAX que recebe dados em JSON de um domínio diferente, o servidor que hospeda esses dados deve configurar cabeçalhos CORS (por exemplo, `Access-Control-Allow-Origin`) para permitir que o navegador aceite essa resposta.
- Antes do suporte a CORS ser amplamente implementado, uma técnica chamada JSONP era usada para contornar o problema de domínios cruzados. 
- JSONP envolve o uso de uma função de callback, onde o servidor retorna os dados em JSON dentro de uma função JavaScript que é injetada na página como um script. 
- Como a tag `<script>` não está sujeita à política de mesma origem, isso permitia o carregamento de dados de domínios cruzados, embora com limitações de segurança.