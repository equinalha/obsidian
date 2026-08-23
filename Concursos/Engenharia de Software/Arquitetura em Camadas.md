---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2024-10-01T17:15:00
Owner:
  - Eduardo Quinalha
---
[https://www.diegomacedo.com.br/arquitetura-de-aplicacoes-em-2-3-4-ou-n-camadas/](https://www.diegomacedo.com.br/arquitetura-de-aplicacoes-em-2-3-4-ou-n-camadas/)

# Arquitetura de 1 camada

- Utilizadas nos antigos mainframes
- O mainframe (nó central da rede) rodava toda a aplicação, inclusive a interface gráfica
- Os terminais (terminais burros) apenas se conectavam ao mainframe e executavam uma instância do programa
- O consumo de recursos era alto
- Não suportava um número muito grande de clientes conectados simultaneamente

# Arquitetura de 2 camadas

- Cliente - Servidor
- Separa fisicamente a interface do usuário da camada de gerenciamento de dados.
- Componentes
	- Servidores
		- Recebem e respondem solicitações dos clientes
		- Não se comunicam com outros servidores diretamente, 
		- prestam serviços distribuídos, 
		- atendem a diversos clientes simultaneamente
		- possuem um poder de processamento e armazenamento mais alto que de um cliente. 
		- Os clientes talvez precisem saber os nomes dos servidores e os serviços que eles fornecem, mas os servidores não precisam saber sobre os clientes.
		- **São responsáveis por:**
			- Banco de dados
	- Clientes
		- Clientes iniciam/terminam a comunicação com servidores, solicitando/terminando serviços distribuídos.
		- Clientes não se comunicam com outros clientes diretamente, são responsáveis pela entrada e saída de dados e comunicação com o usuário e tornam a rede transparente ao usuário
		- Em geral, clientes são computadores pessoais conectados a uma rede.
		-  Um cliente faz um pedido a um servidor e espera até receber uma resposta. 
		- **São responsáveis por:**
			- Apresentação
			- Lógica de negócio
	- Rede
- A vantagem mais importante de um modelo cliente servidor é que ele é uma **arquitetura distribuída.**
- O uso efetivo de sistemas em rede pode ser feito com muitos processadores distribuídos.
- Neste modelo, um programa, normalmente desenvolvido em um ambiente de desenvolvimento, como o Visual Basic, Delphi ou Power Builder, é instalado em cada Cliente. 
- Este programa acessa dados em um servidor de Banco de dados, conforme ilustrado na figura abaixo:

![[Untitled 649.png]]

- Formas de implementação
	- Cliente Magro
	- Cliente Gordo
		- O servidor somente é responsável pelo gerenciamento de dados e o software do cliente implementa a lógica da aplicação e as interações com os usuários
- Desvantagens
	- Uma atualização de interface requer a atualização da aplicação em todos os clientes
	- O mesmo para uma atualização de regra de negócio
	- Podiam ocorrer conflitos de bibliotecas quando sistemas diferentes utilizavam as mesmas bibliotecas em versões diferentes (DLL`s)
	- Falta de escalabilidade (conexões a bancos de dados)
	- Enormes problemas de manutenção (mudanças na lógica de aplicação forçava instalações)
	- Dificuldade de acessar fontes heterogêneas (legado CICS, 3270, …)

# Arquitetura em 3 camadas

> [!note] 🔥
> Obs: As camadas são lógicas. Fisicamente, várias camadas podem executar na mesma máquina

- O objetivo é “retirar” as Principais Regras do Negócio do cliente e centralizá-las em um determinado ponto, o qual é chamado de Servidor de Aplicações.
- O acesso ao Banco de dados é feito através das regras contidas no Servidor de Aplicações.
- Ao centralizar as Regras do Negócio em um único ponto, fica muito mais fácil a atualização destas regras.
- O cliente não tem acesso direto ao Banco de dados, sem antes passar pelo servidor de aplicações
- A parte mais importante das regras de negócio ficam na camada intermediária. Porém ainda há algum processamento nas demais camadas:
	- Cliente:
		- Valida entrada de dados
	- Dados:
		- Validações de regras de integridade
- Camadas
	- Apresentação
		- Programa instalado no cliente
		- Alterações na Interface do programa, geram a necessidade de atualizar a aplicação em todos os computadores, onde esta está sendo utilizada.
		- Porém cabe ressaltar, que alterações na interface, são menos freqüentes do que alterações nas regras do negócio.
		- Exibe e coleta informações
	- Lógica de Negócio
		- Roda no servidor de aplicações
		- Implementa as regras de negócio do sistema
		- Facilita a manutenção da aplicação
	- Banco de dados
		- Mantém o estado da aplicação
		- Os dados somente podem ser acessados através do servidor de aplicação
- Normalmente as camadas são distribuídas, rodando em hardwares diferentes

![[Untitled 650.png]]

# Arquitetura Cliente-Servidor em 4 Camadas (Web Based)

- Surgiu com a ideia de retirar a Apresentação do cliente e centralizá-la em um Servidor Web
- Com isso o próprio Cliente deixa de existir como um programa que precisa ser instalado em cada computador da rede. 

![[Untitled 651.png]]

- As camadas eram: 
	- Cliente
		- Navegador Web
	- Apresentação
		- Servidor Web
	- Lógica
		- Regras de negócio
		- Servidor de aplicações
	- Dados
		- Banco de dados
		- Acessível somente pelo servidor de aplicações
- Fluxo:
	- Um usuário faz uma requisição por meio de um Navegador (Camada do Cliente), 
	- essa requisição é passada para um Servidor Web (Camada de Apresentação), que a processa e procura a
regra de negócio correspondente no Servidor de Aplicação (Camada de Aplicação), 
	- A camada de aplicação procura os dados no banco de dados (Camada de Dados).

# MVC

> [!tip] 💡
> À primeira vista, a Arquitetura MVC parece não ter diferença alguma em relação à Arquitetura em Três-Camadas, com o Modelo substituindo a Camada de Dados, a Visão substituindo a Camada de Apresentação e o Controlador substituindo a Camada de Lógica de Negócio. No entanto, essas duas arquiteturas são diferentes em relação a interação entre suas camadas.

> Na Arquitetura em Três-Camadas, a comunicação entre camadas é rigidamente linear, isto é, a Camada de Apresentação e a Camada de Dados só se conversam bidirecionalmente com a Camada de Lógica, mas nunca entre si. Já no MVC, a comunicação é triangular – existem diversas
> implementações diferentes dessa arquitetura, uma comunicação típica é apresentada na imagem a seguir.
> 
> 
> Observem que a Visão pode tanto gerar eventos a serem tratados pelo Controle quanto obter os dados a serem exibidos diretamente do modelo. O Controle trata os eventos da Visão, mas também pode manipular diretamente o Modelo. Finalmente, o Modelo pode reagir diretamente tanto à Visão quanto ao Controle, mas também pode gerar eventos a serem tratados pela visão
> 
> ![[Untitled 652.png]]

- Padrão arquitetural
- Divide o software em 3 partes interconectadas (camadas)
- Forma de organizar o código de forma que a manutenção fique mais fácil
- Visão
	- Classes responsáveis pela apresentação da interface gráfica
	- Responsável pela exibição do modelo
	- Existem várias visões para cada modelo
- Controladoras
	- Coordenação entre atualizações no modelo e interações com o usuário
	- Recebe requisições do usuário
	- Actions
		- Métodos responsáveis por uma página, controlando qual modelo e qual visão usar
	- Envia comandos para o modelo atualizar seu estado
	- Envia comandos para a visão alterar sua apresentação do modelo
	- Define o comportamento da aplicação
	- **Em geral, há um controlador para cada visão, porém pode existir vários controladores para cada visão**
	- O controlador é o único no sistema que conhece o responsável pela execução do método específico solicitado, neste caso a camada que contém as regras de negócios. Esta operação matemática será realizada pelo **Model** assim que ele receber um pedido do class="lf-badge">Controller.
- Modelo
	- O model é a camada que possui a lógica da aplicação. 
	- Ele é o responsável pelas regras de negócios, persistência com o banco de dados e as classes de entidades. 
	- O model recebe as requisições vindas do controller e gera respostas a partir destas requisições.
	- É no model também que as operações de CRUD devem ser realizadas.
	- Responsável por **manter o estado da aplicação**
	- Provê meio de acesso aos dados
	- Também faz **validação dos dados**
	- **Gerencia os comportamentos fundamentais da aplicação**
		- **Regras de negócio!**
	- Notifica suas visões e controladores sobre qualquer mudança em seu estado
	- Armazenam os dados manipulados pela aplicação
![[Untitled 653.png]]

# MVC vs 3 Camadas

- As camadas VIEW e CONTROLLER do MVC equivalem à camada de apresentação do modelo de 3 camadas
- A lógica de negócio no MVC encontra-se na camada MODEL, enquanto no 3 camadas encontra-se em uma camada própria
- A camada de dados do modelo de 3 camadas não tem equivalência no MVC, uma que a camada MODEL também é responsável por esta persistência e não há separação

<!-- Column 1 -->
![[Untitled 654.png]]

<!-- Column 2 -->
![[Untitled 655.png]]

# MVVM - Model - View - ViewModel

- Utilizada em aplicações Mobile
- Assemelha-se em alguns aspectos o MVC (Model View Controller) e ao MVP (Model View Presenter)
- MVVM é uma especialização do MVP adaptado
- Mantém uma espécie de façade entre o Modelo ( entenda classes de negócio, serviços externos e até mesmo acesso a banco de dados ) de objetos e a View
- a View está ligada a ViewModel através do mecanismo de binding

![[image 125.png]]

- a View através do databinding interage com a ViewModel notificando a ocorrência de eventos e o disparo de comandos.
- A ViewModel por sua vez, responde a esta notificação realizando alguma ação no modelo; seja obtendo alguma dado, atualizando ou inserindo informações no modelo.

## View

- Define a interface com o usuário
- referencia a ViewModel através da propriedade **DataContext**

## ViewModel

- Disponibiliza para a View uma lógica de apresentação
- não tem nenhum conhecimento específico sobre a view
- coordena as iterações da View com o Model, haja vista, ambos não terem conhecimento um do outro
- a ViewModel, também pode implementar a lógica de validação, para garantir a consistência dos dados.

## Model

- encapsula a lógica de negócios e os dados
- O Modelo nada mais é do que o Modelo de domínio de uma aplicação, ou seja, as classes de negócio que serão utilizadas em uma determinada aplicação.
- também contém os papéis e também a validação dos dados de acordo com o negócio
- O Modelo não referencia diretamente a View ou ViewModel.

# MVP (Model-View-Presenter)

- Evolução do MVC
- Comunica bidirecionalmente com as outras camadas
- Desacopla funções e torna a arquitetura ainda mais modular

![[Untitled 656.png]]
