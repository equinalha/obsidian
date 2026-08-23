---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2024-10-09T17:06:00
Owner:
  - Eduardo Quinalha
---
[https://www.youtube.com/watch?v=6fKIpkKtiEs](https://www.youtube.com/watch?v=6fKIpkKtiEs)

# SSL/TLS

- Se posiciona em uma **camada intermediária** entre as camadas de aplicação e transporte da arquitetura TCP/IP
- Objetivos
	- Autenticação entre clientes e servidores
	- Integridade dos dados
	- Garantia de confidencialidade
- SSL não é um protocolo simples e único, mas sim um conjunto de protocolos auxiliares que atuam em conjunto
- Esse conjunto de protocolos pode ser dividido em **duas camadas**
	- Camada de segurança e integridade dos dados: **SSL Record**
	- Camada de conexão SSL: **SSL Handshake Protocol, SSL Change Cipher Spec Protocol e SSL Alert Protocol**

## Etapas

- O estabelecimento de uma conexão SSL se dá em etapas

![[Untitled 472.png]]

- Inicia com o **Handshake Protocol**
	- Negociação dos algoritmos
		- Definição do algoritmo que, suportado por ambos, será utilizado
		- A escolha sempre tenderá pelo mais robusto
	- Troca de chaves e autenticação
		- Utiliza-se criptografia assimétrica como RSA ou DH
		- Aplica-se conceito de certificado digital
	- Encriptação simétrica e autenticação das mensagens
		- A partir deste ponto, utiliza-se a criptografia simétrica

![[Untitled 473.png]]

# TLS

- TLS e SSL não são totalmente compatíveis
- O TLS tem a capacidade de trabalhar em portas diferentes e usa algoritmos de criptografia mais robustos como o **HMAC**, enquanto o SSL suporta apenas o MAC
- O TLS, quando utilizado em infraestrutura de chaves públicas, pode ser utilizado por uma **autoridade intermediária**, não necessitando recorrer à raiz de um Autoridade de Certificação como o SSL.

### TLS 1.2

- Troca de chaves - Criptografia Assimétrica
	- RSA
	- DH
	- DHE
- Criptografia simétrica
	- AEAD
	- CBC
	- **RC4**
	- **3DES**
	- **AES 256 com SHA-256**

### TLS 1.3

- Troca de chaves - Criptografia Assimétrica
	- DHE
- Criptografia simétrica
	- AEAD
	- **AES 256 com SHA-256**

# mTLS

- Protocolo de autenticação mútua
- Extensão do TLS que adiciona autenticação mútua às duas pontas da conexão.

![[Untitled 474.png]]

- Aplicações
	- Integrações de API: O mTLS pode ser usado para proteger as comunicações entre APIs de diferentes organizações.
	- [Webhooks](/147ed608be3543c39cb1f53f49f3a10c)
	- Segurança de aplicativos: O mTLS pode ser usado para proteger as comunicações entre aplicativos e servidores.
	- Segurança de rede: O mTLS pode ser usado para proteger as comunicações entre dispositivos em uma rede.

# OpenSSL

- Código aberto
- Suporta também o TLS (apesar do nome)
- Suporta uma grande gama de algoritmos de criptografia simétrica, assimétrica e funções de HASH

# Pilha de protocolos SSL

Na verdade, SSL não é apenas um único protocolo, mas uma pilha, posicionando diferentes cabeçalhos na mensagem:

![[SSL-TLS synced block]]

# SSL Handshake Protocol

![[Untitled 476.png]]

## Fase 1:

- ClientHello
	- Enviada pelo cliente. Contém as seguintes informações
		- Maior versão SSL suportada pelo cliente
		- SessionID
		- Parâmetros de algoritmos de cifra suportados
		- Lista de métodos de compressão suportados
- ServerHello
	- Enviada pelo servidor
		- Maior versão SSL suportada pelo cliente
		- SessionID
		- Algoritmo criptográfico selecionado da lista enviada pelo cliente
		- Algoritmo de compressão selecionado da lista enviada pelo cliente

## Fase 2:

- Server Certificate
	- Servidor envia seu certificado para o cliente que fará autenticação
	- Se o algoritmo for Diffie-Hellman, não será necessária autenticação
- Server Key Exchange
	- Opcional
- Client Certificate Request
	- Opcional
- Server Hello Done

## Fase 3:

- Client Certificate
	- Opcional
- Client Key Exchange
	- Baseado no algoritmo de criptografia escolhido
- Certificate Verify
	- Somente se o cliente foi solicitado a enviar seu certificado para o servidor

## Fase 4:

- Mensagem 1: Client → Server
	- Change Cipher Spec
	- Client Handshake finished
- Mensagem 2: Server → Client
	- Change Cipher Spec
	- Server Handshake finished

# SSL Change Cipher Spec Protocol

- O mais simples dos protocolos. Tem apenas 1 byte com o valor 1
- Apenas uma mensagem
- Copia o pending state para current state, atualizando a suite de criptografia a ser usada pela conexão

# SSL Alert Protocol

- Pode ser enviado pelo cliente ou servidor
- Alerta sobre a ocorrência de erros
- Possibilita interromper a conexão
- Ocupa 2 bytes
	- Byte 1:
		- 1: Warning
		- 2: Fatal Error
	- Byte 2:
		- Especificação do erro ou alerta

# SSL Record Protocol

- Transmissão de dados criptografados
- Encapsulamento de dados
- Confidencialidade dos dados
- Integridade dos dados
- Funcionamento
![[SSL-TLS synced block 1]]
![[SSL-TLS synced block 2]]
- O campo Content Type identifica o tipo de mensagem contida no SSL Record
	- CHANGE_CIPHER_SPEC
	- ALERT
	- HANDSHAKE
	- APPLICATION_DATA
- MAC
	- Message Authentication Code

# SSL Offloading

[https://aboutssl.org/what-is-ssl-offloading/](https://aboutssl.org/what-is-ssl-offloading/)

- Processo que ocorre em uma máquina posicionada entre o cliente (browser) e o servidor
- Pode ser um gateway, load balancer, ou proxy
- Pode ser utilizado para desonerar o servidor de aplicação do trabalho de lidar com o overhead do SSL e acelerar a comunicação
- Pode também ser utilizado para proteção, fazendo análises dos dados enviados, antes que eles cheguem ao servidor da aplicação
- Utiliza-se de certificados Wildcard, ou seja, certifica todos os subdomínios do domínio pai
- Existem dois tipos:
	- **SSL Termination**
		- Termina a conexão SSL
		- Repassa os dados descriptografados ao servidor de aplicação
		- Usado para reduzir a carga do servidor de aplicação e acelerar a troca de dados
![[Untitled 479.png]]
	- **SSL Bridging**
		- Os dados são descriptografados no load balancer e depois criptografados novamente para enviar ao servidor de aplicação
		- Utilizado principalmente para examinar os dados quanto a ameaças como spywares, virus, SQL Injection, DDoS, etc.
![[Untitled 480.png]]

# SSL vs TLS - Diferenças

## Regras de autenticação

- **SSL:** O SSL oferece autenticação unilateral ou mútua. Na autenticação unilateral, apenas o servidor é autenticado. Na autenticação mútua, tanto o cliente quanto o servidor são autenticados.
- **TLS:** O TLS oferece autenticação unilateral, mútua e opcional. Na autenticação opcional, o cliente pode escolher se deseja se autenticar.
