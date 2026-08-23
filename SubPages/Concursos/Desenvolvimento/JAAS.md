---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2024-08-26T17:59:00
Owner:
  - Eduardo Quinalha
---
# JAAS - Java Authentication and Authorization Service

- Conjunto de API
- Framework de segurança
- Facilita autenticação e autorização em aplicações Java

## Autenticação com JAAS

- Modulo de Login
	- Pode implementar mecanismos de autenticação específicos
		- Login e senha
		- Certificados digitais
		- Tokens
- Configuração do Login
	- Configuração dos módulos de login
	- Arquivo: `jaas.config`
- Chamada de Autenticação
	- Chamado no código da aplicação
	- O JAAS delega para os módulos configurados

```java
LoginContext lc = new LoginContext("ExemploLogin", new CallbackHandler() {
    public void handle(Callback[] callbacks) throws IOException, UnsupportedCallbackException {
        for (Callback callback : callbacks) {
            if (callback instanceof NameCallback) {
                ((NameCallback) callback).setName("usuario");
            } else if (callback instanceof PasswordCallback) {
                ((PasswordCallback) callback).setPassword("senha".toCharArray());
            }
        }
    }
});
lc.login();
```

## Autorização

- Política de autorização
	- Baseado em:
		- funções
		- grupos
		- informações de contexto
		- *realm, user, group, role.*

```java
public void imprimirRelatorio() {
    if (subject.getPrincipals().contains(new RolePrincipal("gerente"))) {
        // O usuário tem permissão para imprimir o relatório
        // Executa a ação
    } else {
        // O usuário não tem permissão para imprimir o relatório
        // Gere um erro ou redirecione para uma página de erro
    }
}
```
