---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2025-04-29T14:41:00
Owner:
  - Eduardo Quinalha
---
# Características

- Amplamente usado para implementar protocolos de comunicação segura, como SSL/TLS
- Fornece ferramentas para criptografia, assinatura digital, geração de chaves e outras operações relacionadas à segurança de dados
- É dividido em duas bibliotecas que desempenham papéis complementares, `libcrypto `e `libssl`
	- `**libcrypto**`
	-  `**libssl**`

## Destaques da versão 3.0

- **Provedores de Criptografia**
	- encapsulam implementações criptográficas (como algoritmos de cifra, hashes, funções de chave) 
	- podem ser carregados ou descarregados conforme necessário
- **Provedor de FIPS**
	- Federal Information Processing Standards
	- Atende às exigências de conformidade com os padrões de segurança para criptografia usados por organizações governamentais e outras que lidam com informações sensíveis
- OpenSSL 3.0 foi projetado para ser extensível para suportar algoritmos resistentes à computação quântica, o que é uma área importante para o futuro

# Bibliotecas

## Libcrypto

- Principal biblioteca do OpenSSL
- Criptografia geral
- Capacidades criptográficas de** ****baixo nível**
- Fornece** algoritmos e primitivas** criptográficas
- Não está restrita a protocolo de comunicação
- Funcionalidades da libcrypto:
	- **Algoritmos de criptografia**: Implementa diversos algoritmos de cifra simétrica e assimétrica, como AES, DES, RSA, DSA, ECC (Criptografia de Curvas Elípticas), etc.
	- **Hashing e HMAC**: Suporte para funções de hash, como SHA-256, SHA-3, MD5, e funções de autenticação de mensagens, como **HMAC** (Hash-based Message Authentication Code).
	- **Geração de números aleatórios**: Inclui funções para a **geração de números aleatórios criptograficamente seguros.**
	- **Funções de assinatura e verificação**: Utilizadas para assinar digitalmente dados e verificar essas assinaturas.
	- **Gerenciamento de chaves**: Ferramentas para geração, armazenamento, e manipulação de **chaves criptográficas** (privadas, públicas e simétricas).
	- **Codificação/decodificação**: Funções para lidar com formatos de dados codificados como **Base64 e ASN.1**.
	- **Criação de certificados**: Utilizado para** criar e manipular certificados X.509 e PKCS#12**.

## LibSSL

- Biblioteca de nível mais alto responsável pela implementação dos **protocolos SSL (Secure Sockets Layer) e TLS (Transport Layer Security)**
- Utiliza as funcionalidades criptográficas fornecidas pela libcrypto para estabelecer conexões seguras
- Funcionalidades da libssl:
	- **Protocolo TLS/SSL**: A libssl implementa os protocolos SSL e TLS, que permitem a comunicação segura entre clientes e servidores.
	- **Estabelecimento de Handshake**: Gerencia o processo de handshake do TLS/SSL, que envolve a negociação dos parâmetros de segurança (cifras, versões do protocolo, etc.) entre as partes e a troca de chaves para criptografia da comunicação.
	- **Criptografia e Descriptografia de Fluxos de Dados**: Depois de estabelecida a conexão segura, a libssl criptografa e descriptografa os dados transmitidos usando chaves derivadas durante o handshake.
	- **Verificação de Certificados**: A libssl verifica a autenticidade de certificados digitais (normalmente usados para verificar a identidade de servidores web), utilizando as funções de libcrypto para isso.
	- **Suporte a SNI (Server Name Indication)**: Permite a hospedagem de múltiplos domínios SSL no mesmo endereço IP.
	- **Compatibilidade com várias versões de TLS**: A libssl suporta diversas versões do protocolo, incluindo TLS 1.2 e TLS 1.3 (a mais recente e segura).

# Provedores

- Um provedor para o OpenSSL é um agrupamento de implementações de algoritmos (por exemplo, criptografia simétrica)
- Para utilizar um dado algoritmo é necessário ter carregar pelo menos um provedor que contenha sua implementação
- É possível obter provedores adicionais de terceiros
- Provedores podem ser fornecidos em módulos carregáveis separados
- O carregamento de um provedor pela aplicação é um processo custoso.
- Por isso, normalmente é carregado uma vez durante o ciclo de vida e mantido na memória.
- Exemplo de provedores
	- **Base provider**
		- É parte da `libcrypto`
		- Contém algoritmos para codificar e decodificar chaves OpenSSL
		- Alguns algoritmos não são compatíveis com as especificações FIPS, porém contém os algoritmos desta
	- **FIPS provider**
		- Contém algoritmos validados pelo padrão FIPS
		- Necessita também do carregamento do provedor base
	- **Legacy provider**
		- Necessita de carregamento explícito
		- Contém implementações consideradas inseguras
	- **Null provider**
		- Não contém algoritmos
		- Como o provedor padrão é carregado automaticamente em algumas situações, especificar o provedor como `null `pode prevenir este fato
