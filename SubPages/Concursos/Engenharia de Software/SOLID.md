---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2024-10-01T20:02:00
Owner:
  - Eduardo Quinalha
---
# Princípios SOLID

- Princípios que visam principalmente o **baixo acoplamento**
- Facilitam manter, entender, sustentar, escalar e estender software
- Aplicados a OO
- SOLID Significa
	- **S**ingle Responsability
	- **O**pen/Closed
	- **L**iskov Substitution
	- **I**nterface Segregation
	- **D**ependency Inversion

## Single Responsability

- Uma classe deve ter uma única responsabilidade
- O objetivo desse princípio é separar comportamentos para que, se surgirem bugs como resultado de sua alteração, isso não afete outros comportamentos não relacionados.

## Open/Closed

- Classes devem ser **abertas para expansão** mas **fechadas para modificação**
- Se você deseja que a classe execute mais funções, a abordagem ideal é adicionar às funções que já existem e, não, alterá-las.

## Liskov Substitution

- Se **S** é um subtipo de **T**, então objetos do tipo **T** podem ser substituídos por **S** sem alterar as propriedades desejáveis do programa
- A classe-filha deve ser capaz de fazer tudo o que a classe-pai pode fazer ou pode entregar um resultado do **mesmo tipo.** 

## Interface Segregation

- Uma classe deve executar apenas as ações necessárias para cumprir seu papel.
- Qualquer outra ação deve ser removida completamente ou movida para outro lugar se puder ser utilizada por outra classe no futuro

## Inversão de Dependência

- Módulos de alto nível não devem depender de módulos de baixo nível: Ambos devem depender da abstração
- Abstrações não devem depender de detalhes: Detalhes devem depender de abstrações
- Tanto a classe quanto a interface não devem saber como a ferramenta funciona. No entanto, a ferramenta precisa atender à especificação da interface
