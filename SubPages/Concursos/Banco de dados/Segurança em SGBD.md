---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2024-08-26T18:07:00
Owner:
  - Eduardo Quinalha
---
# Controle de Inferência

O Controle de Inferência em um Sistema Gerenciador de Banco de Dados (SGBD) é um conjunto de mecanismos que garantem a confidencialidade dos dados, protegendo-os contra inferências e acessos indevidos.

**1. Conceito:**

A inferência ocorre quando um usuário, a partir de informações acessíveis, consegue deduzir dados confidenciais que não foram explicitamente disponibilizados a ele. O Controle de Inferência visa prevenir essa dedução, controlando o acesso a informações e limitando a quantidade de dados que um usuário pode visualizar.

**2. Tipos de Controle de Inferência:**

- **Controle de acesso:** Define quem tem acesso a quais dados e quais operações podem ser realizadas.
- **Controle de visualização:** Limita a quantidade de dados que um usuário pode visualizar em uma consulta.
- **Controle de agregação:** Restringe como os dados podem ser agregados, impedindo a inferência de informações confidenciais a partir de estatísticas.
- **Criptografia:** Protege os dados armazenados no banco de dados, tornando-os ilegíveis para usuários não autorizados.

# Controle de Fluxo

- Impedem que as informações fluam de modo a alcançarem usuários não autorizados.
- É necessário evitar que canais secretos ou percursos para as informações fluírem implicitamente em caminhos que violam a política de segurança de uma organização.

# Grant

- Quando utilizado com` WITH GRANT OPTION` permite que o usuário que recebeu o privilégio propague esta permissão
- Caso seja revogada a permissão do primeiro usuário, a revogação ocorrerá em cascata para os demais usuários que receberam a autorização do primeiro
