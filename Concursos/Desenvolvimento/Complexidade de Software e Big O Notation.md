---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2024-12-01T15:54:00
Owner:
  - Eduardo Quinalha
---
- Se não for especificado, a notação sempre levará em conta o pior caso

![[Untitled 744.png]]

# Classes de Complexidade

## Classe P

- É o conjunto de problemas que podem ser resolvidos em tempo polinomial por um algoritmo determinístico.
- Se um problema pertence à classe P, existe um algoritmo eficiente que pode resolver o problema em um tempo razoável (polinomial) à medida que o tamanho da entrada cresce.

## Classe NP

- Significa "Nondeterministic Polynomial time" (tempo polinomial não-determinístico). 
- É o conjunto de problemas para os quais uma solução proposta pode ser verificada em tempo polinomial por um algoritmo determinístico, mesmo que não se saiba como encontrar a solução em tempo polinomial.
- Se você tem uma "proposta de solução", pode verificar rapidamente (em tempo polinomial) se essa solução está correta.

## NP-Completo

- Um problema é dito NP-Completo se ele satisfaz duas condições:
	1. **Pertence à classe NP**: Ou seja, se você tiver uma solução candidata para o problema, você pode verificar se ela é correta em tempo polinomial.
	2. **É tão difícil quanto qualquer outro problema em NP**: Isso significa que qualquer problema em NP pode ser transformado (ou "reduzido") em tempo polinomial para este problema específico. Se alguém descobrir um algoritmo de tempo polinomial para resolver qualquer problema NP-Completo, então esse algoritmo poderia ser usado para resolver todos os problemas em NP em tempo polinomial. Esse processo de transformação é chamado de **redução polinomial**.
- Problemas NP-Completos são considerados os problemas mais difíceis dentro da classe NP