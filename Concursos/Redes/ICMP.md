---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2024-09-05T15:04:00
Owner:
  - Eduardo Quinalha
---
# Características

- Qualquer computador que utilize o protocolo IP precisa aceitar as mensagens ICMP e alterar o seu comportamento de acordo com o erro relatado.
- Os gateways (roteadores) devem também estar programados para enviar mensagens ICMP quando receberem pacotes que provoquem algum tipo de erro ou detectarem algum problema listado no protocolo ICMP.
- O ICMP é transportado no campo de dados do pacote IP e identificado como **tipo de protocolo “1”** pelo cabeçalho do IP.
- Tipos de mensagens:
	- Um pacote IP não consegue chegar ao seu destino, por exemplo, quando o tempo de vida (TTL) do pacote está expirado (o contador chegou à zero). Esta mensagem é o tempo de vida expirado ou “**time exceeded**”.
	- O roteador não consegue retransmitir os pacotes na frequência adequada, ou seja, o roteador está **congestionado** (mensagem “**source quench**”).
	- O roteador indica uma rota melhor para o host que está enviando pacotes (mensagem de redirecionamento de rota ou “**redirect**”).
	- Quando um host de destino ou rota não está alcançável (mensagem “**destination unreachable**” ou destino inalcançável).
	- Quando o host ou o roteador descobrem um erro de sintaxe no cabeçalho do IP (mensagem “**parameter problem**”).

# Formato

![[Untitled 155.png]]

- **TYPE (8 bits)**: identifica o tipo mensagem, por exemplo, se o valor for 8 é uma requisição (echo request). Se o conteúdo for 0 é uma reposta (echo reply).
- **CODE (8 bits)**: utilizado em conjunto com o campo TYPE para identificar o tipo de mensagem ICMP que está sendo enviada.
- **CHECKSUM (16 bits)**: verifica a integridade do pacote ICMP.
- **MESSAGE CONTENTS (Tamanho Variável)**: contém o conteúdo da mensagem ICMP.

## Principais tipos de mensagens

- **0: Solicitação de eco**
- **3: Destino inacessível**
- 4: Extinção de Fonte
- 5: Redirecionar
- **8: Resposta de eco**
- 11: Tempo Excedido
- 12: Problema de parâmetro
- 30: Traceroute
