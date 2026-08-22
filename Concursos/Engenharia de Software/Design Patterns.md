---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2026-08-05T17:06:00
Owner:
  - Eduardo Quinalha
---
[https://brizeno.wordpress.com/padroes/](https://brizeno.wordpress.com/padroes/)

![[20230829_225319.jpg]]

# Padrões de Projetos GoF

[https://refactoring.guru/pt-br/design-patterns/factory-method](https://refactoring.guru/pt-br/design-patterns/factory-method)

![[Untitled 562.png]]

## **Padrões criacionais**

> [!note] 🔥
> **Uma fábrica abstrata constrói um protótipo único.**
> - Factory
> - Abstract Factory
> - Builder
> - Prototype
> - Singleton

- Estes padrões fornecem vários mecanismos de criação de objetos, que aumentam a flexibilidade e reutilização de código já existente.
- Abstraem ou adiam o processo de criação de objetos
- Fornecem mecanismos de criação de objeto que aumentam a flexibilidade e reutilização do código

### Factory Method

- Fornece uma interface para criar objetos
- Permite que as subclasses alterem o tipo de objeto que será criado
- Na classe cliente, ao invés de instanciar diretamente o objeto desejado com o operador `new`, chama-se a classe Factory que irá retornar uma instância pronta
- A lógica de escolha do tipo de objeto que será criado é encapsulada pela classe Factory
- delega a responsabilidade de instanciação para as subclasses.

<!-- Column 1 -->
![[Untitled 563.png]]

<!-- Column 2 -->
![[Untitled 564.png]]

### Abstract Factory

- Fornece uma interface para criar **famílias de objetos relacionados** ou **dependentes** **sem especificar suas classes concretas.**
- Isola o cliente (código que necessita do objeto) da lógica de criação dos objetos
- É uma abstração do padrão Factory

![[image 121.png]]

### Builder

- Permite a construção de **objetos complexos passo a passo**
- Resolve o problema de onde seria necessário um **construtor com muitos parâmetros**

<!-- Column 1 -->
![[Untitled 565.png|Sem o padrão Builder]]

<!-- Column 2 -->
![[Untitled 566.png|Com o padrão Builder]]

- O Builder **não permite que outros objetos acessem o produto enquanto ele está sendo construído.**
- **Não precisa chamar todas as etapas**. Você chama apenas aquelas etapas que são necessárias para a produção de uma configuração específica de um objeto.

### Prototype

- Permite **copiar objetos existentes**, sem deixar o código **dependente de suas classes**
- Delega para o próprio objeto o processo de clonagem deste
- Na abordagem mais Trivial para este problema, você teria que:
	- Saber a classe que criou aquele objeto e instanciar um novo
	- Copiar cada atributo para o novo objeto
- Porém:
	- Alguns atributos podem ser privados
	- Seu código torna-se dependente da classe (acoplamento)
	- Algumas vezes só sabe-se a interface que criou o objeto e não sua classe concreta (polimorfismo)

### Singleton

- Garante que uma classe tenha apenas uma instância
- Provê um ponto de acesso global para esta
- Utiliza o construtor padrão privado, para prevenir que outros objetos usem o operador `new` com a classe singleton.
- O objeto singleton é inicializado somente quando for pedido pela primeira vez.
- Desvantagens
	- Viola o *princípio de responsabilidade única*. 
	- requer tratamento especial em um ambiente multithreaded para que múltiplas threads não possam criar um objeto singleton várias vezes.
	- **Pode ser difícil realizar testes unitários do código cliente do Singleton porque muitos frameworks de teste dependem de herança quando produzem objetos simulados**. 
	- 

## **Padrões estruturais**

> [!note] 🔥
> A **ponte adaptada **é **composta **de **decorações **na **fachada** para o **peso mosca** se “**aproxymar**”.
> - Bridge
> - Adapter
> - Composite
> - Decorator
> - Facade
> - Flyweight
> - Proxy

- Estes padrões explicam como montar objetos e classes em estruturas maiores mas ainda mantendo essas estruturas flexíveis e eficientes.
- Preocupam-se como as classes e objetos são compostos para formar estruturas maiores
- Explicam como montar objetos e classes em estruturas maiores, mantendo as estruturas flexíveis e eficientes

### Adapter

- Permite** objetos com interfaces incompatíveis **colaborarem entre si.
- Algumas vezes é possível criar um adaptador de duas vias que pode converter as chamadas em ambas as direções.
- Utilizado para dar uma interface padrão para uma série de classes específicas, por baixo.

![[Untitled 567.png]]

![[Untitled 568.png]]

### Bridge

- **Desacopla uma interface de sua implementação**, de forma que ambas possam variar independentemente
- **Fornece um nível de abstração maior que o Adapter**, na medida em que permite variações independentes da interface e da implementação.
- Permite que você divida uma classe grande ou um conjunto de classes intimamente ligadas em duas hierarquias separadas—**abstração e implementação**—que podem ser desenvolvidas independentemente umas das outras.
- O padrão Bridge troca a abordagem de **herança para composição** do objeto.
- Isso significa que você **extrai uma das dimensões em uma hierarquia de classe separada**, para que as classes originais referenciem um objeto da nova hierarquia, ao invés de ter todos os seus estados e comportamentos dentro de uma classe.
- Exemplo:
	- Problema:
![[Untitled 569.png]]
	- Quanto mais formas ou cores forem adicionais, mais classes concretas diferentes seriam necessárias
	- Solução: Bridge
![[Untitled 570.png]]

### Composite

- Permite que você componha objetos em **estruturas de árvores** e então trabalhe com essas estruturas **como se elas fossem objetos individuais.**
- Faz sentido apenas quando o modelo central de sua aplicação pode ser **representada como uma árvore.**
- Problema:
	- Suponha uma coleção de classes de caixas que podem conter produtos ou outras caixas menores que, por sua vez, também poderão conter outras caixas ou produtos.
![[Untitled 571.png]]
	- Como fazer para determinar o preço final de um pedido composto de múltiplas caixas/produtos?
- Solução: Composite
	- Elaborar uma interface comum que seja capaz de retornar um preço
	- Se for um produto, retorna seu próprio preço
	- Se for uma caixa, ela retornaria o valor total de seu conteúdo, perguntando a cada item abaixo dela o seu preço
![[Untitled 572.png]]

### Decorator

- Permite que você acople **novos comportamentos** para objetos ao **colocá-los dentro de invólucros de objetos que contém os comportamentos.**
- Assim como bridge, também funciona substituindo o princípio de **herança por agregação**
- “**Envoltório**” (ing. “**wrapper**”) é o apelido alternativo para o padrão Decorator que expressa claramente a ideia principal dele.
- Problema:
	- Suponha uma classe responsável por enviar uma notificação ao usuário.
	- Com o tempo, novos tipos de notificação são adicionados usando-se herança.
	- Para combiná-los, seria necessário criar muitas classes com as possíveis combinações de notificações
![[Untitled 573.png]]

![[Untitled 574.png]]

- Solução
	- Troca da abordagem de herança por agregação ou composição
![[Untitled 575.png]]

### Facade

- Fornece uma **interface simplificada** para uma biblioteca, um framework, ou qualquer **conjunto complexo de classes.**
- Útil quando você precisa integrar sua aplicação com uma biblioteca sofisticada que tem dúzias de funcionalidades, mas você precisa de apenas um pouquinho delas.
- O padrão Facade fornece uma interface simplificada para um conjunto de interfaces em um subsistema, tornando mais fácil para os clientes interagirem com esse subsistema.

![[Untitled 576.png]]

### Flyweight

- Permite a você colocar mais objetos na quantidade de RAM disponível ao compartilhar partes comuns de estado entre os múltiplos objetos ao invés de manter todos os dados em cada objeto.
- Usado para implementar um **pool de Sessions Beans**
- Utilizado quando há um **grande número de objetos similares **que precisam ser criados
- A ideia é **compartilhar** de maneira eficiente esses objetos para **economizar recursos**
- Padrão de projeto **Estrutural**
- Permite a você colocar mais objetos na quantidade de RAM disponível ao compartilhar** partes comuns de estado **entre os múltiplos objetos ao invés de manter todos os dados em cada objeto.
- Usado para implementar um **pool de Sessions Beans**
- Utilizado quando há um **grande número de objetos similares** que precisam ser criados
- Separa o contexto de estado dos objetos em:
	- **Estado extrínscico:** Armazenado em um objeto separado e compartilhado entre as instâncias
	- **Estado intrínsico:** Define o estado individual de cada objeto

### Proxy

- Padrão de projeto estrutural que fornece um objeto que atua como um **substituto** para um objeto de serviço real usado por um cliente. 
- Um proxy recebe solicitações do cliente, realiza alguma tarefa (controle de acesso, armazenamento em cache etc.) e **passa a solicitação para um objeto de serviço.**
- O objeto proxy tem a** mesma interface que um serviço**, o que o torna intercambiável com um objeto real quando passado para um cliente.
- É insubstituível quando você deseja adicionar alguns comportamentos adicionais a um objeto de alguma classe existente sem alterar o código cliente.
- Proxies **delegam todo o trabalho real para algum outro objeto.**
- **Aplicações:**
	- **Inicialização preguiçosa (proxy virtual). **Este é quando você tem um objeto do serviço peso-pesado que gasta recursos do sistema por estar sempre rodando, mesmo quando você precisa dele de tempos em tempos.
		Ao invés de criar um objeto quando a aplicação inicializa, você pode atrasar a inicialização do objeto para um momento que ele é realmente necessário.
	- **Controle de acesso (proxy de proteção). **
	- **Execução local de um serviço remoto (proxy remoto). **Este é quando o objeto do serviço está localizado em um servidor remoto.
		Neste caso, o proxy passa o pedido do cliente pela rede, lidando com todos os detalhes sujos pertinentes a se trabalhar com a rede.
	- **Registros de pedidos (proxy de registro). **Este é quando você quer manter um histórico de pedidos ao objeto do serviço.
	- **Cache de resultados de pedidos (proxy de cache)**
	- **Referência inteligente. **Este é para quando você precisa ser capaz de se livrar de um objeto peso-pesado assim que não há mais clientes que o usam.

## **Padrões comportamentais**

- Estes padrões são voltados aos algoritmos e a designação de responsabilidades entre objetos.
- Concentram-se nos algoritmos e atribuições de responsabilidade entre objetos
- Cuidam de uma comunicação eficaz e da atribuição de responsabilidade entre objetos

### Chain of responsability

- Permite que você passe pedidos por uma **corrente** de handlers
- Ao receber um pedido, cada handler decide se processa o pedido ou o **passa adiante para o próximo handler** na corrente.
- **Cada handler ligado tem um campo para armazenar uma referência ao próximo handler da corrente.**

![[Untitled 577.png]]

### Command

- Transforma um pedido em um objeto independente que contém toda a informação sobre o pedido.
- baseia no princípio da **separação de interesses,**
- Permite que os parâmetros da solicitação sejam parametrizados, enfileirados, logados e até mesmo desfeitos.
- O padrão Command encapsula uma solicitação como um objeto, permitindo que você parametrize clientes com operações, agende solicitações e suporte para operações desfazer. 

### Iterator

- Permite **percorrer elementos de uma coleção sem expor as representações **dele (lista, pilha, árvore, etc.)
- encapsula todos os detalhes da travessia, tais como a posição atual e quantos elementos faltam para chegar ao fim.
- podem averiguar a mesma coleção ao mesmo tempo, independentemente um do outro.
- **fornecem um método primário para pegar elementos de uma coleção**. 
- O cliente pode manter esse método funcionando até que ele não retorne mais nada, o que significa que o iterador atravessou todos os elementos.

### Mediator

- permite que você reduza as dependências caóticas entre objetos.
- **restringe comunicações diretas entre objetos** e os força a colaborar apenas através do objeto mediador.
- define um objeto que encapsula a forma como um conjunto de objetos **interage**
- promove o **baixo acoplamento entre esses objetos,** evitando que eles se refiram explicitamente uns aos outros, permitindo assim a independência entre eles.

### Memento

- permite que você **salve e restaure o estado anterior de um objeto** sem revelar os detalhes de sua implementação.
- Frequentemente utilizado para implementar comando “desfazer” ou “undo”
- Externaliza o estado interno de um objeto, sem violar o encapsulamento

### Observer

- Event Listener
- Event Subscriber
- Define um mecanismo de assinatura para **notificar múltiplos objetos sobre quaisquer eventos que aconteçam com o objeto que está sendo observado**

### State

- Permite que um objeto altere seu comportamento quando seu estado interno muda
- Como se mudasse de classe
- intimamente relacionado com o conceito de uma** *****Máquina de Estado Finito***

### Strategy

- permite que você defina uma família de algoritmos, coloque-os em classes separadas, e faça os objetos deles **intercambiáveis**.
- O padrão Strategy sugere que você pegue uma classe que faz algo específico em **diversas maneiras diferentes** e extraia todos esses algoritmos para classes separadas chamadas ***estratégias***.
- A classe original, chamada ***contexto***, deve ter um campo para armazenar uma **referência para um dessas estratégias. **
- O contexto **delega** o trabalho para um objeto estratégia ao invés de executá-lo por conta própria.

![[Untitled 578.png]]

### Template Method

- Define o esqueleto de um algoritmo na superclasse mas deixa as **subclasses sobrescreverem etapas específicas do algoritmo sem modificar sua estrutura.**
- O padrão do Template Method sugere que você quebre um algoritmo em uma **série de etapas**, transforme essas etapas em métodos, e coloque uma série de chamadas para esses métodos dentro de um único *método padrão*.
- Para usar o algoritmo, o cliente deve fornecer sua própria subclasse, implementar todas as etapas abstratas, e sobrescrever algumas das opcionais se necessário (mas não o próprio método padrão).

![[Untitled 579.png]]

### Visitor

- permite que você **separe algoritmos dos objetos nos quais eles operam.**

---

[http://en.wikipedia.org/wiki/GRASP_(object-oriented_design)](http://en.wikipedia.org/wiki/GRASP_(object-oriented_design))

# GRASP

- Soluções reutilizáveis para atribuir **responsabilidades** a classes e objetos na** Programação Orientada a Objetos** (POO).

## Alta Coesão

- Cada classe deve focar apenas em sua responsabilidade

## Baixo Acoplamento

- As classes devem possuir pouca dependência umas das outras.

## Controller

- Uma classe é responsável por tratar os** eventos do sistema. **
- Na prática, essa classe **representa o sistema** ou um **cenário do caso de uso** em que o evento ocorre.
- Tem como objetivo a separação do controle da interface das demais partes do sistema.

## Creator

- Responsável por criar instâncias / objetos **de outra classe.**

## Information Expert

- Uma classe ou um objeto pode **delegar** uma **responsabilidade** a outro(a), que é especialista no domínio em questão
- Quem recebe a delegação possui as **informações necessárias para o cumprimento da responsabilidade.**

## Pure Fabrication

- Classe **fictícia**, com **comportamento artificial**, que não possui vínculos, **nem representa o domínio em questão**. 
- Está lá apenas para **prestar ****um ****serviço**, por conveniência.

## Indirection

- Um objeto ou uma classe realiza a **mediação** entre dois elementos, de maneira intermediária. 
- É uma espécie de **delegação de responsabilidades**, mantendo o baixo acoplamento entre os elementos envolvidos.

## Polimorfismo

- Uma classe pode apresentar **métodos similares**, mas com** comportamentos diferentes**, cada qual com sua responsabilidade.

## Protected Variations

- Identifica **pontos de variação** ou **instabilidade **no sistema
- Por meio da atribuição de responsabilidades, é criada uma** *****interface *****estável**, evitando que os componentes do sistema tenham variantes.
