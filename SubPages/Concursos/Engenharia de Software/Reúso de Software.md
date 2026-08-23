---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2024-08-26T18:10:00
Owner:
  - Eduardo Quinalha
---

# Reúso de Software

- Processo de desenvolvimento é orientado para o reúso
- Uma vez que software é considerado um ativo valioso, o reúso permite um maior ROI
- Existem custos e problemas associados ao reúso
	- Custo associado ao processo de compreensão e verificação de adequação ao uso
	- Testes

## Tamanhos de unidades de softwares reusadas:

- **Sistema de Aplicação**
	- Totalidade de um sistema de aplicação
	- Sem necessidade de alterações
	- Configuráveis
		- Podem ser desenvolvidas famílias de aplicações com uma arquitetura comum, mas adaptadas para clientes específicos
		- Um produto de sistema de aplicação é um sistema de software que pode ser adap­tado para as necessidades de diferentes clientes sem que o código-fonte do sistema seja modificado.
		- Podem permitir que o sistema aceite plugins que ampliem a funcionalidade ou que verifiquem as entradas de usuário para garantir que sejam válidas.
	- Integrados
		- Incluem dois ou mais sistemas de aplicação, geralmente legados
		- 
- **Componentes**
	- Desde subsistemas até objetos únicos
- **Objetos e Funções**
	- Componentes de software que implementam uma única função
- **Reúso de conceito**
	- Reutilização de uma ideia, forma, trabalho ou algoritmo

## Abordagens que apoiam o reúso

- Frameworks de aplicação
	- Baseiam-se em características orientadas a objetos, como herança e polimorfismo, para implementar extensões para o framework.
- Linha de sistemas de sofware
	- incorpora informações detalhadas do domínio e da plataforma.
	- compostas de uma família de aplica­ções relacionadas, de propriedade da mesma organização.
	- Quando uma nova aplicação é criada, o ponto de partida costuma ser o membro mais próximo da família de aplicações, não a aplicação genérica básica.
- Integração de sistemas de aplicação
- Padrões de arquitetura
- Softwares orientados a aspectos
- Softwares baseados em componentes
- Sistemas de aplicação configuráveis
- Padrões de projeto
- Sistemas ERP
- Sistemas de sistemas
	- Dois ou mais sistemas são integrados para criar um sistema novo.

## Benefícios

- Confiança aumentada
	- Componentes maduros, amplamente testados
- Risco de processo reduzido
	- Custo já é conhecido
- Uso eficaz de especialistas
	- Softwares reusáveis que encapsulam o conhecimento especializado
- Conformidade com padrões
	- UI
- Desenvolvimento acelerado

## Problemas

- Maiores custos com manutenção
	- Caso o código fonte não seja conhecido
- Falta de ferramentas de suporte
- Adaptação
	- Às vezes pode ser necessário a adaptação de componentes a fim de permitir que trabalhe em um novo ambiente

## Planejamento para o reúso

- **Cronograma de desenvolvimento**
	- Se o software necessita ser desenvolvido rapidamente, dar preferência a sistemas de prateleira em vez de componentes individuais
- **Expectativa de duração do software**
	- Sistemas de vida longa, deverão ser pensados na manutenção
	- Implicações do reúso a longo prazo
	- Evitar sistemas de prateleira e fornecedores externos
- **Conhecimento e experiência da equipe**
	- Tecnologias de reúso são mais complexas
- **Importância do software e seus requisitos não funcionais**
	- Para requisitos de desempenho rigorosos, o reúso pode ser um obstáculo
- **Domínios bem conhecidos**
	- Domínios bem conhecidos como sistemas médicos e manufatura têm grande disponibilidade de sistemas de prateleira customizáveis
- **Plataforma em que o sistema será executado**

# Engenharia de Software Baseada em Componentes

- Surgiu a partir de uma frustração com o desenvolvimento orientado a objetos
- Componentes são abstração de um nível mais alto do que objetos

## Fundamentos

- Componentes independentes especificados completamente por suas interfaces
- Padrões de componentes que definem interfaces
- Middleware que fornece suporte de software para integração de componentes
- Componentes são independentes
- Detalhes de implementação são ocultos

## Problemas

- As empresas envolvidas não puderam concordar com um padrão único de componentes
- Componentes desenvolvidos em plataformas diferentes não conseguem se comunicar
- Padrões e protocolos complexos
- Os componentes tinham que ser integrados fisicamente ao projeto
- Estes problemas levaram ao desenvolvimento da engenharia de software orientada a serviços e SOA

## Característica de um componente

- Passível de composição
	- As interações externas ocorrem por meio de interface definidas publicamente
- Implantável
	- Autocontido
	- Entidade standalone
	- Normalmente um código binário, que não precisa ser compilado
- Documentável
- Independente
- Padronizado
- Acessados via RPC