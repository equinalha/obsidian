---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2025-08-12T13:03:00
Owner:
  - Eduardo Quinalha
---
> [!tip] 💡
> O OAuth é uma tecnologia de autorização, enquanto o SSO é uma tecnologia de autenticação.

![[20230804_070408.jpg]]

# AAA

- Authentication
	- Relacionado à identificação
	- Apenas relaciona o usuário com uma identidade
	- Não bloqueia ou autoriza nada
- Authorization
- Accounting

## Autenticação Forte

- Dois ou mais fatores
	- Algo que vc sabe
	- Algo que vc tem
	- Algo que vc é
		- Digital
		- Palma da mão
		- Imagem da face
		- Íris
		- Retina
		- Reconhecimento de voz

## Biometria

1. Universalidade – Significa que todas as pessoas devem possuir a característica;
2. Singularidade – Indica que esta característica não pode ser igual em pessoas diferentes;
3. Permanência – Significa que a característica não deve variar com o tempo;
4. Mensurabilidade – Indica que a característica pode ser medida quantitativamente;

# SSO

- **OAuth não é SSO**
	- OAuth é autenticação via serviço parceiro
	- SSO está relacionado com seção compartilhada
- SSO é um ponto único de logon, e todos os serviços associados já entram logados
- Tipos
	- SSO Web
		- Ambientes baseados em web
		- Utiliza tecnologias como SAML, OAuth e OpenID Connect
	- SSO Federado
		- Entre organizações
		- Variação do SSO Web
	- SSO Desktop
		- Usado em redes locais
		- Kerberos
		- Windows Integrated Authentication

# SAML

- É usado para implementar um SSO
- **Focado no processo de identificação**
- **Utiliza XML como formato de mensageria**
- **Não usa JWT**
- Atores - **SUI (Service Provider, User Agent, Identity Provider)**
	- Service Provider
		- Provê o serviço requisitado pelo usuário
		- Faz o redirecionamento ao SSO, Identity Provider (pode existir mais de 1)
	- User Agent
		- O usuário que deseja acessar o serviço
	- Identity Provider (IdP)
		- Faz o reconhecimento do usuário
		- Confirma a identidade do usuário
- Processo
	- Usuário acessa o Service Provider, requisitando o acesso
	- O Service Provider identifica qual é o Identity Provider do usuário (pode ser via escolha do próprio usuário) e redireciona a requisição para este
	- O IdP responde com uma estrutura xhtml

![[SAML.png]]

# OAuth2

[https://developer.okta.com/blog/2019/10/21/illustrated-guide-to-oauth-and-oidc](https://developer.okta.com/blog/2019/10/21/illustrated-guide-to-oauth-and-oidc)

- Provê a capacidade de uma aplicação fornecer acesso aos recursos, sem precisar ter o conhecimento das informações de autenticação do usuário
- A aplicação não precisa mais armazenar informações sobre o usuário
- É um framework próprio, se integra a outros como LDAP, mas não depende deste
- Pode utilizar JWT
- um único servidor de autorização pode emitir *tokens* de acesso aceitos por vários servidores de recursos
- **Não há compatibilidade total com a versão 1.0**
- o servidor de autorização pode ser o mesmo que o servidor de recursos
- Os refresh Tokens são emitidos para o **cliente** pelo servidor de **autorização **e utilizados para se obter um novo access token, quando o atual expirar

## Papéis

- **Proprietário do Recurso (Resource Owner):**
	- O proprietário do recurso é o usuário final que possui recursos protegidos e tem a capacidade de conceder acesso a esses recursos a aplicativos de terceiros.
	- Ele pode ser uma pessoa ou uma entidade que controla os recursos protegidos.
	- Por recurso entenda-se dados do usuário que ele pode escolher dar ou não acesso à aplicação. Por exemplo: endereço de e-mail, foto do perfil, histórico de navegação, etc.
	- Você já deve ter se deparado com uma tela semelhante a esta em algum momento. Trata-se de uma etapa do fluxo do OAuth 2.0 e que solicita seu consentimento para que a aplicação (cliente) tenha acesso aos seus recursos (resources) hospedados pelo Resource Server, que neste caso pode ser o google, microsoft ou facebook, por exemplo.=
- **Cliente (Client):**
	- O cliente é o aplicativo que solicita acesso aos recursos protegidos em nome do proprietário do recurso.
	- Ele pode ser um aplicativo web, um aplicativo móvel, um serviço da web, entre outros.
	- O cliente não possui credenciais próprias para acessar os recursos protegidos, ele precisa obter autorização do proprietário do recurso.
	- Existem dois tipos de clientes:
		- **Clientes Confidenciais (Confidential Clients):**
			- Os clientes confidenciais são capazes de manter segredos, como uma chave secreta ou um certificado, de forma segura. Normalmente são aplicações que rodam em servidores (backend).
			- Eles podem autenticar-se diretamente com o Servidor de Autorização e trocar esses segredos por tokens de acesso.
		- **Clientes Públicos (Public Clients):**
			- Os clientes públicos não são capazes de manter segredos de forma segura, geralmente porque são executados em um ambiente não confiável, como um navegador da web ou um aplicativo móvel que pode ser comprometido. São aplicações que rodam no lado do usuário, em navegadores ou aplicações mobile.
			- Eles não podem autenticar-se diretamente com o Servidor de Autorização usando segredos, em vez disso, eles dependem de métodos de autenticação mais fracos, como redirecionamento de URI ou tokens de ID de cliente.
- **Servidor de Autorização (Authorization Server):**
	- O servidor de autorização é responsável por autenticar o proprietário do recurso e conceder tokens de acesso ao cliente.
	- Ele interage diretamente com o proprietário do recurso para autenticá-lo e solicitar sua autorização.
- **Servidor de Recursos (Resource Server):**
	- O servidor de recursos hospeda os recursos protegidos que o cliente deseja acessar em nome do proprietário do recurso.
	- Ele é responsável por verificar os tokens de acesso recebidos pelo cliente para garantir que o acesso aos recursos seja autorizado.
	- O servidor de recursos serve os recursos protegidos somente se o cliente apresentar um token de acesso válido e autorizado.

## Fluxos

O OAuth 2.0 define vários fluxos de autorização, ou grant types, que descrevem como um aplicativo pode obter acesso a recursos protegidos em nome de um usuário. Cada fluxo é projetado para atender a diferentes cenários de uso e requisitos de segurança. Vamos explicar cada um:

- **Client Credentials**
	- Empregado quando os clientes (aplicações) requisitam um token para acessar **seus próprios recursos** em seu próprio nome, em vez de fazê-lo em nome do usuário. 
	- Esses clientes frequentemente são aplicações **machine-to-machine (M2M),** como CLIs, daemons ou serviços operando no backend. 
	- Deve ser adotado **somente por clientes considerados confiáveis.**
- **Authorization Code**
	- Fluxo mais comum e recomendado para a maioria das aplicações. 
	- Atende tanto clientes confidenciais quanto públicos que podem ser web, mobile ou nativos. 
	- Ao contrário do Client Credentials, neste caso o resource owner (usuário) precisará abrir o navegador para iniciar o fluxo. 
	- O Client irá redirecioná-lo para o Authorization Server, onde fará sua autenticação e em seguida retornará ao Client, em uma URL específica, com um código de autorização. 
	- Este código, deverá depois ser trocado por um Access Token que permitirá o acesso aos recursos do usuário no Resource Server.
- **Device Code**
	- Este fluxo é projetado para dispositivos com recursos limitados de entrada, como televisões, consoles de jogos, dispositivos IoT (Internet das Coisas) e outros dispositivos que não possuem uma interface de usuário completa para autenticação.
	- Neste fluxo, o Client faz uma requisição ao Authorization Server que irá responder com um User_code, um Device_code e uma URL. 
	- O User code é fornecido ao usuário que deverá acessar a URL em outro dispositivo (computador ou smartphone) para fazer sua autenticação. 
	- Enquanto isso, o Client continuará fazendo requisições ao Authorization Server, em curtos intervalos de tempo, informando o Device_code recebido.
	- Quando o usuário concluir a autenticação informando o User_code recebido, um Access Token será fornecido ao Client em sua próxima requisição.
- **PKCE**
	- Proof Key for Code Exchange (PKCE) é uma extensão Authorization Code para prevenir ataques CSRF e de injeção de código de autorização. 
	- A técnica envolve o cliente criando primeiro um segredo em cada solicitação de autorização e, em seguida, utilizando esse segredo novamente ao trocar o código de autorização por um token de acesso. 
	- Dessa forma, se o código for interceptado, não será útil, pois a solicitação do token depende do segredo inicial.
- **Implicit Grant**
	- É utilizado em cenários onde a aplicação cliente está operando em um ambiente confiável e não é necessário proteger a confidencialidade do token de acesso. 
	- Neste fluxo, o token de acesso é obtido diretamente pelo cliente, sem a necessidade de troca de um código de autorização. 
	- Isso simplifica o fluxo de autorização, mas também apresenta alguns desafios de segurança, especialmente em ambientes públicos.
	- Este fluxo é um dos fluxos **legados**, herdados de versões anteriores.
	- Atualmente, não é recomendado utilizá-lo devido aos riscos inerentes de retornar tokens de acesso em um redirecionamento HTTP sem qualquer confirmação de que foi recebido pelo cliente. 
	- Clientes públicos, como aplicativos nativos e aplicativos JavaScript, devem agora utilizar o fluxo de código de autorização com a extensão PKCE em seu lugar.
- **Resource Owner Credentials Grant**
	- Este fluxo é utilizado quando a aplicação cliente precisa acessar recursos protegidos em nome do próprio usuário, utilizando as credenciais do usuário (como nome de usuário e senha). 
	- Embora esse fluxo forneça uma maneira direta para que as aplicações obtenham tokens de acesso, ele também apresenta riscos de segurança, como a exposição das credenciais do usuário à aplicação cliente e a dificuldade de revogação se as credenciais do usuário forem comprometidas.

## Tokens

### **Tokens de Acesso**

- Os tokens de acesso são os principais componentes de confiança do OAuth. 
- Eles são emitidos pelo Authorization Server e funcionam como credenciais, permitindo que clientes (como aplicativos) acessem recursos do usuário no Resource Server. 
- Eles funcionam como "vales" digitais que devem ser apresentados pelo cliente sempre que uma solicitação de acesso a um recurso for feita.
- Os tokens não são legíveis nem interpretáveis pelo cliente. 
- Além disso, eles não transmitem informações de identidade do usuário ou qualquer outro dado sensível. 
- Os tokens utilizados no OAuth podem ser organizados em duas principais classes: 
	- Access Tokens e 
	- Refresh Tokens.

### **Access Tokens**

- Os Access Tokens, em geral, possuem uma vida útil limitada, com um tempo de expiração relativamente curto, muitas vezes apenas alguns minutos. 
- Essa medida de segurança visa mitigar possíveis ataques, como a interceptação de comunicações, que poderiam resultar no comprometimento do token e acesso não autorizado aos recursos do usuário.

Os Access tokens do OAuth 2.0 podem ser dos seguintes tipos:

- **Bearer Token: **O nome "Bearer" significa "portador" em inglês, e o termo refere-se ao fato de que o cliente (ou "portador" do token) o apresenta ao servidor de recursos como prova de sua autorização para acessar os recursos protegidos. Este tipo de token é considerado "opaco" para o cliente, o que significa que o cliente não precisa entender ou interpretar o conteúdo do token. Em vez disso, o cliente simplesmente apresenta o token ao servidor de recursos (resource server) para obter acesso aos recursos protegidos.
	Bearer Tokens são frequentemente usados em aplicativos da web, APIs RESTful e outros cenários onde a simplicidade e a eficiência são importantes.
- **Sender-Constrained:**** O Sender-Constrained Token funciona como uma passagem de avião. Não basta apresentá-la no guichê, também é necessário comprovar que ele foi emitido a quem está embarcando, ou seja, além de apresentar o ticket, o portador deverá comprovar ser a pessoa para quem a passagem foi emitida.Este tipo de token requer que o cliente prove que tem posse de uma chave privada específica ao apresentar o token ao servidor de recursos. Essa abordagem é particularmente útil em cenários onde a segurança é uma preocupação extrema, como em transações financeiras ou acesso a recursos altamente sensíveis. No entanto, também adiciona complexidade ao processo de autenticação e autorização, pois requer a implementação de mecanismos adicionais para gerar, proteger e validar as chaves privadas.**

### **Refresh Token**

- O Refresh Token é um tipo especial de token que permite aos clientes obterem novos Access Tokens sem a necessidade de solicitar ao usuário que faça login novamente. 
- Como eles têm vida curta, sem o Refresh Token o usuário seria obrigado a se autenticar junto ao Authorization Server toda vez que seu token expirasse.
- Como forma de contornar este inconveniente, sempre que um cliente solicita um Access Token ao servidor de autorização (authorization server) durante o processo de autenticação inicial, geralmente é emitido também um Refresh Token. 
- Enquanto o Access Token é usado para acessar recursos protegidos, o Refresh Token é usado para obter um novo Access Token quando o token atual expira.
- Ao contrário dos demais tipos, que sempre são apresentados ao Resource Server, o refresh token é apresentado pelo cliente ao Authorization Server.

## Boas Práticas

- Utilizar um servidor de autenticação para certificar a identidade do servidor de autorização
	- Mitiga o risco de um ataque do tipo man in the middle, onde o refresh token poderia estar sendo interceptado por uma réplica falsa do servidor de autorização

![[OAuth2.png]]

# OpenID Connect (OIDC)

- O OIDC utiliza o** OAuth 2.0** como um protocolo subjacente
- As principais extensões em relação ao OAuth são: 
	- um valor de escopo especial ("openid"), 
	- o uso de um token extra (o token de ID, que encapsula as claims de identidade no formato JSON)
	- ênfase na autenticação em vez da autorização.
	- o termo "fluxo" é usado no lugar da "concessão" do OAuth2.
- Os tokens de ID devem ser assinados digitalmente para evitar adulterações. 
- Eles também podem ser criptografados para fornecer privacidade adicional, embora, em muitos casos, a segurança da camada de transporte (HTTPS) seja suficiente. 
- Para SPAs e aplicativos móveis, a criptografia de token de ID não é útil, pois a chave de descriptografia pode ser descoberta facilmente.
- Com OAuth puro, a aplicação (client) não tem informações sobre o usuário logado
- OIDC permite à aplicação cliente saber mais sobre o usuário
- Segue o mesmo fluxo do OAuth2, com uma pequena modificação:
	- quando o Authorization Server redireciona o usuário novamente para a aplicação, passando o código temporário, ele envia também um JWT, contendo informações do usuário (claims)
- Enquanto [**o OAuth 2.0 é um protocolo de autorização**](https://auth0.com/docs/videos/learn-identity/02-oidc-and-oauth), o OIDC é um protocolo de **autenticação de identidade** e pode ser usado para verificar a identidade de um usuário para um serviço cliente, também chamada **Parte Confiável**.
- Pode ser usado por:
	- SPA
	- SSO
	- aplicativos móveis

## Fluxos do OIDC

- [**Fluxo implícito**](https://auth0.com/docs/api-auth/tutorials/adoption/implicit): 
	- Neste fluxo, comumente usado por SPAs, os tokens são devolvidos diretamente para a RP (Cliente) em um URI de redirecionamento.
![[image 69.png]]
- [**Fluxo de código de autorização**](https://auth0.com/docs/api-auth/tutorials/adoption/authorization-code): 
	- Este fluxo é mais seguro do que o fluxo implícito, pois os tokens não são retornados diretamente. 
	- Para aplicativos nativos/móveis e SPAs, a segurança pode ser aprimorada usando uma [**chave de prova para troca de código**](https://auth0.com/docs/api-auth/tutorials/authorization-code-grant-pkce). (PKCE)
![[image 70.png]]
- [**Fluxo híbrido**](https://auth0.com/docs/api-auth/tutorials/hybrid-flow): 
	- Combinando os fluxos de código implícitos e de autorização, neste caso o token de ID é devolvido diretamente para a RP, mas o token de acesso não. 
	- Em vez disso, é retornado um código de autorização que é trocado por um token de acesso.

# OAuth 2.0 - Questões 

**1 - **Considerando o protocolo OAuth 2.0 e seus fluxos, responda à seguinte questão.

Neste fluxo de autorização, um dos quatro participantes não está presente. Trata-se de uma comunicação máquina a máquina que só pode ser adotado por clientes considerados confiáveis.

Estamos falando do fluxo:

(A) Authorization Code

(B) Implicit Grant

(C) Resource Owner Credentials Grant

(D) Client Credentials

(E) Password Credentials

**Resumo:**

O OAuth 2.0 define vários fluxos de autorização, ou grant types, que descrevem como um aplicativo pode obter acesso a recursos protegidos em nome de um usuário. Cada fluxo é projetado para atender a diferentes cenários de uso e requisitos de segurança.

O fluxo denominado **Client Credentials** é empregado quando os clientes (aplicações) requisitam um token para acessar seus próprios recursos em seu próprio nome, em vez de fazê-lo em nome do usuário. Esses clientes frequentemente são aplicações machine-to-machine (M2M), como CLIs, daemons ou serviços operando no backend. Deve ser adotado somente por clientes considerados confiáveis.

Neste fluxo, o **Resource Owner**, um dos quatro papéis previstos pelo OAuth 2.0, não participa da comunicação.

**Gabarito: D**

Vamos analisar as demais alternativas:

**A - Authorization Code: **Fluxo mais comum e recomendado para a maioria das aplicações. Atende tanto clientes confidenciais quanto públicos que podem ser web, mobile ou nativos. Ao contrário do Client Credentials, neste caso o resource owner (usuário) precisará abrir o navegador para iniciar o fluxo. O Client irá redirecioná-lo para o Authorization Server, onde fará sua autenticação e em seguida retornará ao Client, em uma URL específica, com um código de autorização. Este código, deverá depois ser trocado por um Access Token que permitirá o acesso aos recursos do usuário no Resource Server.

**B - Implicit Grant: **É utilizado em cenários onde a aplicação cliente está operando em um ambiente confiável e não é necessário proteger a confidencialidade do token de acesso. Neste fluxo, o token de acesso é obtido diretamente pelo cliente, sem a necessidade de troca de um código de autorização. Isso simplifica o fluxo de autorização, mas também apresenta alguns desafios de segurança, especialmente em ambientes públicos. Por este motivo, foi descontinuado nas versões atuais do protocolo.

**C - Resource Owner Credentials Grant: **Este fluxo é utilizado quando a aplicação cliente precisa acessar recursos protegidos em nome do próprio usuário, utilizando as credenciais do usuário (como nome de usuário e senha). Embora esse fluxo forneça uma maneira direta para que as aplicações obtenham tokens de acesso, ele também apresenta riscos de segurança, como a exposição das credenciais do usuário à aplicação cliente e a dificuldade de revogação se as credenciais do usuário forem comprometidas. Trata-se de uma forma antiga de trocar as credenciais do usuário, herdada das versões anteriores do protocolo. Como a aplicação cliente precisa coletar a senha do usuário e enviá-la para o servidor de autorização, não é recomendado que este tipo de concessão seja mais utilizado. Este fluxo não oferece suporte a mecanismos mais avançados como autenticação multifatorial.

**E - Password Credentials: **Sinônimo de Resource Owner Credentials Grant.

**2 - **Considere a figura a seguir:

![[Untitled 272.png]]

Qual fluxo de autorização do OAuth 2.0 pode ser melhor descrito pela imagem?

(A) Authorization Code

(B) PKCE

(C) Device Code

(D) Client Credentials

(E) Resource Owner Credentials

**Resumo:**

Observe que o usuário fornece suas credenciais (usuário e senha) para o client (aplicativo). Este por sua vez, repassou estes dados, acrescido de sua própria identificação para o Authorization Server que lhe devolveu um Access Token em resposta.

Este fluxo, onde o usuário compartilha suas informações de autenticação com o Client é chamado de Resource Owner Credentials.

É importante destacar que este é um fluxo antigo, herdado das versões anteriores do protocolo e não deve mais ser utilizado, pelo fato de expor as credenciais do usuário.

**Gabarito: E**

Vamos analisar as outras alternativas:

(A) No fluxo Authorization Code, o usuário não compartilha suas informações de autenticação com o Client. Ao invés disto, é redirecionado para o Authorization Server e aí sim, fornece suas credenciais para autenticação.

(B) Proof Key for Code Exchange (PKCE) é uma extensão Authorization Code para prevenir ataques CSRF e de injeção de código de autorização. A técnica envolve o cliente criando primeiro um segredo em cada solicitação de autorização e, em seguida, utilizando esse segredo novamente ao trocar o código de autorização por um token de acesso. Dessa forma, se o código for interceptado, não será útil, pois a solicitação do token depende do segredo inicial.

(C) O fluxo Device Code é projetado para dispositivos com recursos limitados de entrada, como televisões, consoles de jogos, dispositivos IoT (Internet das Coisas) e outros dispositivos que não possuem uma interface de usuário completa para autenticação.

(D) O fluxo denominado Client Credentials é empregado quando os clientes (aplicações) requisitam um token para acessar seus próprios recursos em seu próprio nome, em vez de fazê-lo em nome do usuário. Esses clientes frequentemente são aplicações machine-to-machine (M2M), como CLIs, daemons ou serviços operando no backend. Deve ser adotado somente por clientes considerados confiáveis. Neste fluxo, o Resource Owner, um dos quatro papéis previstos pelo OAuth 2.0, não participa da comunicação.

**3 - **Existem propriedades dos tokens de acesso que são fundamentais para o modelo de segurança do OAuth, são elas:

I - Os tokens de acesso não devem ser lidos ou interpretados pelo cliente OAuth. O cliente OAuth não é o público-alvo do token.

II - Os tokens de acesso devem transmitir a identidade do usuário e os papéis concedidos a ele, para que o Client possa autorizar ou não o seu acesso aos recursos protegidos da aplicação.

III - Os tokens de acesso devem ser usados apenas para fazer solicitações ao servidor de autorização.

Está correto o que se afirma em:

**(A)** I apenas

**(B)** I e II

**(C)** II apenas

**(D)** II e III

**(E)** III apenas

**Resumo:**

Os tokens de acesso são os principais componentes de confiança do OAuth. Eles são emitidos pelo Authorization Server e funcionam como credenciais, permitindo que clientes (como aplicativos) acessem recursos do usuário no Resource Server. Eles funcionam como "vales" digitais que devem ser apresentados pelo Client ao Resource Server sempre que uma solicitação de acesso a um recurso for feita. Os tokens de acesso não devem ser interpretados pelos Clients nem carregar qualquer informação sobre o usuário.

Vamos analisar as alternativas:

I - Correto. Os tokens não devem ser interpretados pelo Client. Eles servem apenas para que o Client os repasse ao Resource Server que irá validá-los e conceder acesso aos recursos solicitados.

II - Falso. Os tokens de acesso não devem transmitir nenhuma informação sobre o usuário para o Client.

III - Falso. Os tokens devem ser utilizados para efetuar as requisições ao Resource Server (Servidor de recursos). Este por sua vez irá validá-lo junto ao Authorization Server.

**Gabarito: A**

**4 - **Os tokens de acesso são os principais componentes de confiança do OAuth. Eles são emitidos pelo Authorization Server e funcionam como credenciais, permitindo que clientes (como aplicativos) acessem recursos do usuário, em nome deste, no Resource Server.

Sobre o formato dos tokens é correto afirmar que:

(A) Os tokens de acesso utilizados pelo OAuth são strings hexadecimais com tamanho de 170 caracteres.

(B) Os tokens OAuth são documentos XML codificados em Base64 e enviados como string.

(C) Os tokens não precisam estar em nenhum formato específico.

(D) Os tokens de acesso utilizados pelo OAuth são tokens JWT, onde as informações são representadas como um documento JSON.

(E) Tokens devem ser criptografados antes de serem enviados ao Resource Server.

**Resumo:**

De acordo com a própria RFC 6749, que descreve o protocolo OAuth 2.0, os tokens não precisam estar em nenhum formato específico. Na verdade, são strings opacas do ponto de vista do Client. Cada implementação OAuth poderá especificar o seu formato.

**Gabarito: C**

Vamos analisar as demais alternativas:

(A) Errado. Não há necessidade de se respeitar um formato específico.

(B) Errado. Na verdade seria pouco prático esta abordagem, uma vez que documentos XML costumam ser grandes e verbosos.

(D) Errado. Eles podem ser JWT, mas não é uma obrigatoriedade.

(E) Errado. Como eles já são uma string opaca, sem significado, não há esta necessidade. Além do mais, o uso de uma conexão criptografada por meio de HTTPS já é um pré-requisito para o uso do OAuth, dispensando esta camada adicional de criptografia.

**5 - **OAuth 2.0 é um protocolo de autorização que permite que aplicativos obtenham acesso limitado a recursos em nome de um usuário, sem a necessidade de compartilhar as credenciais de login. Dentre os elementos que viabilizam o funcionamento do protocolo estão os tokens que essencialmente podem ser de três tipos: Access Tokens, Refresh Tokens e ID Tokens. Sobre os ID Tokens é correto afirmar:

(A) São strings opacas que não carregam nenhuma informação específica.

(B) Requer que o cliente prove que tem posse de uma chave privada específica ao apresentar o token ao servidor de recursos. Essa abordagem é particularmente útil em cenários onde a segurança é uma preocupação extrema, como em transações financeiras ou acesso a recursos altamente sensíveis.

(C) São tokens apresentados ao Resource Server com a intenção de identificar o Resource Owner.

(D) São tokens destinados ao Client e podem conter informações sobre o Resource Owner.

(E) São utilizados pelo Client para obter o Access Token.

**Resumo:**

ID tokens são especificados separadamente pelo OpenID Connect, que funciona como uma camada adicional sobre o OAuth 2.0. Um ID token contém informações sobre o que aconteceu quando um usuário se autenticou e é destinado a ser lido pelo cliente OAuth. Ele também pode conter informações sobre o usuário, como seu nome ou endereço de e-mail, embora isso não seja um requisito.

**Gabarito: D**

Sobre as demais alternativas:

(A) Errado, esta descrição combina melhor com o Access Token.

(B) Errado, estes são os tokens Sender-Constrained, um tipo específico de Access Token.

(C) Errado, esta especificação não existe.

(E) Errado, esta descrição combina com o Authorization Code.

**6 - **De acordo com a especificação do OAuth 2.0, as aplicações podem ser classificadas como confidenciais ou públicas. A principal diferença está relacionada a se a aplicação é capaz ou não de manter as credenciais (como um ID de cliente e uma senha) de forma segura. Isso afeta o tipo de autenticação que as aplicações podem usar.

Assinale a alternativa que corresponde a clientes do tipo confidencial.

(A) Aplicativos nativos para smartphones ou desktop

(B) Aplicações web rodando em servidores backend seguros

(C) Aplicações web client-side utilizando frameworks como React.JS ou Angular

(D) Aplicações Java Desktop

(E) Aplicações web do tipo Progressive Web Apps (PWA)

**Resumo:**

Clientes confidenciais são aqueles que podem manter credenciais armazenadas de forma segura, o que significa, longe do alcance do próprio usuário ou outros agentes mal intencionados. Sendo assim, somente uma aplicação que rode em um ambiente fora do controle do usuário, como o backend, atende a esta especificação.

**Gabarito: B**

Vamos às alternativas:

(A) Errado. Aplicativos nativos rodam em dispositivos do usuário, o que significa que este poderá ter acesso ao token contendo as informações confidenciais.

(C) Errado. Estas aplicações rodam em navegadores no lado do usuário.

(D) Errado. Aplicações Java Desktop também rodam em dispositivos de usuário.

(E) Errado. Estas aplicações também rodam no navegador, do lado do usuário.

**7 - **SPA, ou Single Page Application, é um tipo de aplicativo web que carrega dinamicamente todo o conteúdo da página em uma única carga inicial. Em vez de recarregar a página inteira ao interagir com o aplicativo, o SPA atualiza apenas as partes relevantes da página. Normalmente estas aplicações fazem isto enviando requisições para uma API rodando em um servidor remoto, que na maioria das vezes precisa ser autenticada e autorizada. Para atender a este tipo de aplicação, qual fluxo do OAuth 2.0 pode ser utilizado?

Assinale a alternativa correta.

(A) Client Credentials

(B) Implicit Grant

(C) Authorization Code com a extensão do PKCE

(D) Device Code

(E) Resource Owner Credentials

**Resumo:**

SPA são aplicações web que rodam em um navegador, no lado do usuário. Sendo assim, a recomendação é que se utilize o fluxo Authorization Code com a extensão do PKCE, uma vez que as credenciais não podem ser armazenadas localmente de forma segura.

**Gabarito: C**

Quanto às demais alternativas:

(A) Este fluxo é utilizado em comunicações que ocorrem entre as aplicações rodando em backend, sem a participação do usuário.

(B) Tipo de fluxo simplificado em que o Access Token é enviado diretamente ao Client. Atualmente encontra-se descontinuado nas versões mais atuais do protocolo.

(D)  Este fluxo é utilizado para a autenticação de dispositivos que possuem limitação de recursos de entrada de dados, como televisores e consoles de videogame.

(E) Neste fluxo, o usuário fornece suas credenciais para o Client que as reenvia para o Authorization Server. Atualmente encontra-se descontinuado por ser considerado inseguro.

**8 - **O fluxo Implicit Grant foi descontinuado e não é mais suportado pelas últimas versões do protocolo OAuth. Qual das alternativas abaixo representa uma justificativa para tal decisão?

(A) Neste fluxo, o token enviado pelo Authorization Server para o Client contém informações sobre o Resource Owner.

(B) Por ser demasiadamente complexo, este fluxo prejudicava o desempenho das aplicações clientes.

(C) Os tokens utilizados neste fluxo possuem um tempo de vida muito curto, o que por consequência fazia com que o Client disparasse muitas requisições ao Authorization Server, buscando por Refresh Tokens, podendo ocasionar comprometimento da disponibilidade deste.

(D) Este fluxo se destinava ao uso em dispositivos com limitação de entrada de dados como televisores e consoles de videogame, no entanto, foram descobertas vulnerabilidades no processo que possibilitavam o extravio dos tokens, podendo estes serem reaproveitados por possíveis atacantes.

(E) Este fluxo possibilita que ocorra vazamento do token, podendo este ser utilizado por terceiros em ataques do tipo replay.

**Resumo:**

No fluxo Implicit Grant, os tokens de Acesso são enviados diretamente ao Client, logo após a autenticação do usuário. De acordo com o grupo de trabalho do OAuth na IETF, este fluxo é vulnerável ao vazamento dos Access Tokens, o que significa que um atacante pode extraílos e usá-los em benefício próprio. Isso pode, por exemplo, resultar no acesso do atacante ao registro de saúde do usuário legítimo ou na realização de um pagamento em sua conta bancária.

**Gabarito: E**

Quanto às demais alternativas:

(A) Errado. Access Tokens não são destinados ao Client, não possuem informações sobre o usuário e não podem ser interpretados por este.

(B) Errado. Na verdade, o fluxo Implicit Grant é até mais simples do que o Authorization Code, que é amplamente utilizado.

(C) Errado. Justamente por ter um tempo de vida consideravelmente alto, este fluxo possibilita que o atacante sequestre o token e o reutilize a seu proveito

(D) Errado. O fluxo dedicado a este tipo de dispositivos é o Device Code.

**9 - **OAuth 2.0 é um protocolo de autorização que permite que aplicativos obtenham acesso a recursos em nome de um usuário sem necessidade de compartilhar credenciais de login. Um dos componentes que define o funcionamento deste protocolo é o escopo.

Assinale a alternativa que melhor define o que é um escopo.

(A) Um identificador exclusivo atribuído a cada aplicativo cliente registrado no servidor de autorização.

(B) São permissões específicas que o usuário concede ao aplicativo cliente durante o processo de autorização e que definem o nível de acesso que um aplicativo cliente tem a recursos protegidos em nome do usuário.

(C) Uma técnica de criptografia utilizada para proteger as comunicações entre o aplicativo cliente e o servidor de autorização.

(D) Um token de acesso único gerado pelo servidor de autorização para autenticar o usuário durante o processo de autorização.

(E) Um conjunto de plugins instalados no servidor de autorização para personalizar o comportamento do OAuth 2.0.

**Resumo:**

Os escopos são strings que definem o nível de acesso que um aplicativo cliente tem a recursos protegidos em nome do usuário. Eles representam permissões específicas que o usuário concede ao aplicativo cliente durante o processo de autorização. Por exemplo, um escopo pode ser "ler_dados_usuario" para permitir que o aplicativo cliente acesse informações básicas do usuário, enquanto outro escopo pode ser "escrever_postagens" para permitir que o aplicativo cliente publique postagens em nome do usuário.

**Gabarito: B**

Quanto às demais alternativas:

(A) Errado. Esta definição atende ao conceito de ClientID.

(C) Errado. OAuth faz uso de SSL/TLS para isso, uma vez que só pode ser utilizado em comunicações via HTTPS.

(C) Errado. Tal token não existe no OAuth 2.0

(D) Errado.

**10 - No **OAuth 2.0 existe um mecanismo que define um formato que os clientes podem utilizar para buscar as informações necessárias para interagir com um servidor OAuth. Isso inclui parâmetros como o endpoint de autorização, lista dos escopos suportados e protocolos de autenticação do cliente. Como se chama este mecanismo?

(A) OAuth Discovery

(B) OAuth Lookup

(C) OAuth Search

(D) OAuth Finder

(E) OAuth Explore

**Resumo:**

O mecanismo que permite às aplicações clientes obterem informações sobre como interagir com o servidor OAuth é o OAuth Discovery, também conhecido por Authorization Server Metadata. Isso é feito através do uso de um documento JSON chamado "Discovery Document", que contém metadados sobre o provedor de serviços OAuth, incluindo URLs para autorização, token, revogação, informações do usuário, entre outros. O cliente pode obter esse documento em um local padrão (como /.well-known/oauth-authorization-server) e, a partir dele, pode descobrir dinamicamente os detalhes necessários para interagir com o provedor OAuth.

**Gabarito: A**

Quanto às demais alternativas, elas não representam nenhum mecanismo existente no protocolo OAuth 2.0

# Keycloak

[https://medium.com/geekculture/using-keycloak-with-spring-boot-3-0-376fa9f60e0b](https://medium.com/geekculture/using-keycloak-with-spring-boot-3-0-376fa9f60e0b)

[https://blog.4linux.com.br/gerenciando-identidades-e-acessos-com-keycloak-parte-1](https://blog.4linux.com.br/gerenciando-identidades-e-acessos-com-keycloak-parte-1)

[https://blog.4linux.com.br/gerenciando-identidades-e-acessos-com-keycloak-parte-2/](https://blog.4linux.com.br/gerenciando-identidades-e-acessos-com-keycloak-parte-2/)

[https://codejourney.com.br/o-que-e-keycloak/](https://codejourney.com.br/o-que-e-keycloak/)

[https://wjw465150.gitbooks.io/keycloak-documentation/content/index.html](https://wjw465150.gitbooks.io/keycloak-documentation/content/index.html)

## O que é?

- Gestão de identidades para WebApps e RESTful webservices
- Open source
- Utiliza:
	- OpenID Connect
	- SAML 2.0
- Provê:
	- SSO
	- OpenID Connect
	- OAuth 2
	- SAML
	- 2FA
- Os grupos de usuários são divididos em realms
	- Os realms são isolados uns dos outros
	- Por padrão o keycloak vem com o realm master, que é dedicado a usuários com poderes administrativos
- Tem suporte a federação com LDAP / Active Directory.

## Features

> [!note] 🔥
> Listando as menos óbvias

- Identity Brokering - Permite a autenticação com Identity Providers externos usando OpenID Connect ou SAML
- User Federation - Sincronismo de usuários com servidores LDAP ou Active Directory
- Login Flows - Permite auto-registro, recuperação de senha, verificação de e-mail, atualização de senhas, etc.

## Conceitos

- Realms
	- Grupo de usuários
	- Vinculado a uma ou mais aplicações
- Clients
	- Aplicações protegidas pelo Keycloak
- Roles
	- Definem as permissões dentro do sistema
	- Podem ser atribuídas a usuários ou grupo de usuários
	- Tipos
		- Normais → Controle de acesso
		- Composite → Agregação com outras roles
		- Default → Atribuídas a todos os usuários por padrão
- Consent
	- Permite ao usuário (resource owner) decidir compartilhar ou não recursos com o cliente (a aplicação)
	- Consiste em uma tela apresentada após o processo de identificação, informando quais recursos a aplicação está requisitando ao resource server
- Service account
	- Todo cliente tem uma conta de serviço que o permite obter access tokens

## SSL

Keycloak is not set up by default to handle SSL/HTTPS. It is highly recommended that you either enable SSL on the Keycloak server itself or on a reverse proxy in front of the Keycloak server.

## Cache

Keycloak will cache everything it can in memory within the limits of your JVM and/or the limits you’ve configured it for. If the Keycloak database is modified by a third party (i.e. a DBA) outside the scope of the server’s REST APIs or Admin Console there’s a chance parts of the in-memory cache may be stale. You can clear the realm cache, user cache or cache of external public keys (Public keys of external clients or Identity providers, which Keycloak usually uses for verify signatures of particular external entity) from the Admin Console by going to the `Realm Settings` left menu item and the `Cache` tab.

## Uso

- Configurações
	- As configurações podem ser passadas ao Keycloak de 5 formas diferentes:
		- Linha de comando
		- Variáveis de ambiente
		- Arquivos de configuração
		- Arquivo `conf/keycloak.conf`
		- Keystore do java
		- Exemplo

| **Source** | **Format** |
| --- | --- |
| Command line parameters | `--db-url=cliValue` |
| Environment variable | `KC_DB_URL=envVarValue` |
| Configuration file | `db-url=confFileValue` |
| Java KeyStore file | `kc.db-url=keystoreValue` |
- Aplicações e Serviços
	- Bibliotecas chamadas Keycloak Client Adapters
	- Passos para integrar aplicações:
		- 1- Registro do cliente no realm, via:
			- Keycloak Admin Console
			- Client Registrations Service
			- CLI
		- 2- Habilitar OpenID Connect ou SAML na aplicação:
			- Via conector OpenID ou SAML existente
			- Via Keycloak Adapter

## Configuração do adaptador

**bearer-only**

*OPTIONAL*. This should be set to *true* for services. If enabled the adapter will not attempt to authenticate users, but only verify bearer tokens. The default value is *false*.

**expose-token**

*OPTIONAL*. If , an authenticated browser client (via a JavaScript HTTP invocation) can obtain the signed access token via the URL . The default value is *false*.

**enable-basic-auth**

*OPTIONAL*. This tells the adapter to also support basic authentication. If this option is enabled, then *secret* must also be provided. The default value is *false*.

**verify-token-audience**

If set to , then during authentication with the bearer token, the adapter will verify whether the token contains this client name (resource) as an audience. The option is especially useful for services, which primarily serve requests authenticated by the bearer token. This is set to  by default, however for improved security, it is recommended to enable this. See  for more details about audience

**disable-trust-manager**

*OPTIONAL*. If the Keycloak server requires HTTPS and this config option is set to  you do not have to specify a truststore. This setting should only be used during development and **never** in production as it will disable verification of SSL certificates. The default value is .

Fonte: https://www.keycloak.org/docs/latest/securing_apps/

## Authorization Services

- Keycloak suporta diferentes tipos de políticas de autorização:
	- ABAC - Attribute-based
	- RBAC
	- UBAC - User-based
	- CBAC - Context-based
	- Rule-based Access Control
		- Via Javascript
	- Time-based
	- Tipos customizados

# Segurança em Endpoints

- Endpoint → Todo e qualquer dispositivo que se conecte à rede

# Auditoria

## ISO 27001

- Requisitos de SGSI
	- Estabelecer
	- Implementar
	- Operar
	- Monitorar
	- Revisar
	- Manter
	- Melhorar
- Linhas gerais

## ISO 27002

- Código de boas práticas
- Controles

# DLP

- Data Loss Prevention
- Conjunto de tecnologias, políticas e processos
- Controle de acesso
- Monitoramento
- Classificação dos dados

# CASB

- Cloud Access Security Broker
- Proteção de dados corporativos armazenados em nuvem
- Monitoramento de tráfego
- Políticas de segurança
- Detecção de atividades suspeitas
- Criptografia
