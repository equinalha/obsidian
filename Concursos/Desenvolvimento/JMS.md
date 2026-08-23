---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2024-08-26T18:00:00
Owner:
  - Eduardo Quinalha
---
O JMS é utilizado para comunicação assíncrona em sistemas distribuídos e suporta dois modelos de mensagens: ponto-a-ponto (queue) e publicação/assinatura (topic).

O **JMSContext**, introduzido na versão JMS 2.0, é um artefato que simplifica a interação com a API do JMS. Antes do JMS 2.0, a utilização do JMS envolvia várias etapas para criar uma conexão e uma sessão separadamente, além de criar produtores e consumidores de mensagens. Isso tornava o código mais complexo e verboso.

Com o advento do **JMSContext**, agora temos a combinação de uma conexão e uma sessão em um único objeto. Isso simplifica a criação de produtores (*message producers*) e consumidores (*message consumers*), pois podemos realizar essas operações diretamente através do JMSContext. Dessa forma, a complexidade do código é reduzida e a legibilidade aumentada.
