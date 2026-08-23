---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2024-11-29T08:19:00
Owner:
  - Eduardo Quinalha
---
# Características

- Desenvolvido para ser adotado gradualmente
- Pode ser utilizado para construir componentes de UI em projetos existentes
- Framework baseado na renderização client-side de aplicativos web
- Pode ser inserido no HTML ou no JavaScript

## Pilares

- **Componentes**
	- Tudo no Vue.JS é um componente, que são trechos reutilizáveis de código que encapsulam HTML, CSS e JavaScript
	- Cada componente pode conter sua própria lógica, estilo e estrutura
- **Reatividade**
	- Sistema de reatividade que monitora alterações nos dados e automaticamente atualiza a interface do usuário quando esses dados mudam
	- Elimina a necessidade de manipular o DOM diretamente
- **Renderização declarativa**
	- Descreve como a interface deve parecer usando uma sintaxe semelhante ao HTML (templates) ou diretamente em JavaScript com a render function
	- Dispensa a manipulação direta do DOM, que passa a ser atualizado dinamicamente pelo Vue

# Criação de uma aplicação

- Exemplo

```javascript
import { createApp } from 'vue';
import myApp from './myApp.vue';

const app = createApp(myApp); // ou vue.createApp(myApp)

// Usa o roteador e a store
app.use(router);
app.use(store);

// Registra um componente globalmente
app.component('my-component', MyComponent);

// Registra uma diretiva globalmente
app.directive('my-directive', MyDirective);

// Fornece um valor que pode ser injetado
app.provide('globalValue', 12345);
```

- O parâmetro da função `createApp()` é o rootComponent - Componente raiz da aplicação

## v-bind

- diretiva destinada a vincular dados e valores na visualização
- `<img v-bind:src="url">`
	- Vinculação do atributo `src` com um valor chamado de `url` que pode ser uma variável dentro do Vue
- Também pode ser utilizado para CSS
- Pode ser abreviado por dois pontos `:`
	- `<img :src="url">`

## v-if

```javascript
<p v-if="produtoEmEstoque > 0">
	Disponível em estoque
</p>
<p v-else>
	Estoque esgotado
</p>
```

## v-show

- objetiva tornar um elemento visível ou tirá-lo de visão
- **v-if →só cria (renderiza) o elemento se atender à condição**
- **v-show → sempre cria o elemento, mas pode ocultá-lo**

## v-for

```javascript
<ul>
	<li v-for="item in items" :key="item.id">
		{{ item.text }}
	</li>
</ul>

<script>
	new Vue({
		el: '#app',
		data: {
			items: [
				{ id: 1, text: 'Item 1' },
				{ id: 2, text: 'Item 2' },
				{ id: 3, text: 'Item 3' }
			]
		}
	});
</script>
```

## V-on

- Responde a eventos
- Corresponde a `onClick`, `onMouseOver`, entre outros
- Também podemos usar uma abreviação para o `v-on`, escrita como um arroba `@`. No nosso exemplo acima, teríamos `@:input` como sintaxe abreviada

```javascript
<div id="app">
	<input v-on:input="inpCount++">
	<p>{{ Quantidade de teclas apertadas: ' + inpCount }}</p>
</div>

<script>
	const app = Vue.createApp({
		data() {
			return {
				inpCount: 0
			}
		}
	})
	app.mount('#app')
</script>
```

## v-model

- Utilizado para formulários
- Vue também trabalha com **two-way binding**

```javascript
<div id="app">
	<input type="text" v-model="inpText">
	<p> {{ inpText }} </p>
</div>

<script>
	const app = Vue.createApp({
		data() {
			return {
				inpText: 'Texto inicial'
			}
		}
	})
	app.mount('#app')
</script>
```

# Single-File Components (SFC)

- Permitem encapsular o código relacionado a um componente Vue em um único arquivo, geralmente com a extensão .vue.
- Este arquivo contém três seções principais:
	- `<template>` → Conteúdo HTML
	- `<script> `→ Código Vue
	- `<style>` → Estilos CSS

# Mixins

- são uma maneira de reutilizar funcionalidades em diferentes componentes
- permitem que você agrupe lógica e a distribua entre múltiplos componentes de uma maneira modular.
- ajuda a evitar duplicação de código e promove a manutenção do software.

```javascript
// Definindo um mixin
const myMixin = {
  data() {
    return {
      mixinData: 'Isso veio do mixin!'
    };
  },
  methods: {
    logMessage() {
      console.log('Log do mixin');
    }
  }
};

// Componente Vue que utiliza o mixin
const MyComponent = Vue.extend({
  mixins: [myMixin], // Aplicando o mixin
  data() {
    return {
      componentData: 'Isso veio do componente!'
    };
  },
  created() {
    this.logMessage(); // Acessando o método do mixin
  }
});
```

- Nesse exemplo, o componente `MyComponent` tem acesso tanto aos dados e métodos do seu próprio escopo (`componentData` e outros), quanto aos dados e métodos definidos no mixin (`mixinData` e `logMessage`).
- Mixins são muito úteis em cenários mais simples, mas em projetos grandes, soluções como o Composition API podem ser mais recomendadas para evitar problemas de organização e legibilidade.

# Filtros

- são utilizados para transformar a exibição de dados no template de forma declarativa
- são aplicados diretamente na camada de apresentação (ou seja, no template), permitindo a formatação de valores exibidos, sem alterar os dados subjacentes. 
- Igual aos filtros do Angular

```javascript
<div id="app">
  <p>{{ message | capitalize }}</p>
</div>
```

- Exemplo de uso e definição de um filtro
	- Local (dentro do próprio componente)
```javascript
const MyComponent = {
  template: `<div>{{ price | currency }}</div>`,
  data() {
    return {
      price: 1234.56
    };
  },
  filters: {
    currency(value) {
      return '$' + value.toFixed(2);
    }
  }
};
```
	- Global com `vue.filter`
```javascript
Vue.filter('capitalize', function(value) {
  if (!value) return '';
  value = value.toString();
  return value.charAt(0).toUpperCase() + value.slice(1);
});

new Vue({
  el: '#app',
  data: {
    message: 'hello world'
  }
});
```
- No **Vue 3**, os filtros foram removidos. 
- O time do Vue recomenda que transformações de exibição sejam feitas usando **métodos de componentes ou funções dentro do template**, ou que se use o **Composition API** para manipular dados diretamente. 
- Isso aconteceu porque os filtros, com o tempo, foram considerados uma forma menos clara de separar a lógica de apresentação e poderiam gerar complexidade desnecessária.
- Exemplo de uso no **Vue 3 **

```javascript
const app = {
  data() {
    return {
      message: 'hello world'
    };
  },
  methods: {
    capitalize(value) {
      if (!value) return '';
      value = value.toString();
      return value.charAt(0).toUpperCase() + value.slice(1);
    }
  }
};

// No template
<p>{{ capitalize(message) }}</p>
```

# Pipes

- Conceito utilizado tanto no Angular quanto no Vue
- permitem a transformação de dados diretamente no template

```javascript
{{ value | pipeName }}

// Com parâmetros:
<p>{{ birthday | date:'fullDate' }}</p> <!-- Exibe a data completa -->
```

- Basicamente a mesma coisa que filter

# Plugins

- forma de adicionar funcionalidades globais à aplicação,
- injeção de mixins ou filtros (no Vue 2)

# Slots

- permite criar componentes reutilizáveis e flexíveis, fornecendo uma forma de inserir conteúdo dinâmico dentro de componentes.
- Eles funcionam como "espaços reservados" (ou placeholders) que podem ser preenchidos com conteúdo fornecido por outros componentes ou instâncias, permitindo que o conteúdo inserido seja altamente customizável.
- Um slot é um mecanismo de template para passar conteúdo dinâmico de um componente pai para um componente filho.

## Tipos

- **Slot padrão** (ou básico)

```html
<!-- Componente Filho (MyComponent.vue) -->
<template>
  <div>
    <slot></slot> <!-- Conteúdo vai ser inserido aqui -->
  </div>
</template>

<!-- Componente Pai -->
<MyComponent>
  <p>Este é o conteúdo inserido no slot!</p>
</MyComponent>
```

- **Slots nomeados**

```html
<!-- Componente Filho (MyComponent.vue) -->
<template>
  <header>
    <slot name="header"></slot>
  </header>
  <main>
    <slot></slot> <!-- Slot padrão -->
  </main>
  <footer>
    <slot name="footer"></slot>
  </footer>
</template>

<!-- Componente Pai -->
<MyComponent>
  <template v-slot:header>
    <h1>Cabeçalho Personalizado</h1>
  </template>

  <p>Este é o conteúdo principal.</p>

  <template v-slot:footer>
    <p>Rodapé Personalizado</p>
  </template>
</MyComponent>
```

- **Slots com escopo** (slots com props)

```html
<!-- Componente Filho (MyComponent.vue) -->
<template>
  <div>
    <slot :info="data"></slot> <!-- Passando dados para o slot -->
  </div>
</template>

<script>
export default {
  data() {
    return {
      data: { message: 'Olá do componente filho!' }
    }
  }
}
</script>

<!-- Componente Pai -->
<MyComponent v-slot:default="slotProps">
  <p>{{ slotProps.info.message }}</p> <!-- Acessando dados passados pelo componente filho -->
</MyComponent>
```