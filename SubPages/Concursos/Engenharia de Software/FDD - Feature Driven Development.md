---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2024-09-02T09:54:00
Owner:
  - Eduardo Quinalha
---
# Introdução

- Faz parte das 6 implementações de metodologias ágeis preconizadas pelo manifesto ágil
- Fundamentada em técnicas de gerenciamento de projeto
- Modelagem orientada a objetos
- Fornece informação de estado e progresso de forma simples
- Feature
	- Funcionalidade ou característica valorizada pelo cliente
	- Similar a um requisito funcional

# Práticas

- modelagem de objetos de domínio
- desenvolvimento por feature
- posse individual do código
- equipes de features
- inspeções
- builds regulares
- gerenciamento de configuração
- relatório e visibilidade de resultados.

# Fases

![[Untitled 351.png]]

## Fase 1 – Concepção & Planejamento

- **Abrange todo o projeto**
- Nesta fase que são listadas as características (Features) que serão desenvolvidas
- São definidas todas as características e fases do sistema e projetos, respectivamente

### Processos

1. **Desenvolver um Modelo Abrangente**
	- Realiza-se um estudo dirigido sobre o escopo do sistema e seu contexto
	- Então, são realizados estudos mais detalhados para cada área a ser modelada
	- Pequenos grupos são formados por membros do domínio do negócio e por desenvolvedores, que comporão seus próprios modelos
	- Um dos modelos propostos é selecionado por consenso, tornando-se, assim, o modelo para aquela área do domínio do negócio
	- Realiza-se, então, uma combinação do modelo da área do domínio dentro de um modelo abrangente
2. **Construir uma lista de funcionalidades**
	- Identificam-se todas as funcionalidades que satisfaçam os requisitos
	- Forma-se uma lista categorizada de funcionalidades
3. **Planejar por funcionalidade**
	- É produzido o plano de desenvolvimento
	- Contempla a ordem de implementação, baseado nas dependências entre as features
	- As principais atividades não são uma sequência estrita

## Fase 2 – Construção

- **Abrangem cada funcionalidade**
- A implementação inicia-se agrupando reatures relacionadas dentro de pacotes de trabalho
- Um pacote de trabalho representa uma parte do sistema que já poderá ser utilizada pelo cliente

### Processos

4. **Detalhar por funcionalidade**
	- É produzido o pacote de trabalho
	- Um certo número de funcionalidades são agendadas para desenvolvimento
	- Presença da figura do programador líder
	- Formação da equipe
5. **Construir a funcionalidade**
	- São produzidas as funcionalidades
	- O código passa por testes e inspeções
	- Por último é promovido a build

# Marcos

- O FDD facilita a comunicação de status do projeto
- Permite o rastreio do progresso
- Para isso, utiliza-se de marcos
- Os marcos começam a ser monitorados pelo gerente de projeto a partir da fase de construção
- São eles:
	- **Walkthroughs do projeto**
	- **Projeto**
	- **Inspeção do projeto**
	- **Código**
	- **Inspeção de código**
	- **Progressão para construção**
