---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2024-09-05T15:05:00
Owner:
  - Eduardo Quinalha
---
# O que é

- É uma especificação de interface para acesso a dados\
- Provê funções para conectar e desconectar fontes de dados, preparar e executar comandos, processar erros e processar transações.
- Permite acessar vários DB’s com uma API Única
- Uma aplicação escrita utilizando ODBC é portável para outras plataformas, tanto no lado do cliente quanto no lado do servidor **com poucas modificações no código de acesso a dados**
- O Auto commit é habilitado por padrão

# Componentes

- Aplicação
- Driver Manager
	- uma DLL (Dynamic-Link Library) que provê **acesso aos drivers ODBC. **
	- O Driver Manager carrega as DLL´s dos drivers e direciona chamadas a funções ODBC ao driver correto. 
	- Ele também verifica algumas condições de erro e processa algumas chamadas a funções ODBC.
- Driver
	-  uma DLL que processa chamadas a funções ODBC. 
	- O driver conecta uma fonte de dados, traduz comandos SQL e os submete à fonte de dados, recupera informações da fonte de dados e retorna dados para a aplicação. 
	- Se um SGBD, como Xbase, não usa SQL, o driver também tem que processar os comandos SQL.
- Fonte de Dados
	- SGBD