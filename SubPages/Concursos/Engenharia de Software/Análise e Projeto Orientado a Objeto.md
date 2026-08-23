---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2024-10-28T08:38:00
Owner:
  - Eduardo Quinalha
---
[https://proedu.rnp.br/bitstream/handle/123456789/1548/24.1_versao_Finalizada_Analise_Projeto_Software_14_09_15.pdf?sequence=1&isAllowed=y](https://proedu.rnp.br/bitstream/handle/123456789/1548/24.1_versao_Finalizada_Analise_Projeto_Software_14_09_15.pdf?sequence=1&isAllowed=y)

# Análise vs Projeto

- **Análise**
	- atividades necessárias para entender o domínio do problema, isto é, o que deve ser feito
	- Na análise, a tecnologia de implementação e os requisitos não-funcionais **não são modelados, **pois tratam-se de atividades técnicas de projeto
	- pensa-se apenas em modelar funções, dados e relacionamentos do sistema
	- **Atividades:**
		1. Identificar Classes
		2. Identificar Responsabilidades
		3. Identificar Atributos
		4. Identificar Relacionamentos
- **Projeto**
	- atividades necessárias para entender o domínio da solução do problema, isto é, como deve ser feito. 
	- É uma atividade técnica, com foco no programador.

## Modelo de Classes de Análise

- Representa classes de domínio de negócio
- Não leva em consideração as restrições inerentes à tecnologia a ser utilizada
- É mais estável que o modelo de projeto

![[SubPages/Pessoal/images/image 64.png]]

## Modelo de Classes de Especificação (ou projeto)

- Estende o modelo de análise
- Contém detalhes específicos inerentes à solução

![[SubPages/Pessoal/images/image 65.png]]

## Modelo de Classes de Implementação

- Estende o modelo de classes de projeto
- Contém detalhes específicos, inerentes ao desenvolvimento das classes em alguma linguagem

# Classes de Fronteira, Controle e Entidade

- Categorização das classes de acordo com sua responsabilidade

![[SubPages/Pessoal/images/image 66.png]]

- **Fronteira**
	- Modela a interação entre um ator e o sistema
	- Para cada ator é identificada pelo menos uma classe de fronteira para permitir sua interação com o sistema
	- Permite que o sistema se comunique com o mundo exterior
	- **Altamente dependentes do ambiente**
- **Controle**
	- Controlam a lógica de execução ou negócio, correspondente a cada caso de uso
	- Fazem a comunicação entre os objetos de fronteira e os objetos de entidade
	- Decidem o que o sistema deve fazer quando um evento externo relevante ocorre
	- Representam a dinâmica do sistema
- **Entidade**
	- Armazena informação que é manipulada ou processada pelo caso de uso
	- Responsáveis pela persistência
	- Representam os conceitos-chave do sistema que está sendo desenvolvido

# Projeto de Software

- Determinar como o sistema deve funcionar para atender aos requisitos identificados na fase de análise
- soluções técnicas para implementar os requisitos são definidas.
- **Atividades**
	- Desenvolver uma **arquitetura de software** de alto nível para o sistema
	- Especificar estruturas de dados, interfaces e componentes
	- Decidir sobre tecnologias, frameworks e bibliotecas a serem usadas.
	- Projetar algoritmos e determinar estratégias de implementação para os requisitos
	- Criar diagramas UML, como diagramas de classe, de sequência ou de estado.