---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2024-10-01T17:02:00
Owner:
  - Eduardo Quinalha
---
# O que é

- Verifica o código em busca de erros e vulnerabilidades comuns, como vazamentos de memória ou estouros de buffer.
- A análise também pode impor padrões de codificação.
- Como a análise estática é realizada no código-fonte, sem executar o programa, ela pode ser executada:
	- [bem no início do pipeline de CI/CD](https://www.jetbrains.com/pt-br/teamcity/ci-cd-guide/ci-cd-best-practices/) ou 
	- diretamente da IDE

# Aspectos Principais

- **Verificação por estilo:** 
	- Considera elementos como identação, espaços e tabs, convenção de nomes, número de parâmetros, alinhamento na vertical, formato e presença de comentários, dentre outros. 
	- São todos os aspectos que contribuem para tornar o código mais padronizado, organizado e legível. 
	- A ferramenta mais utilizada para verificação por estilo é o Checkstyle;
- **Verificação por boas práticas: **
	- Aplica uma gama de regras para verificar se práticas corretas estão sendo realizadas, como evitar duplicação de código, garantir o correto uso de encoding, implementação do método **clone()**, tamanho de métodos e classes, tamanho de parâmetros, uso do padrão Singleton, criação desnecessária de variáveis locais e muitas outras. 
	- O conjunto de regras é extenso e visa garantir que o código apresente as melhores práticas possíveis. 
	- A ferramenta de verificação mais utilizada para aplicar boas práticas é o PMD;
- **Verificação por bugs: **
	- Trata de encontrar erros no sistema. 
	- Isto é importante para antecipar a identificação de problemas no software (até antes mesmo de sua execução pelo cliente). 
	- A ferramenta mais utilizada para identificação de bugs é o Firebug.

# Classificação de Defeitos

- **Gerenciamento de armazenamento**: 
	- Relacionada a problemas na alocação, desalocação e gerenciamento de memória, como vazamentos de memória.
- **Dados**: 
	- Envolvem problemas com a manipulação de dados, como variáveis não inicializadas ou erros de tipo.
	- Variáveis usadas antes da iniciação
	- Variáveis declaradas, mas nunca usadas
	- Variáveis atribuídas duas vezes, mas nunca usadas entre atribuições
	- Possíveis violações de limites de vetor
	- Variáveis não declaradas
- **Interface**: 
	- Problemas na interação do usuário com a interface do software, como botões que não funcionam ou elementos de interface mal posicionados.
	- Incompatibilidades de tipo de parâmetro
	- Incompatibilidades de número de parâmetros
	- Não uso de resultados d e funções
	- Funções e procedimentos não chamados
	- Defeitos de gerenciamento de armazenamento
	- Ponteiros não atribuídos
	- Ponteiro aritmético Perdas de memória
- **Entrada/saída**: 
	- Problemas nas operações de entrada e saída de dados, como leitura/escrita de arquivos ou comunicação com dispositivos externos.
	- Saída de variáveis duas vezes sem atribuição intermediária
- **Controle:**
	- Problemas no fluxo de execução do programa.
	- **Código inacessível**
	- Ramos incondicionais dentro de loops

# Técnicas

- Análise de Fluxo de dados
	- Variáveis sem inicialização ou com valores inconsistentes
	- Conexões de banco abertas e não fechadas
	- A abordagem **backward**, também conhecida como "para trás" ou "de baixo para cima", começa a partir do uso de uma variável (como uma leitura ou uma saída) e rastreia o caminho de volta para encontrar as definições dessa variável, permitindo verificar se as variáveis foram inicializadas corretamente antes do uso, se existem variáveis não usadas ou se ocorrem outros tipos de erros no uso das variáveis.
- Análise de Complexidade Ciclomática
	- Medir a complexidade do código
	- Identifica funções ou métodos com muitos caminhos diferentes de execução
- Detecção de duplicidade de código
- Análise de métricas de código
	- Quantidade de linhas de código
	- Número de classes, métodos, comentários
- Verificação de conformidade com padrões de codificação
- Verificação de estilo
- Análise de dependências
- Detecção de vulnerabilidades de segurança
	- Busca por padrões que representem riscos
	- SQL injection
	- Funções inseguras
	- Exposição de dados
- Análise de cobertura de testes
- Análise de dívida técnica

# Ferramentas

- SonarQube