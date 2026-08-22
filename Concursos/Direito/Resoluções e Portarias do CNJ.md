---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2024-11-20T14:57:00
Owner:
  - Eduardo Quinalha
---
[https://www.cnj.jus.br/tecnologia-da-informacao-e-comunicacao/plataforma-digital-do-poder-judiciario-brasileiro-pdpj-br/capacitacao/](https://www.cnj.jus.br/tecnologia-da-informacao-e-comunicacao/plataforma-digital-do-poder-judiciario-brasileiro-pdpj-br/capacitacao/)

# Res CNJ 522/2023 - MoReq-Jus

- Requisitos para o desenvolvimento de novas soluções (ainda que segmentados ou microsserviços)
- Garantir:
	- Disponibilidade, integridade, confidencialidade, autenticidade, não repúdio, **conformidade** e **preservação**
- Sistemas de gestão de processos e documentos utilizados em atividades** judiciais e administrativas**
- Na especificação e no desenvolvimento de funcionalidade em que se constate** conflito entre requisitos**, deverão ser aplicados os requisitos **não funcionais relacionados à segurança **em detrimento de outros.

## MoReq-Aval

- Programa de avaliação do grau de aderência dos sistemas ao MoReq-Jus
- Executado pela TI do CNJ e apoio do Proname

## MoReq-Jus

[https://atos.cnj.jus.br/files/compilado1741272023101965316a47d262e.pdf](https://atos.cnj.jus.br/files/compilado1741272023101965316a47d262e.pdf)

- Estabelece critérios a serem cumpridos pelos sistemas de gestão de processos e documentos **digitais, não digitais ou híbridos**
- estabelece processos e requisitos mínimos para um Sistema Informatizado de Gestão de Processos e Documentos (GestãoDoc), **independentemente da plataforma tecnológica em que for desenvolvido e implantado**. 
- O MoReq-Jus tem por objetivo fornecer especificações** técnicas e funcionais,** para orientar a aquisição, o detalhamento e o desenvolvimento de sistemas de gestão de processos e documentos no âmbito do Judiciário brasileiro. Também tem por objetivo estabelecer critérios para certificação do grau de aderência ao modelo. 
- O MoReq-Jus é especialmente dirigido a:
	- Potenciais usuários de um GestãoDoc — Na elaboração de um edital de licitação para a apresentação de propostas de fornecimento de software.
	- Usuários de um GestãoDoc — Como base para auditoria ou inspeção do GestãoDoc existente.
	- **Fornecedores e desenvolvedores de sistemas** — Como guia no desenvolvimento de um GestãoDoc em conformidade com os requisitos exigidos.
	- **Profissionais e provedores de serviços de gestão de documentos** — Com vistas a orientar a execução desses serviços a partir de uma abordagem arquivística.
	- Potenciais usuários de serviços externos de gestão de documentos — Guia para a especificação dos serviços a serem adquiridos.
- Objetiva o desenvolvimento e/ou implementação de um RDC-Arq
	- Repositório Arquivístico Digital Confiável
	- desenvolvido como software livre, gratuito e de código aberto, projetado para manter os dados em padrões de preservação digital e o acesso em longo prazo
	- com a aplicação do modelo OAIS (“Open Archival Information System”)
- Organizado em Requisitos Funcionais e Não funcionais
- **Requisitos Funcionais (RF)**
	- Organização dos documentos institucionais
	- Captura
	- Fluxo de Trabalho e Tramitação
	- Avaliação: temporalidade e destinação
	- Pesquisa, localização e apresentação de documentos
	- Segurança: controle de **acessos e auditoria**
- **Requisitos Não Funcionais (RNF)**
	- **Armazenamento**
	- **Preservação**
	- Segurança: **Aspectos estruturais**
	- Disponibilidade
	- Usabilidade
	- **Interoperabilidade**
	- Desempenho e escalabilidade
	- Implementação, manutenção e evolução

# Res CNJ 335/2020 - PDPJ-Br

- Institui a política pública para a governança e gestão de **processo judicial eletrônico**
- A resolução não se aplica às soluções tecnológicas que **não tratam de processo judicial eletrônico **ainda que sirvam ao **Poder Judiciário.**
- Cria o PDPJ-Br
- Mantem o PJe como sistema prioritário de processo eletrônico
- Implanta o conceito de desenvolvimento comunitário
- Estabelece padrões de desenvolvimento, arquitetura e UX
- Institui plataforma única para publicação e disponibilização de aplicações, microsserviços e modelos de IA, por meio de computação em nuvem
- Provida por meio de marketplace de soluções
- Utilização preferencial de tecnologias com código aberto (open source)
- Fica proibida a contratação de qualquer novo sistema, módulo ou funcionalidade privados, mesmo de forma não onerosa, que cause **dependência tecnológica do respectivo fornecedor** e que não permita o **compartilhamento não oneroso **da solução na PDPJ-Br
- A PDPJ-Br será **hospedada em nuvem**, podendo se valer de serviço de computação em nuvem **provido por pessoa jurídica de direito privado**, inclusive na modalidade de integrador de nuvem (broker), desde que observado o seguinte:
	- armazenamento dos dados em datacenter abrigado em território nacional
	- cumprimento da LGPD
	- atendimento aos requisitos de **disponibilidade**, de **escalabilidade**, de **redundância** e de **criptografia**;
	- capacidade de **mensuração de uso** dos recursos da nuvem de forma **individualizada** **por cliente** de cada serviço provido na PDPJ
	- conformidade com as normas técnicas e outras estabelecidas em ato próprio da Presidência do CNJ

## Conceitos para desenvolvimento e adoção de soluções

- **Obrigatórios**
	- Processo eletrônico em plataforma pública
	- Desenvolvimento comunitário que possibilite o compartilhamento entre todos os segmentos e esferas do PJ
	- Ampla cobertura de testes, baixo acoplamento, alta coesão, modularização
	- Mcirosserviços
	- Computação em nuvem
	- Autenticação uniformizada
	- Interoperabilidade
	- Autenticação uniformizada
	- Portabilidade
	- Mobilidade
	- Acessibilidade
	- Usabilidade
	- SI
	- Adaptável ao uso de IA e ML
	- Automação
	- Incremento da robotização e técnicas disruptivas de desenvolvimento de soluções
	- LGPD
- **Preferenciais**
	- Utilização preferencial de tecnologias com código aberto (open source).

## Nuvem Nacional

- A PDPJ-Br proverá aplicações, módulos e microsserviços, em especial o PJe, por meio do conceito de “nuvem nacional”
- O CNJ coordenará as ações para contratação e implantação da nuvem nacional.
- Os custos serão reateados entre os utilizadores

# Portaria CNJ 252/2020 - Modelo de Governança e Gestão do PDPJ-Br

- Requisitos para as soluções a serem integradas ao PDPJ
	- Atendimento aos requisitos da Res 335/2020
	- **Não haver sobreposição** de solução já existente
	- Não haver **dependência compulsória de componentes licenciados**
	- O órgão aderente deve: 
		- possuir propriedade intelectual das aplicações a serem integradas e dispor de autonomia para modificá-las, adaptá-las e criar derivações; 
		- possuir planos de suporte, manutenção e evolução da solução disponibilizada
		- prestar auxílio na coordenação, para fins de colaboração e contribuição de melhorias por outros órgãos, repassando boas práticas, auxiliando o CNJ na gestão de solução de demandas corretivas e implementação de novas funcionalidades
- O uso de componentes licenciados e a integração com soluções proprietárias podem ser admitidos **fora dos serviços essenciais da plataforma**, desde que possam ser **substituídos por outras soluções de código aberto.**

## Rede de Governança do PDPJ-Br

- Composição:
	**I – Comissão Permanente de Tecnologia da Informação e Infraestrutura do CNJ;**
		- Responsável pela coordenação da rede de governança da PDPJ
	**II – Comitê Gestor Nacional da PDPJ;**
		- Membros designados pelo Presidente do CNJ
			- 1 conselheiro do CNJ (presidente do comitê)
			- 2 juízes auxiliares
			- 3 representantes da justiça estadual
			- 1 representante da justiça federal
			- 1 representante da justiça militar
			- 1 representante da justiça do trabalho
			- 1 representante da justiça eleitoral
			- 1 representante da procuradoria geral da república
			- 1 representante do conselho federal da OAB
		- Reuniões ao menos 1 vez a cada bimestre, preferencialmente por videoconferência
		- exercer a supervisão geral da Plataforma
		- sugerir à Presidência o modelo de rateio dos custos da nuvem computacional e, após aprovado, acompanhar sua execução;
	**III – Comitês Gestores dos Tribunais;**
		- Facultativo para TRE e TRT
		-  avaliar as necessidades de evolução e correção dos microsserviços e módulos da PDPJ-Br;
		- propor a organização da estrutura de atendimento às demandas de seus usuários internos e externos, que será responsável pelo atendimento de primeiro e segundo níveis;
	**IV – Gerência Executiva da PDPJ**
		- caberá aos juízes auxiliares da presidência designados como supervisores do Departamento de Tecnologia da Informação
		- subsidiar, promover e acompanhar a definição de tribunais e/ou órgão que ficarão responsáveis pelo desenvolvimento de cada módulo e serviço
	**V – Grupos de Trabalho.**
		- **Grupo Nacional de Gerenciamento, Desenvolvimento e Sustentação,**
			I – corrigir erros e falhas;
			II – assegurar a qualidade dos artefatos depositados, bem como zelar pela estrutura e padrões de arquitetura estabelecidos;
			III – prestar auxílio técnico aos tribunais quando necessário;
			IV – capacitar multiplicadores técnicos, quando demandados pelos Comitês Gestores locais;
			V – supervisionar o desenvolvimento e sustentação do sistema, visando a garantir aderência entre as funcionalidades desenvolvidas e os requisitos definidos;
			VI – garantir o cumprimento dos acordos de níveis de serviço estabelecidos conforme a criticidade das demandas relatadas;
			VII – observar a execução da metodologia de desenvolvimento definida para o projeto; e
			VIII – atuar como prospector de novas tecnologias em áreas de usabilidade, acessibilidade, segurança e performance do sistema, dentre outras.
		- **Grupo Nacional de Requisitos de Negócio**
			- avaliar as demandas de evolução, mudanças ou melhorias e, em caso de acolhimento, sugerir a respectiva priorização ao Comitê Gestor Nacional

# Portaria CNJ 253/2020 - Diretrizes e Critérios PDPJ-Br

- O CNJ fornecerá padronização de API, modelos de dados, eventos e mensagens
- Infraestrutura centralizada de versionamento

## Classificação dos serviços e aplicações

- **Serviços estruturantes**
	- Implementam funcionalidades essenciais básicas para um sistema de processo judicial de tramitação eletrônica
	- Também aqueles necessários à integração, coreografia e interoperabilidade
- **Serviços negociais**
	- Implementam necessidades de negócio relevante para tramitação de processo judicial eletrônico
- **Serviços de integração com sistemas externos**
	- Fazem interface com sistemas externos ao Poder Judiciário
- **Soluções e aplicações da comunidade externa ao judiciário**
	- Desenvolvidos externamente
	- Atendem a necessidades adotando padrões de API que integrem à PDPJ

## Modelo arquitetural e de desenvolvimento

- Arquitetura
	- Microsserviços
	- Stateless
	- REST
	- OpenAPI 3.0
	- OAuth 2.0
	- Kubernetes
	- Acesso de entrada via Gateway
- Plataforma
	- Java (Recomendado)
		- Se utilizado outra linguagem, seguir as orientações técnicas desta portaria
	- Spring + Springboot
	- Projeto de referência: Sample Service
- Metodologia
	- Modelagem por meio de histórias
		- desenvolvedores + Domain experts
	- DDD
	- TDD
		- obrigatória a produção de relatório de cobertura de testes automatizados
	- CI/CD
- Interoperabilidade
	- Coreografia com Mensageria
	- Service Discovery Netflix Eureka

# Portaria CNJ 131/2021 - Grupo Revisor de Código-Fonte

- Seus membros desempenharão suas atividades no grupo em caráter honorífico
- Avaliar os merge requests
- O merge request será aceito se pelo menos **um** tribunal, distinto daquele que desenvolveu a funcionalidade ou solução, aprová-lo.
- O merge request que não for expressamente aceito ou rejeitado **terá sua análise sobrestada automaticamente para a sprint seguinte do Grupo Revisor.**
- Caso o Grupo Revisor não consiga analisar todas as *merge requests* que compõem a *sprint* **quinzenal**, **as que ficarem pendentes terão prioridades sobre as demais na próxima sprint.**
- Caberá aos **coordenadores do Grupo Revisor** priorizar, se for necessário, os merge requests da próxima sprint, conforme critérios objetivos de relevância nacional.
- Sprints de 15 dias
- Coordenado pela DPJe
- Representantes indicados pelo DTI do CNJ e tribunais
- Composição:
	- Membros natos:
		- Servidores lotados na Divisão do PJe
	- 5 (cinco) ou mais servidores indicados pelos Tribunais de Justiça estaduais;
	- 5 (cinco) ou mais servidores indicados pelo Conselho da Justiça Federal;
	- 5 (cinco) ou mais servidores indicados pelo Tribunal Superior Eleitoral; e
	- 5 (cinco) ou mais servidores indicados pelo Conselho Superior da Justiça do Trabalho.
- Quando da existência de soluções concorrentes
	- O grupo revisor realizará testes
	- Não caberá ao grupo a escolha da solução
- Antes de submeter ao grupo, a solução deverá passar por ferramenta de análise automatizada

# Res CNJ 396/2021 - ENSEC-PJ

- Estratégia Nacional de Segurança Cibernética do Poder Judiciário (ENSEC-PJ)
- É estruturada para concretização dos objetivos da PSEC-PJ (Política de Segurança Cibernética do PJ)
- Objetivo de aprimorar o nível de maturidade em segurança cibernética nos órgãos do Poder Judiciário
- Os órgãos do Poder Judiciário, **com exceção do STF,** devem colocar em prática as ações para o pleno alcance dos objetivos da ENSEC-PJ

## Objetivos

- Aprimorar o nível de maturidade em segurança cibernética nos órgãos do PJ
- Concretização dos objetivos instruídos na PSEC-PJE (Política de segurança cibernética do PJ)
- **Objetivos**
	- Tornar o judiciário mais seguro e inclusivo
	- Aumentar a resiliência às ameaças cibernéticas
	- estabelecer governança de segurança cibernética
	- permitir a manutenção e a continuidade dos serviços, ou o seu restabelecimento em menor tempo possível.
- Os órgãos do judiciário deverão colocar em prática as ações
- O engajamento da **alta administração **de cada tribunal é essencial para a consecução das finalidades e das medidas de proteção ao serviço, sobretudo quando implicarem a necessidade de **rápida suspensão do acesso ao público**, para evitar o alastramento de ataque cibernético e conter os danos.

## Ações

- fortalecer as ações de governança cibernética
	- estabelecer um Sistema de Gestão em Segurança da Informação baseado em riscos
- elevar o nível de segurança das infraestruturas críticas
	- instituir ETIR
	- elaborar e aplicar processo de resposta a incidentes
	- Utilização de SIEM e SOAR
	- utilizar tecnologia que permita a inteligência em ameaças cibernéticas em redes de informação; especialmente em fóruns, inclusive da iniciativa privada e comunidades virtuais da internet;
	- Utilização de backups em locais segregados
	- Requisitos específicos de Segurança Cibernética para ativos
	- elaborar requisitos específicos de segurança cibernética relacionados com o trabalho remoto
	- adotar práticas e requisitos de segurança cibernética no desenvolvimento de novos projetos, tais como dupla verificação do acesso externo
	- realizar, ao menos semestralmente, avaliação e testes de conformidade em segurança cibernética de forma a aferir a eficácia dos controles estabelecidos;
	- gestão de incidentes e aprimoramento contínuo
	- troca de informações e boas práticas com outros membros do poder público em geral e do setor privado com objetivo colaborativo.
- estabelecer **rede de cooperação** do Judiciário para a segurança cibernética
- estabelecer **modelo centralizado de governança cibernética nacional**

## Modelo Centralizado de Governança

- Coordenado pelo CNJ
- Objetivos
	- coordenação dos diversos entes relacionados com a segurança cibernética;
	- **análise conjunta do nível de maturidade** em segurança cibernética nos órgãos do Poder Judiciário;
	- estabelecer **padrão de maturidade unificado** de segurança cibernética
	- estabelecer** rotinas de verificações de conformidade** em segurança cibernética
	- convergência de esforços e iniciativas na **apuração de incidentes** e na promoção de ações de **capacitação e educação** em segurança cibernética

## Comitê Gestor de SI do PJ - CGSI-PJ

- Composição
	- 2 especialistas do CNJ
	- 2 do STF
	- 1 do STJ
	- 1 do TSE
	- 1 do TST
	- 1 do Conselho Superior da Justiça do Trabalho
	- 1 do Conselho da Justiça Federal
	- 1 do STM
	- 1 dos Tribunais de Justiça Estaduais
- Coordenado por um representante do CNJ, designado pela Presidência
- Compete ao CGSI-PJ, assessorando o CNJ, nos temas relacionados à segurança da informação
- Os integrantes do CGSI-PJ deverão ter conhecimento técnico na área de segurança da informação.
- Reuniões semestrais
- Competências
	- Estabelecer **norma** sobre a definição dos requisitos metodológicos para a implementação da **gestão de risco dos ativos da informação**
	- Aprovar políticas, diretrizes, estratégias, normas e recomendações 
	- Elaborar e implementar programas sobre segurança da informação destinados à **conscientização e à capacitação **
	- Estabelecer critérios que permitam **monitorar e avaliar** a execução da PSEC-PJ e **nível de maturidade** em segurança da informação
	- Estabelecer norma de criação e funcionamento do Centro de Prevenção, Tratamento e Resposta a Incidentes Cibernéticos do Poder Judiciário (**CPTRIC-PJ**)
	- Troca de informações e experiências com os comitês gestores de segurança da informação dos outros Poderes e com a sociedade

## Rede Nacional de Cooperação

- Objetivos
	- compartilhamento de informações sobre incidentes e vulnerabilidades cibernéticas
	- realizar exercícios cibernéticos com a participação de múltiplos entes;
	- emitir alertas e recomendações de segurança cibernética
	- ampliar parceria com outros órgãos do Poder Executivo, do Poder Legislativo, do Ministério Público, da polícia judiciária, do setor privado e do meio acadêmico
- Todos os órgãos do Judiciário que detectarem incidentes de segurança cibernética deverão reportá-los ao CPTRIC-PJ
- Cada órgão do Poder Judiciário, com exceção do STF, deverá constituir **Comitê de Governança de Segurança da Informação (CGSI)**

## Política de Segurança Cibernética - PSEC-PJ

- Princípios
	- **segurança jurídica**
	- respeito e promoção dos direitos humanos e das garantias fundamentais, em especial a liberdade de expressão, a proteção de dados pessoais, a proteção de privacidade e o acesso à informação (**LGPD**)
	-  visão abrangente e sistêmica da segurança cibernética
	- integração, cooperação e intercâmbio científico e tecnológico relacionado à segurança cibernética entre os órgãos da Administração Pública Federal e do meio acadêmico
	- educação e **inovação** como alicerce **fundamental** para o fomento da cultura em segurança cibernética
	- orientação à gestão de riscos e à gestão da segurança da informação;
	- prevenção, tratamento e resposta a incidentes cibernéticos
	- articulação entre as ações de segurança cibernética e de proteção de dados e ativos de informação
	- garantia ao sigilo das informações imprescindíveis à segurança da sociedade e do Estado e inviolabilidade da vida privada, da honra e da imagem das pessoas
- Objetivos
	- fomentar as atividades de pesquisa científica, de desenvolvimento tecnológico e de inovação
- Instrumentos
	- a Estratégia Nacional de Segurança Cibernética do Poder Judiciário (ENSEC-PJ)
	- o Protocolo de Prevenção de Incidentes Cibernéticos no âmbito do Poder Judiciário (PPINC-PJ)
	- o Protocolo de Gerenciamento de Crises Cibernéticas no âmbito do Poder Judiciário (PGCC-PJ)
	- o Protocolo de Investigação para Ilícitos Cibernéticos no âmbito do Poder Judiciário (PIILC-PJ)

## Gestão de Usuários

- Cada órgão do Poder Judiciário, com exceção do STF, deverá implementar a gestão de usuários de sistemas informatizados composta de
	- Gerenciamento de identidades
	- Gerenciamento de acessos
	- Gerenciamento de privilégios

# Portaria CNJ 162/2021 - Protocolos e Manuais do ENSEC-PJ

## Protocolos

### Prevenção de Incidentes Cibernéticos do Poder Judiciário (PPINC-PJ)

- **Funções**
	- Identificar
	- Proteger
	- Detectar
	- Responder
	- Recuperar
- **Princípios Críticos**
	- Base de conhecimento de defesa
	- Priorização
	- Instrumentos de medição e métricas
	- Diagnóstico contínuo
	- Formação, capacitação e conscientização
	- Automação
	- Resiliência
- **ETIR**
	- Terá** autonomia compartilhada**, ou seja, participará do resultado da decisão recomendando os procedimentos a serem executados ou as medidas de recuperação
durante a identificação de uma ameaça e debaterá sobre as ações a serem tomadas, seus impactos e a repercussão, caso as recomendações não sejam seguidas.
- **Boas práticas**
	- Prevenção de incidentes:
		- Contempla funções:
			- preparação
			- identificação
			- contenção
				- Inclui a comunicação prevista na Estratégia Nacional de Segurança Cibernética do Poder Judiciário (ENSECPJ)
			- erradicação
			- recuperação
			- lições aprendidas
		- As dimensões e práticas poderão ser adaptadas, incrementadas ou ajustadas conforme a realidade de cada órgão

### Gerenciamento de Crises Cibernéticas do Poder Judiciário (PGCRC-PJ)

- Prevê as **ações responsivas** a serem colocadas em prática quando ficar evidente que um incidente de segurança cibernética **não será mitigado rapidamente **e poderá durar dias, semanas ou meses
- Inicia quando
	- Ficar caracterizado grave dano material ou de imagem
	- Restar evidente que as ações de resposta ao incidente cibernético provavelmente persistirão por longo período, podendo se estender por dias, semanas ou meses
	- O incidente impactar a atividade finalística ou o serviço crítico mantido pela organização
	- O incidente atrair grande atenção da mídia e da população em geral.
- **Fases**
	- **Planejamento (pré-crise)**
		- Estabelecimento de um **Programa de Gestão da Continuidade de Serviços**
			- Atividades detalhadas e consolidadas em um plano de contingência
			- Realizar simulações e testes
		- Definir uma **sala de situação** e criar um **Comitê de Crises Cibernéticas**
	- **Execução (durante a crise)**
		- Devem ser efetivados os planos de contingência, visando a continuidade dos serviços
		- Reunião imediata dos membros do comitê de crise na sala de situação
		- Todos os incidentes graves deverão ser comunicados ao CPTRIC-PJ
	- **Melhoria Contínua (pós-crise)**
		- As lições aprendidas devem ser utilizadas para a elaboração ou revisão dos procedimentos específicos de resposta (playbooks) e para a melhoria do processo de
preparação para crises cibernéticas.

### Investigação de Ilícitos Cibernéticos do Poder Judiciário (PIILC-PJ)

- Procedimentos básicos para coleta e preservação de **evidências **e para comunicação obrigatória dos fatos penalmente relevantes ao **Ministério Público** e ao órgão de **polícia judiciária** com atribuição para o início da **persecução penal**
- O horário dos ativos de TI deverá ser sincronizado com a Hora Legal Brasileira, pelo Observatório Nacional
- Deverão ser registrados eventos relevantes de TIC:
	- Autenticações (tanto bem quanto malsucedidas)
	- Acesso a recursos privilegiados
	- Acesso e alteração nos registros de auditoria
- Contendo:
	- Identificação do usuário
	- Natureza do evento
	- Timestamp
	- IP, porta de origem, coordenadas geográficas (Se possível)
- Os sistemas de redes de dados devem ser monitorados e ter logs registrados
- Os registros devem ser armazenados por no mínimo** 6 meses**
	- É recomendado que este armazenamento seja tanto local quanto remoto
- **Coleta e preservação das evidências**
	- Executada pela ETIR
	- Se possível
		- Mídias de armazenamento
		- Dados voláteis (RAM)
	- Se não for possível, devido necessidade de restauração dos serviços:
		- Cópia dos arquivos afetados como logs, configurações, arquivos do sistema de informação
		- As ações de restabelecimento não devem comprometer a coleta e preservação das evidências
	- Para a preservação, deve-se:
		- Gerar lista com hash de todos os arquivos coletados
		- guardar a lista junto com os arquivos coletados
		- Gerar hash da lista
- **Comunicação do incidente**
	- Comunicação imediata ao órgão de polícia judiciária e ao MP
	- Se for considerado crise, acionar o comitê de crise

## Manuais

### Proteção de Infraestruturas Críticas de TIC

- Baseado no **CIS Controls 7.1**
- Agrupamento Basic + controles selecionados:
	- **Agrupamento Basic**
		- Inventário e controle de ativos de hardware
		- Inventário e controle de ativos de software
		- Gerenciamento contínuo de vulnerabilidades
		- Uso controlado de privilégios administrativos
		- Configuração segura para hardware e software em dispositivos móveis, laptops, estrações de trabalho e servidores
		- Manutenção, Monitoramento e Análise de Logs de Auditoria
	- **Controles Adicionais Selecionados**
		- E-mail
		- Proteção de navegador web
		- Defesas contra malware
		- Capacidade de recuperação de dados
		- Proteção de dados
- Categorização apoiada pelo **NIST CSF** para determinação da fase em que o incidente se encontra

### Prevenção e Mitigação de Ameaças Cibernéticas e Confiança Digital

- Trata fundamentalmente de análise de riscos
- Baseado em frameworks de mercado:
	- MITRE ATT&CK
	- Normas ABNT Série 27000
	- NIST SP 800-160 Vol. 2 (Desenvolvendo Sistemas Cyber Resilientes: Uma – Abordagem de Engenharia de Segurança de Sistemas)
- **Princípios**
	- Proteção dos valores organizacionais;
	- Melhoria contínua da organização;
	- Visão sistêmica;
	- Qualidade e tempestividade das informações;
	- Abordagem explícita da incerteza;
	- Transparência;
	- Dinamismo e interatividade;
	- Alinhamento à gestão de riscos corporativos;
	- Integração.
- Metodologias utilizadas para identificação e avaliação de riscos relacionados a ativos de TIC
	- MIA (Mission Impact Analysis)
	- BIA (Business Impact Analysis)
- Princípios de Design da resiliência cibernética
	- Focalizar em ativos comuns e críticos
	- Ter suporte ágil e arquitetura para adaptabilidade
	- Reduzir a superfície de ataque
		- Tokens de conexão temporários
		- Privilégio mínimo
	- Assumir que recursos serão comprometidos
		- Uso de técnicas de modelagem e simulação de impacto
	- Esperar que os adversários evoluam
		- Usar frameworks de ataque como MITRE ATT&CK
		- Implementação de times de ataque (red team) e jogos de guerra
- Resiliência cibernética
	- **Identificar**
		- Inventário de ativos
		- Base de processos
		- Papéis e políticas
		- Documentação das vulnerabilidades
	- **Proteger**
		- Gestão de identidades
		- Gerenciamento e proteção do acesso lógico (Firewall, IPS, WAF)
		- Proteção dos dados tanto em repouso quanto em trânsito
		- Backups
		- Gestão de mudanças
	- **Detectar**
		- Mecanismos de alta disponibilidade
		- Uso de EDR e UEBA (User and Entity Behavioral Analysis)
		- Uso de SIEM
	- **Responder**
		- Plano de resposta (durante e após o incidente)
		- Classificação do incidente
		- Investigação forense
		- Lições aprendidas
	- **Recuperar**
		- PRD
		- Gerenciamento de comunicação ao público

### Gestão de Identidades

- Diretrizes
	- Padronização de nome de usuário e conta de e-mail
	- Privilégio mínimo
	- SSO
	- RBAC
	- MFA
	- Unificação de plataformas de AAA
	- PAM (Privillege Access Management)
	- Rastreabilidade de acessos e ações executadas por administradores de TI
- Tipos de contas
	- **De usuário**
		- Pessoa específica
		- Federada (Preferencialmente) ou local
	- **Compartilhadas**
		- Vários usuários utilizam a mesma identidade
		- Não recomendado
	- **De serviço**
		- Utilizados quando sistemas precisam autenticar em outros sistemas
		- Devem ser documentadas e controladas
		- Revisadas periodicamente
		- Não devem ser utilizadas por pessoas
	- **Privilegiadas**
		- Contas de qualquer um dos 3 tipos anteriores que recebe privilégios adicionais
		- Deve ser limitado
		- Evitar contas compartilhadas ou de sistema, privilegiadas

### Política de Educação e Cultura em Segurança Cibernética do Poder Judiciário

- Estabelece diretrizes para ações de capacitação, educação e cultura de segurança cibernética
