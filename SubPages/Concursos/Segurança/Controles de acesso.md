---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2024-11-17T07:54:00
Owner:
  - Eduardo Quinalha
---
# Segurança Lógica

- A nível de elementos de rede
- A nível de rede
- A nível de sistemas e software

## Hardening

- Desabilitar recursos, serviços e credenciais que não serão utilizadas
- Contexto de um equipamento ou servidor

# Controle de Acesso

- Tanto conceitos físico e lógico
- Princípio da **autenticidade **e **autorização**
- Geralmente organizado em camadas
	- Defesa em profundidade

## Mandatory Access Control (MAC)

- O administrador é o responsável por atribuir as permissões
- Diretamente ligado ao princípio da autenticidade e autorização
- Utiliza o conceito de LABEL ou marcador para verificar o grau de autorização do acesso

## Discretionary Access Control (DAC)

- Modelo mais flexível comparado com o MAC
- Usuário compartilha o recurso com outros usuários
	- Recursos dos quais ele é dono
- Pode inclusive transferir a propriedade sobre determinado objeto
- Controle descentralizado
- Auditoria mais difícil

## Role-Based Access Control (RBAC)

- Baseado em papéis
- Privilégios de acordo com a função exercida pelo usuário
- Simplifica o processo

## Níveis RBAC

### RBAC 0

- Não possui hierarquia de papéis
- Inviável para ambientes com muitos usuários

### RBAC 1

- Introduz hierarquia de papéis
- Não é possível delegação

### RBAC 2

- Permite hierarquia
- Permite delegação
- Adequado a ambientes corporativos em geral

### RBAC 3

- Extensão do RBAC 2
- Permite hierarquia
- Permite delegação
- Inclui** controle de acesso baseado em tempo e contexto**

### RBAC 4

- Ainda não está totalmente implementado
- Recursos adicionais de segurança e flexibilidade
- Alta complexidade de gerenciamento

## Attribute-Based Access Control (ABAC)

- Baseia-se em atributos do sujeito, objeto e contexto
	- Localização do sujeito
	- Tempo
	- Tipo de recurso
	- Critérios de segurança
- Mais flexível e granular que o RBAC
- Exemplo:
	- "Permitir que usuários do departamento de vendas acessem documentos de vendas apenas durante horário comercial e a partir do escritório”

![[Controle_de_Acesso.png]]
