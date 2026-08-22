---
base: "[[Simulados.base]]"
Desempenho: 0.77
Banca: CEBRASPE
Obs: ""
1o Colocado: 0.77
Tipo: Certo/Errado
Obj: TSE
"% Colocação": 0
Status: Done
Data: 2024-10-30
---
62 - O banco de dados PostgreSQL possui um tratamento automático para resolver situações de *deadlock*, embora seja difícil prever qual das transações conflitantes será interrompida.

> O PostgreSQL possui um mecanismo robusto para **detectar e resolver situações de deadlock **de forma automática. Quando duas ou mais transações entram em um estado de espera mútua, o sistema identifica esse impasse e, para restabelecer a consistência, aborta uma das transações envolvidas.
> A escolha da transação a ser abortada é, de fato, **indeterminística**. Isso se dá por diversos motivos:
> 
> - **Complexidade dos Grafos de Espera:** À medida que o número de transações e bloqueios aumenta, o grafo de espera (uma representação visual das dependências entre as transações) se torna cada vez mais complexo. Identificar a transação "culpada" por iniciar o deadlock pode ser computacionalmente caro e, em alguns casos, até mesmo impossível.
> - **Custos de Abortar uma Transação:** O custo de abortar uma transação varia dependendo do trabalho já realizado e das alterações que precisam ser revertidas. Escolher a transação mais "barata" de abortar pode ser difícil de quantificar.
> - **Equidade:** Para evitar que uma mesma transação seja sempre a vítima de um deadlock, os algoritmos de detecção e resolução tendem a escolher aleatoriamente entre as transações envolvidas.

64 - Para facilitar a integração com o Windows, o Kubernetes utiliza armazenamento do tipo NTFS. 

> 
> - Kubernetes é agnóstico em relação ao sistema de arquivos subjacente utilizado para o armazenamento
> - Kubernetes abstrai o armazenamento em volumes e persistent volumes, que podem ser montados em pods
> - Kubernetes oferece suporte a contêineres Windows, e quando utilizado em um ambiente Windows, o NTFS pode ser o sistema de arquivos padrão para esses contêineres.

66 - Na replicação por fluxo do banco de dados PostgreSQL, as alterações são simultâneas tanto no servidor primário quanto no servidor em espera.

> Apesar de serem transmitidas ao servidor em Standby, esta replicação é assíncrona
O primário espera uma confirmação do standby antes de considerar uma transação como concluída. Isso garante que os dados estão em ambos os servidores após o commit, mas pode introduzir latência dependendo da rede e da carga.

67 - No modelo de identidade federada, o provedor de identidades (*identity provider*) fornece uma identidade ao usuário após este passar por um processo de autenticação.

> 
> - **Identidade Federada:** 
>     - É um modelo em que a autenticação e a autorização são delegadas a um serviço externo de confiança, conhecido como Provedor de Identidade (IdP). 
>     - Isso permite que usuários usem a mesma identidade em múltiplos sistemas ou aplicações sem precisar criar credenciais diferentes para cada um.
> - **Provedor de Identidade (IdP):** 
>     - O IdP é responsável por autenticar o usuário. 
>     - Quando um usuário tenta acessar um serviço ou aplicação (chamado *Service Provider* ou SP), ele é redirecionado ao IdP. 
>     - O IdP autentica o usuário (por exemplo, através de um login e senha) e, se a autenticação for bem-sucedida, emite um token de segurança ou afirmação que o SP pode verificar e usar para autorizar o acesso.
> - **Processo de Autenticação:** 
>     - No modelo de identidade federada, uma vez que o usuário é autenticado pelo IdP, este emite uma identidade, geralmente na forma de um token (como SAML, OAuth, ou OpenID Connect). 
>     - Esse token é então usado pelo SP para garantir que o usuário está autenticado e possua as permissões necessárias.
> - Esse modelo é amplamente utilizado em cenários como Single Sign-On (SSO), onde um usuário pode acessar várias aplicações e serviços com uma única autenticação. 

72 - No *deploy *em nuvem, a característica pool de recursos garante que os recursos possam ser provisionados e liberados para que a infraestrutura seja escalável de acordo com a demanda. 

> 
> - **Pool de recursos**: refere-se à capacidade da nuvem de agrupar recursos computacionais (como CPU, memória, armazenamento) em um pool compartilhado que pode ser alocado dinamicamente para diferentes usuários ou aplicações. Isso permite uma utilização mais eficiente dos recursos, mas não implica diretamente na escalabilidade.
> - **Escalabilidade**: é a capacidade da infraestrutura de aumentar ou diminuir recursos de acordo com a demanda. Embora a escalabilidade possa ser facilitada pelo pool de recursos, o conceito de escalabilidade está mais relacionado à capacidade da infraestrutura de atender a variações na demanda, o que depende de outros fatores, como a elasticidade e a automação no provisionamento de recursos.

75 - O conceito de *roles *do banco de dados PostgreSQL pode estar associado a um usuário único ou a um grupo de usuários, conforme o modo de configuração do *role*.

> Um "role" pode ser configurado de maneira que seja atribuído a um único usuário, ou pode ser utilizado como um grupo, ao qual vários usuários podem ser atribuídos. 

80 - Ansible é uma ferramenta escrita em Java e que usa JSON para descrever o estado desejado dos dispositivos e da configuração. 

> 
> - Ansible é escrito em Python.
> - Em vez de JSON, o Ansible usa YAML

86 - O tempo de *lease* em um servidor DHCP corresponde ao período de tempo durante o qual um dispositivo conserva um endereço IP atribuído pelo servidor.

> 
• Após o tempo expirar ele pode solicitar uma nova conexão no mesmo IP ou então se não for mais necessário aquele IP usado volta para a Pool de endereços disponíveis para uso no DHCP

87 - *Cgroups *em contêineres corresponde à política de estruturação de grupos em um único contêiner, com o objetivo de compartilhar todos os recursos disponíveis.

> Cgroups são uma funcionalidade do kernel Linux que permite o agrupamento e a limitação de recursos do sistema, como CPU, memória, e I/O, entre diferentes processos ou grupos de processos.

O objetivo principal dos cgroups é controlar e isolar o uso de recursos entre diferentes grupos de processos. Isso permite limitar a quantidade de CPU, memória, e outros recursos que um grupo de processos pode usar, garantindo que nenhum grupo consuma mais do que sua alocação permitida e evitando que o sistema fique sobrecarregado.

91 - Segurança e qualidade são princípios fundamentais das metodologias ágeis e estão relacionados ao valor agregado que as entregas devem incluir, com foco nos benefícios e na satisfação dos clientes.

> Embora segurança e qualidade sejam importantes em qualquer projeto de TI, a**s metodologias ágeis focam principalmente na entrega rápida e frequente de valor ao cliente, com ênfase em flexibilidade, adaptação a mudanças e satisfação do cliente**. A segurança e a qualidade são consideradas, mas não são necessariamente os princípios fundamentais das metodologias ágeis. O foco principal está em entregar software funcionando e atender às necessidades do cliente, o que pode incluir segurança e qualidade, mas não como princípios fundamentais centrais.

95 - É tendência atual que os escritórios de projetos desempenhem cada vez menos o papel de articuladores junto a líderes, unidades de negócios e proprietários de produtos e passem a focar cada vez mais o desenvolvimento e a entrega de valor e excelência em projetos junto às equipes especializadas.

> uma das principais funções dos Escritórios de Projetos (Project Management Office – PMO) é justamente atuar como facilitadores e articuladores junto aos **stakeholders** (partes interessadas), incluindo **líderes organizacionais, unidades de negócios e proprietários de produtos**. O PMO desempenha um papel fundamental em promover o alinhamento estratégico, garantindo que os projetos estejam diretamente ligados às prioridades organizacionais e oferecendo suporte à governança.

Embora haja uma tendência crescente de foco em **entrega de valor** e **excelência em projetos**, isso não significa que o PMO deixará de atuar como articulador junto aos líderes e demais unidades.

101 - O CSF 2.0, em sua função de identificar, preconiza a utilização das salvaguardas para gerenciar os riscos de segurança cibernética da organização.

> 
> As cinco funções principais do **CSF 2.0** (Cybersecurity Framework) são:
> 
> 1. **Identificar**: Compreender o ambiente organizacional, os ativos críticos e os riscos para priorizar as ações de segurança.
> 2. **Proteger**: Implementar salvaguardas e medidas para garantir a segurança dos sistemas e dos dados.
> 3. **Detectar**: Monitorar continuamente para identificar incidentes de segurança cibernética em potencial.
> 4. **Responder**: Desenvolver e executar planos de resposta a incidentes para mitigar danos e restaurar funções.
> 5. **Recuperar**: Restaurar os serviços e capacidades afetadas após um incidente de segurança.

102 - A governança faz parte do núcleo do CSF 2.0 e estabelece a estratégia voltada para a gestão de riscos de segurança cibernética da organização.

> O NIST Cybersecurity Framework (CSF) é um guia desenvolvido pelo Instituto Nacional de Padrões e Tecnologia dos EUA (NIST) para ajudar as organizações a** gerenciar e reduzir os riscos de segurança cibernética**.
> O framework é estruturado em torno de cinco funções principais: **Identify, Protect, Detect, Respond, e Recover**. Essas funções ajudam as organizações a entender, gerenciar e comunicar o risco cibernético de forma eficaz.
> 
> No CSF 2.0, a **governança** refere-se ao conjunto de políticas, procedimentos e processos que garantem que a segurança cibernética esteja alinhada com os objetivos de negócios da organização. Isso inclui:
> 
> - **Definição da Estrutura de Governança**
> - **Alinhamento com a Estratégia de Negócios**
> - **Gestão de Riscos**
> - **Monitoramento e Melhoria Contínua**
> 
> A governança é um elemento essencial do CSF 2.0, pois estabelece a base para a gestão de riscos de segurança cibernética em uma organização. Ela garante que a segurança cibernética seja tratada de forma estratégica, alinhada com os objetivos de negócios e adaptada para enfrentar as ameaças em constante evolução.
> 
> 
> ![[image 134.png]]
