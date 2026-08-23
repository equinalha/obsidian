---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2024-11-04T08:05:00
Owner:
  - Eduardo Quinalha
---
# Conceitos

- URI
	- URI = URL + URN
	- URI = protocolo + URL (domínio) + URN (Nome do recurso: /pagina/endpoint)
- URL
	- Local, nome do domínio + path completo
	- Vai desde o protocolo até o final do path
- URN
	- Recurso que será acessado dentro da URL 
	- Vai desde o primeiro subdomínio até o final dos parâmetros (queries)
	- Não abrange os fragmentos
- Codificação: ASCII
- Stateless

![[Untitled 444.png]]

![[Untitled 445.png]]

# Versões

## **HTTP/1**

- Não faz persistência de sessão
- Cada chamada faz uma nova conexão TCP

![[Untitled 446.png]]

## **HTTP/1.1**

- Trabalha com conexão persistente
- Em uma conexão, várias chamadas podem ser feitas
- Normalmente navegadores abrem múltiplas conexões por servidor, a fim de paralelizar o carregamento da página

## **HTTP/2.0**

- Uma única conexão TCP persistente
- Requisições paralelas
![[Untitled 447.png]]
- Enquadramento binário
	- A requisição é quebrada em frames, sendo:
		- HEADERS frame
		- DATA frame

![[Untitled 448.png]]

- Priorização de requisições
- Server push
	- O servidor pode enviar múltiplas respostas ao cliente a partir de uma única requisição
- Compressão automática
	- Cabeçalho: HPACK
	- Dados: GZIP

# Estrutura das mensagens

## Requisição (3 partes)

1. Linha de requisição: Método + caminho + versão do protocolo
2. Cabeçalho
	1. **Generic Headers: **Usado em todos os tipos de requisições
	2. **Request Headers:** Informações sobre o recurso desejado + informações do cliente
	3. **Entity Headers**: vazio
3. Corpo da entidade: Body (normalmente utilizado com o método POST)

![[HTTP-HTTPS synced block]]

### Cabeçalhos

- End-to-end: Cabeçalhos para o destinatário final (servidor ou cliente). Proxies intermediários devem repassá-los sem alterações e caches devem armazená-los
- Hop-by-hop: Válidos apenas para uma única conexão. Estes cabeçalhos são redefinidos a cada salto.

## Resposta

4. Status line
5. Cabeçalho
	1. **Generic Headers: **Usado em todos os tipos de requisições
	2. **Response Headers:** Informações sobre o servidor
	3. **Entity Headers**: Conteúdo da entidade, tamanho e MIME-type
6. Corpo da entidade: Body - Conteúdo da resposta da requisição

![[HTTP-HTTPS synced block 1]]

# Métodos

- GET: Solicitação de leitura
- PUT: Alteração de dados. Pode ser utilizado para enviar arquivos de configuração, páginas.
- POST: Envio de informações prévias, antes da resposta.
- HEAD: Leitura apenas do cabeçalho de objeto ou página web. Mesma solicitação do GET, mas sem body. Pode ser utilizado para obter a última atualização de uma página
- DELETE
- OPTIONS: Utilizado para comunicação com servidores proxy, permite criação de um túnel até o alvo
- TRACE: Utilizado para testes, depuração. Envia de volta a solicitação. LOOPBACK
- CONNECT: Similar ao OPTIONS
- PATCH: Alteração de dados parcial

## Classificação

- Idempotente
	- GET, HEAD, PUT, DELETE
	- A repetição de requisições idênticas, não altera o estado do backend
- Não idempotentes
	- Gera novos registros para cada interação
	- A repetição de requisições idênticas, altera toda a vez o estado do backend

# Cache e Proxy

- Proxy Reverso:
	- Busca proteger o servidor de destino
	- Balanceamento de carga
	- Armazenamento em cache de conteúdo estático

# HTTPS

> [!tip] 💡
> Os protocolos SSL e TLS funcionam em uma camada intermediária entre a camada de transporte e de aplicação, na pilha TCP/IP
Ou seja, estes protocolos não servem apenas para o HTTP(S), mas sim, para qualquer protocolo da camada de aplicação

- SSL/TLS
	- Túnel seguro para a comunicação
	- **Confidencialidade** (dados criptografados)
	- **Autenticidade** (tanto do servidor quanto do cliente)
		- Versão simples → Autentica apenas o servidor
		- Versão mútua → Autentica as duas partes
	- **Integridade** → Hash

# HTTP Novas versões

## HTTP 2.0

- Compactação e criptografia dos dados e cabeçalho HTTP
- **Protocolo binário ao invés de texto**
- Multiplexação de solicitações na mesma conexão TCP, com cabeçalhos comprimidos
	- A contrapartida da multiplexação é que se houver perda de pacote TCP, vários recursos são afetados simultaneamente (ver a evolução deste ponto no HTTP 3.0)

![[Untitled 451.png]]

- Suporte aos recursos das versões antigas
- Priorização de requests
- Server-PUSH
	- Capacidade preditiva de ação
	- Baseado em padrões de acesso, antecipa ações independente de requisição
- TLS 1.2 mas suporta o 1.3
- Compressão automática
	- Nas versões anteriores GZIP
	- Versão atual HPACK com compressão obrigatória (Compressão dos HEADERS)

## HTTP 3.0

- Utiliza QUIC ao invés do TCP puro. O QUIC é um protocolo intermediário entre a camada de aplicação e de transporte
	- Incorpora o TLS e parte da camada de transporte

![[Untitled 452.png]]

- Protocolo multiplexado de transporte sobre UDP
- Acelerou comunicação segura com o TLS
- Implementa detecção de perda e retransmissão para cada fluxo e isola os processos de recuperação
	- Isto resolve o problema causado pela multiplexação no HTTP 2.0, quando da perda de pacotes TCP

# Cookies

> [!tip] 💡
> **Cookies Secure e HttpOnly**
> Um cookie seguro só é enviado ao servidor com uma requisição criptografada sobre um protocolo HTTPS. Mesmo com a diretiva **Secure**, informações confidenciais nunca devem ser guardadas em cookies, pois são intrinsecamente inseguros e esta diretiva não oferece proteção real. Iniciando com o Chrome 52 e o Firefox 52, sites inseguros (http:) não podem mais configurar cookies com a diretiva **Secure**.
> 
> Para se prevenir de ataques cross-site scripting (XSS), os cookies **HttpOnly** são inacessíveis para a API JavaScript Document.cookie; eles são enviados só para o servidor. Por exemplo, cookies que persistem sessões de servidor não precisam estar disponíveis para o JavaScript, e portanto a diretiva **HttpOnly** deve ser configurada.
> 
> **Fonte:** https://developer.mozilla.org/pt-BR/docs/Web/HTTP/Cookies#cookies_secure_e_httponly
> 
> Resumindo: Não existe **HttpsOnly**

![[20230811_063735.jpg]]