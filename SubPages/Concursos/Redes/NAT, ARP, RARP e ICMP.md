---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2024-08-26T18:26:00
Owner:
  - Eduardo Quinalha
---
# NAT

- Estático: faz o mapeamento 1:1 de endereço interno para externo
- Dinâmico: As conversões são realizadas dinamicamente a medida que as requisições internas surgem
- PAT:
	- Quando múltiplos hosts internos fazem uma requisição a um mesmo host externo, a porta de origem é modificada e cada host interno será mapeado em uma porta de saída do endereço externo
	- Desta forma o servidor remoto irá responder para esta mesma porta, e o gateway nat saberá para qual host interno encaminhar a mensagem
	- Processo conhecido também como NAPT ou NAT OVERLOAD
	- Mapeamento do tipo N para 1 ou N para M em que N > M

**- NAT RECONHECE APENAS UDP ou TCP. os processos na Internet não são obrigados a usar o TCP ou o UDP. Se um usuário na máquina A decidir empregar algum novo protocolo de transporte para se comunicar com um usuário na máquina B (por exemplo, no caso de uma aplicação de multimídia), a introdução de um NAT fará a aplicação falhar, porque o NAT não será capaz de localizar corretamente o campo Porta de origem do TCP.**

# NAT reverso e Load Balancing

- Funciona de maneira inversa
- A requisição externa é encaminhada para um host interno
- Possibilita o load balance

# Outros tipos de NAT

- NAT-PT
	- Protocol translations
	- Permite a conversão de protocolos
	- IPv4 → IPv6 e vice-versa
- Twice NAT (2xNAT)
	- Quando existem dois endereços externos válidos
	- Balanceamento de requisições ou regras de saída de acordo com o host de destino

# ARP

- Atua a nível de uma mesma rede
- Conversão IP → MAC
	- de MAC para IP: RARP
- O tamanho do cabeçalho é variável, devido aos campos SHA, SPA, THA e TPA

![[NAT, ARP, RARP e ICMP synced block]]

- Hardware Type
	- 2 Bytes
	- Identifica o tipo de hardware utilizado:
![[Untitled 469.png]]
- Protocol Type
	- Identifica o protocolo usado na camada 3
	- 2 bytes
- HLEN
	- Hardware Addrss Length
- PLN
	- Protocol Address Length
- OP
	- O tipo de requisição que está sendo feita
![[Untitled 470.png]]
- SHA - Sender Hardware Address
- SPA - Sender Protocol Address
- THA - Target Hardware Address
- TPA - Target Protocol Address

# RARP

- Pode ser utilizado para distribuição de endereços IP,
- Era utilizado antes do DHCP
- Depende de um RARP server
- Apenas atribui o IP, ao contrário do DHCP que envia outras informações de configuração também
- É um protocolo da camada de rede, mas atua também na camada de enlace
- Baseado em requisição e resposta

![[Untitled 471.png]]

# ICMP

- Atua na camada de rede de forma complementar ao IP
- Controle de tráfego e status da rede
- Testes e troubleshooting
- suas mensagens trafegam no payload do IPv4, após o cabeçalho
- A identificação é feita pelo campo protocol do cabeçalho e tem o valor 1
- Tem um cabeçalho de 8 bytes, sendo os 4 primeiros fixos
