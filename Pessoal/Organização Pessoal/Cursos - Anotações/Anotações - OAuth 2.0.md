---

---
# Tools

[https://8gwifi.org/jwkconvertfunctions.jsp](https://8gwifi.org/jwkconvertfunctions.jsp)

[https://tonyxu-io.github.io/pkce-generator/](https://tonyxu-io.github.io/pkce-generator/)

[https://developers.google.com/oauthplayground/](https://developers.google.com/oauthplayground/)

# Authorization Code Grant

- Usado para **Confidential Client**
- Ou seja, aplicações que rodam **server side** e podem armazenar o **client secret** de forma segura
- Evita expor o **Access Token** no frontend
- **NÃO PODE SER USADO NO FRONTEND**

![[SubPages/Pessoal/images/image 50.png]]

1. O usuário (resource owner) acessa o client que, por sua vez, necessita de autorização para acessar o resource server. Para isso, ele faz um redirect para o Authorization Server para que o Resource Owner se autentique. Neste redirect, o client informa uma URL de Callback que será utilizada pelo Authorization Server para fornecer o Authorization Code
2. O usuário se autentica e o Authorization Server faz um redirect para o Client, na URL especificada, fornecendo um **Authorization Code **que é válido por poucos minutos
3. O Client faz uma chamada para o Authorization Server, fornecendo os seguintes dados para poder obter o Access Token:
	1. o Authorization Code (Header `Authorization_code`)
	2. Client Id
	3. Client secret
	4. O Grant Type
4. Caso esteja utilizando OIDC, o Client pode também fazer uma chamada adicional para obter informações sobre o usuário
5. O Client chama o Resource Server passando o token obtido
6. O Resource server acessa o Introspect Endpoint do Authorization server para validar o token, caso este seja opaco, e obtém os escopos
7. Caso o token seja JWT (estruturado), a validação e obtenção dos escopos pode ser feito localmente, porém para isso, o Resource Server precisa, ao menos uma vez, acessar o Endpoint JWKS do Authorization Server para obter a chave pública deste e poder validar a assinatura do token

## **Configuração do Client (keycloak)**

Para que um client no keycloak seja do tipo **Confidential** e o fluxo utilizado seja o **Authorization Code Grant**, a configuração no keycloak é a seguinte:

![[SubPages/Pessoal/images/image 51.png]]

![[Anotações - OAuth 2.0]]

## Simulação Passo a passo (keycloak)

### Obtendo o Authorization Code - Frontend

8. Fazer a chamada via navegador pois o **postman** e **insomnia** podem ter problemas ao lidar com os cookies: 
```bash
https://au-dev.mppr.mp.br/realms/mppr/protocol/openid-connect/auth?response_type=code&client_id=idmask&redirect_uri=https%3A%2F%2Flocalhost%3A8080&scope=openid&state=teste
```
9. No redirect, é possível obter o **Authorization Code**
```bash
https://localhost:8080/?state=teste&session_state=e4269eb5-2c05-4b9e-8062-efd5bee16cba&iss=https%3A%2F%2Fau-dev.mppr.mp.br%2Frealms%2Fmppr&code=9cc63d7d-1a58-42e5-aba2-3611caddfb30.e4269eb5-2c05-4b9e-8062-efd5bee16cba.4b5e5ab4-4692-4c43-9e3a-2f451d987882
```

### Obtendo o Access Token - Backend

10. Fazer um request http **POST** para o endpoint do token, fornecendo o **Authorization Code** para trocá-lo por um **Access Token**
O parâmetro `redirect_uri` deverá ser exatamente o mesmo utilizado na chamada ao endpoint `auth `

```bash
curl --request POST \
--url https://au-dev.mppr.mp.br/realms/mppr/protocol/openid-connect/token \
--header 'Content-Type: application/x-www-form-urlencoded' \
--header 'User-Agent: insomnia/11.6.2' \
--data grant_type=authorization_code \
--data client_id=idmask \
--data client_secret=f8uwkjvlB9tHffTPsFQ39reb8OB5rSVf \  
--data code=a9133728-ea09-4148-bccb-256f700192ca.e4269eb5-2c05-4b9e-8062-efd5bee16cba.4b5e5ab4-4692-4c43-9e3a-2f451d987882 \  
--data redirect_uri=https://localhost:8080
```

11. A resposta fornecida vai conter: 
	1. O `access_token`, que deverá ser passado como **Bearer token** às demais chamadas
	2. O `id_token` que contém as informações do usuário, caso o escopo `openid` tenha sido solicitado
	3. O `refresh_token`, utilizado para renovar o `access_token`

```json
{
	"access_token": "eyJhbGciOiJSUzI1NiIsInR5cCIgOiAiSldUIiwia2lkIiA6ICI5OHF0cmVicFp1SGxacm1YVG8zYWtEcWp2SzBaVkQ3cnVqUXVlX0VBZ1RVIn0.eyJleHAiOjE3NzMxNzUwMzgsImlhdCI6MTc3MzE3MzIzOCwiYXV0aF90aW1lIjoxNzczMTcxMjM4LCJqdGkiOiJvbnJ0YWM6ZTc5ODYxMzMtZWUxNS0xOTM1LTI4YjktY2MyNjljZTM0OTViIiwiaXNzIjoiaHR0cHM6Ly9hdS1kZXYubXBwci5tcC5ici9yZWFsbXMvbXBwciIsImF1ZCI6WyJyZWFsbS1tYW5hZ2VtZW50IiwiZXByb21wLWp1ZCIsImNlYXAzNjAtaW5zcGVjb2VzLXBvbGljaWFpcyIsImhlcm1lcyIsImFjY291bnQiXSwic3ViIjoiODE4ZTQzYjItNTVhNi00YmU3LWE1OTQtNDY5NzU2NjExZDE4IiwidHlwIjoiQmVhcmVyIiwiYXpwIjoiaWRtYXNrIiwic2lkIjoiZTQyNjllYjUtMmMwNS00YjllLTgwNjItZWZkNWJlZTE2Y2JhIiwiYWNyIjoiMCIsImFsbG93ZWQtb3JpZ2lucyI6WyJodHRwczovL2lkbWFzay1kZXYubXBwci5tcC5ici8qIl0sInJlYWxtX2FjY2VzcyI6eyJyb2xlcyI6WyJzZXJ2aWRvcmVzIiwib2ZmbGluZV9hY2Nlc3MiLCJkZWZhdWx0LXJvbGVzLW1wcHIiLCJ1bWFfYXV0aG9yaXphdGlvbiJdfSwicmVzb3VyY2VfYWNjZXNzIjp7InJlYWxtLW1hbmFnZW1lbnQiOnsicm9sZXMiOlsidmlldy1yZWFsbSIsInZpZXctaWRlbnRpdHktcHJvdmlkZXJzIiwibWFuYWdlLWlkZW50aXR5LXByb3ZpZGVycyIsImltcGVyc29uYXRpb24iLCJyZWFsbS1hZG1pbiIsImNyZWF0ZS1jbGllbnQiLCJtYW5hZ2UtdXNlcnMiLCJxdWVyeS1yZWFsbXMiLCJ2aWV3LWF1dGhvcml6YXRpb24iLCJxdWVyeS1jbGllbnRzIiwicXVlcnktdXNlcnMiLCJtYW5hZ2UtZXZlbnRzIiwibWFuYWdlLXJlYWxtIiwidmlldy1ldmVudHMiLCJ2aWV3LXVzZXJzIiwidmlldy1jbGllbnRzIiwibWFuYWdlLWF1dGhvcml6YXRpb24iLCJtYW5hZ2UtY2xpZW50cyIsInF1ZXJ5LWdyb3VwcyJdfSwiZXByb21wLWp1ZCI6eyJyb2xlcyI6WyJlcHJvbXBqdWQtc2Vydmlkb3JlcyJdfSwiY2VhcDM2MC1pbnNwZWNvZXMtcG9saWNpYWlzIjp7InJvbGVzIjpbImNlYXAzNjAtc2Vydmlkb3JlcyJdfSwiaGVybWVzIjp7InJvbGVzIjpbInRlc3RhZG9yZXMiLCJkZXNlbnZvbHZlZG9yZXMiXX0sImFjY291bnQiOnsicm9sZXMiOlsibWFuYWdlLWFjY291bnQiLCJ2aWV3LWFwcGxpY2F0aW9ucyIsInZpZXctY29uc2VudCIsInZpZXctZ3JvdXBzIiwibWFuYWdlLWFjY291bnQtbGlua3MiLCJ2aWV3LXByb2ZpbGUiXX19LCJzY29wZSI6Im9wZW5pZCBlbWFpbCBwcm9maWxlIiwiZW1haWxfdmVyaWZpZWQiOnRydWUsIm5hbWUiOiJFRFVBUkRPIFFVSU5BTEhBIiwicHJlZmVycmVkX3VzZXJuYW1lIjoiZXF1aW5hbGhhIiwiZ2l2ZW5fbmFtZSI6IkVEVUFSRE8iLCJmYW1pbHlfbmFtZSI6IlFVSU5BTEhBIiwiZW1haWwiOiJlcXVpbmFsaGFAbXBwci5tcC5iciJ9.k2DeBu21Dp00YRsjKP2VOrAL2-vZyxsdzocuMYihpIYASkb6-XnD7tBhrQsoxDEqeTYg3vI7_b6a5_q3pxs_sG8QgC-a6BaO1aCFBBnvirb74x1mhuBHHiw1uJfL5rp5vb-zKRKzjpdIi3EXaSPA9qwK-fVHfiUru68H4HN8dxq6js-Wqn99KCAhZFd18npoaMo6oxYdZGzRCvdVVN-0UZoiZEiDNaq72U_6XJcKmuLKi8StVwqerSvsDTSheenzoXeo4fjEOHh8VA776q4jW4VRdqBotqJPvaDUR16vUj9qp8YjDNBE2gHjlQja1e7nCzjzJkp0DO0FVQq6ksFU_A",
	"expires_in": 1799,
	"refresh_expires_in": 960,
	"refresh_token": "eyJhbGciOiJIUzUxMiIsInR5cCIgOiAiSldUIiwia2lkIiA6ICI1MTJiOWEyZi02YjljLTQyYTQtYmQ2NC0yOTYzNDQ0Y2UzOTgifQ.eyJleHAiOjE3NzMxNzQxOTksImlhdCI6MTc3MzE3MzIzOSwianRpIjoiMWM5ZjE2ODItNjJhNS0wOGNhLWQyMTgtNWY4MmJmNzczZjZjIiwiaXNzIjoiaHR0cHM6Ly9hdS1kZXYubXBwci5tcC5ici9yZWFsbXMvbXBwciIsImF1ZCI6Imh0dHBzOi8vYXUtZGV2Lm1wcHIubXAuYnIvcmVhbG1zL21wcHIiLCJzdWIiOiI4MThlNDNiMi01NWE2LTRiZTctYTU5NC00Njk3NTY2MTFkMTgiLCJ0eXAiOiJSZWZyZXNoIiwiYXpwIjoiaWRtYXNrIiwic2lkIjoiZTQyNjllYjUtMmMwNS00YjllLTgwNjItZWZkNWJlZTE2Y2JhIiwic2NvcGUiOiJvcGVuaWQgZW1haWwgcHJvZmlsZSB3ZWItb3JpZ2lucyByb2xlcyBzZXJ2aWNlX2FjY291bnQgYmFzaWMgYWNyIiwicmV1c2VfaWQiOiIyZTc4YmRhZi00YWRkLTQxNWUtYjM0Mi0yMTQwZTQ2ZTNiNzkifQ.8bY2nAowZO8Lyu5WA6Pv5dTm_LwhCdgTFJ7_QXRv0WSGH2te9C_KOPsQddhNVGwN3daT122KNilToPMiwA1W6A",
	"token_type": "Bearer",
	"id_token": "eyJhbGciOiJSUzI1NiIsInR5cCIgOiAiSldUIiwia2lkIiA6ICI5OHF0cmVicFp1SGxacm1YVG8zYWtEcWp2SzBaVkQ3cnVqUXVlX0VBZ1RVIn0.eyJleHAiOjE3NzMxNzUwMzgsImlhdCI6MTc3MzE3MzIzOSwiYXV0aF90aW1lIjoxNzczMTcxMjM4LCJqdGkiOiI2ZDQxMzIwMi04YjA1LWIyYzgtZDUxYy02Yzg1MWUzMzg3MDciLCJpc3MiOiJodHRwczovL2F1LWRldi5tcHByLm1wLmJyL3JlYWxtcy9tcHByIiwiYXVkIjoiaWRtYXNrIiwic3ViIjoiODE4ZTQzYjItNTVhNi00YmU3LWE1OTQtNDY5NzU2NjExZDE4IiwidHlwIjoiSUQiLCJhenAiOiJpZG1hc2siLCJzaWQiOiJlNDI2OWViNS0yYzA1LTRiOWUtODA2Mi1lZmQ1YmVlMTZjYmEiLCJhdF9oYXNoIjoibzE2M2MyWUdQN0dyeFFiek9uVGVQZyIsImFjciI6IjAiLCJlbWFpbF92ZXJpZmllZCI6dHJ1ZSwibmFtZSI6IkVEVUFSRE8gUVVJTkFMSEEiLCJwcmVmZXJyZWRfdXNlcm5hbWUiOiJlcXVpbmFsaGEiLCJnaXZlbl9uYW1lIjoiRURVQVJETyIsImZhbWlseV9uYW1lIjoiUVVJTkFMSEEiLCJlbWFpbCI6ImVxdWluYWxoYUBtcHByLm1wLmJyIn0.XoTZ7ymaldHm75tw3rwKvtn-KFcBqQ7P8-6PeHzQiCQh8f11m_0Ojau8RcfsMhL3lfElZbLUgVZJZV01aOd8bXqv9TIJ_wW-XeKPGqLq0uiK-XONdj9FtTiDnjlxkNCUxPOx2aGr4qkJCCTQgHT6_aZz7L5KLfKDcJ7QMnlgQ601BxDyoRYu0lr4WFrcMrfnunAtRfPAzW5dLNHNJahIyj2BwchliVChgT3AwvfBi641jP4bvOXDDg9TMLSxcq5CxSkRHYbU5uXKbwBYzqPMHnv8-mJcl-ACz8DY_kWg9dhQSz_o3gDFkW8EpNgxuBagK0-G6VdjV02IeyYkmbccNA",
	"not-before-policy": 0,
	"session_state": "e4269eb5-2c05-4b9e-8062-efd5bee16cba",
	"scope": "openid email profile"
}
```

# Authorization Code Grant with PKCE

- Usado em um **Public Client**
- Ou seja, pressupõe que o **Client Secret** não pode ser armazenado de forma segura, o usuário poderia ter acesso a ele (frontend, pwa, mobile, etc.)
- Permite utilizar o Authorization Code no frontend
- Pode também ser utilizado por Confidential Clients, sendo inclusive recomendado

![[SubPages/Pessoal/images/image 52.png]]

12. O Client faz um redirect para o Authorization Server, passando um código aletorio (challange)
13. Depois do usuário se autenticar, o Authorization Server faz um redirect para a URL especificada pelo client, fornecendo o mesmo challange fornecido e o Authorization Code, garantindo que a requisição voltou para o mesmo cliente que a gerou e não um interceptador

## **Configuração do Client (keycloak)**

Para que um client no keycloak seja do tipo **Public **e o fluxo utilizado seja o **Authorization Code Grant with PKCE **, a configuração no keycloak é a seguinte:

![[SubPages/Pessoal/images/image 53.png]]

## Simulando Passo a passo (keycloak)

### Obtendo o Authorization Code - Frontend

14. Fazer a chamada via navegador pois o **postman** e **insomnia** podem ter problemas ao lidar com os cookies: 
```bash
https://au-dev.mppr.mp.br/realms/mppr/protocol/openid-connect/auth?response_type=code&client_id=idmask&scope=openid&state=state123&redirect_uri=https%3A%2F%2Flocalhost%3A8080&code_challenge=NDYwNzBkNGJmOTM0ZmIwZDRiMDZkOWUyYzQ2ZTM0Njk0NGUzMjI0NDQ5MDBhNDM1ZDdkOWE5NWU2ZDc0MzVmNQ&code_challenge_method=S256
```
	1. Para gerar o challenge, utilizar **Base64UrlEncode**(**SHA256Hash**(<code verifier>))
	2. Este site ajuda a gerar o challange: [https://tonyxu-io.github.io/pkce-generator/](https://tonyxu-io.github.io/pkce-generator/)
15. No redirect, é possível obter o `code `
```bash
https://localhost:8080/?state=teste&session_state=e4269eb5-2c05-4b9e-8062-efd5bee16cba&iss=https%3A%2F%2Fau-dev.mppr.mp.br%2Frealms%2Fmppr&code=9cc63d7d-1a58-42e5-aba2-3611caddfb30.e4269eb5-2c05-4b9e-8062-efd5bee16cba.4b5e5ab4-4692-4c43-9e3a-2f451d987882
```

### Obtendo o Access Token - Backend

16. Fazer um request http **POST** para o endpoint do token, fornecendo o **Authorization Code** para trocá-lo por um **Access Token**
	1. O parâmetro `redirect_uri` deverá ser exatamente o mesmo utilizado na chamada ao endpoint `auth`
	2. O parâmetro `code_verifier` faz o keycloak entender que trata-se do fluxo **Authorization Code Grant With PKCE, **seu valor deve coincidir exatamente com o campo `challange` da chamada anterior, porém, sem nenhum hash ou codificação 
```bash
curl --request POST \
--url https://au-dev.mppr.mp.br/realms/mppr/protocol/openid-connect/token \
--header 'Content-Type: application/x-www-form-urlencoded' \  
--header 'User-Agent: insomnia/11.6.2' \
--data grant_type=authorization_code \
--data client_id=idmask \
--data client_secret=f8uwkjvlB9tHffTPsFQ39reb8OB5rSVf \
--data code=9cc63d7d-1a58-42e5-aba2-3611caddfb30.e4269eb5-2c05-4b9e-8062-efd5bee16cba.4b5e5ab4-4692-4c43-9e3a-2f451d987882 \
--data redirect_uri=https://localhost:8080 \
--data code_verifier=teste
```

# Implicit Grant

- Deprecado por ser inseguro
- Envia o Access Token diretamente para o frontend via um redirect (GET), o que permitia que o token fosse sequestrado e utilizado por outros clients 

![[SubPages/Pessoal/images/image 54.png]]

# Client Credentials Grant

- Utilizado por comunicações entre backends (machine to machine)
- É o mais simples de todos
- Utilizado por Cronjobs

![[SubPages/Pessoal/images/image 55.png]]

# Resource Owner Password Grant

- Deprecado por ser inseguro
- O usuário fornece seu login e senha para o próprio client
- Poderia ser usado se o client e resource server forem da mesma aplicação ou corporação
- Significa que o client é confiável

![[SubPages/Pessoal/images/image 56.png]]

# Refresh Token

- É tratado como um Grant Type
- Funciona em conjunto com o Authorization Code Grant
- O Client faz uma requisição do tipo Get Access Token passando como parâmetro o token expirado e o refresh token para obter um novo Access Token

![[SubPages/Pessoal/images/image 57.png]]

# Token Revocation

- Pode funcionar diferente em cada tipo de Authorization Servers
- Idealmente invalida tanto o Access Token e o Refresh Token

![[SubPages/Pessoal/images/image 58.png]]

# OpenID

- É tratado como um escopo do OAuth 2.0
- Uma vez informado o escopo openid, o client poderá acessar o endpoint `/userinfo` para obter informações do usuário
- Alguns escopos adicionais devem ser fornecidos de acordo com o tipo de informação que o client deseja acessar

![[SubPages/Pessoal/images/image 59.png]]
