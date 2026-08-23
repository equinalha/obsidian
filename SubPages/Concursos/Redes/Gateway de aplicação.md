---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2024-09-05T15:04:00
Owner:
  - Eduardo Quinalha
---
# O que é?

- Gateway de rede tradicional faz o direcionamento do tráfego baseado nas camadas 3 e 4
- Gateway de aplicação analisa também atributos da camada de aplicação, especialmente HTTP
- Pode encaminhar o tráfego de acordo com a URL

![[Untitled 466.png]]

- O encaminhamento pode ser conhecido como balanceamento de carga da camada de aplicação

# Como funciona

![[Untitled 467.png]]

- Pode funcionar em conjunto com um WAF
- Exerce função de load balancer
- Insere cabeçalhos adicionais na requisição http
	- Exemplos:
		- x-forwarded-for
		- x-forwarded-port
		- x-forwarded-proto