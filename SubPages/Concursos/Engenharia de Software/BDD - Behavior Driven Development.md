---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2024-09-02T09:54:00
Owner:
  - Eduardo Quinalha
---
# O que é

- Metodologia de desenvolvimento de software que se baseia na colaboração entre desenvolvedores, testadores e não-desenvolvedores (como clientes ou gerentes de produto) para criar um entendimento comum sobre como o software deve se comportar.
- É considerado uma evolução do TDD, mas com um foco mais forte no comportamento do usuário.

# Características

- As funcionalidades do sistema são descritas em uma linguagem simples, próxima da** linguagem natural,** permitindo que todos os envolvidos no projeto entendam o que está sendo desenvolvido. 
- Isso geralmente é feito usando a sintaxe **Gherkin**, que segue a estrutura **"Dado-Quando-Então" (Given-When-Then).**
	- Esta linguagem pode ser interpretada tanto por humanos quanto pelo computador, no desenvolvimento de testes automatizados
```plain text
Feature: Login de usuário

  Scenario: Usuário faz login com sucesso
    Given o usuário está na página de login
    And o usuário insere o nome de usuário "Joao"
    And o usuário insere a senha "senha_secreta"
    When o usuário clica no botão de login
    Then o usuário deve ser redirecionado para a página inicial
    And o usuário deve ver a mensagem "Bem-vindo, Joao!"
```
	- Essas especificações em Gherkin são então convertidas em testes automáticos usando uma ferramenta de BDD, como Cucumber ou SpecFlow:

```java
// Arquivo de passos: LoginSteps.java

import io.cucumber.java.en.*;

public class LoginSteps {

    @Given("o usuário está na página de login")
    public void oUsuarioEstaNaPaginaDeLogin() {
        // Código para navegar até a página de login
    }

    @And("o usuário insere o nome de usuário {string}")
    public void oUsuarioInsereONomeDeUsuario(String username) {
        // Código para inserir o nome de usuário
    }

    @And("o usuário insere a senha {string}")
    public void oUsuarioInsereASenha(String password) {
        // Código para inserir a senha
    }

    @When("o usuário clica no botão de login")
    public void oUsuarioClicaNoBotaoDeLogin() {
        // Código para clicar no botão de login
    }

    @Then("o usuário deve ser redirecionado para a página inicial")
    public void oUsuarioDeveSerRedirecionadoParaAPaginaInicial() {
        // Código para verificar o redirecionamento
    }

    @And("o usuário deve ver a mensagem {string}")
    public void oUsuarioDeveVerAMensagem(String mensagem) {
        // Código para verificar a mensagem de boas-vindas
    }
}
```
	- Esses testes validam se o comportamento descrito é realmente implementado no código da aplicação.
- **Foco no Comportamento do Usuário**: 
	- O BDD enfatiza o que o software deve fazer do **ponto de vista do usuário final**, ao invés de focar em como ele deve ser implementado. 
	- Isso ajuda a garantir que o software atenda às necessidades reais do usuário.
- **Automação de Testes**: 
	- As especificações em BDD podem ser convertidas em testes automatizados, que são executados para garantir que o software se comporte conforme o esperado.
- **Colaboração**: 
	- O BDD promove a colaboração entre todas as partes interessadas, permitindo que desenvolvedores, testadores e stakeholders não técnicos trabalhem juntos desde o início do processo de desenvolvimento.

# Vantagens

- **Redução de Falhas de Comunicação**: Como todos os envolvidos entendem o que está sendo desenvolvido, há menos chances de mal-entendidos que possam levar a problemas no software.
- **Testes mais Eficazes**: Com testes automatizados baseados em comportamentos, é mais fácil garantir que o software atende aos requisitos desde o início.
- **Maior Qualidade**: Ao focar no comportamento do usuário e colaborar desde o início, o BDD pode levar a um software que é mais alinhado com as necessidades do cliente.

# Ferramentas

- **Cucumber**: Uma ferramenta popular que suporta a sintaxe Gherkin e integra testes automatizados.
- **SpecFlow**: Ferramenta similar ao Cucumber, mas voltada para o ecossistema .NET.
- **JBehave**: Outra ferramenta BDD usada principalmente em projetos Java.

# **Ciclo de Desenvolvimento:**

1. **Escrever o cenário de comportamento** (usando Gherkin).
2. **Implementar os testes automáticos** (que falharão inicialmente).
3. **Escrever o código da aplicação** para fazer os testes passarem.
4. **Refatorar** o código para melhorar a qualidade, enquanto os testes garantem que o comportamento desejado é mantido.
