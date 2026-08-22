---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2024-10-31T14:34:00
Owner:
  - Eduardo Quinalha
---
[Apostila Webservices - Direção Concursos](https://free-content.direcaoconcursos.com.br/demo/curso-8189.pdf)

# Definições

- Webservices visam a integração entre sistemas heterogêneos
- **Baseados em XML**
- Utilizam protocolo aberto
- Autocontidos

# Participantes

- Service provider
- Service requester
- Service broker
	- Qualquer aplicação que faça a intermediação entre o provedor e o solicitante

# Características

- Autocontidos: Não dependem de outros componentes para sua própria existência
- Autodescritivos: Não necessitam de informações externas para expor suas funcionalidades
- Utilizam protocolos abertos
- Fracamente acoplados
- Independentes de tecnologia

# Abordagens

- Service First / Code First
	- Inicia pela codificação do serviço
	- O contrato (WSDL) é gerado automaticamente
	- Qualquer mudança na implementação poderá mudar o WSDL, afetando todos os clientes do webservice
- Contract First
	- Inicia pela escrita do contrato (WSDL)
	- As interfaces são geradas a partir deste

# Paradigma SOAP

- SOAP
	- Baseado em XML
	- Troca estruturada de dados entre Web Services
- WSDL
	- Baseado em XML
	- Define a representação da interface dos Web Services
- UDDI
	- Baseado em XML
	- Padrão de descobrimento
	- Define como as informações podem ser organizadas

Com o tempo foram surgindo lacunas que demandaram diversas extensões ao paradigma SOAP, dentre eles:

- Criptografia
- Assinatura digital
- autorização
- conversação
- federação
- políticas de segurança e privacidade

Este conjunto de extensões ficou conhecido como **WS-Security**

Outros conjuntos como:

- processos de negócio
- mensageria
- especificação de metadados
- especificação de recursos
- especificação de gerenciamento
- interoperabilidade
- transações

Ficaram conhecidos como **WS-***

# Definições

- WSDL
	- Protocolo baseado em XML para troca de informação entre aplicações em ambientes distribuídos
	- **Descreve** como acessar um Web Service e quais operações ele disponibiliza
	- Especifica três principais aspectos:
		- O que o serviço faz
		- Como Acessar o Serviço
		- Onde está localizado o serviço
	- Descreve a interface
	- É parte do UDDI (Universal Description, Discovery and Integration)
	- É a linguagem utilizada pelo UDDI
	- Uma aplicação cliente lê o WSDL para determinar as funções disponíveis pelo serviço
	- A aplicação então encapsula a mensagem em um SOAP para chamar o método descoberto pelo WSDL
![[Untitled 780.png]]
	- Possui duas perspectivas
		- Abstrata:
			- Trata da interface do serviço
			- Descreve o que ele faz, parâmetros de entrada, saídas, mensagens de falha, etc.
		- Concreta:
			- Descreve como é feito
			- Protocolos, codificação, portas, endereço de rede, etc.
		- Desta forma, pode-se alterar a implementação (concreta) sem afetar a interface (abstrata)
![[Untitled 781.png]]
![[Untitled 782.png]]
	- Service
		- Corresponde à classe anotada por `@WebService`
		- Normalmente é adicionado `Service` ao nome da classe
	- Port
		- Associado ao Service
		- Cada service tem uma Port
	- Binding
		- Informações sobre como aquele método é acessado, protocolo (ex: http)
	- Operations
		- Métodos da classe anotada com `@WebService`
		- Cada método será uma operation
		- Um conjunto de operations compõem uma Port
	- Input Message / Output Message
		- Correspondem aos parâmetros de entrada do método e o retorno deste
	- Types
		- Correspondem aos tipos de dados enviados nas mensagens input Message e Output Message
- UDDI
	- Serviço de diretório, baseado em XML, em que é possível registrar e localizar Web Services
	- É um repositório de interfaces de Web Services descritas por WSDL.
	- O UDDI é uma especificação técnica, ou protocolo e um serviço de diretório onde empresas podem registrar, publicar, descrever, buscar,
descobrir e integrar serviços web.
	- Faz metáfora com Lista telefônica. É dividido em **Páginas Brancas**, **Páginas Verdes **ou **Páginas Amarelas**
- SOAP
	- Formato da mensagem
	- Marshalling / demarshalling
		- Processo de encapsulamento de dados em uma mensagem SOAP
- JAX-WS
	- Tecnologia presente dentro do Java EE para implementação de Web Services utilizando XML
	- Utiliza-se do WSDL e mensagens SOAP

# SOAP

- SOAP (Simple/Single object access protocol)
	- Baseado em XML
	- Define uma organização para troca estruturada de dados entre webservices
	- WSDL
		- Define a estrutura da mensagem SOAP para a aplicação
	- **Elementos:**
		- Envelope (obrigatório)
			- Elemento raiz do XML. Identifica a mensagem como SOAP
		- Cabeçalho (Opcional)
			- Carrega informações específicas para a aplicação
			- Torna possível adicionar mais funcionalidades
		- Corpo (Obrigatório)
			- Aqui seguem as informações propriamente ditas
			- Obrigatório tanto na requisição quanto na resposta
		- Falha (opcional)
			- Em caso de falha, detalha o erro
```xml
<!-- Requisição -->
POST /InStock HTTP/1.1
Host: www.dre.ufrj.br
Content-Type: application/soap+xml; charset=utf-8
Content-Length: nnn

<?xml version="1.0"?>
<soap:Envelope xmlns:soap="http://www.w3.org/2001/12/soap- envelope"
soap:encodingStyle="http://www.w3.org/2001/12/soap-encoding" xmlns:tiposns="http://www.w3.org/2001/XMLSchema">
	 <soap:Header>
		 <m:autenticacao xmlns:m="http://www.dre.ufrj.br/ws/dre">21423edf69fgs</m:autenticacao>
	 </soap:Header>
	 <soap:Body>
		 <m:retornaNome xmlns:m="http://www.dre.ufrj.br/ws/dre">
			 <numdre type="tiposns:int">123.456.789-00</drenum>
		 </m:retornaNome>
	 </soap:Body>
</soap:Envelope>

<!-- Resposta -->
HTTP/1.1 200 OK
Content-Type: application/soap+xml; charset=utf-8
Content-Length: nnn

<?xml version="1.0"?>
<soap:Envelope xmlns:soap="http://www.w3.org/2001/12/soap- envelope"
soap:encodingStyle="http://www.w3.org/2001/12/soap-encoding" xmlns:tiposns="http://www.w3.org/2001/XMLSchema">
	 <soap:Header>
		 <m:atenticacao xmlns:m="http://www.dre.ufrj.br/ws/dre">2kg469fgs</m:atenticacao>
	 </soap:Header>
	 <soap:Body>
		 <m:retornaNomeResponse xmlns:m="http://www.dre.ufrj.br/ws/dre">
			 <nome type="tiposns:string">João da Silva</nome>
		 </m:retornaNomeResponse>
		 <soap:Fault>
		 </soap:Fault>
	 </soap:Body>
</soap:Envelope>
```
![[Untitled 783.png]]

![[Untitled 784.png]]

## Nós SOAP

- Os nós SOAP agem como pontos no fluxo onde o processamento do serviço da web está configurado e aplicado. 
- As propriedades dos nós SOAP controlam o processamento realizado e podem ser configuradas pelo fornecimento de uma definição WSDL ou configurando manualmente propriedades, ou ambos.
- **implementa um provedor de serviço da web.**
- O nó SOAPInput atende a solicitações de serviços web recebidas, e o SOAPReply envia respostas de volta para o cliente;

## WSDL

- O elemento raiz em WSDL 2.0 é** **`**<description> **`em vez de `<definitions>`, como na versão 1.1
- `Interface`: Este elemento, que substitui o portType de WSDL 1.1, define um conjunto de operações suportadas. Cada operação tem um nome e está associada a um ou mais
elementos de mensagem.
- `Operation`: define uma operação que pode ser realizada, bem como o formato da mensagem de entrada e saída
	- `one-way`: A operação pode receber uma mensagem, mas não retornará resposta
	- `request-response`: Recebe a requisição e retorna resposta
	- `solicit-response`: A operação envia uma requisição e espera pela resposta
	- `notification`: A operação envia uma mensagem mas não aguarda uma resposta
![[image 131.png]]

## SEI - Service Endpoint Interface

- Classe responsável por converter objetos e data types java para uma mensagem SOAP
- Parte do JAX-WS

## Consumindo um webservice SOAP no Java

- Existe um utilitário CLI que vem junto com o java: wsimport
- Este utilitário está disponível no Java SE
- `wsimport <WSDL URI>`
- Este utilitário vai gerar as classes para interagir com o webservice desejado. Basta importá-las para o projeto desejado

## Criando um webservice SOAP no Java

- Basta anotar a classe com`@WebService`
- O Jax-ws irá assumir que qualquer método público desta classe será um método do webservice
- O WSDL será criado automaticamente, disponibilizado em um endpoint para consulta

# REST (Representational State Trasfer)

> [!note] 🔥
> **REST não é protocolo!** É um estilo arquitetônico

[https://www.brunobrito.net.br/api-restful-boas-praticas/](https://www.brunobrito.net.br/api-restful-boas-praticas/)

- Conceitos
	- Idempotente
		- Chamadas idênticas vão retornar respostas iguais
		- Não promovem nenhuma alteração no estado
	- Safe
		- Métodos Read-Only
		- Não alteram o estado
- Paradigma de troca de dados mais leve e mais simples que SOAP, que visava principalmente conexões de baixa velocidade (smartphones)
- Usa HTTP puro
- Menos burocrático que SOAP
- Enquanto SOAP suporta apenas XML, REST suporta:
	- Html
	- xml
	- Json
	- Yaml
	- TXT
	- etc.
- Feito para ser escalável
- **STATELESS**
	- Informações de estado devem ficar no cliente
	- Toda chamada deve incluir todos os dados necessários para que o servidor possa executá-la corretamente
	- Cada chamada é independente
- Camadas podem ser incluídas facilmente entre cliente e servidor
	- gateways
	- firewalls
	- proxies
	- load balancers
- Pode ser cacheado
- **Principais verbos HTTP utilizados**
	- GET
	- POST
	- PUT
	- DELETE
	- TRACE
		- Faz um loopback da solicitação
		- Útil para depuração
	- OPTIONS
		- Usado para descrever as opções de comunicação como recurso
	- HEAD
		- Igual ao GET, no entanto não retorna o corpo da resposta, apenas seu cabeçalho
- **Principais códigos de status**
	- 2XX - SUCESSO
		- 200 - OK
		- 201 - Criado
		- 202 - Aceito → Confirma que a solicitação foi recebida, mas o recurso poderá ou não ser tratado, dependendo de processamento posterior
		- 204 - Nenhum conteúdo → A solicitação foi processada, mas não há nenhuma resposta para ser enviada
		- 206 - Conteúdo parcial
	- 3XX - REDIRECT
		- 300 - Múltipla escolha → Utilizado para desambiguação da solicitação
		- 301 - Movido → Esta e todas as solicitação deverão ser redirecionadas a outra URL
		- 307 - Redirecionamento Temporário
		- 308 - Redirecionamento Permanente
	- 4XX - CLIENT ERROR
		- 400 - Requisição Inválida - Erro de sintaxe
		- 401 - Não Autorizado
			- O uso de autenticação é possível, porém não foi fornecido
			- A resposta deve incluir um cabeçalho www-authenticate
		- 403 - Proibido
			- O pedido é reconhecido, porém não autorizado
			- Independente de fornecimento de credenciais de autenticação
		- 404 - Not Found
		- 405 - Método não permitido
		- 408 - Timeout
			- Timeout do cliente
			- Este deveria ter enviado uma solicitação qualquer dentro de um tempo estabelecido
		- 409 - CONFLICT
			- Pedido não processado devido a um conflito
			- Por exemplo, conflito de edição
		- 410 - Gone
			- O recurso existia, porém foi removido e não voltará a existir
	- 5XX - SERVER ERROR
		- 500 - Internal Server Error
		- 501 - Não implementado
			- A funcionalidade não é suportada
		- 502 - Bad Gateway
		- 503 - Serviço indisponível
		- 504 - Gateway Timeout
		- 505 - Versão do HTTP não suportada
- Principais códigos de URL
	- %20 → Espaço
	- %24 → $
	- %25 → %
	- %26 → &
	- %2F → /

## HATEOAS

- Componente da arquitetura REST
- Permite que clientes consumam a API sem conhecimento prévio
- Significa Hypermedia As the Engine Of Application State
- Ao ser implementado passa a fornecer links que indicarão aos clientes como navegar pelos recursos
- Facilita a implementação do cliente, uma vez que este não precisa avaliar o estado da entidade
- O próprio backend vai fornecer os links com as ações disponíveis

# Materiais

[https://blog.postman.com/soap-vs-rest/?s=09](https://blog.postman.com/soap-vs-rest/?s=09)

![[20230306_123830.jpg]]