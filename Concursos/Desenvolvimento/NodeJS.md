---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2024-09-03T19:10:00
Owner:
  - Eduardo Quinalha
---
# Características

- Usa programação assíncrona
- Roda na engine V8, extraída do Google Chrome
- Um aplicativo Node roda em um único processo, sem a criação de uma nova thread para cada requisição
- Isso libera o servidor de ter que gerenciar concorrência de múltiplas threads
- JavaScript is generally considered an interpreted language, but modern JavaScript engines no longer just interpret JavaScript, they compile it.
- JavaScript is internally compiled by V8 with **just-in-time** (JIT) **compilation** to speed up the execution.

# Móduto HTTP

- Quando uma nova requisição é recebida, um evento `request` é chamado e provê dois objetos
	- `http.IncomingMessage`
	- `http.ServerResponse`

# NPM

- Gerencia downloads de dependências do projeto
- `**-save-dev**` installs and adds the entry to the `**package.json**` file *devDependencies*
- `**-no-save**` installs but does not add the entry to the `**package.json**` file *dependencies*
- `**-save-optional**` installs and adds the entry to the `**package.json**` file *optionalDependencies*
- `**-no-optional**` will prevent optional dependencies from being installed
- The difference between ***devDependencies*** and ***dependencies*** is that the former contains **development tools**, like a testing library, while the latter is bundled with the app in production.
- As for the ***optionalDependencies*** the difference is that build failure of the dependency **will not cause installation to fail**. But it is your program's responsibility to handle the lack of the dependency.

# Produção vs desenvolvimento

- **There is no difference between development and production in Node.js**, i.e., 
- there are no specific settings you need to apply to make Node.js work in a production configuration. 
- However, a few libraries in the npm registry recognize using the `**NODE_ENV**` variable and default it to a `**development**` setting. 
- Always run your Node.js with the `**NODE_ENV=production**` set.
