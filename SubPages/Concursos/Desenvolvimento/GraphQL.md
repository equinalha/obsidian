---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2024-08-26T18:04:00
Owner:
  - Eduardo Quinalha
---
# O que é

- Linguagem de consulta e manipulação de dados, criada como uma alternativa ao modelo tradicional REST para consumir e manipular APIs, com o objetivo de oferecer uma maneira mais flexível e eficiente de interagir com os dados.

# Características

- O cliente pode especificar exatamente quais dados deseja receber em uma única requisição.
- evita o problema de over-fetching (receber mais dados do que o necessário) e under-fetching (não receber dados suficientes), comum em APIs REST.
- O GraphQL utiliza um sistema de **tipos** para descrever a estrutura da API.
- Isso significa que tanto o cliente quanto o servidor têm uma compreensão clara dos tipos de dados que podem ser enviados ou recebidos, reduzindo erros e facilitando a validação.
- Em vez de fazer múltiplas requisições para diferentes endpoints (como em REST), o GraphQL permite que o cliente faça uma única requisição que pode recuperar e combinar dados de diferentes fontes.

## Mutations

- Além de consultas (`queries`), o GraphQL também suporta operações de escrita chamadas `mutations`, que permitem ao cliente criar, atualizar ou deletar dados no servidor.
- Exemplo: Enviar uma `mutation` para adicionar um novo usuário ou atualizar as informações de um produto.

## Subscriptions

- O GraphQL também suporta `subscriptions`, que permitem que o servidor envie atualizações em tempo real para o cliente. 
- Isso é útil para aplicações que requerem dados dinâmicos, como chats ou notificações em tempo real.
- Exemplo: Um cliente pode se inscrever em uma subscrição que notifica sempre que há uma nova mensagem em uma conversa.

## Introspecção

- GraphQL permite a introspecção, onde o cliente pode consultar a própria estrutura da API para entender quais dados estão disponíveis, tornando a API autodescritiva e facilitando o desenvolvimento e a manutenção.

# Arquitetura

- **Servidor GraphQL**:
	- O servidor GraphQL é responsável por expor o endpoint GraphQL, processar as consultas e devolver os dados solicitados ao cliente. 
	- Ele é implementado usando uma biblioteca ou framework GraphQL em uma linguagem de programação como JavaScript (Node.js), Python, Java, Ruby, etc.
- **Schema**:
	- O Schema define a estrutura da API GraphQL. 
	- Ele descreve os tipos de dados disponíveis, as consultas (`queries`), as operações de modificação (`mutations`), e as assinaturas de eventos (`subscriptions`). 
	- O schema é essencialmente o contrato entre o cliente e o servidor, especificando o que pode ser solicitado e como.
- **Resolvadores (Resolvers)**:
	- Resolvadores são funções que lidam com a lógica para obter os dados solicitados em uma consulta GraphQL. 
	- Cada campo em uma consulta GraphQL é mapeado para um resolvador que executa o código necessário para recuperar o dado correspondente, seja de um banco de dados, de outra API, ou de qualquer outra fonte de dados.
- **Cliente GraphQL**:
	- O cliente é a aplicação que consome o endpoint GraphQL. 
	- Pode ser uma aplicação web, um aplicativo móvel, ou qualquer outro sistema que precise acessar os dados expostos pelo servidor GraphQL. 
	- Ferramentas como Apollo Client ajudam a interagir com servidores GraphQL.

## Comunicação com o Banco de Dados:

A comunicação entre o servidor GraphQL e o banco de dados é feita através dos resolvadores. Aqui está como isso geralmente funciona:

1. **Consultas (Queries)**:
	- Quando uma consulta GraphQL é recebida, o servidor GraphQL a decompõe em resolvadores que mapeiam cada campo solicitado para as funções que irão buscar esses dados.
	- Os resolvadores podem então executar consultas SQL (ou equivalentes em outros bancos de dados), interagir com ORMs (Object-Relational Mappers), ou chamar APIs de terceiros para obter os dados necessários.
	- Exemplo: Um resolvador para um campo `user` pode executar uma consulta SQL para buscar os dados de um usuário específico em um banco de dados relacional.
2. **Mutations**:
	- Para operações de escrita, como criar, atualizar ou deletar dados, as `mutations` são usadas. 
	- Assim como as consultas, as `mutations` são processadas por resolvadores, que executam as operações no banco de dados ou outras fontes de dados.
	- Exemplo: Uma `mutation` para criar um novo usuário pode envolver a execução de uma inserção SQL no banco de dados.
3. **Assinaturas (Subscriptions)**:
	- Em sistemas que suportam `subscriptions`, o servidor pode manter uma conexão ativa com o cliente para enviar notificações em tempo real. 
	- As `subscriptions` são frequentemente usadas em conjunto com tecnologias como WebSockets, e os dados podem ser empurrados para o cliente quando eventos específicos ocorrem no banco de dados.
