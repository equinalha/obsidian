---
base: "[[Simulados.base]]"
Banca: CEBRASPE
Obs: ""
Tipo: Certo/Errado
"% Colocação": -100
Status: Done
---
### **Bloco 1**

Julgue os próximos itens, relativos a redes de computadores e sistemas distribuídos.

**51 Para que um servidor SNMP identifique a diminuição de tráfego em uma linha de dados, é necessário que esse tráfego seja uma das variáveis configuradas na MIB (management information base) do referido servidor.**

Certo.

MIB, ou Management Information Base (Base de Informações de Gerenciamento), é uma estrutura de dados hierárquica que define os objetos que podem ser gerenciados em um dispositivo de rede. Ela descreve os parâmetros e suas propriedades que podem ser monitorados e controlados através do SNMP, permitindo aos administradores de rede obter informações e gerenciar dispositivos de rede de forma remota.

Não vejo motivos para invalidar a questão, senão pela redação que ficou estranha ao mencionar “do referido servidor” ao final, sendo que nenhum servidor foi mencionado. Mas se for este o caso, o correto seria a anulação da questão e não a alteração do gabarito.

Gabarito da banca: Inicialmente dada como “Certo”, porém alterado para “Errado” no gabarito definitivo.

**52 Nas redes com topologia em barramento, a informação é transmitida a partir dos vários nós de rede, não havendo necessidade de controle de colisão dos pacotes.**

Errado.

Em uma rede com topologia do tipo barramento, todos os nós estão ligados a um meio de transmissão comum. Quando duas estações transmitem ao mesmo tempo, ocorre o que chamamos de colisão.

Justamente pelo fato do barramento ser um ambiente comum a todos, é necessário que haja um controle de colisões a fim de detectar quando dois pacotes de dados são colocados simultaneamente neste barramento.

**53 RSVP (resource reservation protocol) é o protocolo responsável pela reserva de recursos na implementação de serviços diferenciados (Diffserv) em uma implementação de QoS.**

Errado.

DiffServ e IntServ são implementações responsáveis por permitir qualidade de serviço (QoS) no protocolo IP. No DiffServ o nível de qualidade é alcançado pela técnica do melhor esforço. São atribuídos níveis de prioridade aos pacotes que os roteadores tentarão atender da melhor forma possível.

Já no IntServ, a qualidade é garantida por meio de um protocolo de reserva de banda. É feita uma negociação prévia com os roteadores pelo qual os dados vão trafegar, utilizando o RSVP. Portanto RSVP está relacionado ao IntServ e não ao DiffServ.

**54 Uma requisição de resolução de nomes via DNS (domain name service) pode utilizar tanto a porta 53/TCP quanto a porta 53/UDP para resolver a requisição; caso o tamanho da mensagem de resposta seja superior a 512 bytes, a conexão TCP deverá ser utilizada, necessariamente.**

Errado.

É correto que mensagens maiores que 512 bytes devem acontecer via TCP, no entanto esta não é a única situação. Existe outra comunicação que ocorre sempre via TCP independente do seu tamanho que é a troca de zonas entre servidores DNS.

A respeito da configuração do servidor Apache, julgue os itens subsequentes.

**55 A diretiva de configuração SSLEngine deve receber como parâmetro o caminho da chave privada do certificado digital que será utilizado para o servidor.**

Errado.

A diretiva SSLEngine na configuração do Apache habilita ou desabilita o suporte ao SSL (Secure Sockets Layer) ou ao TLS (Transport Layer Security) para uma determinada configuração de host virtual (virtual host) e não recebe nenhum parâmetro.

**56 O módulo mod_cache pode ser habilitado para gerenciamento de cache, mas depende da associação com o funcionamento do módulo mod_proxy quando o servidor Apache atua como proxy reverso.**

Errado.

Na verdade o mod_cache funciona de forma independente do mod_proxy. O mod_cache permite que o Apache armazene em cache as respostas de solicitações HTTP para reutilização posterior, mesmo quando não está atuando como um servidor proxy reverso.

**57 Se DirectoryIndex index.html for informado na configuração, o servidor, ao acessar diretórios, buscará por um arquivo de índice com nome index.html.**

Correto.

Esta é a configuração padrão do Apache.

A respeito do Windows 10, julgue os itens seguintes.

**58 No Windows 10, é possível disponibilizar acesso por meio do recurso de área de trabalho remota, que é suportado exclusivamente na versão Professional.**

Errado.

O recurso de área de trabalho remota permite que o usuário acesse sua estação remotamente de outro computador, tendo acesso ao ambiente gráfico completo.

Na verdade, não é exclusividade da versão Professional. Este recurso está disponível também para as versões Enterprise e Education.

**59 Para definir as configurações TCP/IP de uma placa de rede wi-fi utilizando recebimento automático de endereço IP ou definindo um endereço IP estático, é correto acessar por meio do menu Iniciar -> Configurações -> Wi-FI -> Alterar opções de adaptador e, na janela disponibilizada, escolher qual placa de rede deseja fazer as alterações.**

Questão Anulada pois o caminho pode ter sofrido alterações a depender a versão do Windows 10 instalado na máquina.

**60 O cache do DNS é um arquivo que associa nomes de hosts e endereços IP dos endereços que foram visitados; o comando ipconfig /flushdns permite limpar esse cache, no Windows 10.**

Correto.

O ipconfig é uma ferramenta de linha de comando utilizada no sistema operacional Windows para exibir informações sobre a configuração de rede do computador. Quando utilizado com o parâmetro /flushdns permite efetuar a limpeza do cache de DNS.

Este comando também funciona em várias outras versões do windows.

Julgue os itens a seguir, relativos a gerenciamento do ciclo de vida do sistema.

**61 Durante o desenvolvimento do sistema, os testes podem ocorrer no nível de componentes e no nível unitário: no primeiro caso, o foco é testar as interfaces dos componentes; no segundo, o foco é testar a funcionalidade dos métodos.**

Correto.

Testes de software são importantes no desenvolvimento de software, e permitem antecipar erros e reduzir o risco. No primeiro caso os testes podem ser considerados de caixa branca ou preta. Já no segundo caso são testes de caixa branca predominantemente.

**62 Apenas um requisito não funcional de segurança pode afetar a arquitetura geral de um sistema inteiro; em função dele, pode-se gerar uma série de requisitos funcionais relacionados, assim como requisitos que restrinjam os já existentes.**

Correto.

A engenharia de requisitos é a disciplina responsável por propor métodos e ferramentas eficientes para o levantamento de requisitos de software. Requisitos podem ser funcionais ou não funcionais.

Requisitos funcionais descrevem o que o sistema deve fazer, enquanto requisitos não funcionais especificam como o sistema deve se comportar em termos de desempenho, segurança e usabilidade. Requisitos não funcionais podem alterar profundamente o desenvolvimento do software e por este motivo devem ser tratados logo no início do projeto, diminuindo assim os riscos.

Julgue o item seguinte, relativo a gerenciamento de projeto.

**63 Gerenciar o escopo do projeto abrange a definição e o controle do que está e o que não está incluído no projeto, incluindo a criação da estrutura analítica do projeto e a coleta de requisitos.**

Correto.

O gerenciamento do escopo do projeto inclui a definição clara de tudo que está no projeto, mas também o que não está.

Quanto à estrutura analítica ou EAP, trata-se de uma ferramenta utilizada para dividir o escopo do trabalho em pequenos pacotes de trabalho, mais facilmente gerenciados.

![[Untitled 854.png]]

Considerando os dados na tabela precedente para a montagem do diagrama de rede de um projeto hipotético, e que as atividades INÍCIO e FIM devem ser consideradas apenas para melhor organização do diagrama, julgue os itens que se seguem.

**64 O caminho crítico do projeto é formado pelas atividades CDH.**

Errado.

O fato da atividade D não depender de C já invalida o enunciado, uma vez que CDH não configura um caminho.

**65 As atividades F e G são executadas em sequência.**

Errado.

F depende tão somente de C, que por sua vez é executada no início do cronograma. Já G depende de D que por sua vez depende de A que é executada no início do cronograma. Sendo assim, estas tarefas não configuram uma sequência.

**66 A duração estimada do projeto é de 25 meses.**

Errado.

Para avaliar a duração estimada precisamos encontrar o caminho crítico que é o maior caminho traçado pelas atividades e que representa a maior duração. Podemos traçar alguns caminhos no diagrama:

ADG: 14 meses

CEH: 15 meses

CFI: 9 meses

Assim, logo identificamos que o caminho crítico é o que passa pelas atividades C, E e H e que tem uma duração de 15 meses, definindo assim a duração estimada do projeto.

Com relação à segurança física e lógica e à operação de segurança da informação, julgue os itens a seguir.

**67 A despeito de sua capacidade de agregação e correlação automatizada de dados de eventos provenientes de várias fontes, as soluções SIEM são ineficazes em processos de coleta e verificação de dados de conformidade no âmbito da infraestrutura de negócios.**

Errado.

SIEM, ou Security Information and Event Management, é uma solução de segurança cibernética que combina duas áreas distintas: Gerenciamento de Informações de Segurança (SIM) e Gerenciamento de Eventos de Segurança (SEM). Essa integração proporciona uma visão abrangente das atividades de segurança em uma rede, permitindo a detecção, resposta e relato de incidentes de segurança.

Estas soluções são muito eficazes na coleta e verificação de dados.

**68 A proteção de perímetro é usada para dissuadir invasões e para possibilitar que as pessoas utilizem entradas controladas para entrar em uma instalação.**

Correto.

A proteção de perímetro é alcançada com o uso de barreiras e dispositivos físicos de proteção. Essas barreiras podem incluir cercas, portões, controles de acesso, câmeras de vigilância, sistemas de alarme e outros dispositivos de segurança.

Julgue os itens subsecutivos, a respeito de softwares maliciosos e ataques.

**69 Entre as contramedidas técnicas relacionadas à prevenção contra ataques DDoS, estão a restrição de tráfego ICMP e UDP desnecessário em roteadores de perímetro e a desabilitação de serviços e subsistemas não utilizados em computadores e servidores.**

Correto.

O primeiro caso é utilizado para proteção contra ataques do tipo smurf, ping of death dentre outros. Já no segundo caso, o objetivo é reduzir a superfície de ataque deixando menos serviços expostos na rede.

**70 Vírus polimórficos escondem as modificações maliciosas que realizaram em arquivos ou setores de boot, interceptando as funções de leitura do sistema para apresentar resultados forjados em lugar dos dados reais afetados.**

Errado.

Vírus polimórficos são aqueles que conseguem mudar sua assinatura, dificultando a detecção.

Acerca de MFA, julgue o item a seguir.

**71 Soluções de MFA com dependências externas aos sistemas incluem o risco de introduzir vulnerabilidades de segurança passíveis de exploração por atacantes.**

Correto.

MFA significa Multiple Factor Authentication ou Autenticação por múltiplos fatores. Seu conceito envolve a autenticação por meio de dois ou mais fatores, cada um em um dos paradigmas abaixo:

- Algo que você sabe (como senha, ou PIN)
- Algo que você possui (smartphone, token)
- Algo que você é (biometria)

Algumas soluções de MFA dependem de provedores externos para enviar códigos de verificação por SMS, e-mails ou aplicativos de autenticação. Se os sistemas desses provedores forem comprometidos ou se os canais de comunicação forem interceptados, os atacantes podem comprometer a autenticação de dois fatores.

Julgue os próximos itens relacionados a network-attached storage (NAS) e storage area network (SAN).

**72 Uma SAN combina armazenamento, processamento e rede em um único sistema, o que permite armazenamento definido por software e virtualização de redes.**

Errado.

Uma SAN é uma infraestrutura similar à rede LAN tradicional, porém pode utilizar meios físicos diferentes como fibra óptica e uma pilha de protocolos próprios. Ela não é responsável por processamento de dados e nem virtualização de redes.

73 Um servidor NAS contém unidades de armazenamento, processador e RAM, e pode ser acessado pelos clientes por meio de protocolos de transferência de dados através de uma rede de computadores, permitindo que os clientes armazenem dados ou compartilhem arquivos.

Correto.

Esta é a definição de NAS. Na prática trata-se de um dispositivo com poder computacional semelhante a um computador, porém dedicado ao armazenamento de dados. Ele pode ser acessado pela rede local tanto para o gerenciamento quanto para o armazenamento e recuperação dos dados.

Julgue os itens a seguir a respeito de virtualização.

**74 A virtualização de rede interna combina sistemas fisicamente ligados à mesma rede local (LAN) em redes locais virtuais (VLANs) separadas, o que permite melhorar a eficiência por meio de segmentação de redes.**

Errado.

VLANs ou Virtual LAN são segmentações de uma rede local ao nível lógico, normalmente feitas pelos switches de rede.

Embora VLANs realmente sejam utilizadas para segmentar redes, isto não está relacionado ao conceito de virtualização de redes.

**75 Hypervisor é o processo que cria e executa máquinas virtuais (VMs); ele funciona como um monitor da VM, compartilhando virtualmente seus recursos, como memória e processamento.**

Correto.

Hypervisors também são conhecidos por monitor de máquina virtual (VMM) por este motivo.

**76 No hypervisor do tipo bare-metal, os recursos da máquina virtual são programados diretamente no hardware; o hypervisor gerencia o sistema operacional guest, ocupando o lugar do sistema operacional host.**

Correto.

Neste tipo de virtualização não é necessário um SO host e as máquinas virtuais rodam diretamente sobre o hardware físico, com o intermédio do hypervisor.

**77 Diferentemente dos demais tipos de virtualização, na virtualização de dados é possível acessar múltiplas fontes de dados e tratá-las como uma só, sem a necessidade de hypervisor.**

Gabarito da banca: Errado

Meu gabarito: Correto. Tal descrição corresponde à definição de virtualização de dados. Fonte: https://www.ibm.com/br-pt/topics/virtualization

**78 A virtualização de rede permite que funções de rede sejam entregues independentemente do hardware, como uma rede virtual, podendo, inclusive, consolidar redes físicas, subdividir uma dessas redes ou conectar máquinas virtuais.**

Gabarito da banca: Anulada

Meu gabarito: Correto pois a descrição corresponde ao modelo de redes virtuais.

### **Bloco 2**

Julgue os próximos itens, relativos à arquitetura de computadores e computação de alto desempenho.

**79 Na implementação de computação de alto desempenho utilizando múltiplos processadores, em todos os casos, o tempo de acesso de determinado processador a uma palavra na memória não difere em relação a outro; a memória do sistema operacional é reservada e protegida, logo, independentemente da posição da palavra na memória, o tempo de acesso à memória será igual.**

Errado.

Isto depende da arquitetura: UMA x NUMA.

- UMA:
	- Utilizam uma topologia de sistema interconectado simples, como barramento compartilhado.
	- Todos os processadores têm acesso igualmente rápido a toda a memória do sistema.
- NUMA:
	- A memória é dividida em vários bancos de memória, com cada banco associado a um conjunto específico de processadores.
	- Processadores em um nó NUMA têm acesso mais rápido à memória local do que à memória de outros nós.

**80 Ao se incluir um novo computador em um cluster escalável, o balanceamento de carga deve incluir automaticamente esse computador no agendamento de aplicações entre os computadores disponíveis.**

Correto.

Um cluster escalável é uma infraestrutura de computação distribuída projetada para aumentar sua capacidade de processamento e/ou armazenamento de forma linear, à medida que a demanda por recursos computacionais aumenta. Isso é alcançado adicionando novos nós (máquinas ou servidores) ao cluster conforme necessário, de modo que a capacidade total do cluster cresça proporcionalmente à carga de trabalho.

Um componente fundamental do cluster é o balanceador de carga. Ele distribui o tráfego de entrada de forma equilibrada entre os diversos nós do cluster, garantindo assim uma distribuição uniforme da carga de trabalho.

Sendo assim, sempre que for adicionado um novo nó ao cluster, este deverá ser incluído também na política de agendamento do balanceador Desta forma as cargas de trabalho poderão ser divididas entre todos os nós do cluster.

**81 Em uma arquitetura de cluster computacional, os computadores individuais podem ser conectados por hardware de comutação tal que a camada intermediária de software em cada computador possibilita a operação do cluster, o que fornece uma imagem unificada do sistema para o usuário e alta disponibilidade pelo balanceamento de carga.**

Correto.

Em um cluster, os nós são conectados por hardware de comutação, como switches de rede, para facilitar a comunicação entre eles. Isso permite uma alta taxa de transferência de dados e baixa latência. Com relação à camada intermediária, ela é responsável por coordenar a comunicação e a cooperação entre os nós. Esta camada de software pode incluir sistemas de gerenciamento de cluster, middleware ou sistemas operacionais distribuídos que permitem a operação coesa do cluster como uma única entidade.

Tendo como referência as principais fases no ciclo de vida do DevOps, julgue os itens subsequentes.

**82 Uma das vantagens do modelo DevOps para desenvolvimento de soluções em cloud computing é a possibilidade de automação de atividades no fluxo de desenvolvimento, na qual se prescinde a fase de teste, até a entrega para o cliente e o feedback da implementação.**

Errado.

DevOps é uma cultura e conjunto de práticas que promovem a colaboração entre equipes de desenvolvimento de software (Dev) e operações de TI (Ops), visando acelerar a entrega de software, aumentar a frequência de lançamentos e melhorar a qualidade dos produtos de software.

A fase de testes é integrante do ciclo DevOps e não deve ser prescindida.

**83 A integração e a entrega contínuas (CI/CD) devem ser implementadas na etapa operar (operate), na qual de fato a solução de software é entregue ao cliente.**

Errado.

Continuous Integration está associado ao lado Dev do ciclo DevOps e refere-se à prática que se concentra na integração automatizada e frequente de alterações de código em um repositório principal.

Já o Continuous Delivery está associado ao lado Ops e diz respeito à capacidade de implantar continuamente alterações de código em ambientes de teste e produção de forma automatizada e segura.

Julgue os seguintes itens, relativos a contêineres e microsserviços.

**84 Do ponto de vista de framework de arquitetura, os microsserviços são fortemente acoplados e distribuídos; os microsserviços são componentes embutidos em contêineres que trabalham juntos para realizar tarefas específicas.**

Errado.

Microsserviços são uma arquitetura de software onde uma aplicação é dividida em pequenos serviços independentes, cada um executando um processo específico e se comunicando através de APIs. Esses serviços são distribuídos e implantados de forma independente, facilitando a escalabilidade e a manutenção do sistema como um todo.

Microsserviços são realmente distribuídos, porém fracamente acoplados. Cada microsserviço é uma unidade independente de desenvolvimento, implantação e escala. Eles podem ser desenvolvidos, implantados e escalados independentemente uns dos outros.

Além disso, microsserviços são geralmente embutidos em contêineres devido à praticidade, porém não há uma regra que obrigue esta prática.

**85 Um contêiner é um conjunto de processos organizados isoladamente do sistema; todos os arquivos necessários para executá-los são disponibilizados por uma imagem distinta.**

Correto.

Um container é uma unidade de software coesa e integrada, que compartilha recursos computacionais e o kernel da máquina hospedeira. Dentro do container estão encapsulados uma aplicação, suas bibliotecas e dependências de software.

**86 A arquitetura de microsserviços decompõe a aplicação em serviços e pode ser criada e implantada de maneira independente, o que permite executar no DevOps o continuous integration / continuous delivery (CI/CD).**

Correto.

A arquitetura de microsserviços é utilizada para desenvolver uma aplicação com um conjunto de pequenos serviços, cada um funcionando em seu próprio processo. Cada serviço é desenvolvido em torno de um conjunto de regras de negócio específico, e é implementando de forma independente.

Julgue os próximos itens, relativos a computação em nuvem e seus componentes.

**87 A adoção da tecnologia de computação em nuvem traz como benefício, entre outros, o aumento da disponibilidade dos serviços.**

Correto.

A computação em nuvem se caracteriza pela distribuição geográfica de seus datacenters e elasticidade dos serviços, permitindo que os recursos sejam provisionados ou desativados dinamicamente conforme a demanda. Isso ajuda a garantir que os aplicativos permaneçam disponíveis mesmo durante picos de uso ou falhas pontuais.

**88 Serviços com demanda variável, como os portais de comércio eletrônico, podem se aproveitar de ganhos financeiros na implementação de computação em nuvem, já que a empresa não precisa dispor de servidores próprios, que ficam ociosos na época de pouca utilização.**

Correto.

Esta é outra vantagem da nuvem. No modelo On Premises (quando a infraestrutura é local), os recursos de hardware e infraestrutura devem ser dimensionados para atender os maiores picos de demanda. No restante do tempo, este excedente permanece ocioso, o que representa um desperdício de poder computacional e dinheiro.

Já no modelo de nuvem, estes recursos podem ser alocados automaticamente, de forma elástica, garantindo o atendimento das demandas no pico e se ajustando ao uso normal nos demais períodos.

**89 A migração de paradigma no provimento de um serviço de computação em nuvem, de IaaS (Infrastructure as a Service) para SaaS (Software as a Service), por exemplo, não acarreta mudanças significativas na gestão de recursos da prestação de serviços.**

Errado.

No paradigma IaaS, o usuário é responsável por administrar os sistemas operacionais, das máquinas, instalar o conjunto de software e bibliotecas necessárias, configurar, manter, monitorar, e controlar toda sua infraestrutura virtual.

Já no paradigma SaaS, nada disso é necessário. O usuário tem acesso ao produto final, por exemplo um serviço de e-mail, uma aplicação em nuvem, uma suíte de escritório, etc.

A figura a seguir ajuda a entender este conceito:

![[Untitled 855.png]]

**90 O uso da computação em nuvem permite a divisão do provedor de serviços em regiões e zonas, o que aumenta a disponibilidade dos serviços, tendo em vista que, caso ocorra um desastre natural em determinada região geográfica, outro data center do provedor pode assumir o fornecimento dos serviços.**

Correto.

Esta é uma das principais vantagens do uso da nuvem. Também é possível se utilizar da distribuição geográfica para disponibilizar serviços mais críticos o mais próximo possível do cliente final.

Julgue os itens a seguir, a respeito da gestão de segurança e da gestão de custos de serviços de computação em nuvem.

**91 Se o preço de um serviço de contratação de servidores virtuais foi calculado apenas com base no sistema operacional utilizado pelo servidor, então, nesse caso, a definição do preço do serviço está bem dimensionada.**

Errado.

Existem outros fatores que devem ser incluídos no preço final:

- Recursos de Hardware como CPU, RAM, armazenamento e largura de banda.
- Nível de Suporte: Serviços que incluem níveis mais altos de suporte técnico e gerenciamento geralmente têm um preço mais alto. Isso pode incluir suporte 24/7, monitoramento proativo, manutenção de segurança e outras características.
- A localização geográfica dos servidores e a garantia de disponibilidade também podem afetar o preço do serviço. Data centers em regiões de alta demanda ou com infraestrutura premium podem cobrar mais pelos seus serviços.

**92 Em serviços de computação em nuvem, as contas de usuários são criadas para a empresa contratante e não para cada usuário.**

Errado.

Nos serviços de cloud as contas podem ser criadas tanto para administradores como também para os demais usuários.

**93 A garantia de segurança nos serviços de computação em nuvem demanda a instalação de firewall e balanceadores de carga, entre outros, na infraestrutura de tecnologia da informação do cliente do serviço.**

Errado.

A responsabilidade é compartilhada. No modelo de Infraestrutura como Serviço (IaaS), o provedor de nuvem é responsável pela segurança da infraestrutura física subjacente, incluindo a camada de rede. Isso pode incluir a implementação de firewalls, balanceadores de carga físicos e outras medidas de segurança na infraestrutura física. No entanto, a responsabilidade pela segurança da camada virtual, que inclui sistemas operacionais, aplicativos e dados, geralmente recai sobre o cliente do serviço.

Julgue os itens subsecutivos, relativos ao ITIL v3.

**94 O estágio de operação no ciclo de vida do ITIL visa gerenciar os serviços responsáveis pelas atividades do dia a dia, orientando sobre como garantir a entrega e o suporte a serviços de forma eficiente e eficaz em ambientes operacionais gerenciados.**

Correto.

ITIL (Information Technology Infrastructure Library) é um conjunto de práticas e diretrizes para gerenciamento de serviços de TI, que abrange diversos aspectos, como estratégia, desenho, transição, operação e melhoria contínua dos serviços. Ele fornece um framework para alinhar os serviços de TI com as necessidades do negócio, promovendo eficiência, qualidade e controle nos processos de TI.

O estágio de operação abrange atividades relacionadas à execução, monitoramento e controle das operações de serviços de TI, incluindo a resolução de incidentes, o cumprimento de solicitações de serviço, o gerenciamento de eventos, o controle de acesso, a execução de tarefas de rotina e a manutenção da infraestrutura de TI.

**95 No ciclo de vida de operações há quatro funções; a função gerenciamento de operações de TI é responsável por realizar as atividades diárias necessárias para o gerenciamento dos serviços de TI e da infraestrutura de TI de que eles dependem.**

Correto.

O gerenciamento de operação de TI é responsável pela gestão e manutenção da infraestrutura de TI necessária para fornecer o nível de serviços de TI acordado para o negócio. Isso inclui o monitoramento, tratamento de incidentes e recuperação de falhas.

**96 O processo gerenciamento de configuração e de ativo de serviço da transição de serviços é responsável, dentre outros, por gerenciar a implantação de componentes finais no ambiente de produção em conformidade com os requisitos estabelecidos na estratégia e no desenho.**

Errado.

O objetivo do GCAS é identificar, controlar e avaliar os ativos de serviços e itens de configuração (IC), protegendo e garantindo a sua integridade em todo o ciclo de vida do serviço.

Com base no COBIT 4.1, julgue os itens que se seguem.

**97 Em que pese não haver no domínio entregar e suportar processo diretamente relacionado a garantir a segurança dos sistemas, o COBIT trata, por meio da área de foco gestão de risco, a gestão de impacto sobre os negócios de vulnerabilidades e incidentes de segurança.**

Errado.

Existe sim um processo destinado à garantia da segurança de sistemas no domínio DSS do COBIT 4.1. Trata-se do processo DS5: Garantir Segurança dos Sistemas.

**98 Ao processo gerenciar o desempenho cabe assegurar um impacto mínimo nos negócios no caso de uma interrupção dos serviços de TI, provendo à organização a capacidade de recuperação por meio de planos de continuidade.**

Errado.

Esta atribuição é do processo DS4: Assegurar a Continuidade dos Serviços.

**99 No domínio entregar e suportar, há processo específico que visa gerenciar dados, incluindo procedimentos efetivos para becape e recuperação de dados, de modo a assegurar a qualidade e disponibilidade dos dados de negócio.**

Correto.

Trata-se do processo DS11: Gerenciar Dados.

### **Bloco 3**

Acerca do gerenciamento de resposta a incidente e testes de penetração, julgue os itens a seguir.

**100 No teste de penetração de caixa branca não são fornecidas informações prévias à equipe de testadores sobre a infraestrutura de segurança da organização; por isso, vulnerabilidades eventualmente existentes e não descobertas no tempo alocado para o teste poderão permanecer ativas no ambiente.**

Errado.

No contexto de testes de penetração, quanto à visibilidade da infraestrutura interna, existem 3 classificações:

- Testes de caixa branca
- Testes de caixa preta
- Testes de caixa cinza

A descrição dada corresponde a testes de caixa preta. No teste de caixa branca, os profissionais têm acesso à documentação e detalhes sobre os sistemas internos.

**101 Segundo o NIST SP 800-61, é recomendável evitar, sempre que possível e por questões de compartimentação da informação, a integração temporária de especialistas externos à equipe de resposta a incidentes.**

Errado.

Na verdade no trecho abaixo, retirado da norma, é dito justamente o oposto:

"***2.4.3 Incident Response Personnel***

(...) *It may also be helpful to have some team members specialize in particular technical areas, such as network intrusion detection, malware analysis, or forensics. It is also often helpful to temporarily bring in technical specialists that aren’t normally part of the team.*"

Fonte: https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-61r2.pdf

A respeito de políticas de segurança da informação, julgue os itens seguintes, considerando as normas ISO 31000 e ISO 27002.

**102 De acordo com a ISO 31000, para assegurar que as diferentes formas de tratamento de riscos se tornem e permaneçam eficazes, o monitoramento e a análise crítica precisam ser parte integrante da sua implementação.**

Correto.

De acordo com a referida norma:

6.5 Tratamento de riscos

Ainda que cuidadosamente concebido e implementado, o tratamento de riscos pode não produzir os resultados esperados e pode produzir consequências não pretendidas. Monitoramento e análise crítica precisam ser parte integrante da implementação do tratamento de riscos, para assegurar que as diferentes formas de tratamento se tornem e permaneçam eficazes.

**103 De acordo com a ISO 27002, no desenvolvimento de uma política para criptografia, o nível de proteção criptográfica requerido pela organização será identificado com base em uma avaliação de risco.**

Correto.

Deve-se ainda considerar:

- Nível de proteção necessário vs Força do algoritmo aplicado
- Impacto do uso de criptografia em controles que dependam da inspeção de conteúdo, por exemplo, anti-malwares, filtragem de conteúdo

**104 Segundo a ISO 27002, as políticas de segurança da informação devem garantir a estabilidade organizacional, impedindo mudanças no ambiente de gestão e de tecnologia, por meio da análise crítica, e definindo por seus termos as circunstâncias do negócio.**

Errado.

O objetivo não é impedir mudanças, mas sim gerenciá-las. A norma prevê inclusive um controle específico para isso: Gerenciamento de Mudanças, em Controles Tecnológicos.

Quanto à segurança em nuvem e à segurança em IoT, julgue os itens subsecutivos.

**105 A falta de padrões para autenticação e criptografia, combinada à capacidade dos sensores e dispositivos IoT de detectar, coletar e transmitir dados pela Internet representam riscos à privacidade dos indivíduos.**

Correto.

IoT, ou Internet das Coisas, refere-se à interconexão de dispositivos físicos através da internet, permitindo que eles coletem e compartilhem dados entre si e com sistemas externos. Esses dispositivos podem incluir uma ampla variedade de objetos do dia a dia, como eletrodomésticos, veículos, dispositivos médicos, sensores industriais, entre outros.

O uso de dispositivos IoT tem se tornado cada vez mais presente, no entanto, há pouca padronização no mercado sobre isso.

**106 No modelo IaaS, o provedor do serviço de nuvem é responsável pela segurança fundamental do ambiente, enquanto o usuário da nuvem é responsável pela segurança de sua rede virtual e de tudo o que for construído sobre a infraestrutura disponibilizada.**

Correto.

Assim como na questão 93, destacamos que a responsabilidade é compartilhada. No modelo de Infraestrutura como Serviço (IaaS), o provedor de nuvem é responsável pela segurança da infraestrutura física subjacente, incluindo a camada de rede. Isso pode incluir a implementação de firewalls, balanceadores de carga físicos e outras medidas de segurança na infraestrutura física. No entanto, a responsabilidade pela segurança da camada virtual, que inclui sistemas operacionais, aplicativos e dados, geralmente recai sobre o cliente do serviço.

Julgue o item abaixo, a respeito da linguagem SQL.

**107 O comando delete alunos permite apagar uma tabela de nome alunos.**

Errado.

A sintaxe correta seria:

DROP TABLE *alunos*;

Acerca de gerência de transações, modelagem entidade relacionamento e abordagem relacional, julgue os itens subsecutivos.

**108 Atomicidade da transação em um banco de dados ocorre quando todas as operações da transação são refletidas corretamente no banco de dados; ou quando nenhuma delas é refletida.**

Correto.

Trata-se de uma das propriedades ACID que dizem respeito a como as transações de banco de dados devem se comportar. Atomicidade significa que ou todas as operações da transação são realizadas ou nenhuma é realizada, prezando assim pela integridade dos dados.

Imagine que você deseje fazer uma transação bancária de transferência de uma certa quantidade de dinheiro para outra pessoa. Na primeira operação desta transação, a quantidade é subtraída do seu saldo. No entanto, antes que ela seja somada no saldo da outra pessoa, ocorre uma falha e a transação é interrompida.

Se não houvesse atomicidade, seu dinheiro seria perdido e a outra pessoa também não o receberia.

**109 Uma chave estrangeira garante a unicidade de informações em uma tabela.**

Errado.

Este é o conceito de chave primária. A chave estrangeira garante a correta referência a um elemento de outra tabela, normalmente apontando para a chave primária ou chave candidata de outra relação.

**110 Considere que, para uma instância da entidade A, existe zero, uma ou muitas instâncias da entidade B; mas para uma instância da entidade B, existe zero ou uma instância da entidade A. Nesse caso, trata-se de um relacionamento 1:n da entidade A para entidade B.**

Correto.

No modelo entidade relacionamento, a quantidade de relacionamentos que uma entidade pode ter com outra é chamada de cardinalidade. A descrição dada pode ser representada da seguinte maneira:

![[Untitled 856.png]]

Dentro dos parênteses temos as cardinalidades mínimas (à esquerda) e máximas (à direita).

- A está relacionado com no mínimo 0, no máximo N entidades B
- B está relacionado a no mínimo 0 e no máximo 1 entidade A

Fazendo a leitura das cardinalidades máximas, temos um relacionamento 1:N

Quanto a gatilhos (triggers), procedimentos armazenados (stored procedures) e gerência de bloqueios, julgue os itens subsecutivos.

**111 Bloqueio de um banco de dados é gerado para contornar o conflito de consulta simultânea de tabelas por um usuário do aplicativo desenvolvido.**

Errado.

O bloqueio ocorre quando duas ou mais operações tentam modificar o mesmo dado simultaneamente.

**112 Trigger é um tipo especial de procedimento armazenado que é executado em resposta a determinado evento na tabela, como inserção, exclusão ou atualização de dados.**

Correto.

Uma trigger monitora a ocorrência de um determinado evento e, quando disparada, executa as ações que foram programadas. Normalmente são utilizadas para garantir a integridade dos dados ou realizar algum tipo de manutenção em tabelas do banco.

![[Untitled 857.png]]

Tendo como referência o código precedente, julgue os itens que se seguem.

**113 Uma variável do tipo string pode ser descrita como um vetor (array) cujos elementos são caracteres.**

Correto.

Inclusive esta é uma abordagem comum para manipulação de strings. Veja o exemplo:

String texto = "Ola mundo";

System.out.println(texto[4]); // Será impresso "m" no console.

**114 O comando out.println(“background-color: green;”); altera a cor de fundo da página HTML e a deixa na cor verde.**

Errado.

A sintaxe CSS está incorreta, uma vez que é necessário dar um seletor que irá especificar a qual elemento a propriedade "background-color"está relacionada. Neste caso o correto seria:

out.println(“body {background-color: green;”});

**115 A linha String nome = request.getParameter(“nome”); pode ser alterada para String nome = request.getAttribute(“nome”); sem perda de funcionalidade no código.**

Errado.

- request.getParameter() é utilizado para recuperar parâmetros enviados junto com a requisição HTTP, na própria URL. Serão sempre do tipo String.
- request.getAttribute() é utilizado para recuperar atributos de um objeto ServletRequest, que podem ser definidos pelo desenvolvedor da aplicação. São do tipo Object.
