---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2024-08-26T18:26:00
Owner:
  - Eduardo Quinalha
---
<!-- Column 1 -->
> [!note]+ ## Topologia Lógica x Topologia Física
> - **Física →** Como os nós são conectados
> - **Lógica →** Como os dados são trafegados
>     - Varia conforme o tipo de equipamento utilizado
>     - Por exemplo um hub configura uma topologia física em estrela, mas logicamente é um barramento
> - Podem ser iguais ou não

- **Barramento**
	- Difusão
	- Pode utilizar formas de controle de acesso ao meio centralizado ou descentralizado para evitar colisões
	- Escalável até o limite de capacidade do barramento
	- Menos seguro (informação disponível para todos os nós)
	- Tolerância a falhas (uma falha em um dispositivo conectado ao barramento, não afeta os demais)

<!-- Column 2 -->
![[Untitled 489.png]]

<!-- Column 1 -->
![[Untitled 490.png]]

<!-- Column 2 -->
- **Anel**
	- Conexões ponto a ponto
	- Dependente dos nós intermediários
	- Não escalável (a medida que cresce, são necessários mais saltos, ficando mais lento)
	- Não seguro (a informação passa pelos nós intermediários)
	- Tolerante a falhas (na falha de um nó, o dado pode trafegar no outro sentido - Rotas tolerantes)
	- Utiliza tokens para acesso ao meio
	- É possível a implementação de anel bidirecional e duplo (lembrar da infiNet)

<!-- Column 1 -->
- **Estrela**
	- Conexão ponto a ponto com um comutador central
	- Necessita de controle de acesso ao meio (no caso do HUB. Para switch não há necessidade)
	- Possibilita gerência da rede
	- Boa tolerância a falhas, porém possui um ponto crítico (comutador)
	- A expansão dependente da capacidade do nó central

<!-- Column 2 -->
![[Untitled 491.png]]

<!-- Column 1 -->
![[Untitled 492.png]]

<!-- Column 2 -->
- **Mesh / Malha**
	- Interconexão ponto a ponto entre alguns nós
	- Pouco escalável
	- Excelente tolerância a falhas
	- Full mesh → interconexão entre todos os dispositivos


<!-- Column 1 -->
- **Árvore**
	- Hierarquização entre os concentradores
	- Derivação de uma rede estrela
	- Padrão mais utilizado atualmente
	- Boa tolerância a falhas
	- Boa escalabilidade

<!-- Column 2 -->
![[Untitled 493.png]]