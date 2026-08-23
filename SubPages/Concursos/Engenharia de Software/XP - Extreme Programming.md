---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2026-08-05T17:21:00
Owner:
  - Eduardo Quinalha
---
# XP - Extreme Programming

- O desenvolvimento é feito de forma **incremental** 
- o software é construído em pequenas partes que são continuamente melhoradas e expandidas.
- Novas versões do software são lançadas **frequentemente**, até **várias vezes ao dia.**
- Ciclo de lançamento ou release **muito curto e iterativo**, com frequência em torno de **duas semanas**
- O comprometimento com prazos de releases é **estrito**
- Se um problema de desenvolvimento ameaçar o cumprimento do prazo de entrega, a equipe de desenvolvimento é instruída a entrar em contato com o cliente para decidir sobre a remoção ou modificação de funcionalidades, em vez de adiar o lançamento.
- Recomenda que as boas práticas sejam levadas ao extremo:
	- **Testar é bom?** Então vamos testar toda hora (prática de TDD).
	- **Integrar é bom? **Então vamos integrar toda hora (prática de integração contínua).
	- **Melhorar o código é bom?** Então vamos melhorar o código sempre que possível (prática de refactoring).
- Equipes **pequenas e médias**
- Requisitos vagos
- Conjunto de práticas focadas em engenharia de software
- parte do princípio de que o código-fonte é a melhor documentação,
- **É mais técnico que o Scrum**
- Focado na programação em si
- Revisar o código o máximo possível** - Pair Programming**
- Testar o máximo possível **- Testes funcionais, TDD**
	- A XP enfatiza a importância da **engenharia de software** e adota práticas como o **Desenvolvimento Orientado a Testes (TDD - Test-Driven Development)**
- Os testes de aceitação (ou testes de cliente) são **especificados pelo cliente**
- **Refactoring**
- **Integração contínua**
- Projeto o mais simples possível

## Práticas

- As práticas do XP estão organizadas em 4 grupos (ou arcabouços):
	- Práticas de Planejamento
	- Práticas de Projeto (Design)
	- Práticas de Codificação
	- Práticas de Testes

### Práticas de Planejamento

- **Planejamento incremental**
	- As histórias a serem incluídas em um release são determinadas pelo tempo disponível e sua prioridade relativa
	- As histórias são divididas em tarefas
- **Pequenas Releases**
	- Entregas em pequenos releases
	- Confiança ao cliente sobre o progresso real
	- Um conjunto mínimo útil de funcionalidades que agrega valor ao negócio é desenvolvido primeiro
	- Releases do sistema adicionam funcionalidades incrementalmente em relação ao primeiro release
- **Reuniões em pé**
	- Standup meetings
	- Rápidas e diárias
	- Discutir apenas o essencial
- **Cliente sempre presente**
	- Disponível em tempo integral para a equipe

### Práticas de Projeto

- **Projeto simples**
	- Código** simples o suficiente** para entregar a funcionalidade e passar pelos testes necessários
	- KIS - Keep It Simple
- **Metáfora**
	- Uma história que todos podem contar acerca de como o sistema funciona
	- Facilita a comunicação entre os interessados
- **Design Incremental**
	- O design do sistema evolui com o tempo, conforme as necessidades mudam. 
	- Ele é constantemente revisado e refinado.
- **Refatoração**
	- Constante melhoria do código
	- Simples, genérico, **removendo redundâncias e duplicidades**
	- Não deve alterar o comportamento

### Práticas de Codificação

- **Programação em pares**
	- Programadores trabalhando em pares, validando mutuamente o trabalho feito
	- Literalmente na mesma máquina
- **Propriedade coletiva do código**
	- Todos são responsáveis pelo código
	- Qualquer pessoa está autorizada a efetuar mudanças sobre ele (da equipe)
- **Integração contínua**
	- Depois de qualquer integração, todos os testes unitários do sistema devem ser realizados
- **Padrão de codificação**
	- A equipe adota padrões de codificação consistentes para facilitar a leitura e manutenção do código
- **Jogo de Planejamento**
	- Clientes e desenvolvedores colaboram para criar o plano de desenvolvimento, 
	- priorizando as funcionalidades mais importantes.
- **Ritmo sustentável**
	- Cada trabalhador trabalha 40h por semana, no máximo
- **Time Coeso**
	- Pessoas engajadas
	- Multidisciplinares

### Práticas de Teste

- **TDD**
	- Testes automatizados
	- Escritos antes da funcionalidade ser implementada
- **Testes de Aceitação**
	- Clientes e desenvolvedores colaboram para definir testes que representam a aceitação das funcionalidades pelo cliente.

## Valores / Princípios

- **Comunicação**
	- Face a face
	- Tanto entre desenvolvedores quanto com os clientes
- **Simplicidade**
	- Criação do design mais simples possível para atender aos requisitos atuais
	- Facilita mudanças quando forem necessárias
- **Feedback**
	- Do cliente, do sistema, da equipe
	- Testes automatizados
	- Entregas frequentes
- **Coragem**
	- Disposição a fazer mudanças no projeto, mesmo quando isso é difícil
	- Mudanças de requisito, refatoração, abandonar práticas que não estão funcionando
- **Respeito**
	- Equipe, clientes, usuários

# Histórias de Usuário

- São artefatos de desenvolvimento utilizados em sistemas geridos segundo metodologias ágeis.
- Elas devem ser concluídas em até uma iteração. 
- Uma história de usuário que não caiba em uma iteração deverá ser decomposta em duas ou mais histórias menores de modo que caibam em uma iteração.
- O cliente atribui um valor (prioridade) à história baseando-se no valor de negócio global do recurso/função.
- A estimativa para uma história de usuário é feita pelos **membros da equipe (todos participam)**
- No entanto, muitas vezes **quem atribui a estimativa é o Product Owner**
- Esta estimativa é feita em **Story Points**
- User Stories não correspondem exatamente aos casos de uso, pois estes são normalmente mais detalhados e técnicos, além de serem utilizados de formas diferentes
- User Stories definem o que será desenvolvido, não como
- User Stories  não são requisitos, os requisitos são derivados a partir delas.
- Cada história do usuário pode ser associada a um ou mais critérios de aceitação, que são usados para confirmar que a história foi implementada corretamente.

# Ciclo de vida

![[image 74.png]]

- As fases não são estritamente sequenciais e podem ocorrer simultaneamente ou se sobrepor
- O teste por exemplo, ocorre simultaneamente ao desenvolvimento

![[XP.png]]