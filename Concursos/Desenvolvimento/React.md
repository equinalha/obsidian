---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2025-04-29T14:39:00
Owner:
  - Eduardo Quinalha
---
[[React Interview Questions.pdf]]

# Características

- Biblioteca JavaScript criada pelo Facebook, utilizada para criar interfaces com o usuário
- Depende do NodeJS e npm
- Declarativa
	- O React é considerado uma biblioteca declarativa porque permite que os desenvolvedores descrevam *como* a UI deve parecer para diferentes estados da aplicação, sem se preocupar com as mudanças de estado propriamente ditas. 
	- O React se encarrega de atualizar a UI para corresponder ao estado atual da aplicação.
- Virtual DOM
	- O React mantém uma representação leve do DOM, conhecida como Virtual DOM. 
	- Quando o estado de um componente muda, o React faz uma comparação eficiente entre o Virtual DOM e o DOM real, e **apenas aplica as mudanças mínimas necessárias**, o que resulta em um melhor desempenho.
- Criação de aplicativos móveis
	- Com o advento do React Native, uma extensão do React, é possível criar aplicativos móveis para iOS e Android usando a mesma metodologia baseada em componentes do React. 
	- Isto permite reutilizar a lógica de estado e renderização entre plataformas web e móveis.

# JSX

- JavaScript XML
- Utilizado para descrever UI em javascript
- Retorna um código em HTML
- Não é de uso obrigatório no React. É possível criar elementos sem o uso de JSX utilizando `React.createElement`
- Expressões em JSX
	- É possível utilizar javascript dentro de JSX
```javascript
const myElement = <h1>React is {5 + 5} times better with JSX</h1>;
```
- Atributo `class`
	- Uma vez que trata-se de uma palavra reservada pelo JavaScript, no JSX utiliza-se `className`
- if
	- JSX não suporta `if`
	- Ao invés de escrever um controle condicional dentro do JSX, recomenda-se utilizar fora deste
	- Ou utilizar o operador ternário

# Componentes

## Class Components

- Deve ser definido como uma classe que estende `React.component`
- O Nome da classe deve iniciar com letra maiúscula
- Deve conter um método `render()` que retorna um HTML

```javascript
class Car extends React.Component {
  render() {
    return <h2>Hi, I am a Car!</h2>;
  }
}

// Renderizando
const root = ReactDOM.createRoot(document.getElementById('root'));
root.render(<Car />);
```

- Pode conter um `constructor()`
- As propriedades do componente, devem ser armazenadas em um objeto chamado `state`

```javascript
class Car extends React.Component {
  constructor() {
    super();
    this.state = {color: "red"};
  }
	 render() {
    return <h2>I am a {this.state.color} Car!</h2>;
  }
}
```

- Parâmetros fornecidos ao componente são armazenados em um objeto chamado `props`

```javascript
class Car extends React.Component {
  constructor(props) {
    super(props);
  }
  render() {
    return <h2>I am a {this.props.color} Car!</h2>;
  }
}

const root = ReactDOM.createRoot(document.getElementById('root'));
root.render(<Car color="red"/>);
```

## Function Components

## Ciclo de Vida dos Componentes

### **Mounting**

- Os elementos são inseridos no DOM
- Quatros métodos built-in estão disponíveis para interagir com o evento mounting:
	1. `constructor()`
		1. Primeiro método a ser chamado
		2. Ponto ideal para definição das variáveis do `state` de forma independente
	2. `getDerivedStateFromProps()`
		3. Chamado imediatamente antes de renderizar elementos no DOM
		4. Aqui é o ponto correto para definição das variáveis do `state `quando estas dependerem dos valores do `props`
```javascript
class Header extends React.Component {
  constructor(props) {
    super(props);
    this.state = {favoritecolor: "red"};
  }
  static getDerivedStateFromProps(props, state) {
    return {favoritecolor: props.favcol };
  }
  render() {
    return (
      <h1>My Favorite Color is {this.state.favoritecolor}</h1>
    );
  }
}

const root = ReactDOM.createRoot(document.getElementById('root'));
root.render(<Header favcol="yellow"/>);
```
	3. `render()`
	4. `componentDidMount()`
		5. Chamado depois da renderização do componente
		6. Aqui é o local correto para execução de código que dependa de o componente já estar no DOM
- `render()` é o único de uso obrigatório

### Updating

- Disparado sempre que houver alteração no `state `ou `props `do componente
- Está associado a 5 métodos:
	1. `getDerivedStateFromProps()`
	2. `shouldComponentUpdate()`
		1. Retorna um booleano que indica ao React se deverá continuar com a atualização do componente ou não
	3. `render()`
	4. `getSnapshotBeforeUpdate()`
		2. Disponibiliza os valores de `state `e `props `antes da atualização para elaboração de lógica associada a isso
		3. Se este método estiver presente, é obrigatório também o uso do `componentDidUpdate()`
	5. `componentDidUpdate()`

### Unmounting

- Disparado quando um componente é removido do DOM
- Possui apenas um método associado:
	- `componentWillUnmount()`
		- Chamado imediatamente antes da remoção do componente

# Renderização

- `createRoot()`
	- Recebe um argumento
	- Corresponde ao elemento HTML onde o componente React vai ser renderizado
- `render()`
	- Define o componente React que será renderizado
```javascript
// JSX
const myelement = (
  <table>
    <tr>
      <th>Name</th>
    </tr>
    <tr>
      <td>John</td>
    </tr>
    <tr>
      <td>Elsa</td>
    </tr>
  </table>
);

// Renderização
const container = document.getElementById('root');
const root = ReactDOM.createRoot(container);
root.render(<p>Hello</p>);
```

## Root

- É o elemento HTML onde o conteúdo react será renderizado
- É um container
- **Não é obrigatório** que seja um` <div>` e também **não é obrigatório** que tenha o atributo` id=’root’`

# Eventos

- Os eventos do React se distinguem dos naturais do HTML pelo uso de camel case
- Exemplos
	- React: `onCLick `/ HTML: `onclick`
- As funções disparadas em reação a um evento podem levar 0, 1 ou 2 argumentos

```javascript
return (
    <button onClick={(event) => shoot("Goal!", event)}>Take the shot!</button>
  );
  
// O primeiro argumento é livre
// O segundo é o próprio evento em si
```

# Hooks

- Permitem que function components tenham acesso a estado e outras features do React
- Regras
	- Só podem ser invocadas de dentro de function components, no topo deste
	- Não podem ser condicionais
	- Não funcionam em class components

## useState

- Este Hook é utilizado para **declarar variáveis de estado** em componentes **funcionais **do React.
- Lida com o estado da aplicação
- Ao ser invocada, aceita como parâmetro o estado default da variável e retorna dois valores:
	- O estado corrente
```javascript
import { useState } from "react";

function FavoriteColor() {
  const [color, setColor] = useState("");
}
```
	- A função responsável por atualizar o estado

## useEffect

- Este Hook é utilizado para realizar efeitos colaterais em componentes funcionais, como: 
	- chamadas a APIs, 
	- assinaturas de eventos, 
	- ou manipulações de DOM.
- Aceita dois argumentos: `useEffect(<function>, <dependency>)`
- Como regra, o `UseEffect` irá rodar toda vez que o componente renderizar
- Para controlar quando ele rodará, utilizam-se as dependências

```javascript
useEffect(() => {
  //Runs on every render
});

useEffect(() => {
  //Runs only on the first render
}, []);

useEffect(() => {
  //Runs on the first render
  //And any time any dependency value changes
}, [prop, state]);
```

## useContext

- Este Hook é utilizado para acessar o contexto do React, permitindo que componentes consumam valores de contexto.
- **Permite o compartilhamento de estado entre componentes**
- Sem o uso do contexto, para repassar o estado de um componente para outro seria necessário o uso de `props`
- Se existem muitos componentes aninhados, cada componente na hierarquia teria de repassar o valor via `props`, mesmo que não estivesse utilizando-o

```javascript
// Primeiro é necessário importar o createContext e iniciá-lo
import { useState, createContext } from "react";
import { useState, createContext, useContext } from "react";
import ReactDOM from "react-dom/client";

const UserContext = createContext()

// Em seguida, os componentes que usarão do contexto compartilhado deverão estar envolvidos pelo componente UserContext.Provider
function Component1() {
  const [user, setUser] = useState("Jesse Hall");

  return (
    <UserContext.Provider value={user}>
      <h1>{`Hello ${user}!`}</h1>
      <Component2 user={user} />
    </UserContext.Provider>
  );
}

// Para ter acesso ao contexto compartilhado, o componente interno deverá utilizar o Hook useContext()
function Component5() {
  const user = useContext(UserContext);

  return (
    <>
      <h1>Component 5</h1>
      <h2>{`Hello ${user} again!`}</h2>
    </>
  );
}
```

## useRef

- Permite persistir dados entre renderizações
- Pode ser utilizado para armazenar uma variável mutável que não cause nova renderização quando atualizada
- `useState` pode causar um número de renderizações infinitas. `useRef` por sua vez, previne este problema

## useReducer

- Similar ao `useState`
- Permite o uso de lógica de estado customizada

## useMemo

- Embora também seja utilizado para memorização, o **useMemo** é usado para memorizar valores calculados
- Ele é adequado para otimizar cálculos pesados

## useCallback

-  retorna uma função *memorizada* que só é recriada quando uma das dependências muda. 
- Isso ajuda a evitar a recriação desnecessária de funções e, consequentemente, a melhorar a performance da aplicação.

