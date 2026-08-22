---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2024-08-26T18:26:00
Owner:
  - Eduardo Quinalha
---
- **CSMA / CD**
	- **Ethernet (IEEE 802.3)**
	- **Não previne a colisão, apenas detecta**
	- 1 - O nó inicialmente escuta para verificar se o meio está livre
	- 2 - Inicia a transmissão “escutando” o meio ao mesmo tempo
	- Detecta amplificações do sinal (interferência construtiva) → Colisão
	- Quando detectado a colisão, faz o **backoff**
		- Transmite um sinal jam (sinal com amplitude maior que o padrão) para sinalizar a todos os nós que uma colisão foi detectada
		- Aqueles nós que desejam voltar a transmitir vão aguardar um tempo aleatório
- **CSMA / CA**
	- **Wireless (IEEE 802.11)**
	- **Prevenção de colisão**
	- 1 -  O dispositivo escuta o meio a fim de identificar se está livre
	- 2 - Antes de iniciar a transmissão, envia um pacote informando que irá utilizar o meio durante X segundos
	- 3 - As demais estações aguardarão o tempo informado antes de tentar transmitir