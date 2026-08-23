---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2024-10-31T14:24:00
Owner:
  - Eduardo Quinalha
---
# Como uma aplicação é construída

- Primeira geração → Aplicação + BD
	- Todos os módulos em uma só aplicação
	- Monolítico
- Segunda geração → Separação Front e Back end
- Terceira geração → Microsserviços
- Escalabilidade
	- Load balancer
		- stateless
		- statefull (stick session)

# **Monolito**

- Vantagens:
	- ótimo para pequenos times
	- padronização de tecnologias (IDE, frameworks)
	- fácil obter programadores experientes no mercado
	- deploy facilitado
	- monitoramento facilitado
- Desvantagens
	- Escalabilidade → Desperdício de recursos
	- Aplicação grande → Difícil manutenção, difícil mudanças
	- Ruim para grandes times → Gerenciamento de versões, alterações, merge
	- Deploy pode parar toda a aplicação
- Decompondo a aplicação
	- Cada funcionalidade em um processo diferente
	- Ao surgir a necessidade de alterar um módulo do monolito, desenvolver este à parte

# Formas de Comunicação

- REST
- GraphQL
- webhooks
- GRPC
- Mensageria

![[Untitled 786.png]]

**Via de regra:**

- Comunicação para fora da Cloud → REST
- Comunicação interna cloud
	- Assíncrona e alta escalabilidade → Mensageria (kafka, Nats)
	- **Síncrona → gRPC**

# Evolução

- Já se trabalha com a quebra de microsserviços em entidades ainda menores, conhecido como FaaS (function as a service)
- **Define a arquitetura Servless**

# 12 Factor App

1. **Codebase: **Fonte única do código (repositório) e a partir dela sejam feitos os deploys
2. **Dependencies: **Dependências declaradas, e não embutida no classpath da aplicação
3. **Config: **Configurações de ambiente → A aplicação é única! O ambiente é quem vai definir como a aplicação vai se comportar
4. **Backing Services: **Serviços de apoio podem ser alterados sem necessidade de alteração de código
5. **Build, release, run: **Fases separadas, automatizadas
6. **Process:** Primar por serviços stateless. Se houver necessidade de guardar estado, deve-se utilizar cache
7. **Port Binding:** O serviço deve ser autocontida, exposta por meio de uma porta
8. **Concurrency: **Facilidade de escalabilidade horizontal
9. **Disposability:** A aplicação deve ter a capacidade de subir rapidamente e ser descartada rapidamente
10. **Dev/Prod parity:** Manter os ambientes o mais similar possível
11. **Logs:** Tratar os logs como um streaming de eventos (Elasticsearch - ELK)
12. **Admin process: **Processos de administração devem ser automatizados, infra as a code

# Padrões de Microsserviços

## SAGA

- Persistência poliglota

![[Untitled 787.png]]

- Contexto transacional independente para cada serviço
- Um erro no último serviço da sequência, por exemplo, deve disparar uma mensagem para os serviços anteriores desfazerem as partes da transação global que não foi corretamente concluída.

![[Untitled 788.png]]

![[Untitled 789.png]]

- O gerenciamento global é feito por um gerenciador SAGA

## CQRS

- Command Query Responsability Segregation

![[Untitled 790.png]]

- Baseia-se em eventos e filas
- Módulos:
	- Core Logic
	- Event
	- Side Effect

![[Untitled 791.png]]

- Ao invés de buscar a informação em vários bancos de dados espalhados (microsserviços), é colocado um nó responsável por escutar os eventos destes microsserviços e escrever todas as informações em um banco central, chamado de Read Model
- O CQRS também propõe dividir a aplicação em dois modelos separados: Um responsável por promover alterações nos dados e outro responsável apenas por fazer leituras.
	- Query Model → Leituras
	- Command Model → Atualizações / escrita 

## Servless Deployment / FaaS

- O serviço é quebrado em unidades menores, funções. Cada função é deployada independentemente e um serviço, por exemplo OpenFaaS se responsabiliza por gerenciar tudo na forma de uma API

## API Gateway

- Segurança
- Autorização
- Cobrança

## BFF

- Backend For Frontend
- Customização de dados para cada frontend específico
- Corresponde a diferentes API Gateways para cada tipo de frontend
- Cada respectivo gateway vai modelar as chamadas ao backend (que pode ser único) de forma a que os dados obtidos sejam adequados para cada caso, levando em consideração a quantidade de dados trafegando na rede e limitações de banda do cliente

![[Untitled 792.png]]

## Circuit Breaker

- Fail fast
- O serviço deve responder o mais rápido possível caso esteja down
- Os demais serviços podem decidir entre desfazer toda a cadeia ou manter desta forma

[[Microservices]]

[[BFF vs API gateway]]

![[20230810_231630.jpg]]

![[20231029_124039.jpg]]

# Resumo de Padrões de Arquitetura de Microsserviços

[https://javarevisited.blogspot.com/2021/09/microservices-design-patterns-principles.html](https://javarevisited.blogspot.com/2021/09/microservices-design-patterns-principles.html)

![[Untitled 793.png]]

## Princípios

- Escalabilidade
- Flexibilidade
- Autonomia e independência
- Governança descentralizada
- Resiliência
- Isolamento de falhas
- Entrega contínua por DevOps

## Padrões

### Database per Microservice

- Existe um armazenamento por microsserviço, pode ser um schema ou apenas uma tabela
- Outros serviços não têm acesso aos repositórios que não são controlados por eles
- Cada serviço tem sua necessidade particular e pode justificar a escolha de um tipo de base de dados diferente
	- SQL, No-SQL, uso de criptografia, etc.
- Vantagens
	- Facilmente escalável
	- O microsserviço encapsula o domínio de dados, o que facilita a compreensão
	- Granularidade
- Desvantagens
	- Há a necessidade de proteção contra falhas em caso de falha na comunicação
	- Necessário o uso de 2PC
	- A consistência não é imediata

### Event Sourcing

- Padrão da categoria dos “Event Driven Architectures”
- Possui uma base central que armazena todas as solicitações na forma de evento, empilhando-as
- Esta base central também serve como um “Event Broker” para outros serviços, os “Subscribers”
- Cada serviço vai ler o que lhe interessa, a partir do event log, e atualizar sua base local
- Vantagens
	- Permite efetuar um rebuild completo do estado da aplicação, a partir da re-leitura dos eventos em ordem em que ocorreram
	- Temporal Query (reconstruir o estado em qualquer ponto no tempo)
	- Event Replay - Debugging
	- Possibilidade de Snapshot
	- Auditoria
- Desvantagens
	- Consistência eventual (cada serviço vai ter um delay desde a leitura do event log até sua atualização local)

![[Untitled 794.png]]

### CQRS - Command-Query Responsibility Segregation

- Pertence à categoria “Event Driven Architecture”
- Separa responsabilidades entre serviços de escrita e serviços de consulta de dados
- É um padrão complexo, e normalmente não é recomendado para aplicações CRUD mais simples
- Normalmente utiliza-se quando há um grande desbalanceamento na quantidade de operações de escrita e leitura
- Normalmente utilizado em conjunto com outros padrões orientado a eventos, como o Event Sourcing
- Vantagens
	- Separa escrita e leitura em sistemas diferentes, possibilitando a escalabilidade independente
	- Funciona muito bem com Event Sourcing
- Desvantagem
	- Padrão muito complexo
	- Não indicado para CRUD

### SAGA

- Pertence à categoria “Event Driven Architecture”
- Provê uma maneira de comunicar dois serviços de uma forma semelhante à uma transação de banco
- Tenta aproximar o máximo possível do ACID, embora na prática o Isolamento não seja possível em microsserviços
- Faz o uso de Orquestração ou Coreografia
- Orquestração
	- Faz o uso de um elemento central que coordena as chamadas aos outros serviços, na ordem correta.
	- Também pode desfazer algumas chamadas em caso de falha.
	- Pode ser síncrono (quando aguarda o recebimento de cada resposta)
	- Ou assíncrono, quando segue atendendo novas chamadas até receber a resposta gerada pela chamada anterior
![[Untitled 795.png]]
- Coreografia
	- Baseado em eventos
	- Cada serviço será responsável por gerar eventos na sua saída
	- Os serviços correspondentes deverão assinar o recebimento dos eventos relevantes e repassar adiante
![[Untitled 796.png]]
- Vantagens
	- Pode ser utilizado para manter a consistência dos dados com baixo acoplamento
- Desvantagens
	- Alta complexidade do ponto de vista do desenvolvedor
	- Não são transações tradicionais

### Backend For Frontend (BFF)

- Define como o dado é recuperado entre servidor e cliente
- Normalmente fica sob responsabilidade do time de frontend
- Cada BFF é responsável por atender a uma única UI e ajuda a manter a simplicidade do frontend
- A principal função do BFF é atuar como uma **camada intermediária** entre o frontend e os microsserviços. Isso permite que o BFF **agregue dados de diferentes microsserviços em uma única resposta para o frontend**, evitando **múltiplas chamadas de API** diretamente a diversos serviços. Isso é especialmente útil quando o frontend precisa de informações específicas formatadas de maneira especial.
- Vantagens
	- Evita que o frontend precise manipular dados brutos recebidos diretamente dos microsserviços
	- Reduz a quantidade de chamadas de API feitas pelo frontend
	- O BFF pode cuidar de questões relacionadas à segurança, como autenticação e autorização, aliviando a carga dessas preocupações no lado do frontend.
- Desvantagens
	- Aumenta a complexidade geral da arquitetura
	- Pode haver duplicação da lógica de negócio
	- Desafios de escalabilidade

### API Gateway

- Provê um ponto de entrada único para um grupo de microsserviços
- Situa-se entre a aplicação cliente e os serviços
- Pode oferecer: proxy reverso, autenticação, SSL Termination, cache
- Vantagens
	- Esconde os microsserviços do mundo externo, diminuindo a superfície de ataque
	- Reduz a complexidade no lado do cliente, evitando que este tenha que conhecer detalhes sobre a arquitetura
	- Pode lidar com falhas parciais
![[Untitled 797.png]]
- Desvantagens
	- Ponto único de falha
	- Devido à camada adicional, aumenta a latência
	- Aumenta a complexidade da arquitetura

### Circuit Breaker

- Solução para a falha de chamadas remotas ou timeout de respostas
- Aumenta a tolerância a falha e a resiliência da arquitetura
- Para cada chamada pode ser adicionado um método de fallback, caso a operação falhe
- Implementação típica para java: **Hystrix**
- Estados:
	1. **Fechado (Closed):**
		- O circuito está inicialmente fechado, permitindo que as solicitações fluam normalmente para o componente ou serviço dependente.
	2. **Aberto (Open):**
		- Se o número de falhas ultrapassar um determinado limiar durante um intervalo de tempo definido, o circuito é aberto. Nesse estado, as solicitações não são encaminhadas para o componente dependente, evitando que o sistema sobrecarregue e degrade ainda mais.
	3. **Meio-Aberto (Half-Open):**
		- Após um período definido de inatividade (timeout), o circuito muda para o estado meio-aberto. Durante esse período, um número limitado de solicitações de teste é permitido passar para avaliar se o componente dependente está se recuperando.
- Vantagens
	- **Resiliência a Falhas: **O padrão "Circuit Breaker" melhora a resiliência do sistema, evitando que falhas em um componente se propaguem e causem danos mais amplos.
	- **Prevenção de Sobrecarga: **Ao abrir o circuito, o padrão evita que solicitações adicionais sejam encaminhadas para um componente que já está sobrecarregado ou experimentando falhas. 
	- **Recuperação Automática: **O estado meio-aberto permite que o sistema teste periodicamente a recuperação do componente dependente, facilitando a retomada das operações normais se a condição de falha temporária for resolvida.
	- **Evita Esperas Indefinidas: **Ao invés de esperar indefinidamente por uma resposta de um serviço que está falhando, o "Circuit Breaker" fornece um mecanismo para definir limites de tempo e lidar com falhas de maneira controlada.
- Desvantagens
	- Complexidade adicional
	- Configuração sensível → Pode ser difícil chegar aos valores de threshold ideais
	- Latência adicional
	- Dificuldade em lidar com falhas intermitentes

### Service Discovery

- Padrão e técnica para localizar e obter informações sobre os serviços disponíveis em um ambiente distribuído
- Ao invés de deixar os endereços dos serviços hardcoded, são utilizados nomes e estes são traduzidos dinamicamente pelo service registry
- Torna possível o escalonamento dos serviços, failover e load balancer em ambiente distribuído
- Os próprios serviços se anunciam para o service registry, que mantem uma base atualizada com os respectivos endereços
- **Principais implementações**
	- Spring Cloud → Spring Cloud Netflix Eureka
	- Kubernetes → Suporte nativo por meio do DNS interno do cluster
		- O DNS aponta para um serviço
		- Um serviço por sua vez corresponde a um ou mais pods
		- A atualização é gerenciada automaticamente pelo kubernetes
- Padrões
	- Client Side
		- Feito via DNS
		- Comunicação entre cliente e servidor diretamente
	- Server Side
		- Via Service Registry
			- Comunicação entre serviços
		- Pode utilizar um proxy entre serviços
	- Self Registration
		- Cara serviço se encarrega de se anunciar para o Service Registry quando se inicia
		- Também é responsável por notificar o service registry no processo de shut down
	- 3rd Party Registration
		- Um terceiro serviço, chamado Service Registrar, é responsável por monitorar os serviços e atualizar o Service Registry
		- Pode ser implementado por um sidecar junto à cada serviço ou por um orquestrador, como kubernetes
			- Neste caso, apenas serviços de dentro do cluster de orquestração serão automaticamente atualizados
			- Serviços externos, não são atualizados automaticamente

### API Gateway

- Componente de uma arquitetura de microsserviços
- Ponto único de entrada para as requisições
- Responsável pelo roteamento, controle, proteção e gerenciamento de tráfego
- Encaminha a requisição ao serviço apropriado de acordo com suas regras de roteamento
- Verifica autenticação e autorização, fazendo uso de JWT para isso
- Pode fazer controle de quotas, balanceamento de tráfego e verificações de segurança
- Pode realizar transformação nos dados
- **Implementações**
	- Em java, usando Spring Cloud, uma API Gateway pode ser implementada pela combinação de 2 componentes
		- Spring Netflix Eureka
			- Service Discovery + Service Registry
		- Spring Netflix Zuul
			- Gerenciamento de tráfego e segurança
	- No Kubernetes pode ser feito de duas formas
		- Ingress Controller
			- Utiliza o Nginx por padrão, mas pode utilizar outros servidores
			- As regras são definidas no Ingress Resources
		- API Gateway Dedicada
			- Ferramentas de terceiros
			- Fornece recursos avançados como roteamento avançado, autenticação, transformação de dados, monitoramento e controle de tráfego

# Servless

[https://medium.com/appvia/serverless-technology-c06060b79b25](https://medium.com/appvia/serverless-technology-c06060b79b25)

> [!note] 🔥
> **Servless = Function as a Service (FaaS)**

**É um possível tema de discursiva!!!!!**

- Refere-se à execução de código em resposta a eventos utilizando contêineres de vida curta (sob demanda)
- Eventos, neste caso, podem ser:
	- Requisições HTTP
	- Regras baseadas em tempo (CRON)
	- Mensageria
	- Webhooks
- Aplicações servless são construídas em funções, que usualmente são:
	- pacotes zip contendo código e suas dependências ou 
	- uma imagem Docker
- Na prática, são contêineres leves, invocados sob demanda
- Vantagens
	- Terceirização da complexidade
		- Livra o desenvolvedor de preocupações como montagem do container, provisionamento do ambiente, configuração de escalabilidade, etc
		- Mantém o foco na lógica de negócio
	- Desenvolvimento orientado a eventos
		- O código somente executa em resposta a eventos externos ou mensagens
		- Dispensa o uso de processos executando em background 24/7
	- Redução de custos
- Desvantagens
	- Cold Start
		- Diferença de tempo entre a requisição e seu processamento
		- Pode ser causado pelo tempo de download da imagem do container
		- Tempo de inicialização da JVM

# Outros materiais

[[What does an API Gateway do]]

[[microsservices patterns]]

[https://microservices.io/patterns/](https://microservices.io/patterns/)