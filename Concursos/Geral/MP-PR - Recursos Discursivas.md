---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2025-04-29T14:41:00
Owner:
  - Eduardo Quinalha
---
# Questão 1

No aspecto 1, o candidato atendeu parcialmente ao quesito d apresentando três estratégias de mitigação para os desafios apresentados no segundo parágrafo do texto. O uso de um modelo de consistência mais rígido (linhas 12 e 13), como a consistência forte [1] e [2], garante transações atômicas, mitigando o atraso de consistência gerado pelo modelo de consistência eventual, desafio que foi mencionado na linha 8. A segunda estratégia fornecida pelo candidato foi o uso de Frameworks ORM (linha 13) que visam mitigar o desafio levantado em relação à diversidade de linguagens de manipulação (linha 9). Exemplos incluem Mongoose para MongoDB e Spring Data para vários bancos NoSQL [3]. Já com relação ao desafio de controle de integridade (linhas 10 e 11), foi apresentando como estratégia o uso de controles de integridade na aplicação (linhas 13 e 14) pois muitos bancos NoSQL não oferecem suporte nativo para restrições como chaves estrangeiras, verificações de integridade ou unicidade e outros objetos utilizados para validação e garantia de integridade dos dados [4], que são comuns em bancos de dados relacionais. Ao invés disso, bancos de dados NoSQL priorizam desempenho e escalabilidade em detrimento destas características e, quando for necessário, tais controles deverão ser implementados no lado da aplicação [5]. Sendo assim, justifica-se requerer a atribuição de 3 pontos ao quesito, referente às três estratégias levantadas pelo candidato.

Referências:

[1] [https://learn.microsoft.com/pt-pt/azure/cosmos-db/consistency-levels#strong-consistency](https://learn.microsoft.com/pt-pt/azure/cosmos-db/consistency-levels#strong-consistency)

[2] [https://cloud.google.com/datastore/docs/articles/balancing-strong-and-eventual-consistency-with-google-cloud-datastore?hl=pt-br](https://cloud.google.com/datastore/docs/articles/balancing-strong-and-eventual-consistency-with-google-cloud-datastore?hl=pt-br&authuser=0)

[3] [https://docs.spring.io/spring-boot/docs/2.0.x/reference/html/boot-features-nosql.html](https://docs.spring.io/spring-boot/docs/2.0.x/reference/html/boot-features-nosql.html)

[4] [https://cloud.google.com/discover/what-is-nosql?hl=pt-BR](https://cloud.google.com/discover/what-is-nosql?hl=pt-BR&authuser=0)

[5] [https://dzone.com/articles/data-integrity-in-nosql-and-java-application-using](https://dzone.com/articles/data-integrity-in-nosql-and-java-application-using)

# Questão 2

No aspecto 1, item b, o candidato atendeu aos requisitos solicitados no subitem i. A resposta aborda elementos do Design Thinking que contribuem para a inovação: "Levantar diversas possíveis soluções" (linha 4) indica a exploração de múltiplas ideias fomentando a criatividade. Já em "Uso de métodos como o de pensamentos divergentes" (Linha 5) faz-se uma referência à busca por soluções não convencionais, que é um aspecto fundamental da inovação. Por fim, em "Etapa de prototipação, na qual as ideias são testadas" (linha 6) demonstra o aspecto prático e iterativo do Design Thinking, permitindo a exploração tangível de soluções inovadoras. Neste sentido, justifica requerer a aplicação da nota máxima 2,0.
