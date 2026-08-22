---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2024-11-24T06:29:00
Owner:
  - Eduardo Quinalha
---
---

[https://github.com/bregman-arie/devops-exercises](https://github.com/bregman-arie/devops-exercises)

[[Learn DevOps for free]]

[https://www.youtube.com/watch?v=0yWAtQ6wYNM](https://www.youtube.com/watch?v=0yWAtQ6wYNM)

# O que é

- Uma cultura suportada por um conjutno de ferramentas
	- Versionamento de código: Git, GitLab, Nexus, Subversion
	- Automação de DB: Flyway, etc…
	- Integração Contínua: Jenkins, GItLab, etc…
	- Testes Automatizados: Selenium, Junit, etc…
	- Configuração / Infra as a Code: Ansible, Chef, Terraform, Puppet
	- Deploy Automatizado
	- Container: Docker, Kubernetes, Rancher
	- Orquestração de Releases
	- Cloud
	- Monitoração: Zabbix, Grafana, Prometheus
	- Análises: Elastic Search
	- Colaboração: Jira

![[Untitled 785.png]]

- Fortemente focada em Automação
- Commit, click and run
- Continuous Integration
- Continuous Delivery
- Fortemente ligada ao conceito ágil
- **5 Pilares**
	- Reduzir os silos organizacionais
	- Aceitar falhas
		- Mas recuperar de forma automatizada
	- Aceitar as mudanças
	- Favorer a automação
	- Medir/Monitorar tudo
- Benefícios
	- Feedback
	- Automação
	- Qualidade
	- Velocidade na entrega
	- Escalabilidade (em relação ao processo)
	- Colaboração
- **Processos: PCBT / RDO**

![[20230723_125027.jpg]]

- Dev
	- Plan
	- Code
	- Build
	- Test
- Ops
	- Release
	- Deploy
	- Operate
	- Monitor

# Princípios

- Processo repetível para entrega de software
- Automatizar tudo o que for possível
- Manter tudo em um sistema de controle de versões
- Se um passo causa dor, execute-o com mais frequência e o quanto antes
- Concluído significa pronto para entrega
- Todos são responsáveis pela entrega de software

# Práticas

- **Automação**
	- Automatizar tarefas repetitivas, como testes, builds e deployments.
	- Usar ferramentas como Jenkins, GitLab CI/CD ou Azure DevOps.
- **Integração Contínua (CI)**
	- Integrar código frequentemente, geralmente várias vezes ao dia.
	- Testar automaticamente o código após cada integração.
	- Usar ferramentas como GitLab CI/CD, CircleCI ou Travis CI.
- **Entrega Contínua (CD)**
	- Implementar automaticamente novas versões do software em produção.
	- Fazer deployments com frequência, mas com cuidado.
	- Usar ferramentas como Kubernetes, Docker ou Ansible.
- **Infraestrutura como Código (IaC)**
	- Gerenciar a infraestrutura através de scripts, como Terraform ou Ansible.
	- Tornar a infraestrutura configurável e replicável.
	- Usar a mesma infraestrutura para desenvolvimento, teste e produção.
- **Monitoramento**
	- Monitorar o desempenho e a saúde do software em produção.
	- Usar ferramentas como Prometheus, Grafana ou New Relic.
	- Detectar e corrigir problemas rapidamente.
- **Database Migration**
	- Versionamento da base de dados
	- As mudanças no banco devem ser versionadas juntamente com o código da aplicação
	- Usar ferramentas como Flyway, Liquibase e DbSchema

# XOps

[https://www.profissionaisti.com.br/xops-apenas-mais-um-termo-da-ti-ou-uma-tendencia/](https://www.profissionaisti.com.br/xops-apenas-mais-um-termo-da-ti-ou-uma-tendencia/)

- Junção de DevOps, SecOps, FinOps e CloudOps
- **DevOps: **
	- Desenvolvimento e as operações de TI trabalhando simultaneamente em todo o ciclo de vida de desenvolvimento de um programa.
- **SecOps: **
	- Segurança e Operação de TI
	- Integrar tecnologia e processos para reduzir riscos e aumentar a segurança de dados
- **FinOps:**
	- Cloud Financial Management
	- Gerir operações financeiras ligando pessoas, processos e tecnologia
	- Responsabilidades financeiras para os gastos variáveis da nuvem
	- Ajuda no desenvolvimento de melhores ações para compreender melhor os custos da nuvem
- **CloudOps:**
	- Identificação e definição de procedimentos operacionais relacionados a serviços de TI em nuvem

# Ferramentas

## Ansible

- Usado no provisionamento de infraestrutura, implantação de aplicações, configuração de servidores
- **Abordagem Imperativa**
	- Cada comando deverá ser especificado
- Não requer a instalação de agentes
- Baseado em SSH
- Open Sorce
- Escrito em Python
- Usa YAML

## Puppet

- Usado no provisionamento de infraestrutura e automação de TI
- Roda tanto em ambiente Unix/Linux como Windows
- **Abordagem declarativa**
	- Descreve o estado final do sistema desejado
- Depende de um servidor mestre e agentes instalados nos clientes
- Escrito em Ruby
- Utiliza uma DSL semelhante a JSON

## Jenkins

- **Jenkins** é uma ferramenta de integração contínua de código aberto que pode ser instalada e configurada em qualquer servidor. 
- Isso oferece flexibilidade, pois você pode adaptá-lo conforme suas necessidades específicas e infraestrutura. 
- Jenkins é amplamente utilizado devido à sua extensibilidade, com inúmeros plugins que permitem integrar com várias ferramentas e fluxos de trabalho.

## Travis CI

- **Travis CI** é uma ferramenta de integração contínua que é hospedada na nuvem e se **integra diretamente com o GitHub**. 
- Isso significa que, ao contrário do Jenkins, que você precisa instalar e manter, o Travis CI é uma solução **SaaS **(Software as a Service) onde a configuração é mínima e a manutenção é feita pela própria Travis. 
- Ele é especialmente popular em projetos de código aberto devido à facilidade de uso e integração direta com repositórios GitHub
