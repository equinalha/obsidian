---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2024-10-01T17:18:00
Owner:
  - Eduardo Quinalha
---
# Tipos de Aplicativos

## Nativos

- Desenvolvidos especificamente para cada plataforma
- Amplo acesso ao hardware
- Melhor desempenho
- Podem funcionar sem conexão com a internet

## Webapp

- Trata-se de um site web desenvolvido para dispositivos móveis
- Programados em HTML 5, CSS e JavaScript
- São mais lentos e não conseguem utilizar todas as funcionalidades do dispositivo
- São PWA

## Híbridos

- Combina elementos de aplicativos nativos e aplicativos da web.
- utiliza uma **WebView**, que é uma instância isolada do navegador dentro do aplicativo, para carregar e executar um aplicativo da web
- Isso permite que o aplicativo híbrido acesse recursos nativos do dispositivo, como a câmera ou o armazenamento local, enquanto ainda é capaz de carregar conteúdo web que pode ser atualizado sem necessidade de distribuir uma nova versão do aplicativo nativo.

# Android

## Fundamentos

- Baseado no Kernel Linux
- **Cada aplicativo é um usuário diferente**
	- Existe a possibilidade de dois aplicativos compartilharem o mesmo usuário, o que permite que acessem arquivos um do outro
	- Para isso é necessário que tenham o mesmo certificado
- Cada processo tem sua própria VM
- Adota o princípio do privilégio mínimo
- Cada app tem sua área de armazenamento privada
- Trabalha com mapeamento e paginação em memória
- Uma área de memória utilizada por um app não pode ser despaginada, salvo em necessidade de liberação de memória
- A máquina virtual responsável por executar os aplicativos chama-se ART (Android Run Time)

## Componentes

- Interagem entre si
- Definidos dentro do `AndroidManifest.xml`
	- **Activities**
		- Representa uma única tela com uma UI
		- Ponto de interação principal entre o usuário e o aplicativo
	- **Services**
		- Executa operações em segundo plano
	- **Content Providers**
		- Gerenciam o acesso a um conjunto estruturado de dados
		- Permite o compartilhamento de dados entre aplicativos
		- Exemplo:
			- Acesso aos contatos, fotos ou vídeos do aparelho
			- Acesso a um banco SQLite
	- **Broadcast Receivers**
		- Permite que o aplicativo responda a mensagens enviadas pelo sistema ou outros aplicativos
		- Eventos de sistema, recebimento de mensagens SMS ou eventos de alarme
	- **Fragments**
		- Porção reutilizável da UI dentro de uma activity
	- **Resources**
		- Arquivos que fornecem dados adicionais e conteúdo
		- Layouts, drawable, values, temas, etc.
	- **Android Manifest**
		- Declara todos os componentes do aplicativo

## Intent

- Objeto de mensagens que permite a comunicação entre diferentes componentes de um aplicativo (como atividades, serviços, e receptores de broadcast) ou até mesmo entre diferentes aplicativos
- usadas principalmente para iniciar novas atividades
- Podem ser
	- Explícitas: A chamada à intent especifica diretamente o componente que será acessado
	- Implícitas: A chamada deixa o Android decidir o que será chamado. Exemplo:
```java
Intent intent = new Intent(Intent.ACTION_VIEW);
intent.setData(Uri.parse("https://www.example.com"));
startActivity(intent);
```

## Android Manifest

- Descreve a estrutura e as configurações do aplicativo
- Manifest.permission
	- Quando o aplicativo necessita utilizar um recurso protegido pelo SO é necessário declarar esta permissão no manifest
`<uses-permission android:name="android.permission.CAMERA" />`
- Manifest.permission_group
	- Agrupamento de permissões relacionadas a um determinado conjunto de recursos ou funcionalidade

## Activity

- Uma "activity" é uma classe que representa uma **tela ou uma janela** com a qual o usuário interage
- Para navegar pelas transições entre os estágios do ciclo de vida da atividade, o A classe `Activity` fornece um conjunto principal de seis callbacks: 
	- [`onCreate()`](https://developer.android.com/reference/android/app/Activity?hl=pt-br#onCreate(android.os.Bundle)), 
		- Acionado assim que o sistema cria a atividade
		- Pode ser usado para lógica básica de inicialização do aplicativo que acontece **apenas uma vez** durante toda a vida da atividade
		- pode vincular dados a listas, associar a atividade a um [`ViewModel`](https://developer.android.com/reference/androidx/lifecycle/ViewModel?hl=pt-br)
		- recebe o evento parâmetro `savedInstanceState`, que é um [`Bundle`](https://developer.android.com/reference/android/os/Bundle?hl=pt-br) que contém o estado anteriormente salvo da atividade. 
	- [`onStart()`](https://developer.android.com/reference/android/app/Activity?hl=pt-br#onStart()), 
		- Invocado quando a atividade entra no estado Iniciado
		- Torna a atividade visível na tela
		- prepara a atividade para entrar em primeiro plano e se tornar interativa
		- é concluído rapidamente e, como no estado Criado, a atividade não permanece no estado Iniciado. 
		- Quando esse callback termina, a atividade insere o *Retomado* e o sistema invoca o [`onResume()`](https://developer.android.com/reference/android/app/Activity?hl=pt-br#onResume()).
	- [`onResume()`](https://developer.android.com/reference/android/app/Activity?hl=pt-br#onResume()), 
		- É nesse estado que o aplicativo **interage com o usuário**
		- Coloca em **primeiro plano**
		- Também invocado quando a atividade é ativada novamente** após uma interrupção**
		- O aplicativo permanece nesse estado até que algo aconteça tirar o foco do aplicativo
		- É nesse momento que os componentes do ciclo de vida podem ativar qualquer funcionalidade que precise operar enquanto o componente estiver visível e em primeiro plano, como o início da visualização da câmera.
		- Quando ocorre um evento de interrupção, a atividade entra no estado *Pausado*, e o sistema invoca o Chamada de retorno [`onPause()`](https://developer.android.com/reference/android/app/Activity?hl=pt-br#onPause()).
	- [`onPause()`](https://developer.android.com/reference/android/app/Activity?hl=pt-br#onPause()), 
		- O sistema chama esse método como a primeira indicação de que o usuário está saindo sua atividade, embora isso não signifique sempre que ela será destruída.
		- Isso indica que a atividade não está mais em primeiro plano, mas está ainda ficará visível se o usuário estiver no modo de várias janelas.
		- Use o método [`onPause()`](https://developer.android.com/reference/android/app/Activity?hl=pt-br#onPause()) para pausar ou ajustar operações que não podem continuar ou que possam continuar com moderação
		- Também é possível usar o método `onPause()` para liberar recursos do sistema, processá-los para sensores (como GPS) ou outros recursos afetar a duração da bateria enquanto sua atividade estiver Pausada e o usuário não precisar deles.
	- [`onStop()`](https://developer.android.com/reference/android/app/Activity?hl=pt-br#onStop())
		- Quando sua atividade não está mais visível para o usuário, ela entra no *Parado*
		- Isso pode ocorrer quando uma atividade recém-iniciada cobre toda a tela.
		- Ou quando a atividade termina de ser executada e está prestes a ser encerrada.
		- Idealmente utilizado para salvar informações em um banco de dados
	- [`onDestroy()`](https://developer.android.com/reference/android/app/Activity?hl=pt-br#onDestroy())
		- Invocado quando:
			-  A atividade está sendo finalizada, porque o usuário descartou completamente o atividade ou devido a [`finish()`](https://developer.android.com/reference/android/app/Activity?hl=pt-br#finish()) sendo seja chamado na atividade.
			- O sistema está destruindo temporariamente a atividade devido a uma configuração mudar, como girar o dispositivo ou entrar no modo de várias janelas
![[SubPages/Pessoal/images/image 57.png]]

## Views

- componentes de interface, como botões, textos, etc.) dentro de uma **Activity** ou **Fragment**. 
- Existem vários tipos de layouts que podem ser aplicados a uma view
	- **LinearLayout**
		- Organiza as views em uma única coluna ou linha (vertical ou horizontal).
		- Permite distribuir espaço disponível entre as views proporcionalmente.
![[SubPages/Pessoal/images/image 58.png]]
	- **RelativeLayout**
		- Permite posicionar as views em relação a outras views ou em relação ao contêiner pai.
		- Por exemplo, você pode alinhar uma view à direita de outra view ou centralizar uma view dentro do layout.
		- As views podem ser alinhadas usando atributos como `layout_alignParentTop`, `layout_centerInParent`, `layout_toRightOf`, etc.
![[SubPages/Pessoal/images/image 59.png]]
	- **ConstraintLayout**
		- permite posicionar e redimensionar views com base em restrições relativas entre elas e em relação ao contêiner pai.
		- **ConstraintLayout** e o **RelativeLayout** possuem similaridades, como a capacidade de posicionar componentes em relação uns aos outros, mas o **ConstraintLayout** é mais avançado e versátil, oferecendo uma gama maior de opções de posicionamento e dimensionamento, além de melhorar o desempenho ao reduzir a profundidade da hierarquia de visualização (view hierarchy).
		- O ConstraintLayout permite que você crie layouts grandes e complexos com uma hierarquia de visualização plana (<u>**sem**</u>** grupos de visualização aninhados**).
			- A fim de possibilitar interfaces mais complexas, era comum o uso de **grupos aninhados **utilizando LinearLayout e RelativeLayout
			- Com o ConstraintLayout isso não é mais necessário
		- É recomendado para layouts complexos, pois pode substituir a necessidade de múltiplos layouts aninhados.
		- As views são posicionadas usando restrições, como `start`, `end`, `top`, `bottom`, e bias (deslocamento).
		- Permite agrupar views em uma cadeia para distribuir espaço horizontal ou vertical de forma uniforme.
![[SubPages/Pessoal/images/image 60.png]]

# Android Enterprise

- Permite o gerenciamento centralizado de dispositivos android em ambiente corporativo

# Kotlin

- **Interoperável com Java** e outras linguagens
- Dentro do Kotlin é possível instanciar classes java
- Multiplataforma
- Também pode ser utilizado server-side
- Atualmente é a linguagem preferencial para aplicações Android
- Podem ser desenvolvidas aplicações utilizado frameworks
	- Spring
	- Ktor

## Conceitos iniciais

- Também utiliza a noção de pacotes, como no Java, no entanto,** não é necessário que o pacote declarado no código seja idêntico ao diretório onde ele se encontra**
- Os arquivos podem ser distribuídos de forma arbitrária na estrutura

```kotlin
// Estrutura do Main
fun main() {
    println("Hello world!")
}

// Ou
fun main(args: Array<String>) {
    println(args.contentToString())
}

print("Hello ")
print("world!")
println("Hello world!")
println(42)

// Funções
// Retorna Int
fun sum(a: Int, b: Int): Int {
    return a + b
}

// Sem retorno
fun printSum(a: Int, b: Int): Unit {
    println("sum of $a and $b is ${a + b}")
}

// Unit pode ser omitido
fun printSum(a: Int, b: Int) {
    println("sum of $a and $b is ${a + b}")
}
```

## Variáveis

- Existem 2 tipos de declarações de variáveis:
	- `val` → Read Only
	- `var` → Mutáveis
```kotlin
val popcorn = 5    // There are 5 boxes of popcorn
val hotdog = 7     // There are 7 hotdogs
var customers = 10 // There are 10 customers in the queue

// Some customers leave the queue
customers = 8
println(customers)
// 8
```

## String Templates

- Uso de variáveis dentro de uma String

```kotlin
val customers = 10
println("There are $customers customers")
// There are 10 customers

println("There are ${customers + 1} customers")
// There are 11 customers
```

# Swift

- Similar a C ou Objective-C
- Código aberto
- Linguagem com tipagem opcional
- Compilada

## Conceitos Iniciais

- Código escrito no contexto global é utilizado como **entrypoint**
	- Não é necessário uma função `main()`
- Não é necessário ; ao final da linha
- Variáveis são declaradas apenas com `let` e `var`

## Strings

```swift
var emptyString = ""               // empty string literal
var anotherEmptyString = String()  // initializer syntax
// these two strings are both empty, and are equivalent to each other

if emptyString.isEmpty {
    print("Nothing to see here")
}
// Prints "Nothing to see here"

let badStart = """
    one
    two
    """
let end = """
    three
    """
print(badStart + end)
// Prints two lines:
// one
// twothree


let goodStart = """
    one
    two

    """
print(goodStart + end)
// Prints three lines:
// one
// two
// three
```

## String Templates

```swift
var word = "cafe"
print("the number of characters in \(word) is \(word.count)")
// Prints "the number of characters in cafe is 4"
```