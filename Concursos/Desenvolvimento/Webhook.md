---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2024-11-05T10:47:00
Owner:
  - Eduardo Quinalha
---
# Webhooks

- Outra forma de comunicação assíncrona entre aplicações (serviços)
- Webhook é uma função de callback baseada em HTTP que viabiliza a comunicação entre duas [interfaces de programação de aplicações (APIs)](https://www.redhat.com/pt-br/topics/api/what-are-application-programming-interfaces). 
- Os webhooks são usados por várias web apps para receber pequenos volumes de dados de outras aplicações e  também podem ser  usados para acionar workflows de automação em ambientes [GitOps](https://www.redhat.com/pt-br/topics/devops/what-is-gitops).
- Para configurar um webhook, o cliente oferece uma URL exclusiva para a API servidor e especifica sobre qual evento ele quer as informações. Quando o webhook estiver configurado, o cliente não precisará mais das pesquisas. O servidor enviará automaticamente o payload relevante para o URL do webhook do cliente quando o evento especificado ocorrer.
- Em geral, os webhooks são descritos como ***APIs reversas***** ou *****APIs de push*****,** porque colocam a responsabilidade da comunicação no servidor, e não no cliente
- Em geral, os webhooks são protegidos por autenticação [**Mutual Transport Layer Security (mTLS)**](/e51512d075c346d68cb1c85e1b8ad5c5)[,](/e51512d075c346d68cb1c85e1b8ad5c5) que verifica o cliente e o servidor antes do envio do payload.
- O serviço receptor disponibiliza um endpoint específico para recepção dos eventos
- O serviço remetente envia uma solicitação HTTP POST no endpoit com as informações relevantes
- **O termo “webhook” é utilizado tanto para quem envia informações/dados, quanto para quem os recebe.**
- Funções:
	- **push**: para enviar notificações em tempo real em aplicações web;
	- **pipes**: para permitir a integração entre aplicações por meio do processamento dos dados recebidos ou enviados pelo webhook;
	- **plugins**: para o desenvolvimento de plugins para adicionar funcionalidades em aplicações web, como a integração entre sistemas e o envio de notificações.