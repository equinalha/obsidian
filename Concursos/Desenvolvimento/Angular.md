---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2024-11-29T18:16:00
Owner:
  - Eduardo Quinalha
---
# Angular via Framework

```typescript
import { Component, EventEmitter, Output } from '@angular/core';
	@Component({
		selector: 'app-button',
		templateUrl: './button.component.html',
		styleUrls: ['./button.component.css']
	})

export class ButtonComponent {
	// Propriedade para armazenar o texto do botão
	buttonText: string = 'Clique-me';
	// Evento que será emitido quando o botão for clicado
	@Output() buttonClick = new EventEmitter<void>();
	// Método para emitir o evento quando o botão é clicado
	onButtonClick() {
		this.buttonClick.emit();
	}
}
```

- Essa é a forma básica de desenvolvimento de um componente
- `templateUrl `e `styleUrls `correspondem ao template que será renderizado pelo Angular
- No código HTML, será indicado o seletor no local onde o componente será colocado:

```html
<button (click)="onButtonClick()">{{ buttonText }}</button>
```

- A montagem de todos os componentes da aplicação é feita em um arquivo chamado `app.module.ts` que normalmente tem o seguinte conteúdo: 

```typescript
import { NgModule } from '@angular/core';
import { BrowserModule } from '@angular/platform-browser';
import { AppComponent } from './app.component';
import { ButtonComponent } from './button/button.component';

@NgModule({
	declarations: [
		AppComponent,
		ButtonComponent
	],
	imports: [
		BrowserModule
	],
	providers: [],
	bootstrap: [AppComponent]
})

export class AppModule { }
```

- Atenção especial ao decorador `**@NgModule**` que é responsável por marcar uma classe como um módulo Angular e fornecer metadados que dizem ao Angular como compilar e executar esse módulo.

# Diretivas

- **ng-app** define uma aplicação AngularJS
- **ng-model** vincula um campo de formulário com uma variável da aplicação Angular
	- Ela pode também:
		- Provide type validation for application data (number, email, required).
```html
<form ng-app="" name="myForm">
  Email:
  <input type="email" name="myAddress" ng-model="text">
  <span ng-show="myForm.myAddress.$error.email">Not a valid e-mail address</span>
</form>

<!-- o span com a diretiva ng-show irá aparecer na tela somente se a condição resolver como True -->
```
		- Provide status for application data (invalid, dirty, touched, error).
```html
<form ng-app="" name="myForm" ng-init="myText = 'post@myweb.com'">
  Email:
  <input type="email" name="myAddress" ng-model="myText" required>
  <h1>Status</h1>
  {{myForm.myAddress.$valid}}   <!-- True se a validação do campo ocorreu com sucesso (e-mail) -->
  {{myForm.myAddress.$dirty}}   <!-- True se o campo foi alterado -->
  {{myForm.myAddress.$touched}} <!-- True se este campo aqui foi clicado -->
</form>
```
		- Provide CSS classes for HTML elements.
```html
<!-- Define a cor que será automaticamente aplicada quando a entrada for inválida -->
<style>
input.ng-invalid {
  background-color: lightblue;
}
</style>
<body>

<form ng-app="" name="myForm">
  Enter your name:
  <input name="myName" ng-model="myText" required>
</form>

<!-- Outras classes autmatizadas estão disponíveis:
	ng-empty
	ng-not-empty
	ng-touched
	ng-untouched
	ng-valid
	ng-invalid
	ng-dirty
	ng-pending
	ng-pristine
-->
```
		- Bind HTML elements to HTML forms.
- **ng-bind** acessa o valor da variável da aplicação angular
- **ng-init** inicializa uma variável com um determinado valor
	- Pode ser utilizado mais de um na mesma inicialização: `<div ng-app="" ng-init="quantity=1;cost=5">`
- **ng-repeat **estrutura de repetição. Ele clona o elemento html uma vez para cada elemento de um array
```html
<div ng-app="" ng-init="names=[
{name:'Jani',country:'Norway'},
{name:'Hege',country:'Sweden'},
{name:'Kai',country:'Denmark'}]">

<ul>
  <li ng-repeat="x in names">
    {{ x.name + ', ' + x.country }}
  </li>
</ul>

</div>
```
- Novas diretivas personalizadas podem ser criadas utilizando a função `**.directive**`
```html
<body ng-app="myApp">

<w3-test-directive></w3-test-directive>

<script>
var app = angular.module("myApp", []);
app.directive("w3TestDirective", function() {
  return {
    template : "<h1>Made by a directive!</h1>"
  };
});
</script>

</body>
```
- Podem ser invocadas como:
	- Tag html
	- Atributo
	- Classe
	- Comentário
```html
<!-- Exemplos -->

<!-- Tag -->
<w3-test-directive></w3-test-directive>

<!-- Atributo -->
<div w3-test-directive></div>

<!-- Classe -->
<div class="w3-test-directive"></div>

<!-- Comentário -->
<!-- directive: w3-test-directive -->
```
- No entanto, este comportamento pode ser restringido pela propriedade `restrict`
```javascript
var app = angular.module("myApp", []);
app.directive("w3TestDirective", function() {
  return {
    restrict : "A",
    template : "<h1>Made by a directive!</h1>"
  };
});

/* Onde:

E for Element name
A for Attribute
C for Class
M for Comment
/*
```

# Expressões

- São escritas dentro de {{ }}
- Pode ser utilizado inclusive para alterar propriedades CSS
- Não suportam estruturas de controle como loops, condicionais, etc.

```html
<div ng-app="" ng-init="myCol='lightblue'">

<input style="background-color:{{myCol}}" ng-model="myCol">

</div>
```

# Modules

- Módulos são contêineres para diferentes partes de uma aplicação
- São também contêineres para controllers
- Um controller sempre pertence a um módulo

```html
<div ng-app="myApp">...</div>

<script>

var app = angular.module("myApp", []);

</script>
```

## Adicionando um controller

```html
<div ng-app="myApp" ng-controller="myCtrl">
{{ firstName + " " + lastName }}
</div>

<script>

var app = angular.module("myApp", []);

app.controller("myCtrl", function($scope) {
  $scope.firstName = "John";
  $scope.lastName = "Doe";
});

</script>
```

# Scope

- Quando é utilizado um `**controller**`** **ele recebe como parâmetro um `$scope`
- Quando são adicionadas propriedades dentro do `$scope` por um controller, o view (HTML) recebe acesso a esta propriedade
- Na view, não é necessário utilizar `$scope`, apenas o nome da propriedade
- Existe um $rootScope padrão (não precisa ser definido)
- Cada controller vai ter seu $scope. Caso dois models tenham o mesmo nome, valerá o $scope mais específico

# Filters

- O AngularJS provê filtros para transformação de dados:
	- `currency` Format a number to a currency format.
```javascript
{{ number | currency : symbol : fractionsize }}
```
	- `date` Format a date to a specified format.
	- `filter` Select a subset of items from an array.
	- `json` Format an object to a JSON string.
	- `limitTo` Limits an array/string, into a specified number of elements/characters.
	- `lowercase` Format a string to lower case.
	- `number` Format a number to a string.
	- `orderBy` Orders an array by an expression.
	- `uppercase` Format a string to upper case.
- Filtros podem ser invocados pelo caractére `|` logo após o **model**
```html
<div ng-app="myApp" ng-controller="personCtrl">

<p>The name is {{ lastName | uppercase }}</p>

</div>
```
- Filtros também podem ser utilizados em diretivas
```html
<div ng-app="myApp" ng-controller="namesCtrl">
	<ul>
	  <li ng-repeat="x in names | orderBy:'country'">
	    {{ x.name + ', ' + x.country }}
	  </li>
	</ul>
</div>
```
- O filtro `filter `pode ser utilizado em arrays somente
```html
<!--Return the names that contains the letter "i":-->
<div ng-app="myApp" ng-controller="namesCtrl">
	<ul>
	  <li ng-repeat="x in names | filter : 'i'">
	    {{ x }}
	  </li>
	</ul>
</div>

<!-- O exemplo abaixo filtra uma lista dinamicamente com base em um input -->
<div ng-app="myApp" ng-controller="namesCtrl">
<p><input type="text" ng-model="test"></p>
<ul>
  <li ng-repeat="x in names | filter : test">
    {{ x }}
  </li>
</ul>
</div>
```

# Services

- São objetos ou funções disponíveis e limitados para a aplicação AngularJS
- Existem aproximadamente 30 services fornecidos com o framework
- Principais:
	- `$location` → Possui métodos que retornam informações sobre a location da página atual
	- `$http` → Utilizado para faze requisições
		- Na prática, `$http` é um objeto **XMLHttpRequest**
		- O resultado é esperado que seja um JSON
```javascript
var app = angular.module('myApp', []);
app.controller('myCtrl', function($scope, $http) {
  $http.get("welcome.htm").then(function (response) {
    $scope.myWelcome = response.data;
  });
});
```
	- `$timeout`
	- `$interval`

# Eventos

- Funcionam como event listeners adicionados às views HTML
	- `ng-blur`
	- `ng-change`
	- `ng-click`
	- `ng-copy`
	- `ng-cut`
	- `ng-dblclick`
	- `ng-focus`
	- `ng-keydown`
	- `ng-keypress`
	- `ng-keyup`
	- `ng-mousedown`
	- `ng-mouseenter`
	- `ng-mouseleave`
	- `ng-mousemove`
	- `ng-mouseover`
	- `ng-mouseup`
	- `ng-paste`
- Exemplos
```html
<div ng-app="myApp" ng-controller="myCtrl">
	<h1 ng-mousemove="count = count + 1">Mouse over me!</h1>
	<h2>{{ count }}</h2>
</div>
<script>
var app = angular.module('myApp', []);
app.controller('myCtrl', function($scope) {
  $scope.count = 0;
});
</script>

<!-- Pode ser especificado uma função como ação do event -->

<div ng-app="myApp" ng-controller="myCtrl">
	<button ng-click="myFunction()">Click me!</button>
	<p>{{ count }}</p>
</div>
<script>
	var app = angular.module('myApp', []);
	app.controller('myCtrl', function($scope) {
	  $scope.count = 0;
	  $scope.myFunction = function() {
	    $scope.count++;
	  }
	});
	</script>
```
- O objeto `$event` pode ser passado como parâmetro para a função invocada
	- Este objeto contém informações sobre o evento do navegador
```html
<div ng-app="myApp" ng-controller="myCtrl">
	<h1 ng-mousemove="myFunc($event)">Mouse Over Me!</h1>
	<p>Coordinates: {{x + ', ' + y}}</p>
</div>
<script>
	var app = angular.module('myApp', []);
	app.controller('myCtrl', function($scope) {
	  $scope.myFunc = function(myE) {
	    $scope.x = myE.clientX;
	    $scope.y = myE.clientY;
	  }
	});
</script>
```

# Formulários

- Possuem variáveis de estado e validação fornecidas pelo Angular, tanto para os campos individualmente quanto para o formulário como um todo
- Campos:
	- `$untouched` The field has not been touched yet
	- `$touched` The field has been touched
	- `$pristine` The field has not been modified yet
	- `$dirty` The field has been modified
	- `$invalid` The field content is not valid
	- `$valid` The field content is valid
- Formulário:
	- `$pristine` No fields have been modified yet
	- `$dirty` One or more have been modified
	- `$invalid` The form content is not valid
	- `$valid` The form content is valid
	- `$submitted` The form is submitted
- Exemplo: 
```html
<input name="myName" ng-model="myName" required>
<span ng-show="myForm.myName.$touched && myForm.myName.$invalid">The name is required.</span>
```
- Também existem classes CSS pré-definidas pelo Angular, que auxiliam na visualização destas propriedades nos formulários
- Classes CSS para os Campos:
	- `ng-untouched` The field has not been touched yet
	- `ng-touched` The field has been touched
	- `ng-pristine` The field has not been modified yet
	- `ng-dirty` The field has been modified
	- `ng-valid` The field content is valid
	- `ng-invalid` The field content is not valid
	- `ng-valid-``*key*` One *key* for each validation. Example: `ng-valid-required`, useful when there are more than one thing that must be validated
	- `ng-invalid-``*key*` Example: `ng-invalid-required`
- Classes CSS para o formulário:
	- `ng-pristine` No fields has not been modified yet
	- `ng-dirty` One or more fields has been modified
	- `ng-valid` The form content is valid
	- `ng-invalid` The form content is not valid
	- `ng-valid-``*key*` One *key* for each validation. Example: `ng-valid-required`, useful when there are more than one thing that must be validated
	- `ng-invalid-``*key*` Example: `ng-invalid-required`
```html
<style>
input.ng-invalid {
  background-color: pink;
}
input.ng-valid {
  background-color: lightgreen;
}
</style>
```

# API

- Um conjunto de métodos utilitários que podem ser acessados pelo objeto Angular. Exemplos:
| `angular.lowercase()` | Converts a string to lowercase |
| --- | --- |
| `angular.uppercase()` | Converts a string to uppercase |
| `angular.isString()` | Returns true if the reference is a string |
| `angular.isNumber()` | Returns true if the reference is a number |

# Include

- A diretiva `ng-include` permite a inclusão de outros arquivos html, dinamicamente
```html
<body ng-app="">
	<div ng-include="'myFile.htm'"></div>
</body>
```
- Por padrão, não é possível incluir arquivos html de outros domínios. Para isso, é necessário a inclusão de uma whitelist: 
```html
<body ng-app="myApp">
	<div ng-include="'https://tryit.w3schools.com/angular_include.php'"></div>	
	<script>
		var app = angular.module('myApp', [])
		app.config(function($sceDelegateProvider) {
		  $sceDelegateProvider.resourceUrlWhitelist([
		    'https://tryit.w3schools.com/**'
		  ]);
		});
	</script>
</body>
```

# Routing

- Permite que a aplicação funcione como SPA, sem reload de páginas
- É necessário utilizar o módulo `ngRoute`
- É tratado em um script separado que deverá ser importado pela aplicação
```javascript
<!-- 1: Importar o script -->
<script src="https://ajax.googleapis.com/ajax/libs/angularjs/1.6.9/angular-route.js"></script>

<!-- 2: Adicionar o ngRoute como dependência para a aplicação -->
var app = angular.module("myApp", ["ngRoute"]);

<!-- 3: Utilizar o $routerProvider para configurar as diferentes rotas na sua aplicação -->
app.config(function($routeProvider) {
  $routeProvider
  .when("/", {
    templateUrl : "main.htm"
  })
  .when("/red", {
    templateUrl : "red.htm"
  })
  .when("/green", {
    templateUrl : "green.htm"
  })
  .when("/blue", {
    templateUrl : "blue.htm"
  });
});
```
- O conteúdo invocado pelo router será renderizado no container definido por `ng-view`
- Só pode existir uma `ng-view` por aplicação (`ng-app`)
- A `ng-view` pode ser definida das seguintes formas
```html
<div ng-view></div>
<ng-view></ng-view>
<div class="ng-view"></div>
```
- Exemplo completo
```html
<!DOCTYPE html>
<html>
	<script src="https://ajax.googleapis.com/ajax/libs/angularjs/1.6.9/angular.min.js"></script>
	<script src="https://ajax.googleapis.com/ajax/libs/angularjs/1.6.9/angular-route.js"></script>

	<body ng-app="myApp">
		<p><a href="#/!">Main</a></p>
		<a href="#!london">City 1</a>
		<a href="#!paris">City 2</a>

		<p>Click on the links to read about London and Paris.</p>
		
		<div ng-view></div>
		
		<script>
			var app = angular.module("myApp", ["ngRoute"]);
			app.config(function($routeProvider) {
			    $routeProvider
			    .when("/", {
			        templateUrl : "main.htm"
			    })
			    .when("/london", {
			        templateUrl : "london.htm"
			    })
			    .when("/paris", {
			        templateUrl : "paris.htm"
			    });
			});
		</script>
	</body>
</html>
```

# Angular CLI

- Seguem a sintaxe: `ng <argumentos> [opções]`
- Principais comandos:
	- `ng add`
		- Adiciona bibliotecas
	- `ng build`
		- Gera os arquivos estáticos
	- `ng deploy`
		- Implanta em um serviço de nuvem pré-configurado
	- `ng generate`
		- Gera e modifica arquivos do projeto Angular, como **componentes, serviços, módulos**, entre outros
	- `ng new`
		- Cria um novo projeto com a estrutura inicial

# AngularJS

> [!note] 🔥
> Sua versão original, chamada de AngularJS, equivale às versões anteriores ao Angular 2 - ou seja, as versões 1.x. Isso pois a versão do Angular 2 foi “reescrita” para ser baseada em TypeScript, não mais puramente em JavaScript. 
Então cuidado, pois AngularJS e Angular, apesar de serem derivados de um mesmo framework, **são coisas distintas**. Essa aula terá como foco o AngularJS.

- Uma aplicação AngularJS segue o padrão MVC
	- View - é o HTML
	- Model - são os dados disponíveis para a view atual
	- Controller - São as funções JavaScript que produzem, alteram, removem e controlam os dados
- Utiliza abordagem **modular e baseada em componentes**
- Possui **injeção de dependências** e separação de responsabilidades
- Facilita a escrita de testes unitários e de integração. 
- É projetado para ser testável desde o início, oferecendo suporte para bibliotecas de testes como Jasmine e Karma.

## MVW

- Apesar da construção feita em MVC, o Google “vende” o Angular como adepta ao modelo MVW
- **Model-View-Whatever**. Isso quer dizer que podemos ter qualquer coisa ocupando o espaço do
controlador: testes unitários, diretivas, ou um próprio controlador.

## Diretivas

- Estendem a capacidade do HTML
- Marcadores especiais no HTML que o AngularJS reconhece e utiliza para anexar comportamento específico a um elemento DOM ou até mesmo transformar o DOM
- Começam com o prefixo `**ng-**`

```html
<div ng-app="">
	<p>Name: <input type="text" ng-model="name"></p>
	<p ng-bind="name"></p>
</div>
```

## ng-model vs ng-bind

### **ng-model**

- Realiza vinculação de dados bidirecional (two-way data binding) entre o modelo e a view[1](https://stackoverflow.com/questions/12419619/whats-the-difference-between-ng-model-and-ng-bind)[4](https://findnerd.com/list/view/-Difference-between-ng-model-and-ng-bind/22416/).
- Geralmente usado em elementos de formulário como inputs, selects e textareas[2](https://www.w3schools.com/angular/angular_model.asp)[5](https://www.guru99.com/pt/ng-model-angularjs.html).
- Atualiza o modelo quando o usuário altera o valor na view, e vice-versa[2](https://www.w3schools.com/angular/angular_model.asp).

Exemplo:

```html
<input ng-model="nome">
<p>Olá, {{nome}}!</p>
```

### **ng-bind**

- Realiza vinculação de dados unidirecional (one-way data binding) do modelo para a view.
- Usado para exibir valores do modelo em elementos HTML.
- Atualiza apenas a view quando o modelo muda, não o contrário.

Exemplo:

```html
<p ng-bind="nome"></p>
```

## Controllers

- São ferramentas do AngularJS responsáveis por controlar os dados da aplicação
- Fazem a ponte entre a camada de modelo, e de visualização
- Eles funcionam como objetos de JavaScript, e são criados a partir de construtores de objeto do JavaScript
- A diretiva ng-controller é a responsável por definir o controlador da aplicação

```html
<div ng-app="myApp" ng-controller="myCtrl">

	Nome: <input type="text" ng-model="firstName"><br>
	Sobrenome: <input type="text" ng-model="lastName"><br>
	<br>
	Nome completo: {{firstName + " " + lastName}}
	
</div>

<script>
	var app = angular.module('myApp', []);
	
	app.controller('myCtrl', function($scope) {
		$scope.firstName = "João";
		$scope.lastName = "da Silva";
	});
</script>
```

- É possível também implementar métodos como propriedades dentro de um controlador.

```html
<div ng-app="myApp" ng-controller="myCtrl">

	Nome: <input type="text" ng-model="firstName"><br>
	Sobrenome: <input type="text" ng-model="lastName"><br>
	<br>
	Nome completo: {{fullName()}}
	
</div>

<script>
	var app = angular.module('myApp', []);
	app.controller('myCtrl', function($scope) {
		$scope.firstName = "João";
		$scope.lastName = "da Silva";
		$scope.fullName = function() {
			return $scope.firstName + " " + $scope.lastName;
		};
});
</script>
```

- O escopo de um controlador é limitado ao elemento que o declarou.
- O código abaixo, por exemplo, não funciona devido ao fato da propriedade estar sendo chamada fora do seu escopo

```html
<div ng-app="myApp">
	<div ng-app="myApp" ng-controller="myCtrl">
		First Name: <input type="text" ng-model="firstName"><br>
		Last Name: <input type="text" ng-model="lastName"><br>
		<br>
		Full Name: {{fullName()}}
	</div>
	<p>
		Aqui dará erro por estar fora do escopo! {{fullName()}}
	</p>
</div>
```

## Services

- Auxiliam na **modularidade **e **reutilização **do código
- Compartilham **funcionalidades **entre partes da aplicação
- Existem services pré-prontos, porém é possível criar novos personalizados
- Muitas das informações obtidas pelos serviços são** retiradas do DOM**, e poderiam ser **utilizadas diretamente**
- Por exemplo, o `$location` traz a mesma informações que o `windows.location`
- Principais services prontos:
	- `$http`
		- Chamadas HTTP (GET, POST, PUT, etc)
	- `$q`
		- Implementação de promises
	- `$rootScope`
		- Escopo raiz que é criado no topo da hierarquia de escopos do AngularJS
	- `$location`
		- Ler ou alterar URL da aplicação
	- `$route`
		- Roteamento
- Os services funcionam como objetos do tipo **singleton**

```javascript
// Definindo o módulo AngularJS
var app = angular.module('userApp', []);

// Definindo o controlador
app.controller('UserController', ['$scope', '$http', function($scope, $http) {
	$scope.users = [];
	$scope.errorMessage = '';
	
	// Função para buscar usuários
	$scope.fetchUsers = function() {
		$http.get('https://jsonplaceholder.typicode.com/users')
			.then(function(response) {
				// Sucesso na requisição
				$scope.users = response.data;
			})
		.catch(function(error) {
			// Erro na requisição
			$scope.errorMessage = 'Erro ao buscar usuários: ' + error.message; });
		};
}]);
```

## Routing

```javascript
var app = angular.module("myApp", ["ngRoute"]);
	app.config(function($routeProvider) {
	$routeProvider
	.when("/", {
		templateUrl : "main.htm"
	})
	.when("/london", {
		templateUrl : "london.htm"
	})
	.when("/paris", {
		templateUrl : "paris.htm"
	});
});
```
