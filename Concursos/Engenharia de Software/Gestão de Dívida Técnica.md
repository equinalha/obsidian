---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2024-10-28T08:27:00
Owner:
  - Eduardo Quinalha
---
# Gestão de Dívida Técnica

[https://www.objective.com.br/insights/divida-tecnica/](https://www.objective.com.br/insights/divida-tecnica/)

## Dívida Técnica (DT)

- Dívida Técnica (DT) descreve as consequências que os projetos de software enfrentam durante o seu desenvolvimento, ocasionada muitas vezes, quando tarefas não são realizadas adequadamente
- no desenvolvimento de software, quando o programador opta por ignorar as **melhores práticas** de programação e **design**, isso resulta na acumulação de uma dívida técnica que, eventualmente, precisará ser quitada.
- Preço da gambiarra
- acumula-se ao longo do tempo se não for tratada e pode levar a problemas significativos no projeto.
- código mal escrito, falta de documentação, arquiteturas inadequadas, falta de testes ou atrasos na implementação de correções necessárias.
- há **riscos de segurança** significativos, com código mal escrito deixando o software vulnerável a ataques cibernéticos e violações de dados, afetando negativamente a reputação da empresa
- Consequências:
	- bugs frequentes, 
	- baixa escalabilidade e 
	- dificuldade em manter e expandir o aplicativo. 
	- à medida que a dívida técnica se acumula, o **custo de manutenção do software aumenta**, tornando mais demorado e complexo corrigir bugs, fazer alterações no código e adicionar novos recursos devido à complexidade do código de baixa qualidade.
- Por que é importante?
	- *aproximadamente 30% dos Diretores de Tecnologia da Informação (CIOs) relataram que mais de ****um quinto ****de seu orçamento destinado a novos produtos é desviado para resolver questões relacionadas à dívida técnica. Além disso, eles estimam que a dívida técnica representa entre 20% e 40% do valor total de seus ativos tecnológicos (antes da depreciação).*
- Formas de resolver:
	- **refatoração do código, **
	- **melhorias na arquitetura, **
	- implementação de **testes automatizados** ou 
	- outras práticas de **engenharia de software**.

## Tipos

- **Dívida de Código**
	- Código mal escrito, 
	- duplicação de código, 
	- falta de modularidade e 
	- código difícil de entender
- **Dívida de Design**
	- Arquiteturas inadequadas,
	- falta de padrões de projeto e 
	- dependências complexas
- **Dívida de Testes**
	- Falta de [testes automatizados,](https://www.objective.com.br/insights/testes-automatizado-com-ia/) 
	- cobertura de teste inadequada e 
	- testes de baixa qualidade
- **Dívida de Infraestrutura**
	- Dependência de tecnologias desatualizadas,
	- falta de automação na implantação e 
	- configurações de servidor mal otimizadas

## Prevenção

- **Identificar e priorizar**
	- análise abrangente do código-fonte, arquitetura e processos de desenvolvimento
	- identificar **áreas específicas **de dívida técnica.
	- Priorizar essas áreas com base em sua gravidade e impacto no projeto.
- **Padrões de Codificação**
	- codificação claros e consistentes para garantir que todos os membros da equipe sigam as melhores práticas de desenvolvimento de software
	- padronizar a nomenclatura, a estrutura do código e as práticas de documentação.
- **Refatorar o Código**
	- simplificando-o, eliminando **redundâncias** e tornando-o mais legível e sustentável. 
	- reestruturação de classes, a extração de métodos e a eliminação de código morto ou duplicado.
- **Testes Automatizados**
	- Abrangentes
	- O mais automatizado possível
	- Unitários, integração, regressão e aceitação
- **Adotar CI/CD**
	- permite identificar e corrigir problemas rapidamente, reduzindo o tempo entre a escrita do código e sua entrega aos usuários.
- **Estabelecer a cultura de revisão de código**
	- promove a colaboração e o compartilhamento de conhecimento dentro da equipe.

## Ágil vs DT

- as metodologias ágeis oferecem uma estrutura eficaz para lidar com a dívida técnica.
- Motivos:
	- **Identificação precoce**
		- Devido a característica incremental e interativa
		- Problemas são frequentemente identificados devido às entregas de partes menores
	- **Transparência e visibilidade**
		- exposição da dívida técnica durante as reuniões diárias, revisões de sprint e outras cerimônias ágeis. 
	- **Priorização por valor**
		- o foco está na entrega de valor para o cliente de forma rápida e contínua.
		-  a dívida técnica é frequentemente priorizada com base em seu valor para o negócio. 
		- Se a dívida técnica estiver impedindo a entrega de valor ao cliente, ela é geralmente tratada como uma prioridade.
	- **Flexibilidade para adaptação**
		- Metodologias ágeis são flexíveis e adaptáveis
		- Isto inclui a capacidade de lidar com dívida técnica a medida que ela surge
	- **Abordagem proativa**
		- alocação de tempo durante o ciclo de desenvolvimento para atividades de refatoração, teste e redução da dívida técnica. 
