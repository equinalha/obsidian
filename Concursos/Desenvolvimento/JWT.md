---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2024-09-05T10:41:00
Owner:
  - Eduardo Quinalha
---
[https://jwt.io/introduction](https://jwt.io/introduction)

![[JWT.png]]

# Características

> [!note] 🔥
> O propósito não é esconder dados (criptografia), mas sim garantir a autenticidade destes dados
No entanto, o JWT pode ser criptografado (tanto payload como header)

- Padrão RFC 7519
- Compacto, pode ser verificado, confiável
- Assinado com HMAC, RSA ou ECDSA
- Assinado, validado com chave pública
- Integridade e não repúdio
- Possui um TTL
- Foco em autorização e troca de informações

# Estrutura

- Header
	- Tipo de token
	- algoritmo de assinatura
- Payload
	- Claims → Informações a respeito do usuário
	- Tipos
		- registered / reserved
			- Contém claims pré-definidas, não obrigatórias, mas recomendadas
				- `iss (issuer), `
				- `exp (expiration time), `
				- `sub (subject), `
				- `aud (audice)`
				- `iat (issued at)`
				- `jti (JWT ID)`
		- public
			- claims customizadas
		- private
			- claims customizadas e específicas de uma organização
			- Utilizado para troca de informações entre partes
- Signature
	- Assinatura utilizada para validação do token
	- A assinatura é feita tomando-se como entrada o header codificado em base64, o payload codificado em base64 e a chave / secret do emissor
```json
HMACSHA256(
  base64UrlEncode(header) + "." +
  base64UrlEncode(payload),
  secret)
```
