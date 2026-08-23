---

---
[https://jstherightway.org/](https://jstherightway.org/)

[Referência oficial](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript)

[https://eloquentjavascript.net/](https://eloquentjavascript.net/)

# Variáveis

## Falseáveis e Trully

- Considerados como falso:
	- “ “
	- 0

## Hoisting

- Permite que as variáveis sejam declaradas em qualquer parte do corpo, mesmo após a função que a invoca

```javascript
//Criando e executando uma função instantaneamente

(function(){
	console.log("Teste")
})()

```

## Função como parâmetro

Sempre que referencia-se a uma função usando parênteses (), o que está sendo passado é o retorno da função. Exemplo:

```javascript
document.addEventListener("load", funcao()); // na prática o parâmetro passado será o retorno da função funcao()

document.addEventListener("load", funcao); // Aqui o que está sendo fornecido como parâmetro é a própria função.
```

# Trabalhando com módulos

Existem duas sintaxes possíveis:

```javascript
// Formato commonJS (Criado pelo NodeJS)
const fs = require('fs')

// Formato ecma script
	import {writeFile} from 'node:fs/promises' // importando somente um método dentro do módulo
	import fs from 'node:fs/promises' // importando apenas o método default
	import * from 'node:fs/promises' // importando tudo
```

Por padrão, todos os métodos e atributos dentro de um arquivo são privados. É necessário exportar aquilo que se deseja tornar disponível para importação em outros arquivos

```javascript
// Formato commonJS (Criado pelo NodeJS)
module.exports = {
	método1,
	método2,
	atributo1
}

// Formato ecma script
	export default metodoDefault // neste caso, se não especificado na importação, este será o método padrão a ser importado
```

# React

- Criando APP: `npx create-react-app <nome>`
- Instalando o ES-Lint: `npm install -g eslint`
	- Necessário instalar também a extensão no VS-Code
- Instalar a extensão react developer tools no navegador

> [!tip] 💡
> Convenção: Componentes do react costumam ser nomeados com a primeira letra do nome do arquivo em maiúsculo
JSX é case sensitive (diferente do JS em html)

## Trabalhando com props

```javascript
// Componente
export default function Ola(props) {
    // JSX
    let nome = props.nome
    return (
        <div>
            <h1>Olá {nome}</h1>
        </div>
    )
}

// Chamando o componente
<React.StrictMode>
    <Ola nome = 'Eduardo'/>
    <Ola nome = 'José' />
    <Ola nome = 'João' />
    <Ola nome = 'Maria' />
</React.StrictMode>
```

```javascript
// Renderizando uma lista
import './lista.css'

let cidades = ['Curitiba', 'Pinhais', 'Araucária']

export default function Lista(){
    
    let itens = cidades.map(cidade => {
        return (<li>{cidade}</li>)
    })
    
    return (
        <>
            <h1>Lista de Cidades</h1>
            <input type='text' />
            <div>
                <ul className='lista'>
                    { itens }
                </ul>
            </div>
        </>
    )
}
```

```javascript
//Lista com pesquisa dinâmica
let cidades = ['Curitiba', 'Pinhais', 'Araucária']

export default function Lista(){
    
    const [nomeCidade, setNomeCidade] = useState("")

    let itens = cidades.filter((cidade, idx) => {
        let exp = new RegExp(nomeCidade, "i")

        return cidade.search(exp) > -1
    }).map((item, idx) => {
        return <li key={idx}>{item}</li>
    })

    function filtra(event) {
        setNomeCidade(event.target.value)
    }

    return (
        <>
            <h1>Lista de Cidades</h1>
            <input type='text' onChange={filtra} />
            <div>
                <ul className='lista'>
                    { itens }
                </ul>
            </div>
        </>
    )
}
```