---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2024-08-26T17:59:00
Owner:
  - Eduardo Quinalha
---
# O que é

- É tanto uma especificação quanto um framework
- é um framework** web MVC** para a construção de interfaces de usuário **baseadas em componentes**.
- JSF trouxe uma abordagem voltada para interfaces de usuário, disponibilizando para o programador uma rica coleção de componentes, bem como uma melhor separação entre as camadas da aplicação.
- Com o JSF, o programador pode escrever views em XHTML e através de Data Binding conectá-las a classes Java

![[Untitled 555.png]]

```xml
<?xml version="1.0" encoding="ISO-8859-1"?>
    <html xmlns="http://www.w3.org/1999/xhtml"
          xmlns:f="http://java.sun.com/jsf/core"
          xmlns:h="http://java.sun.com/jsf/html">
    <h:head></h:head>
    <h:body>
    <h:form>

    <h3>Novo modelo</h3>
    <div>Descrição: <h:inputText value="#{novoModeloMB.modelo.descricao}"/></div>
    <div>Fabricante:
          <h:selectOneRadio value="#{novoModeloMB.modelo.fabricante}">
                <f:selectItems value="#{novoModeloMB.fabricantesDisponiveis}"/>
          </h:selectOneRadio>
    </div>
    <div>Ano:
          <h:selectOneMenu value="#{novoModeloMB.modelo.ano}">
                <f:selectItems value="#{novoModeloMB.anosDisponiveis}"/>
          </h:selectOneMenu>
    </div>
    <div>Alcóol: <h:selectBooleanCheckbox value="#{novoModeloMB.modelo.alcool}" /> </div>
    <div>Gasolina: <h:selectBooleanCheckbox value="#{novoModeloMB.modelo.gasolina}" /> </div>
    <div>
          <h:commandButton action="#{novoModeloMB.cadastra}" value="Cadastrar" />
    </div>

    </h:form>
    </h:body>
    </html>
```

- O arquivo de configurações é o faces-config.xml, no entanto desde o JSF 2.0, as configurações têm sido substituídas por annotations
- Oferece diversos validadores embutidos para validar componentes UI
	- Tamanho de campos
	- Tipo de entrada
	- Range
	- RegEx
	- Validadores customizados
- Define 3 taglibs
	- HTML
		- Representação de diversos elementos HTML
```xml
<!-- Alguns Exemplos-->

<h:commandButton value="Meu Botão"
                 action="#{devmediaMB.teste}"
                 actionListener="#{devmediaMB.testeVoid}"
                 styleClass="estiloBotao"
                 disabled="true">
	<f:ajax execute="@this" render="@form"/>
</h:commandButton>

<h:inputText
	value="#{devmediaMB.nomeCompleto}"
	maxlength="150"
	required="true"
	requiredMessage="O Nome é obrigatório" />
```
	- CORE
		- Internacionalização
		- Validação
		- Conversão
		- Outros
	- FACELETS
		- Templates para aplicações Web
- **FacesServlet**
	- Recebe requisições dos componentes View do MVC e redireciona para os managed beans do Model
	- gerencia o ciclo de vida das páginas JSF
	- Requisições JSF processadas são direcionadas para um Servlet chamado `FacesServlet`, o qual cria um objeto denominado* *`*FacesContext*`.
	- Responde às requisições
	- Deve ser configurada tanto no `web.xml` quando no `faces-config.xml`
- **Managed Beans (backing beans)**
	- Objetos vinculados com o comportamento de tela (seus eventos e componentes) tradicionalmente são chamados de ManagedBeans.
	- Fornece os dados que serão exibidos
	- Recebe dados enviados nas requisições
- **Converters**
	- Objetos responsáveis por converter informações indicados pelo usuário em uma representação mais adequada no servidor, e vice-versa.
	- Por exemplo, o usuário preenche um campo de data na UI que será enviado ao servidor como `String`, no entanto, poderá ser convertido para `Date` utilizando um `converter`
	- O JSF já disponibiliza alguns conversores que podem ser utilizados imediatamente em nosso código, como é o caso do conversor para tipos data
	- Também é possível criar e utilizar conversores customizados, por exemplo, para um campo de CPF
	- Um converter é uma classe que implementa a interface `javax.faces.convert.Converter` e deve ser anotada com `@FacesConverter`

## Ciclo de Vida do JSF

<!-- Column 1 -->
![[Untitled 556.png]]


<!-- Column 2 -->
- Quando a tela é manipulada por um usuário em seu navegador, disparando algum evento que deva envolver processamento do servidor, a árvore de componentes desta página é carregada novamente pelo lado do servidor, o que ocorre na etapa `Restaurar View`
- Após isto, os valores referentes ao formulário, enviados pelo navegador, são armazenados na árvore de componentes no servidor. Logo após o armazenamento, estes valores são **convertidos** para valores mais adequados, já pensando em sua representação no modelo Java, utilizando os **Converters**. Este ciclo de vida também possui uma etapa focada em processar validações individuais dos componentes, o que nos permite escrever e reutilizar validações elegantes através de **Validators**.
- Com os dados dos componentes validados, o JSF aplica estes valores diretamente no `**modelo**`
- Após os dados da tela do usuário estarem em seus “devidos lugares”, o JSF **invoca o método indicado** para o evento correspondente à ação executada. De acordo com o retorno do processamento do modelo, o JSF processa o resultado da navegação, isto é, para qual página essa requisição deve ser encaminhada. 
- Com o resultado da navegação, o framework **renderiza a resposta **para o navegador baseada em alguma página XHTML.

# Facelets

- subprojeto do JSF
- maneira de se implementar views nas páginas web
- **princípio fundamental do JSF**: abstrair qualquer código Java diretamente na camada de visão através do uso de tags customizadas.
- Proporciona a criação de templates reaproveitáveis e importáveis; e fornecendo recursos para operações básicas da lógica de programação como repetições, condições e manipulação de dados através da EL (Expression Language) do próprio JSF.
- por exemplo, você pode criar uma página Facelets para representar o cabeçalho da aplicação, outra para o rodapé, e pode importá-las facilmente em todas as demais páginas, sem necessitar usar as tags de include diretamente
- Elimina o sistema **JSP Compiler to Servlet** que é usado para compilar as páginas JSPs em Servlets antes de devolver a resposta ao browser. Isso basicamente aumenta em 30% a 50% a performance do sistema.
- Precisão para reportar erros, isto é, o sistema de mensagens de erro do Facelets é semelhante ao do Java, baseado em stack traces (pilhas de mensagens de exceções).

![[Untitled 557.png]]

# PrimeFaces

- O JSF provê uma forma de desenvolver interfaces em HTML utilizando componentes prontos
- O Facelets adiciona ao JSF a funcionalidade de se trabalhar com templates, podendo-se modularizar a interface final
- O PrimeFaces provê uma biblioteca de componentes de interface gráfica
- Existem outros equivalentes:
	- IceFaces
	- RichFaces
