---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2024-10-14T14:39:00
Owner:
  - Eduardo Quinalha
---
> [!note] 🔥
> Possível tema de discursiva

> [!note] 🔥
> (continuous integration) Integração Contínua --> Ainda não há que se falar em testes e nem deploy/release,
> (continuous delivery) Entrega Contínua --> O deploy é aprovado e entregue... (Segue a assertiva da questão!)
> 
> (continuous deployment) Implantação Contínua --> O deploy é totalmente automatizado.

![[CI-CD synced block]]

[https://martinfowler.com/articles/continuousIntegration.html](https://martinfowler.com/articles/continuousIntegration.html)

**Guia de CI/CD do TeamCity**

[https://www.jetbrains.com/pt-br/teamcity/ci-cd-guide/](https://www.jetbrains.com/pt-br/teamcity/ci-cd-guide/)

![[Untitled 681.png]]

# Continuous Integration

- Ambientes
	- Jenkins → Java, Open Source
		- jenkinsfile
	- Circle CI
	- Gitlab
	- Team City
	- Sonar
		- Analizador de qualidade de código
- Etapas/componentes
	- Repositório de dados
		- Versionamento
	- Build automatizado
	- Testes automatizados
	- Quality Assurance (Q/A) automatizado (sonar)
	- Delivery
- Feature Toggle
	- Utilizado quando o desenvolvimento é do tipo trunk based
	- Cada commit deveria estar pronto para ir p/ produção
	- Na prática utilizam-se flags para especificar se a feature que está em desenvolvimento está ou não habilitada
	- Assim se o código for para produção, mesmo antes da feature estar concluída, ela não terá efeito no código final
- Git Flow
	- Cada feature numa branch separada
	- As branches são derivadas de uma branch secundária → Dev

# Continuous Delivery

- Deploy automatizado (Disparável)
- Rollback automatizado (disparável)

# Continuous Deployment

- O Deploy em produção é automatizado

## Canary Deployment

- O Load Balancer direciona gradualmente mais requisições para  a nova versão até que haja certeza de que o funcionamento está OK
- Neste momento, todo o tráfego é roteado para a nova versão e a antiga é retirada de produção
- Este processo deve ser automatizado

![[Untitled 682.png]]

---