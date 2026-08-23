---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2024-11-24T08:30:00
Owner:
  - Eduardo Quinalha
---
# Modelagem de Ameaças

## STRIDE

| **Propriedade** | **Ameaça** | **Definição** |
| --- | --- | --- |
| Autenticação | **Spoofing** |  Personificar algo ou pessoa |
| Integridade | **Tampering** | Modificar dados ou código |
| Não repúdio | **Repudiation** | Alegar não ter realizado uma ação |
| Confidencialidade | **Information disclosure** | Expor informações |
| Disponibilidade | **Denial of Service** | Negar ou degradar serviço |
| Autorização | **Elevation of privilege** | Obter recursos sem autorização |

## DREAD

- Composto de 5 critérios utilizados para avaliar uma ameaça

### 1. **Damage Potential (Potencial de Dano)**

- Qual o nível de dano que a vulnerabilidade pode causar se for explorada?
- Considerar em termos de perda de dados, comprometimento da integridade do sistema, ou consequências para a confidencialidade.
- A pontuação geralmente vai de 1 (baixo impacto) a 10 (impacto catastrófico).

### 2. **Reproducibility (Reprodutibilidade)**

- Com que facilidade essa ameaça pode ser reproduzida por um invasor?

### 3. **Exploitability (Explorabilidade)**

- Qual o nível de esforço ou conhecimento técnico necessário para explorar essa vulnerabilidade?
- Quanto mais fácil for explorar a ameaça, maior a pontuação.

### 4. **Affected Users (Usuários Afetados)**

- Quantos usuários serão impactados se a vulnerabilidade for explorada?

### 5. **Discoverability (Descoberta)**

- Quão fácil é para um atacante identificar essa vulnerabilidade?

# **Secure Software Development Life Cycle**

[https://learn.microsoft.com/en-us/previous-versions/windows/desktop/cc307748(v=msdn.10)](https://learn.microsoft.com/en-us/previous-versions/windows/desktop/cc307748(v=msdn.10))

[https://learn.microsoft.com/pt-br/compliance/assurance/assurance-microsoft-security-development-lifecycle](https://learn.microsoft.com/pt-br/compliance/assurance/assurance-microsoft-security-development-lifecycle)

- Criado pela Microsoft
- incorpora requisitos de segurança abrangentes, ferramentas específicas de tecnologia e processos obrigatórios no desenvolvimento e funcionamento de todos os produtos de software.
- Consiste em 7 componentes sendo as 5 fases principais:
	- Requisitos
	- Design
	- Desenvolvimento
	- Verificação
	- Release
- 2 Atividades de segurança de suporte
	- Preparação (Treinameto)
	- Resposta
- Processo estruturado que engloba diferentes etapas
- Desde a concepção até a manutenção
- Está intrinsecamente ligado ao conceito de Shift Left Security

![[image 102.png]]

## Princípios de segurança

- Conhecidos por **SD3 + C**
- São eles:
	- Secure by Design
	- Secure by Default
	- Secure in Deployment
	- Communication

### Secure By Design

- Arquitetura, projeto e estrutura de software seguras
- O projeto é revisado em busca de possíveis falhas de segurança
- É feito uma modelagem de ameaças (por exemplo STRIDE) e as mitigações são incluídas nos requisitos funcionais
- Eliminação das vulnerabilidades
- Códigos legados menos seguros são eliminados e substituídos por novas abordagens

### Secure By Default

- Na prática, o software não atingirá uma segurança perfeita; 
- portanto, os designers devem considerar a possibilidade de haver falhas de segurança.
- Aqui são considerados:
	- **Princípio do privilégio mínimo**
	- **Defesa em profundidade**
		- Várias camadas de segurança
	- **Falha segura**
		- Exemplo: Se o sistema de autorização falhar, deverá negar todas as solicitações
	- **Desativação de Funcionalidades Inseguras**: Funcionalidades não utilizadas ou desnecessárias que possam introduzir vulnerabilidades devem ser desativadas por padrão.
	- **Configurações Seguras**: As configurações padrão devem ser as mais seguras possíveis, reduzindo a superfície de ataque.

### Secure In Deployment

- Visa garantir que ele permaneça seguro em ambientes de produção
	- **Ambiente Seguro**: Configurar o ambiente de execução de forma segura, incluindo sistemas operacionais, servidores e redes.
	- **Atualizações e Patches**: Garantir que o software e todos os componentes subjacentes estejam sempre atualizados com os patches de segurança mais recentes.
	- **Monitoramento e Auditoria**: Implementar sistemas de monitoramento contínuo e auditoria para detectar e responder a incidentes de segurança em tempo real.
	- **Backups e Recuperação**: Estabelecer procedimentos robustos de backup e recuperação para proteger contra perda de dados e garantir a continuidade dos negócios em caso de incidentes.

### Communications

- Resposta
	- Os times de desenvolvedores deverão responder prontamente a reportes de vulnerabilidades e comunicar sobre atualizações de segurança
- Engajamento
	- Os desenvolvedores agem de forma proativa junto aos usuários para responder questões sobre segurança, vulnerabilidade e atualizações

## Princípios de privacidade

- São análogos aos princípios de segurança
- Conhecidos como **PD3 + C**

### Privacy by Design

- Notificação e consentimento
	- Notificar sobre a coleta e especificar quais dados serão coletados, armazenados, compartilhados
- Habilitar política e controle de usuário
	- Pais podem gerenciar configurações de privacidade para seus filhos
	- Empresas podem gerenciar estas configurações para seus empregados
- Minimizar coleta de dados sensíveis
- Proteger o armazenamento e transferência de dados

### Privacy by Default

- Software entregue com configurações mais conservadoras possíveis
- Obter consentimento antes de coletar ou transferir dados

### Privacy in Deployment

- Disponibilizar guias de deploy

### Communications

- Estabelecer um time de resposta para incidentes de privacidade de dados

## Atividades de Suporte e Resposta

### Treinamento

- Treinamentos nas áreas de:
	- Secure Design
	- Modelagem de ameaças
	- Desenvolvimento seguro
	- Testes de segurança
	- Privacidade

### Resposta

- Os softwares e serviços são monitorados após o lançamento

## Fases

### **Requisitos**

- requisitos de segurança e privacidade claramente definidos
- definem estes requisitos com base em fatores como:
	- o tipo de dados que o produto irá processar, 
	- ameaças conhecidas, 
	- melhores práticas, 
	- regulamentos e requisitos do setor
	- lições aprendidas com incidentes anteriores
- Uma vez definidos, os requisitos devem ser claramente documentados e controlados

### **Projeto / Design**

- **Foco no modelo de ameaças**
- decidir os parâmetros principais, como arquitetura, plataforma e interfaces de usuário.
- Os modelos de ameaças têm de ser **mantidos e atualizados **ao longo do ciclo de vida de cada produto à medida que são feitas alterações ao software.
- Definidos a partir dos componentes e integrações
- São utilizados DFD´s

### **Desenvolvimento**

- Garantir que o código-fonte siga boas práticas de segurança
- Verificações de segurança incorporadas na IDE

### Verificação

- verificações automatizadas e estão **incorporadas no pipeline** para analisar código
- são realizadas revisões manuais por profissionais separados
- Atividades
	- SAST
	- **Análise binária**: avalia as vulnerabilidades ao nível do código binário
	- Scanner de credenciais e segredos
	- Análise de encriptação
	- Teste de Fuzzing
	- Validação de configuração
	- **Governação de Componentes (CG)**: deteção de software open source e verificação da versão, vulnerabilidade e obrigações legais.
	- Testes de penetração

### Release

- Depois de passar todos os testes e revisões de segurança necessários, as compilações não são imediatamente lançadas para todos os clientes
- As compilações são lançadas sistematicamente e **gradualmente **para grupos maiores e maiores, referidos como anéis, no que é chamado de processo de implementação segura (SDP).
	- **Cadência 0**: a equipa de desenvolvimento responsável pelo serviço ou funcionalidade
	- **Anel 1**: Todos os funcionários da Microsoft
	- **Anel 2**: utilizadores fora da Microsoft que tenham configurado a sua organização ou utilizadores específicos para estarem no canal de lançamento direcionado
	- **Anel 3**: lançamento padrão mundial em sub fases

# CLASP (Comprehensive, Lighweight Application Security Process).

- metodologia de desenvolvimento seguro de software orientada a atividades e papéis
- Antecessor do OWASP SAMM
- provê um guia para participantes de um projeto
- É dividido em 5 visões que contém processos cada uma
	- Visão conceitual
	- Visão de papéis
	- Visão de avaliação de atividade
	- Visão de implementação de atividade
	- Visão de vulnerabilidades

# Shift Left Security

- Conceito parecido com DevSecOps
- Pensando em DevOps, Shift Left Sec é trazer a preocupação com segurança para o lado esquerdo do gráfico
- Prover ferramentas que possibilitem a prevenção e implementação de segurança já das etapas de Dev

![[Untitled 367.png]]

![[Untitled 368.png]]

# DevSecOps

![[Untitled 369.png]]

- **Na prática significa incorporar ferramentas como SAST, DAST e SCA no pipeline**
- Pilares do DevOps
	- Velocidade
	- Entrega rápida e contínua (CI/CD)
	- Confiabilidade
- Pilares do DevSecOps
	- Segurança em primeiro lugar
	- Velocidade
	- Entrega rápida e contínua (CI/CD)
	- Confiabilidade
- Na prática, DevSecOps torna aceitável uma degradação do segundo pilar (velocidade) em troca de priorizar a segurança
- Automatizar testes de segurança na esteira CI/CD
	- Para cada estágio da pipeline haverá uma ferramenta
	- Por exemplo:
		- Anti-vírus scan
		- SAST
		- Busca por credenciais
- Segurança vem primeiro!
	- Neste caso, a afirmação é prática pois as auditorias de segurança devem vir antes mesmos dos testes em uma esteira CI/CD
	- Princípio do Falhe Rápido

## AST (Application Security Testing)

- **O que é**: AST é um termo genérico que engloba todas as abordagens de teste de segurança de aplicações, incluindo SAST, DAST, IAST (Interactive Application Security Testing), e outras metodologias.
- **Como funciona**: AST pode combinar diferentes métodos de teste para fornecer uma visão mais abrangente da segurança da aplicação.
- **Benefícios**: Permite uma abordagem mais holística e abrangente para identificar vulnerabilidades em diferentes estágios do ciclo de desenvolvimento.
- **Limitações**: Pode ser complexo e exigir a coordenação de várias ferramentas e técnicas.

### SAST

- Static Analisis Software Testing
- Foco em **código proprietário**
- Tem como objetivo identificar as vulnerabilidades no seu código-fonte antes de ele ser colocado em produção. 
- É como uma revisão direta do código-fonte. Para isso são usadas técnicas de análise de código estático para procurar problemas sem precisar executar o código.
- Um dos aspectos verificados durante a análise estática é a **sintaxe do código-fonte**.
- Deve ser utilizado no início do ciclo
- verificação da **correta utilização dos elementos da linguagem de programação**, como: palavras-chave, construções de controle de fluxo, declaração e definição de variáveis, entre outros.
- Ferramentas de análise estática são capazes de detectar **erros sintáticos** que um compilador também identificaria, além de padrões que, embora possam não ser incorretos do ponto de vista do compilador, podem ser considerados **más práticas de programação.**
- É eficaz em localizar falhas que poderiam levar a vulnerabilidades com CSS, SQL Injection e Buffer Overflow
- Não consegue identificar problemas relacionados ao tempo e ao ambiente
- Normalmente utiliza uma base de referência, como por exemplo o OWASP Top 10
- Principal referência: **SonarQube**

### DAST

- Reste de segurança na qual um aplicativo em execução é testado de fora, o tratando como uma caixa preta.
- Tem por objetivo testar as interfaces expostas em busca de vulnerabilidades. 
- Dessa forma, o teste é feito de fora para dentro, sendo que, nesse caso, a interface já é o suficiente para que o especialista realize o teste.
- software dinâmico de teste de segurança de aplicativos. 
- O DAST **apoia as análises feitas do SAST**
- Deve ser realizado com a aplicação rodando, em ambiente igual ao de produção.
- Esse é um teste mais complexo, e as vulnerabilidades localizadas tendem a ser direcionadas para serem corrigidas somente no próximo começo do ciclo de desenvolvimento.
- Requer conhecimento da tecnologia e framework utilizados
- Principais referências: 
	- OWASP ZAP (Zed Attack Proxy)
	- Burp Suit

![[Untitled 370.png]]

### IAST

- Combina elementos de SAST e DAST
- analisa uma aplicação em tempo real enquanto ela está em execução
- Interage com a aplicação de maneira interna para identificar vulnerabilidades.
- Executado **dentro da aplicação** enquanto ela está rodando. 
- Isso permite que o IAST acompanhe o fluxo de dados através da aplicação e identifique pontos onde os dados entram e saem

### RASP

- *Runtime Application Self-Protection*
- Este tipo de ferramenta analisa o comportamento do aplicativo, implementando uma análise de segurança contínua, sendo uma das tecnologias de segurança usadas em tempo de execução.

### SCA

- Software Composition Analysis
- Identifica todos os componentes **open source** utilizados na base de código e mapeia as vulnerabilidades conhecidas
- As ferramentas mais avançadas são capazes inclusive de identificar “code snippets” copiados de fontes conhecidas

## Container Security

- Principais referências:
	- Aqua Security

## IaC Security

- Provê segurança para a infraestrutura de nuvem
- As ferramentas são capazes de provisionar a infraestrutura, utilizando-se de melhores práticas e padrões de segurança
- Principais referências
	- Terraform
	- Checkov
		- Ferramenta SAST para IaC
		- Suporte a Terraform, CludFormation, Kubernetes

# OWASP SAMM

- Modelo aberto que auxilia organizações a formular e implementar uma estratégia para a segurança de software
- Adaptado aos riscos específicos enfrentados pela organização
- Agnóstico em relação a tecnologias e processos, orientado por riscos e evolução
- É um framework **prescritivo** que fornece um caminho para organizações implementarem práticas de segurança de software de acordo com os melhores padrões da indústria
- Enquanto o BSIMM pode ser usado para benchmarking e referência, o SAMM fornece um roteiro para ação.

## Estrutura

- O SAMM é dividido em 5 áreas de negócio com 3 objetivos cada

![[image 103.png]]

## Áreas

> [!note] 🔥
> **O governo projeta, implementa e verifica as operações**

## Níveis de maturidade

- São 3 níveis:
	- Fundacional
		- Atividades iniciais, básicas, ad-hoc e facilmente executáveis.
	- Maduro
		- Práticas definidas, padronizadas, consistentes e com maior formalização.
	- Avançado
		- Práticas avançadas, otimizadas, integradas, altamente formalizadas e sofisticadas.
- Aplicado a cada prática

# BSIMM

- Building Security in Maturity Model
- Modelo descritivo que fornece uma linha de base de atividades observadas para iniciativas de segurança de software
- Fornece uma análise objetiva e baseada em dados e observações
- Utilizado para benchmarking
- mede a maturidade de um programa de segurança de software contra 126 atividades específicas
- BSIMM é descritivo, não prescritivo, documentando práticas atuais em vez de prescrever o que deveria ser feito.

## Estrutura

- 4 áreas principais
> [!note] 🔥
> **O governador inteligente constrói e implanta**

	- **Governança**
		- Suporte executivo
		- Desenvolvimento de estratégia de segurança de software e realização de avaliações regulares
	- **Inteligência**
		- Coleta de dados e aprendizado contínuo sobre ameaças
	- **Construção**
		- Integrar segurança ao longo do SDLC
	- **Implantação**
		- Práticas de segurança para software em produção
		- Monitoramento de eventos e resposta a incidentes
- 12 categorias (domínios)

# NIST SSDF

[https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-218A.pdf](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-218A.pdf)

- Secure Software Development Framwork
- Conjunto de práticas com o objetivo de auxiliar as organizações a incorporar segurança em todas as etapas do desenvolvimento de software
- Promove a adoção de práticas seguras no ciclo de vida de desenvolvimento de software (SDLC).
- adaptável a empresas de qualquer tamanho e setor.
- Organizações podem personalizar o framework de acordo com suas necessidades e integrá-lo com frameworks existentes como o DevSecOps ou outras abordagens de segurança ágil.
- **BSIMM**: Enquanto o BSIMM se baseia na observação de práticas de segurança em diferentes empresas, o NIST SSDF é **mais prescritivo e normativo,** estabelecendo práticas recomendadas que as organizações devem adotar.
- **OWASP SAMM**: O SSDF e o SAMM (Software Assurance Maturity Model) compartilham o objetivo de melhorar a segurança de software, mas o SSDF tem um foco mais claro em **regulamentos e conformidade de segurança** nacional nos Estados Unidos.

## Organização

- As práticas são organizadas em 4 grupos:
	- **Preparar a Organização (PO)**
		- Garantir que a organização, pessoas e processos estejam preparadas para desenvolvimento seguro de software
	- **Proteger o Software (PS)**
		- Proteger todos os componentes de software contra modificações e acesso não autorizado
	- **Produzir software seguro (PW)**
		- Produzir software bem estruturado com um mínimo de vulnerabilidades de segurança
	- **Responder a vulnerabilidades (RV)**
		- Identificar vulnerabilidades residuais e responder apropriadamente
- Cada prática é definida com os seguintes elementos:
	- Prática
	- Tarefa
	- Exemplo
	- Referência

## Princípios fundamentais

- Melhoria contínua
- Gestão de riscos
- Automação de ferramentas de segurança
- Transparência e comunicação

## Níveis de Implementação

- **Nível 1 - Inicial**:
	- Neste nível, as práticas de segurança são ad hoc e informais. A segurança não é uma prioridade clara, e as equipes podem estar cientes de algumas práticas de segurança, mas não têm uma abordagem estruturada ou documentada.
	- **Características**:
		- Falta de políticas e processos de segurança bem definidos.
		- Reatividade a incidentes em vez de uma abordagem proativa.
		- Dependência de conhecimento informal e experiências pessoais.
- **Nível 2 - Gerenciado**:
	- As práticas de segurança começam a ser implementadas de forma mais organizada e consistente. Neste nível, a segurança é reconhecida como importante, e as equipes têm processos básicos para integrar práticas de segurança no desenvolvimento de software.
	- **Características**:
		- Políticas de segurança e práticas começam a ser formalizadas e documentadas.
		- As equipes realizam avaliações regulares e auditorias de segurança.
		- Um processo básico de gerenciamento de vulnerabilidades é estabelecido, embora a comunicação e a resposta possam ainda ser ineficazes.
- **Nível 3 - Otimizado**:
	- Neste nível, a segurança é uma parte integral e otimizada do processo de desenvolvimento de software. As organizações têm uma abordagem proativa para segurança, com práticas bem definidas e mensuráveis que são continuamente melhoradas com base em feedback e análise.
	- **Características**:
		- Práticas de segurança estão totalmente integradas ao SDLC, com forte colaboração entre as equipes de desenvolvimento, segurança e operações.
		- Uso de ferramentas automatizadas para verificar a segurança de código e dependências.
		- Processo contínuo de

# Segurança da cadeia de suprimento de software

A **Segurança da Cadeia de Suprimento de Software** (ou **Supply Chain Security**) refere-se à proteção de todo o processo envolvido na criação, distribuição e manutenção de software, incluindo todos os componentes, bibliotecas, ferramentas e serviços utilizados para desenvolver e operar o software. Com o aumento da complexidade dos sistemas e a dependência de componentes de terceiros (como bibliotecas de código aberto, APIs e serviços de nuvem), proteger a cadeia de suprimentos tornou-se uma prioridade crítica para garantir a segurança de aplicações modernas.

### Principais Desafios na Cadeia de Suprimento de Software:

1. **Dependências de Terceiros**:
	- A maioria dos softwares atuais é construída com a integração de pacotes de terceiros, bibliotecas de código aberto ou componentes de software que não são diretamente desenvolvidos pela organização. Vulnerabilidades nesses componentes podem comprometer o software como um todo.
2. **Ataques na Cadeia de Suprimento**:
	- Os ataques na cadeia de suprimentos envolvem comprometer componentes ou fornecedores confiáveis que são integrados ao software de uma organização. Exemplos incluem ataques como o **SolarWinds** ou compromissos de repositórios de pacotes como o **npm** ou **PyPI**.
	- Nesse tipo de ataque, um componente legítimo pode ser adulterado em qualquer fase do ciclo de desenvolvimento, resultando na distribuição de código malicioso ou vulnerável.
3. **Falta de Visibilidade e Controle**:
	- Organizações muitas vezes têm pouca visibilidade sobre os processos de segurança dos fornecedores de software que utilizam. Sem o conhecimento adequado da origem e do estado de segurança dos componentes, o risco de introduzir vulnerabilidades ou backdoors é elevado.
4. **Manutenção e Atualizações**:
	- A gestão contínua da segurança de componentes externos, incluindo aplicar patches e atualizações de segurança, é crítica. A falta de um processo eficaz de gerenciamento de atualizações pode deixar sistemas vulneráveis a ataques conhecidos.

### Boas Práticas para Segurança da Cadeia de Suprimento de Software:

5. **Auditoria e Verificação de Componentes**:
	- Implementar verificações regulares para garantir que os componentes utilizados no desenvolvimento do software sejam legítimos e livres de vulnerabilidades conhecidas.
	- Ferramentas como **SCA (Software Composition Analysis)** permitem identificar vulnerabilidades em bibliotecas e pacotes de terceiros e fornecem informações sobre licenças e conformidade.
6. **SBOM (Software Bill of Materials)**:
	- O **SBOM** é uma lista formal que documenta todos os componentes e dependências utilizados no desenvolvimento de um software. Ele fornece visibilidade total da cadeia de suprimentos, permitindo que as organizações saibam quais bibliotecas e versões estão sendo utilizadas.
	- O SBOM ajuda a rastrear vulnerabilidades em tempo real e é frequentemente exigido para conformidade em setores regulados.
7. **Zero Trust**:
	- Adotar uma abordagem de **confiança zero** em relação à cadeia de suprimentos significa não confiar implicitamente em nenhum componente, mesmo que seja de um fornecedor confiável. Em vez disso, realizar verificações e auditorias contínuas para validar a integridade e segurança do código.
8. **Assinaturas Digitais e Integridade do Código**:
	- Garantir que todos os pacotes e atualizações de software sejam assinados digitalmente, para que os desenvolvedores e equipes de operação possam verificar a autenticidade e a integridade de um componente antes de usá-lo ou distribuí-lo.
	- Ferramentas como o **SLSA (Supply Chain Levels for Software Artifacts)** e **in-toto** ajudam a estabelecer e garantir cadeias de confiança no processo de desenvolvimento.
9. **Gestão de Riscos com Fornecedores**:
	- Avaliar regularmente os fornecedores de software e suas práticas de segurança para garantir que eles mantenham padrões de segurança compatíveis com as expectativas da organização.
	- Acordos de nível de serviço (SLAs) que incluem cláusulas de segurança e auditoria de código são uma prática recomendada.
10. **Monitoramento e Resposta a Incidentes**:
	- Estabelecer um processo contínuo de monitoramento para detectar atividades suspeitas ou anômalas dentro do pipeline de desenvolvimento, incluindo o uso de sistemas de segurança como **CI/CD security tools**.
	- Desenvolver um plano robusto de resposta a incidentes que cubra cenários de comprometimento de componentes da cadeia de suprimentos.

### Padrões e Frameworks Relacionados à Segurança da Cadeia de Suprimento:

11. **NIST SSDF (Secure Software Development Framework)**:
	- Como mencionado anteriormente, o NIST SSDF define práticas que podem ser aplicadas para melhorar a segurança de software em todo o ciclo de vida de desenvolvimento, incluindo a gestão segura de componentes de terceiros.
12. **CISA – Cybersecurity & Infrastructure Security Agency**:
	- A CISA tem publicado diretrizes específicas para melhorar a segurança da cadeia de suprimentos, especialmente após incidentes de grande escala como o ataque à SolarWinds.
13. **OWASP Dependency-Check**:
	- Uma ferramenta que ajuda a verificar automaticamente bibliotecas e dependências de software em busca de vulnerabilidades conhecidas.
14. **ISO/IEC 27001**:
	- Embora seja um padrão mais geral de gestão de segurança da informação, a ISO/IEC 27001 cobre aspectos relacionados à segurança na cadeia de suprimentos, exigindo que as organizações avaliem e gerenciem os riscos associados a fornecedores.

### Exemplos de Ataques à Cadeia de Suprimento:

- **Ataque SolarWinds (2020)**: Um dos maiores exemplos de ataque à cadeia de suprimento, onde hackers comprometeram o software de monitoramento Orion da SolarWinds, inserindo código malicioso que foi distribuído para milhares de clientes, incluindo agências governamentais.
- **Ataques em repositórios de pacotes**: Hackers comprometem bibliotecas populares em repositórios de pacotes como **npm** ou **PyPI**, injetando código malicioso que é baixado inadvertidamente por desenvolvedores que confiam nesses pacotes.

# SDLC Segundo a ISO 27002

## Separação dos Ambientes

- Desenvolvimento, teste, produção
- Definir regras para implementar e autorizar a implantação de software de desenvolvimento para produção
- Exibir etiquetas de identificação do ambiente nos Menus
- Em alguns casos, a distinção entre ambientes de desenvolvimento, teste e produção pode ser deliberadamente acobertada

## Princípios de arquitetura e engenharia de sistemas seguros

- Princípios de engenharia segura que devem ser observados
	- Segurança por design
	- Defesa em profundidade
	- Segurança por padrão
	- Negar por padrão
	- Falhar com segurança
	- Desconfiar de entrada de aplicações externas
	- Segurança na implantação
	- Assumir violação
	- Menor privilégio
	- Usabilidade e capacidade de gerenciamento
	- Menor funcionalidade
- Princípios de confiança zero
	- Não depender da segurança do perímetro da rede
	- Nunca confie, sempre verifique
	- Criptografia ponta-a-ponta
	- Verificar cada solicitação a um sistema como se tivesse se originado de uma rede aberta e externa
	- Privilégio mínimo
	- ABAC
- Técnicas como virtualização podem ser usadas para evitar interferências entre aplicações em execução no mesmo dispositivo físico

## Codificação segura

- Convém que os princípios de codificação segura sejam utilizados tanto em novos projetos quanto os de reutilização
- Recomenda-se
	- Programação em duplas
	- Refactoring
	- Revisão por pares
	- iterações de segurança
	- TDD
- SAST pode identificar vulnerabilidades de segurança no software

## Segurança da informação no gerenciamento de projetos

- Riscos de segurança tratados em estágio inicial e periodicamente
- Incluindo propriedade intelectual
- Responsabilidades e autoridades definidas e alocadas a papéis especificados

## Testes de segurança em desenvolvimento e aceitação

- Realizados com um conjunto de requisitos (funcionais ou não funcionais)
- Devem ser incluídos
	- Funções de segurança (autenticação, restrição de acesso e uso de criptografia)
	- Codificação segura
	- Configurações seguras (SO, firewalls, etc)
- Os testes devem ser realizados inicialmente pela equipe de desenvolvimento
- Podem existir vários ambientes de teste, usados para diferentes testes

## Repositórios seguros para código-fonte e configuração

- Controle de acesso ao código fonte
- Com base em papéis
- Processo para impor configuração definida
- Alterações na configuração deverão seguir o processo de gestão de mudanças
- A gestão de configurações pode ser integrada aos processos de gestão de ativos e ferramentas associadas

## Desenvolvimento terceirizado

- Requisitos contratuais
- Provisão do modelo de ameaças a ser considerado pelo desenvolvedor externo
- Contratos de custódia para o código-fonte