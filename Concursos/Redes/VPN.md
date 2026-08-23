---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2024-10-09T17:02:00
Owner:
  - Eduardo Quinalha
---
# Tipos

- SSL
	- Baseados em Web
- IPsec
	- Camada 3
	- Entre filiais
- PPTP
	- Atualmente considerado pouco seguro, pois baseia-se em chaves de 128 bits
	- considerado leve, rápido e de fácil implementação
	- Normalmente depende do IPSEC em camadas superiores para sua completa implementação
	- Camada 2
- L2TP
	- Frequentemente utilizado em conjunto com IPSec
	- Baseado nos protocolos L2F e PPTP
	- **Não garante confidencialidade, por este motivo utiliza IPSEC na camada superior**
	- Camada 2
	- Utiliza a porta TCP/UDP 1701
	- Autenticação via PAP ou CHAP
- MPLS
	- Permite a criação de circuito virtual dedicado, porém sem confidencialidade dos dados, apenas isolamento de tráfego
- SSTP
	- Proprietário da Microsoft
	- Utiliza SSLv3, portanto usa a porta 443/TCP, evitando problemas com firewalls
	- Integração completa com Windows
