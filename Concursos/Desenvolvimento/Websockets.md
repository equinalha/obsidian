---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2024-10-15T14:46:00
Owner:
  - Eduardo Quinalha
---
WebSockets é uma tecnologia que permite a **abertura de uma conexão interativa entre o navegador do usuário (cliente) e o servidor.** Esta conexão permite uma **comunicação bidirecional em tempo real**, o que significa que **tanto o cliente quanto o servidor podem iniciar a comunicação e enviar dados a qualquer momento.** Essa característica torna os WebSockets particularmente úteis para aplicações web que requerem trocas de mensagens em tempo real, como jogos online, chats, aplicações de trading, etc.

- Permite a comunicação [bidirecional](https://pt.wikipedia.org/wiki/Bidirecional) por canais [*full-duplex*](https://pt.wikipedia.org/wiki/Full-duplex) sobre um único [s](https://pt.wikipedia.org/wiki/Soquete_de_CPU)ocket TCP
- **Depende do HTML 5**
- O schema da URL fica sendo:
	- `ws:// `ou `wss://`
		- No segundo caso, quando utilizado sobre SSL ou TLS
- Pode ser utilizado tanto em HTTP/1.1 quanto HTTP
- No entanto:
	- Em HTTP/1.1, é comum que a solicitação inicial para iniciar uma conexão WebSocket seja um **HTTP GET**.
	- Já o HTTP/2 permite que uma única conexão seja usada para várias solicitações e o método **CONNECT** é uma maneira de indicar a intenção de estabelecer uma conexão persistente com o servidor.
	- Isso implica que seja necessário ajustar as rotas e os controladores para lidar com as solicitações CONNECT em vez de GET.
- O objeto **WebSocket** possui um atributo chamado `readyState`, que indica o estado atual da conexão. Os valores possíveis para este atributo são:
	- **0** - CONNECTING: a conexão está sendo estabelecida.
	- **1** - OPEN: a conexão foi estabelecida e a comunicação é possível.
	- **2** - CLOSING: a conexão está em processo de fechamento.
	- **3** - CLOSED: a conexão foi fechada ou não pôde ser aberta.
- A comunicação WebSocket normalmente começa como uma conexão HTTP normal, mas é "atualizada" para uma conexão WebSocket através de um handshake especial. 
- Após o handshake, o protocolo muda para WebSocket, permitindo a comunicação contínua.
- O WebSocket opera sobre uma conexão TCP, que é baseada em um fluxo de bytes. 
- No entanto, o WebSocket abstrai essa comunicação em um nível mais alto, fornecendo um **fluxo de mensagens** que é encapsulado em quadros (frames). 
- Cada quadro pode conter uma mensagem completa ou uma parte dela.
- A comunicação via WebSocket **não ocorre via HTTP,** mas o processo de estabelecimento de uma conexão WebSocket **começa** com uma requisição HTTP especial:
	- O processo de conexão WebSocket inicia com um **handshake HTTP**
		- O cliente envia uma requisição HTTP ao servidor, indicando que deseja estabelecer uma conexão WebSocket. 
		- Essa requisição inclui cabeçalhos específicos como `Upgrade: websocket` e `Connection: Upgrade`, que sinalizam ao servidor que o cliente deseja "atualizar" a conexão de HTTP para WebSocket.
	- Se o servidor aceitar a solicitação, ele responderá com um código de status `101 Switching Protocols`, junto com os cabeçalhos necessários para confirmar a mudança do protocolo HTTP para o WebSocket.
	- Após o handshake bem-sucedido, a conexão deixa de ser uma conexão HTTP e se torna uma conexão WebSocket.
		- A partir deste ponto, a comunicação é feita diretamente sobre uma conexão TCP usando o protocolo WebSocket, e **não** mais via HTTP.
	- Depois que a conexão WebSocket está estabelecida, tanto o cliente quanto o servidor podem enviar mensagens a qualquer momento, sem a necessidade de uma nova requisição HTTP.
