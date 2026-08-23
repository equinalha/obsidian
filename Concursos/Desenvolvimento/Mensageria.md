---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2024-11-08T06:19:00
Owner:
  - Eduardo Quinalha
---
# Mensageria

## Message Broker

- Possibilita a troca de informações (mensagens) entre aplicações
- Middleware de sistema de mensagens
- Podem validar, armazenar, rotear e entregar mensagens aos destinos apropriados.
- Permite que os remetentes emitam mensagens sem saber onde estão os destinatários, se eles estão ativos ou não ou quantos deles existem.
- Facilita o desacoplamento de processos e serviços dentro de sistemas.
- Contam com uma subestrutura ou componente chamado de [fila de mensagens,](https://www.ibm.com/br-pt/topics/message-queues)  que armazena e ordena as mensagens até que os aplicativos de consumo possam processá-las.
- As mensagens são armazenadas na ordem exata em que foram transmitidas e permanecem na fila até que o recebimento seja confirmado.
- Comunicação Síncrona
	- SOAP
	- REST
	- GraphQL
- Comunicação Assíncrona
	- Mensageria
	- Garante que as mensagens serão entregues uma vez (apenas uma) e na ordem correta em relação a outras mensagens.

## Message Broker vs ESB

Um [barramento de serviço corporativo (ESB) ](https://www.ibm.com/br-pt/topics/esb) é um padrão arquitetônico utilizado algumas vezes em [arquiteturas orientadas por serviços (SOAs)](https://www.ibm.com/br-pt/topics/soa) implementadas em empresas. Em um ESB, uma plataforma de software centralizada combina protocolos de comunicação e formatos de dados em uma "linguagem comum" que todos os serviços e aplicativos na arquitetura possam compartilhar. Ele pode, por exemplo, converter as solicitações que recebe de um protocolo (como XML) para outro (como JSON). Os ESBs transformam suas cargas úteis de mensagens usando um processo automatizado. A plataforma centralizada de software também trata de outra lógica de orquestração, como conectividade, roteamento e processamento de solicitações.

Os message brokers são uma alternativa "leve" aos ESBs, pois fornecem uma funcionalidade semelhante: um mecanismo para comunicações entre serviços, só que mais simples e barato. Eles são adequados para uso nas arquiteturas de microsserviços que se tornaram mais comuns à medida que os ESBs caíram em desuso.

## Tipos de canais / Tipos de Message Brokers

- **Queue / Point to Point**
	- Padrão utilizado em filas de mensagens com relacionamento 1:1
	- Favorece a escalabilidade
	- **Cada mensagem na fila é enviada somente a um destinatário e é usada somente uma vez.**
	- Existem ferramentas que monitoram o broker e quando detectarem que ele está sobrecarregado
	- Na ocorrência de sobrecarga do broker, novos consumidores são instanciados
	- Exemplos de casos de uso adequados para esse estilo de sistema de mensagens incluem folha de pagamento e processamento de transações financeiras.
- **Topic / Publish and Subscriber**
	- Utilizado em relacionamentos 1:N
	- As mensagens são publicadas e armazenadas
	- **O Broker envia todas as mensagens a todos os subscribers**
	- A mesma mensagem é enviada a todos os destinatários
	- Por exemplo, compra finalizada
		- Notificar estoque, financeiro, logística, etc…
	- O broker é responsável por notificar todos os consumers
	- Durable Subscriber
		- Quando é necessário que a mensagem seja persistida mesmo quando o subscriber esteja fora do ar
- **Transferência de Arquivos:**
	- A transferência de arquivos é um modo de operação que envolve o envio de arquivos inteiros entre sistemas, em vez de mensagens individuais.
	- É útil quando você precisa transmitir dados em lotes, como arquivos de log, imagens, documentos ou qualquer outro tipo de arquivo.
	- Essa modalidade pode ser implementada em sistemas de mensageria para transferir arquivos de forma confiável e eficiente.

## Modelos de Entrega

- Persistente
- Cliente Durável

## Vantagens

- Garantia de entrega
- Autenticação / Autorização
- Tolerância a falhas
- Fácil escalabilidade

## Desvantagens

- Modelo de desenvolvimento mais complexo
	- Modelo event driven com diversos event handlers
- Garantir a ordem de entrega das mensagens
- Overhead de comunicação, especialmente para grandes volumes de dados
- Vendor lockin, com muitos protocolos proprietarios

## Domain Events / Eventos Negociais

[https://fullcycle.com.br/principais-conceitos-sobre-domain-events/](https://fullcycle.com.br/principais-conceitos-sobre-domain-events/)

- O Domain Events é uma abordagem de Domain Driven Design cuja função é estabelecer **quais são os eventos importantes que acontecem no coração do software e como podemos distribuí-los.**
- *Use um evento de domínio para capturar uma ocorrência de algo que aconteceu no domínio*
- *A essência de um Evento de Domínio é que você o usa para capturar coisas que podem desencadear uma mudança no estado do aplicativo que você está desenvolvendo. Esses objetos de evento são então processados para causar alterações no sistema e armazenados para fornecer um Audit Log*
- Eventos significativos do ponto de vista de negócio e que sinalizam ações a serem tomadas por um ou mais consumers
- Decorrem de uma ação ou mudança de estado dentro do sistema
- Desencadeiam ações em microsserviços relacionados
- São representados por mensagens estruturadas contendo dados relevantes ao evento
- Ajudam a criar uma arquitetura orientada a eventos
- Quando utilizar?
	- Quando é desejado notificar outros Bounded Contexts de uma mudança de estado
- Componentes
	- Event
		- O evento representa o que aconteceu, mostrando os dados, data e hora. Ele também pode ter um ID, que é o identificador, dependendo do que você decidir colocar e achar razoável ter em determinado evento.
	- Handler → Executa o processamento quando um evento é chamado
		- O handler executa o que foi declarado no evento. Pode ser um User Created, um Email Sent ou mesmo um outro handler de User Created que publica uma mensagem no RabbitMQ.
	- Event Dispatcher → Armazena e executa os handler de um evento quando ele for disparado
		- Esse componente armazena todos os eventos junto aos handlers executados. Você pode registrar um evento de User Created junto ao handler de envio de e-mail, assim como um outro evento de User Created para publicar no RabbitMQ. Basicamente o Event Dispatcher lista todos os eventos junto aos handlers executados.

## Principais Brokers

### JMS

- Implementado pelos application servers
- Componentes
	- JMS Context
	- JMS Producer
	- JMS Consumer
- Mensagem JMS
![[image 108.png]]
	- Cabeçalho
		- Metadados da mensagem
		- Principais campos
			- Expiração
			- Persistência
	- Propriedades
		- Metadados adicionais
		- Algumas são pré-definidas, mas também é possível criar propriedades customizadas
	- Body
		- Mensagem
		- Tipos
			- TextMessage
				- String de texto
				- XML, JSON
			- MapMessage
				- Chave - Valor
			- BytesMessage
				- Binário
			- StreamMessage
				- Stream de valores primitivos Java
			- ObjectMessage
				- Objeto java serializável
			- Message
				- Campo vazio, sem valores

### Active MQ

- Baseado em POJO
- Cada servidor conta com um journal próprio, usado para persistência das mensagens
- Possui 3 API’s Client Side
	- API Central
	- JMS 2.0
	- Jakarta Messaging 3.0
- Agnóstico quanto a protocolos. Suporta:
	- AMQP
	- OpenWire
	- MQTT
	- STOMP
	- HornetQ
	- Core (Active MQ)
- O broker pode ser implementado das seguintes formas:
	- Standalone
		- Processo independente
		- Ambiente independente
	- Embedded
		- Incorporado a uma aplicação java
	- Integrado ao Jakarta EE

### NATS

- Dividido em NATS server
	- Broker
- NATS streaming
	- Garantia de entrega
	- Persistência das mensagens
- Pode trabalhar em somente uma instância (SPOF) ou em cluster
- Modos de entrega
	- at most ONCE
	- at least ONCE
- Mensagem NATS

![[image 109.png]]

- Por padrão as mensagens NATS são configuradas para um tamanho máximo de 1MB
	- É possível ampliar para até 64MB
	- Parâmetro `max_payload`

### Apache Kafka

- Maior desempenho (rápido)
- Trabalha com streaming de eventos
- Introduz o componente chamado Zookeeper, um nó de monitoramento do cluster kafka
- Os tópicos são divididos em partições que podem ser distribuídas entre os nós
- As mensagens são distribuídas de forma randomica
- Utiliza um protocolo próprio
- Conceitos importantes sobre o Kafka
	- **Dados são permanentes por padrão**
		- O tempo de armazenamento e política de descarte deverá ser parametrizado pelo desenvolvedor
	- **Eventos são imutáveis após publicação**

### RabbitMQ

- Broker poliglota
	- Entende diversos protocolos ex: JMS, MQTT

## Protocolos

### AMQP

- Advanced Message Queuing Protocol
- Padrão aberto para troca de informações
- Define o formato dos dados
- Binário

### MQTT

- Message Queue Telemetry Transport
- Protocolo leve para ambientes de alta latência
- publisher subscriber

### XMPP

- Extensible Message and Presence Protocol
- Baseado em XML
- Real Time
- Ideal para video, chats

### STOMP

- Simples
- Baseado em texto
- Bidirecional
- Na prática é um wrapper em cima do websocket

# RabbitMQ

<!-- Column 1 -->
[https://fullcycle.com.br/como-funciona-o-rabbitmq/](https://fullcycle.com.br/como-funciona-o-rabbitmq/)

<!-- Column 2 -->
[https://tryrabbitmq.com/](https://tryrabbitmq.com/)

## Características

- OpenSource
- Trabalha por padrão com o protocolo AMQP mas pode trabalhar com diversos outros, por exemplo MQTT
- Pode trabalhar com canais ponto a ponto, topicos ou grupos
- Usa filas do tipo FIFO
- Mensagens podem ou não ser persistentes
- Roda na porta padrão 5672
- Suporta QoS
	- Mensagens possuem um campo TTL
	- Mensagens podem ter uma prioridade associada
- Conceitos
	- Producer → Sistema que origina a mensagem
	- Routing Key → Campo da mensagem usado para especificar a regra de entrega desta
	- Binding Key → Regra de ativação para uma fila específica
	- Consumer → Aplicação que vai consumir as mensagens armazenadas na fila. Cada consumer tem sua própria fila
	- Bind → Relação entre uma fila e uma exchange
![[Untitled 437.png]]

## Exchangers

- Componente do RabbitMQ responsável por receber a mensagem do producer e distribuí-la a uma ou mais filas. Existem 4 tipos de Exchangers:
	- **Direct**
		- Entrega a mensagem a uma única fila, de acordo com o que foi especificado no campo `rounting Key `da mensagem
		- Se múltiplas filas possuírem a mesma `routing key`, as mensagens serão entregues a todas elas
![[image 110.png]]

	- **FanOut**
		- Entrega a todas as filas, **independente do que for especificado em** `routing Key`
		- O campo `routing key` é ignorado
		- Ideal para **broadcast **de mensagens
![[image 111.png]]
	- **Topic**
		- Pode entregar a 0, 1 ou N filas, de acordo com a regra que for especificada em `routing Key`. 
		- Para isso, faz uso de curingas
		- Ideal para **multicast**
	- **Header**
		- Mensagens são roteadas com base em cabeçalhos da mensagem
		- Possibilita o roteamento baseado em múltiplos atributos
		- O campo `routing key` é ignorado
		- Um campo especial `x-match` é utilizado para definição de regras de roteamento: `any`, `all`, `all-with-x`,` any-with-x`
- O **exchanger default** do RabbitMQ é do tipo **Direct **e é criada por padrão pelo broker
- Ele não possui nome (é uma string vazia)
- Quando uma nova fila é criada ela é automaticamente vinculada (bind) com o exchanger default com uma routing key que corresponde ao** nome da fila**
- Não é permitido operações de bind/unbind manualmente com o exchanger default

## Queues

- Trata-se de uma estrutura de dados para armazenamento das mensagens
- Propriedades
	- `name`
	- `durable`
	- `exclusive`
		- Significa que será utilizada apenas para uma conexão e, quando esta terminar, será excluída
	- `auto-delete`
		- Automaticamente excluída quando ocorrer o `unsubscribe `do último assinante
	- `arguments`
		- Opcional
		- Usado por plugins
- Uma fila deve ser declarada antes de poder ser utilizada
- Caso não exista, será criada
- Se existir com as mesmas propriedades, a nova declaração não terá efeito
- Se os argumentos forem diferentes dos da atual fila, ocorrerá uma exceção

## Bindings

- Regras usadas pelos exchangers para rotear as mensagens para as filas de destino
- Se a regra especificada não corresponder a nenhuma fila, a mensagem pode ser **dropada** ou **retornada ao publicador**, dependendo dos atributos desta mensagem

## Consumers

- As mensagens podem ser entregues de duas formas
	- O consumidor faz um `subscribe `e então a `push AP`I fará a entrega ao consumidor
	- `Polling`, o consumidor consulta de tempos em tempos a fila para recuperar a mensagem
		- Este modo não é recomendado por ser mais ineficiente
- É possível configurar confirmação de leitura para que haja garantia de entrega das mensagens

## Transmissão das mensagens

- Padrão via AMQP (Porta 5672)
- Pode ser adaptado para uso com outros protocolos
	- STOMP (Simple Text Oriented Messaging Protocol)
		- Envio de mensagens via Websockt ou HTTP
		- API Javascript
	- MQTT
		- Largura de banda limitada
		- API em Javascript
		- Utilizado em IoT
	- Plugins de gerenciamento AMQP

## RabbitMQ no Java

- Dependência

```xml
<dependency>
    <groupId>com.rabbitmq</groupId>
    <artifactId>amqp-client</artifactId>
    <version>5.18.0</version>
</dependency>
```

- Sender

```java
// Sender - Criando uma conexão com o servidor
ConnectionFactory factory = new ConnectionFactory();
factory.setHost("localhost");
try (Connection connection = factory.newConnection();
     Channel channel = connection.createChannel()) {

}

// Enviando uma mensagem
channel.queueDeclare(QUEUE_NAME, false, false, false, null);
String message = "Hello World!";
channel.basicPublish("", QUEUE_NAME, null, message.getBytes()); // As mensagens são tratadas com o um array de bytes
System.out.println(" [x] Sent '" + message + "'");


```

- Consumer

```java
public class Recv {

  private final static String QUEUE_NAME = "hello";

  public static void main(String[] argv) throws Exception {
    ConnectionFactory factory = new ConnectionFactory();
    factory.setHost("localhost");
    Connection connection = factory.newConnection();
    Channel channel = connection.createChannel();

    channel.queueDeclare(QUEUE_NAME, false, false, false, null);
    System.out.println(" [*] Waiting for messages. To exit press CTRL+C");

		DeliverCallback deliverCallback = (consumerTag, delivery) -> {
		    String message = new String(delivery.getBody(), StandardCharsets.UTF_8);
		    System.out.println(" [x] Received '" + message + "'");
		};
		channel.basicConsume(QUEUE_NAME, true, deliverCallback, consumerTag -> { });

  }
}
```

# Recursos

- Pode utilizar diversos mecanismos de autorização e autenticação. Por padrão, ele vem com suporte a:
	- LDAP
	- HTTP
	- Outros podem ser adicionados via plugins
- Suporta criptografia das mensagens
	- TLS
- Pode rodar em ambiente de nuvem
- Suporta diferentes mecanismos de persistência
- Suporta federação, permitindo a comunicação entre múltiplos brokers distribuídos geograficamente
