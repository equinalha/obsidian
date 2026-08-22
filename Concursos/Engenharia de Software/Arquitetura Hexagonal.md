---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2024-10-01T17:15:00
Owner:
  - Eduardo Quinalha
---
# Objetivos

- Favorecer a reusabilidade de código, alta coesão, baixo acoplamento e independência de tecnologia
- Divide as classes em dois grupos
	- Classes de domínio
	- Classes relacionadas com infraestrutura, tecnologias e interfaces com sistemas externos (inclusive BD)
- As classes de domínio não devem depender destas classes (tecnologia, infraestrutura e sistemas externos)
- A comunicação entre as classes dos dois grupos é feita por meio de adaptadores

![[Untitled 657.png]]

## Adaptadores e Portas

> [!note] 🔥
> Cada face do hexágono visa representar um motivo para o sistema se comunicar com o mundo externo. Exemplos: Persistência, interfaces com o usuário

### Portas

- representam os pontos de **entrada e saída da aplicação**
- Definem interfaces através das quais o **núcleo da aplicação interage com o mundo exterior.**
- permitem a comunicação com componentes externos, como** interfaces de usuário, bancos de dados, serviços externos**, entre outros.
- Tipos:
	- **Primárias**
		- São **pontos de entrada no sistema.**
		- interfaces que permitem a interação entre o núcleo da aplicação e os "drivers" ou componentes que iniciam a execução de casos de uso da aplicação.
		- podem ser invocados por um **controlador da interface de usuário** ou por um **serviço externo.**
	- **Secundárias**
		- São **pontos de saída do sistema.**
		- interfaces que o núcleo da aplicação usa para se comunicar com serviços externos ou recursos que ele depende para funcionar, como bancos de dados, APIs externas, ou sistemas de mensageria

### Adaptadores

- implementações concretas que **conectam o núcleo da aplicação às portas**. 
- traduzem ou adaptam os pedidos e respostas entre o núcleo e o mundo exterior.
- Cada tipo de interface (mobile, web, sistema) vai ter um adaptador específico para conversar com o núcleo
- Tipos
	- **Primários**
		- Adaptam os dados e chamam as portas primárias.
		- implementam as portas primárias e são responsáveis por receber os inputs do mundo externo e passá-los para o núcleo da aplicação
	- **Secundários**
		- traduzem as chamadas do núcleo para o formato apropriado e interagem com os serviços ou recursos necessários.
		- implementam as portas secundárias e conectam o núcleo da aplicação aos recursos externos. 

![[Untitled 658.png]]