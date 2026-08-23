---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2025-04-29T14:41:00
Owner:
  - Eduardo Quinalha
---
# Características

- Biblioteca para transferência de dados usando vários protocolos de rede, como HTTP, HTTPS, FTP, SFTP, SMTP, POP3, …
- Usada para consumir API e transferir arquivos de forma automatizada
- Permite realizar operações de rede como `HTTP GET` ou `POST`
- Permite fazer upload ou download de arquivos, e enviar e-mails
- Oferece suporte integrado para HTTPS e SSL/TLS, garantindo conexões seguras.

# API´s

- A libcurl é composta por API´s
- `curl_easy`
	- Easy Interface
	- API mais utilizada
	- Opera de forma síncrona
```c
CURL *curl;
CURLcode res;

curl = curl_easy_init();
if(curl) {
    curl_easy_setopt(curl, CURLOPT_URL, "https://example.com");
    res = curl_easy_perform(curl);
    curl_easy_cleanup(curl);
}
```
- `curl_multi`
	- Permite múltiplas transferências simultaneamente, de forma não bloqueante (assíncrona)
	- Baseado em um loop que verifica o estado das transferências
- `curl_share`
	- Permite compartilhar dados entre múltiplas sessões easy, como cache de conexões ou cookies
	- Útil quando várias conexões independentes precisam compartilhar dados
- **Form API**
	- Facilita o envio de dados de formulários multipart via requisições HTTP_POST
- **Slist API**
	- Permite criar e manipular listas encadeadas simples
	- Útil para gerenciar listas de cabeçalhos HTTP personalizados
- `libcurl-url`
	- Parsing de URL
	- Permite manipulação de URL´s
- `libcurl-ws`
	- websocket interface