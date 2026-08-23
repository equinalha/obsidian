---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2024-10-01T17:15:00
Owner:
  - Eduardo Quinalha
---
# Clean Architecture

- É um tipo de arquitetura em camadas
- O objetivo é deixar o domínio da aplicação totalmente independente de tecnologias
- Os elementos do domínio não precisam e não devem saber detalhes de implementação de serviços providos por frameworks, tecnologias, e outros detalhes técnicos

![[Untitled 680.png]]

## Camadas

- Camadas internas = **Domínio**
	- Entidades
		- Classes comuns a vários sistemas da empresa
		- São entidades como Aluno, Professor, Departamento
		- Podem implementar regras de negócio genéricas
	- Casos de Uso
		- Regras de negócio específicas de cada sistema
- **Adaptadores**
	- Interfaces
	- Fazem a mediação entre a camada mais externa e as camadas centrais
	- Pode ser, por exemplo, implementações de *endpoints* de uma API REST
- **Frameworks externos**
	- Bibliotecas, frameworks e sistemas externos
	- É nesta camada que ficam sistemas responsáveis por persistência de banco, UI, envio de e-mails, comunicação com outros sistemas e hardwares

## Regras de dependência

> [!note] 🔥
> **Em uma arquitetura limpa, as classes de uma camada X não devem conhecer nenhuma classe de uma camada Y mais externa.**

> *O nome de um elemento declarado em uma camada externa não deve ser mencionado pelo código de uma camada interna. Isso inclui funções, classes, variáveis e qualquer outro elemento de código.*

- em uma Arquitetura Limpa, as camadas centrais são mais estáveis – menos sujeitas a mudanças – do que as camadas mais externas

## Inversão do fluxo de controle

- Ocorre quando uma classe de uma camada mais interna, por exemplo caso de uso, precisa de um serviço de uma camada externa.
	- Por exemplo, uma classe de caso de uso necessita enviar um e-mail
	- Lembrando que e-mail está na camada de Frameworks externos
- Para não violar a regra de dependência da arquitetura, faz-se o seguinte:
	- Cria-se uma interface na camada de caso de uso, por exemplo `MailServiceInterface`
	- Nesta interface, declara-se um método abstrato, por exemplo `sendMail()`
- Na camada de frameworks externos, cria-se uma classe que implementa a interface, por exemplo `MailServiceImpl`
	- Nesta classe, a implementação do método `sendMail()` irá se utilizar dos recursos de framework externo para viabilizar o envio