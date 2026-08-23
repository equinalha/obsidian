---
base: "[[ADS - PUC-PR.base]]"
Reviewed: false
Created: 2023-11-20T14:44:00
Status: Not started
Description: ""
---
**Exercícios de Fixação**

Descreva com suas palavras como funciona o algoritmo de criptografia simétrica.

> Utiliza uma mesma chave para criptografar e decriptografar a mensagem

Quais os elementos fundamentais da criptografia simétrica?

> Texto claro, Algoritmo, Chave, Texto Cifrado, Algoritmo de decifração

Quais os dois requisitos necessários para utilização da criptografia simétrica de forma segura?

> Algoritmo forte
As partes devem compartilhar e armazenar a chave por meio seguro

Quais os principais tipos de ataques direcionados a criptografia simétrica?

> Criptoanálise
Força Bruta

Cite 3 algoritmos de criptografia simétrica.

> DES, 3DES, AES

Quais os problemas relacionados a distribuição das chaves na criptografia simétrica?

> A segurança do canal de compartilhamento de chaves
Gerenciamento de múltiplas chaves para múltiplas partes em uma comunicação

O que é um KDC, e para que é utilizado?

> Uma entidade confiável que visa gerenciar o uso de chaves entre partes que desejam se comunicar

Qual a diferença da chave mestra e chave de sessão no KDC?

> Chave mestra: Utilizada na comunicação de cada parte com o KDC
Chave de sessão: Gerada pelo KDC e fornecida aos participantes que desejam comunicar-se entre si

Descreva com suas palavras como funciona o algoritmo de criptografia assimétrica.

> Faz o uso de duas chaves, uma privada (que não pode ser compartilhada) e uma pública, que pode ser distribuída. Um texto cifrado com a chave pública só pode ser decifrado com a chave privada e vice-versa.

Quais os elementos fundamentais da criptografia assimétrica?

> Texto claro
Algoritmo de cifração
Chaves
Texto cifrado
Algoritmo de decifração

Cite 3 algoritmos de criptografia assimétrica.

> RSA, Diffie-Hellman, DSS

Cite 3 aplicações para criptografia de chave pública.

> Compartilhamento de chaves de criptografia simétrica, assinatura digital, Envelopes Digitais

Para que é utilizado a assinatura digital?

> Possibilita garantir integridade e não repúdio de uma mensagem

O que é uma CA?

> Emite, armazena e atesta a veracidade de certificados digitais de chave pública

Para que é utilizado um certificado de chave pública?

> Para garantir a autenticidade da chave e associá-la ao emissor

Para que serve os envelopes digitais?

> Protege uma mensagem sem a necessidade de que emissor e receptor compartilhem uma chave secreta

Quais são as principais abordagens para distribuição das chaves públicas?

> Diretório público
Autoridade de chave pública (CA)
Certificados de chave pública
Anúncio público

---

## **Conceitos de Segurança de Computadores**

A informação é um conjunto de dados que devidamente tratado produz conhecimento, fornece significado e compreensão no contexto que está inserido. Em geral a informação é um elemento extremamente valioso, tanto para um indivíduo quanto para uma organização. A informação é considerada um dos principais ativos de uma empresa, essencial que seja devidamente protegida.

Atualmente, dado o avanço da tecnologia estamos em mundo cada vez mais conectado com a internet, deste modo, a informação se não tratada corretamente pode acabar sendo exposta. Nesta “era digital” existem inúmeras ameaças e vulnerabilidades, proteger a informação tem se tornado um desafio. Para ajudar a vencer este desafio surge a Segurança da Informação.

O conceito de segurança da informação está diretamente ligado à proteção concedida a um conjunto de informações e têm como objetivo preservar o valor que esta informação possui. Deste modo, fornece proteção a informação contra diversos tipos de ameaças, bem como permite garantir a continuidade do negócio e reduzir riscos associados.

A segurança da informação é obtida a partir da implementação adequada de diversos mecanismos de segurança, contemplando políticas, processos, procedimentos, estratégias, estruturas organizacionais e aspectos de configuração de hardware e software. Tais mecanismos devem ser implementados, monitorados e analisados constantemente para garantir a segurança da organização, como também dos objetivos do negócio. Para preservar a informação, a área de segurança de computadores é estruturada sobre três pilares fundamentais, também conhecidos como propriedades de segurança: confidencialidade, integridade e disponibilidade.

![[UE1_img1.jpeg]]

©beebright/Adobe Stock

## **Propriedades de Segurança**

Essas três propriedades de segurança, estabelecem os princípios fundamentais da segurança para proteção dos dados e informações, bem como os serviços de computação a esses associados. Na sequência vamos conhecer cada uma dessas propriedades básicas de segurança.

- **Confidencialidade**
- **Integridade**
- **Disponibilidade**

### **Propriedades de segurança adicionais**

Essas três propriedades básicas de segurança seguem os padrões internacionais definidos na ISO/IEC 27002, formam uma tríade comumente conhecida como CID (confidencialidade, integridade e disponibilidade). Embora a CID tenha sido bem constituída para a fim de atingir os objetivos de segurança da informação, alguns pesquisadores defendem o uso de outras duas propriedades complementares de segurança: autenticidade e legalidade.

- **Autenticidade**
- **Legalidade**

## **Requisitos de Segurança**

É extremamente importante que as organizações identifiquem os requisitos de segurança da informação. Conforme a norma ISO/IEC 27002, os requisitos de segurança da informação podem ser identificados a partir de três fontes:

- Análise e avaliação de riscos da organização alinhados com os objetivos e estratégias de negócio da organização – na análise de risco é realizado a identificação das ameaças e vulnerabilidades aos ativos, onde deve ser realizado uma estimativa da probabilidade da ocorrência de uma ameaça e qual seu impacto ao negócio.
- Legislação vigente, estatutos, regulamentação e cláusulas contratuais da organização (parceiros, contratados e provedores de serviço).
- Conjunto particular de princípios, objetivos e requisitos do negócio para o processamento da informação – o que exatamente a organização tem que desenvolver para apoiar suas operações.

Os resultados obtidos da análise de risco ajudam a determinar ações gerenciais apropriadas, estabelecendo as prioridades dos riscos na implementação dos controles e mecanismos de proteção. Existem vários modos para classificar as contramedidas que são utilizadas para lidar com as ameaças e vulnerabilidades. Seguindo a classificação definida no FIPS PUB 200, as contramedidas são estruturadas em termos de requisitos funcionais, esse padrão lista um conjunto de 17 áreas de segurança que estão relacionadas a proteção dos pilares da segurança (confidencialidade, integridade e disponibilidade). As áreas de segurança da informação estabelecidas no FIPS PUB 200 foram elencadas abaixo.

1. Controle de acesso;

1. Conscientização e treinamento;

1. Auditoria e responsabilidade;

1. Avaliação de certificação, credenciamento e segurança;

1. Gerenciamento de configuração;

1. Planejamento de contingência;

1. Identificação e autenticação;

1. Respostas a incidentes;

1. Manutenção

1. Proteção da mídia;

1. Proteção física e ambiental;

1. Planejamento estratégico;

1. Segurança de pessoal;

1. Avaliação de risco;

1. Aquisição de sistemas e serviços;

1. Proteção de sistemas e comunicações;

1. Integridade de sistemas e informações.

**IMPORTANTE**Na próxima unidade veremos os requisitos funcionais de cada uma dessas áreas, ressaltando as contramedidas adotadas para lidar com as ameaças e vulnerabilidades.

## **Desafios da Segurança de Computadores**

A Segurança da Informação é uma área extremamente fascinante, atualmente em ascensão no mercado de trabalho, setor que busca cada dia mais por profissionais qualificados. Contudo, a área de Segurança da Informação pode ser bastante complexa e desafiadora, exige que o profissional esteja em constante atualização. É uma batalha contra o tempo, enquanto os adversários (crackers/hackers) motivados por uma “sensação” de impunidade exploram brechas de segurança nos sistemas (realizando atividades criminosas para tentar levar vantagem financeira ou por puro vandalismo), o profissional de segurança da informação deve proteger os sistemas computacionais.

![[UE1_img2.png]]

Fonte: Adaptado de Symantec, 2020.

É uma luta constante e diária contra os crimes cibernéticos, pesquisadores na área de segurança demostrar que quase 500 milhões de consumidores foram vítimas de crime cibernético, sendo que quase 350 milhões realizados apenas no último ano [[Norton](https://br.norton.com/nortonlifelock-cyber-safety-report), 2021]. Os dados comprovam a importância e necessidade de profissionais qualificados na área de segurança.

O crime cibernético continua constantemente evoluindo, os criminosos cibernéticos exploram/encontram sempre novas formas de atingirem os consumidores. Em definição os crimes cibernéticos são caracterizados como sendo um crime pessoal cometido por meio de um dispositivo conectado na internet. Em geral, são crimes nos quais um computador é utilizado para prejudicar um indivíduo, através de roubo, fraude e extorsão, ainda há crimes que visam outros computadores/dispositivos conectados na internet para acessar os seus dados ou recursos, ou ainda apenas para afetar a operação do dispositivo. Entre os crimes cibernéticos mais comuns podemos citar:

- Criar e disseminar software com conteúdo malicioso, tais como: vírus, ransomware, spyware, vírus, worms, cavalos de tróia, adware, entre outros;
- Exposição de informações pessoais e financeiras, violação dos dados;
- Solicitar dinheiro em resposta a um e-mail, mensagem de texto ou sites fraudulentos;
- Roubar informações pessoais e uso sem permissão;
- Extorsão ou ameaça de publicação de fotos, vídeos ou informações pessoais confidenciais roubadas no meio online;
- Efetuar acesso não autorizado à rede pessoal ou organizacional;
- Efetuar acesso não autorizado em uma conta pessoal (rede social, e-mail, conta bancária ou financeira, contas de compras online e outras;
- Perseguição, intimidação e assédio.

Para dificultar a realização dos crimes cibernéticos é necessário adotar todos os requisitos de segurança. Os requisitos de segurança podem parecer simples no primeiro contato, entretanto ao se aprofundar nos mecanismos utilizados para satisfazer esses requisitos observamos que o processo pode ser bastante complexo. Compreender efetivamente em detalhes o mecanismo de segurança vai exigir empenho e raciocínio.

Ao desenvolver um mecanismo ou algoritmo de segurança, devemos sempre considerar possíveis ataques aos requisitos de segurança. Em geral, nos casos de ataques "bem-sucedidos" os atacantes enxergam o problema de uma maneira um pouco diferente, deste modo conseguem explorar uma fraqueza inesperada no mecanismo de segurança.

Neste sentido, os procedimentos realizados para fornecer determinado serviço não são intuitivos. O mecanismo de segurança não deixa óbvio o que foi implementado, apenas quando consideramos os vários aspectos de ameaças ao mecanismo que conseguimos captar o sentido.

Após projetar um mecanismo de segurança é necessário decidir onde deve ser adicionado, definir o posicionamento físico e lógico. No posicionamento físico é necessário determinar em quais pontos específicos da rede o mecanismo de segurança deve atuar. Já no sentido lógico, estabelecer em qual camada da arquitetura o mecanismo deve ser introduzido (modelo OSI ou modelo TCP/IP).

![[UE1_img3.jpg]]

©sabelskaya/Adobe Stock

A implementação de um mecanismo de segurança normalmente envolve mais que apenas um algoritmo ou protocolo em específico. Normalmente, exige que os envolvidos tenham posse de alguma informação secreta (uma chave criptográfica por exemplo), onde é necessário levantar questões sobre a criação, armazenamento, distribuição e proteção dessa informação secreta. Também é necessário analisar aspectos e restrições em relação a dependência de protocolos envolvidos. Tais como o protocolo de comunicações, onde o comportamento pode complicar a tarefa do desenvolvimento do mecanismo de segurança - por exemplo a implementação de um mecanismo de segurança que exige que os limites de tempo sejam fixados para o intervalo de transporte entre a mensagem do remetente e o destinatário, o protocolo rede pode inserir atrasos variáveis e imprevisíveis o que pode inviabilizar o desenvolvimento do mecanismo.

Como mencionado anteriormente na área de segurança de informação existe uma batalha entre a capacidade do atacante que visa encontrar uma brecha de segurança e o profissional de segurança (projetista ou administrador) que tenta remover esta brecha. Um dos grandes problemas é que o atacante está em vantagem, pois esse só precisa descobrir uma única fraqueza no sistema. Em contrapartida, o profissional de segurança deve localizar e eliminar todas as fraquezas para conseguir uma efetiva segurança no sistema.

Apesar de tantas evidências, existe uma certa resistência da parte dos usuários e gerentes de sistemas de perceberem os benefícios em fazer investimento em segurança, acabam dando a devida importância apenas depois que ocorre uma falha de segurança. O processo de segurança de informação requer que haja um monitoramento constante, difícil de ser alcançado em um ambiente de curto prazo e sobrecarregado. Onde muito frequentemente, a segurança acaba sendo incorporada a um sistema apenas depois do projeto ser concluído, em vez de ser parte integral de todo ciclo de vida no desenvolvimento do projeto.

Existe um outro aspecto que deve ser levado em consideração, a segurança da informação deve ser ajustada sob medida, semelhante a tarefa de apertar um parafuso, o parafuso deve ser apertado com a pressão necessária, caso o parafuso seja apertado com muita força este poderá espanar, porém se o parafuso for apertado pouco ficará frouxo.

Este estudo é delicado, deve ser avaliado todo cenário envolvido, as restrições nem sempre são bem aceitas, muitos usuários e até mesmo administradores de segurança consideram que a segurança forte atrapalha a operação eficiente dos sistemas computacionais ou a utilização da informação. Um exemplo típico é fornecer políticas eficazes para controles spam, ao definir políticas muito rígidas de controle de spam podemos restringir e-mails com conteúdo legítimo, por outro lado, quando definimos políticas muito permissivas teremos um problema com a grande quantidade de spam. Em reflexão a analogia do parafuso, as regras *antispam* definidas no servidor de e-mail devem ser realizadas sob medida, aplicar a força necessária.

Neste sentido, é preciso equilíbrio e bom senso do administrador do sistema, analisar cada um dos requisitos de segurança caso a caso, mas, principalmente, as vulnerabilidades associadas a eles.

## **Ameaças, Ataques e Ativos**

Considerando que exista vulnerabilidades em um ativo de sistema, uma ameaça visa explorar tais vulnerabilidades. A ameaça representa um potencial dano na segurança de um ativo. Os ativos do sistema de informação contemplam hardware, software, dados e rede. Por sua vez, um ataque é uma ameaça executada direcionada a um ativo e, quando "bem-sucedida", resulta na violação de um requisito de segurança. Podemos classificar os ataques em dois tipos diferentes:

**Ataque ativo**: este ataque é definido com uma tentativa de alterar ativos de sistemas ou afetar sua operação (indisponibilidade de serviços).

**Ataque passivo**: este ataque é definido como tentativa de descobrir ou utilizar informações obtidas dos sistemas, este tipo de ataque não afeta diretamente os ativos do sistema.

Em geral, as ameaças ferem as propriedades básicas de segurança, a RFC 2828, descreve quatro tipos de consequências de ameaças e os ataques provenientes de cada uma dessas consequências. As consequências das ameaças são: revelação não autorizada, fraude, disrupção e usurpação. Vejamos do que se trata cada uma dessas consequências das ameaças.

![[UE1_img4.png]]

©ivan mogilevchik/Adobe Stock

- **Revelação não autorizada**
	- **Esta é uma ameaça investida sobre a propriedade de confidencialidade, pode ser consequência de três tipos de ataques:**
	**Exposição**: Pode ser realizada de propósito por uma pessoa interna com intenção de divulgar informações sensíveis de forma deliberada a um indivíduo externo à organização. Ainda, pode ser ocasionado por um erro humano, de software ou hardware, resultando na exposição não autorizada de dados sensíveis;
	**Interceptação**: A interceptação é tipo de ataque bastante comum no contexto de comunicações. Dado a comunicação realizada entre uma rede de computadores, os dispositivos conectados a esta rede podem receber uma cópia dos pacotes de rede cujo destino pretendido era outro dispositivo. Neste sentido, um atacante captura e analisa os pacotes de rede para obter determinadas informações;
	**Intrusão**: Neste tipo de ataque o adversário consegue obter o acesso não autorizado ao sistema computacional, este burla as proteções definidas por meio do controle de acesso, deste modo tem acesso às informações contendo dados sensíveis.
- **Fraude**
	- **Esta ameaça é investida sobre a propriedade da segurança de integridade, a integridade pode ser definida no âmbito de sistemas ou sobre os dados. Pode ser consequência dos seguintes tipos de ataques:**
	**Personificação**: o ataque de personificação é a tentativa do atacante de obter acesso a um sistema fazendo-se passar por um outro usuário autorizado. Ainda, o atacante pode introduzir/substituir um dispositivo de rede ou até mesmo reproduzir um site para induzir outros a se conectarem a estes. A vítima ao invés de se conectar a um dispositivo legítimo, acaba sendo direcionado a um dispositivo “adulterado”, o que permite que o atacante capture senhas de acesso e informações sensíveis que por este trafegue. Outro exemplo de personificação é o uso de um cavalo de troia, programa malicioso que parece executar uma função útil ou desejável, porém na verdade sua real intenção é conceder o acesso não autorizado ao sistema;
	**Falsificação**: este ataque refere-se à alteração ou substituição de dados válidos ou ainda a introdução de dados falsos em um arquivo ou banco de dados. Podemos ter a combinação de diferentes tipos de ataques, muitos ataques de falsificação também compõe um ataque de personificação. A falsificação de e-mail (e-mail *spoofing*) pode ser um exemplo disto, esta técnica consiste em alterar os campos do cabeçalho de e-mail, para que o destinatário receba um e-mail aparentando ser de uma origem, contudo o e-mail vem de outro local;
	**Retratação (repúdio)**: Nesta investida u
- **Disrupção**
	- **Esta é uma ameaça investida sobre duas das propriedades de segurança, disponibilidade ou integridade do sistema. Pode ser consequência de três tipos de ataques:**
	**Incapacitação**: este ataque visa atingir a disponibilidade dos serviços e sistemas. Um ataque de incapacitação bem conhecido é o ataque de negação de serviço, também conhecido como *DoS (Denial Of Service)*, neste tipo de ataque o adversário tenta sobrecarregar as requisições no servidor para que os recursos do sistema fiquem indisponíveis para seus usuários. Para alcançar seu objetivo o atacante utiliza técnicas de enviar diversas requisições com a finalidade de que o servidor fique tão sobrecarregado que não consiga mais responder a nenhum pedido;
	**Corrupção**: este ataque visa atingir a integridade do sistema. Uma rotina de software malicioso pode criptografar os arquivos do usuário ou ainda fazer o sistema e serviços funcionarem de uma maneira não pretendida. Ainda, um atacante pode obter acesso não autorizado a um sistema e modificar determinadas funções, este pode adicionar uma porta *backdoor* (porta dos fundos), fornecendo acesso aos sistemas e ativos por meio de um procedimento alternativo (não usual).
	**Obstrução**: neste ataque o adversário procura um modo de obstruir as operações do sistema, uma das maneiras utilizadas é interferir na comunicação. Neste sentido, o atacante incapacita os enlaces de comunicação ou altera as informações de controle da comunicação. Também podendo utilizar como outro modo de sobrecarregar o sistema, onde o atacante cria uma carga excessiva de processamento ou tráfego de comunicação.
- **Usurpação**
	- **É uma ameaça investida sobre a integridade do sistema. Pode ser consequência de dois tipos de ataques.**
	**Apropriação indevida**: este tipo de ataque concede a característica de se apropriar de um dado ou informação que lhe pertence, podendo ser incluído neste cenário o roubo de serviço. Para um hacker realizar um ataque de negação de serviço distribuído, o atacante contamina diversas máquinas com um software malicioso, estas máquinas serão usadas todas em conjunto para direcionar o tráfego para seu alvo (servidor ou serviço). Neste sentido, o software malicioso faz uso não autorizado dos recursos da máquina e do sistema operacional, caracterizando como um ataque de apropriação indevida.
	**Utilização indevida**: este ataque ocorre por ação de um *malware* (programas maliciosos) ou hacker que obteve um acesso não autorizado ao sistema, como consequência as funções de segurança do sistema acabam sendo desativadas ou limitadas.

### **Ameaças e Ativos**

Conforme mencionado anteriormente os ativos no contexto de sistema de informação podem ser categorizados em quatro categorias: hardware, software, dados e redes de comunicação. Nesta subseção, vamos verificar essas quatro categorias e sua relação com as propriedades de segurança (integridade, confidencialidade e disponibilidade).

- **Hardware**
	- **A principal ameaça ao hardware no sistema de informação está relacionada a propriedade de segurança da disponibilidade. O hardware é um elemento bastante vulnerável a ataques, porém menos sujeito a controles automatizados. As ameaças podem incluir dano acidental ou intencional a determinado equipamento, bem como desvio.**
	**Atualmente, existe um conceito que está se tornando bastante comum o BYOD (*****Bring Your Own Device*****) que é a utilização de dispositivos pessoais como ferramenta de trabalho. Porém, o aumento do uso de computadores pessoais como estações de trabalho na rede local (LAN) da instituição pode introduzir problemas relacionados à segurança da informação, visto que isso adiciona novas falhas e ameaças na rede.**
	**Ainda, com a miniaturização dos dispositivos de hardware (ex.: *****pendrive*****, memória, cartão *****sd*****) facilita o roubo de informação o que pode ocasionar perda da confidencialidade. Neste sentido, é necessário adotar medidas de segurança físicas e administrativas a fim de lidar com tais ameaças.**
- **Software**
	- **Tratando de ativos de software devemos contemplar os sistemas operacionais, utilitários e software aplicativos. Uma das ameaças fundamentais realizadas contra os softwares é o ataque realizado sobre a propriedade de disponibilidade. Em geral, os softwares, principalmente softwares de aplicação são muito fáceis de se destruir - podendo ser alterados ou danificados para que se tornem inúteis. Realizar um gerenciamento efetivo na configuração de softwares pode garantir uma alta disponibilidade, processo que deve incluir atualização constante do software e backup das versões mais recentes.**
	**Um problema um pouco mais difícil de tratar é uma modificação realizada no software, o programa ainda funciona, porém se comporta diferentemente do anterior, resultando em uma ameaça à integridade/autenticidade. Um ataque realizado por um vírus de computador pode inserir alguma rotina maliciosa que pode ser responsável por esta modificação.**
	**Ainda, um problema amplamente difundido é pirataria de software. Embora existam estratégias para combater a pirataria de software, a cópia não autorizada de software ainda é um problema em aberto (não resolvido).**
- **Dados**
	- **As preocupações de segurança referentes aos dados são amplas, envolve os arquivos e outras formas de dados que podem ser manipulados por indivíduos, grupos e organizações. As preocupações de segurança relacionadas aos dados abrangem questões referente a disponibilidade, ao sigilo e integridade. Tratando-se da propriedade disponibilidade, a preocupação está diretamente ligada à perda de arquivos de dados (exclusão/destruição), que pode ocorrer por acidente ou de forma deliberada.**
	**A preocupação em relação ao sigilo é evidente, corresponde a leitura não autorizada de arquivos de dados ou a bancos de dados, esta é uma área de segurança que recebe bastante atenção, foco de diversas pesquisas. Uma outra ameaça ao sigilo, sendo um pouco menos óbvia, envolve a análise de dados e a utilização de bancos de dados estatísticos. Os dados estatísticos fornecem resumos de informações ou informações agregadas. Acredita-se que informações agregadas não ameaçam a privacidade dos indivíduos. Contudo, à medida que a utilização dos bancos de dados estatísticos vem crescendo, tem se observado um potencial cada vez maior para a divulgação de informações de cunho pessoal. Em geral, para comparar a consistência dos dados em diferentes conjuntos de dados em níveis de agregação distintas é necessário ter acesso as unidades individuais. Deste modo, as unidades individuais são motivo de grandes preocupações para privacidade, pois acabam ficando expostas em vários estágios no processamento dos conjuntos de dados.**
	**Por fim, a integridade dos dados que é uma preocupação bastante importante para maioria das instituições. As modificações dos arquivos de dados podem gerar consequências em diferentes grandezas, do insignificante até as consequências mais desastrosas.**
- **Redes de Comunicação**
	- **Os ataques à segurança da rede podem ser classificados em dois tipos, ataques passivos e ataques ativos. O ataque passivo tenta adquirir informações do sistema, podendo fazer uso de tais informações, contudo isto não afeta ativos do sistema. Por outro lado, o ataque ativo tenta modificar os ativos do sistema, afetando sua operação.**
	**Ataque passivo****: este tipo de ataque por natureza consiste em especular/monitorar transmissões. Onde a meta do atacante é obter informações que estejam sendo transmitidas. Existem dois tipos de ataques passivos a revelação do conteúdo de mensagens e a análise de tráfego.**
	**• ****Revelação do conteúdo de mensagens****: este ataque consiste em obter informações sensíveis/confidenciais das quais gostaríamos que apenas pessoas específicas tivessem acesso, podendo ser uma mensagem em e-mail, arquivo transferido ou até mesmo uma conversa por telefone. Neste sentido é necessário impedir que um adversário conheça o conteúdo dessas transmissões.****
• ****Análise de tráfego****: este tipo de ataque é um pouco mais sagaz, o atacante analisa o tráfego e os pacotes de rede a fim de obter informações. Poderíamos utilizar um meio para tentar disfarçar o conteúdo das mensagens ou tráfego de informações, de tal maneira que os adversários mesmo que capturassem a mensagem não teriam acesso a informações contida na mensagem. A técnica mais comum para esconder o conteúdo é através de cifração.****
****Os ataques passivos são extremamente difíceis de detectar pois não realizam qualquer alteração nos dados. Geralmente, o tráfego da rede e as trocas de mensagens (enviar e receber) ocorrem de maneira normal, de modo que o remetente e o receptor não percebem que um outro individuo teve acesso ao conteúdo das mensagens. Neste sentido, é recomentado impedir o sucesso deste tipo ataque, pode ser aplicado uma técnica de cifração. De maneira que o tratamento contra-ataques passivos está na prevenção, em vez de tentar detectar este tipo de ataque.**
    **Ataque ativo****: este tipo de ataque envolve uma modificação no fluxo de dados ou até mesmo realizar a criação de um fluxo falso. O ataque de rede ativo é estruturado em quatro categorias: repetição, personificação, modificação de mensagens e negação de serviço. ****
• ****Repetição:**** este tipo de ataque consiste na captura passiva de uma unidade de dados e posteriormente sua retransmissão a fim de produzir um efeito não autorizado.****
• ****Personificação: ****este tipo de ataque ocorre quando uma entidade finge ser uma entidade diferente.****
• ****Modificação de mensagens: ****este ataque consiste em alterar uma parte da mensagem legítima ou ainda atrasar ou reordenar a ordem das mensagens a fim de produzir um efeito não autorizado.****
• ****Negação de serviço:**** este tipo de ataque impossibilita o gerenciamento normal dos equipamentos de rede e comunicação. Outra vertente do ataque de negação de serviço é a disrupção da rede inteira, ataque que sobrecarrega a na rede com mensagens a fim de degradar o serviço e seu desempenho.**
    **Os ataques ativos possuem características opostas aos ataques passivos. À medida que os ataques passivos são extremamente difíceis de detectar, existem medidas que podem ser aplicadas para impedir o seu sucesso. Em contrapartida, os ataques ativos são bem difíceis de impedir, pois isto exigiria uma proteção física para de todas os equipamentos e rotas de comunicação utilizados constantemente. Em vez disso, a estratégia é detectar e recuperar o sistema de qualquer disrupção ou lentidão ocasionadas por eles. Este caso a detecção pode contribuir com a prevenção.**

## **Cenário de Estudo (Insegurança/Intrusão)**

O Capítulo anterior ressalta a existência de diversas ameaças, o profissional de segurança da informação deve estar pronto para lidar com cada uma dessas ameaças, deve visar a proteção de cada um dos ativos do sistema de informação. Convém a este profissional efetuar uma análise e avaliação dos riscos de segurança da informação associados à sua organização.

As organizações podem atuar em diferentes frentes: saúde, educação, política, economia, tecnologia, segurança entre outras. Neste sentido temos diferentes cenários de estudo, contudo ressalta-se que em todas as organizações é imprescindível adotar as medidas de segurança da informação. Os mecanismos de segurança da informação serão os mesmos indiferentemente de qual seja o campo de atuação da organização, o que pode mudar são as políticas de segurança da informação que devem ser avaliadas caso a caso. Distintos setores de atuação refletem diferentes níveis de segurança, porém nenhum dos setores está isento de problemas de segurança da informação. Na figura abaixo alguns dos incidentes de segurança da informação que se tornaram públicos no ano de 2020 [[RNP](https://www.rnp.br/noticias/rnp-lanca-relatorio-anual-de-seguranca-2020), 2021].

![[UE1_img12.png]]

Fonte: Adaptado de Rede Nacional de Ensino e Pesquisa (RNP), 2020.

Destaca-se que não existe nenhum sistema computacional que seja totalmente seguro, sendo passiveis a falhas e vulnerabilidades. Ao definir exatamente o escopo no qual a segurança da informação deve atuar estaremos mais equipados/preparados para combater a causa da insegurança ou intrusão dos sistemas.

### **O banco de Tóquio**

Para não expor nenhuma organização, ao longo das unidades vamos trabalhar sobre um cenário de estudo fictício, porém este sendo baseado em situações que ocorrem no mundo real.

Nosso cenário de estudo é “O banco Tóquio”.  Esta instituição bancária está tendo problemas com segurança da informação. Foi identificado que alguém internamente no banco executou de maneira deliberada e proposital uma rotina de código maliciosa, este foi replicado rapidamente a todos os dispositivos conectados na rede, onde inúmeros computadores foram contaminados, inclusive servidores que hospedam serviços essenciais para o funcionamento do banco e possuem acesso externos.

Ao realizar um diagnóstico minucioso em um dos computadores contaminados, foram identificados alguns dos comportamentos deste *malware*, entre os quais o *malware*: insere informações no registro do computador, libera determinadas portas no firewall e ainda escala privilégios de administrador na máquina que foi alvo do ataque. Adicionalmente, o *malware* ao conseguir ter acesso a um usuário com privilégios de administrador altera a senha de todos os usuários da máquina. Este malware é bastante engenhoso, permite que o atacante explore vulnerabilidades causando danos e obtendo acesso indevido a informações restritas. Ataque realizado sobre todas as três propriedades de segurança.

Contudo, neste momento um dos maiores problemas são as portas do firewall que foram liberados no servidor de aplicação, a grande preocupação este servidor possui acesso externo – está conectado na internet. No momento seguinte em que o servidor foi contaminado e as portas no firewall foram abertas, foi constatado que foram realizadas inúmeras tentativas de intrusão ao sistema. Analisando a origem dos pacotes do tráfego de rede foi observado endereços IP’s de diferentes partes do mundo. O que tudo indica que este servidor está sendo alvo de uma *botnet* – conjunto de dispositivos conectado à internet, infectados por uma *malware*, que permite que os atacantes os controlem. Este servidor não pode ficar fora do ar, seria um prejuízo imensurável para o banco. O backup do servidor está sendo restaurado, porém pode levar algumas horas para que o servidor esteja pronto.

Estabeleceu-se o caos dentro do banco de Tóquio, as consequências são desastrosas. Os diretores do banco de Tóquio convocaram imediatamente uma reunião. Agora você, o mais novo membro da equipe de segurança, foi designado como responsável para liderar a equipe de segurança na resolução deste problema. A princípio você se sente um pouco ansioso e intimidado, você ainda tem pouco contato com os diretores do banco. Contudo, pode estar surgindo uma ótima oportunidade: então é hora de aproveitar!

Após efetuar uma análise do cenário, você realiza um mapeamento do incidente, então apresenta um plano estratégico para os diretores, ressalta que serão necessárias diversas atividades para a contenção e a recuperação dos sistemas, entre essas:

- Isolar e restabelecer os computares/ativos que foram contaminados;
- Aplicar os procedimentos de segurança da informação baseados em normas e boas práticas;
- Redefinir as políticas de segurança de informação da instituição;
- Realiza processo de auditoria nos computadores, sistemas e ativos na rede;
- Aplicar todos os mecanismos de segurança necessários;
- Definir critérios de autenticação mais robustos para os usuários;
- Utilizar funções *hash* criptográficas sem colisões nos sistemas;
- Introduzir autenticação multifator para os sistemas do banco;
- Verificar as políticas de controle de acesso e gestão de identidade;
- Revogar, criar e substituir os certificados digitais;
- Alterar as chaves públicas e simétricas dos sistemas;
- Analisar o comportamento do *malware*;
- Utilizar Sistemas de Detecção de Intrusão (IDS);
- Conter os ataques de intrusão aos sistemas;
- Analisar o comportamento dos atacantes utilizado um *honeyspot*;
- Explorar as vulnerabilidades de segurança de forma ética e responsável.

**MUNDO DO TRABALHO**A partir de agora, sua missão é conter o incidente, colocar o novo servidor em produção, restabelecer todos os serviços e garantir que as propriedades de segurança da informação no “banco de Tóquio” sejam preservadas. Para isso será necessário observar todos os aspectos e requisitos de segurança da informação, conhecer as normas, políticas, mecanismos e boas práticas de segurança de segurança da informação, bem como saber como aplicá-los. Mas não se preocupe, vamos nortear você nesta caminhada, ao longo das unidades prepararemos você para lidar com este e outros problemas de segurança da informação de âmbito real.

## **Relatórios e Procedimentos de Segurança**

Este Capítulo, foi estruturado para demonstrar em números que o cenário de estudo apresentado anteriormente reflete o que acontece na realidade. Para isto, trazemos as informações mais recentes contidas no relatório de segurança de informação da Rede Nacional de Ensino e Pesquisa (RNP) e Centro de Atendimento a Incidentes de Segurança (CAIS).

Conforme o relatório da RNP, o destaque de 2020 foram os ataques de *ransomware*, não apenas pela grande quantidade, mas também a evolução deste tipo de ataque. Este ataque que consiste em sequestrar os dados de uma vítima, de forma geral utilizam um malware para criptografar os seus dados. Os atacantes cobram dinheiro (geralmente exigem o pagamento em criptomoedas) das vítimas para devolver-lhes o acesso aos seus dados. Em 2020, muitos ataques de *ransomware* foram combinados com o ataque de vazamento de dados, onde o atacante além de cobrar para devolver os dados da vítima, cobraram para que estes dados não fossem divulgados na internet.

Outro aspecto destacado em 2020, foi a realização de diversas campanhas de *phishing*, os atacantes exploram vastamente temas relacionados à COVID-19: pandemia, novas vacinas, planos assistenciais do governo, entre outros. O ataque de *phishing* é uma técnica de engenharia social, onde o atacante tenta enganar suas vítimas para obter informações confidenciais. Os alvos e métodos não tiveram muita mudança, porém o aumento na quantidade de *phishing* foi bastante expressivo. Adicionalmente, o interesse a estes temas foi reforçado pelo cenário de isolamento social e riscos iminente de contaminação.

O relatório da RNP ainda traz como estudo de caso o incidente ocorrido no Supremo Tribunal de Justiça (STJ), em novembro de 2020. O STJ foi alvo de um ataque de *ransomware* que criptografou os dados, impedindo a restauração dos serviços. Outras instituições governamentais também foram alvos de ataques. Neste sentido, o CAIS tomou uma série de medidas internas e externas para impedir a ocorrência de incidentes na própria RNP e instituições associadas ao Sistema RNP.

Abaixo, os gráficos A, B e C apresentados fazem parte do [relatório da RNP](https://www.rnp.br/arquivos/documents/Relat%C3%B3rio_anual_seguranca_RNP_2020_final.pdf) [RNP,2021]. Primeiramente, no gráfico A apresentamos informações do volume de notificações de vulnerabilidades e incidentes ocorridos ao longo dos três últimos anos. O cenário em evidências compreende todo sistema da RNP, composto por mais de 800 organizações espalhadas pelo país.

![[UE1_img5(1).png]]

Fonte: Adaptado de Rede Nacional de Ensino e Pesquisa (RNP), 2020.

![[UE1_img6.png]]

Fonte: Adaptado de Rede Nacional de Ensino e Pesquisa (RNP), 2020.

O gráfico B, dispõe do percentual de notificações de vulnerabilidades e incidente que ocorreram em cada região do Brasil nos últimos três anos. Adicionalmente o gráfico C possui os dados referente ao volume das notificações de vulnerabilidades separadas por ano. Os dados evidenciam que houve um crescimento gradual de notificações principalmente no estado do Rio de Janeiro, cerca de 46% do número das notificações [RNP,2021], já no estado do Paraná e Pernambuco houve uma redução sistemática na incidência das notificações com o passar dos últimos três anos.

Apenas no primeiro semestre de 2020, foram reportados mais de 318 mil incidentes no Centro de Estudos, Resposta e Tratamento de Incidentes de Segurança no Brasil (CERT.br).  Sem mencionar os inúmeros incidentes que ocorrem e não são registrados. No [gráfico](https://www.cert.br/stats/incidentes/) a seguir é apresentado a distribuição dos tipos de incidentes reportados neste período, cerca de 58% dos incidentes notificados trata-se de *scan* na rede [CERT,2021], onde o atacante faz uma varredura nas redes de computadores, com o intuito de identificar quais computadores estão ativos e quais serviços estão sendo disponibilizados, assim consegue identificar vulnerabilidades e potenciais alvos.

![[UE1_img7.png]]

Fonte: CERT.br, 2020.

Conforme o relatório de segurança da HornetSecurity1 de 2020, o Brasil está entre os seis países que mais disseminam malware por meio de e-mail, chegando em 4,7% no cenário global, ressalta-se também um número expressivo no percentual dos e-mails contaminados de origem vinda dos USA, chegando em 22,94% no cenário global [HornetSecurity,2021].

![[UE1_img8.png]]

Fonte: Hornet Security, 2020.

Por fim, consultamos o boletim de ocorrências da Fortinet2, conforme os dados do primeiro trimestre de 2021, foram detectados mais de 53 mil vírus apenas aqui no Brasil, correspondente a 3,94% do percentual global [FORTIGUARD,2021].

![[UE1_img9.png]]

Fonte: Fortinet, 2021.

No mesmo período, foram identificados mais de 1,8 milhões computadores no Brasil infectados por software malicioso de *botnet*, percentual de 4,27% no cenário mundial.

![[UE1_img10.png]]

Fonte: Fortinet, 2021.

Ainda, cerca de 158 mil detecções de *exploit* no Brasil. No *exploit* o atacante explora as vulnerabilidades em aplicativos, redes, sistemas operacionais ou hardwares para invadir sistemas, roubar dados e danificar os programas.

![[UE1_img11.png]]

Fonte: Fortinet, 2021.

Durante o trimestre de 2021, a Fortinet reportou que foram detectadas na América Latina várias tentativas de execução de código remoto em dispositivos que oferecem serviços de conectividade residencial (modem). Devido a COVID-19, uma grande parte das pessoas está trabalhando *home office*. Os criminosos estão tentando comprometer os trabalhadores remotos, interceptando suas comunicações e redirecionando-os para sites maliciosos.

Conforme o boletim de segurança da Forninet, foi detectado novamente um aumento crescente na distribuição de *malware* baseado na web em toda região da América Latina. Para isso, diferentes campanhas de phishing foram utilizadas, no qual as contas das redes sociais dos usuários comprometidos são utilizadas para compartilhar anúncios e sites falsos sem que haja consentimento do usuário. Este tipo de campanha utiliza um método de propagação automática, replicando para os contatos da rede social da vítima.

Além disso, foi detectado também um aumento significativo na atividade das botnets, especificamente uma botnet conhecida como Trochilus RAT. Esta botnet é conhecida por usar várias técnicas que permite dos firewall e antivirus, além de ter a capacidade de procurar novas vítimas.

## **EXERCÍCIO**

**Exercícios de Fixação**

Quais são as três principais propriedades de segurança da informação?

Cite cinco áreas de atuação da segurança da informação.

Cite cinco dos crimes cibernéticos mais comuns.

Como podemos classificar os tipos de ataques?

Quais os quatro tipos de consequências de ameaças definidas pela RFC2828?

O que é uma ameaça?

Quais são os ativos de um sistema de informação?

Identifique três desafios de segurança da informação.

No cenário de estudo do banco de Tóquio identifique uma das ameaças investida sobre uma das propriedades de segurança da informação.

## **O alicerce da segurança da informação**

Este vídeo vai fornecer uma visão de como os três pilares da segurança da informação são utilizados para proteger os sistemas e ativos de informação, dicas e boas práticas para atuação do profissional de segurança da informação.

## **Conclusão**

Esta unidade abordou os princípios e conceitos básicos da segurança de computadores. Destacando que a área de segurança de informação é estruturada sobre três pilares fundamentais: confidencialidade, integridade e disponibilidade. Ainda, é exposto que segurança da informação é alcançada a partir da implementação adequada de diversos mecanismos de segurança, contemplando políticas, processos, procedimentos, estratégias, estruturas organizacionais e aspectos de configuração de hardware e software.

Conforme ressaltado, não basta apenas implementar os mecanismos, é necessário monitorar e analisar constantemente para garantir a segurança na organização, consequentemente, alcançar os objetivos estratégicos de negócio.

Adicionalmente, foi apresentado outras duas propriedades de segurança, a autenticidade e legalidade. Segundo alguns pesquisadores da área, essas propriedades adicionais permitem contemplar melhor todos os objetivos de segurança.

Ainda, foi exposto os desafios da segurança da informação, quais os crimes cibernéticos e atuação do profissional de segurança da informação. Observamos a relação das vulnerabilidades com as ameaças da segurança da informação. Verificamos a consequências das ameaças sobre as propriedades de seguranças, bem como os ataques direcionados aos ativos de sistema se informação.

No caso de uso foi apresentado alguns dos principais incidentes de segurança da informação que acabaram se tornando públicos em 2020. Apresentamos também, o caso de uso do “banco de Tóquio”, um problema de segurança da informação que trabalharemos ao longo das unidades.

Por meio dos relatórios técnicos foi apresentado uma visão dos incidentes de segurança aqui no Brasil. Primeiramente, o relatório de segurança da informação da RNP, realizado na rede de pesquisa nos últimos três anos. Este relatório fornece uma visão geral dos incidentes ocorridos em cada uma das regiões do Brasil. Foi destacando a grande quantidade de ataques *phishing* com temas relacionados a COVID-19, e ataques *ransonware* combinados com vazamento de dados. Ainda, compartilhado a experiência do CAIS, atuando com medidas preventivas para proteção da rede RNP.

Ainda, no âmbito nacional são apresentados os relatórios de incidentes reportados para o CERT.br no primeiro semestre de 2020, fornecido o percentual de ataques categorizados pelo tipo. Um outro relatório da HornetSecurity, expõe a origem de e-mail com disseminação de malware, onde o Brasil está em sexto lugar. Por fim, o boletim de ocorrência da Fortinet, obtido do primeiro trimestre de 2021, demostrando a quantidades de incidências na detecção de vírus, *botnets* e *exploit* especificamente no Brasil.

Esta unidade foi estruturada para alcançar dois objetivos: Primeiramente, apresentar os principais conceitos de segurança da informação, importantes para formar um alicerce que será utilizado nas unidades posteriores. Um segundo objetivo, não menos importante, mostrar quais são alguns dos desafios que esperam você como profissional de segurança da informação.

## **Norma ISO 27001 E ISO 27002**

No sentido de orientar o processo de gestão da segurança de informação foram estabelecidas as normas internacionais ISO/IEC 27001 e a ISO 27002. Normas que foram concebidas em outubro de 2005 pela *International Organization for Standardization* (ISO) em conjunto com *International Electrotechnical Commission* (IEC). Tais normas definem os requisitos e as melhores práticas direcionadas à segurança da informação e cibersegurança.

As organizações podem ser certificadas pela norma ISO/IEC 27001. Esta é considerada uma das principais e mais importantes certificações de segurança da informação. A organização que “conquista” esta certificação, comprova que segue todas as exigências e requerimentos para alcançar a segurança da informação de maneira eficiente.  A norma ISO 27002, por sua vez, funciona como se fosse um guia de práticas e procedimentos que facilitam o alcance da certificação da ISO 27001. Procedimentos e boas práticas que podem ser aplicados em organizações de todos os portes e todos os setores.

![[UE2_img1.jpeg]]

Fonte: ©WrightStudio/Adobe Stock

As empresas que adotam tais normas, garantem um Sistema de Gestão de Segurança da Informação (SGSI) orientado por padrões internacionais. Deste modo, contam com todos seus benefícios, tais como redução de riscos, organização dos processos, fortalecimento das ações estratégicas e diferencial competitivo no mercado.

Neste sentido, no SGSI a segurança da informação deve ser planejada, implementada, monitorada, analisada e melhorada constantemente. Onde o processo de gestão tem suas responsabilidades bem definidas, nas quais os objetivos devem ser analisados e alcançados. Existem alguns elementos que são definidos especificamente na norma ISO 27001, porém não na norma ISO 27002. Então vejamos o que trata cada uma das normas.

### **ISO 27001**

Essa é uma norma de gestão que define os requisitos para que uma organização tenha e administre um SGSI certificado. Esta norma, leva em consideração os ativos da segurança da informação e as necessidades da área de negócio, define estratégias para melhor administrar a segurança da informação. Neste sentido, estabelece etapas fundamentais para gestão da segurança da informação: análise, planejamento, implementação, monitoramento e ciclo de aperfeiçoamento.  Entre as atividades realizadas nessas etapas destacam-se:

- Redução de risco de responsabilidade (definição de políticas e procedimentos);
- Alinhamento de processos;
- Identificação e correção das falhas e pontos fracos;
- Segurança da informação como elemento estratégico;
- Informações e dados sensíveis devidamente protegidos;
- Responsabilidade da segurança da informação atribuída a alta gestão da organização;
- Permite que seja realizado revisão independente do SGSI;
- Garantia de confiabilidade para os clientes e parceiros;
- Aumento da conscientização interna dos colaboradores sobre segurança da informação;
- Possibilidade de combinar os recursos com outros sistemas de gestão;
- Permite acompanhar o êxito do sistema;
- Visibilidade da organização com uma comprovação oficial que o SGSI está de acordo com os padrões internacionais.

### **ISO 27002**

Essa norma estabelece um código composto pelas melhores práticas de segurança da informação, adotadas para apoiar a implantação do SGSI nas organizações.  Possui como objetivo, estabelecer diretrizes e princípios fundamentais para introduzir, implementar, preservar e otimizar a gestão de segurança da informação em determinada organização.

A ISO/IEC 27002 fornece um guia completo de implementação que descreve os procedimentos e mecanismos de segurança que devem ser estabelecidos e de qual forma. Por meio desta norma, a organização institui uma avaliação de riscos dos ativos mais importantes da empresa. Ressalta-se que em uma organização a tecnologia, pessoas, processos, segurança e os negócios estão interligados, sendo necessário saber lidar com a informação visando as propriedades fundamentais da segurança da informação (integridade, confidencialidade e disponibilidade).

Mesmo que uma organização não tenha interesse em ser certificada pela norma ISO 27001, seguir as boas práticas estabelecidas na norma ISO 27002, pode auxiliar a empresa a alcançar um SGSI mais sólido. Consequentemente, garantir que todos na empresa tenham consciência sobre os aspectos de segurança da informação, pois esse é um fator essencial para garantir a proteção dos dados. Além de inúmeros benefícios de aplicar da norma, tais como:

- Fornece maior proteção aos ativos dos sistemas de informação, incluindo dados sensíveis e informações estratégicas;
- Possibilita a identificação dos pontos fracos dos sistemas de informação permitindo realizar correções;
- Permite uma melhor organização com processos e mecanismos segurança bem definidos;
- Fornece redução de custos com a prevenção de incidentes de segurança da informação;
- Estabelece um diferencial competitivo visando os clientes que estimam a conformidade das normas internacionais;
- Estar em conformidade com a legislação vigente e outras regulamentações;
- Introduz uma melhor conscientização da equipa e colaboradores sobre a segurança da informação;
- Reduzir riscos por meio da implementação de um SGSI (políticas e procedimentos de segurança bem definidos);
- Oferece uma abordagem para implantação de políticas de controles.

## **Federal Information Processing Standards 200**

O FIPS PUB 200 é um padrão especificado pela Lei Federal de Gestão de Tecnologia da informação (FISMA - *Federal Information Security Management Act*), visa estabelecer os requisitos mínimos de segurança da informação para os sistemas de informação federais. Este padrão foi desenvolvido pelo NIST (*National Institute of Standards and Technology*) em 1996, estipula níveis de segurança baseado no gerenciamento de riscos à segurança da informação.

![[UE2_img2(1).jpeg]]

Fonte: ©Tierney/Adobe Stock

Conforme mencionado na Unidade 1, existem algumas maneiras para classificar as contramedidas utilizadas para lidar com as ameaças e reduzir as vulnerabilidades. O FIPS PUB 200 classifica as contramedidas em termos de requisitos funcionais, como resultado fornece uma lista composta de 17 áreas relacionadas à segurança informação.  Tais áreas, fornecem as diretrizes necessárias para garantir a proteção dos pilares fundamentais da segurança da informação (confidencialidade, integridade e disponibilidade). Deste modo, ressalta-se a importância de cada uma das áreas, assim como as atividades a elas relacionadas, então vejamos do se trata cada uma das áreas:

### **Controle de acesso**

O controle de acesso é o mecanismo de segurança da informação que permite limitar as ações que um usuário pode realizar sobre determinado recurso. Este mecanismo contempla o uso de políticas, procedimentos, dispositivos de hardware e software para restringir e gerenciar o acesso a determinado ambiente físico ou lógico. Neste sentido, fornece a proteção a informação e seus ativos (sistemas, equipamentos, instalações entre outros) impedindo que ocorra acessos não autorizados em seus ambientes. Entre as principais atividades do controle de acesso destaca-se:

- Limitar o acesso das ações e operações que os usuários autorizados podem realizar sobre determinado recurso;
- Limitar os processos associados aos usuários autorizados ou dispositivos, tipos de transações e funções;
- Definir as permissões que usuários autorizados exerce no sistema.

### **Conscientização e treinamento**

Esta é uma das áreas mais críticas da segurança da informação, envolve diversos tipos de riscos associados ao fator “humano”. Pessoas não devidamente treinadas podem se tornar um “elo” fraco para segurança da informação. Por exemplo, um colaborador que não foi instruído pode ser vítima de um ataque de *phishing*, abrir um e-mail ou link contendo um software malicioso, ou ainda, conectar um *pendrive* contaminado com um malware em um dos computadores da empresa, este malware pode se espalhar para toda rede. Para evitar contratempos, se faz necessário realizar todo um trabalho de educação de segurança da informação com os colaboradores da organização. Ao fornecer instrução aos funcionários esses serão capazes de identificar e se proteger contra todos os tipos de ameaças à segurança cibernética, consequentemente preservando a segurança da informação de toda organização. Na área de conscientização e treinamento destacam-se as atividades:

- Conscientizar os usuários dos sistemas computacionais dos riscos à segurança da informação associados às suas atividades;
- Apresentar aos colaboradores as leis, regulamentações e políticas organizacionais de segurança de informação, bem como as sanções administrativas do não cumprimento das normas;
- Fornecer treinamento aos colaboradores para que esses executem apropriadamente seus deveres e responsabilidades.

### **Auditoria e responsabilidade**

A área de auditoria e responsabilidade, trata-se de um processo de avaliação sistemática realizada nos sistemas e ativos da informação, têm como objetivo, mensurar o grau de conformidade da segurança da informação conforme os critérios estabelecidos pela organização. Ainda, identifica se os processos estão sendo realizados de forma correta, e unicamente pelas pessoas responsáveis. Deste modo, o processo de auditoria avalia diversos aspectos da segurança da informação, tais como: infraestrutura (hardware e software), ambiente, sistemas, aplicações, manipulação da informação, históricos, práticas do usuário entre outros. A seguir, apresentamos as principais atividades relacionadas a esta área:

- Efetuar o gerenciamento do processo de auditoria dos sistemas de informação - criar, proteger e manter os registros de auditoria pelo período necessário para facilitar monitoramento e análise;
- Proceder investigação de atividades ilegítimas, não autorizadas ou inadequadas no sistema;
- Realizar o rastreamento das ações de cada usuário no sistema a fim responsabilizá-los por suas ações.

### **Avaliação de certificação, credenciamento e segurança**

A implementação de certificações direcionadas a segurança da informação, semelhante a ISO 27001, trazem diversos benefícios a organização. Entre os benefícios destaca-se a visibilidade externa da organização, frente aos clientes e parceiros - receber uma certificação como a ISO 27001 comprova que a empresa segue todas as diretrizes legais e padrões de segurança da informação. A adequação seguindo os padrões internacionais não são aplicados apenas a setores de tecnologia de informação, mas em todos os setores da organização. A seguir, apresentamos as principais atividades relacionadas a esta área:

- Avaliar periodicamente os mecanismos de segurança nos sistemas de informação a fim de verificar se os controles são efetivos em sua aplicação;
- Desenvolver planos de ação para correção de deficiências no sistema visando reduzir ou eliminar vulnerabilidades;
- Fornecer autorização para operação dos sistemas de informação e conexões associadas;
- Monitorar continuamente os mecanismos de segurança para garantir sua efetividade constante.

### **Gerenciamento de configuração**

A área de gerenciamento de configuração é ampla, envolve a implantação de soluções de hardware e software considerando os aspectos de segurança da informação. Desse modo, o processo de gerenciamento das configurações dos sistemas, servidores e ativos vai além de realizar apenas procedimentos técnicos. Contempla a definição de um estado segurança da informação desejado que deve estar de acordo com os padrões de conformidade. Sendo que configurações realizadas de maneira incorretas podem gerar inconsistências e afetar tanto a segurança da informação como as estratégias de negócio. Em vista disso, os procedimentos de configuração, seja este de criação ou manutenção devem ser todos devidamente documentados. Segue as principais atividades da área de gerenciamento de configuração:

- Estabelecer e manter configurações dos sistemas de informação e ativos organizacionais (hardware e software);
- Garantir o cumprimento das configurações de segurança para todos os produtos de tecnologia da informação empregados na organização;
- Realizar o processo de documentação de todos os procedimentos de configuração realizados.

### **Planejamento de contingência**

O plano de contingência é um conjunto de medidas adotadas a fim de assegurar a continuidade dos sistemas vitais para o funcionamento de uma organização quando um determinado problema ocorre. Esse planejamento deve garantir a continuidade do negócio. Para isto, o setor de tecnologia da informação deve estar preparado e atuar rapidamente, seguir os passos de segurança da informação pré-definidos visando reduzir o impacto e recuperar os danos causados o mais breve possível. As atividades da área do planejamento de contingência contemplam:

- Implementar e manter planos de contingência para respostas a emergências, políticas de backup e recuperação pós-desastre para os sistemas de informação;
- Garantir a disponibilidade dos ativos de informação críticos e a continuidade dos serviços em casos de emergências.

### **Identificação e autenticação**

Esta é uma das principais áreas da segurança da informação definida no FIPS PUB 200, ela implementa o mecanismo de autenticação que é responsável em assegurar que as pessoas são quem realmente dizem ser. Neste sentido, este mecanismo é utilizado para restringir o acesso a informações (sistemas e bancos de dados), serviços e ambientes (infraestrutura/datacenter) entre outros - concedendo o acesso apenas a pessoas autorizadas. O processo de identificação do indivíduo no sistema se dá por meio de um ou ainda mais fatores: conhecimento, propriedade e características. O conhecimento retrata-se aquilo que o indivíduo "sabe", por exemplo uma senha. O fator de propriedade refere-se aquilo que o indivíduo possui, por exemplo um cartão magnético ou um token. Por fim, o fator "características" aquilo que o indivíduo é, ou seja, características que permitem distinguir o indivíduo de outros, por exemplo a biometria (digital, reconhecimento facial, leitura da íris ou retina). Entre as principais atividades da área de identificação e autenticação destaca-se:

- Identificar os usuários no sistema e certificar suas identidades - verificar se o usuário é quem alega ser;
- Identificar os processos e dispositivos que agem sob nome de um usuário;
- Autenticar e liberar acesso dos usuários, processos e dispositivos ao sistema.

**Nota de rodapé**

**Token** - dispositivo físico que fornece mais uma camada de segurança para o usuário no acesso a conta bancária/financeira, este gera uma senha temporária para cada um dos acessos.

### **Respostas a incidentes**

A área de Resposta a Incidentes envolve diversos departamentos da organização (tecnologia, jurídico, comunicação e outros), tem como objetivo coordenar ações contra os incidentes de segurança da informação. No contexto de segurança da informação, um incidente é caracterizado como qualquer evento que atente contra os princípios básicos da segurança da informação (confidencialidade, integridade e disponibilidade), podendo ser suspeito ou confirmado. Entre as principais atividades desta área destaca-se:

- Desenvolver processo de capacitação operacional para lidar de forma adequada com incidentes relativos a sistemas de informação, contemplando as atividades de preparação, detecção, análise, tratamento, contenção, recuperação e resposta ao usuário;
- Realizar o rastreamento, documentação e reportar incidentes aos responsáveis e autoridades cabíveis;
- Aprender com o incidente ocorrido.

### **Manutenção**

A área da manutenção é essencial para garantir a segurança da informação de uma organização. Quando o processo de manutenção na organização não é constante, um sistema ou ativo da informação (hardware ou software) pode passar dias com uma determinada vulnerabilidade, o que insere brechas de segurança que podem ser exploradas pelos adversários (hackers). Toda infraestrutura de tecnologia da informação necessita de manutenção preventiva, deve ser levado em consideração tanto a estrutura de hardware como software, consequentemente os equipamentos e sistemas terão melhor desempenho o que reflete na qualidade do serviço fornecido. Ainda, no processo de manutenção quanto mais tempo se arrasta um problema, mas complexo e custoso este se torna. Entre as principais atividades da área de manutenção destaca-se:

- Realizar processo de manutenção periódica e preventivas nos sistemas de informação e ativos;
- Fornecer os recursos necessários e efetivos para execução dos processos de manutenção nos sistemas de informação e ativos, tais como ferramentas, técnicas e equipe capacitada.

### **Proteção da mídia**

As mídias contêm o ativo mais valioso de uma organização, a informação. Deste modo, é importante que as mídias sejam devidamente manipuladas, tanto que uma das áreas definidas na FIPS PUB 200 trata especificamente da proteção das mídias. A área de proteção da mídia se preocupa com as informações e dados sensíveis que estão contidos nas mídias, seja de forma física ou digital. Desta forma, tem como objetivo evitar que dados confidenciais se tornem públicos, prejudicando as estratégias de negócios da organização. Neste mesmo sentido, quando uma mídia precisa ser descartada, estratégias adequadas para que as mídias sejam eliminadas corretamente devem ser adotadas. Entre as principais atividades da área de proteção de mídia destaca-se:

- Proteger e armazenar as mídias do sistema de informação de forma adequada, seja em papel ou meio digital;
- Limitar acesso a informações relativas a mídias do sistema de informação apenas aos usuários autorizados;
- Estabelecer políticas de descarte de mídia - a mídia do sistema de informação pode conter dados e informações sensíveis da organização, assim se faz necessário apagar ou destruir a mídia antes de realizar o seu descarte ou liberar a mesma para ser reutilizada.

### **Proteção física e ambiental**

A área de proteção física e ambiental visa proteção dos ativos da informação contra danos físicos provenientes de ações criminosas ou riscos naturais. Neste sentido, esta área estabelece medidas de segurança da informação tendo em vista a proteção dos ambientes físicos, contra acessos não autorizados, destruição ou modificação dos sistemas de informações ou ativos. Entre as principais atividades desempenhadas nesta área, destacam-se:

- Limitar o acesso físico a infraestrutura de tecnologia da informação a apenas indivíduos autorizados - acesso ao datacenter, equipamentos, sistemas de informação e respectivos ambientes operacionais;
- Proteger as instalações físicas e a infraestrutura de suporte aos sistemas de informação;
- Fornecer serviços de suporte e manutenção ao ambiente físico;
- Definir estratégias para proteger os sistemas de informação e ativos contra perigos ambientais;
- Garantir que procedimentos ambientais sejam realizados de forma adequada em instalações que contenham sistemas de informação.

### **Planejamento**

A área de planejamento é o cerne do processo de segurança da informação, concentra o planejamento de cada uma das demais áreas definidas no FIPS PUB 200. Está área fornece ações que estruturam o alicerce que amparam o SGSI de uma organização. Por meio do planejamento é realizado todo um estudo, onde são efetuadas avaliações de riscos, traçados os objetivos de negócios, bem como efetuado um levantamento de quais medidas de segurança da informação devem ser adotadas no SGSI. Entre as principais atividades da área de planejamento destacam-se:

- Definir os planos de segurança da informação para organização;
- Desenvolver e executar os planos de segurança da informação;
- Documentar os planos de segurança da informação;
- Atualizar periodicamente as políticas/procedimentos de segurança da informação adotados na organização (destinado aos sistemas de informação e aos indivíduos que o acessam - regras de comportamento).

### **Segurança de pessoal**

A área de segurança de pessoal deve estar alinhada como o setor de recursos humanos da organização. No contexto de gestão de pessoas podem existir alguns riscos à segurança da informação, tais como vazamentos de informações sigilosas, ataques de engenharia social e incidentes de segurança ocasionadas por falhas humanas ou ações realizadas de forma deliberada (executadas por pessoas de maneira intencional). Visando garantir a preservação de informações confidenciais e estratégicas algumas medidas podem ser adotadas: estabelecer plano de conduta, contratos de confidencialidade e principalmente treinamentos internos de segurança da informação. Entre as principais atividades desta área destacam-se:

- Garantir que os indivíduos que ocupam posições estratégicas e responsabilidade dentro de organizações são confiáveis e cumprem os critérios de segurança estabelecidos em suas respectivas posições;
- Garantir que os ativos organizacionais (informações e sistemas de informação) estejam protegidos durante o processo relativo ao gerenciamento de pessoal (demissões e transferências)
- Aplicar penalidades formais aos indivíduos que descumpram as políticas e procedimentos de segurança organizacional.

### **Avaliação de risco**

A área de avaliação de riscos consiste no processo de levantar as principais ameaças que possam impactar o ambiente de uma organização (sistemas de informação ou ativos). Na avaliação de risco três aspectos básicos devem ser analisados: qual é a importância dos ativos em risco, quão crítica é a ameaça e qual o nível de vulnerabilidade do sistema em relação a esta ameaça. Considerando tais aspectos a área de avaliação de risco tenta identificar o risco, mensurar o impacto da ameaça e tentar alcançar um equilíbrio entre o impacto do risco e o custo para estabelecer as contramedidas. Entre as principais atividades da área de avaliação de risco destacam-se:

- Efetuar avaliação periódica dos riscos de segurança da informação;
- Identificar e avaliar riscos de segurança da informação nas operações, ativos e indivíduos da organização;
- Analisar riscos resultante da operação de sistemas de informação organizacionais e do processamento, armazenamento ou transmissão de informações organizacionais.

### **Aquisição de sistemas e serviços**

A área de aquisição de sistemas e serviços fica responsável em planejar e conduzir o processo de contratação e aquisição da infraestrutura de tecnologia da informação. Deste modo, esta área precisa analisar, especificar e padronizar o processo de aquisição de hardware e software, bem como a contratação de serviços (fornecedores ou terceirizados) para atender as necessidades da organização. Em vista disso, fica responsável pela locação e expansão de equipamentos, adquirir sistemas e soluções de tecnologia e ainda distribuição dos recursos. Entre as principais atividades desta área destacam-se:

- Efetuar gerenciamento de aquisições de maneira adequada e eficaz, selecionar e dimensionar a ativos suficientes para proteção dos sistemas de informação organizacionais;
- Assegurar que os sistemas da informação incorporam a segurança da informação em todo ciclo de vida de desenvolvimento dos sistemas;
- Definir e aplicar políticas adequadas para gestão do uso de software e controle de acesso - restringir à utilização e instalação de software;
- Garantir que provedores de serviços terceirizados empreguem medidas de segurança adequadas para proteger informações, aplicações e serviços fornecidos para a organização.

### **Proteção de sistemas e comunicações**

A área de proteção de sistemas e comunicações visa garantir a proteção e comunicação segura dos dados dos sistemas de informação. Esta área não se limita apenas aos sistemas de comunicação, engloba todos os âmbitos da proteção de dados, desde a transmissão até recebimento da informação. Deste modo, inclui procedimentos, estruturas organizacionais, processos, políticas, entre outras funcionalidades. Entre as principais atividades da área de proteção de sistemas e comunicações destacam-se:

- Monitoramento, controle e proteção das comunicações da organização (informações transmitidas ou recebidas por sistemas de informação);
- Implementar técnicas de segurança da informação dentro dos sistemas de informação da organização - aplicando boas práticas de segurança nos projetos de arquitetura e técnicas de desenvolvimento de software seguro e os princípios de engenharia de sistemas.

### **Integridade de sistemas e informações**

Esta área está diretamente ligada a uma das propriedades básicas da segurança da informação, em específico o atributo da integridade. Deste modo, a área de integridade de sistemas e informações visa proteger as informações e os sistemas para que esses não sejam alterados por pessoas terceiras não autorizadas. Nesse contexto, esta área, adota todas as precauções necessárias para que a informação não seja modificada ou eliminada sem autorização, isto é, mantendo sua legitimidade e consistência. Entre as principais atividades desta área destacam-se:

- Garantir a integridade dos sistemas de informação da organização - identificar, corrigir e reportar falhas nos sistemas de informação;
- Garantir a proteção dos sistemas de informação contra rotinas de código malicioso;
- Efetuar o monitoramento e auditoria de segurança dos sistemas de informação, ativos e da rede - gerar alertas para reportar os problemas de segurança e tomar providências adequadas para enfrentá-los.

## **Lei Brasileira N° 12.737**

Devido o avanço da tecnologia houve um crescente aumento na quantidade de crimes cibernéticos. Para possibilitar que as autoridades sejam capazes de lidar com tais tipos de delitos virtuais se faz necessário que estes estejam previsto em lei.

Neste sentido, algumas modificações foram realizadas na constituição brasileira, entre a adição de novas leis. A **Lei Nº 12.737/2012** sancionada pelo presidente da república em 2012, efetua uma alteração no código penal brasileiro a fim de contemplar a tipificação de crimes virtuais e delitos de informática. Esta lei estabelece penas para crimes cometidos no ambiente virtual, como invasão de computadores, disseminação de vírus, roubo de senhas, falsificação de documentos e uso indevido de dados sem autorização do usuário.

![[UE2_img3.jpeg]]

Fonte: ©promesaartstudio/Adobe Stock

A **Lei Nº 12.737/2012** ficou popularmente conhecida como Lei Carolina Dieckmann. Este nome foi atribuido decorrente ao caso ocorrido com a atriz Carolina Dieckmann, que acabou tendo "dados" do computador pessoal roubados e divulgados na internet após ter sido vítima de extorsão. Apesar de ter ganhado grande percursão na mídia graças ao incidente ocorrido com a atriz, o projeto da lei já vinha sendo discutido, dado as reivindicações dos representantes do sistema financeiro que estavam sendo vítimas de um grande número de crimes virtuais.

Entre os principais delitos previstos na **Lei Nº 12.737/2012** podemos citar:

**Art. 154-A** – *“Invasão de dispositivo informático alheio, conectado ou não à rede de computadores, mediante violação indevida de mecanismo de segurança e com o fim de obter, adulterar ou destruir dados ou informações sem autorização expressa ou tácita do titular do dispositivo ou instalar vulnerabilidades para obter vantagem ilícita. Pena - detenção, de 3 (três) meses a 1 (um) ano, e multa”;*

**Art. 266** – *“Interrupção ou perturbação de serviço telegráfico, telefônico, informático, telemático ou de informação de utilidade pública - Pena - detenção, de um a três anos, e multa”;*

**Art. 298** – *“Falsificação de documento particular/cartão - Pena - reclusão, de um a cinco anos e multa”;*

**Art. 154-B** – *“Nos crimes definidos no art. 154-A, somente se procede mediante representação, salvo se o crime for cometido contra a administração pública direta ou indireta de qualquer dos Poderes da União, Estados, Distrito Federal ou Municípios ou contra empresas concessionárias de serviços públicos”.*

Alguns delitos no âmbito jurídico ainda são difíceis de serem julgados e processados, principalmente decorrente a própria característica da internet e pela dificuldade de imputar os criminosos. Consequentemente estão surgindo novas leis mais abrangentes e cada vez mais complexas.

## **Marco Civil da Internet (Lei N° 12.965)**

O Marco Civil da Internet é a Lei brasileira de **N° 12.965** que regulamenta o uso da internet no Brasil, sancionada pelo presidente da república em 23 de abril de 2014. Conforme o **Art. 1°**: “Esta Lei estabelece princípios, garantias, direitos e deveres para o uso da internet no Brasil e determina as diretrizes para atuação da União, dos Estados, do Distrito Federal e dos Municípios em relação à matéria”. Desta forma, o Marco Civil da Internet estabelece os princípios e direitos do uso da Internet no Brasil amparado pela constituição. Sobretudo, fornece um conjunto de regras sobre o que deve ou não ser realizado na Internet, consequentemente trazendo mais segurança para os usuários e organizações (setor público e privado).

Entre os principais aspectos definidos na **Lei N° 12.965**, confere os princípios de uso disponível no **Art. 3°**:

*“I.garantia da liberdade de expressão, comunicação e manifestação de pensamento, nos termos da Constituição Federal;*

*II.proteção da privacidade;*

*III.proteção dos dados pessoais, na forma da lei;*

*IV.preservação e garantia da neutralidade de rede;*

*V.preservação da estabilidade, segurança e funcionalidade da rede, por meio de medidas técnicas compatíveis com os padrões internacionais e pelo estímulo ao uso de boas práticas;*

*VI.responsabilização dos agentes de acordo com suas atividades, nos termos da lei;*

*VII.preservação da natureza participativa da rede;*

*VIII.liberdade dos modelos de negócios promovidos na internet, desde que não conflitem com os demais princípios estabelecidos nesta Lei.”*

Entre os principais aspectos definidos no Art. 3° destaca-se o princípio da proteção da privacidade e dos dados pessoais.

O Art. 7° dispõe dos direitos e garantias dos usuários assegurados por lei: a inviolabilidade, sigilo das comunicações privadas (salvo a quebra do sigilo por ordem judicial) e qualidade dos serviços de conexão de internet contratados.

Outro artigo extremamente importante é o Art. 10°, esse refere-se à proteção dos registros, dados pessoais e comunicações privadas. Conforme disposto no **Art. 10°**:

*“A guarda e a disponibilização dos registros de conexão e de acesso a aplicações de internet de que trata esta Lei, bem como de dados pessoais e do conteúdo de comunicações privadas, devem atender à preservação da intimidade, da vida privada, da honra e da imagem das partes direta ou indiretamente envolvidas”.*

A **Lei N° 12.965** é estruturada em cinco capítulos e dispõe de 32 artigos. Como profissional de segurança da informação é necessário conhecer cada um dos artigos previsto na lei, estar ciente dos direitos e deveres tanto como usuário, mas principalmente no que se refere a organização. Esta lei fornece as diretrizes para o bom uso da internet, porém deve ser complementada com outras leis vigentes, tais como a LGPD.

## **Lei Geral de Proteção de Dados Pessoais**

A LGPD (Lei Geral de Proteção de Dados Pessoais) é a **Lei Nº 13.709**, sancionada pelo presidente da república em 2018 entrou em vigência em agosto de 2020. Esta lei visa garantir a proteção dos dados pessoais de todo cidadão que esteja em território nacional brasileiro, estabelece diretrizes importantes e obrigatórias para a **coleta, processamento e**** armazenamento de dados pessoais**. Deste modo, propõe um cenário de segurança jurídica baseado na padronização de normas e boas práticas para promover a segurança dos dados. Conforme o **Art. 1°**

*"Esta Lei dispõe sobre o tratamento de dados pessoais, inclusive nos meios digitais, por pessoa natural ou por pessoa jurídica de direito público ou privado, com o objetivo de proteger os direitos fundamentais de liberdade e de privacidade e o livre desenvolvimento da personalidade da pessoa natural".*

![[UE2_img4.jpg]]

Fonte: ©dmutrojarmolinua/Adobe Stock

Esta lei estabelece que indiferente da organização ser sediada no Brasil ou exterior se existe processamento de conteúdo de pessoas no território nacional a lei deve ser cumprida. Ainda, segundo a lei, é permitido compartilhar dados com entidades internacionais e com outros países desde que sejam seguidas as exigências legais.

Conforme demostrado na Unidade 1, recentemente houve diversos incidentes de segurança da informação que ficaram públicos, em geral, casos envolvendo vazamento de dados. Neste sentido, a LGPD pode ser de grande valia, pois as novas regras além de garantir a privacidade dos brasileiros, possibilitam evitar impasses comerciais com outros países.

A **Lei Nº 13.709** foi instituída sob diversos valores, entre os seus principais objetivos propõe:

- *Garantir o direito à privacidade e à proteção de dados pessoais dos usuários, por meio de práticas transparentes e seguras, assegurando os direitos fundamentais.*
- *Definir regras claras sobre a utilização dos dados pessoais.*
- *Consolidar a segurança das relações jurídicas e a confiança do proprietário no tratamento dos dados pessoais.*
- *Garantir a livre iniciativa, a livre concorrência e a defesa das relações comerciais e de consumo.*
- *Promover a concorrência e a livre atividade econômica, inclusive com portabilidade de dados.*

## **General Data Protection Regulation**

O GDPR (*General Data Protection Regulation*) é uma lei criada pelo Parlamento Europeu em conjunto com Conselho da União Europeia. Esta lei estabelece regras de privacidade e proteção de dados de cidadãos da União Europeia. A sigla GDPR traduzindo para nosso idioma corresponde a Regulamento Geral sobre a Proteção de Dados. O GDPR foi proposto pela primeira vez em 2012, aprovada em 2016 pelo Parlamento Europeu, contudo entrou em vigor apenas em maio de 2018. Este período da aprovação até a data de vigência foi estipulado para que as empresas de adaptassem a nova lei.

![[UE2_img5.jpeg]]

Fonte: ©arrow/Adobe Stock

O objetivo do GDPR é fornecer aos usuários o controle sobre seus dados pessoais, nos quais são armazenados pelas empresas e trafegam livres pela internet. Deste modo, os usuários passam a ter o poder de decidir o que as empresas podem ou não realizar com os seus dados. Adicionalmente, estabelece que as empresas precisam seguir regras rigorosas para manipular os dados pessoais e informações de seus usuários.

Tratando-se da proteção dos dados o GDPR compreende dois conceitos fundamentais, a transparência e a responsabilidade.

A transparência concede a prática de não se esconder nada, ou seja, as empresas que coletam dados dos usuários devem deixar bem claro, qual será o seu uso. Sem haver o preceito da transparência não é possível estipular o consentimento, outro conceito muito importante no GDPR. No consentimento o usuário analisa as políticas de transparência e verifica se o concorda ou não com os termos definidos. Ainda, a partir da política de transparência e dos termos de privacidade, o próprio usuário deve ter controle de quais dados poderão ou não ser utilizados pela empresa.

Já no que se refere a responsabilidade, corresponde a postura que as empresas devem ter em relação ao compromisso de conduzir os dados de outras pessoas. Desta forma, o GDPR permite restringir o uso das informações coletadas dos usuários para que não sejam indevidamente utilizadas.

De maneira sucinta, a principal preocupação do GDPR é a privacidade das pessoas e o comprometimento com a segurança dos dados armazenados. Logo, nenhuma empresa pode armazenar informação que permita identificar um usuário sem que haja o consentimento dele.

## **Tipificação de Crimes Virtuais**

Visando alinhar a compreensão referente a tipificação dos crimes virtuais, vamos caracterizar os crimes cibernéticos como sendo qualquer "atividade criminosa que tem como alvo ou faz uso de um computador, uma rede de computadores ou um dispositivo conectado em rede" [Kaspersky, 2020]. Segue abaixo uma lista contendo os principais crimes que podem ser realizados na internet.

1. **Calúnia:** este crime consiste em atribuir falsamente a alguém a autoria de um crime por meio da internet, crime previsto no **Código Penal Art. 138**;

1. **Difamação:** este crime consiste em atribuir a alguém um fato, com circunstâncias descritivas, ofensiva à sua reputação, por meio da internet, crime previsto no **Código Penal Art. 139**;

1. **Injúria:** este crime consiste em ofender a dignidade ou decoro de alguém, ferindo sua honra subjetiva, por meio da internet, crime previsto no **Código Penal Art. 140**;

1. **Ameaça:** este crime consiste no ato de intimidar alguém por meio da internet, mediante promessa de fazer algum mal contra a pessoa, crime previsto no **Código Penal Art. 147**;

1. **Divulgação de segredo****:** este crime consiste em revelar segredos de terceiros na internet ou divulgar material confidencial de documentos/correspondências que possam causar danos, crime previsto no **Código Penal Art. **[**153**](https://www.jusbrasil.com.br/topicos/10620036/artigo-153-do-decreto-lei-n-2848-de-07-de-dezembro-de-1940);

1. **Invasão de dispositivo informático****:** este crime consiste em violar indevidamente dispositivos de informática ou contribui para tal, oferecendo, distribuindo ou difundindo programa malicioso, crime previsto no **Código Penal Art. **[**154-A**](https://www.jusbrasil.com.br/topicos/28004011/artigo-154a-do-decreto-lei-n-2848-de-07-de-dezembro-de-1940);

1. **Furto****:** este crime consiste em subtrair o patrimônio de uma pessoa pela internet, por ex.: colocar os dados de outra pessoa para sacar ou desviar dinheiro de uma conta, pela internet, crime previsto no **Código Penal Art. 155**;

1. **Fraude**: este crime consiste no ato de má fé de enganar “alguém” a fim de tirar vantagem utilizando a Internet, ex.: fraudes bancárias por meio de Internet Banking ou clonagem de cartão, ou fraude nos setores financeiros, previsto no **Código Penal Art. 155, § 4°, inciso II**;

1. **Preconceito e Discriminação**: crimes no meio virtual cometidos por intolerância racial, étnica, religiosa ou de nacionalidade, ex.: comentar, em chats, e-mails e outros, de forma negativa, estimulando preconceito e discriminação, crime previsto na **LEI Nº **[**7.716**](https://www.jusbrasil.com.br/legislacao/1035120/lei-do-crime-racial-lei-7716-89)**  Art. 20**;

1. **Exposição infracional de crianças e adolescente****:** este crime consiste em divulgar por meio da internet, nome, ato ou documento de procedimento policial, administrativo ou judicial relativo à criança ou adolescente que se envolva em ato infracional, crime previsto na **LEI N° **[**8.069**](https://www.jusbrasil.com.br/legislacao/91764/estatuto-da-crian%C3%A7a-e-do-adolescente-lei-8069-90)** Art. **[**247**](https://www.jusbrasil.com.br/topicos/10581919/artigo-247-da-lei-n-8069-de-13-de-julho-de-1990);

1. **Pedofilia:** este crime consiste em disponibilizar, transmitir, distribuir, publicar ou divulgar por meio de sistema informático, fotografia, vídeo ou qualquer outro registro que contenha qualquer situação que envolva criança ou adolescente em atividades de cunho sexuais, crime previsto na **LEI Nº **[**8.069**](https://www.jusbrasil.com.br/legislacao/91764/estatuto-da-crian%C3%A7a-e-do-adolescente-lei-8069-90)** Art. **[**241-A**](https://www.jusbrasil.com.br/topicos/28003230/artigo-241a-da-lei-n-8069-de-13-de-julho-de-1990) e **Art. **[**241-E**](https://www.jusbrasil.com.br/topicos/28003194/artigo-241e-da-lei-n-8069-de-13-de-julho-de-1990);

1. **Estelionato****:** este crime consiste em obtenção de vantagens em proveito próprio em esquemas de fraude com uso da internet, crime previsto no **Código de Penal Art. 171**;

1. Falsificação de medicamentos: este crime consiste no ato de adulterar/alterar de forma fraudulenta um produto para fins terapêuticos e medicinais para ser comercializado utilizando a internet, ex.: venda de medicamentos irregulares e insumos farmacêuticos na Internet, crime previsto no **Código Penal Art. 273, § 1º**;

1. **Intolerância Religiosa:** este crime consiste no desrespeito a liberdade religiosa no ato de ofender ou zombar afrontosamente a religião alheia pela internet, ex.: criar comunidade online que menospreze ou zombe de outras religiões, crime previsto no **Código Penal Art. 208**;

1. **Estupro:** este crime consiste em constranger alguém por meio de chantagem ou qualquer ameaça no meio virtual utilizando a internet, a fim de satisfazer o prazer sexual por meio de prática imoral, crime previsto no **Código Penal Art. **[**213**](https://www.jusbrasil.com.br/topicos/10612010/artigo-213-do-decreto-lei-n-2848-de-07-de-dezembro-de-1940);

1. **Favorecimento da prostituição****:** este crime consiste em induzir ou atrair alguém à prostituição ou outra forma de exploração sexual utilizando a internet, crime previsto no **Código Penal Art. 228**;

1. **Crime de ato obsceno / escrito ou objeto obsceno****:** consiste no crime de criar, importar, exportar, adquirir, portar, para fins de comércio, distribuição ou exposição pública, escrito, desenho, pintura estampa ou qualquer objeto obsceno – neste contexto utilizando o meio digital, crime previsto no **Código Penal Art. **[**233**](https://www.jusbrasil.com.br/topicos/10608816/artigo-233-do-decreto-lei-n-2848-de-07-de-dezembro-de-1940) e **Art. **[**234**](https://www.jusbrasil.com.br/topicos/10608777/artigo-234-do-decreto-lei-n-2848-de-07-de-dezembro-de-1940);

1. **Interrupção ou perturbação de serviço de informação de utilidade públic****a:** este crime consiste em indisponibilizar ou impedir o restabelecimento de serviços de utilidade pública, ex.: modificar ou danificar um site na internet que contenha informação de utilidade pública, crime previsto no **Código Penal Art. **[**266**](https://www.jusbrasil.com.br/topicos/10605134/artigo-266-do-decreto-lei-n-2848-de-24-de-fevereiro-de-1891)**, § 1º**;

1. **Incitação ao crime****:** este crime consiste em incentivar a prática de determinado crime por meio da internet, crime previsto no **Código Penal Art. 286**;

1. **Apologia ao crime****:** este crime consiste em criar comunidades virtuais ensinando como burlar a legislação ou divulgar ações ilícitas realizadas, crime previsto no **Código Penal Art. **[**287**](https://www.jusbrasil.com.br/topicos/10602088/artigo-287-do-decreto-lei-n-2848-de-07-de-dezembro-de-1940);

1. **Pirataria de software****:** este crime consiste em realizar cópias de programas de computador sem que haja a prévia autorização do autor, crime previsto na **Lei Nº **[**9.610**](https://www.jusbrasil.com.br/legislacao/92175/lei-de-direitos-autorais-lei-9610-98);

1. **Plágio****:** este crime consiste em realizar cópia de informações publicadas por terceiros sem a devida citação da fonte, crime previsto na **Lei Nº **[**9.610**](https://www.jusbrasil.com.br/legislacao/92175/lei-de-direitos-autorais-lei-9610-98);

1. **Falsificação de cartão****:** este crime consiste em falsificar cartões  de crédito ou débito, crime previsto no **Código Penal Art. **[**298**](https://www.jusbrasil.com.br/topicos/10600081/artigo-298-do-decreto-lei-n-2848-de-07-de-dezembro-de-1940);

2. **Falsa identidade****:** este crime consiste em criar uma “identidade” virtual falsa, ex.: a criar um perfil fake nas redes sociais, crime previsto no **Código Penal Art. 307**.

**Nota de rodapé**

**Fake - **Termo utilizado para denominar contas criadas na Internet visando ocultar a identidade real de um usuário.

Esta lista dispõe de alguns dos crimes cibernéticos previsto na esfera jurídica, porém existem outros inúmeros crimes virtuais que não foram citados, nos quais muitos dos delitos ainda não foram previstos por lei. Alguns dos crimes citados são próprios da internet, ou seja, dependem da internet para ocorrer, outros utilizam da tecnologia como meio de realizar o delito. Neste sentido, devemos estar atentos aos crimes cibernéticos bem como conhecer as leis que nos amparam.

![[UE2_img6.jpeg]]

Fonte: ©vchalup/Adobe Stock

## **Crimes Contra Propriedade Intelectual**

A área de segurança da informação também deve considerar a proteção da propriedade intelectual da organização. Onde devemos caracterizar a propriedade intelectual como sendo um bem imaterial protegido em âmbito jurídico.  A propriedade intelectual é segmentada em três categorias: Direito Autoral, Propriedade Industrial e Proteção *Sui Generis*. A propriedade intelectual visa garantir o direito de autoria dos inventores ou responsáveis por qualquer produção intelectual, sendo no domínio científico, artístico, literário ou industrial. As violações dos direitos autorais são consideradas crimes contra propriedade intelectual e estão previstas no Código Penal.

Os **direitos autorais** são protegidos pela **LEI Nº 9.610**, conforme disposto no Art. 1° *“**Esta Lei regula os direitos autorais, entendendo-se sob esta denominação os direitos de autor e os que lhes são conexos**”*. Esta lei garante os privilégios sobre livros, textos literários, artísticos ou científicos, obras artísticas e fotográficas, programas de computador, entre outras criações proveniente do intelecto humano.

Os direitos de **propriedade industrial** são garantidos pela **LEI N° 9.279**, responsável por regular e proteger legalmente as obras, projetos e ideias voltados às atividades industriais. Esta lei garante os direitos sobre marcas, registro de nomes comerciais, patentes, desenhos industriais, modelos de utilidade entre outros. Consequentemente, fornecendo exclusividade sobre a utilização, difusão e exploração dos bens intelectuais. Porém, deste caso se faz necessário obter um registro no órgão responsável.

Por fim, a **proteção sui generis** atua em três diferentes vertentes: topografia de circuitos integrados, técnicas de cultivo e conhecimentos tradicionais. A topografia de circuitos integrados é amparada pela **LEI N° 11.484**, esta fornece segurança do bem intelectual para as empresas que produzem semicondutores. As técnicas de cultivo também são resguardadas legalmente, a **LEI N° 9.456** prevê garantias em relação as pesquisas realizadas nesta área, bem como os produtos vegetais com características claramente distinguíveis das espécies conhecidas. Por último, os conhecimentos tradicionais que são protegidos pela **LEI Nº 13.123**, também conhecida como lei da biodiversidade, esta lei visa proteger conhecimentos adquiridos por meio de práticas e costumes passados de pais para filhos ao longo do tempo.

Visando proteger a propriedade intelectual nossa legislação define sua violação como um crime. O profissional de segurança da informação deve zelar pelos bens intelectuais. Por exemplo, prevenir sua organização contra a pirataria. Ainda é muito importante manter os colaboradores devidamente informados a respeito da proibição de fazer cópias ou de distribuir dados sem autorização.

Observe que a violação dos direitos autorais está descrita no Código Penal, conforme o **Art. 184°** estabelece pena que varia de três meses até 4 anos de reclusão. No mesmo sentido os crimes direcionados a propriedade industrial tipificadas no **Art. 183°** e **Art. 195°** da **LEI 9.279**. Ainda, relativo aos programas de computadores, os crimes estão previstos no **Art. 12°** da **LEI 9.609** que estabelece pena de seis meses até quatro anos de reclusão.

## **Políticas de Segurança da Informação**

As políticas de segurança da informação são regras bem definidas que ditam o acesso, controle e transmissão da informação dentro da organização. Tais políticas devem estar devidamente documentadas e sempre atualizadas. Por meio, da implementação de políticas de segurança da informação bem definidas é possível reduzir consideravelmente os riscos relacionados à segurança da informação, fornecendo a devida proteção contra ameaças internas e falhas de segurança.

Para que a implantação das políticas de segurança da informação seja bem-sucedidas, é necessário a participação de todos os colaboradores da organização, incluindo a diretoria e a equipe de TI. Esta política deve ser escrita de uma forma clara, para que todos na organização tenham o seu correto entendimento, entendam como manusear a informação conforme os padrões e preceitos da segurança da informação.

A aplicação adequada das políticas de segurança da informação pode reduzir os danos à infraestrutura de TI da organização. Consequentemente, melhora a experiência do usuário que se beneficia significativamente com a qualidade dos serviços fornecidos.

Sabe-se que a área de segurança da informação possui uma metodologia própria. Então, é fundamental estudar e planejar as políticas de segurança da informação, ajustar para que estejam condizentes com as estratégias de negócio da organização, mas sobretudo desempenhar sua função da proteção da informação. A elaboração da política de segurança da informação depende de certos cuidados, ações prévias podem contribuir na sua construção, ao definir uma estrutura básica e identificar qual cultura mais indicada, sendo que todos na organização deverão ser capazes de compreender os conceitos e saber lidar com as ferramentas.

## **Avaliação e Gerenciamento de Risco a Segurança da Informação**

Para discutir a avaliação e gerenciamento de riscos à segurança da informação vamos resgatar o cenário de uso do Banco de Tóquio, introduzido na Unidade 1. Analisando o cenário do Banco de Tóquio, podemos perceber a ausência de normas e padrões que estabelecem boas práticas relacionados à segurança da informação. Provavelmente, se as normas fossem devidamente aplicadas muitos dos problemas ocasionados no banco poderiam ter sido evitados.

Ao adotar a ISO 27001, o banco teria estratégias bem consolidadas para melhor administrar a segurança da informação, contemplando as etapas fundamentais para gestão da segurança da informação: análise, planejamento, implementação, monitoramento e ciclo de aperfeiçoamento.  Neste sentido, na gestão dos riscos de segurança haveria uma redução de riscos de responsabilidades por meio das definições de políticas e procedimentos bem definidos.

Ainda, no processo de ciclo de aperfeiçoamento seria implantado o alinhamento de processos para identificação e correção das falhas e pontos fracos relacionados à segurança da informação. Consequentemente os dados sensíveis dos clientes do banco estaria devidamente protegido. Sem mencionar o processo de conscientização sobre segurança da informação, trabalho que poderia ter sido desenvolvido com os colaboradores do banco – um funcionário que foi adequadamente treinado sobre os aspectos de segurança da informação estaria consciente das usas ações, reduzindo assim a probabilidade de o banco ter sido contaminado pelo malware.

No mesmo sentido a norma ISO 27002 poderia auxiliar, fornecendo uma maior proteção aos ativos dos sistemas de informação do banco, incluindo os dados sensíveis e informações estratégias. O banco de Tóquio ao aplicar está norma estaria empregando boas práticas de segurança da informação, ou seja, a implantação de políticas de controles com processos e mecanismos segurança bem definidos. O banco além de contar com a redução de custos com a prevenção de incidentes de segurança da informação, este estaria em conformidade com a legislação vigente e outras regulamentações.

Tendo em vista que o Japão também possui leis de proteção de dados, o Banco de Tóquio está sujeito a sanções. No Japão a lei de proteção de dados é denominada *Act on the Protection of Personal Information* (APPI), entrou em vigor em 2017. Esta regulamentação é aplicada sob informações pessoais e as informações que requerem cuidados especiais. Assim, as empresas que não tratarem os dados dos cidadãos japoneses de forma adequada podem sofrer sanções previstas em lei.

Neste momento, sua missão no “banco de Tóquio” é garantir que as propriedades de segurança da informação sejam preservadas. Para isto, esta “Unidade” tratou alguns dos principais aspectos e requisitos de segurança da informação, contemplando normas, políticas, legislação e boas práticas de segurança de segurança da informação. Adicionalmente, foi mencionado os mecanismos fundamentais de segurança que são imprescindíveis para garantir a proteção da segurança da informação, e contornar o problema no “banco de Tóquio”. Nas próximas unidades vamos conhecer cada um destes mecanismos de segurança, bem como saber aplicá-los.  Mas não se preocupe, vamos nortear você nesta caminhada, ao longo das próximas unidades vamos te preparar para lidar com este e outros problemas de segurança da informação no âmbito real.

## **Conhecendo a Lei Geral de Proteção de Dados**

Este vídeo vai fornecer uma visão maior sobre a Lei Geral de Proteção de Dados, qual a importância desta nova lei, o que mudou com a regulamentação da LGPD e qual é o impacto desta nova lei para as empresas e pessoas.

## **EXERCÍCIO**

**Exercícios de Fixação**

Quais as etapas fundamentais para gestão da segurança da informação estabelecidas na norma ISO 27001?

Cite três atividades estabelecidas na norma ISO 27001?

Quais os benefícios de ser certificado pela norma ISO 27001?

Qual o objetivo da norma da norma ISO 27002?

Quais os benefícios que a norma ISO 27002 pode trazer?

O que propõe o FIPS PUB 200?

Cite três das áreas definidas no FIPS PUB 200?

Do que se trata a Lei Brasileira N° 12.737 (Lei Carolina Dieckmann)?

O que estabelece o Marco Civil da Internet?

Qual a importância da LGPD e da GDPR?

Cite três tipos de crimes cibernéticos, descreve do que se trata cada um desses crimes.

O que é o crime contra propriedade intelectual?

Qual a importância das políticas de segurança da informação dentro de uma organização?

Avalie o caso de uso do "Banco de Tóquio", baseado nas normas e padrões que foram estudados apresente três medidas que poderiam ter sido tomadas para evitar o incidente.

## **Conclusão**

Esta unidade abordou as principais normas e padrões no processo de gestão da segurança de informação. Entre as normas internacionais destacam-se a ISO 27001 e a ISO 27002, conforme discutido, tais normas definem os requisitos e as melhores práticas de segurança da informação e cibersegurança. Ainda, foi ressaltado os benefícios que uma organização pode obter ao ser certificada pela norma ISO 27001. Adicionalmente, apresentamos a norma ISO 27002 que estabelece as melhores práticas de segurança da informação, fundamentais para introduzir, implementar, preservar e otimizar a gestão de segurança da informação nas organizações.

Na sequência, detalhamos o padrão FIPS PUB 200 que estabelece os requisitos mínimos de segurança da informação exigidos nos sistemas de informação federais. Conforme visto, este padrão classifica as contramedidas em termos de requisitos funcionais, como resultado foram elencadas 17 áreas relacionadas à segurança informação, fundamentais para garantir a proteção dos sistemas de informação e seus ativos.

Enfatizamos o grande aumento na quantidade dos crimes cibernéticos e os desafios da segurança da informação. Em contrapartida, no âmbito jurídico apresentamos as principais leis que permitem combater os crimes virtuais. Primeiramente a Lei Nº 12.737 que estabelece penas para crimes cometidos no ambiente virtual, como invasão de computadores, disseminação de vírus, roubo de senhas, falsificação de documentos e uso indevido de dados sem autorização do usuário. Posteriormente, foi apresentado o Marco Civil da Internet que estabelece os direitos e deveres para o uso adequado da internet no Brasil. Adicionalmente, destacamos as leis de proteção dos dados, tanto no território nacional como em outros países (LGPD, GDPR e APPI). Também, tratamos da tipificação dos crimes virtuais, onde foram caracterizados os crimes virtuais mais comuns e outros que migram para contexto virtual. Abordamos também os crimes que atentam contra propriedade intelectual, bem como as leis que as resguardam.

Ainda, foi enfatizado a importância de implementar políticas de segurança da informação adequadas nas organizações, ressaltamos os benefícios e as etapas necessárias. Por fim, resgatamos o caso de uso do “banco de Tóquio”, onde foi aplicado o método de avaliação e gerenciamento de riscos à segurança da informação. O objetivo foi que você pudesse identificar os problemas de segurança da informação que esta instituição está enfrentando, mas sobretudo como eles poderiam ter sido evitados se tivesse sido adotado boas práticas de segurança da informação. Demostramos qual a importância dentro de uma organização, de orientar a segurança da informação a partir das normas, políticas e padrões, bem como conhecer no âmbito jurídico a legislação que nos protege.

## **Identificação e Autenticação**

No contexto de segurança da informação, a autenticação é um mecanismo essencial e deve ser utilizado como uma defesa primária. Conforme a definição estabelecida pela RFC 2828, este processo consiste em efetuar uma verificação de uma certa identidade alegada por uma pessoa ou entidade do sistema. Este mecanismo é composto por duas etapas, **identificação**** **e **verificação**. Na etapa de identificação um determinado usuário apresenta uma identidade ao sistema. A verificação consiste no processo de certificar a validade da identidade que foi apresentada.

O processo mais comum é a autenticação utilizando usuário e senha. O login do usuário corresponde a sua identidade e deve ser um identificador único.  A senha deve ser vinculada com o identificador do usuário. Esta senha deve ser utilizada no processo de verificação, permite comparar a senha fornecida pelo usuário com uma senha previamente armazenada no sistema. Deste modo, conseguimos validar a identidade do usuário, ou seja, verificar se o usuário é realmente quem alega ser, onde apenas o usuário legítimo deve ter conhecimento da sua senha.

Assim, o processo de identificação permite identificar os usuários do sistema, bem como os processos que agem associados a este usuário ou dispositivos. Adicionalmente, a autenticação permite verificar (autenticar) a identidade de tais usuários, processos ou dispositivos. Deste modo é possível liberar ou restringir o acesso aos dados ou sistemas de informação de uma organização.

![[UE3_img1.jpeg]]

Fonte: ©Blue Planet Studio/Adobe Stock

## **Princípios da Autenticação**

Conforme os princípios da autenticação, o usuário deve ser devidamente identificado. Além do mais, todo usuário autêntico deve ser automaticamente autorizado a utilizar os sistemas.

O princípio da autenticação fornece garantias da identidade de quem está enviando a informação. Este mecanismo é utilizado para proteger uma das propriedades fundamentais da segurança da informação, a confidencialidade. Conforme estudamos na primeira Unidade, a confidencialidade permite garantir que a informação somente seja acessada por pessoas autorizadas.

A principal forma de garantir a confidencialidade é por meio da autenticação e do controle de acesso, desta forma a informação será acessada apenas por pessoas devidamente autorizadas. Em contrapartida, temos a perda da confidencialidade se alguém não autorizado obtém acesso a tais recursos. Visando a proteção desta propriedade de segurança, a norma ISO 27002 fornece algumas diretrizes para orientar o processo de identificação e autenticação. Conforme a norma ISO 27002:

- Todos os usuários devem ter um identificador único de uso pessoal e exclusivo, convém que uma técnica adequada de autenticação seja selecionada para validar a identidade dos usuários;
- O controle de autenticação deve ser aplicado para todos os tipos de usuários, inclusive administradores do sistema e diretoria;
- Os identificadores dos usuários devem ser utilizados para rastrear as atividades dos indivíduos. Como boas práticas as atividades regulares dos usuários não devem ser realizadas por meio de contas privilegiadas;
- Convém documentar qualquer tipo de circunstância excepcional que exija a utilização de identificador de usuário compartilhado por um grupo de pessoas, controles adicionais podem ser necessários para manter as responsabilidades dos indivíduos que vão utilizar este identificador;
- Identificadores genéricos para uso de um indivíduo só devem ser autorizados onde as ações executadas pelo usuário não precisam ser rastreadas, ou quando existem outros controles implementados para tal;
- É conveniente que onde exista a necessidade de uma autenticação mais robusta, sejam implementados métodos adicionais de autenticação, tais como meios criptográficos, smart cards, tokens e mecanismos para autenticação biométrica;
- Convém que a força dos processos de identificação e autenticação sejam proporcionais a sensibilidade da informação que deve ser acessada. Ideal que as senhas sejam protegidas utilizando meios criptográficos e protocolos de autenticação;
- Objetos como tokens podem ser utilizados para identificação e autenticação;
- Tecnologias de autenticação biométricas que usam características únicas de um indivíduo podem ser utilizadas para autenticar a identidade de um usuário;
- A combinação de diferentes tecnologias e mecanismos de segurança resultam em uma autenticação mais forte.

## **Fatores da Autenticação**

Conforme mencionado, o processo de autenticação consiste em determinar se um usuário é quem realmente afirma ser, existem basicamente quatro fatores principais que permitem autenticar a identidade de um usuário:

- O que o indivíduo sabe;
- O que o indivíduo possui;
- Características físicas do indivíduo (biometria estática);
- Características comportamentais (biometria mecânica).

Os fatores podem ser utilizados sozinhos ou ainda combinados.

O primeiro fator corresponde a algo que apenas o indivíduo “sabe”, por exemplo a senha, o número de identificação pessoal (PIN), respostas a um conjunto de perguntas que foram previamente cadastras (utilizado em combinação com outros fatores para troca de senha), desenhos ou representações gráficas que apenas o usuário consiga identificar.

O segundo fator é algo que o indivíduo possui, por exemplo *token**s* (amplamente utilizado nas instituições bancárias), senhas descartáveis enviadas por e-mail, SMS ou aplicativos no smartphones, cartões eletrônicos, *smart card*, chaves criptográficas.

O terceiro fator está associado diretamente as características físicas do indivíduo, relacionado ao que o indivíduo é, retrata-se da biometria estática que contempla a impressão digital, identificação da face, leitura biométrica da íris ou retina.

O último fator está associado as características do que o indivíduo faz, relacionadas as características comportamentais, correspondente a biometria mecânica, tais como o padrão de voz, característica de escrita (em geral utilizado a assinatura), ritmo de digitação entre outros.

Contudo, cada um dos fatores possui suas próprias limitações. O fator que o indivíduo sabe pode ser adivinhado ou roubado (quebra de senhas por exemplo). Semelhante, o fator que o indivíduo possui pode ser roubado ou ainda falsificado. As características de biometria estática tendem a ser mais precisas, entretanto existe um alto custo associado à sua implementação. Por sua vez, a biometria mecânica pode gerar muitos erros no processo de autenticação (falsos negativos e positivos), ainda dependendo do cenário pode não ser conveniente.

## **Tipos de Autenticação**

Os fatores de autenticação mencionados anteriormente permitem estabelecer os mecanismos de autenticação, consequentemente podemos ter diferentes tipos de autenticação. Um sistema pode implementar mais de um fator de autenticação para certificar as credenciais dos usuários, atualmente é um procedimento que está se tornando comum e bastante recomendado, esta técnica é denominada como autenticação multifator.

Existem diferentes tecnologias para autenticação multifator, contudo são estruturas basicamente sobre três tipos:

- Autenticação baseado em senha;
- Autenticação baseado em token;
- Autenticação biométrica.

Atualmente a segurança no Ciberespaço exige muito mais do que apenas uma simples senha para garantir a segurança dos usuários. Com a crescente transformação digital, o potencial das ameaças também vem sendo explorado. Nesse sentido, a autenticação multifator está se tornando cada vez mais importante, pois utilizar mais de um elemento para autorizar o acesso, propõe uma camada extra de segurança. Então, primeiramente vamos conhecer brevemente cada um dos tipos de autenticação, na sequência vejamos como podemos combiná-los.

![[UE3_img2.jpg]]

Fonte: ©Irina Strelnikova/Adobe Stock

### **Autenticação baseado em senha**

A autenticação baseada em senha é a principal linha de defesa do sistema de informação contra um adversário, em essência a autenticação é um meio utilizado para validar a identidade fornecida por uma determinada entidade, podendo ser um usuário legítimo ou não. Neste mecanismo o usuário legítimo deve fornecer um identificador e uma senha válida previamente cadastrada no sistema. O sistema irá verificar se as credenciais deste usuário são verdadeiras. Ao validar a identidade alegada o sistema fornece o acesso deste usuário ao sistema. Então outros mecanismos de segurança deverão ser empregados, tal como o mecanismo de controle de acesso que visa garantir que o usuário tenha acesso e privilégios no sistema apenas para aquilo que lhe compete – garantir que um usuário não tenha privilégios superiores do que deve ter (privilégios de administrador na máquina ou sistema). O mecanismo de controle de acesso será estudado na nossa próxima Unidade, mas primeiramente vamos conhecer um pouco mais sobre a nossa principal linha de defesa, a autenticação, por enquanto é apenas necessário que você compreenda que existe uma integração entre esses dois mecanismos.

### **Autenticação baseado em *****token***

A autenticação baseada em *token* consiste na utilização de um objeto por parte do usuário para auxiliar no processo de autenticação.

O token é um dispositivo em geral eletrônico que permite gerar senhas temporárias para reforçar o processo de autenticação. Na maioria das vezes o token não possui uma conexão física com o computador, porém existem algumas versões que devem ser conectadas a porta USB do computador. Entre as tecnologias mais recentes temos a utilização dos *smart cards* e smartphones que são capazes de realizar a mesma tarefa. A tendência atualmente é a utilização dos smartphones para fornecer a funcionalidade do token, que está sendo bastante utilizado por instituições bancárias e financeiras.

![[UE3_img3.jpeg]]

Fonte: ©bestforbest/Adobe Stock

Contudo, os adversários também têm explorado estas novas tecnologias, existe uma quantidade significativa de *malware* destinado aos dispositivos móveis, veremos isto na Unidade correspondente. Em relação aos *token**s* vamos estudar duas frentes, os *token**s* como cartões de memória e os *smart **token**s*.

**Cartões de memória**

Este tipo de *token* permite o armazenamento de informação, contudo não realiza nenhum tipo de processamento. Tal dispositivo, está presente nos cartões bancários que possuem uma fita magnética na parte de trás do cartão. Esta fita magnética possibilita armazenar um código de segurança comum, podendo ser lido na maioria das leitoras de cartões. Uma das grandes desvantagens é que este dispositivo pode ser reprogramado. Existem outros cartões de memória que adicionam uma memória eletrônica interna.

Os cartões de memória são usados para utilização em acessos físicos, normalmente associados a algum tipo de senha. Um exemplo de uso típico são os cartões de débito com a utilização nos caixas eletrônicos dos bancos.

O cartão de memória quando associado com uma senha fornece uma segurança maior do que apenas a utilização de uma senha individual. Neste sentido, o adversário precisa ter posse do cartão físico para realizar qualquer tipo de operação. Contudo, mesmo existindo uma limitação física, os criminosos conseguem aplicar golpes por meio de engenharia social ou ainda por clonar o cartão (duplicar o cartão), deste modo devemos estar sempre atentos.

**Smart *****tokens***

Os smart *token**s* são dispositivos hardware, mídias que armazenam informações. Em geral seus chips permitem armazenar os dados do certificado digital do usuário. As informações são acessadas por meio da utilização da senha pessoal do usuário. Os smart *token**s* possuem algumas das seguintes características:

![[UE3_img4.jpg]]

Fonte: ©Sergey Yakovlev/Adobe Stock

**Características físicas:** os smart *token**s* contêm um microprocessador inserido internamente em seus dispositivos, um dos principais exemplos é o cartão smart card. Os smart cards são cartões inteligentes, fabricados em plástico, são muito semelhantes aos cartões de crédito convencionais, porém este tipo de cartão possui um microchip embutido em sua superfície. Existe outros tipos de smart tokens, pequenos objetos portáteis, muito semelhante a um chaveiro, este permite gerar senhas temporárias para acesso.

**Interface:** um smart *token* pode possuir uma interface para permitir interação com o usuário, em geral possui um teclado e um display. Este dispositivo pode se comunicar com um dispositivo externo (leitora ou gravadora).

![[UE3_img5.jpeg]]

Fonte: ©JonikFoto.pl/Adobe Stock

**Protocolo de autenticação: **o propósito de smart *token* é fornecer autenticação para os usuários. Desse modo, podemos classificar este dispositivo conforme o protocolo de autenticação utilizado, em geral existem basicamente três categorias básicas:

- **Estático**: neste protocolo o usuário autentica-se no *token* e o *token* faz a autenticação do usuário no computador.
- **Gerador de senha ****dinâmico:** o token gera uma senha temporária. Essa senha deve ser digitada no sistema para realizar o procedimento de autenticação, introduzida manualmente ou automaticamente por meio do *token.*
- **Requisição/resposta: **o sistema gera uma requisição, posteriormente o *token* deve fornecer uma resposta para solicitação efetuada.

### **Autenticação biométrica**

A autenticação por biometria consiste em autenticar um indivíduo utilizando características físicas únicas que os diferem de outros indivíduos. Tais características podem ser classificadas como estáticas ou dinâmicas. Entre as características estáticas temos as impressões digitais, a geometria da palma da mão, padrões da retina e íris dos olhos e identificação facial. Associado as características dinâmicas temos assinatura, padrão da escrita, padrão do reconhecimento de voz e ritmo de digitação.

![[UE3_img6.jpg]]

Fonte: ©-=MadDog=-/Adobe Stock

A biometria é essencialmente baseada na tarefa de reconhecimento de padrões. Vejamos as principais aplicações para autenticação biométrica:

- **Impressões digitais:**** **são uma das biometrias mais populares, consiste no padrão de saliências e traços na superfície das pontas dos dedos. As impressões digitais são únicas, o que permite diferenciar um indivíduo dentro da população humana. Desse modo, os sistemas de reconhecimento de impressões digitais extraem diversas características da digital que armazenadas no sistema para realizar o processo de verificação da digital. O processo de verificação consiste em confrontar a digital fornecida pelo usuário com a digital previamente armazenada.
- **Assinaturas:** no processo de escrita cada indivíduo possui um estilo, o que reflete na sua assinatura que consiste na representação escrita do nome da pessoa. Porém, a assinatura possui algumas limitações, por mais parecidas que as assinaturas sejam, um indivíduo não vai conseguir replicar assinatura idênticas, o que para o computador torna-se um desafio. Outro aspecto é que assinatura do indivíduo pode mudar ao longo do tempo.
- **Geometria da mão****: **esta abordagem consiste em identificar padrões na palma da mão do indivíduo, identifica características tais como forma, comprimento e largura dos dedos. Tais informações são previamente armazenadas nos sistemas de autenticação baseado na geometria da mão, posteriormente são utilizadas para verificar a identidade do usuário.
- **Características faciais:** esta abordagem consiste em utilizar as características faciais para identificar um indivíduo. Entre as principais características são analisadas a geometria do rosto, aspectos faciais fundamentais como olhos, sobrancelhas, nariz, lábios e formato do queixo.
- **Padrão da retina e íris:**** **o formato das veias sanguíneas abaixo da superfície da retina são características únicas de um indivíduo, deste modo pode ser utilizada no processo de identificação. O sistema biométrico de retina obtém uma imagem digital do padrão da retina utilizando um facho de luz infravermelha no olho. Então, armazena esta imagem no sistema, posteriormente utiliza ela para verificar a identidade do usuário. Outra característica biométrica advinda dos olhos é o padrão da íris dos olhos, sendo que a íris fornece um formato único, podendo também ser utilizada para diferenciar os indivíduos.
- **Identificação de voz:**** **esta abordagem consiste em identificar padrões de voz que estão fortemente associados a características físicas e anatômicas do locutor. Este tipo de método de autenticação possui uma certa limitação, ao longo do tempo a voz acaba sofrendo uma certa variação, com isto a tarefa de reconhecimento biométrico da voz pode se tornar um desafio.

![[UE3_img7.jpeg]]

Fonte: ©vinitdeekhanu/Adobe Stock

A autenticação biométrica em comparação com autenticação baseada em senhas e tokens é uma abordagem bastante complexa. Um outro fator que deve ser avaliado é o preço necessário para implementar esta tecnologia, ainda é um investimento bastante alto. Apesar de ser uma tecnologia promissora ainda deve ser amadurecida.

## **Autenticação Baseada em Senha**

A autenticação baseada em senha é a principal linha de defesa dos sistemas de informação contra intrusos, sendo amplamente utilizada, praticamente todos os sistemas solicitam que um usuário forneça suas credenciais, exigindo tanto um identificador único como também uma senha.

O sistema deve comparar a senha que está sendo fornecida pelo usuário com a senha que foi previamente cadastrada por um usuário autêntico, sendo preservada em um arquivo de senhas ou armazenada em um banco de dados do sistema. A senha permite autenticar o identificador único do usuário que está acessando o sistema. Desta forma, o identificador único fornece segurança das seguintes maneiras:

- O identificador permite determinar se o usuário está autorizado a acessar o sistema. Em geral, apenas os usuários que tiveram seu identificador armazenado no sistema devem ter permissão de acesso.
- O identificador permite definir quais privilégios serão concedidos ao usuário. O sistema pode fornecer privilégios de super usuário, usuário que contém privilégios para administrar todo o sistema, inclusive executar funções que são protegidas pelo sistema operacional. Em contrapartida, o sistema fornece contas com privilégios restritos, tais contas são mais limitadas, onde o usuário pode realizar poucas ações no sistema.
- O identificador pode ser utilizado no controle de acesso discricionário. Neste sentido, um usuário que apresentar uma lista de identificadores de outros usuários, pode conceder privilégios para que outros usuários manipulem (leitura, escrita e execução) seus arquivos.

![[UE3_img8.jpeg]]

Fonte: ©Song_about_summer/Adobe Stock

## **Políticas e Estratégias para Definição de Senhas**

Para conceber políticas e estratégias adequadas na definição de senhas devemos primeiramente conhecer algumas das abordagens utilizadas pelo adversário para realizar a “quebra” da senha. Ainda, compreender a importância de estabelecer senhas que sejam efetivamente seguras nos sistemas.

### **Abordagens para quebra de senha**

A abordagem tradicional utilizada para “adivinhar” ou “quebrar” a senha, consiste em utilizar um dicionário contendo inúmeras senhas possíveis e testar essas senhas sobre o arquivo de senhas do sistema. Além de existir inúmeros arquivos de dicionários de senhas distribuídos na *internet**,* contendo milhões de senhas cadastradas, os adversários podem criar seus próprios dicionários de senhas.

Um programa testa exaustivamente todas as senhas contidas no dicionário. Caso não encontre nenhuma senha correspondente no arquivo, o programa de quebra de senhas tenta submeter variações de todas as palavras contidas no dicionário de senhas. Entre as variações temos a inversão da palavra *(**strings**),* substituição de caracteres (números e caracteres especiais) e sequência de caracteres.

Para cada tentativa que o programa realiza para tentar quebrar a senha, um *hash* correspondente a este valor é criado. Gerar milhões de *hash* pode levar um tempo considerável para que o programa consiga testar todas as senhas. Neste sentido, os atacantes vêm otimizando tal abordagem, ao invés do programa testar uma senha de cada vez, gerando um *hash* a cada tentativa, o adversário processa antecipadamente todos os valores contidos no dicionário, obtendo uma tabela contendo todas as senhas e seus *hashes* correspondentes. Esta tabela que contém todos os *hash* também é conhecida como Rainbow Table, onde a tradução para o português significa tabela “arco-íris”. Tal estratégias tem otimizado bastante o tempo que o adversário leva para tentar quebrar uma senha do sistema.

### **Abordagens de seleção de senhas**

Apesar de ser bastante significativo as taxas de adivinhação de senhas por parte do adversário, ainda não viável para o atacante utilizar uma simples técnica de força bruta a fim de testar todas as combinações possíveis de caracteres para descobrir uma determinada senha. Sendo que esta técnica além de exigir recurso computacional irá exigir um tempo considerável. Conforme pesquisa da Kaspersky, uma GPU que consegue testar 10,3 bilhões de hashes por segundo, levaria aproximadamente 526 anos para descobrir uma senha contendo 10 caracteres [Kaspersky, 2021]. Embora a utilização de supercomputadores poderia fazê-lo em poucas semanas, ainda um tempo considerável.

Deste modo, programas de quebra de senha exploram principalmente o aspecto de haver pessoas que acabam definindo senhas que são extremamente fáceis de adivinhar. Foi observado que quando os usuários podem selecionar suas próprias senhas sem que haja critérios ou políticas para definição de senhas, muitos usuários optam por senhas absurdamente curtas. Em um estudo realizado com 7 mil pessoas demostrou que 3% das pessoas tinham senhas com três ou menos de três caracteres de comprimento [Stallings, 2014].

Neste sentido, um atacante pode iniciar o ataque testando exaustivamente todas as combinações possíveis de senhas com comprimento de três ou menos caracteres, tendo sucesso em poucos segundos. Seguindo boas práticas, o ideal que o sistema não aceite senhas com um comprimento menor, exigir que o usuário adicione uma senha com pelo menos oito caracteres de comprimento.

O tamanho da senha é apenas um dos fatores que devem ser avaliados. Quando o usuário possui a liberdade de selecionar sua própria senha, não havendo critérios para a definição de senhas, muitos irão selecionar senhas fracas fáceis de adivinhar, tais como o nome, sobrenome, nome da rua onde mora, alguma palavra comum do dicionário entre outras. Para o adversário é conveniente, pois é algo que acaba facilitando o seu trabalho, pois a tarefa de quebra a senha acaba se tornando algo direto. Assim, o programa de quebra de senha precisa simplesmente testar um arquivo contendo as senhas prováveis que o usuário pode ter cadastrado. Visto que inúmeras pessoas utilizam senhas fáceis de quebrar, tal estratégia será bem-sucedida na maioria dos casos.

Deste modo, é ideal que os usuários sigam alguns requisitos de complexidade na definição de suas senhas, a senha deve contemplar pelo menos três dos requisitos das seguintes categorias:

- Letras maiúsculas (A à Z);
- Letras minúsculas (a à z);
- Dígitos (0 a 9);
- Caracteres especiais (caracteres não alfanuméricos): (~! @ #$%^&*_-+='|\() {} []:;"' <>,.? /).

Estabelecer políticas de senhas que definam tais requisitos de complexidade é extremamente aconselhável. Esta configuração de política de senha associado a definição de senha com no mínimo 8 caracteres, garante que exista pelo menos 218.340.105.584.896 possibilidades diferentes para uma única senha [Simpson, 2021]. Este tipo de política de senha dificulta bastante um ataque de força bruta, contudo ainda assim este ataque é possível.

### **Controle de acesso em arquivo de senhas**

Uma das maneiras mais efetivas de frustrar um ataque de senha é não permitir que o adversário tenha acesso ao arquivo de senhas. O arquivo de senhas deve ser acessível apenas pelos usuários privilegiados, o adversário não deve ter acesso de leitura sobre o arquivo de senha, desta maneira ele não terá acesso ao hash correspondente a senha de um usuário privilegiado. Em geral, os arquivos de senhas são preservados em um arquivo separado do arquivo que contém os identificadores dos usuários. Bastante comum nas distribuições do sistema operacional Linux, neste caso o arquivo de senhas é denominado “shadow” e o arquivo que contém os identificadores dos usuários é o arquivo “passwd”. É necessário que o arquivo de senhas seja protegido contra acessos não autorizados, sendo definido permissões adequadas. Ainda que a proteção dos arquivos de senhas seja imprescindível, as vulnerabilidades ainda permanecem:

- O adversário pode explorar uma vulnerabilidade do sistema operacional para tentar enganar o sistema de controle de acesso visando obter o arquivo de senhas. Ainda, pode adquirir o arquivo de senhas explorando a fraqueza do sistema de arquivos ou sistema de gerenciamento de banco de dados;
- Procedimentos realizados de forma imprudente ou acidentais podem expor o arquivo de senhas, deixando as senhas legíveis, comprometendo todas as contas dos usuários;
- Usuários que utilizam a mesma senha em diferentes contas, cadastradas em diferentes máquinas ou domínios estão mais suscetíveis a vulnerabilidades com senhas. Pois, caso a senha do usuário seja lida em qualquer que seja das máquinas, consequentemente as demais máquinas estarão comprometidas;
- O adversário pode explorar oportunidades para obter o arquivo de senhas, devemos observar a segurança física do datacenter e suas fraquezas. Destaca-se a importância da manipulação correta dos backups, para que apenas pessoas autorizadas tenham acesso, visto que o backup provavelmente contém os arquivos de senhas. Ressalta-se, que se o adversário tiver acesso a estrutura física do datacenter este poderá inicializar o sistema a partir de outro disco, utilizando um pendrive ou disco de boot (Live CD), tendo acesso ao arquivo de senha por meio de outro sistema operacional (em geral uma distribuição Linux).
- Além de capturar o arquivo de senhas, o adversário poderá utilizar uma estratégia um pouco mais sútil, este poderá analisar os pacotes que trafegam na rede a fim de obter o identificador e a senha dos usuários.

Deste modo, é essencial definir políticas de proteção de senhas adequadas, fornecer técnicas para forçar os usuários a definirem senhas difíceis de quebrar, seguindo certos critérios e padrões para obter uma senha forte.

## **Vulnerabilidades na Autenticação**

Em geral, os sistemas baseados em senhas mantêm um arquivo de senhas, este arquivo dispõe do identificador do usuário associado à sua respectiva senha. Para que as senhas não sejam armazenadas em formato "bruto" (ao efetuar a leitura do arquivo a senha fica exposta) uma das estratégias é adotar a aplicação de funções hash. Deste modo, ao invés de armazenar efetivamente a senha, adicionamos no arquivo o hash criptográfico da senha correspondente.

Ao longo das unidades iremos nos aprofundar em relação as funções hash criptográficas. Neste momento, é suficiente que você compreenda que uma função hash criptográfica utiliza algoritmos matemáticos para gerar uma saída de tamanho fixo independentemente do tamanho da entrada, mas principalmente, que esta função é praticamente impossível de ser invertida. Deste modo, um indivíduo, mesmo que tenha acesso ao arquivo de senhas do sistema não terá acesso efetivo as senhas dos usuários.

Contudo, mesmo adotando tal estratégia a autenticação pode ser alvo de ataques, entre os mais comuns:

- Ataques de dicionário;
- Ataque a conta específica;
- Ataque a senha popular;
- Adivinhação de senha contra usuário único;
- Explorar erros do usuário;
- Monitoração eletrônica;
- Explorar reutilização de senhas.

![[UE3_img9.jpeg]]

Fonte: ©Vitalii Vodolazskyi/Adobe Stock

**Ataques de dicionário:**

Na técnica de ataques de dicionário off-line o atacante obtém acesso ao arquivo de senhas. Por meio de um ataque de força bruta o "adversário" *(**hacker**)* compara os *hashes* de senhas comumente usadas com as senhas do sistema armazenadas no arquivo obtido. Em geral são utilizados programas que vão testando exaustivamente os *hashes* com as senhas. Ao encontrar um *hash* igual o atacante terá acesso ao sistema, sendo que ele terá acesso ao identificador do usuário e sua senha. Entre as contramedidas destacam-se a adoção de controle de acessos robustos visando impedir o acesso não autorizado ao arquivo de senhas, sistemas de detecção de intrusão para identificar se o sistema foi comprometido, um processo rápido de reemissão de senhas em caso de ocorrer um comprometimento no arquivo de senhas, adotar técnicas de criptografias adequadas.

**Ataque a conta específica:**

Neste ataque o adversário visa o acesso a uma conta específica, tenta descobrir a senha por meio de adivinhações, realiza tentativas até descobrir qual é a senha correta. Para este tipo de ataque a contramedida mais comum é utilizar uma política de *lockout**,* ou seja, realizar o bloqueio da conta após a realização de um número de tentativas incorretas. Seguindo boas práticas de segurança da informação, o ideal que o número de tentativas de login não ultrapasse mais de cinco tentativas consecutivas de acesso.

**Ataque utilizando senha populares:**

O ataque de senha popular consiste em utilizar um conjunto de senhas "populares" (muito utilizado pelos usuários) e testar estas senhas sobre vários identificadores de usuários.  É bastante comum os usuários definir senhas que sejam fáceis de recordar, porém tais senhas acabam sendo muito fáceis de decifrar. Como contramedida é possível estabelecer políticas para definição de senhas, inibindo que os usuários cadastrem senhas comuns nos sistemas, adicionalmente é ideal monitorar os endereços IP´s em busca de padrões de pedidos de autenticação, restringindo o acesso de tais IP´s ao identificar em casos de anomalias.

Adivinhação de senha contra usuário específico:

Este tipo de ataque consiste em descobrir informações sobre um determinado usuário e sobre as políticas de senha do sistema, utilizando tais informações o adversário realiza um ataque direcionado, tenta adivinhar a senha por meio do conhecimento obtido. As contramedidas incluem treinamento e a efetiva execução das políticas de senha, tornar as senhas difíceis de serem adivinhadas.

**Explorar erros do usuário:**

As senhas que são definidas pelos sistemas acabam sendo mais difíceis do usuário recordar, muito provavelmente o usuário acaba realizando uma anotação desta senha. Consequentemente isto pode acabar gerando um problema, uma pessoa mal-intencionada pode acabar lendo a senha escrita. Ainda, o usuário pode compartilhar intencionalmente a senha com outros usuários, para conceder privilégios de acesso a outros colegas (por exemplo acessar um arquivo ou e-mail). Visando evitar problemas com a exposição de senhas é necessário que o usuário tenha consciência que a senha é pessoal e de uso exclusivo dele, para que ele não passe a senha para outras pessoas. Outro aspecto que o usuário deve estar atento, são as táticas de engenharia social, onde o atacante pode tentar enganar o usuário a fim de fazer que este revele sua senha. Entre as contramedidas destaca-se a realização de treinamentos com os usuários, detecção de intrusão e autenticação multifator (utilização de senhas mais simples combinadas com outros mecanismos de autenticação).

**Monitoramento eletrônico:**

A senha ao ser comunicada na rede para realização de um acesso a um sistema remoto pode se tornar vulnerável a interceptação. Um adversário poderá monitorar a rede a fim de capturar os pacotes que trafegam na rede, podendo ter acesso a senha do usuário que está sendo encaminhada. Ainda que esta senha seja criptografada, existe um certo potencial de perigo, pois esta pode ser observada e reutilizada pelo adversário. Apesar existir algumas limitações no processo, a criptografia é uma das contramedidas mais adequadas, outro fator que deve ser realizado é o processo de treinamento dos usuários.

Um fator fundamental para combater as vulnerabilidades de senhas é estabelecer políticas de senhas adequadas. Na definição das políticas de senha alguns critérios devem ser levados em consideração, as senhas dos usuários devem contemplar certos requisitos: a senha deve ter tamanho mínimo (quantidade de caracteres), estabelecer o conjunto de caracteres (letras maiúsculas/minúsculas, números e caracteres especiais), proibir que o usuário utilize identificadores de usuário bastante conhecido (palavras do dicionário, nome, sobrenome), senha deve ser de uso exclusivo e caráter sigiloso, definir intervalos de tempo adequados para realização da troca da senha.

Ainda, norteados por padrões e boas práticas devemos evitar que os sistemas sejam deixados com senhas defaults. É bastante comum que os ativos dos sistemas de informação (hardware e software) sejam entregues com senhas pré-configuradas para os administradores do sistema. Geralmente, as senhas defaults são dispostas na documentação. Neste sentido, ao implementar uma nova solução de TI (tecnologia da informação) as senhas defaults devem ser trocadas, evitando que sejam facilmente adivinhadas.

Observando que não é raro os usuários utilizarem a mesma senha em diferentes sistemas e dispositivos, devemos ressaltar que isto pode trazer graves problemas. A utilização de senhas repetidas é extremamente desaconselhável, pois caso a senha seja comprometida em um dos sistemas, todos os demais sistemas que possuem a mesma senha também estarão comprometidos, onde os danos serão bem maiores. Neste sentido, é necessário que as senhas sejam diferentes, sendo necessário "educar" os usuários, bem como definir políticas de senha que restrinjam utilização de senha iguais ou semelhantes principalmente em dispositivos de redes.

Associado as vulnerabilidades na autenticação existe o sequestro da estação de trabalho do usuário. Neste tipo de ataque o adversário aguarda que a estação de trabalho no qual um usuário legítimo se autenticou esteja desatendida. Como contramedida para este ataque o usuário deve bloquear automaticamente o acesso a sua estação de trabalho quando a estação não estiver sendo utilizada. Destaca-se que por meio da detecção de intrusão é possível detectar mudanças no comportamento do usuário, verificar quando o usuário realmente está utilizando a máquina.

## **Meios de Autenticação**

No decorrer desta unidade conhecemos os diferentes mecanismos de autenticação, esses baseados nos quatro fatores básicos de autenticação: o que o indivíduo sabe, o que ele possui, características físicas e comportamentais. Ainda, constatamos que a autenticação baseada em senha é o principal mecanismo de autenticação. Contudo, observamos que este mecanismo possui suas limitações. A fim de fortalecer o procedimento de autenticação podemos associar mais de um mecanismo, conforme já mencionado denominamos esta abordagem como autenticação multifator. A combinação de diferentes tecnologias para autenticação permite alcançar níveis maiores de segurança.

Ao refletir no cenário de estudo do Banco de Tóquio, introduzido na Unidade 1, observamos que não havia presença de autenticação multifator nos sistemas interno do banco, tão pouco um mecanismo para rastrear as atividades dos indivíduos. Provavelmente, a existência de uma autenticação multifator nos sistemas do banco evitaria a rápida disseminação do *malware**.* O *malware* poderia até comprometer a primeira linha de defesa do sistema do banco, ou seja, a autenticação baseada em senha, porém, havendo um segundo mecanismo de autenticação por meio de biometria ou utilização de um token, seria um pouco mais difícil do código malicioso passar por esta outra barreira.

Neste sentido, para que o *malware* tivesse sucesso na sua investida, seria necessário que o usuário fornecesse um segundo fator de autenticação, muito provável um dispositivo físico por meio de *token* ou uma característica física como a própria digital do usuário. Devemos analisar um aspecto secundário, não existe nenhum registro de quem exatamente introduziu o *malware* nos sistemas interno do banco. Conforme disposto na norma ISO 27002, no processo de identificação e autenticação os identificadores dos usuários deveriam permitir o rastreamento das atividades dos indivíduos.  Observando que estamos tratando de uma instituição bancária tal registro é imprescindível. Não existe nenhum tipo de registro após o processo de autenticação com a senha, a rotina de código malicioso pode ter sido executada de forma acidental ou proposital, desta forma, não temos como identificar o responsável.

Uma instituição financeira ou bancária necessita de mecanismos de autenticação adequados, tais mecanismos devem ser proporcionais a sensibilidade da informação do banco. Ressalta-se que a combinação de diferentes tecnologias e mecanismos de segurança resultam em uma autenticação mais forte. A implementação de um mecanismo de autenticação multifator em primeira instância pode parecer um pouco complexa, porém é uma ação simples e altamente eficiente para manter a segurança das informações corporativas. Em outras palavras, este processo consiste em apenas um passo adicional onde o usuário será solicitado durante o processo de conexão para obter uma segunda forma de validação da sua identidade, seja por inserir um código no smartphone ou por fornecer uma impressão digital.

Neste sentido, o banco de Tóquio precisa de um mecanismo de autenticação robusto, nossa missão é garantir que as propriedades de segurança da informação do banco sejam preservadas. Para isto, esta “Unidade” tratou alguns dos principais aspectos do mecanismo de autenticação. Nas próximas unidades vamos conhecer outros mecanismos para garantir a segurança dos ativos de informação do banco, conhecer e saber como aplicá-los.  Mas não se preocupe, vamos nortear você nesta caminhada, ao longo das próximas unidades vamos te preparar para lidar com este e outros problemas de segurança da informação no âmbito real.

## **Explorando a Autenticação Multifator**

Este vídeo vai fornecer uma visão mais ampla sobre o mecanismo de autenticação multifator, quais os benefícios de utilizar uma autenticação de dois ou mais fatores, dicas e boas práticas para implementação deste mecanismo de segurança.

## **EXERCÍCIO**

**Exercícios de Fixação**

3. Quais as etapas fundamentais para gestão da Quais as etapas de um mecanismo de autenticação? E como são utilizadas?
4. Quais os principais fatores de autenticação?
5. Cite 3 recomendações estabelecidas na norma ISO 27002 que orientam o processo de identificação e autenticação.
6. Cite 3 mecanismos de autenticação e como eles funcionam.
7. Explique como funciona um mecanismo de autenticação baseado em token.
8. Explique como funciona um mecanismo de autenticação baseado em biometria.
9. Com suas palavras descreva o procedimento que o atacante (hacker) utiliza para quebrar uma senha no sistema.
10. O que é um Rainbow Table?
11. Cite alguns requisitos que devem ser considerados para definição de uma senha forte.
12. O que é um ataque de dicionário?
13. Como funciona a autenticação multifator?

## **Conclusão**

Esta unidade abordou o mecanismo de autenticação, principal linha de defesa contra os ataques cibernéticos. Foi analisado cada uma das etapas do mecanismo de autenticação. Adicionalmente, apresentamos as diretrizes estabelecidas na norma ISO 27002 que permite orientar o processo de identificação e autenticação, aplicando as melhores práticas. Ainda, foram apresentados os quatro fatores principais que permitem autenticar a identidade de um indivíduo. Correspondente ao que o indivíduo sabe, o que ele possui, características físicas e comportamentais do indivíduo.

Na sequência abordamos os diferentes tipos de autenticação, estabelecidos através dos fatores de autenticação. Neste sentido, existem diferentes mecanismos de autenticação, autenticação baseado em senha, *token* e utilizando biometria. Ainda, foi apresentado a autenticação multifator que permite a combinação de diferentes mecanismos de autenticação. Conforme discutido, a autenticação multifator permite reforçar a segurança no Ciberespaço, fornecendo uma camada a mais no processo de autenticação do usuário.

Apresentamos a autenticação baseada em senha, atualmente o mecanismo de autenticação mais comum encontrado nos sistemas de informação. Demostramos que o mecanismo de autenticação deve ser adequado e fortemente proporcional a sensibilidade da informação que o sistema contém. Foi destacado que a autenticação baseada em senha possui suas limitações. Enfatizado alguns critérios e requisitos para obter uma senha razoavelmente segura. Ainda, reforçamos a importância de as organizações estabelecer políticas de definição de senhas adequadas e treinamento para seus usuários.

Abordamos também os mecanismos autenticação baseados em *token**s,* como funcionam, e de que maneira eles podem reforçar o processo de segurança nos mecanismos de autenticação. Foram apresentadas duas tecnologias de autenticação baseado em *token**,* mecanismos utilizando dispositivos físicos como cartões de memória e os smart *token**s.* Observamos que token como cartão de memória permite armazenar informações, contudo não realiza nenhum tipo de processamento, um exemplo bastante comum são os cartões bancários que possuem uma fita magnética no verso. Em contrapartida, foi exposto os mecanismos que utilizam os smart tokens, dispositivo que em geral possui um microchip embutido, presente nos* smart cards* e outros tipos de s*mart* *token**s.*

Também abordamos os mecanismos de autenticação baseados na biometria. Enfatizamos como que funciona este tipo de mecanismo. Demostramos que os mecanismos de autenticação biométrica são segmentados em duas classes, mecanismos que utilizam características estáticas e outros dinâmicas. Observamos que entre as características estáticas temos as impressões digitais, a geometria da palma da mão, padrões da retina e íris dos olhos e identificação facial. Já entre os mecanismos associados as características dinâmicas temos assinatura, padrão da escrita, padrão do reconhecimento de voz e ritmo de digitação.

Por fim, resgatamos o caso de uso do “banco de Tóquio”, onde foi analisado o mecanismo de autenticação dos sistemas internos do banco. O objetivo foi identificar problemas de segurança da informação relacionados a autenticação, mas sobretudo como poderiam ter sido evitados se os mecanismos de segurança tivessem sido adequadamente implementados. Demostramos a importância de tais mecanismos dentro da organização, quanto mais significativo é a informação a ser preservada, mais robusto deve ser o mecanismo de autenticação. Concluímos que os mecanismos de autenticação são essenciais, contudo, só serão realmente efetivos por meio da aplicação de outras boas práticas de segurança da informação, principalmente no que se refere ao fator pessoa.

## **Controle de Acesso e Gestão da Identidade**

*Nesta Unidade, iremos estudar os principais mecanismos de controle de acesso e gestão de identidade. Conhecer os princípios e políticas de controle de acesso. Ainda, iremos nos aprofundar nos três modelos de controle de acesso: discricionário, mandatório e baseado em papéis. Apresentar algumas vantagens e desvantagens na implementação de tais modelos. Ainda, iremos explorar a matriz de acesso e as listas de controle de acesso. Também, demostraremos como podemos aplicar este tipo de controle de acesso sobre o sistema de arquivo, conheceremos o modelo tradicional e as listas de controle de acesso estendida. Ainda, conheceremos os principais modelos de acesso mandatório, modelo de Bell-LaPadula e o modelo Biba. Adicionalmente, apresentaremos a proposta do gerenciamento de identidades, mostraremos os principais elementos, mas sobretudo os benefícios da implementação desta abordagem. Por fim, apresentaremos algumas estratégias e boas práticas para implementar um mecanismo de acesso adequado.*

## **Princípios de Controle de Acesso**

O controle de acesso é o mecanismo de segurança que visa a proteção dos recursos dos sistemas de informação. Este mecanismo foi projetado para limitar as ações ou operações que determinado usuário autorizado pode realizar sobre determinado recurso. O mecanismo de controle de acesso deve coexistir com outros mecanismos de segurança, conforme estudamos na unidade anterior, esse mecanismo está fortemente interligado com o mecanismo de autenticação. O mecanismo de controle de acesso passa a exercer sua atividade logo após um usuário ser devidamente autenticado, sua responsabilidade é controlar os privilégios dos usuários legítimos, ou seja, o que este usuário pode fazer no sistema.

Basicamente toda área de segurança da informação depende do controle de acesso. Abordada, inclusive na definição de segurança da informação proposta na RFC 2828, que dispõe: *"**medidas que implementam e asseguram serviços de segurança em um sistema de computador, em particular as que asseguram o serviço de controle de acesso**"*.

Por resolução o controle de acesso estabelece políticas de segurança da informação específicas que permite determinar quem pode ter acesso a cada recurso fornecido no sistema e qual é o tipo de acesso concedido a cada ativo do sistema de informação. O controle de acesso está estreitamente associado com outras funções relativas à segurança da informação:

- **Autenticação****:** este tópico foi estudado amplamente na unidade anterior, mas em linhas gerais este mecanismo permite verificar se as credenciais de determinado indivíduo são válidas;
- **Autorização****:** esta propriedade visa fornecer permissão a uma entidade (usuário, grupo ou processo) do sistema permitindo ou restringindo o acesso a algum recurso do sistema.
- **Auditoria****:** esta função visa garantir que as políticas e procedimentos operacionais sejam devidamente cumpridos, além de permitir detectar falhas no processo e na segurança, por conseguinte solicitando mudanças prescrita nos termos de controle, processos e políticas.

O controle de acesso faz uma intermediação entre um usuário e o recurso que este está tentando acessar, tais como sistemas operacionais, aplicações, banco de dados entre outros. Primeiramente, o sistema necessita validar uma entidade que está solicitando acesso. Neste sentido, o mecanismo de autenticação é utilizado para determinar se o usuário tem realmente permissão para acessar o sistema. Posteriormente, o mecanismo de controle de acesso verifica se o acesso solicitado pelo usuário é permitido - por exemplo, o usuário abre um arquivo e tenta modificar o arquivo, o controle de acesso deve verificar se este usuário tem permissão de escrita sobre este arquivo.

![[UE4_img1.jpeg]]

Fonte: ©leowolfert/Adobe Stock

Dependendo do mecanismo de controle de acesso as permissões de acesso são definidas em um banco de dados de autorização. O administrador do sistema manipula este banco de dados e define as permissões de acesso de cada usuário, ou seja, estabelece o tipo de acesso e quais são os recursos que este usuário pode acessar. Então, a função de controle de acesso consulta o banco de dados para determinar se o mecanismo deve ou não liberar o acesso solicitado. Por fim, é necessário que todas as operações sejam registradas, neste seguimento a função de auditoria deve registrar as atividades do usuário no sistema, registrando tudo que foi acessado e modificado.

Visando garantir o funcionamento efetivo do controle de acesso, vários componentes são implementados, agem de forma cooperativa para proteger os sistemas. Os sistemas operacionais possuem pelo menos um componente de controle de acesso principal, em geral este componente é bastante robusto. Ainda, existem sistemas operacionais que permitem alterar o componente padrão de controle de acesso, mais comum em distribuições Linux, por exemplo habilitar o SELinux1. Além disso, determinadas aplicações também agregam funções de controle de acesso, tal como os SGBD (Sistemas de Gerenciamento de Banco de Dados). Adicionalmente, existem componentes de controle de acesso externos que provem uma outra camada de segurança, normalmente a arquitetura de segurança contempla o uso de firewalls que também fornecem o serviço de controle de acesso.

## **Políticas de Controle de Acesso**

As políticas de controle de acesso permitem definir quais os tipos de acesso são permitidos no sistema e sobre quais condições. Tais políticas normalmente são armazenadas no banco de dados de autorização. Em geral, as políticas de controle de acesso são classificadas em três grupos:

- **Controle de acesso discricionário****:** fornece o controle de acesso baseado na identidade do solicitante e em regras de acesso, permissões que definem o que este indivíduo está autorizado a fazer. Política nomeada discricionário devido ao fato de uma entidade poder conceder direitos de acesso a outras entidades sobre os recursos que lhe pertence.
- **Controle de acesso mandatório**: fornece o controle de acesso baseado na comparação de rótulos de segurança com autorização de segurança. Os rótulos de segurança permitem determinar quão crítico são os recursos do sistema. Por sua vez, a autorização de segurança permite definir quais entidades do sistema têm permissão para acessar determinados recursos. Política nomeada mandatória (obrigatória), porque neste caso uma entidade que está autorizada a acessar um certo recurso no sistema não tem privilégios de conceder acesso a aquele recurso a outras entidades.
- **Controle de acesso baseado em papéis****:** fornece o controle de acesso baseado nos papéis que um indivíduo desempenha dentro do sistema e por meio de regras que estabelecem quais acessos podem ser concedidos ao indivíduo que exerce tais papéis.

Um mecanismo de controle de acesso pode implementar mais de uma política, aplicadas a diferentes categorias dos recursos do sistema.

## **Elementos Fundamentais do Controle de Acesso**

Os elementos fundamentais do controle de acesso são: sujeito, objeto e direito de acesso.

O sujeito corresponde a uma entidade capaz de acessar um recurso no sistema, podendo ser um usuário, grupo ou processo. O conceito de sujeito é equivalente ao de processo. Os usuários obtêm acesso a um recurso por meio de um processo que atua em nome do usuário. O processo obtém as propriedades do usuário como as permissões de acesso.

No contexto de segurança da informação o sujeito é responsável pelas atividades relacionadas ao seu identificador, ou seja, ações executadas em nome do usuário. Os procedimentos de auditoria do controle de acesso devem ser utilizados para rastrear e registrar as atividades do usuário realizadas sobre algum recurso do sistema. Os sistemas de controle de acesso em geral definem três categorias de sujeito, concedendo privilégios distintos para cada categoria. Segue as principais categorias:

- **Proprietário:** o proprietário é o dono de um recurso, por exemplo um diretório ou arquivo. Em geral, o usuário responsável em criar determinado recurso automaticamente torna-se proprietário deste recurso.
- **Grupo:** adicional aos privilégios concedidos ao proprietário, um conjunto de usuários pode receber privilégios de acesso por pertencer a um determinado grupo. Em geral um usuário pode se associar a diversos grupos.
- **Outros:** esta categoria se aplica aos usuários autenticados no sistema que não são proprietários e nem pertencem a um grupo de determinado recurso, neste sentido são concedidos privilégios mínimos de acesso a este recurso.

Um objeto é caracterizado como sendo qualquer recurso cujo acesso deve ser controlado. O objeto em geral dispõe de alguma informação. Entre alguns exemplos de objeto podemos citar arquivos, diretórios, programas, mensagens, registros, páginas entre outros. Ainda, em um nível mais baixo alguns sistemas de controle de acesso englobam, bits, bytes, processadores, registradores, portas de comunicação, entre outros.

A quantidade e tipos de objetos que devem ser protegidos pelo mecanismo de controle de acesso variam conforme o ambiente em qual este mecanismo está inserido. Ainda, outros aspectos devem ser analisados, o nível de segurança necessário, complexidade do mecanismo, facilidade de uso e capacidade de processamento.

A permissão de acesso deve descrever a maneira que o sujeito deve acessar o objeto. Entre as principais permissões de acesso destacamos as seguintes:

- **Criar:** permissão que possibilita que os usuários criem tipos de objetos como arquivos, diretórios, registros, instâncias entre outros.
- **Excluir****:** permissão que possibilita que os usuários excluam determinados recursos do sistema, tais como arquivos, diretórios, registros, instâncias entre outros.
- **Listar****:** permissão que possibilita que os usuários visualizem os recursos, permite listar os arquivos e diretórios do sistema, e ainda realizar buscas nestes diretórios.
- **Leitura**: permissão que possibilita que os usuários visualizem informações de um determinado recurso do sistema, incluindo capacidade de copiar ou imprimir. Um exemplo típico é o privilégio de leitura fornecida em um arquivo.
- **Escrita****:** permissão que possibilita que os usuários realizem alterações em determinado recurso, podendo incluir, excluir e modificar os dados do sistema. Em muitos casos o acesso de escrita ele inclui o acesso a permissão de leitura. Por exemplo editar algum arquivo.
- **Executar**: permissão que possibilita que os usuários executem determinados programas ou rotinas de códigos, em geral programas executáveis ou scripts.

## **Controle de Acesso Discricionário**

Controle de acesso discricionário ou DAC, tradução do termo inglês *Discretionary Access Control*. Conforme mencionado anteriormente no controle de acesso discricionário, uma entidade pode receber privilégios de acesso que permitem que esta entidade habilite outras entidades a acessar certo recurso. Em geral, a abordagem implementada pelo controle de acesso discricionário é a matriz de acesso, adotada na grande maioria dos sistemas operacionais e SGBD. O conceito da matriz de acesso foi proposto por Lampson [LAMPSON, 1969].

Disposto em uma das dimensões (linhas ou colunas) da matriz são inseridos os sujeitos devidamente identificados que podem requisitar acesso a algum recurso. Geralmente, essa matriz consiste em uma lista de usuários e grupos. Em outra dimensão da matriz são inseridos os objetos que podem ser acessados. Considerando um detalhamento maior, os objetos são as instâncias dos dados cadastrados individualmente. Esses são agrupados com um maior nível de associação, como registros, arquivos e inclusive o banco de dados pode ser um objeto nesta matriz. Consequentemente, cada uma das entradas da matriz corresponde a uma permissão de acesso do sujeito (usuário ou grupo) a um determinado objeto (recurso).

Na figura abaixo um exemplo simples de uma matriz de acesso. Onde Bob é o proprietário do arquivo 1 e diretório 1, tem acesso de leitura e escrita sobre o arquivo 1 e permissão de leitura sobre o diretório 1, recebendo as permissões mínimas definidas por padrão, ainda recebe permissão de leitura sobre o arquivo 3 e escrita no diretório 2. Alice é proprietária do arquivo 3 possui permissão de leitura e escrita sobre este objeto, ainda permissão de leitura, escrita e execução sobre o arquivo 1, leitura sobre o arquivo 2 e leitura e escrita sobre o diretório 1, e assim por diante.

#ParaTodosVerem
Fonte: Autor

![[UE4_img2.png]]

A matriz de acesso é regularmente esparsa, onde uma grande quantidade dos elementos não está presente. Esta matriz poder ser analisada por colunas, por meio das listas de controle de acesso denominadas ACLs (*Acess Control Lists*). Nesta abordagem, para cada objeto a ACL dispõe dos usuários e as permissões de acesso autorizadas. As ACLs podem fornecer uma entrada padrão ou pública, isto possibilita que um sujeito (usuário ou grupo) que possua privilégios especiais, que não estão explicitamente contidos na ACL, recebam um conjunto de permissões padrão. As permissões definidas por padrão devem fornecer privilégios mínimos, em geral fornecido apenas acesso de leitura. Os elementos desta lista podem incluir usuários ou grupos. Abaixo a lista de controle de acesso (ACL) correspondente a matriz de acesso representada anteriormente.

#ParaTodosVerem
Fonte: Autor

![[UE4_img3(1).png]]

A análise realizada por linhas estabelece os rótulos de capacidade. O rótulo de capacidade permite especificar os objetos e permissões concedidas para cada usuário em específico. Utilizando esta abordagem cada usuário possui uma quantidade de rótulos, onde os rótulos podem ser fornecidos (emprestar ou dar) para autorizar outros usuários. Porém os rótulos de capacidade apresentam uma limitação quando comparado com as listas de controle de acesso, em relação à segurança são mais vulneráveis, pois os rótulos podem estar espalhados no sistema. Assim, a integridade do rótulo de capacidade deve ser garantida pelo mecanismo que a implementa, ou seja, proteger o rótulo para que não seja possível falsificá-lo.

Uma das maneiras que garantir que os rótulos não sejam falsificados é forçar o sistema operacional a manter todos os rótulos em nome dos seus respectivos usuários. Tais rótulos deveriam ser alocados em uma região que não seja acessível pelos usuários. Alternativamente, uma outra estratégia seria vincular um token não falsificável no rótulo. O token poderia gerar uma senha aleatória com um tamanho considerável, ou ainda *hash* criptográfica, onde o valor deve verificado no recurso sempre que este for solicitado. Os rótulos de capacidade são indicados para ambientes distribuídos, nos casos em que a segurança do recurso não tem como ser garantida. Na figura abaixo a representação do rótulo de capacidade correspondente a matriz de acesso.

#ParaTodosVerem

![[UE4_img4.png]]

Fonte: Autor

Existem vantagens e desvantagens de implementar os rótulos de capacidade. A vantagem que é fácil de determinar o conjunto de permissões que um usuário possui. A desvantagem que é mais difícil gerar uma lista de usuários com direitos de acesso específico a um determinado recurso.

## **Controle de Acesso a Arquivos**

Indiferente de qual seja o sistema operacional, todos implementam um mecanismo de controle de acesso sobre seus arquivos. Em geral os sistemas Windows e Unix implementam o controle de acesso a arquivos por meio das ACLs.   Nesta secção vamos explorar o controle de acesso a arquivos no Linux (sendo que este teve sua origem baseada no Unix).

No Linux todos os recursos do sistema operacional são manipulados por meio de arquivos. Por sua vez, todos os tipos de arquivos no Linux são gerenciados pelo sistema operacional por meio de uma estrutura denominada inodes. Os inodes ou "nó de índice" são estruturas de controle que compreende as informações fundamentais que o sistema operacional precisa manter para gerenciar o sistema de arquivos e controle de acesso. Cada inode está associado a um único arquivo, este armazena informações do arquivo, seus atributos, permissões e outras informações necessárias que permitem controlar este arquivo.  Na unidade de disco, com a criação do sistema de arquivos uma tabela de inodes é gerada, está tabela contém todos os inodes dos arquivos do sistema. Sendo assim, quando um arquivo é acessado, seu inode é trazido para memória principal então este é armazenado em uma tabela de inodes que se encontra na memória.

O sistema operacional organiza a estrutura do sistema de arquivos utilizando os diretórios, são estruturados de forma hierárquica. Deste modo, um diretório que se encontra disposto dentro de outro é denominado como subdiretório. Ressalta-se que um diretório na verdade é um arquivo que contém uma lista de nomes de arquivos e ponteiros associados a inodes, em outras palavras uma representação do sistema de arquivos. Tendo isto em vista, cada diretório também está associado a um inode.

### **Modelo tradicional de controle de acesso a arquivos no Linux**

O sistema operacional Linux é estruturado a partir do seu sistema de arquivos. Para garantir o funcionamento adequado do sistema operacional o controle de acesso a arquivos foi introduzido logo nas primeiras versões do Unix que serviu de base para implementação do Linux. Cada usuário no Linux possui um identificador (ID), valor numérico único que permite identificar um usuário. Todo usuário no Linux também é membro de pelo menos um grupo, este definido como grupo primário, além do grupo primário um usuário pode se associar a outros vários grupos. Semelhante ao usuário cada grupo é identificado por um ID, neste caso um ID de grupo. Assim que um arquivo é criado no Linux, ele será automaticamente associado ao ID de usuário e ID de grupo do seu criador. Adicionalmente, associado a cada arquivo existe um conjunto de 12 bits que permite definir as permissões para proteger o arquivo. As informações do ID de usuário, ID de grupo e bits de proteção compõe parte da estrutura do inode.

![[UE4_img5.jpeg]]

Fonte: ©Julien Tromeur/Adobe Stock

Em sequência, nove dos bits de proteção alocados no inode são utilizados para definir as permissões do arquivo, para ler, escrever e executar para o proprietário do arquivo, grupo que o arquivo está associado e todos os demais usuários autenticados no sistema. Neste sentido é possível definir uma hierarquia compreendendo o usuário proprietário, o grupo e demais usuários, fornecendo um conjunto de permissões de maior valor. Na figura abaixo é apresentado o esquema de permissões do Linux, as três primeiras permissões são direcionadas ao usuário proprietário, na sequência são definidas outras três permissões que são utilizadas para definir as permissões do grupo, por fim as últimas três permissões são reservadas para definir as permissões de todos os outros usuários.

#ParaTodosVerem

![[UE4_img6.png]]

Fonte: Autor

As permissões no Linux representam respectivamente read (r), write(w) e execute (x). Vejamos um exemplo de como as permissões são aplicadas, a figura abaixo mostra um exemplo das permissões aplicadas sobre o arquivo “arquivo1.txt”, este arquivo o proprietário possui permissão de leitura e escrita.

#ParaTodosVeremFonte: Autor

![[UE4_img7_2.png]]

Na sequência no arquivo “arquivo1.txt” é definido as permissões do grupo, referente as próximas três posições. Neste exemplo o grupo tem apenas permissão de leitura.

![[UE4_img8_2.png]]

Fonte: Autor

Por fim, as últimas três posições são utilizadas para definir as permissões de outros usuários que não são nem o proprietário do arquivo e não estão no grupo ao qual este arquivo está associado.

![[UE4_img9_2.png]]

Fonte: Autor

Neste exemplo mostramos as permissões aplicadas a um arquivo, quando aplicamos as permissões em um diretório, os bits de leitura e escrita são respectivamente utilizados para listar o diretório e modificar os arquivos dentro do diretório (criar, excluir e renomear). Por sua vez, o bit de execução permite acessar o diretório ou localizar algum arquivo dentro deste diretório. Para determinar o tipo de objetos que está sendo manipulado é utilizado um bit adicional antecedendo os bits de proteção. Entre os principais tipos de objetos são arquivos (-), diretórios (d), links simbólicos (l), arquivo de bloco (b), arquivo especial de caractere(c), canal(p) e socket (s).

![[UE4_img10(1).png]]

Fonte: Autor

Observe que no exemplo das permissões definidas anteriormente o primeiro caractere que antecedem os bits de proteção é utilizado um traço (-), ou seja, este objeto é um arquivo, se tivéssemos utilizado a letra “d” estaríamos trabalhando como um diretório, a letra “l” um link simbólico e assim por diante.

![[UE4_img11_2.png]]

Fonte: Autor

Os três últimos bits são utilizados para definir permissões adicionais para os arquivos e diretórios. Os três modelos especiais para controle de acesso são denominados Set User ID (SUID), Set Group ID (SGID) e Sticky Bit (Sticky).

![[UE4_img12(1).png]]

Fonte: Autor

As permissões especiais alteram o comportamento padrão do sistema operacional na manipulação dos arquivos que possuem tais permissões.  Então, vejamos qual o funcionamento do sistema operacional para cada uma dessas permissões.

A propriedade SUID permite ajustar o ID do usuário (SetUID), é aplicada apenas para arquivos executáveis não tendo qualquer efeito sob diretórios. Quando um arquivo executável com a propriedade SUID aplicada, entrar em execução, o programa deverá rodar com o ID do proprietário do arquivo, não com o ID do usuário que o executou. Em outras palavras, o processo do arquivo executável utilizando o acesso SUID será executado como se estivesse sido iniciado pelo dono do arquivo. Esta permissão de acesso só pode ser definida no campo de execução do proprietário do arquivo, atribuição realizada com a letra “s”. Tal funcionalidade proporciona a criação e utilização de programas privilegiados que podem usar arquivos que são normalmente inacessíveis a outros usuários.

![[UE4_img13(1).png]]

Fonte: Autor

Alternativamente, a propriedade SGID é utilizada para ajustar o ID do grupo. Esta propriedade tem uma função bastante semelhante a propriedade SUID para arquivos executáveis, contudo esta propriedade tem um efeito especial quando aplicado sob diretórios. Quando esta permissão é aplicada em um diretório, os novos arquivos que serão criados dentro deste diretório assumem o mesmo ID de grupo do diretório com a propriedade SGID aplicada. Esta permissão de acesso especial só pode ser definida no campo que habilita a execução para o grupo, atribuição realizada com a letra “s”.

![[UE4_img14(1).png]]

Fonte: Autor

Por último, o bit de permissão *Sticky*, em português o termo mais adequado seria “Aderente”. Esta propriedade quando habilitada em arquivos executáveis faz com que o sistema mantenha uma imagem do programa em memória depois que o programa finalizar. Deste modo, é possível aumentar o desempenho, pois isto permite realizar um cache do programa para a memória, a próxima vez que este arquivo for executado, ele será carregado mais rápido.

Adicionalmente, a propriedade *Sticky* pode ser utilizada para aumentar a segurança, pois quando aplicada sobre os diretórios, impede que outros usuários excluam ou renomeiem os arquivos nos quais não são donos. Assim, este diretório estará em modo *append-only* (somente incremento), apenas o proprietário do arquivo pode excluir e renomear esses arquivos. Esta propriedade é útil para gerenciar arquivos em diretórios temporários. Esta permissão de acesso especial é definida no campo que habilita a execução para outros usuários, atribuição realizada com a letra “t”.

![[UE4_img15(1).png]]

Fonte: Autor

Dados as características das permissões especiais mencionadas, é necessário ter certo cuidado ao definir as permissões. Em particular existe os ID de usuário que possui privilégios de "superusuário", comumente denominado nas distribuições Linux como usuário de "root". O usuário com privilégios de root está isento das restrições designadas pelo mecanismo de controle de acesso, este usuário tem amplo acesso a sistema e arquivos. Neste sentido, qualquer arquivo que pertença ao usuário de "root" e seja concedido permissão de SUID, consequentemente ele fornecerá acesso irrestrito ao sistema a qualquer usuário que execute tal arquivo. Portanto, é necessária muita cautela ao definir tais permissões.

Outro aspecto que deve ser avaliado no esquema tradicional de controle de acesso a arquivos no Linux é que por padrão ele propõe uma estrutura simples de domínios de proteção. O domínio está associado aos usuários, alterar o domínio reflete em substituir o ID do usuário temporariamente. Por exemplo, um usuário comum solicitar privilégios de superusuário para instalar um pacote no sistema ou efetuar uma configuração nos arquivos de sistema.

### **Listas de controle de acesso no Linux**

A maioria dos sistemas operacionais baseados no Unix suportam as listas de controle de acesso. No Linux denominada como lista de controle de acesso estendida.

No Linux é possível conceder uma lista de ID´s de usuários e grupos a um arquivo ou diretório, para isto é utilizado o comando setfacl. Este comando permite associar qualquer número de usuário ou grupo a um determinado tipo de objeto (arquivo ou diretório), fornecendo as permissões de leitura, escrita e execução de forma individual.

Esta abordagem fornece uma flexibilidade maior na hora de atribuir as permissões de acesso. Neste sentido, um arquivo além ser protegido pelo mecanismo de acesso a arquivos tradicional, adicionalmente pode dispor de uma ACL estendida. Os arquivos Linux fornecem um bit de proteção adicional para indicar se este arquivo possui uma ACL estendida ou não, este bit é representado por um sinal de adição (+).

![[UE4_img16_2.png]]

Fonte: Autor

O proprietário do arquivo “arquivo1.txt” é o usuário “aluno”, por sua vez o grupo proprietário é “equipe1”. Podemos utilizar o comando getfacl para visualizar as permissões na ACL estendida. Observe que adicionalmente, foram concedidas duas outras permissões na ACL estendida, conforme disposto na imagem abaixo existem dois usuários nomeados, usuários aluno2 e aluno3, ambos com permissão de leitura e escrita.

![[UE4_img17_2.png]]

Fonte: Autor

O Linux e grande parte das implementações baseadas em UNIX suportam ACLs estendidas e adotam as seguintes abordagens

1. As permissões das classes proprietário e outros, estabelecido pelos 9 bits de proteção do modelo de controle de acesso tradicional são correspondente as ACLs estendidas.

1. A permissões da classe grupo representam as permissões máximas que podem ser atribuídas aos usuários ou grupos nomeados, com exceção do proprietário do arquivo. Neste último, a permissão funciona como uma máscara.

1. Todos os usuários e grupos definidos na ACLs estendidas que estão associados a um arquivo, definem sua permissão na ACL estendida utilizando um campo de permissão de 3 bits (leitura, escrita e execução). As permissões listadas para um usuário ou grupo nomeado são verificadas no campo referente a máscara. Qualquer permissão que não esteja presente neste campo deve ser automaticamente desabilitada.

Assim, quando determinado processo solicita acesso a um tipo de objeto do sistema de arquivos duas etapas são realizadas. Na primeira etapa é selecionado a entrada da ACL estendida que correspondente ao processo solicitante. Então as entradas das permissões definidas na ACL estendida são examinadas na seguinte ordem: proprietário, usuários nomeados, grupos (proprietário ou nomeados), outros. Apenas uma das entradas é utilizado para definir a permissão de acesso. Posteriormente, na etapa seguinte é analisado se a entrada fornecida detém privilégios de acesso suficientes. Destaca-se que um processo pode fazer parte de mais de um grupo, consequentemente, mais de uma entrada de grupo pode ser fornecida a este processo. Então, se qualquer das entradas contiver a permissão solicitada o acesso é concedido. Em contrapartida, se nenhuma das entradas de grupo possui as permissões solicitadas o acesso deverá ser negado.

## **Controle de Acesso Baseado em Papéis (RBAC)**

O controle de acesso RBAC é baseado nos papéis que os usuários assumem no sistema. O Modelo RBAC define um papel como sendo uma função que é desempenhada dentro de uma organização. Neste sentido, os sistemas que implementam o modelo RBAC atribuem as permissões de acesso a papéis em vez das permissões de acesso de usuários individuais e grupos de usuários. Utilizando esta abordagem os papéis são atribuídos aos usuários, de maneira estática ou dinâmica, estabelecidos de acordo com sua responsabilidade.

![[UE4_img18.jpeg]]

Fonte: ©shane/Adobe Stock

O RBAC estabelece a relação entre os usuários e seus papéis de muitos para muitos, semelhante a relação entre os papéis e os recursos do sistema. Neste modelo, o conjunto de usuário pode ser alterado, em determinados ambientes com um a certa frequência, a atribuição de um ou mais papéis para o usuário pode ser realizado de forma dinâmica. Em geral, na grande maioria dos ambientes o conjunto de papéis é relativamente estático, ocorrendo adição ou remoção somente ocasionais. Nesta abordagem cada papel fornece permissões de acesso específicos a um ou mais recursos. Deste modo, o conjunto de recursos e as permissões de acesso não serão alteradas frequentemente. Na figura abaixo é representado a relação entre usuários, seus papéis e os recursos do sistema, observe que temos uma relação de muitos para muitos.

![[UE4_img19(1).png]]

Fonte: Autor

Para representar os elementos fundamentais de um sistema RBAC é possível utilizar uma matriz de acesso. Observe que na figura abaixo a matriz permite relacionar os usuários individuais a seus respectivos papéis. Geralmente, a quantidade de usuário é bem maior do que a quantidade de papéis. As posições marcadas na matriz indicam que um usuário foi designado a determinado papel, ao contrário este espaço deve ser deixado em branco. Destaca-se que um usuário pode receber vários papéis, e ainda um único papel pode ser atribuído a vários usuários.

![[UE4_img20(1).png]]

Fonte: Autor

Esquematizado na figura abaixo, definimos uma segunda matriz, com papéis como sujeitos. Em geral, existem poucos papéis e uma quantidade maior de objetos e recursos. Nesta outra matriz as entradas da matriz são as permissões de acesso que os papéis possuem. É importante destacar que nesta estrutura um papel pode ser definido como um papel, estratégia bastante interessante pois possibilita que seja definido hierarquias de papéis.

![[UE4_img21(1).png]]

Fonte: Autor

O RBAC possibilita a implementação do princípio do privilégio mínimo. Proposta do conceito que cada papel deve possuir um conjunto mínimo de permissões de acesso necessário para desempenhar aquele papel. Um usuário designado a desempenhar um determinado papel terá permissões somente para executar o que for requerido por este papel. Ainda, vários usuários que sejam designados para os mesmos papéis irão usufruir do mesmo conjunto mínimo de permissões de acesso.

## **Controle de Acesso Mandatório (MAC)**

Controle de acesso obrigatório ou MAC, tradução do termo inglês *Mandatory Access Control*. As políticas de controle de acesso definidas no MAC são estabelecidas pelo sistema e não pelo proprietário do recurso. Em geral este mecanismo é utilizado em sistemas onde os dados são extremamente sensíveis, tais como dados governamentais, segurança pública e militares.

![[UE4_img22.jpeg]]

Fonte: ©Gorodenkoff/Adobe Stock

Em um sistema de controle de acesso mandatório todos os sujeitos e objetos estão associados a um rótulo de sensibilidade. O rótulo de sensibilidade permite definir o grau de confiança de um sujeito. Quando aplicado em um objeto este define qual o grau de confiança necessário para acessar este objeto. Neste sentido, para um sujeito consiga acessar um objeto, esse deve possuir um rótulo de sensibilidade igual ou superior ao rótulo solicitado pelo objeto.

Um sistema baseado em MAC precisa garantir que os rótulos de sensibilidade sejam manipulados de maneira apropriada. Para tal, é definido o controle de importação e exportação dos dados, destaca-se que esta uma das funções críticas dos sistemas baseados em MAC, pois é necessário que a informação sensível seja protegida a todo momento.

Em geral, dois métodos são utilizados na implementação de um controle de acesso obrigatório, controle baseado em regras e controle de acesso baseado no modelo lattice.

- **Controle de acesso baseado em regras****:** Basicamente todos os sistemas de controle de acesso obrigatório implementam uma forma simples de controle de acesso baseado em regras, isto permite definir que o acesso seja permitido ou recusado baseado no rótulo de sensibilidade do objeto e do sujeito.
- **Controle de acesso baseado no modelo lattice:** Este tipo de controle permite que sejam tomadas certas decisões complexas que envolvem múltiplos objetos e sujeitos. Basicamente o conceito do modelo lattice é utilizar um grafo dirigido sem ciclos para definir níveis de prioridade a partir de uma ordenação parcial (exemplo: soldado -> cabo -> sargento).

### **Modelo de Bell-LaPadula**

O modelo de Bell-LaPadula (BLP), desenvolvido por David Elliott Bell e Leonard J. LaPadula em 1970 [BELL, 1973]. Neste modelo de controle de acesso, cada sujeito e objeto é atribuído a uma determinada classe. As classes formam uma hierarquia específica e são denominados níveis de segurança [BELL, 2005]. Um típico exemplo da utilização deste modelo é o esquema de classificação do exército americano dos EUA.

![[UE4_img23(1).png]]

Fonte: Autor

Ressalta-se que é possível adicionar um conjunto de categorias a cada nível de segurança, atribuindo a um sujeito o nível de segurança e a categoria adequada para poder acessar o objeto.

Esta abordagem pode ser aplicada em outras áreas, as informações podem ser estruturadas em níveis e categorias gerais, deste modo os usuários podem obter permissões para acessar categorias de dados específicas. Por exemplo, considerando um ambiente corporativo, poderia ser atribuído um nível de segurança maior nos documentos e dados de planejamento estratégico, concedendo permissões de acesso apenas aos diretores corporativos e sua equipe, na sequência dados financeiros e dados pessoais sensíveis, dados liberados apenas para o pessoal administrativo e diretores da empresa, em seguida os dados que podem ser acessíveis a quaisquer colaborares. Tal classificação pode seguir conforme exposto na figura abaixo.

![[UE4_img24(1).png]]

Fonte: Autor

Neste esquema um sujeito possui autorização de segurança em dado nível, ainda a classificação de segurança em dado nível. Deste modo, as classes de segurança permitem controlar o modo pelo qual o sujeito pode acessar um objeto. Este modelo propõe quatro modos de acesso:

- **Leitura:** este modo concede permissão ao usuário apenas de leitura sobre o objeto.
- **Adição:** este modo concede permissão ao usuário apenas de escrita sobre o objeto.
- **Escrita:** este modo concede as permissões ao usuário tanto de leitura como escrita sobre o objeto.
- **Execução**: este modo concede permissão ao usuário apenas de execução do objeto, poderá invocar o objeto.

Seguindo esta abordagem é possível implementar vários níveis de segurança (categorias), requisito denominado como segurança multinível. Neste escopo, a segurança multinível centrada em confidencialidade estipula que um sujeito em nível alto não pode transmitir informações para um sujeito de nível mais baixo. Para que a transmissão seja realizada o sujeito que possui o nível mais alto deve ser rebaixado ao mesmo nível do sujeito de nível mais baixo, então pode efetuar a transmissão da mensagem, assim que finalizar a transmissão o sujeito retorna ao nível anterior, técnica denominada como desclassificação autorizada. Um sistema de segurança multinível que visa garantir a confidencialidade deve estabelecer os seguintes requisitos:

- **Não ler para cima****:** Um sujeito só pode realizar a leitura de um objeto de nível de segurança equivalente ou menor que o seu. Este conceito é denominado como **propriedade de segurança simples.**
- **Não escrever para baixo****:** Um sujeito só pode efetuar escrita em um objeto de nível de segurança equivalente ou inferior ao seu. Este conceito é denominado como **propriedade-*** (propriedade estrela - curiosamente quando este modelo foi criado não foi definido nenhum nome para esta propriedade, no lugar foi colocado um coringa (*), o que acabou se tornando definitivo).

![[UE4_img25(1).png]]

Fonte: Autor

Por meio da figura abaixo, expomos a importância da propriedade * na segurança multinível. Conforme disposto na figura, um atacante (sujeito com intenção maliciosa) pode passar informações "teoricamente" confidenciais adicionando as informações em um container com um rótulo de classificação mais baixo que rotulado com classificação de segurança mais baixa que o seu. Desta maneira o adversário poderá obter acesso de leitura a informação consecutiva escrita pelo sujeito de nível de autorização mais baixo.

![[UE4_img26.png]]

Essas duas propriedades são extremamente importantes, elas fornecem os princípios de confidencialidade que estabelecem o controle de acesso mandatório. Sobre tais aspectos, qualquer tipo de acesso que não atenda as duas propriedades deverá ser negado.

### **Modelo de Integridade Biba**

O modelo de Bell-LaPadula visa garantir confidencialidade, preocupa-se que informações não sejam expostas sem autorização. Utilizando uma estrutura similar foi proposto o modelo Biba. O modelo Biba foi concebido para proteger a integridade, visa garantir que não haja modificação não autorizada nos dados [BIBA, 1977].

Este modelo trata a situação dos casos que existem dados que devem ser visíveis aos sujeitos em todos os níveis de segurança (permissão de leitura), porém devem ser modificados apenas por agentes autorizados. O modelo Biba implementa uma estrutura bastante semelhante ao modelo Bell-LaPadula, incluindo os elementos básicos, lida com sujeitos e objetos. Para cada sujeito e objeto é atribuído um nível de integridade, representado por I(S) e I(O), onde a letra "S" é utilizado para definir o sujeito e a letra "O" para definir o objeto. Para implementar este modelo é possível utilizar uma classificação hierárquica simples, determinado uma ordenação específica de níveis, do nível mais baixo até o nível mais alto. Da mesma que o modelo Bell-LaPadula, neste modelo é possível adicionar um conjunto de classes ao esquema de classificação. Este modelo considera os seguintes modos de acesso:

- **Modificar****:** permite escrever e atualizar informações em um determinado objeto.
- **Observar****:** permite ler as informações de um objeto.
- **Executar****:** permite executar um objeto.
- **Invocar****:** permite realizar comunicação de um sujeito com outro.

Os primeiros três modos de acesso são equivalentes aos modos implementados no Bell-LaPadula. Adicionalmente, um novo modo de acesso é incluído no Biba, o modo de acesso invocar. O modelo Biba propõe outras políticas alternativas que podem ser incorporadas ao modelo. Entre as mais relevantes, destaca-se a política de integridade estrita que dispõe as seguintes regras:

- **Integridade simples****:** esta regra determina que um sujeito apenas pode alterar um objeto se o nível de integridade que o sujeito possui for maior ou igual ao nível de integridade do objeto, regra representada por:
![[376873578d080c533d1c587fe10db7b8.png]]
- **Confinamento de integridade****:** esta regra determina que um sujeito apenas pode ter acesso de leitura sobre um objeto apenas se o nível de integridade do objeto for maior ou igual a nível de integridade que o sujeito possui, regra representada por:
![[768c3f3333b1b5f8497456e264eb843d.png]]
- **Propriedade de invocação****:** esta regra determina que um sujeito pode invocar um segundo sujeito apenas se nível de integridade do sujeito for maior ou igual ao nível de integridade do segundo sujeito, regra representado por:
![[06fc232cbd6e82392f547bf8cd3dd7ff.png]]

As primeiras duas regras são equivalentes às regras implementadas no modelo Bell-LaPadula, contudo tais regras têm por interesse a integridade, ainda invertem o significado do acesso de leitura e da escrita. A regra de integridade simples restringe que o acesso de escrita seja concedido para cima, deste modo evitando a contaminação dos dados de alta integridade. Por sua vez, um processo de baixa integridade permite a leitura de dados de baixa integridade, contudo a regra de integridade simples impede que este processo contamine um arquivo de alta integridade. Em via de regras, um processo de alta integridade não contaminaria um arquivo de alta integridade, porém qualquer erro de processo ou a disseminação de malware poderia ocasionar tal contaminação, neste sentido a regra de confinamento de integridade é necessária.

## **Gerenciamento de Identidades**

O gerenciamento de identidades trata-se de uma abordagem centralizada e automatizada para fornecer acesso a recursos de uma organização aos colaboradores e outros indivíduos autorizados. Destaca-se a também a difusão deste termo em inglês, *Identity and Access Management** *(IAM). A proposta desta abordagem é conceder uma identidade para cada usuário, vinculando atributos a esta identidade e estabelecendo uma maneira para que o usuário valide sua identidade. Os principais elementos de um sistema de gerenciamento de identidade são:

- **Autenticação****:** conforme estudado na unidade anterior, este mecanismo permite confirmar a identidade fornecida por usuário.
- **Autorização****:** esta propriedade permite conceder acesso aos recursos/serviços baseados no mecanismo de autenticação.
- **Contabilidade****:** este processo tem por finalidade registrar os acessos e autorizações.
- **Habilitação**: este elemento é responsável pelo processo inserção dos usuários no sistema.
- A**utomação de fluxo de trabalho****:** este elemento é responsável pela manipulação dos dados em um processo de negócio.
- **Administração delegada****:** este elemento é utilizado para fornecer controle de acesso baseado em papéis, consequentemente fornecendo as permissões.
- **Federação****:** este processo permite migrar a autenticação e permissão de um sistema para outro, normalmente processo realizado entre várias empresas, estratégia que permite reduzir o número de autenticações necessárias de um usuário.
- **Serviço próprio de mudança de senha****:** este processo habilita o usuário a alterar sua própria senha.
- **Sincronização de senha****:** este processo pode ser de dois tipos, autenticação única ou de autenticação reduzida. Na autenticação única um usuário pode acessar todos os recursos da rede depois de realizar uma única autenticação. Na autenticação reduzida são implementados vários processos de autenticação única, esta estratégia que permite reduzir o esforço necessário de adicionar um mecanismo de autenticação para cada processo individual.

![[UE4_img27.jpeg]]

Fonte: ©stanciuc/Adobe Stock

Na figura abaixo é apresentado uma arquitetura genérica de gerenciamento de identidades, demostrando o fluxo dos dados e as entidades. A entidade é um portador de uma identidade, em geral trata-se de um usuário que deseja acessar um recurso do sistema. Destaca-se que os dispositivos do usuário, processos agentes e sistemas servidores podem atuar como entidades. As entidades se autenticam em um provedor de identidades. Por sua vez, o provedor de identidades associa as informações de autenticação a uma entidade, contemplando os atributos e seus identificadores.

![[UE4_img28(1).png]]

Fonte: Autor

Existe um número cada vez maior de identidades digitais, atualmente vem sendo incluindo atributos no lugar de simplesmente utilizar um identificador tradicional (login e senha). Um serviço de atributos permite gerenciar a criação e manutenção de tais atributos. O gerenciador de identidades estimula que o usuário forneça suas informações de autenticação, tais informações são mantidas em um único lugar, então são liberadas para entidades consumidora de dados conforme as políticas de autorização e privacidade estabelecidas (em destaque a LGPD que trabalhamos na unidade 2). Os usuários podem adicionar atributos que desejam incluir na sua identidade digital, por exemplo: endereço, e-mail, telefone entre outros.

Os administradores do sistema também conseguem designar atributos aos usuários, por exemplo, podem fornecer papéis, definir permissões de acesso e manipular informações dos colaboradores.

Consumidores de dados são entidades que usam os dados fornecidos pelo provedor de identidades, frequentemente utilizados para dar suporte na tomada de decisões para autorizar o acesso ou manipular informações para auditoria. Um típico exemplo de consumidor de dados pode ser representado por um servidor de banco de dados ou servidor de arquivos que necessita das credenciais do usuário para saber qual acesso deve ser concedido a este usuário.

## **Mecanismo de Controle de Acesso do Banco de Tóquio**

Nesta secção vamos resgatar o estudo de caso do banco de Tóquio, introduzido na primeira unidade. A rápida disseminação do malware no banco demostra que o banco de Tóquio não implementou um mecanismo adequado de controle de acesso. Provavelmente, se um mecanismo de controle de acesso estivesse devidamente aplicado muitos dos problemas ocasionados no banco poderiam ter sido evitados.

O banco utiliza uma variedade de sistemas internos. Nas instituições bancárias é muito comum que tais sistemas sejam desenvolvidos para um ambiente de mainframe. No banco de Tóquio algumas dessas aplicações antigas foram migradas para uma arquitetura cliente-servidor, enquanto outras aplicações mais sensíveis ainda permanecem nos mainframes. As aplicações mais novas são hospedadas nos servidores, tais aplicações foram o principal alvo do malware. Antes do incidente, o banco implementava um simples sistema de controle de acesso discricionário. Os administradores do sistema definiam manualmente as permissões de acesso de cada funcionário, onde era criado um arquivo local de controle de acesso em cada uma das estações de trabalho. Essa abordagem era bastante inconveniente pois além do esforço exigido era propenso a erros, um dos grandes fatores que ocasionou o incidente no banco.

Para melhorar o sistema, o banco de Tóquio pode implementar um esquema de controle de acesso baseado em papéis, o que seria mais apropriado. Os papéis internos da organização podem ser definidos a partir da combinação do cargo oficial e a função que o colaborador realiza no banco. Esta estruturação baseada em papéis estabelecida no banco acaba sendo direcionada de forma natural para uma hierarquia de heranças baseado nos cargos estipulados no banco. Observe que no banco existe uma certa ordenação dos cargos oficiais dentro da organização, o que denota um certo nível de responsabilidade e poder. Por exemplo, estagiário, caixa, analista, gerente e diretor. Podemos definir os direitos de acesso levando em consideração a hierarquia do cargo. Deste modo, como boa prática um usuário designado a desempenhar um determinado papel terá permissões somente para executar o que for requerido por este papel.

Neste momento, o banco de Tóquio precisa de um mecanismo de controle de acesso adequado, nossa missão é garantir que as propriedades de segurança da informação do banco sejam preservadas. Para isto, esta “Unidade” tratou alguns dos principais aspectos do mecanismo de controle de acesso. Nas próximas unidades vamos conhecer outros mecanismos para garantir a segurança dos ativos de informação do banco, conhecer e saber como aplicá-los.  Mas não se preocupe, vamos nortear você nesta caminhada, ao longo das próximas unidades vamos te preparar para lidar com este e outros problemas de segurança da informação no âmbito real.

## **Explorando o Processo de Gestão de Identidade**

Este vídeo vai fornecer uma visão mais ampla sobre a gestão de identidade, vamos apresentar os elementos fundamentais associados a este processo, quais as vantagens e desvantagens de utilizar esta abordagem, dicas e boas práticas para implementação deste mecanismo de segurança.

## **EXERCÍCIO**

**Exercícios de Fixação**

Defina com suas palavras qual a finalidade do mecanismo de controle de acesso?

Quais as áreas/funções diretamente interligada com controle de acesso?

Quais os elementos fundamentais do controle de acesso?

Cite os três principais modelos de controle de acesso.

Cite as principais permissões de acesso que estão relacionadas aos elementos fundamentais de controle de acesso.

Qual a abordagem mais utilizada para implementar o controle de acesso discricionário?

O que é uma ACL? Como é utilizada?

Qual a finalidade do rótulo de capacidade?

O que é um inode?

Como é implementado o controle de acesso a arquivos no Linux?

Quais as permissões básicas do controle de acesso tradicional no Linux?

Quais as três permissões especiais no Linux? Como são utilizadas?

O que é uma lista de controle de acesso estendida no Linux?

Qual o conceito do modelo RBAC?

Quais requisitos de segurança multinível devem ser implementados no modelo de Bell-LaPadula para garantir a confidencialidade?

Qual a principal diferença entre o modelo Bell-LaPadula e o modelo Biba?

Quais os principais elementos de um sistema de gestão de identidade?

## **Conclusão**

Esta unidade abordou os principais mecanismos de controle de acesso. Em resumo, toda área de segurança da informação depende do controle de acesso. Conforme discutido, este mecanismo foi estruturado a fim de restringir as ações/operações que determinado usuário autorizado pode realizar sobre os recursos do sistema.

Ainda, destacamos que o mecanismo de controle de acesso deve coexistir com outros mecanismos de segurança. Adicionalmente, abordamos a definição estabelecida na RFC 2828, conforme disposto sobre o mecanismo de segurança existem "medidas que implementam e asseguram serviços de segurança em um sistema de computador, em particular as que asseguram o serviço de controle de acesso". Observamos que o mecanismo de controle de acesso está fortemente associado a outras funções de segurança tais como autenticação, autorização e auditoria.

Enfatizamos que o mecanismo de controle de acesso somente passa a exercer sua atividade após o processo de autenticação do usuário. Conforme amplamente discutido, o mecanismo de controle de acesso tem como responsabilidade controlar os privilégios dos usuários legítimos, impondo o que este usuário pode ou não fazer no sistema. Apresentamos ainda as principais políticas de controle de acesso. Conforme discutido, tais políticas permitem definir quais os tipos de acesso são permitidos no sistema e sobre quais condições. Na sequência estudamos os elementos fundamentais do controle de acesso, o sujeito, objeto e a permissão de acesso. Posteriormente, analisamos cada um dos modelos de controle de acesso.

Primeiramente, o controle de acesso discricionário que fornece o controle de acesso baseado na identidade do solicitante e em regras de acesso, conforme estudado são permissões que definem o que este indivíduo está autorizado a fazer. Ainda, exploramos as políticas de acesso discricionário, destacamos que esta política permite que uma entidade conceda direitos de acesso a outras entidades sobre os recursos que lhe pertence. Neste modelo, apresentamos a matriz de acesso, bem como as listas de controle de acesso denominadas ACLs. Explorando as ACLs, nos aprofundamos em controle de acesso a arquivos no Linux, tanto o modelo tradicional de controle de acesso a arquivos como também as listas de controle de acesso estendidas.

Por seguinte, conhecemos o controle de acesso baseado em papéis, acrônimo do termo em inglês RBAC. Descobrimos que este modelo fornece o controle de acesso baseado nos papéis que um indivíduo desempenha dentro do sistema. Vimos também que tais papéis permitem definir regras que serão utilizadas para conceder acesso aos indivíduos.

Esta unidade, abordou também o controle de acesso mandatório, vimos que este modelo concede o acesso a partir da comparação de rótulos de segurança com autorização de segurança. Conforme exposto, os rótulos de segurança permitem determinar quão crítico são os recursos do sistema. Por sua vez, a autorização de segurança permite definir quais entidades do sistema têm permissão para acessar determinados recursos.

Adicionalmente, apresentamos a estratégias utilizada na gestão de identidades. Vimos que esta abordagem permite conceder uma identidade para cada usuário, vinculando atributos a esta identidade e estabelecendo uma maneira para que o usuário valide sua identidade.

Por último, foi evidenciado a importância de implementar mecanismo de controle de acesso adequados nas organizações, ressaltamos os benefícios e as etapas necessárias. Por fim, resgatamos o caso de uso do “banco de Tóquio”. Foi exposto as fraquezas no controle de acesso do banco, além de apresentar os problemas de segurança da informação que desencadearam o incidente de segurança, destacamos a importância do mecanismo de controle de acesso para evitar este episódio.

## **Criptografia**

*Nesta Unidade, iremos estudar as funções de **hash** criptográficas. Conhecer os princípios e as propriedades fundamentais para implementação das funções **hash** criptográficas. Ainda, iremos nos aprofundar nos principais algoritmos de função **hash** criptográficas, tais como o SHA, SHA-1, SHA-2, MD5 entre outros. Adicionalmente, apresentar as funções **hash** baseadas em **Cipher Block Chaining**, verificar como que ela é estruturada, quais os benefícios e ameaças associados a esta abordagem. Também, iremos demostrar algumas das aplicações das funções **hash** criptográficas, em destaque o uso de autenticação de mensagens e assinaturas digitais. Apresentaremos, os requisitos de segurança para implementação de função **hash** criptográficas. Abordaremos o impacto das colisões em funções **hash** criptográficas, como que o adversário pode explorar esta e outras fraquezas. Por fim, iremos expor os algoritmos de função **hash** estabelecidos pelos padrões internacionais, ou seja, mostraremos algumas estratégias e boas práticas para implementação das funções **hash** criptográficas.*

## **Funções Hash Criptográficas**

Uma função *hash* mapeia uma mensagem de entrada de tamanho variável em um bloco de dados de tamanho fixo, denominado de código *hash**.* O *Hash* também é conhecido como *checksum**.* O termo *checksum* é bastante utilizado para se referir ao código usado para verificar a integridade de uma mensagem transmitida ou que foi armazenada em algum meio por determinado tempo.

Diferente dos algoritmos de criptografia convencional, o algoritmo de uma função *hash* não é reversível, ou seja, você não consegue retornar ao valor original. As funções *hashes* fornecem a garantia de que a mudança de qualquer bit na mensagem produzirá um código *hash* diferente.

A função *hash* destinada às aplicações de segurança é denominada como função *hash* criptográfica. O algoritmo de uma função *hash* criptográfica estabelece dois princípios:

- A propriedade de mão única.
- A propriedade livre de colisão.

A propriedade de mão única garante que a partir do código *hash* você não consegue retornar ao seu valor inicial, sendo computacionalmente inviável. Por sua vez, a propriedade livre de colisão garante que dois objetos de dados diferentes não serão mapeados com o mesmo resultado *hash**.* Dado essas duas propriedades, as funções de *hash* criptográficas são amplamente utilizadas para determinar se os dados foram alterados ou não.

A função *hash* disposta na fórmula h=H(M), onde a variável M corresponde ao valor de entrada para a função H, tendo como retorno h como sendo o valor do *hash* que possui um tamanho fixo. Esta função é representada pela figura a seguir, a entrada da função *hash* é preenchida por um número inteiro, em geral múltiplo de 1024bits, incluindo também como entrada o tamanho em bits da entrada original. Tal estratégia permite dificultar que um adversário consiga reproduzir uma mensagem com o mesmo valor de *hash.*

![[UE5_img1.png]]

Fonte: Autor

## **Aplicações de Funções Hash Criptográficas**

A função *hash* criptográfica é utilizada em diversas aplicações de segurança, sendo também utilizada em alguns dos protocolos da internet. Nesta seção veremos algumas das principais aplicações das funções *hash* criptográficas no âmbito de segurança da informação.

### **Autenticação de Mensagem**

As funções hash criptográfica podem ser utilizadas para implementar os serviços de autenticação de mensagens. O mecanismo de autenticação de mensagens permite verificar a integridade de determinada mensagem. Este mecanismo é utilizado para garantir que uma mensagem transmitida não foi modificada, ou seja, não houve inserção ou exclusão de algum conteúdo da mensagem. Adicionalmente, o mecanismo de autenticação pode ser utilizado para fornecer garantia que a identidade de um emissor é válida. Ao utilizar uma função hash criptográfica para realizar autenticação de mensagem o valor decorrente deste processo é denominado resumo de mensagem.

A função hash para autenticação de mensagens tem por base os seguintes passos. Primeiramente, o emissor utiliza a função hash para calcular o valor de hash dos bits da mensagem, então transmite a mensagem em conjunto com o valor do hash. Posteriormente, o receptor realiza o mesmo cálculo, utiliza a função hash sobre os bits da mensagem, então compara o hash obtido como o hash que foi enviado pelo emissor da mensagem. Por conseguinte, caso os hashes sejam diferentes, o receptor consegue identificar se a mensagem foi adulterada. Observe os passos de autenticação de mensagens apresentados na figura a seguir.

![[UE5_img2.png]]

Fonte: Autor

O valor *hash* necessita ser transmitido de uma forma segura. É fundamental que o código hash seja protegido, pois se um adversário tentar modificar a mensagem, não terá como alterar o valor do *hash* para tentar enganar o receptor. Deste modo, evita-se um ataque de *man-in-the-middle*, conforme apresentado na figura a seguir.

![[UE5_img3.png]]

Fonte: Autor

Neste tipo de ataque, o adversário se coloca entre o emissor e o receptor da mensagem. Quando o emissor transmite uma mensagem e adiciona um valor de *hash**.* O adversário intercepta a mensagem, então modifica a mensagem e adiciona um novo valor de *hash* gerado a partir da mensagem que foi modificada. Neste sentido, quando o receptor receber a mensagem, irá checá-la, porém não conseguirá perceber se a mensagem foi modificada. Deste modo, para impedir este tipo de ataque, o código hash gerado pelo emissor deve ser protegido.

A autenticação de mensagem pode ser obtida utilizando um código de autenticação de mensagens, também conhecido como função de *hash* chaveada. A função de *hash* chaveada é normalmente usada entre duas partes (emissor e receptor) que compartilham uma chave secreta para trocar informações. Uma função de *hash* chaveada recebe como entrada uma chave secreta e uma mensagem e produz um código *hash**,* conhecido como MAC (*Message Authentication Code*). O MAC é associado a mensagem a ser protegida. Caso seja necessário verificar a integridade da mensagem, a função chaveada pode ser aplicada à mensagem e o resultado é comparado com o valor MAC que foi associado. Desta forma, se um adversário alterar a mensagem não conseguirá alterar o valor do MAC que foi associado sem conhecer a chave secreta compartilhada entre as partes. Ainda, ressalta-se que parte do receptor que está verificando a mensagem tem certeza do emissor da mensagem, visto que apenas o emissor conhece a chave secreta.

### **Assinaturas Digitais**

Uma outra aplicação de função *hash* criptográfica bastante importante é a assinatura digital. O funcionamento de operação da assinatura digital é bastante similar ao funcionamento da função *hash* chaveada. Retratando do mesmo processo da assinatura digital, o valor *hash* da mensagem é cifrado utilizando a chave privada de um determinado usuário. Neste sentido, qualquer indivíduo que tenha posse da chave pública do usuário poderá verificar a integridade da mensagem na qual está associada a assinatura digital. Assim, um adversário somente conseguirá modificar a mensagem se ele tiver posse da chave privada do usuário.

Na figura a seguir é apresentado de maneira simplificada o processo de assinatura digital utilizando o código *hash**.* Observe que o código *hash* é cifrado utilizando a chave privada do emissor, decifrado com a chave pública. Na próxima unidade nos aprofundaremos nos conceitos de criptografia de chave pública e privada. Neste momento, é suficiente compreender que a criptografia de chaves pública e privada utiliza duas chaves distintas, uma para codificar e outra para decodificar mensagens.

![[UE5_img4.png]]

Fonte: Autor

### **Outras aplicações**

Entre outras aplicações, as funções *hash* criptográficas são utilizadas para criar os arquivos de senha de mão única conforme visto na Unidade 3 – Mecanismos de Autenticação, à medida que nos aprofundamos no mecanismo de autenticação, descobrimos que o sistema operacional ao invés de armazenar diretamente o valor da senha, armazena o *hash* correspondente a senha. Logo, o adversário que conseguir acesso ao arquivo de senha não terá acesso efetivo a senha real, dado que a partir do valor do *hash* ele não conseguirá retornar ao valor original da senha. De maneira simplificada, quando um usuário solicitado acesso ao sistema e fornece sua senha, o mecanismo de autenticação imediatamente aplica a função *hash* criptográfica sobre a senha digitada pelo usuário, então é realizado o processo de verificação, onde o *hash* obtido é comparado com valor do *hash* que está armazenado no arquivo de senha. Destaca-se que este procedimento é realizado na grande maioria dos sistemas operacionais.

Uma outra aplicação bastante interessante é a utilização da função *hash* criptográfica para detecção de intrusão e detecção de vírus. Neste caso, a função *hash* criptográfica é aplicada sobre cada arquivo do sistema, gerando um valor *hash* para cada arquivo, então é armazenado uma cópia de segurança dos valores de *hash* - de preferência em uma mídia externa. Posteriormente, você poderá utilizar os valores de *hash* armazenados para determinar se um arquivo foi modificado no sistema, ou seja, aplica-se a função *hash* criptográfica sobre o arquivo que se deseja analisar, então compara-se esse *hash* com o valor armazenado anteriormente.

Ainda, outra aplicação para a função *hash* criptográfica é utilizá-la para construir um gerador de número pseudoaleatório, cujo uso é bastante comum em aplicações que geram as chaves simétricas.

## **Colisões em Funções Hash Criptográficas**

Dado o valor de *hash* h = H(x), definimos x como sendo a pré-imagem de h. Em outras palavras, significa que x é um bloco de dados cuja função *hash* H obtém o *hash* h. Como a função H é mapeada em uma cardinalidade de muitos para um, para qualquer valor existente de h, existirá várias pré-imagens. Neste sentido, uma colisão ocorre quando temos a situação que x ≠ y e H(x) = H(y). Esta notação denota o conceito de colisão, onde ao fornecer duas entradas diferentes para função *hash* é obtido dois códigos de *hash* idênticos. Tratando-se de função *hash* criptográfica a colisão é algo extremamente indesejado, principalmente quando precisamos garantir a integridade dos dados.

![[UE5_img5.png]]

Fonte: Autor

A fim de tentar identificar potenciais colisões para um valor de

*hash*

*,*

devemos considerar a quantidade de pré-imagens existentes para este valor. Para tal, definimos um tamanho de código

*hash*

de n

*bits*

e utilizamos a função

*hash*

H que recebe como entrada uma mensagem contendo um tamanho de b

*bits*

*,*

sendo

*b > n*

. Assim, podemos calcular o total de mensagens possíveis, como sendo

![[1f19e7db57c11f899adc2afeec898f87.png]]

, consequentemente teremos um total de

![[29cbcf4089980c5088ecfe56b05179db.png]]

valores de

*hash*

possíveis. Deste modo, para cada valor de

*hash*

teremos

![[bda1adf6a1c3386eaf0b829b3169d748.png]]

pré-imagens. Então, se a função

*hash*

H distribuir de maneira uniforme os valores de

*hash*

*,*

cada valor de

*hash*

possuirá um valor aproximado de

![[bda1adf6a1c3386eaf0b829b3169d748 1.png]]

pré-imagens. Ainda, devemos destacar que caso seja autorizado entradas de qualquer tamanho, não limitando o tamanho da entrada com um comprimento fixo, teremos uma grande variação no número de pré-imagens por valor de

*hash*

*.*

Contudo, exploramos os riscos de segurança sempre no pior caso. Para compreender com uma melhor clareza o impacto das colisões em termos de segurança das funções *hash* criptográficas, devemos definir com maior precisão os seus requisitos de segurança.

## **Requisitos de Segurança das Funções Hash Criptográficas**

Existem ao todo basicamente sete requisitos que devem ser observados na implementação de funções Hash criptográficas, seguem dispostos abaixo:

1. Tamanho de entrada variável

1. Tamanho de saída fixo

1. Eficiência

1. Propriedade de mão única

1. Resistência à colisão fraca

1. Resistência à colisão forte

1. Pseudoaleatoriedade

Em geral, tais requisitos são amplamente aceitos para implementar uma função *hash* criptográfica. Destaca-se que as três primeiras propriedades são utilizadas em aplicações práticas de função *hash**.* O** ****tamanho de entrada variável**** **é usado para definir um bloco de dados de qualquer tamanho para função *hash* H. Por sua vez, o **tamanho de saída fixo** determina uma saída com um tamanho de código *hash* fixo, indiferentemente do tamanho da mensagem de entrada. Adicionalmente, utilizamos a propriedade da **eficiência**** **para calcular o valor do *hash* a partir da função *hash* H(x), obtendo facilmente o valor de *hash* para qualquer que seja o valor de x, aplicado tanto para implementação de *hardware* como por *software.*

A **propriedade de mão única** é definida como resistência à pré-imagem. Esta propriedade estabelece que para qualquer valor de *hash* h que seja informado, é computacionalmente impossível encontrar y, tal que H(y) = h. Em outras palavras, é fácil gerar o código *hash* a partir da mensagem, porém é praticamente impossível gerar a mensagem a partir do código *hash**.* Esta é uma das principais propriedades da função *hash* criptográfica, técnica bastante utilizada associada ao mecanismo de autenticação que adota o uso de valor secreto. Reforçando que neste caso o valor secreto não é enviado. Contudo, considerando uma função *hash* que não possua a propriedade de mão única, um adversário poderia explorar facilmente o valor secreto.

A **resistência à colisão fraca** é definida como resistência à segunda pré-imagem. Esta propriedade garante que é impossível obter uma mensagem alternativa que possua o mesmo valor de *hash* de uma determinada mensagem. A propriedade de resistência à colisão fraca estabelece a seguinte premissa, para qualquer bloco de dados x informado é computacionalmente impossível encontrar um valor de y ≠ x que atenda a sentença H(y) = H(x). Tal propriedade protege contra a falsificação de uma *hash* cifrado. Considerando um cenário onde esta propriedade não exista, um adversário poderia interceptar uma mensagem com o código *hash* cifrado, então gerar um código de *hash* decifrado de uma mensagem, por fim, gerar uma mensagem diferente reaproveitando o mesmo código *hash* para validar a mensagem modificada.

As funções *hash* que atendem as cinco primeiras propriedades mencionadas anteriormente são denominadas como função *hash* fraca. Porém, a função *hash* pode possuir uma sexta propriedade, denominada de **resistência à colisão forte**, tal propriedade confere proteção contra um ataque onde um adversário gera uma mensagem para ser assinada por outra parte. Esta propriedade estabelece a premissa que é computacionalmente impossível encontrar qualquer par (x, y), tal que H(x) = H(y). Consequentemente, a função que implementa esta propriedade é chamada de função *hash* forte.

Adicionalmente, existe um último requisito denominado como a propriedade da **pseudoaleatoriedade**. Apesar desta propriedade não ser amplamente citada, este requisito da função *hash* criptográfica está relativamente implícita. As funções *hash* criptográficas são normalmente utilizadas para auxiliar no processo de derivação de chaves e ainda geração de número pseudoaleatório. Além disso, nas aplicações que visam integridade de mensagens, as três propriedades de resistência que consistem na saída da função *hash* aparenta ser aleatório. Neste sentido, é possível afirmar que a função *hash* produz uma saída pseudoaleatória.

## **Message Digest Algorithm 5**

O MD5 (Message Digest Algorithm 5) é uma função hash amplamente utilizada que produz um valor de hash de 128 bits declarado em uma string de 32 caracteres. O MD5 foi desenvolvido por Ronald Rivest da RSA Data Security, Inc. em 1991. Esta função hash foi desenvolvida para substituir a função hash anterior MD4 que apresentava algumas vulnerabilidades de segurança. Então, em 1992 o MD5 foi especificado como padrão na RFC 1321.

Destaca-se que o MD5 é um algoritmo unidirecional (algoritmo de mão única), a partir do valor hash gerado no MD5 não é possível retornar ao valor da mensagem. A partir de uma mensagem de tamanho variável (entrada de qualquer tamanho), o MD5 produz um valor hash fixo, correspondente a 128 bits.

Observa-se que como qualquer função hash criptográfico um dos requisitos fundamentais é garantir que não exista colisões entre os hash (conforme estudando anteriormente, encontrar duas mensagens distintas com mesmo hash). Considerando uma das principais fraquezas do MD5, as pseudocolisões foram exploradas no algoritmo MD5. Em destaque, o malware denominado Flame em 2012 explorou as vulnerabilidades do MD5 para falsificar assinaturas digitais da Microsoft.

Este algoritmo é de domínio público, pode ser utilizado para quaisquer fins. Apesar do MD5 ter sido projetado para ser utilizado como função hash criptográfica, foram identificadas algumas vulnerabilidades de segurança no algoritmo. Ainda assim, o MD5 é útil para ser utilizado para fins não criptográficos, como determinar uma partição para uma chave específica em um banco de dados particionado. Também pode ser utilizado para checar a integridade dos dados contra corrupção não intencional. Além, de ser utilizado como mecanismo de integridade em vários protocolos de padrão Internet.

Após a exposição das fraquezas do MD5, Roland Rivest em conjunto com outros pesquisadores publicaram em 2008 uma nova versão do algoritmo, com hash de tamanhos de 224, 256, 384 ou 512 bits. O novo algoritmo foi denominado como MD5. Este algoritmo foi cogitado para ser utilizado como o novo algoritmo SHA-3, porém acabou não sendo aprovado por ser considerado um algoritmo muito lento para os computadores da época. Apesar da fraqueza e depreciação dos pesquisadores da área de segurança, o MD5 ainda continua sendo amplamente utilizado.

## **Funções Hash Baseadas em Cipher Block Chaining**

Na literatura foram apresentadas diversas propostas a fim de aperfeiçoar as funções hash criptográficas, uma das estratégias foi o uso da técnica de Cipher Block Chaining, não adotando uma chave secreta. Entre as primeiras propostas destaca-se a proposta apresentada por Rabin [Rabin, 1978]. Esta proposta consiste em dividir a mensagem (M) em blocos de tamanho fixo (

![[5572e6572b6c58117180cee028e8ea3f.png]]

,

![[d73df264ab8f423a6cd0ccc7ff575c05.png]]

, ....

![[99d9bada124f1f47ed20a46f084cff7c.png]]

). Posteriormente, utilizar um sistema de cifragem simétrica para calcular o código hash G, utiliza-se a seguinte notação:

**Ho=valor inicial**

**Hi=E(Mi,Hi−1)**

**G=Hn**

Semelhante a qualquer código de hash, esta abordagem também está sujeita ao ataque de dia do aniversário, observando que caso seja utilizado um algoritmo de cifragem DES com um código hash com somente 64 bits, o sistema será vulnerável. O ataque do aniversário consiste em um tipo de ataque criptográfico que explora o cálculo matemático por trás do paradoxo do aniversário na teoria da probabilidade.

O paradoxo do aniversário afirma que dado um grupo de 23 sujeitos selecionados aleatoriamente, a chance de dois desses sujeitos terem a mesma data de aniversário é de mais de 50%. Ainda, estendendo este paradoxo, dado 57 ou mais sujeitos, a probabilidade chega a ser maior do que 99%, contudo, não pode ser considerado exatamente 100%, exceto que haja no mínimo 367 pessoas. Este tipo de ataque pode ser utilizado para explorar a comunicação entre duas ou mais partes. Onde o ataque depende da maior probabilidade de colisão localizadas entre as tentativas de ataque aleatório e a quantidade fixa de permutações.

Um ataque derivado do ataque de dia do aniversário pode ser aplicado mesmo que o adversário tenha acesso somente a uma das mensagens e a assinatura válida, e não tenha acesso para obter outras assinaturas. Então, vamos explorar um pouco este cenário, considerando que o adversário consiga interceptar uma mensagem com uma assinatura no formato de um código hash cifrado e que o código de hash não cifrado tenha uma quantidade exata de m bits em sua extensão [Stallings,2008], deve se considerar:

1. Utilizar o algoritmo citado anteriormente (código de hash G) para realizar o cálculo do código de hash não cifrado G.

1. Construir qualquer mensagem desejada norteado pelo formato Q1, Q2,…Qn−2  


1. Calcular , para . 


![[efeeb99f941ef88e43c97d1aace5d3d2.png]]

![[5742b3bc6723f448aa79dc0d872784e6.png]]

1. Gerar   blocos aleatórios; para cada bloco X, calcular . Gerar   blocos aleatórios adicionais; para cada bloco Y, calcular D(Y,G) , onde D é a função de cifragem que corresponde a E.

![[4f1e7a1126b66d15a148c7e5c180e21f.png]]

![[36f7ae0b3b35fe918c430ffece92fd29.png]]

![[f22e7aca73f0ece6ad09db8d4a967e3e.png]]

1. Baseado no paradoxo do dia do aniversário, considerando alta probabilidade, haverá um X e Y tal que blocos aleatórios adicionais; para cada bloco Y, calcular

![[a818bad1ed9e7945b5ee3e295fe45bb2.png]]

1. Formando a mensagem Q 1, Q2,…Qn−2, X,Y . Conferir que esta mensagem tem o código de *hash* G. Consequentemente, poderá ser utilizada com a assinatura cifrada que foi interceptada. 


Este tipo de ataque é conhecido como ataque de *meet-in-the-middle*. Vários autores na literatura propuseram otimizações para fortalecer a técnica tradicional de *Cipher Block Chaining*. Em contrapartida, os adversários também exploraram as novas técnicas a fim de encontrar vulnerabilidades. Algumas técnicas de *Cipher Block Chaining** *são vulneráveis a uma série de tipos de ataques. Em geral, alguma variante do ataque de dia do aniversário terá sucesso contra uma técnica que utilize *Cipher Block Chaining* sem o uso de chave secreta, no caso de utilizar um código de *hash* de 64 bits ou menos, ou ainda utilizar um código maior que possa ser decomposto em unidades independentes de código [JUEM,1987]. Deste modo, é importante ter uma certa atenção em relação a outras propostas para o *hashing**,* sendo que muitas delas também possuem seus prontos fracos [MITC, 1992].

## ***Secure Hash Algorithm (SHA)***

Atualmente, a função *hash* criptográfica mais amplamente utilizada tem sido o* **Secure Hash Algorithm* (SHA). Este algoritmo foi desenvolvido pelo NIST *(**National Institute of Standards and Technology*) e publicado como um padrão de processamento de informações federais (FIPS 180) em 1993. Este algoritmo foi introduzido visando substituir as funções *hashes* anteriores que apresentaram vulnerabilidades de criptoanálise críticas. Destaca-se que em 2005 era um dos últimos algoritmos padronizado, restante, que ainda não havia sido encontrado vulnerabilidades. Então, assim que foram encontrados alguns pontos fracos no SHA, uma outra versão foi lançada como padrão no FIPS 180-1 em 1995. Esta nova versão do SHA passou a ser chamada de SHA1, diante disto, a versão anterior ficou conhecida como SHA-0. Ressalta-se que o documento de padrões oficial é intitulado como *Secure Hash Standard*, ainda que a função hash do SHA seja baseada na função hash do MD4, o que confere uma modelagem do projeto bem próxima.

A função *hash* que implementa o SHA-1 produz uma saída de hash de 160 bits. Posteriormente, o NIST concebeu outras três novas versões do SHA (estabelecidas no FIPS 180-2), com os tamanhos de valor de *hash* de 256, 384 e 512 bits, respectivamente denominadas como SHA-256, SHA-384 e SHA-512. O conjunto desses três algoritmos de *hash* são também conhecidos como SHA-2. As novas versões utilizam a mesma estrutura básica do SHA-1, adotam os mesmos tipos de aritmética modular e realizam as mesmas operações lógicas binárias. Algum tempo depois, uma nova versão de 224 bits foi incluída no documento do FIP PUB 180-3. Ainda, é importante enfatizar que tanto o SHA-1 como o SHA-2 são especificados na RFC 6234, apesar de compor o mesmo conteúdo definido no material do FIPS 180-3, adicionalmente é incluído implementação do código C.

Na medida que um algoritmo de *hash* apresenta algum ponto fraco, deve ser imediatamente descontinuado. Neste sentido, novos algoritmos mais robustos são utilizados. Nesta linha de raciocínio, em 2005, o NIST informou a intenção de descontinuar a versão do SHA-1 e migrar para o SHA-2, fornecendo um prazo para transição ocorrer até 2010. Porém, por curiosidade uma equipe de pesquisa na área de segurança descreveu um ataque onde duas mensagens distintas poderiam gerar o mesmo valor *hash* no SHA-1 utilizando apenas 269 operações. Um número relativamente menor de operações que havia sido determinado que seria necessário para encontrar uma colisão em um *hash* SHA-1 [Wang,2005]. Esse resultado foi um dos grandes motivadores para acelerar o processo da transição do SHA-1 para o SHA-2. Na tabela abaixo é apresentado uma comparação entre os parâmetros do algoritmo SHA, exposto no FIPS 180-4, observe que o algoritmo SHA-512 possui outras duas versões que modificam o tamanho do resumo da mensagem, o SHA-512/224 e SHA-512/256.

![[New database.base]]

Finalmente, destacamos que atualmente o FIPS 180-4 corresponde a última versão do documento disponibilizado pelo NIST, ou seja, a versão que está vigente.

## **Funções Hash Criptográficas No Banco de Tóquio**

Analisando o estudo de caso do banco do Tóquio que foi apresentado na Unidade 1 – Introdução a Segurança da Informação, podemos trazer o incidente de segurança para ser avaliado sob a perspectiva do que estudamos aqui. Temos por objetivo que você reflita em alguns aspectos relacionados ao uso de funções *hash* criptográficas no banco. Primeiramente, o banco utiliza uma variedade de sistemas internos, em alguns desses sistemas a autenticação era realizado utilizando arquivos de senha de mão única. Devido serem sistemas legados existia uma certa resistência para realizar modificações nos sistemas. Posterior ao incidente de segurança, foi realizado um inventário minucioso em cada um dos sistemas e foi identificado que grande parte desses sistemas ainda utilizavam o algoritmo de *hash* MD5.

Nesta unidade, apresentamos algumas fraquezas das funções *hash* criptográficas, mas em destaque o algoritmo de hash MD5 que foi utilizado inclusive para falsificar assinaturas digitais da Microsoft. Ainda, está sendo investigado se o *malware* que foi disseminado no banco não acabou explorando este tipo de vulnerabilidade. Apesar não ter sido confirmado que a fraqueza do MD5 contribuiu com *malware* para realizar o ataque nos sistemas do banco, já estão sendo tomadas medidas para adotar um algoritmo que implementa funções *hash* criptográficas mais seguras. Estão sendo realizados testes de desempenho nos algoritmos *hash* mais atuais, está sendo estudado para que seja adicionado a versão do SHA-512.

As funções *hash* criptográficas são também utilizadas em outras aplicações no banco de Tóquio. A comunicação oficial entre os colaboradores do banco é realizada por meio de um sistema interno do banco e esta comunicação trafega em aberto. Deste modo, qualquer indivíduo mal-intencionado que capture os pacotes que trafegam na rede poderá ter acesso a informações sigilosas. Neste sentido, tais sistemas estão sendo modificados para implementar serviços de autenticação de mensagens. Cada colaborador será responsável em manter sua chave privada para realizar as trocas de mensagens no sistema, a criptografia de chave pública e privada serão alvo da nossa próxima unidade. Porém, para garantir a integridade da mensagem esta mensagem será cifrada utilizando uma função *hash**.* Adicionalmente, está sendo verificado a possibilidade de adicionar a assinatura digital em alguns dos processos do banco.

As novas aplicações que utilizam as funções *hash* criptográficas propõem melhorias nos processos do banco, porém, devemos considerar a existência de vulnerabilidades em certos algoritmos de *hash**.* No desenvolvimento deste processo, precisamos ficar atentos para que sejam utilizados algoritmos de *hash* adequados ao cenário de segurança do banco.  Neste momento, o banco de Tóquio precisa implementar as novas aplicações, nossa missão é garantir que as propriedades de segurança da informação do banco sejam preservadas. Assim, devemos selecionar as funções *hash* criptográficas apropriadas, a fim de assegurar a propriedade de mão única e livre de colisão. Nas próximas unidades vamos conhecer outros mecanismos para garantir a segurança dos ativos de informação do banco, conhecer e saber como aplicá-los.  Mas não se preocupe, vamos nortear você nesta caminhada, ao longo das próximas unidades vamos te preparar para lidar com este e outros problemas de segurança da informação no âmbito real.

## **Explorando as funções *****hash***** criptográficas**

Este vídeo fornecerá uma visão mais ampla das funções *hash* criptográficas, vamos apresentar os elementos fundamentais associados a este algoritmo, quais as vantagens e desvantagens de utilizar esta abordagem, dicas e boas práticas para implementação deste mecanismo de segurança.

## **EXERCÍCIO**

**Exercícios de Fixação**

14. Quais os dois princípios básicos de uma função hash criptográfica?
15. O que é o checksum e para que é utilizado?
16. Explique o conceito da propriedade mão única estabelecidas em funções hash.
17. Cite algumas aplicações de uso das funções hash criptográficas, descreva como são utilizadas.
18. O que é uma colisão em função hash criptográfica?
19. Cite os requisitos que devem ser observados para implementação de função hash criptográfica.
20. Descreva qual a principal diferença entre resistência à colisão fraca e a resistência à colisão forte.
21. Porque o algoritmo MD5 é considerado uma função hash criptográfica vulnerável?
22. Porque o algoritmo MD6 não foi adotado como padrão SHA-3?
23. Explique como o paradoxo do aniversário pode ser utilizado para efetuar ataques em funções hash criptográficas.
24. Qual a diferença entre o algoritmo SHA-0 e SHA-1?
25. Quais os algoritmos que compõe o SHA-2?

## **Conclusão**

Esta unidade abordou as funções hash criptográficas. Descobrimos que a função hash mapeia uma mensagem de qualquer tamanho variável em um bloco de dados de tamanho fixo. Conforme discutido, qualquer função hash criptográfica é fundamentada sobre dois princípios básicos, a propriedade de mão única e a propriedade livre de colisão. Verificamos que a propriedade de mão única garante que a partir do código hash não será possível retornar ao seu valor inicial da mensagem. Por sua vez, a propriedade livre de colisão garante que duas mensagens distintas não serão mapeadas com o mesmo valor de hash.

Exploramos o uso das funções hash criptográficas, apresentamos algumas das principais aplicações. Entre as aplicações, demonstramos como as funções hash criptográfica podem ser utilizadas para implementar serviços de autenticação de mensagens. Ainda, exploramos as funções hash criptográficas para fornecer o processo de assinatura digital. Adicionalmente, apresentamos algumas outras aplicações das funções hash criptográficas, tais como gerador de números pseudoaleatórios, detecção de intrusão, detecção de vírus, alguns protocolos da internet entre outros.

Enfatizamos os requisitos de segurança das funções hash criptográficas, verificamos que existem basicamente sete requisitos que devem ser avaliados na implementação dos algoritmos de hash: tamanho de entrada variável; tamanho de saída fixo; propriedade de mão única; resistência à colisão fraca; resistência à colisão forte e pseudoaleatoridade. Estudamos cada um desses requisitos.

Por conseguinte, nos aprofundamos nos principais algoritmos que implementam as funções de hash. Primeiramente, apresentamos o algoritmo MD5, um dos algoritmos de hash mais utilizados. Abordamos as fraquezas do MD5 e como os adversários exploram tais vulnerabilidades. Conforme discutido, mesmo após a exposição das fraquezas e da depreciação dos especialistas de área de segurança o MD5 ainda continua a ser utilizado. Adicionalmente, apresentamos as funções hash baseadas em Cipher Block Chaining, mostramos quais os tipos de ataques utilizados pelo adversário, bem como algumas estratégias utilizadas para evitá-los. Na sequência, conhecemos a família do algoritmo SHA, exploramos sua evolução do primeiro algoritmo até os algoritmos utilizados atualmente.

## **Criptografia simétrica e assimétrica**

*Nesta Unidade, iremos estudar os mecanismos de criptografia simétricos e assimétricos. Conheceremos os elementos fundamentais da criptografia simétrica. Ainda, iremos nos aprofundar nos principais algoritmos de criptografia simétrica, tais como o algoritmo DES, Triplo DES e AES. Adicionalmente, demonstraremos o processo de distribuição chave simétricas de forma segura. Na sequência, vamos apresentar os princípios de cifração assimétrica, os elementos envolvidos na criptografia de chave pública. Também, iremos apresentar os principais algoritmos de cifração de chave pública, o algoritmo RSA, Diffie-Hellman, DSS e as Curvas elípticas. Além de ressaltar as vantagens e desvantagens de cada tipo de criptografia, vamos mostrar as principais aplicações que utilizam estes dois tipos de criptografia, tais como assinatura digital, autenticação de mensagens, certificados de chave pública, envelopes digitais, entre outras. Estaremos também conhecendo o processo de distribuição de chave pública de forma segura, utilizando diretórios de chave pública, anúncio público, autoridades e certificados de chave pública. Por fim, demonstraremos como associar diferentes algoritmos de criptografia para obter um mecanismo mais seguro.*

## **Princípios de Cifração Simétrica**

A cifração simétrica, também conhecida como criptografia de chave secreta, era o único tipo de método de cifração utilizado antes da inserção da criptografia de chave pública no final da década de 1970. Esse método de criptografia ainda continua sendo amplamente utilizado.

Para compreender a criptografia simétrica primeiramente vamos definir alguns termos fundamentais. A mensagem original é conhecida como **texto claro**, ao passo que uma mensagem codificada é denominada como **texto cifrado**. Neste sentido, a ação de modificar um texto claro em um texto cifrado é chamado de **cifração**; por sua vez o processo de restaurar o texto claro a partir do texto cifrado é conhecido como **decifração**.

O estudo dos diversos métodos e procedimentos utilizados para cifragem/decifragem constituem a área de segurança conhecida como **criptografia**. Cada um desses métodos ou procedimentos é denominado como **sistema criptográfico** ou mais comumente chamado de **cifra**. Os métodos utilizados para decifrar um texto cifrado sem haver qualquer conhecimento dos detalhes do algoritmo de cifração estabelecem a área de **criptoanálise**. Por fim, a associação entre as áreas de criptografia e criptoanálise são denominadas como criptologia.

Um método de criptografia simétrica possui cinco elementos fundamentais:

- **Texto às claras**: é a mensagem original que é atribuída como entrada para o algoritmo de criptografia.
- **Algoritmo de cifração**: é um algoritmo matemático que executa várias substituições e transformações no texto às claras para gerar o texto cifrado.
- **Chave secreta**: a chave secreta é um segundo elemento de entrada para o algoritmo de cifração. Esta chave é um valor individual que não depende nem do texto claro e nem do algoritmo de cifragem. Para cada chave secreta o algoritmo de cifração produzirá uma saída diferente (texto cifrado). As substituições e transformações que serão realizadas pelo algoritmo dependem exclusivamente da chave utilizada.
- **Texto cifrado**: É a mensagem codificada produzida como saída. Esta mensagem é embaralhada, ela depende do texto às claras e da chave secreta. Destaca-se que uma mensagem cifrada com duas chaves diferentes irá gerar dois textos cifrados distintos.
- **Algoritmo de decifração**: é um algoritmo matemático que executa o algoritmo de cifragem de maneira inversa, ou seja, ele recebe como entrada o texto cifrado e a chave secreta e produz o texto original.

A Figura abaixo dispõe do modelo de criptografia simétrica.

![[UE6_img1.png]]

Fonte: Autor

Existem dois requisitos que devem ser atendidos para utilização da cifração simétrica de forma segura:

1. Adotar um algoritmo de cifração forte. O algoritmo deve ser robusto o suficiente para impedir que o adversário que conheça o algoritmo e tenha acesso a um ou mais textos cifrados, não seja capaz de decifrar o texto cifrado ou adivinhar a chave secreta.

1. O emissor e receptor de uma mensagem deve obter cópias da chave secreta de maneira segura e preservá-las em segurança. Pois, qualquer indivíduo que conseguir acesso à chave e descobrir o algoritmo utilizado, terá acesso a toda comunicação realizada com essa chave.

Em geral, existem basicamente duas abordagens que os adversários utilizam para atacar um esquema de criptografia simétrica. O primeiro é o ataque de criptoanálise, neste ataque o adversário explora a natureza do algoritmo, além das características gerais do texto às claras e amostras em pares - amostras do texto às claras e o mesmo texto cifrado. Este ataque explora as características do algoritmo para tentar decifrar um texto às claras específico ou deduzir qual a chave secreta que foi utilizada. Caso o ataque seja bem-sucedido na dedução da chave, isto poderá gerar um efeito desastroso em cascata, pois todas as mensagens que foram cifradas com esta chave serão comprometidas, incluindo as mensagens transmitidas anteriormente e as mensagens a serem enviadas.

A segunda técnica, é a utilização de um ataque de força bruta. Tratando-se do cenário de criptografia simétrica este ataque consiste em utilizar todas as chaves secretas possíveis em uma amostra de texto cifrado até conseguir ter acesso ao texto às claras. Uma estimativa denota que em média é necessário testar metade de todas as chaves secretas possíveis para obter sucesso neste ataque. Conforme exposto por Stallings é necessário 1ms para executar uma única tentativa de decifração [Stallings,2014], considerando um computador atual com uma configuração razoável. Abaixo uma tabela contendo o estudo realizado pelo autor, na tabela é apresentado o tempo médio para decifrar uma mensagem considerando tamanho de chaves diferentes.

| Tamanho da chave (bits) | Número de chaves possíveis | Tempo requerido <br>em 1 decifração/𝝁s | Tempo requerido em 10 decifrações/ 𝝁s |
| --- | --- | --- | --- |
| 32 | " id="MathJax-Element-4-Frame" tabindex="0">  232 = 4,3∗109 | " id="MathJax-Element-5-Frame" tabindex="0">  231    s * 35,8 minutos | 2,15 milissegundos |
| 56 | " id="MathJax-Element-6-Frame" tabindex="0">  256 = 7,2∗1016 | " id="MathJax-Element-7-Frame" tabindex="0"> Math input errorMath input error55  s = 1142 anos | 10,01 horas |
| 128 | " id="MathJax-Element-3-Frame" tabindex="0">  2128 = 3,4∗1038 | " id="MathJax-Element-8-Frame" tabindex="0">  2127 m  s = 5,4 *  " id="MathJax-Element-12-Frame" tabindex="0">  224   anos | 5,4 * 1" id="MathJax-Element-11-Frame" tabindex="0">  018  anos |
| 168 | " id="MathJax-Element-9-Frame" tabindex="0">  2168 = 3,7∗1050 | " id="MathJax-Element-10-Frame" tabindex="0">  2127   s = 5,9 * " id="MathJax-Element-13-Frame" tabindex="0">  1036  anos | 5,9 * 1" id="MathJax-Element-14-Frame" tabindex="0">  030  anos |
| 26 caracteres (permutação) | " id="MathJax-Element-15-Frame" tabindex="0">  26! = 4∗1026 | " id="MathJax-Element-17-Frame" tabindex="0">  2 ∗ 1026   s = 6,4 * " id="MathJax-Element-16-Frame" tabindex="0">  1012  anos | 6,4 * " id="MathJax-Element-18-Frame" tabindex="0">  106  anos |

Ressalta-se que com a utilização de processamento paralelo é possível reduzir consideravelmente o tempo necessário para "quebrar uma chave". Observe que na última coluna da tabela está sendo apresentado o de um sistema que é capaz de processar um milhão de chaves por microssegundo. Consequentemente, uma chave de 56 bits não deve ser mais considerada segura.

## **Algoritmos de Criptografia Simétrica**

Os algoritmos de criptografia simétrica mais utilizados são as cifras de bloco. A cifra de bloco processa o texto às claras fornecido como entrada utilizando blocos de tamanho fixo, como resultado gera um bloco de texto cifrado de tamanho igual para cada um dos blocos de texto às claras. Este algoritmo processa as sequências de caracteres mais longas de texto às claras como sendo uma série de blocos de tamanho fixo. Entre os algoritmos simétricos mais importantes destacam-se o *Data Encryption Standard* (DES), o *Triple DES* (DES triplo) e o *Advanced Encryption Standard* (AES).

### **Data Encryption Standard**

O algoritmo *Data Encryption Standard* (DES) é um dos principais algoritmos de chave simétrica, foi desenvolvido pela IBM em 1971, tornou-se um padrão adotado pelo NIST1 (*National Institute of Standards and Technology*) em 1977, então publicado na FIPS PUB 46 (*Federal Information Processing Standard*).

**CURIOSIDADE**NIST (*National Institute of Standards and Technology*) em 1977 ainda era conhecido como *National Bureau of Standards* (Escritório Nacional de Padrões)

Este algoritmo também ficou conhecido como algoritmo de cifração de dados, termo advindo do inglês DEA (*Data Encryption Algorithm*). O algoritmo recebe como entrada um bloco de texto às claras de 64 bits e uma chave secreta composta por 56 bits, como resultado gera um bloco cifrado de 64 bits.

A utilização do algoritmo DES institui duas grandes preocupações, relacionadas a implementação do algoritmo em si e outra relativo à utilização de uma chave de 56 bits. A primeira preocupação refere-se a explorar as características do algoritmo utilizando técnicas de criptoanálise. Destaca-se que o algoritmo DES foi intensamente estudado, ao longo dos anos foram realizadas numerosas tentativas de encontrar fraquezas neste algoritmo. Apesar de inúmeras abordagens, não foi reportado nenhuma fraqueza crítica.

Porém, em julho de 1998 o algoritmo DES mostrou ser inseguro, quando a *Electronic Frontier Foundation* (EFF) anunciou que havia decifrado uma cifração DES em uma máquina especializada, denominada DES *cracker*. Dado a evolução do *hardware*, os computadores desempenham um número maior de atividades em um menor tempo, os microprocessadores estão cada vez mais rápidos, o que torna o algoritmo DES praticamente inadequado.

**CURIOSIDADE**DES cracker – máquina denominada como decifradora DES, construída por250 mil dólares na época.

Destaca-se que um ataque de força bruta destinado a busca de chave envolve mais do que somente executar todas as chaves possíveis. O analista deve ser capaz de reconhecer o texto às claras após a decriptação, ou seja, seu conteúdo deve ser compreensível. Quando a mensagem for composta por apenas texto às claras em um determinado idioma, o resultado será imediato, sendo apenas necessário reconhecer o idioma de forma automatizada. Porém, se o texto for comprimido antes de realizar a cifração, o processo de reconhecimento possui um grau maior de complexidade. Ainda, tratando-se de uma mensagem contendo um tipo de dado mais específico, como o código de alguma linguagem de programação ou arquivo numérico, e se este arquivo for comprimido, a técnica torna-se muito mais difícil de ser automatizada.

Deste modo, será necessária uma abordagem complementar ao ataque de força bruta, sendo preciso um certo grau de conhecimento sobre o texto às claras e uma forma de distinguir automaticamente se a mensagem cifrada retornou ao formato original. A estratégia adotada pela EFF trata exatamente este contexto, e ainda apresenta várias técnicas automatizadas que poderiam ser utilizadas em diferentes cenários.

Uma contramedida para mitigar o ataque de força bruta realizado ao algoritmo de cifração, seria adotar chaves mais longas. Considerando a tecnologia atual podemos realizar uma estimativa, caso a decifradora conseguisse executar um milhão de decifrações por milissegundos, então um código DES poderia ser "quebrado" em torno de 10 horas. Tendo em mente o aumento da velocidade de aproximadamente sete vezes em relação a tecnologia utilizada na decifradora da EFF. Considerando este cenário, para quebrar uma chave de 128 bits seria necessário mais de 1018 anos. Os resultados demostram que atualmente utilizar um ataque de força bruta sobre um algoritmo que utiliza uma chave de 128 bits é impraticável.

### **Triple Data Encryption Standard**

A algoritmo DES foi utilizado como base para estruturar o algoritmo triplo DES (3DES), que na verdade não é nada mais que a implementação do algoritmo DES tradicional repetido três vezes, utilizando duas ou ainda três distintas, gerando um tamanho de chave de 112 ou 168 *bits* respectivamente. O triplo DES foi padronizado em 1985 como padrão ANSI X9.17, sendo então bastante utilizado em aplicações financeiras. Então, em 1999 foi adicionado ao FIPS PUB 46-3 como sendo uma parte do DES.

O triplo DES traz duas características bastante relevantes que asseguram seu uso para os próximos anos. A primeira característica está relacionada ao comprimento da chave, com uma chave de 168 *bits* o triplo DES consegue superar as vulnerabilidades impostas pelo ataque de força bruta no DES. A segunda característica é que o algoritmo de cifragem incluído dentro do triplo DES é o mesmo que inserido no DES.

Esse algoritmo mais do que qualquer outro algoritmo de cifração foi submetido a ataques de criptoanálise, porém nenhum ataque efetivo foi encontrado, a não ser o ataque de força bruta que levaria milhões de anos para ser "quebrado". Existe um alto nível de confiança da resistência do algoritmo triplo DES em relação aos ataques de criptoanálise. Na seleção de um algoritmo de cifragem, se a segurança fosse o único aspecto a ser avaliado, com certeza o triplo DES seria uma escolha conveniente.

Contudo o triplo DES possui desvantagens, a principal é que este algoritmo acaba sendo extremamente lento em software. O algoritmo DES foi projetado em hardware na década de 1970, porém não apresentava um código em software eficiente. Por sua vez, o triplo DES necessita de três vezes mais processamento, consequentemente muito mais lento. Outra desvantagem, apresentada tanto no DES como no triplo DES, ambos utilizam um tamanho de bloco de 64 *bits*. Levando em consideração tanto a eficiência como a segurança, trabalhar com tamanho de blocos maiores é apreciável.

### **Advanced Encryption Standard**

Observando as desvantagens anteriormente apresentadas, o triplo DES não é um forte candidato para ser utilizado a longo prazo. Neste sentido, em 1997 o NIST publicou uma chamada para criação de novo algoritmo de cifração, o novo algoritmo deveria ter um nível de segurança equivalente ou superior ao 3DES e uma eficiência que fosse expressivamente melhor. Ainda, o NIST especificou que o novo algoritmo deveria ter uma cifra de bloco com comprimento de blocos de 128 *bits*, e forneceria suporte para chaves de 128, 192 e 256 *bits*. Conforme estabelecido pelo NIST, os critérios de avaliação contemplavam a segurança, eficiência computacional do algoritmo, consumo de memória, flexibilidade, algoritmo ajustável (*hardware e software*).

Na primeira etapa da avaliação foram selecionados 15 algoritmos de cifragem. Em uma segunda rodada, dos 15 algoritmos foram selecionados apenas 5 algoritmos. Por fim, em novembro de 2001 o NIST finalizou o processo de avaliação, selecionando o algoritmo de Rijndael como padrão final. Este algoritmo foi denominado Advanced Encryption Standard (AES). O AES foi então publicado no FIPS PUB 197, atualmente este algoritmo está amplamente presente em diversos produtos comerciais.

## **Distribuição de Chave Simétrica**

Conforme mencionado, os algoritmos de criptografia simétricos utilizam a mesma chave tanto para cifrar como para decifrar. A chave secreta é compartilhada entre duas ou mais partes. Destaca-se que a chave secreta deve ser a mesma, tanto para a cifragem quanto para decifragem.

Considerando que a chave é de uso compartilhado e deve ser mantida em segredo pelas duas partes envolvidas na comunicação, para utilizar a criptografia simétrica, é essencial existir um canal para permitir a troca de forma segura das chaves entre as partes envolvidas na comunicação. Ressalta-se que na criptografia simétrica a necessidade de compartilhar a chave secreta com cada parceiro é o que impõem a sua maior fragilidade. Tendo em vista, que a transmissão das chaves entre os envolvidos pode não ser realizada de forma segura, e esta chave pode acabar de posse de um indivíduo mal-intencionado.

A figura a seguir mostra um outro problema da criptografia simétrica, a distribuição das chaves. Onde, cada usuário terá de armazenar e gerenciar o número de chaves de acordo com a quantidade de pessoas com as quais ele se comunica. Por exemplo, conforme disposto na figura, Alice tem duas chaves compartilhadas, uma para se comunicar com Bob e outra para se comunicar com Ted. Se Alice quiser trocar mensagens com John de forma confidencial, ela precisará adquirir e gerenciar mais uma chave.

![[UE6_img2.png]]

Fonte: Autor

Neste sentido, dois grandes problemas necessitam ser avaliados tratando-se de criptografia simétrica:

- Transmitir a chave secreta de uma forma segura e confiável entre as duas partes envolvidas na comunicação.
- Administrar o problema da distribuição de um número considerável de chaves (armazenar uma chave para cada comunicação distinta).

## **Centro de Distribuição de Chaves (KDC)**

De acordo com o que estudamos, uma das grandes limitações da criptografia simétrica é justamente a distribuição das chaves secretas. Como podemos distribuir a chave secreta de maneira segura entre a duas partes. Para tal, podemos utilizar um intermediário de confiança denominado como centro de distribuição de chaves, ou do termo inglês KDC (*Key Distribution Center*). O KDC é considerado uma entidade de confiança na rede com quem o usuário estabelece uma chave secreta compartilhada, a partir desta entidade os usuários podem obter as chaves compartilhadas necessárias para uma comunicação segura com os demais usuários da rede, evitando assim algumas estratégias do adversário para capturar a chave secreta.

A figura a seguir mostra duas partes, Alice e Bob, tentando estabelecer uma comunicação segura utilizando o KDC. Para isto, a seguinte sequência de passos é realizada:

1. Alice solicita ao KDC que deseja se comunicar com Bob.

1. O KDC envia uma chave a Alice.

1. O KDC envia a mesma chave a Bob.

26. A chave que Alice e Bob receberam permitem estabelecer uma comunicação de forma segura, os dados são cifrados com a chave que foi enviada pelo KDC.

![[UE6_img3.png]]

Fonte: Autor

Visando garantir que realmente a chave foi concedida pelo KDC, ele fornece uma chave secreta simétrica diferente para cada um dos seus usuários cadastrados. Sendo esta chave criado no servidor no instante que o usuário se cadastra no KDC. Deste modo, o KDC conhece a chave que foi distribuída para cada usuário, o que permite que o usuário e o KDC se comuniquem com segurança.

Na figura abaixo demonstramos o processo para estabelecer a comunicação entre duas partes.

![[UE6_img4.png]]

Fonte: Autor

Considerando que Alice e Bob são usuários do KDC, eles conhecem somente a chave secreta com o KDC. Alice deseja iniciar a comunicação.

1. Então Alice, utiliza sua chave secreta para se comunicar com o KDC, diz que deseja se comunicar com Bob.

1. O KDC recebe a mensagem de Alice, neste momento o KDC tem certeza da origem da mensagem, sendo que apenas Alice possui esta chave secreta que eles compartilham.

1. O KDC então decifra a mensagem enviada por Alice, verifica a intenção de Alice de se comunicar com Bob. Então, na sequência o KDC cria uma chave para que Alice e Bob possam estabelecer esta comunicação. Esta chave é denominada como "chave de sessão". A chave de sessão será utilizada para estabelecer a comunicação uma única vez, ou seja, uma única sessão de comunicação. Após o KDC criar a chave ele necessita enviar esta chave para Alice e Bob.

1. Para enviar a chave de sessão para Alice, o KDC cifra a chave de sessão utilizando a chave secreta que é compartilhada exclusivamente com Alice.

1. Para enviar a chave de sessão para Bob, o KDC cifra a chave de sessão utilizando a chave secreta que é compartilhada exclusivamente com Bob.

1. Após Alice e Bob receberem suas mensagens, eles decifram a mensagem utilizando a chave secreta que cada um deles compartilha com o KDC. Ao decifrar a mensagem Alice e Bob terão acesso a chave de sessão para se comunicar. Agora toda comunicação realizada entre Alice e Bob deve ser cifrada utilizando a chave de sessão.

Utilizando a criptografia simétrica, distribuindo a chave secreta por meio do KDC, conseguimos garantir as seguintes propriedades de segurança:

- **Confidencialidade**: somente Alice e Bob conseguem decifrar as mensagens cifradas com a chave de sessão.
- **Autenticidade**: quando Alice recebe uma mensagem cifrada com a chave de sessão, ela sabe exatamente com quem a chave é compartilhada, neste caso com Bob, já que apenas Bob conhece essa chave. Da maneira similar, quando Bob recebe uma mensagem cifrada com chave de sessão que compartilha com Alice, ele sabe exatamente que a mensagem foi enviada por Alice.
- **Não Repúdio**: sendo que a chave de sessão é apenas compartilhada entre Alice e Bob eles não poderão negar a autoria da mensagem, ou seja, negar que foi um deles que enviou uma mensagem cifrada com a chave de sessão que apenas ambos compartilham.

## **Hierarquia de Chaves**

O uso de um KDC depende de uma estrutura de hierarquia de chaves. A hierarquia de chaves permite conceder níveis diferentes de criptografia para as chaves. O KDC necessita de no mínimo dois níveis de chaves. Em geral, a comunicação realizada entre os sistemas finais é cifrada utilizando uma chave temporária, a chave de sessão. Geralmente, a chave de sessão é utilizada dentro da duração de tempo fornecida por uma conexão lógica, tal como uma conexão de transporte. Após o tempo de duração a chave de sessão perde sua validade e então é descartada. A chave de sessão é obtida a partir do KDC sob a mesma infraestrutura de rede utilizada para comunicação do usuário final. A figura abaixo mostra a representação adaptada da hierarquia de chaves proposta por Stallings [Stallings,2008].

![[UE6_img5.png]]

Fonte: Adaptada de Stallings

Na sequência, a chave deve ser transmitida ao usuário final de maneira cifrada para que uma terceira parte não tenha acesso a chave de sessão. Para cifrar a chave de sessão deve ser utilizado uma chave mestra, a chave criada pelo KDC assim que o usuário é cadastrado.

Não é necessário centralizar a distribuição de chaves em um único KDC. Em redes maiores pode não ser viável fazer isso. Alternativamente, é possível estabelecer uma hierarquia de KDC. Por exemplo, é possível distribuir os KDC's locais, cada qual fica responsável por um determinado domínio ou subdomínio.

Assim, o KDC local fica responsável por distribuir as chaves dentro do domínio local para entidades que foram ali cadastradas. Contudo, caso duas entidades associados a domínios diferentes desejem se comunicar, então os KDC´s locais podem se comunicar com um KDC global a fim provisionar uma chave de sessão para que as partes consigam se comunicar de forma segura. Neste sentido, qualquer um dos três KDC´s pode realmente gerir a chave. O conceito hierárquico pode ser estendido a três ou mais camadas, dependendo do tamanho da rede e da quantidade de usuários.

O esquema hierárquico permite reduzir o efeito associado à distribuição da chave mestra, tendo em vista a grande quantidade das chaves mestras que serão compartilhadas por um KDC local com suas respectivas entidades. Adicionalmente, este esquema permite restringir a abrangência do dano causado por KDC defeituoso tendo impacto apenas na sua área local.

## **Princípios de Cifração Assimétrica**

O conceito de cifração assimétrica, amplamente conhecido como criptografia de chave pública evoluiu da tentativa de resolver dois problemas complexos associados a cifração simétrica. O primeiro, já mencionado, é o problema relacionado a distribuição de chaves. Conforme discutido, a distribuição de chaves de uma abordagem utilizando cifração simétrica necessita que as duas partes comunicantes compartilhem uma chave que lhes foi atribuída anteriormente. Consequentemente, sendo necessário o uso de KDC. Um outro requisito foi abordado por Whitfield Diffie e Martin Hellman, criadores do algoritmo de cifração de chave pública. Consideraram um aspecto que anulava a própria natureza da criptografia: a capacidade de conservar o segredo absoluto sobre a própria comunicação. Conforme exposto por Diffie “*afinal, qual seria a vantagem de desenvolver criptossistemas impenetráveis, se seus usuários fossem forçados a compartilhar suas chaves com um KDC que poderia ser comprometido por roubo ou suborno?*” [Diffie,1988].

O segundo problema refletido por Diffie foi a das assinaturas digitais. Prevendo o uso da criptografia não apenas para fins militares, vislumbrando atender demandas comerciais e particulares, constatou que as mensagens e documentos digitais precisariam de algo que fosse equivalente às assinaturas manuscritas nos documentos em papel. Idealizou a criação de um método que fosse capaz de satisfazer todas as partes, e afirmar que uma mensagem no meio digital tenha sido enviada por determinado indivíduo.

Investindo sobre a resolução destes dois problemas, Diffie e Hellman projetaram um algoritmo revolucionário no campo da criptografia, propuseram um método de cifragem para trocas de chaves de maneira segura realizado em um canal público. Este algoritmo foi publicado em 1976, denominado como método de troca de chaves de Diffie-Hellman. Considerado um dos primeiros exemplos práticos de métodos de troca de chaves implementado dentro da área de criptografia, propulsor da criptografia de chave pública.

### **Fundamentos de Cifração Assimétrica**

Os algoritmos de criptografia assimétricos trabalham com duas chaves, uma para cifragem dos dados e uma segunda chave para decifragem dos dados. Tais algoritmos possuem uma característica significativa, é computacionalmente inviável especificar a chave de decifragem utilizando apenas o conhecimento do algoritmo e chave de cifragem. Outra característica adicional, específica do algoritmo RSA é a de que qualquer umas das duas chaves podem ser utilizadas para cifragem, como resultado a outra chave deve ser utilizada para decifragem.

A abordagem de criptografia de chave pública dispõe de cinco elementos:

- **Texto às claras**: corresponde à mensagem ou aos dados em formato legível que são disponibilizados como entrada para o algoritmo.
- **Algoritmo de cifra****çã**o: é um algoritmo matemático que realiza várias operações e transformações no texto às claras.
- **Chaves pública e privada**: corresponde a um par de chaves secretas, selecionadas de tal modo que se uma das chaves for utilizada para cifrar a outra é utilizada para decifrar. As transformações específicas realizadas pelo algoritmo, variam de acordo com a chave pública ou chave privada que foi concedida como entrada para o algoritmo.
- **Texto cifrado**: é a mensagem codificada produzida como saída. Esta mensagem é embaralhada, ela depende do texto às claras e da chave secreta que foi utilizada. Destaca-se que duas chaves diferentes produzirão como resultado dois textos cifrados distintos.
- **Algoritmo de decifração**: é um algoritmo matemático que recebe como entrada o texto cifrado e a chave correspondente e produz como resultado a mensagem original, ou seja, o texto às claras.

Na figura abaixo é demostrado um esquema típico de criptografia de chave pública:

![[UE6_img6.png]]

Fonte: Autor

As etapas fundamentais são demostradas as seguir:

27. Cada usuário deve conceber um par de chaves que será utilizado para o processo de cifragem e decifragem das mensagens.
28. O usuário deve alocar uma das duas chaves em um registrador público ou utilizar outro meio para disponibilizar esta chave, esta chave é denominada como chave pública. A outra chave deve ser mantida em segurança, esta chave é denominada como chave privada. Adicionalmente, cada usuário mantém um conjunto de chaves públicas de outros usuários.
29. Caso Alice deseje enviar uma mensagem secreta para Bob, ela cifra a mensagem utilizando a chave pública de Bob.
30. Quando Bob receber a mensagem, ele utiliza a chave privada para decifrar a mensagem. Destaca-se que nenhum outro indivíduo conseguirá decifrar a mensagem, pois somente Bob conhece a chave privada.

Utilizando esta técnica, todos os envolvidos podem ter acesso às chaves públicas. Ressalta-se que as chaves privadas são geradas localmente por cada uma das partes envolvidas, e essas chaves não podem ser distribuídas. A chave privada deve ser protegida e secreta, isto vai garantir que a comunicação realizada entre as partes esteja protegida. Outro fator interessante é a possibilidade de renovar as chaves sempre que necessário, a qualquer momento um sistema poderá modificar a chave privada e redistribuir uma nova chave pública.

## **Algoritmos de Chave Pública**

Nesta seção vamos explorar alguns dos principais algoritmos assimétricos utilizados atualmente, o algoritmo RSA, Diffie-Hellman, DSS e as curva elípticas.

### **Algoritmo RSA**

O RSA foi um dos primeiros algoritmos de cifração assimétrica, desenvolvido em 1977 por Ron Rivest, Adi Shamir e Len Adleman pesquisadores do MIT (Instituto de Tecnologia de Massachusetts), então publicado em 1978 [Rivest et al., 1978]. O algoritmo foi denominado como RSA dado a composição da inicial do nome dos autores. Este esquema de criptografia de chave pública tem sido amplamente aceito e utilizado até os dias de hoje. O RSA é estruturado por uma cifra de bloco onde o texto às claras e o texto cifrado corresponde a um número inteiro entre 0 e* **n - 1*, definido algum valor a n.

Em 1977, em uma publicação da revista* **Scientific American*, os autores do algoritmo RSA desafiaram seus leitores a decifrar um texto cifrado que foi divulgado na coluna "Jogos matemáticos". Os autores do algoritmo proporcionaram uma recompensa de 100 dólares para quem conseguisse retornar o conteúdo da mensagem em texto às claras. Evento que os autores mensuraram que só poderia ocorrer daqui aproximadamente 40 quatrilhões de anos.

**CURIOSIDADE**Quatrilhões – número equivalente a mil bilhões, representado por 1015.

Porém, em 1994 um grupo na internet empenhou-se em decifrar a mensagem, foram utilizados mais de 1600 computadores, então com somente oito meses de trabalho foi reivindicado o prêmio [Leutwyler,1994]. Neste desafio foi utilizado um tamanho de chave de aproximadamente 428 *bits* de comprimento. Ressalta-se que este resultado não anula a utilização do algoritmo RSA, somente enfatiza a necessidade de utilizar chaves com comprimento maiores. Atualmente, as aplicações utilizam um tamanho de chave de 1024 *bits* que é considerado um tamanho adequado e uma chave robusta para maioria dos cenários.

### **Acordo de chaves de Diffie-Hellman**

O algoritmo de Diffie-Hellman foi conhecido como o primeiro algoritmo de chave pública, publicado em 1976. Este algoritmo também é conhecido como troca de chaves ou acordo de chaves de Diffie-Hellman. Existem uma quantidade considerável de produtos no âmbito comercial que utilizam as técnicas empregadas no algoritmo de troca de chaves.

O propósito do algoritmo é permitir que dois indivíduos cheguem em um consenso de como compartilhar um segredo de forma segura, permitindo que este segredo seja utilizado posteriormente como chave secreta em uma aplicação de criptografia simétrica na troca das mensagens. Este algoritmo limita-se somente à troca das chaves secretas.

### **Digital Signature Standard**

O algoritmo *Digital Signature Standard* foi proposto em 1991, publicado pelo NIST em 1994 no FIPS PUB 186, também conhecido como padrão de assinatura digital. Este algoritmo faz uso da função *hash* criptográfica SHA-1 e ainda propõe uma abordagem inovadora para assinatura digital, o algoritmo de assinatura digital conhecido como DSA (*Digital Signature Algorithm*).

Devido algumas menções públicas sobre a segurança do DSS, o algoritmo foi revisado em 1993. Posteriormente, em 1996 houve uma pequena revisão no algoritmo. O algoritmo DSS foi estruturado apenas para fornecer a função de assinatura digital, ou seja, diferente do algoritmo RSA, este algoritmo não pode ser utilizado para realizar trocas de chaves ou ainda para cifragem.

### **Criptografia de Curvas Elípticas**

Devido as propriedades robusta do algoritmo RSA ele tornou-se uma tendência de mercado, atualmente uma grande parte dos produtos e padrões que utilizam criptografia de chave pública ou ainda assinaturas digitais acabam optando por utilizar o algoritmo RSA. Observasse que isto só foi possível porque o algoritmo permite utilizar chaves com tamanho variável. Para manter a robustez do algoritmo em termos de segurança, o comprimento das chaves em *bits* vem sendo ampliado. Contudo, isto reflete em uma carga maior de processamento em relação as aplicações que utilizam o algoritmo RSA.

Este problema possui alguns desdobramentos, em destaque serviços disponibilizados na *web* que realizam um número expressivo de transações seguras por segundo, por exemplo sites de comércio eletrônico. Neste sentido, uma abordagem promissora foi desenvolvida para concorrer com o algoritmo RSA, a criptografia de curvas elípticas. Conhecida também como ECC, acrônimo do termo inglês (*Elliptic Curve Cryptography*). Existem algumas iniciativas para tornar as curvas elípticas em um padrão, incluindo o padrão de criptografia de chave pública, o *Standard for Public-Key Cryptography P1363* do IEEE (*Institute of Electrical and Electronics Engineers*).

Uma das principais vantagens da curva elíptica em relação a RSA é que ela propõe uma segurança equivalente para um comprimento de bits bem menor, característica que permite reduzir o custo computacional. Em contrapartida, apesar da teoria das curvas elípticas terem sido concebidas há algum tempo, apenas recentemente com a adoção de alguns produtos começaram a ser exploradas. Consequentemente, despertando o interesse criptoanalítico, visando encontrar suas fraquezas. Deste modo, podemos inferir que o nível de confiança das curvas elípticas ainda é inferior quando comparado com um algoritmo RSA.

## **Aplicações de Chave Pública**

Os algoritmos de chave pública são utilizados em diversas aplicações. Em geral, essas aplicações são basicamente categorizadas em duas frentes: assinatura digital; e abordagens de gerenciamento e distribuição de chaves.

Relacionado ao processo de gerenciamento e distribuição de chaves, alguns fatores fundamentais relacionados à criptografia de chave pública devem ser levados em consideração:

- Estabelecer um processo para distribuição segura das chaves públicas.
- Utilizar a criptografia de chave pública para fornecer um método para distribuição das chaves secretas.
- Utilizar a criptografia de chave pública para fornecer chaves temporárias para serem usadas na cifração de mensagens.

As aplicações de chave pública apresentadas nesta seção, fornecem uma visão geral das assinaturas digitais e alguns exemplos de aplicações do processo de gestão e distribuição de chaves.

### **Assinatura Digital**

A criptografia de chave pública pode ser utilizada como ferramenta de autenticação, observe a representação exposta na figura abaixo:

![[UE6_img7.png]]

Fonte: Autor

Supondo que Alice necessite enviar uma mensagem para Bob. Considerando que a mensagem não possui caráter confidencial, ou seja, preservar o sigilo da mensagem não é um requisito importante. Porém, Alice quer garantir que Bob tenha certeza de que a mensagem foi enviada por ela.

Visando garantir a autenticidade, Alice utiliza uma função *hash* criptográfica segura, como algoritmo SHA-512, gerando um valor *hash* para sua mensagem. Posteriormente cifra o código *hash* com sua chave privada, concebendo uma assinatura digital. Então, Alice transmite a mensagem com a assinatura digital anexada. Quando Bob recebe a mensagem encaminhada por Alice ele consegue certificar a origem da mensagem por meio da assinatura digital, para isto Bob deve realizar o seguinte processo:

1. Calcular o valor do *hash* da mensagem;

1. Decifrar a assinatura utilizando a chave pública de Alice;

1. Comparar o código *hash* obtido com o código *hash* disposto na mensagem decifrada.

Caso ambos os códigos *hash* forem idênticos, Bob consegue ter certeza de que a mensagem foi assinada com a chave privada de Alice. Sendo que ninguém mais além de Alice possui sua chave privada, ninguém mais poderia ter cifrado o texto que foi decifrado utilizando a chave pública de Alice. Ainda, destaca-se que seria impossível modificar a mensagem sem ter posse da chave privada de Alice, esta propriedade permite autenticar a mensagem, primeiro determinar sua origem, por conseguinte garantir a integridade dos dados transmitidos.

É importante destacar que assinatura digital não fornece confidencialidade. Em outras palavras, a mensagem que está sendo transmitida permite garantir que não sofreu nenhuma alteração, porém não garante que uma terceira parte tenha acesso ao conteúdo da mensagem.

### **Certificados de Chave Pública**

Analisando a criptografia de chave pública, uma característica exclusiva é dispor da chave pública, onde a chave pode ser distribuída publicamente sem nenhum prejuízo. Deste modo, na utilização de um algoritmo de chave pública, tal como o RSA, qualquer usuário pode disponibilizar sua chave pública para outros usuários. Apesar desta abordagem ser oportuna, ela possui certas limitações: qualquer indivíduo pode falsificar um comunicado público, isto é, um indivíduo mal-intencionado pode se passar pela Alice e enviar uma chave pública a outros participantes, o ainda divulgar a chave pública de forma "aberta" (disponibilizar publicamente). Enquanto Alice não descobrir a farsa e conseguir alertar os participantes, o adversário conseguirá ter acesso ao conteúdo de todas as mensagens cifradas que foram enviadas, ainda pode utilizar as chaves falsificadas para conceber a autenticação.

A ideia do certificado consiste em utilizar uma chave pública associado ao identificador do proprietário da chave em conjunto com um bloco inteiro assinado por uma terceira parte, uma entidade confiável. Em geral, esta terceira entidade corresponde a autoridade certificadora na qual a comunidade tem absoluta confiança. A autoridade certificadora também é conhecida como CA (*Certification Authority*). É bastante comum que uma CA seja uma agência governamental ou uma instituição financeira. Para validar um certificado além da informação da CA é necessário fornecer o período de validade do certificado. Um usuário pode solicitar um certificado assinado pela CA dispondo da sua chave pública de forma segura. Posteriormente, este usuário pode publicar o certificado. Deste modo, quem precisar utilizar a chave pública do usuário poderá obter o certificado e consultar se ele é válido, verificando se a assinatura anexada é confiável. A figura exposta abaixo demonstra este processo.

![[UE6_img8.png]]

Fonte: Autor

Para formatar os certificados de chave pública foi adotado um padrão universal, o X.509. Os certificados X.509 são utilizados na grande maioria das aplicações de segurança em rede. Tais aplicações incluem protocolos bastante conhecidos como o IPsec (*IP Security*), TLS (*Transport Layer Security*), SSH (*Secure Shell*) e S/MIME (*Secure / Multipurpose Internet Mail Extension*).

## **CURIOSIDADE**

IPsec - é um protocolo de comunicação segura na internet utilizado para tunelamento, criptografia e autenticação.

S/MIME - é um protocolo amplamente aceito para enviar mensagens assinadas digitalmente e criptografadas.

### **Distribuição de Chave Simétrica Usando Criptografia de Chave Pública**

Conforme mencionado, um requisito fundamental da cifração simétrica para possibilitar uma comunicação segura entre duas partes é que elas devem compartilhar uma chave secreta. Para exemplificar, imagine que Alice deseja criar uma aplicação de envio de mensagens. A aplicação deve possibilitar a troca de e-mail de forma segura na internet ou uma rede privada que seja compartilhada entre duas partes. Alice quer utilizar criptografia simétrica na sua aplicação. Utilizando a criptografia simétrica, para que Alice estabeleça uma comunicação segura com alguns dos seus contatos, ela deve encontrar uma maneira segura de compartilhar a chave secreta para que nenhum indivíduo indesejado tenha acesso ao conteúdo das mensagens.

Digamos que Alice precisa compartilhar a chave secreta com Bob. Dado as restrições da localização física isto pode ser tornar um desafio. Alice poderia cifrar a chave utilizando a criptografia simétrica e posteriormente enviar a chave criptografada por e-mail para Bob, porém isto requer que Alice e Bob já possuam uma chave secreta compartilhada entre eles. Ainda, ressalta-se que todos os demais contatos que desejam utilizar o novo aplicativo irão enfrentar esta mesma situação, cada par de correspondente (emissor e receptor) deverão compartilhar uma chave secreta única e exclusiva.

Uma das estratégias é adotar o método de troca de chaves Diffie-Hellman. Esta é uma abordagem amplamente utilizada, contudo possui uma limitação, na implementação mais simples do algoritmo de Diffie-Hellman não é fornecido qualquer tipo de mecanismo de autenticação entre as duas partes comunicantes. Algumas variações do algoritmo de Diffie-Hellman já tratam este problema. Adicionalmente, também existem alguns protocolos que utilizam criptografia de chave pública para este mesmo propósito.

### **Envelopes Digitais**

Os envelopes digitais são um outro tipo de aplicação que envolve o uso de criptografia de chave pública. O conceito do envelope digital é o de proteger uma mensagem sem a necessidade de que o emissor e o receptor compartilhem a mesma chave secreta. Esta técnica seria o equivalente ao criar um envelope selado, porém contém uma carta que não foi assinada. A representação da abordagem é apresentada na figura abaixo.

![[UE6_img9.png]]

Fonte: Autor

Imagine que Alice deseja encaminhar uma mensagem confidencial para Bob, contudo eles não possuem uma chave secreta simétrica compartilhada entre eles. Deste modo, Alice pode prosseguir da seguinte forma:

1. Estrutura a mensagem.

1. Cria uma chave simétrica aleatória temporária (deverá ser utilizada somente uma vez).

1. Efetua a cifragem da mensagem utilizando criptografia simétrica com a chave secreta que deverá ser usada uma única vez.

1. Realiza a cifragem da chave secreta de uso único utilizando a criptografia assimétrica com a chave pública de Bob.

1. Por fim, anexa na mensagem a chave secreta (uso único) que está cifrada, então envia a mensagem cifrada para Alice.

Deste modo, apenas Bob conseguirá decifrar a mensagem contendo a chave de uso único, necessária para decifrar a mensagem original. Destaca-se que se Alice conseguiu a chave pública de Bob por meio do certificado de chave pública de Bob, então ela terá certeza de que esta chave pública é válida.

## **Cifração/Decifração**

Os algoritmos de criptografia de chave pública utilizam sempre um par de chaves relacionadas, contudo distintas, uma das chaves utilizada para cifrar e outra por sua vez para decifrar. Destaca-se, que a chave utilizada para decifrar não pode ser obtida a partir da análise da chave de cifragem. Nos algoritmos de chave pública, as chaves são criadas sempre em pares: uma para cifrar e a outra para decifrar.

Conforme já discutido, a chave utilizada para cifrar a mensagem é denominada chave pública, esta chave pode ser divulgada para o transmissor da mensagem. Em contrapartida, a chave utilizada para decifrar a mensagem é conhecida como chave privada, esta chave deve ser guardada em segredo, pertencente ao receptor e não deve ser divulgada.

A característica fundamental do algoritmo assimétrico é que a chave pública pode ser distribuída livremente. A chave privada é a única maneira de decifrar uma mensagem que foi cifrada com a chave pública. Desta maneira, apenas o receptor da mensagem será capaz de decifrar a mensagem de qualquer indivíduo que utilize a sua chave pública para cifrar a mensagem. Assim, cada usuário possui uma chave pública e outra privada.

A figura abaixo demonstra o processo de cifragem e decifragem utilizando um algoritmo de criptografia de chave pública. Observe que na cifragem, o usuário emissor utiliza a chave pública do receptor como entrada para o algoritmo de criptografia, em conjunto com o texto às claras. Em contrapartida, na decifragem, o receptor, ao receber a texto cifrado, utiliza a sua chave privada (chave que apenas ele deve conhecer) como entrada para o algoritmo de criptografia, como resultado obtém o texto às claras.

![[UE6_img10.png]]

Fonte: Autor

Os algoritmos de criptografia de chave pública possuem algumas limitações em relação ao desempenho, porque exigem alto nível de processamento, o que os torna muito mais lentos do que os algoritmos simétricos. Neste sentido, uma estratégia bem interessante é utilizar os dois tipos de algoritmos em conjunto, isto permite aproveitar os pontos fortes de cada algoritmo e reduzir os pontos fracos de ambos os tipos de criptografia.

Ao retomar o cenário de estudo do banco de Tóquio (introduzido na Unidade 1) neste ponto, podemos enfatizar a importância de combinar as diferentes abordagens de criptografia para obter um sistema mais seguro. O incidente no banco de Tóquio poderia ter sido evitado se tivessem sido utilizados algoritmos de criptografias adequados ao cenário do banco. O malware disseminado no banco, só conseguiu “quebrar” as senhas dos usuários do sistema de forma rápida, devido os sistemas utilizarem criptografia simétrica com tamanho de chaves de 56 bits, este fator associado com a definição de senhas fracas possibilitou um ataque bem-sucedido.

## **Distribuição de Chaves Pública**

Existem algumas abordagens utilizando a criptografia assimétrica projetada para fornecer um esquema de distribuição de chaves públicas. Em geral, tais abordagens podem ser classificadas em um dos seguintes grupos:

- Diretório de chaves disponível publicamente;
- Autoridade de chave pública (CA);
- Certificados de chave pública;
- Anúncio público.

### **Diretório de Chaves Disponível Publicamente**

A estratégia de utilizar um diretório dinâmico para conceder as chaves públicas fornece um nível maior de segurança. Contudo, o processo de gerenciamento e distribuição das chaves no diretório público deve ser atribuído a uma entidade confiável de fé pública, em geral uma instituição governamental ou financeira. A abordagem de um diretório da distribuição de chaves públicas é representada na figura abaixo:

![[UE6_img11.png]]

Fonte: Autor

As etapas fundamentais são demostradas as seguir:

31. Cada usuário deve conceber um par de chaves que será utilizado para o processo de cifragem e decifragem das mensagens.
32. O usuário deve alocar uma das duas chaves em um registrador público ou utilizar outro meio para disponibilizar esta chave, esta chave é denominada como chave pública. A outra chave deve ser mantida em segurança, esta chave é denominada como chave privada. Adicionalmente, cada usuário mantém um conjunto de chaves públicas de outros usuários.
33. Caso Alice deseje enviar uma mensagem secreta para Bob, ela cifra a mensagem utilizando a chave pública de Bob.
34. Quando Bob receber a mensagem, ele utiliza a chave privada para decifrar a mensagem. Destaca-se que nenhum outro indivíduo conseguirá decifrar a mensagem, pois somente Bob conhece a chave privada.

Esta abordagem fornece um nível considerável de segurança, contudo ainda assim este esquema possui fraquezas. Caso um adversário consiga obter acesso a chave privada da autoridade do diretório, a comunicação entre todos os participantes estaria comprometida. O adversário poderia falsificar a chave pública de qualquer um dos participantes além de espionar as mensagens enviadas pelos demais participantes. Ainda, outra vulnerabilidade que o adversário poderia explorar, são os registros mantidos pela autoridade.

### **Autoridade de Chave Pública**

Um mecanismo de segurança mais forte para distribuição de chave pública pode ser alcançado com a adoção de controles mais rigorosos no processo de distribuição de chaves públicas utilizando um diretório. Um cenário típico foi apresentado por Popek, esquematizado na figura adaptada de [Popek e Kline,1979] a seguir:

![[UE6_img12.png]]

Fonte: Adaptado de: Popek e Kline, 1979

O cenário exposto considera que uma autoridade central gerencia um diretório de chaves públicas. Ainda, é necessário que cada participante tem acesso seguro a chave pública da autoridade responsável, enfatizando que somente a autoridade responsável deve ter acesso a chave privada correspondente. As seguintes etapas são expostas por Popek:

1. O usuário A envia uma mensagem com* **timestamp* à autoridade de chave pública, solicitando a chave pública do usuário B.

1. A autoridade responde com uma mensagem que é cifrada utilizando a chave privada da autoridade. Assim, o usuário A é capaz de decifra a mensagem utilizando a chave pública da autoridade. Desse modo, o usuário A tem certeza de que a mensagem foi originada pela autoridade. A mensagem inclui o seguinte:

- A chave pública do usuário B, que o usuário A pode utilizar para cifrar a mensagens destinadas ao usuário B.
- A solicitação original, para permitir que o usuário A compare essa resposta com a solicitação anterior, verificando se a solicitação original não foi modificada antes do recebimento pela autoridade.
- O* **timestamp* original, para que o usuário A possa determinar que essa mensagem não é antiga da autoridade, contendo uma chave diferente da chave pública atual do usuário B.

1. O usuário A armazena a chave pública do usuário B utilizada para cifrar uma mensagem para o usuário B, contendo um identificador do usuário A e um* **nonce*, utilizada para identificar essa transmissão exclusivamente.

1. O usuário B obtém a chave pública do usuário A na autoridade da mesma forma como o usuário A obteve a chave pública do usuário B.

1. Idem as etapas realizadas pelo usuário A para obter a chave (passos 1 e 2).

Até este ponto, as chaves públicas foram fornecidas com segurança ao usuário A e usuário B, agora eles podem iniciar a troca de mensagens de forma segura. Entretanto, duas etapas adicionais apresentadas na sequência são desejadas:

1. O usuário B envia uma mensagem ao usuário A (cifrada com a chave pública do usuário A) e contendo o *nonce* do usuário A, além de um novo *nonce* gerado pelo usuário B. Como somente o usuário B poderia ter decifrado a mensagem (etapa 3), a presença de primeiro *nonce* na mensagem (etapa 6) permite garantir ao usuário A que o seu correspondente (com quem está trocando mensagem) é o usuário B.

35. O retorno do segundo *nonce* cifrado, utilizando a chave pública do usuário B, permite garantir ao usuário B que o seu correspondente é o usuário A.

## **CURIOSIDADE**

*Timestamp*

- é um instante único de tempo que permite determinar a ocorrência de um evento.

*Nonce* - é um número arbitrário que só pode ser usado uma vez.

Observe que para realizar uma comunicação segura são necessários um total de troca de sete mensagens. Contudo, as primeiras quatro mensagens são utilizadas com pouca frequência, pois tanto o usuário A quanto o usuário B podem salvar a chave pública um do outro para utilização futura, esta técnica é conhecida como *caching*. Devemos ressaltar, que os usuários devem solicitar periodicamente cópias recentes das chaves públicas de seus correspondentes, visando garantir sempre que as chaves públicas sejam atuais.

### **Certificados de Chave Pública**

O aumento na quantidade de usuário e requisições realizadas na autoridade de chave pública pode ocasionar um gargalo no sistema, pois cada usuário deverá contatar a autoridade responsável a fim de obter a chave pública do usuário com quem pretende se comunicar. Ressalta-se que o diretório de nomes e chaves pública também pode ser vulnerável à violação. Como alternativa, é possível utilizar certificados para possibilitar que os usuários troquem as chaves públicas sem a necessidade de participar a autoridade de chave pública, propondo uma maneira para realizar as trocas de chaves que seja tão confiável quanto se a troca fosse realizada com a autoridade de chave pública.

Observando que um certificado consiste basicamente em três partes: a chave pública, um identificador do proprietário da chave (informações do usuário), e um bloco inteiro assinado por uma autoridade certificadora. Um determinado usuário pode solicitar um certificado para uma autoridade certificadora, para isto o usuário deve apresentar a sua chave pública de uma forma segura. Posteriormente, o usuário torna público este certificado. Deste modo, qualquer outro usuário que necessite utilizar a chave pública desse usuário poderá verificar se a chave é válida por meio da assinatura confiável a ele anexado. Os demais participantes também podem gerar seus próprios certificados junto a autoridade certificadora. Consequentemente, cada participante pode consultar se as demais chaves públicas são válidas verificando se o certificado foi realmente criado por uma autoridade confiável. Alguns requisitos devem ser avaliados neste processo:

1. Todos os participantes podem ler o certificado para validar a identidade e a chave pública do proprietário do certificado;

1. Todos os participantes podem verificar se um determinado certificado foi gerado pela autoridade certificadora, garantindo que o certificado não foi falsificado;

1. Apenas a autoridade certificadora deve criar e atualizar os certificados;

1. Todos os participantes podem verificar se os certificados ainda são válidos.

Para que esta abordagem seja efetiva é necessário que cada participante solicite seu certificado válido junto a autoridade certificadora. Ressalta-se que esta demanda é imprescindível que seja realizada de forma segura, feita pessoalmente ou utilizando uma comunicação segura.

### **Anúncio Público**

Utilizando um algoritmo de chave pública como o RSA, qualquer participante pode encaminhar sua chave pública para outro participante, ou ainda poderá transmitir as chaves por meio de *broadcast*, ou seja, enviar a chave pública para todos os participantes da comunidade. Na figura a seguir é demonstrada a distribuição da chave pública utilizando *broadcast*.

![[UE6_img13.png]]

Fonte: Autor

Uma ferramenta bastante popular que utiliza o algoritmo RSA é o PGP (*Pretty Good Privacy*), diversos usuários adotam a prática de disponibilizar sua chave pública em anexo em *posts* em fóruns públicos apropriados.

Apesar desta técnica ser conveniente, de uma certa maneira, ela possui vulnerabilidades, pois, qualquer indivíduo mal-intencionado pode falsificar este anúncio público. Para o adversário seria tarefa simples, ele poderia fingir ser um determinado usuário e enviar uma chave pública falsificada para outro participante ou ainda em *broadcast*. Até que o usuário autêntico que possui aquela identidade que está sendo falsificada descubra a falsificação e avise os demais participantes, o adversário já teve acesso as mensagens que foram enviadas cifradas para este usuário, além do adversário poder utilizar a chave falsificada para fins de autenticação.

## **Explorando os mecanismos de criptografia simétrica e assimétrica**

Este vídeo fornecerá uma visão mais ampla sobre os mecanismos de criptografias simétricos e assimétricos, vamos apresentar os elementos fundamentais associados a cada um dos algoritmos, quais as vantagens e desvantagens de utilizar estas abordagens, dicas e boas práticas para implementação destes mecanismos de segurança.

## **EXERCÍCIO**

**Exercícios de Fixação**

Descreva com suas palavras como funciona o algoritmo de criptografia simétrica.

Quais os elementos fundamentais da criptografia simétrica?

Quais os dois requisitos necessários para utilização da criptografia simétrica de forma segura?

Quais os principais tipos de ataques direcionados a criptografia simétrica?

Cite 3 algoritmos de criptografia simétrica.

Quais os problemas relacionados a distribuição das chaves na criptografia simétrica?

O que é um KDC, e para que é utilizado?

Qual a diferença da chave mestra e chave de sessão no KDC?

Descreva com suas palavras como funciona o algoritmo de criptografia assimétrica.

Quais os elementos fundamentais da criptografia assimétrica?

Cite 3 algoritmos de criptografia assimétrica.

Cite 3 aplicações para criptografia de chave pública.

Para que é utilizado a assinatura digital?

O que é uma CA?

Para que é utilizado um certificado de chave pública?

Para que serve os envelopes digitais?

Quais são as principais abordagens para distribuição das chaves públicas?

## **Conclusão**

Esta unidade abordou os mecanismos de criptografia simétrica e assimétrica. Descobrimos que na criptografia simétrica o emissor e receptor compartilham a mesma chave secreta. Conforme discutido, esta chave é utilizada tanto para cifrar como decifrar uma mensagem. Destacamos a importância de proteger e preservar a chave secreta. Exploramos os princípios da cifração simétrica, onde foram apresentados os cinco elementos fundamentais da criptografia simétrica, o texto às claras, algoritmo de cifração, chave secreta, algoritmo de decifração e texto cifrado. Ainda, foi apresentado as principais características do algoritmo de cifração simétrica. Constatamos que o adversário pode explorar duas técnicas para atacar um sistema de criptografia simétrica, através de um ataque de criptoanálise ou utilizando um ataque de força bruta, então mostramos quais as contramedidas necessárias.

Por conseguinte, apresentamos os principais algoritmos de criptografia simétrica adotados como padrão pelo NIST, o algoritmo DES, Triplo DES e AES. Demonstramos a evolução dos algoritmos de criptografia simétrica e as limitações de cada algoritmo. Ainda, mostramos que o tamanho da chave secreta utilizada para cifrar uma mensagem reflete no tempo necessário para "quebrar" a mensagem que foi cifrada com essa chave. Enfatizamos a importância de proteger e armazenar corretamente a chave secreta. De acordo com o que estudamos, uma das grandes limitações da criptografia simétrica é justamente a distribuição das chaves secretas. Discutimos o cuidado que devemos ter para compartilhar esta chave de maneira segura. Conforme estudamos o KDC é considerado a melhor opção para compartilhar a chave secreta na rede. Adicionalmente, abordamos a hierarquia de chaves necessária para troca de chaves utilizando o KDC.

Exploramos também a criptografia de chave pública, as principais características e os elementos fundamentais deste mecanismo. Conforme discutido, verificamos que a criptografia assimétrica trabalha com um par de chaves, uma chave pública e a outra privada. Verificamos que um texto cifrado com uma das chaves somente poderá ser decifrado pela outra chave correspondente. Descobrimos que a chave privada é exclusiva do proprietário, não deve ser divulgada, apenas ele deve ter acesso a esta chave. Por sua vez, a chave pública pode ser distribuída para os participantes. Adicionalmente, apresentamos os principais algoritmos de criptografia de chave pública, o algoritmo RSA, Diffie-Hellman, DSS e as Curvas elípticas. Entre as aplicações de criptografia, mostramos como é estruturado os algoritmos assinatura digital, autenticação de mensagens, certificados de chave pública, envelopes digitais, e outras aplicações.

Por fim, demonstramos vulnerabilidades que os adversários podem explorar, associadas ao uso dos mecanismos de criptografia, mas sobretudo as estratégias e boas práticas para contorná-las. Descobrimos as vantagens e desvantagens de utilizar as criptografias simétrica e assimétrica. Discutimos sobre os desafios do profissional de segurança da informação para implementar tais mecanismos. Deste modo, demonstramos como podemos combinar diferentes algoritmos de criptografia para propor um cenário de segurança mais robusto e adequado ao contexto de cada organização.

## **Detecção de intrusão**

*Nesta Unidade, iremos estudar os mecanismos defesa para detecção de intrusão. Será abordado como os adversários exploram as vulnerabilidades dos sistemas para ter acesso aos seus recursos, mas sobretudo como o profissional da área de segurança pode atuar para evitar que as tentativas de intrusão sejam bem-sucedidas. Para tal, apresentaremos os Sistemas de Detecção de Intrusão (IDS), como os tais sistemas são utilizados para monitorar e analisar os eventos no sistema. Conhecer os elementos fundamentais do IDS. Na sequência, vamos apresentar os tipos de IDS, como são classificados e as técnicas utilizadas para detectar um ataque. Adicionalmente, vamos apresentar as abordagens detecção de intrusão em rede e realizado em nível de host. Conheceremos também como é realizado a detecção de intrusão utilizando assinaturas e por meio da identificação de anomalias. Ainda, será abordado a evolução do processo detecção das IDS, verificaremos as técnicas de intrusão adaptativa, ou seja, como os mecanismos de segurança podem agir para detectar os eventos de intrusão. Por fim, iremos apresentar o Honeypot, ferramenta que permite analisar o comportamento do adversário visando identificar aspectos que devem ser fortalecidos para proteger os sistemas.*

## **Sistemas de Detecção de Intrusão**

A intrusão de segurança é caracterizada como sendo um evento de segurança (este isolado ou composto por uma série de eventos), onde o intruso obtém ou tenta conseguir acesso ao sistema e seus recursos em ter a devida autorização. A grande maioria dos ataques exploram vulnerabilidades nos sistemas ou *softwares*, permitem que o adversário execute rotinas de código projetadas para abrir portas de entrada para conseguir acesso ao sistema.

Os adversários podem conseguir acesso ao sistema explorando diversas vulnerabilidades, entre elas ataques de estouro de um *buffer* de memória executado em um programa que possui determinados privilégios. Ainda, o intruso pode tentar ter acesso a informações que deveriam estar protegidas, tal como informações de acesso como usuário e senha. Adicionalmente, caso o intruso consiga acesso à senha de um usuário no sistema, ele poderá usufruir de todos os privilégios que o usuário legítimo possui.

Por sua vez, a detecção de intrusão pode ser definida como sendo um serviço de segurança utilizado para monitorar e analisar tais eventos no sistema. Têm como propósito identificar e notificar o administrador do sistema que estão ocorrendo tentativas de acesso não autorizado ao sistema e aos seus recursos. Os alertas devem ser gerados em tempo real ou quase que em tempo real para que o responsável pelo sistema possa realizar determinadas ações. Neste sentido, para auxiliar o profissional de segurança da informação sistemas de detecção de intrusão (*Intrusion Detection System* - IDS) e sistemas de prevenção de intrusão (*Intrusion Prevention System* — IPS) podem ser utilizados.

![[UE7_img1.jpeg]]

Fonte: ©leowolfert/Adobe Stock

Em geral os IDS são classificados do seguinte modo:

- **Baseado em estação**: este sistema monitora as características de uma única máquina, analisa os eventos que ocorrem dentro da máquina em busca de alguma atividade suspeita.
- **Baseado em rede**: este sistema monitora o tráfego de rede dos dispositivos conectados analisando os protocolos de rede, transporte e aplicação visando identificar alguma atividade suspeita.

Basicamente o IDS é constituído por três elementos:

- **Sensor**: os sensores são responsáveis por efetuar a coleta de dados;
- **Analisador**: os analisadores recebem os dados coletados dos sensores e determinam se ocorreu alguma intrusão;
- **Interface do usuário**: a interface do usuário permite que o usuário avalie e controle o comportamento do sistema.

Os IDS utilizam os sensores que realizam a coleta dos dados. Entre os tipos de dados capturados são obtidos pacotes de rede, arquivos de registro e eventos de chamadas do sistema. Após efetuar a coleta dos dados os sensores transmitem essas informações ao componente analisador. Na sequência o analisador verifica os dados e determina se ocorreu uma intrusão. O analisador ao identificar uma intrusão produz uma saída com o resultado da intrusão para que seja tomada uma providência.  O administrador do sistema poderá verificar a ocorrência de uma intrusão por meio da interface do usuário com um IDS, desta forma poderá avaliar e tomar as ações necessárias.

Quando a intrusão é detectada com prontidão o intruso pode ser identificado e imediatamente expulso do sistema, antes que cause qualquer dano ou comprometa os dados do sistema. Ainda que a detecção do intruso não ocorra em tempo real para inibir as ações do invasor, quanto antes for identificado a intrusão menor será o impacto e mais rápido será o processo de recuperação.

Um sistema de detecção de intrusão efetivo pode ser útil tanto para inibir como prevenir que a intrusão ocorra. A partir da coleta das informações no processo de detecção de intrusão é possível extrair informações técnicas que podem ser utilizadas para definir ações para fortalecer os sistemas na prevenção da intrusão.

A detecção de anomalia é efetiva contra a ação do adversário que tenta se passar um usuário legitimo, sendo que este não conseguirá reproduzir os mesmos padrões do comportamento das contas que eles obtêm acesso. Contudo, esta abordagem não será capaz de lidar com os adversários que tem intenção de perturbar o sistema. Para este tipo de ataque, as abordagens baseadas em assinaturas são mais eficazes, sendo capazes de reconhecer eventos e sequências de eventos, pois inseridas em um determinado contexto permitem identificar que está ocorrendo uma determinada intrusão. O ideal é que na prática, o sistema implemente ambas as abordagens, a combinação das duas técnicas será mais efetiva contra um número maior de tipos de ataques.

## **Tipos de Sistemas de Detecção de Intrusão**

Os sistemas de detecção de intrusão podem ser classificados conforme as técnicas utilizadas para identificar o ataque, sendo basicamente os sistemas baseados em regras e os sistemas adaptáveis.

**Sistemas Baseados em Regras**: esta abordagem utiliza regras a partir de padrões de ataques que compõem uma base de dados, conhecidas como assinaturas. A base de dados deve estar constantemente atualizada. Uma das limitações de utilizar esta abordagem é que ela possibilita detectar apenas os ataques conhecidos. Ainda, se a regra definida para identificar um ataque for muito específica, alguns ataques similares que não sejam idênticos certamente não serão identificados.

**Sistemas Adaptáveis**: esta abordagem em geral utiliza inteligência artificial para tentar identificar novos ataques. Apesar de ser uma técnica promissora, exige um custo computacional mais alto e impõe uma certa dificuldade no gerenciamento, que engloba conhecimentos específicos de matemática e estatística.

![[UE7_img2.jpeg]]

Fonte: ©Dmitry/Adobe Stock

### **Arquitetura IDS**

Os sistemas de intrusão podem ser classificados também por meio da sua arquitetura, sendo classificado como arquitetura centralizada ou distribuída.

**Arquitetura Centralizada**: o IDS é classificado como arquitetura centralizada quando realiza a coleta, análise e gerência dos dados em um único componente. Este tipo de arquitetura permite simplificar a topologia de um projeto IDS, praticamente não interfere no desempenho da rede. A desvantagem é que esta arquitetura estabelece um único ponto de falha, onde uma falha nesse componente pode comprometer todo o processo de análise de intrusão do IDS. Destaca-se, a dificuldade da implementação e manutenção desta abordagem em grandes redes, dificultando a escalabilidade do sistema.

**Arquitetura distribuída**: a arquitetura distribuída pode ser classificada em distribuída hierárquica ou livremente distribuída. Na arquitetura distribuída hierárquica as funções são distribuídas em diversos componentes, porém existe um forte acoplamento em relação à hierárquica. Apesar desta arquitetura facilitar em escalabilidade e desenvolvimento, ainda apresenta o problema de ter um ponto único de falha, destaca-se que um problema no componente que possui maior grau de hierarquia compromete todo o sistema. Em contrapartida a arquitetura livremente distribuída não tem esta dependência hierárquica, o que reflete em uma certa facilidade de escalabilidade do sistema, incluindo o crescimento modular, detecção abrangente e facilidade para distribuir as tarefas. Porém, para implementar este sistema existe uma certa complexidade dada a necessidade de integrar todos os componentes, sendo necessário a adoção de um mecanismo de autenticação, contudo a adição de tal ferramenta pode impactar no desempenho da rede.

### **Tipificação dos Sistemas de Detecção de Intrusão**

Os IDS podem ser divididos em três tipos: NIDS, HIDS e IDS Híbrido.

**NIDS (Network-based IDS)**: Um sistema de intrusão baseado em rede examina os pacotes transmitidos tentando identificar pacotes que se assemelham com os padrões de assinaturas correspondentes a uma intrusão no sistema. Esta abordagem é bastante eficiente contra os ataques mais conhecidos, por outro lado novos ataques podem passar despercebidos caso não possuam padrões semelhantes aos padrões de ataques já conhecidos e representados pelas assinaturas.

**HIDS (Host-based IDS)**: nesta abordagem o sistema de detecção de intrusão analisa informações obtidas de computadores individuais. O HIDS verifica as atividades e acessos realizados em servidores que dispõe de tais serviços, verificam as atividades determinando os processos e usuários associados a um determinado ataque. Ainda, podem observar os impactos causados por uma tentativa de ataque, ao identificar arquivos e processos alvos de ataques, o administrador do sistema pode estruturar estratégias para proteger tais recursos. O HIDS é importante tanto para detectar uma intrusão externa como também acessos indevidos de origem interna. O HIDS tenta identificar qualquer atividade suspeita, falhas de acesso (login), alterações nas políticas de controle de acesso não autorizadas (arquivos ou sistemas).

**IDS Híbrido**: IDS Híbrido: esta abordagem basicamente é a combinação de um HIDS (*Host-based IDS*) com um NIDS (*Network-based IDS*).

![[UE7_img3.jpeg]]

Fonte: ©sdecoret/Adobe Stock

## **Detecção de Intrusão em Rede**

O sistema de intrusão baseado em rede é denominado NIDS, acrônimo do termo inglês *Network-based Intrusion Detection System*. O NIDS é uma ferramenta que monitora o tráfego da rede em "tempo real", analisa pacote por pacote, a fim de tentar detectar comportamento de intrusão. Esta ferramenta atua sobre os protocolos de rede, transporte e aplicação. Deste modo, examina o tráfego da rede identificando padrões de intrusão direcionado a sistema de computadores vulneráveis.

A topologia tradicional da ferramenta de NIDS dispõe de sensores, servidores e consoles. Existem diversos sensores distribuídos na rede, estes são utilizados para monitorar o tráfego de pacotes. Um NIDS pode incluir um ou mais servidores, sendo responsáveis pelo gerenciamento da ferramenta. Por fim, o console permite que o administrador da rede interaja com o NIDS por meio da sua interface. O processo de análise dos padrões de tráfego pode ser realizado tanto no sensor como também diretamente no servidor, ou então utilizando uma estratégia realizada a partir da combinação dos dois componentes. Existem algumas limitações em relação a esta abordagem:

- Velocidade de análise: uma rede que possui um número expressivo de dispositivos os sistemas baseados em redes não serão capazes de processar todo grande volume de dados que é transmitido na rede.
- Ambiente *switches*: existe um esforço computacional bastante grande para examinar todos os pacotes que chegam no *switch*. Destaca-se que nem todos os *switches* permitem realizar monitoramento das portas, o que permite que o NIDS analisar apenas uma única estação de trabalho. Alternativamente, uma solução seria adicionar o NIDS diretamente no próprio *switch*.
- Dados criptografados: utilizando uma ferramenta NIDS não é possível analisar pacotes que transitam com dados criptografados, sendo que não possuem a chave para decifrar os dados. Para que o NIDS conseguisse examinar os pacotes com dados cifrados o sistema deveria: .
- Ser estruturado com as chaves cifração ou adquiri-las ao realizar a conexão.
- Identificar o algoritmo de criptografia.
- Compreender o protocolo da aplicação.
- Capturar e decifrar toda a sessão em tempo de execução (quase em tempo real).
- Fornecer garantia que o NIDS não seja comprometido.
- Grande parte dos NIDS não permite determinar se a ocorrência de um ataque foi bem-sucedida, apenas indicam que um ataque identificado.
- Alguns sistemas de detecção de intrusão têm dificuldades para tratar dados fragmentados.

![[UE7_img4.jpeg]]

Fonte: ©Niall/Adobe Stock

Entre as principais vantagens de utilizar um NIDS é que podemos ressaltar é que esta abordagem tem pouco impacto sobre o desempenho da rede. Ainda, um NIDS posicionado de forma estratégica pode permitir monitorar grandes redes de forma transparente ao atacante. Deste modo, é comum instalar o NIDS em pontos de acesso à rede interna, trabalhando em conjunto com* **firewalls* a fim de proteger o perímetro da rede. Adicionalmente, podem ser inseridos em alguns pontos críticos da LANs e WANs.

Um sistema de detecção de intrusão pode reagir com respostas passivas ou ativas. Atuando de forma passiva ele apenas alertam os administradores do sistema, podendo disparar mensagens e e-mail. Por sua vez, a resposta ativa requer que haja uma integração entre o NIDS e o *firewall*. Entre as ações típicas realizadas pelo sistema podemos citar:

- Encerrar a sessão de usuário.
- Bloquear uma conexão TCP.
- Executar um *script* pré-configurado pelo administrador do sistema, em geral para introduzir regras no *firewall*.
- Bloquear determinados endereços IP (origem do ataque) no *firewall*.
- Bloquear o tráfego entre IPs e portas específicas no *firewall*.
- Efetuar a desconexão de um serviço realizado em uma determinada porta.

### **Sensores de Rede NIDS**

Existem basicamente dois tipos de sensores no NIDS: *inline* e passivo. O sensor *inline* é adicionado em ponto estratégico da rede de modo que todo tráfego que está sendo monitorado passe por este sensor. Em geral este comportamento é obtido a partir da combinação do sensor NIDS com outros dispositivos de rede, tais como o *firewall* ou *switch*. Uma das principais vantagens desta abordagem é não ser necessário dispositivos de *hardware* adicionais para realizar a tarefa do sensor, podendo neste caso ser substituído por um componente de *software*. O incentivo de utilizar sensores *inline* é a possibilidade de bloquear ataques assim que eles são detectados. Deste modo, o sensor *inline* permite habilitar o NIDS para atuar na detecção e prevenção da intrusão.

Em geral os sensores passivos são mais utilizados, a abordagem a adotada por este sensor é realizar uma cópia do tráfego de rede, destaca-se que o tráfego real não passa por este dispositivo. Esta abordagem é mais interessante que o sensor *inline*, pois não acrescenta nenhuma etapa adicional no tratamento do tráfego da rede, evitando assim atrasos na transmissão dos pacotes. O sensor passivo estabelece uma conexão física para transmissão da rede, fornecendo uma cópia de todo o tráfego de rede transmitido. Em geral, a placa de rede utilizada para esta conexão não possui um endereço IP configurado. O tráfego que passa pela placa de rede é absorvido sem qualquer interação com o protocolo de rede. Adicionalmente, o sensor passivo possui uma segunda placa rede que possui um endereço IP configurado que permite se comunicar com o servidor NIDS.

## **Detecção de Intrusão em Nível de Host**

Os IDS's baseado em nível de *host* em geral adicionam uma camada adicional de software especializada em segurança em sistemas sensíveis ou vulneráveis. Este sistema monitora as atividades nos servidores tentando identificar comportamentos suspeitos. O objetivo principal deste mecanismo é detectar as intrusões, realizar o registro de eventos que sejam suspeitos e emitir alertas ao responsável pelo servidor. Em determinadas situações, o IDS permite até mesmo interromper um ataque antes que seja causado qualquer dano.

![[UE7_img5.jpeg]]

Fonte: ©shane/Adobe Stock

A principal vantagem do IDS baseado em Host que este pode ser utilizado tanto para detectar intrusões internas como externas. Neste aspecto, o IDS baseado em Host fornece alguns recursos adicionais ao IDS baseado em rede ou *firewall* que detecta apenas intrusões externas. Os IDS baseados em Host são estruturados basicamente de duas maneiras:

- **Detecção de anomalia**: nesta abordagem primeiramente é realizado por um certo tempo a coleta dos dados de usuários legítimos, dados utilizados para definir um padrão do comportamento desses usuários. Posteriormente, testes estatísticos são aplicados sobre os eventos no sistema para definir com um nível de confiança se um determinado comportamento corresponde a um usuário legítimo ou não.
- **Detecção de assinatura**: nesta abordagem são definido um conjunto de regras estruturadas a partir da identificação de padrões de ataques, na sequência tais regras podem ser utilizadas para detectar se um determinado comportamento corresponde a um intruso ou não.

As abordagens baseadas em anomalia são projetadas para definir se determinado comportamento é normal, por sua vez as abordagens baseadas em assinaturas são utilizadas para definir se determinado comportamento é apropriado. Um HIDS atua especificamente sobre as máquinas que devem proteger. Esta abordagem possui algumas limitações:

- Análise em tempo real: para que o HIDS de uma resposta em tempo real ele necessita utilizar recursos do resto do sistema. Acaba consumindo uma quantidade considerável de recurso, o que muitas vezes acaba não sendo proveitoso para determinadas aplicações.
- Complexidade no gerenciamento: esta abordagem é difícil de gerenciar, sendo necessário realizar a configuração em cada um dos *hosts*.
- Ponto de análise único: os HIDS não permitem reconhecer ataques que sejam direcionados a toda a rede.

Em contrapartida existem diversas vantagens em adotar esta abordagem:

- Esta abordagem permite monitorar eventos locais de um determinado *host*, detectando ataques que acabariam passando despercebidos por um IDS baseado em redes.
- O HIDS pode atuar em ambiente cujo tráfego de rede é criptografado, pois é possível analisar a informação antes que o mecanismo de criptografia seja aplicado, caso esteja posicionado no emissor, ou ainda após a mensagem ser decifrada, quando estiver situado no receptor.
- Quando o HIDS atua no nível de sistema operacional ele pode detectar determinados malware, prevenindo ataques relacionados a problemas de integridade em alguns programas.

## **Detecção de Intrusão Baseado em Assinatura e Anomalia**

As técnicas baseadas em assinatura permitem detectar a intrusão mediante a observação dos eventos no sistema e a aplicação de um conjunto de regras que levam o sistema a tomar uma decisão em relação ao padrão de atividade ser ou não um comportamento suspeito.  Tais regras são definidas como assinaturas.

![[UE7_img6.jpeg]]

Fonte: ©sdecoret/Adobe Stock

Atualmente os NIDS baseados em assinaturas são as abordagens mais comuns. Nesta abordagem um sensor é instalado em ponto da rede e fica examinando o tráfego dos pacotes, analisa cada um dos pacotes que passa pelo firewall mais próximo. Para detectar uma intrusão o NIDS baseado em assinatura compara cada um dos pacotes que trafegam na rede com as assinaturas. Então, quando o sensor detecta que determinado pacote possui características semelhantes a uma assinatura (padrão suspeito), ele sinaliza ao sistema que ocorreu um comportamento de intrusão, em resposta o sensor deve ativar um alerta. Ressalta-se que as máquinas utilizadas para rodar tais sensores devem executar apenas a ferramenta do IDS garantido que a estação esteja segura contra algum ataque. O valor do padrão da assinatura do IDS é estabelecido pela avaliação de alguns aspectos:

- Capacidade de detecção do IDS de acordo com as taxas de dados com as quais este é projetado para trabalhar.
- Tempo necessário que o IDS leva para conseguir identificar um ataque.
- Atualização do banco de dados de assinaturas.
- Experiência do profissional que irá atuar nos problemas referentes à intrusão.

Outra abordagem para detectar a intrusão na rede são os NIDS baseados em anomalias, esta classe é segmentada em dois grupos: estatísticos e de protocolo. A abordagem estatística em NIDS é menos frequente, nesta abordagem o sistema examina os pacotes que trafegam na rede, por de métodos estatísticos aplicados sobre os dados extraídos do sistema consegue detectar certos padrões de comportamento. Mudanças significativas identificadas em tais padrões indicam um ataque em potencial e em resposta um alerta é gerado.

Por sua vez, as abordagens baseadas em protocolos tentam identificar anomalias na camada dos protocolos de aplicação, onde são definidas regras a partir da estrutura e funcionamento dos protocolos, posteriormente essas regras são introduzidas nos sensores. Os IDS baseados em protocolos são bastante úteis para identificar ataques como o *Code Red*, esse ataque consiste em utilizar um *worm* que causa uma inundação de buffers utilizando uma sequência longa de caracteres com objetivo de estourar o buffer da aplicação. Isso, permite que o malware execute uma rotina de código malicioso e se espalhe ainda mais, por sua vez desfigurando o servidor neste processo. Destaca-se que uma abordagem baseada em assinatura irá permitir que os pacotes transitem até que uma assinatura seja identificada e utilizada para detectar este novo padrão, enquanto a abordagem baseada no protocolo consegue imediatamente identificar e inibir este ataque.

**CURIOSIDADE**Worm - é um malware capaz de se propagar automaticamente através de redes, enviando cópias de si mesmo de computador para computador.

O Guia de Sistemas de Detecção e Prevenção de Intrusão [Scarfone e Mell,2007] do NIST fornece uma relação dos ataques que são adequados para serem tratados por uma abordagem por assinatura e outra lista de ataques que devem ser tratados com uma abordagem baseada em detecção de anomalia. Para detecção baseada em assinatura são elencados os seguintes ataques:

- **Ataques à camada de aplicação**: A maioria das ferramentas NIDS analisa vários protocolos de aplicação. Entre os mais comuns destacam-se o DHCP, DNS, FTP, HTTP, IMAP, NFS, POP, RPC, SMB, SMTP, SNMP e Telnet. O NIDS tenta localizar padrões de ataque que visam tais protocolos, ataques tais como estouros de capacidade de *buffers*, adivinhação de senha e transmissão de *malware*.
- **Ataques à camada de transporte**: Para este tipo de ataque as ferramentas NIDS analisam o protocolo da camada de transporte, em especifico os protocolos TCP e UDP. Entre os exemplares deste tipo de ataque podemos citar a fragmentação incomum de pacotes, *sniffer* (escanear) em busca de portas vulneráveis e ataques direcionados ao protocolo TCP, tal como inundação da flag SYN.
- **Ataques à camada de rede**: Em geral os NIDSs são estruturados para analisar os protocolos IPv4, ICMP e IGMP. Entre os ataques mais frequentes podemos citar endereços IP falsificados e valores de cabeçalhos IP ilegais.
- **Serviços de aplicação inesperados**: A ferramenta NIDS tenta definir se uma atividade realizada em uma conexão de transporte possui o comportamento correspondente ao protocolo de aplicação. Podemos citar como exemplo, uma estação que executa um serviço de aplicação que não foi autorizado.
- **Violações de políticas**: Em relação a este ataque podemos citar o uso de sites Web inadequados e a utilização de protocolos de aplicação proibidos.

**CURIOSIDADE**IGMP - *Internet* *Group* *Management* *Protocol* é usado por Roteadores em uma rede IP para criar grupos de transmissão múltipla.

Já em relação a lista de ataques que devem ser tratados pela abordagem baseados em detecção de anomalia o NIST enumera os seguintes ataques:

- **Ataques de negação de serviço (*****DoS*****)**: Esse tipo de ataque aumenta significativamente o tráfego de pacotes ou ainda as tentativas de conexão, visando sobrecarregar o sistema. A detecção de anomalia é bem adequada para identificar tais ataques.
- **Escaneamento**: O ataque de escaneamento é realizado quando o adversário investe contra uma rede ou sistema enviando diferentes tipos de pacotes. Por meio das respostas obtidas do retorno dos pacotes, o adversário pode encontrar muitas características e vulnerabilidades do sistema. Deste modo, o ataque de escaneamento é utilizado como ferramenta de identificação do alvo para o adversário. Este tipo de escaneamento pode ser detectado por padrões de fluxo inesperados nas camadas de aplicação, transporte ou rede.
- **Worms**: os *worms* que se espalham entre os computadores podem ser detectados de diferentes formas. Alguns *worms* propagam-se rapidamente e utilizam uma grande quantidade da largura de banda, o que permite identificá-los. Os *worms* ainda podem ser detectados quando tentam fazer o computador se comunicar com outras máquinas com as quais normalmente não realizam nenhuma comunicação, adicionalmente podem fazer com que as estações utilizem portas que em geral não são utilizadas. Por fim, devemos salientar que muitos *worms* também fazem escaneamento.

## **Intrusão Adaptativa**

Com o passar dos anos, o conceito de IDS comunicante foi aos poucos evoluindo para técnicas que compreendem o uso de sistemas distribuídos, tais sistemas cooperam entre si para identificar intrusões, uma das características dos novos sistemas é a capacidade dos sistemas em adaptar-se a perfis de ataques mutáveis. Tais sistemas esbarram em dois problemas.

O primeiro problema é que tais ferramentas como os IDSs e *firewall* podem não reconhecer novas ameaças ou ainda modificações amplas de ameaças já existentes. O segundo problema é que é difícil de atualizar técnicas com a rapidez necessária para conseguir lidar com ataques que são disseminados rapidamente pela rede.

![[UE7_img7.jpeg]]

Fonte: ©sdecoret/Adobe Stock

Adicionalmente, existe um outro problema, relacionado com a defesa de perímetro, como *firewalls*, uma grande parte das empresas não definem políticas robustas no *firewall*, estabelecem fronteiras tênue (fracas) onde as estações conseguem entrar e sair da rede. Um típico exemplo são empresas que dispõem do uso de tecnologia sem fio em suas estações de trabalho ou ainda permitem que os *notebooks* dos colaboradores sejam adicionados as portas de rede.

Os adversários exploram tais problemas de diferentes formas. Uma das abordagens utilizadas pelos atacantes é o desenvolvimento de *worms* e outros malwares que se disseminam cada vez mais rápido, ainda elaboram ataques que atingem com uma potência destrutiva, tal como os ataques de DoS. Tais tipos de ataques ainda predominam. Contudo, os adversários recentemente têm investido esforços em algumas abordagens diferentes: tal como reduzir a velocidade da disseminação do ataque a fim de dificultar que os algoritmos tradicionais consigam identificá-los.

Uma das formas de combater tais ataques é utilizar sistemas cooperativos que são capazes de reconhecer ataques com base em pequenos sinais e então conseguir adaptar-se rapidamente. Considerando esta estratégia, os detectores de anomalia adicionados em nós locais devem procurar por evidências de atividades não usuais. Para ilustrar este cenário podemos dar um exemplo de uma máquina que normalmente realiza poucas conexões de rede, podemos suspeitar que um ataque está sendo realizado caso haja repentinamente um aumento na taxa de transmissão da conexão. Apenas com esta evidência o sistema local pode arriscar um falso positivo se reagir ao ataque suspeito, ou então arriscar um falso negativo se decidir ignorar o ataque aguardando uma evidência adicional. Em contrapartida, um sistema cooperativo adaptativo, utiliza um protocolo "par a par" para informar sua suspeita a outras máquinas, estabelecendo uma certa probabilidade da rede estar sendo alvo de ataque. Caso uma máquina receba um número de mensagens do mesmo tipo que ultrapasse um determinado limiar, esta estação compreende que está ocorrendo um ataque, então pode responder a este. A resposta pode ser apenas localmente para defender a si própria, mas também pode emitir uma mensagem de alerta para um IDS central.

Um IDS central é configurado com um conjunto padrão de políticas e regras de segurança. O sistema tem como base a entrada de sensores distribuídos, tais políticas são adaptadas e ações específicas são transmitidas para as diferentes plataformas no sistema distribuído. As políticas definidas para um dispositivo podem incluir as ações imediatas que devem ser tomadas ou ainda configurações de parâmetros a serem ajustados. O IDS central também pode transmitir políticas colaborativas para todas as plataformas, estas são utilizadas para ajustar o intervalo de envio e o conteúdo de mensagens colaborativas, mensagens "par a par". Existem basicamente três tipos de entrada que orientam as ações do IDS central:

- **Eventos de resumo**: são eventos de advindos de várias fontes que são coletados por pontos de coletas intermediários tais como os *firewalls*, servidores, os sensores IDS que servem como um segmento específico de uma rede organizacional. Tais eventos são concentrados para entrega das políticas para o sistema IDS central.
- **Eventos de Detecção e Interferência Distribuídas**: são alertas gerados quando o tráfego "par a par" habilita uma plataforma a determinar que um ataque está sendo realizado.
- **Eventos Pontos de Imposição de Política**: são eventos que residem em plataformas confiáveis (*IDSs* inteligentes e sistemas com autodefesas). Tais sistemas confrontam informações distribuídas, decisões locais e ações de dispositivos individuais para detectar intrusões que podem não ser evidentes considerando apenas o nível da estação.

## **Honeypots**

Um *honeypot* é uma ferramenta de segurança projetada para atrair o adversário e desviar sua atenção dos sistemas críticos. O *honeypot* também conhecido pelo termo em português "potes de mel", são encarados como um sistema chamarizes. Em um sistema *honeypot* são instaladas ferramentas que permitem simular o sistema operacional e seus serviços, seu propósito é fornecer um ambiente ao atacante para que este interaja com o sistema, em contrapartida o administrador do sistema analisa o comportamento do adversário a fim de proteger os seus sistemas. Os *honeypots* são basicamente projetados para:

- Distanciar o alvo do atacante dos sistemas críticos;
- Obter informações relacionadas as atividades do atacante, analisar seu comportamento e as técnicas utilizadas pelo adversário - objetivo de apreender com o ataque;
- Instigar que o atacante permaneça o tempo suficiente no sistema para que o administrador tome as ações necessárias.

Esses sistemas são constituídos por um conjunto de informações criadas para simular um sistema verdadeiro, porém que um usuário legitimo não acessaria. Deste modo, qualquer tipo de acesso realizado em um *honeypot* é uma atividade suspeita. O *honeypo*t é estruturado com componentes monitores e registradores de eventos. Tais componentes visam detectar a intrusão e coletar as informações referentes as atividades do atacante no sistema. Em geral, os ataques realizados contra um *honeypot* parecem ser bem-sucedidos, porém ao mesmo tempo os administradores do sistema estão focados em registar e rastrear o adversário sem que haja exposição dos sistemas reais.

O *honeypot* não dispõem de recurso legítimo para organização, deste modo qualquer interação de fora da rede que tente comunicar com o sistema é um possível ataque. Ainda, se o *honeypot* iniciar uma comunicação com o meio externo, este acabou sendo comprometido.

As primeiras propostas dos *honeypots* consistia em uma única máquina que possuía uma faixa de endereços IP que eram estruturados de forma a atrair os adversários. Com o avanço das pesquisas foram surgindo propostas de *honeypot* mais interessantes, atualmente redes inteiras são construídas para simular uma rede empresarial, até mesmo o tráfego na rede pode ser simulado. Para o adversário o comportamento da rede seria semelhante a uma rede normal. Neste sentido, assim que o adversário consegue ter acesso a rede, o administrador passa a acompanhar suas atividades e então projeta defesas baseadas nas estratégias que foram utilizadas pelo intruso.

O *honeypot* pode ser colocado em algumas posições estratégicas. A localização varia conforme o objetivo e nível de risco que as organizações estão dispostas a enfrentar para compreender o comportamento do adversário.

O *honeypot* disposto fora do *firewall* externo da organização possibilita rastrear as tentativas de conexão de endereços IPs advindos de fora da rede. Uma das vantagens desta abordagem é que ela não insere nenhum risco para rede interna, ou seja, o perigo de existir um sistema comprometido atrás do *firewall* pode ser reduzido. O *honeypot* disposto nesta localização atrai inúmeros ataques potenciais, ainda reduz a quantidade de alertas emitidos pelo *firewall* e sistemas de detecção de intrusão internos, consequentemente aliviando o processo de gerenciamento. Porém, como desvantagem é que esta abordagem não consegue identificar os atacantes internos, ainda mais se o *firewall* externo estiver configurado para filtrar o tráfego de entrada e saída. Na figura abaixo o *honeypot* está estrategicamente posicionado fora do *firewall* externo.

![[UE7_img8.png]]

Outra posição estratégica para adicionar um *honeypot* é alocar o mesmo dentro da rede DMZ, responsável em fornecer serviços externos (web e e-mail). Neste cenário o profissional de segurança deve garantir que os demais sistemas disponibilizados na rede DMZ estejam seguros contra qualquer tipo de atividade realizada a partir no *honeypot*. Uma desvantagem de posicionar o *honeypot* dentro da DMZ é que esta rede não é totalmente acessível, o *firewall* em geral bloqueia qualquer tráfego quando existe tentativas de acessar serviços que não são necessários. Deste modo, duas abordagens podem ser adotadas para implementação das regras no *firewall*, ou é liberado o tráfego além do que é permitido, contudo sendo uma tarefa meio arriscada, ou então limita-se a efetividade do *honeypot* deixando de analisar totalmente o comportamento do adversário. Na figura abaixo o *honeypot* está estrategicamente posicionado dentro da DMZ.

![[UE7_img9.png]]

Por fim, configurar um *honepot* dentro da rede interna pode conceder algumas vantagens, onde a principal é capacidade de capturar ataques internos. Adicionalmente, o *honeypot** *localizado na rede interna permite detectar um* **firewall* mal configurado. Em contrapartida, existem inúmeras desvantagens, sendo talvez a mais crítica seja que um *honeypot* mal configurado pode ser utilizado para atacar outros sistema internos que sejam legítimos. Neste caso, é necessário observar que qualquer ataque realizado pelo adversário da internet utilizando o *honeypot* o tráfego no *firewall* não será bloqueado - será considerado um tráfego normal direcionado ao *honeypot*. Destaca-se ainda a dificuldade de conceder regras no *firewall* para permitir tráfego até *honeypot*, visto que tais regras tem um potencial de comprometer toda a rede interna.  Na figura abaixo o *honeypot* está estrategicamente posicionado dentro da rede interna.

![[UE7_img10.png]]

## **Explorando os mecanismos de detecção de intrusão**

Este vídeo fornecerá uma visão mais ampla sobre os mecanismos de detecção de intrusão, vamos apresentar como funciona tais ferramentas, quais as vantagens e desvantagens de utilizar estas abordagens, dicas e boas práticas para implementação destes mecanismos de segurança.

## **EXERCÍCIO**

**Exercícios de Fixação**

O que é uma intrusão de segurança?

O que um IDS?

Qual a diferença entre um IDS baseado em rede e baseado em estação?

Quais os elementos fundamentais do IDS? Explique qual sua função.

Qual a diferença entre a arquitetura centralizada e distribuída do IDS?

O que é um NIDS?

O que é um HIDS?

O que é IDS híbrido?

Qual a diferença entre o sensor inline e passivo do NIDS?

Qual a diferença entre a detecção baseado em assinatura e anomalia?

Qual o conceito da intrusão adaptativa, quais ações podem ser adotadas para proteger o sistema?

O que é um Honeypot? Para que ele é utilizado?

## **Conclusão**

Esta unidade abordou os conceitos de intrusão de segurança, vimos que o adversário pode explorar as vulnerabilidades para tentar obter acesso ao sistema e seus recursos. Conforme discutido, a detecção de intrusão é serviço de segurança utilizado para monitorar e analisar os eventos no sistema. Vimos que por meio deste processo é possível alertar o administrador do sistema que estão ocorrendo tentativas de acesso não autorizado ao sistema e seus recursos. Demonstramos que para auxiliar o profissional de segurança da informação existem ferramentas que podem ser utilizadas, são os sistemas de detecção de intrusão (IDS) e os sistemas de prevenção de intrusão (IPS).

Por conseguinte, apresentamos que um IDS pode monitorar uma única máquina ou ainda monitorar todo tráfego de rede. Observamos que um IDS é constituído por três elementos fundamentais o sensor, analisador e interface do usuário, cada um responsável por realizar uma determinada tarefa. Ainda, mostramos que os IDS podem ser classificados conforme as técnicas que são utilizadas para detectar o ataque, então apresentamos os sistemas baseados em regras e os sistemas adaptáveis. Demonstramos também que o IDS pode ser estruturado por meio de uma arquitetura centralizada ou distribuída.

Exploramos também três tipos de IDS, os sistemas de intrusão baseado em rede (NIDS), os sistemas de intrusão baseados em hosts (HIDS) e os IDS híbridos. Conforme discutido, os NIDS examinam os pacotes que foram transmitidos para tentar identificar pacotes que se assemelham com os padrões de assinaturas correspondente a uma intrusão no sistema. Ainda, mostramos que o HIDS analisa informações obtidas de computadores individuais, verificando as atividades e os acessos que estão sendo realizados no servidor para identificar ataques intrusão. Adicionalmente, abordamos o IDS Híbrido, verificamos que este consiste em uma abordagem estruturada da combinação de um HIDS com um NIDS.

Ainda, foi apresentado que o IDS baseado em Host pode trabalhar basicamente de duas maneiras, a partir da detecção de anomalia ou por assinatura. Conforme discutido, na detecção de anomalia é analisado o comportamento do usuário legítimo para identificar um determinado padrão, posteriormente são realizados testes estatísticos para determinar o comportamento diferentes dos usuários legítimos. Conhecemos também a abordagem baseada em assinatura, vimos que nesta abordagem é definido um conjunto de regras a partir da identificação de padrões de ataque, na sequência tais regras podem ser utilizadas para detectar um comportamento de intrusão.

Por fim, demonstramos que com o passar dos anos os ataques de intrusão foram evoluindo, no mesmo sentido abordagens para tratar tais ataques acabaram sendo necessárias. Verificamos que intrusão adaptativa e sistemas distribuídos podem cooperar entre si para identificar intrusões. Conforme observamos tais sistemas possuem a capacidade de adaptar-se a perfis de ataques mutáveis. Adicionalmente, apresentamos o *Honeypot* uma ferramenta que permite analisar o comportamento do adversário visando identificar aspectos que devem fortalecidos nos sistemas. Por último, discutimos sobre os desafios do profissional de segurança da informação para proteger os sistemas contra os ataques de intrusão, destacamos a importância das ferramentas detecção de intrusão para preservar dos sistemas de recursos da organização.

## **Software Malicioso**

*Nesta Unidade, iremos estudar os softwares maliciosos. Será abordado como os adversários exploram as vulnerabilidades dos sistemas a partir de rotinas de códigos maliciosas. Será discutido as principais razões que motivam o adversário a desenvolver e a propagar rotinas de código malicioso. Na sequência, vamos apresentar quais são os principais tipos de malwares, como que eles atuam e se propagam. Conhecer os elementos estruturais de malware; qual a diferença entre um **vírus** e um **worm**; descobrir a relação entre os **botnets** e ataques de negação de serviço; conhecer os **spyware**, como os adversários utilizam este recurso para obter acesso a informações confidenciais do usuário tais como login, senha, número de cartão de créditos; como o adversário utiliza um **backdoor** para permitir retornar a um sistema que foi invadido; quais os diferentes tipos de **Trojan** e como são disseminados; por que devemos estar atentos contra ataques de **ransomware**. Adicionalmente, demostrar os golpes e ataques que são realizados pelos adversários utilizando tais rotinas de código maliciosas. Mas sobretudo, apresentar como profissional da área de segurança pode atuar para se proteger contra essas ameaças.*

## **Software Malicioso**

Os softwares maliciosos são programas desenvolvidos para realizar alguma atividade maliciosa no computador. Os códigos maliciosos também conhecidos pelo termo inglês "malware", em geral realizam ações prejudiciais e nocivas ao sistema. Entre as principais formas que o malware pode infectar uma máquina, podemos destacar:

- Explorar vulnerabilidades existentes no sistema operacional ou programas instalados;
- Utilização de mídias removíveis infectadas, tais como HD externo, pendrives e cartões de memória, em geral a infecção realizada pelo “auto-execução” dos dispositivos;
- Acesso a sites maliciosos, uso de navegadores vulneráveis;
- Realizada por meio da ação direta do adversário após invadir o sistema, adicionam arquivos contendo códigos malicioso para poder retornar a máquina que já foi invadida;
- Execução de arquivos infectados, obtidos em anexos de e-mail, mídias externas (removíveis), páginas web ou ainda disseminado na rede por outro computador que compartilha o mesmo recurso.

O código malicioso ao ser instalado passa a ter acesso aos dados armazenados na máquina e podem executar processos em nome dos usuários legítimos, utilizar os recursos de acordo com as permissões definidas para cada usuário.

![[UE8_img1.jpeg]]

Fonte: ©James Thew/Adobe Stock

As principais razões que motivam o adversário a desenvolver e a propagar rotinas de código malicioso são a tentativa de obter vantagens financeiras, ter acesso informações confidenciais, vandalismo ou apenas pelo propósito de se autopromover. Além do mais, os malwares muitas vezes podem ser utilizados em tarefas intermediárias que possibilitam realizar golpes, ataques, disseminação de spam ou outras atividades de fins maliciosos.

## **Tipos de Malware**

Os termos utilizados para classificar malwares na área de segurança talvez sofram um problema em relação a estabelecer uma nomenclatura que seja de concordância universal para todos os termos, dado que existe algumas das categorias de malware que se sobrepõem, ou seja, existem diversos malwares que estão dentro de mais de uma família.

Embora existam diversos aspectos que podem ser avaliados para classificar um malware, uma abordagem bastante aceita pelos profissionais da área é classificar o malware em duas categorias gerais, primeiramente avaliando o modo como este malware se propaga (como que ele contamina suas vítimas), posteriormente baseado nas ações ou cargas úteis que são executadas quando o malware contamina seu alvo. Os termos apresentados abaixo denotam um comportamento específico de cada uma das famílias de malware, reforçando que um único malware pode ser classificado em mais de uma família

### **Vírus**

Um vírus é um programa escrito como uma rotina de código malicioso, que se propaga na rede e nos computadores efetuando cópias de si mesmo e se inserindo como parte de outros programas e arquivos. Para que o vírus consiga entrar em atividade no processo de infecção, esse necessita que o programa ou arquivo hospedeiro seja executado, deste modo, para que o computador seja infectado é necessário que um programa que contenha uma carga de código malicioso seja executado.

Existem diferentes meios de propagação do vírus, sendo os mais comuns a disseminação por meio de e-mails, acesso a sites contaminados ou ainda pelo uso de mídias externas, tais como pendrives, disco externo ou cartões de memória.

![[UE8_img2.jpeg]]

Fonte: ©Weissblick/Adobe Stock

Existem diferentes tipos de vírus, podendo ser classificados conforme seu comportamento. Uma grande maioria dos vírus procura manter-se ocultos, infectando os arquivos do disco e realizando várias atividades sem o conhecimento e consentimento dos usuários da máquina. Alguns vírus para se camuflar permanecem inativos por um determinado período, então entram em atividade em uma data estipulada. Entre os principais vírus mais comuns, podemos citar:

- **Vírus propagado por e-mail:** programa malicioso anexado como arquivo em e-mail, o adversário tenta induzir o usuário a clicar em um arquivo contaminado, fazendo que o programa seja executado. Quando esse programa é executado ele infecta os arquivos e programas do computador reproduzindo cópias de si e enviando e-mails contaminados para lista de contatos do usuário.
- **Vírus de script****:** é uma rotina de código malicioso escrita em uma determinada linguagem script, em geral carga maliciosa descarregada no computador ao acessar uma determinada página Web, podendo ainda ser enviado por e-mail como anexo de arquivo ou ainda como parte do próprio e-mail quando o e-mail é estruturado no formato HTML. Dependendo da configuração do navegador ou do cliente de e-mail o script pode ser automaticamente executado.
- **Vírus de macro****:** este é um tipo específico de vírus de script, escrito em linguagem de macro utilizado, infectam arquivos dos aplicativos que utilizam tal linguagem - arquivos Microsoft Office como Excel, Word e Power Point.
- **Vírus de dispositivos móveis****:** como o aumento do uso dos dispositivos móveis o adversário tem explorado os vírus que se propagam pelo celular, principalmente com a adoção dos smartphones. Esses vírus podem ser disseminados em lojas de aplicativo, também presente nas diferentes plataformas, em destaque no Android e iOS. Ainda, pode se propagar por meio da tecnologia bluetooth, mensagens SMS (Short Message Service) ou mensagens MMS (Multimedia Message Service). O dispositivo é infectado geralmente quando o usuário permite o recebimento de um determinado arquivo infectado e passa a executá-lo. Então o vírus após infectar o aparelho ele pode modificar o comportamento do aparelho, destruir e sobrescrever arquivos do sistema, ainda remover ou transmitir contatos da agenda do usuário, realizar ligações telefônicas utilizando o número do usuário. O vírus ao infectar um aparelho irá tentar se reproduzir (gerar cópias de si mesmo) e se propagar para outros dispositivos.

**CURIOSIDADE**MMS - Serviço de Mensagens Multimídia é um padrão de envio de mensagens que incluem conteúdo multimídia para o telefone celular em uma determinada rede.

### **Worm**

O worm é um programa malicioso que possui a capacidade de se propagar automaticamente pelas redes, enviando cópias de si próprio para outros computadores na rede. Tal programa também é conhecido como "verme" referente a tradução do termo worm para o português. O worm se distingui de um vírus pelo meio de propagação, um Worm não se propaga por meio de inserção de cópias contaminando programas e arquivos, esse se reproduz pela execução direta de suas cópias, então explora vulnerabilidades nos sistemas e nos programas instalados para poder se disseminar.

![[UE8_img3.jpeg]]

Fonte: ©andriano_cz/Adobe Stock

Ressalta-se que este malware é responsável por consumir uma grande quantidade de recurso, dado que existe uma grande quantidade de cópias que costumam se disseminar, comportamento que pode impactar no desempenho da rede e da utilização dos computadores. O ciclo de propagação do worm ocorre da seguinte maneira:

1. **Identificação dos alvos****:** assim que um computador é infectado o worm tenta se propagar, para atingir este objetivo o worm precisa identificar os computadores alvos para replicar suas cópias. Nesse processo o worm pode realizar uma das seguintes ações:

- Realizar uma busca na rede para identificar computadores ativos;
- Aguardar que seja realizado a conexão de outros computadores com o computador infectado;
- Fazer uso de listas predefinidas contendo a identificação dos alvos;
- Utilizar informações extraídas do computador infectado, arquivos de configuração e listas de endereços de e-mail.

1. **Envio de cópias:** o worm após identificar os alvos realiza a cópia de si mesmo, então passar a enviar estas cópias a seus alvos, utiliza uma das seguintes maneiras para transmitir as cópias:

- Explorando vulnerabilidades existentes dos computadores alvos;
- Transmitido via programas de troca de mensagens instantâneas;
- Transmitida por meio de anexo de e-mail;
- Transmitida utilizando canais IRC (Internet Relay Chat);
- Utilizando pasta de compartilhamento P2P (Peer to Peer);
- Disseminadas via torrent.

1. **Ativação das cópias: **após o processo de envio da cópia é necessário o worm seja executado para que a infecção aconteça, esta ação pode ser realizada de uma das seguintes formas:

- O worm pode ser executado imediatamente após ser transmitido, ação realizada pela exploração de vulnerabilidades em programas sendo executados no computador no instante que o malware é recebido.
- Pode ser executado diretamente pelo usuário por meio da execução das cópias que são enviadas para o seu computador.
- Aguardar uma ação do usuário, por exemplo esperar que o usuário insira uma mídia de armazenamento externo, por exemplo: contaminar um pendrive assim que ele for adicionado no computador.
36. **Reinício do processo:**** ** Para manter o ciclo de propagação, logo após o alvo ser infectado o processo de infecção recomeça, porém neste caso, o computador que anteriormente era o alvo, passa também a realizar o mesmo ataque.

### **Bot e Botenet**

Um bot é um programa malicioso que possui um mecanismo de comunicação que permite que o adversário consiga controlar o computador infectado remotamente. Este malware dissemina-se de forma similar a um worm, tem a capacidade de se propagar de forma automática, este também explora vulnerabilidades existentes no computador alvo.

A comunicação do adversário com o host infectado pelo bot, pode ser realizada de diferentes modos, utilizando canais de IRC, por meio de servidores web e ainda torrent e redes P2P, entre outras maneiras. O adversário ao se comunicar com o bot pode enviar instruções solicitando que sejam realizadas ações maliciosas, realizar ataques, roubar dados e enviar spams.

Uma máquina infectada por um bot é denominada computador zumbi, dado que pode ser controlada remotamente sem que haja conhecimento do proprietário do hardware. A variante do malware bot que utiliza a máquina hospedeira como servidor de e-mails é denominada como spam zumbi.

![[0de99dde7c861d9583927ae0387e9ce4b34d45ca.jpg]]

Fonte: ©nicescene/Adobe Stock

Um conjunto de máquinas infectadas por um tipo de bot é denominada botnet. As Botnets são formadas por milhares de computadores zumbis, isto permite que o adversário intensifique seus ataques. Assim, quanto maior for a quantidade dos computadores zumbis na botnet mais potente é o ataque realizado. O adversário além de utilizar as botnet para realizar seus próprios ataques, ainda fornecem serviços na Deep Web, alugam as botnets para grupos ou pessoas que desejam executar uma ação maliciosa específica.

**CURIOSIDADE***Deep Web* - termo que se refere a todas as páginas da Web que os mecanismos de pesquisa não conseguem identificar.

Entre as principais ações maliciosas que são realizadas por meio das botnets podemos destacar: Ataques de negação de Serviço (DoS), propagação de malware, coletar informação de uma quantidade expressiva de computadores, envio de spam e camuflar a identidade real do adversário - a origem dos ataques é realizada em computadores de terceiros, o uso de proxy instalado na estação zumbi permite que atacante esconda sua identidade (endereço IP). Basicamente o funcionamento básico de uma botnet pode ser estruturado nas seguintes etapas:

1. O adversário dissemina um tipo específico de bot com o objetivo de infectar o maior número possíveis de computadores;

1. Os computares infectados (zumbis) ficam a disposição do adversário, ficam inativos aguardando uma ação do adversário (comandos a serem executados);

1. Quando o adversário deseja realizar uma determinada ação então envia aos zumbis os comandos que deverão ser executados;

1. Os zumbis ao receber a requisição do adversário, executam os comandos que foram enviados.

37. A finalizar esta ação os computadores zumbis retornam a ficar inativos aguardando a próxima sequência de comandos que deverá ser executada.

### **Spyware**

O *Spyware* é um programa malicioso utilizado para espionar as atividades de um sistema, posteriormente envia as informações coletadas para o adversário. Este programa compromete a privacidade dos usuários e a segurança do computador, podem monitorar e capturar informações referentes a navegação do usuário ou informações inseridas em outros programas que despertem o interesse do adversário, por exemplo login e senha. Existem diferentes tipos de spyware, classificados conforme seu comportamento, destacam-se os principais:

- **Keylogger**: este programa permite capturar as teclas que foram digitadas no teclado do computador. Utilizada principalmente para obter as credenciais dos usuários, tais como login e senha.
- **Screenlogger****:** este programa, programa captura a posição do cursor do mouse e realiza um printscreen da tela, apresenta a região na tela onde o mouse foi clicado. Este programa é bastante utilizado pelo adversário para tentar capturar as teclas digitadas pelos usuários em teclados virtuais, tais como os teclados disponíveis pelos sites de Internet Banking.
- **Adware****:** este programa é projetado especificamente para apresentar propagandas. Quando usado para fins maliciosos as propagandas apresentadas são direcionadas, de acordo com a navegação realizada pelo usuário, ou seja, sem efetivamente o usuário saber que está sendo monitorado.

### **Backdoor**

O backdoor é um programa malicioso que permite que um intruso abra uma porta no sistema para que consiga retornar no computador que foi comprometido, para isto o adversário insere serviços criados ou modificados para este fim. As rotinas de código malicioso backdoor podem ser inseridas por meio da ação de outros malwares, que tenham previamente infectado o computador, ou ainda por atacantes que exploram as vulnerabilidades dos sistemas ou programas existente no computador a fim de invadi-lo.

Com adição da rotina de backdoor o adversário consegue garantir uma maneira de acessar futuramente o computador comprometido, permitindo o acesso remoto sem a haver a necessidade de realizar novamente os métodos de invasão ou infecção. A maneira convencional utilizada pelo intruso para adicionar um backdoor consiste em adicionar um novo serviço ou substituir um serviço que esteja rodando por uma versão modificada do programa, normalmente incluindo recurso que possibilitam um acesso remoto.

Os programas de acesso remoto se mal configurados ou usados sem que haja o consentimento dos usuários também podem ser considerados um tipo de backdoor, um exemplo típico é o programa de conexão remota VNC. Existem alguns casos de backdoors inseridos de forma proposital por fabricantes de software, justificam sob o pretexto de necessidades administrativas, Tais casos constituem uma séria ameaça à segurança de computador que possua um desses programas instalados, sendo que além de afetar a privacidade do usuário, também podem ser explorados pelo adversário em tentativas de acesso remoto.

### **Trojan**

O trojan também conhecido como “Cavalo de Tróia”, é um programa malicioso que além de executar as funções que teoricamente foi projetado para realizar, adicionalmente executa outras funções, em geral maliciosas, sem que haja conhecimento e consentimento de seus usuários.

Os trojans tipicamente são distribuídos em grande escala em sites onde é realizado downloads alternativos de programas licenciados que são “crackeados” e estão sendo fornecidos de maneira gratuita, também podem ser inseridos em fotos, vídeos, jogos, entre outros. Tais programas em geral são estruturados em um único arquivo e exige que sejam executados explicitamente para que sejam instalados na máquina.

![[UE8_img5.jpeg]]

Fonte: ©Alexander Limbach/Adobe Stock

Os trojans podem ainda ser instalados pelos adversários, após invasão de uma estação, o intruso pode alterar um programa já existente para que além de executar as funções originais do programa, ele ainda executa determinadas ações de caráter malicioso. Existem vários tipos de trojans, em geral são classificados de acordo com as ações maliciosas que executam no computador ao infectá-lo, entre os principais tipos podemos citar:

- ***Trojan Downloader***: este programa instala outros softwares maliciosos hospedados em determinados servidores na Internet.
- ***Trojan Dropper***: este programa instala outros softwares maliciosos que estão embutidos no próprio código dentro do trojan.
- ***Trojan Backdoor***: este programa é utilizado para inserir rotinas maliciosas de backdoors, tais programas possibilitam o acesso remoto do adversário na máquina.
- ***Trojan DoS***: este programa instala ferramentas utilizadas para ataques de negação de serviço, são utilizadas para desferir um ataque.
- ***Trojan Destrutivo******:*** este programa tem como objetivo deixar o computador fora de operação, para isto ele modifica e exclui arquivos e diretórios, ainda pode formatar determinadas partições do disco.
- ***Trojan Clicker******: ***este programa redireciona as páginas sendo navegadas pelo usuário, acaba direcionando o usuário a alguns sites específicos, tem como finalidade aumentar a quantidade de acessos a esses sites ou ainda apresentar propagandas.
- ***Trojan Proxy******:*** este programa instala um servidor de proxy, permitindo que o computador infectado seja utilizado para navegação anônima ou envio de spam.
- ***Trojan Spy******:*** este programa instala uma rotina de código maliciosa spyware, posteriormente este código é utilizado para coletar informações sensíveis dos usuários, tais como senhas e números de cartão de crédito, para na sequência enviar tais informações para os criminosos.
- ***Trojan Banker******:*** este programa permite coletar dados bancários dos seus usuários, por meio de programas que são ativados quando os sites de Internet Banking são acessados. O comportamento deste Trojan é bastante similar ao Trojan Spy, porém neste caso possui um objetivo mais específico.

### **Ransomware**

O ransomware é um tipo de malware que sequestra o computador das vítimas. Em geral, este malware criptografa os dados armazenados em um equipamento, então exige um pagamento de resgate para restabelecer o acesso ao usuário, é comum que o adversário solicite o pagamento utilizando moedas virtuais, tais como bitcoin, dado a características de não serem rastreáveis. Este tipo de "vírus sequestrador" age codificando os dados do sistema operacional de forma com que o usuário não tenha mais acesso.

Uma vez que algum arquivo do sistema operacional esteja infectado, o malware codificará os dados do usuário, tarefa que é realizada em segundo plano, sem que o usuário perceba, então quando tudo estiver pronto, o malware emiti um aviso informando que o computador foi bloqueado e que o usuário não poderá mais utilizá-lo. Então, o malware solicita o resgate, solicitando que o usuário pague o valor de resgate exigido para obter a chave que dá acesso novamente aos seus dados.

![[UE8_img6.jpeg]]

Fonte: ©Andrey Popov/Adobe Stock

Destaca-se a dificuldade na detecção de um ransomware e seus disfarces, fatores que os tornam mais perigosos. Este malware pode infectar o computador de diversas maneiras, através de sites maliciosos, links suspeitos por e-mail, ou instalação de aplicativos vulneráveis. O ransomware também pode aparecer em links enviados em redes sociais, atualmente um meio muito utilizado para espalhar diferentes malwares.

Uma vez que o computador esteja infectado, é muito difícil realizar a remoção do ransomware, principalmente porque o usuário não consegue nem mesmo acessar o sistema. Deste modo, toda ação preventiva é bem-vinda. Conforme as melhores práticas, a estratégia é manter o antivírus sempre atualizado e fazer buscas regulares no sistema operacional atrás de malware, para que o malware seja detectado antes de ser ativado.

É necessário ter sempre backups atualizados de suas informações e arquivos, caso precise formatar o computador que esteja infectado, esta estratégia vai garantir que você não perca nenhum arquivo importante. As mesmas ações adotadas para se precaver de outros malwares também são válidas para se afastar de um ransomware, nunca clique em links de SPAM em e-mails, sempre desconfie de links e vídeos supostamente enviados por amigos nas redes sociais. Caso não seja comum tal pessoa enviar este tipo de conteúdo, certifique-se com a pessoa antes de clicar em tal conteúdo. Não baixe arquivos de torrents ou sites suspeitos e instale apenas programas baixados de sites confiáveis.

## **Classificação de Malware**

Existem diferentes maneiras de classificar um malwares, conforme já mencionado não existe um consenso universal para classificar os malwares, porém existem algumas propostas. A classificação mais comum dos malwares é obtida pelo seu modus operandi, ou seja, seu comportamento em execução, o que o malware faz e como ele se replica. Este tipo de classificação não está isento de sobreposição, descarta-se ainda que muitas vezes as diferenças entre os malwares também não são tão fáceis de identificar.

**CURIOSIDADE**Modus operandi - expressão em latim que significa "modo de operação" traduzido para língua portuguesa.

Outra abordagem que também é bastante difundida é classificação do malware a partir da sua taxonomia. A taxonomia é a ciência da identificação. Observando que pode não existir uma única classificação para os malwares, e ainda dificuldade em diferenciar as famílias de malware esta abordagem pode ser utilizada. Contudo, ainda sim possui enfrenta alguns desafios, esta abordagem não será capaz de tratar os casos de classificação que o malware sofre mutações.

Em vista disto, surgem abordagens secundárias para classificação, algumas propõem classificar o malware pela maneira que ele se propaga, outros autores defendem a ideia de classificar o malware pela necessidade ou não do um hospedeiro. Contudo, os códigos maliciosos podem possuir características advindas de mais de um tipo de família. Deste modo, ressalta-se a classificação de malware mais adequada deve considerar as diferentes características do malware. Assim, atualmente os fabricantes de soluções de antivírus tem agrupado os malware conforme suas características elementares, sendo que muitas vezes um código malicioso do malware é derivado de outro é possível organizá-los em determinadas famílias.

Conforme Caldas [Caldas,2016] grande maioria dos trabalhos publicados na área de classificação de malware hoje visa classificar amostras de malware entre famílias. Destaca-se que o conceito de classificação baseado em família se difere do tradicional, onde o malware deve ser classificado em uma determinada classe. Na classificação baseado em família de malware é realizado o agrupamento de amostras de malwares que implementam as mesmas funcionalidades no código fonte, ou que possuem semelhanças estruturais [Caro, 2016]. Tais amostras são denominadas de variantes do malware.

## **Mecanismo de Propagação**

Os mecanismos de propagação podem atuar por infecção de conteúdo executável existente ou ainda ser exposto por um vírus, utilizado para disseminar o malware para outros sistemas. Os malware podem explorar vulnerabilidades dos softwares instalados na máquina ou também por meio da rede, um exemplo típico worms ou drive-by downloads. Ainda, os adversários podem utilizar ataques de engenharia social, onde convencem os usuários desativar os mecanismos de segurança para instalar algum Trojan ou responder a algum ataque de phishing.

**CURIOSIDADE***Drive-by downloads *- download não autorizado e sem o conhecimento do usuário para permitir a reprodução do malware*.*

![[UE8_img7.jpeg]]

Fonte: ©sitthiphong/Adobe Stock

Uma das principais categorias de propagação de malware utiliza fragmentos de código malicioso que se ligam com algum conteúdo executável existente. Este fragmento pode ser algum trecho de código de máquina que infecta a aplicação, utilitário ou até mesmo programa do sistema existente. Este código em geral é adicionado junto a rotina que inicializam automaticamente junto com os programas do sistema operacional. Existem diversos fragmentos que são escritos em forma de scripts, também utilizados para utilizados para fornecer suporte a conteúdo ativo dentro de dados, tais como documentos no formato Word, Excel, Power Point ou PDF.

A carga útil do código malicioso, também denominada como payload, quando executada no sistema ela realiza as atividades a qual foi projetada, podendo incluir corrupção dos arquivos de dados ou sistema; atuar como agente zumbi em ataques, fazer parte de uma botnet; realizar o furto de informações confidenciais dos usuário e do sistema, entre os mais visados  o login, senha e número de cartão de crédito, onde em geral o adversário utiliza um software spyware; e ainda estratégias de camuflagem, onde o malware tenta ocultar sua presença no sistema contra ferramentas de segurança como o antivírus utilizado para detectar e bloquear os malwares.

No decorrer do tempo, houve uma evolução no desenvolvimento de código malicioso, sendo observado um crescimento na quantidade de malware mistos, onde o malware incorpora vários mecanismos de propagação e cargas úteis, o que aumentam sua capacidade de disseminação, camuflagem e capacidade de execução (ações que podem ser realizada contra seus alvos) os alvos.

Uma tentativa de ataque utilizando um malware contendo uma carga maliciosa mista utiliza vários métodos de infecção ou propagação para maximizar a velocidade de contágio e a gravidade do ataque. Existem até mesmo alguns malwares que possuem um mecanismo de atualização, permitindo que o malware sofra uma mutação, tanto na forma de atuar como também na propagação.

Entre os comportamentos de propagação dos malwares mais notórios, destaca-se o vírus de computador que acaba sendo expirado em vírus biológicos entrado na natureza. Um vírus de computador possui um conjunto de instruções que permitem realizar uma cópia integra de si mesmo. Este vírus em geral fica embutido em um programa, ou elemento portador de conteúdo executável no computador. Então, sempre que o computador infectado entra em contato com algum trecho de código que ainda não esteja infectado, uma cópia integra do vírus é realizada passando a ser copiado para o novo local. Deste modo, ocorre a proliferação do vírus de um computador para outro.

Um determinado vírus que se insere em um programa executável pode realizar qualquer ação que o programa hospedeiro tenha permissão de realizar. Este executa de maneira oculta assim que o programa hospedeiro é executado. Uma vez que o vírus esteja em execução, o código irá realizar as funções para qual foi projetado, qualquer função que seja permitida pelos privilégios fornecidos pelo usuário corrente (permissões de leitura, escrita e execução), podendo até mesmo excluir arquivos e programas. Alguns pesquisadores na área de segurança direcionados ao estudo dos malwares afirmam que um vírus de computador possui três partes [Aycock, 2006]. De forma ampla, muitos dos tipos de malwares atuis incluem um ou mais variantes de cada um dos seguintes componentes:

- Mecanismo de infecção: componente de código malicioso responsável pela disseminação do vírus, como vai ser propagado e espalhado entre os computadores, ou seja, contempla a atividade de reprodução do malware. Este mecanismo também chamado de vetor de infecção.
- Carga útil: este componente contém o código malicioso que efetivamente vai realizar a atividade malicioso, principal atividade do malware que foi projetada pelo adversário - intenção de tirar vantagens ou causar algum dano.
- Mecanismo de ativação: este componente corresponde a um código malicioso que fornece um gatilho para que o processo do vírus entre em execução, em geral um evento ou condição que vai ativar a carga útil do malware, este componente também é conhecido como "bomba lógica".

A grande parte dos vírus que infectam os arquivos de programas executáveis realizam sua atividade de forma específica, projetado para atingir um sistema operacional em particular, podendo também ser projetado para atacar uma plataforma de hardware especifica. Tal como o exemplo do Stuxnet, um worm que foi projetado especificamente para atacar o sistema operacional SCADA da Siemens, foi utilizado como arma cibernética para controlar as centrífugas de enriquecimento de urânio iranianas, onde foram danificadas cerca de 1000 centrífugas [Kaspersky,2014]. Destaca-se que em geral os malware são projetados para tirar proveito dos detalhes e fraquezas dos sistemas específicos. Porém, existem uma classe de vírus de macro que permite explorar determinados documentos específicos, tais vírus foram projetados para atuar em diferentes sistemas operacionais.

## **Exploração de Vulnerabilidades**

A exploração de vulnerabilidades é uma técnica amplamente explorada pelos worms. O worm é um programa malicioso que busca ativamente contaminar cada vez mais máquinas, onde cada máquina contaminada serve como meio de disseminação para novos ataques a outras máquinas.

Os worms são projetados para explorar vulnerabilidades de softwares, tanto programas clientes como servidores, deste modo conseguem ter acesso a novos sistemas. Ainda, podem utilizar conexões de rede para percorrer de sistema para sistema e se disseminar entre mídias compartilhadas. Os worms de e-mail conseguem se espalhar em códigos scripts ou macro, em geral inseridos em documentos anexados em e-mail ou por meio de transferência de arquivos via mensagens instantâneas.

![[UE8_img8.jpeg]]

Fonte: ©James Thew/Adobe Stock

O worm quando ativado, pode se reproduzir e se propagar novamente. Além de se propagar, o worm também é munido de alguma forma de carga útil maliciosa, como as que discutiremos mais adiante. Para se replicar o worm explora algumas estratégias e vulnerabilidades para conseguir acessar o sistema remotamente. Entre as principais desacatam-se os exemplos a seguir:

- **Recursos de e-mail ou de mensagem instantânea:** Um worm envia por e-mail uma cópia integra de si mesmo para outros sistemas, bastante comum que seja enviado como anexo, ainda pode ser enviado utilizando um serviço de mensagens instantâneas (utilizando um chat ou até por meio de aplicativos como Telegram ou Whatsapp), o código pode ser executado quando o e-mail ou o anexo é recebido ou visualizado.
- **Compartilhamento de arquivo****: **o worm cria uma cópia de si mesmo ou infecta outros arquivos em mídia externa removível, por exemplo um dispositivo USB como um pendrive ou HD externo, então quando este dispositivo for conectado e executado em outro sistema, possivelmente outro computador será infectado. Ao ser disseminado na máquina o worm vai tentar explorar vulnerabilidade de software.
- **Capacidade de execução remota****: **o worm pode executar uma cópia de si mesmo em um outro sistema utilizando um recurso explícito de execução remota ou também explorando alguma falha de programação em um determinado serviço em rede para poder realizar suas ações.
- **Capacidade de acesso/transferência de arquivos remotos****: **o worm pode utilizar um serviço de acesso remoto de compartilhamento de arquivos ou ainda pela transferência de arquivos remotos para outro sistema, deste modo o malware faz uma cópia de si mesmo e envia de um sistema para o outro, de maneira que os usuários do outro sistema sejam infectados.
- **Capacidade de login remoto****:** O worm pode acessar um sistema remotamente com as credenciais de um determinado usuário, então pode executar determinados comandos que irão permitir que seja realizado uma cópia de si mesmo para outro sistema. O worm vai explorar as vulnerabilidades do sistema para executar sua carga útil e continuar a se propagar.

Outra abordagem utilizada pelos adversários para explorar vulnerabilidades em softwares, envolve a exploração de bugs em aplicações comuns do usuário, utilizadas para instalar um malware.

Uma estratégia bastante comum é explorar as vulnerabilidades em um navegador Web, o adversário pode controlar o navegador, assim que o usuário abrir uma página Web, um código malicioso será executado no navegador permitindo que seja explorado um bug. Esta ação irá permitir baixar e instalar um malware no sistema sem haver o conhecimento ou consentimento do usuário. Esta é uma técnica conhecida como download não autorizado, um exploit comum que atualmente vem sendo disponibilizadas em ferramentas de ataques recentes. Em geral, este malware não se propaga de forma ativa como um worm, ao contrário este malware aguarda que o usuário sem suspeitar visite a página maliciosa para que ele possa infectá-lo.

**CURIOSIDADE**Exploit - é um conjunto de intrusões, dados ou software elaborados por "hackers" para tirar proveito de um defeito ou vulnerabilidade do sistema.

Existem outras variantes que exploram bugs em clientes de e-mail comuns, alguns worms realizam o envio de e-mails em massa, permitindo a execução automática de si mesmo. Entre outras vulnerabilidades em bugs de software, os malwares também visavam leitores de PDF, permitindo baixar e instalar malware sem consentimento do usuário, quando o usuário abria o documento PDF contendo a rotina de código malicioso. Ainda, tais documentos eram espalhados por e-mail através spam ou a partir de ataques de phishing.

## **Engenharia Social**

Engenharia social consiste na técnica no qual o adversário procura persuadir um usuário legitimo a realizar uma determinada ação. Para o nosso contexto, consideraremos com sendo a prática utilizada por golpistas para explorar a ingenuidade e confiança de outras para lhes aplicar golpes cibernéticos, obtendo vantagem financeira ou informações sigilosas.

Em geral, atacar e fraudar os dados em um servidor de uma instituição bancária ou financeira não é uma tarefa simples, devido a isto, golpistas concentram-se seus esforços em explorar a fragilidades dos usuários. Deste modo, técnicas de engenharia social são aplicadas, utilizando os mais diferentes meios e discursos, desta forma o golpista procura enganar e convencer potenciais vítimas a fornecerem informações sensíveis ou a realizar ações, tais como executar um determinado código malicioso ou então acessar um páginas falsas ou com algum conteúdo com código malicioso.

![[UE8_img9(1).jpeg]]

Fonte: ©oz/Adobe Stock

Posteriormente, tendo posse dos dados de suas, o adversário costuma realizar transações financeiras, acessar sites utilizando as credenciais de suas vítimas, enviar mensagens eletrônicas em nome das vítimas (e-mail ou whatsapp), abrir contas bancárias ilegítimas ou até mesmo empresas fantasmas, entre muitas outras atividades realizadas pelos golpistas. Muitos dos crimes que são realizados pela internet pode até mesmo serem tipificados como crimes realizados contra o patrimônio, nos quais acabam sendo tipificados como crime de estelionato. Abaixo é apresentado alguns dos principais golpes que são realizados na internet:

- **Furto de identidade**: caracterizado como a ação pelo qual uma pessoa tenta se passar por outra, utilizando uma falsa identidade, tendo como o objetivo obter vantagens indevidas.
- **Fraude de antecipação de recursos**: está fraude é realizada quando o um golpista induz a vítima a fornecer informações confidenciais, ou então realizar um pagamento adiantado, iludindo a vítima com a promessa receber certo benefício por isto.
- **Phishing**: esse tipo de fraude o adversário tenta obter dados pessoais e financeiros das suas vítimas, em geral combinam técnicas de engenharia social em conjunto com recursos tecnológicos.
- **Golpes de comércio eletrônico**: neste golpe os adversários têm objetivo de obter vantagens financeiras, então exploram a relação de confiança existente entre as partes envolvidas em uma determinada transação comercial.
- **Boatos**: também conhecido com Hoax, é caracterizado como uma mensagem que possui um conteúdo alarmante falso, em geral tem como remetente uma instituição bastante conhecida - uma empresa bem-conceituada ou até mesmo um órgão do governo. Analisando o conteúdo da mensagem normalmente é possível identificar informações não fundamentadas e tentativas de golpes.

## **Corrupção do Sistema**

Uma das grandes preocupações após um malware ser ativa está relacionado a quais ações este malware poderá realizar no sistema, ou seja, qual é a carga útil que ele carrega. Existem exemplares de alguns malwares que não possuem uma carga funcional, a carga útil é inexistente, projetado apenas com a finalidade de disseminar. Porém, a grande maioria dos malwares contém uma carga útil nociva e executam ações secretas e maliciosas para o adversário.

Os primeiros exemplares de vírus e worms continham uma carga útil que destruía os dados no sistema infectado quando determinadas condições eram satisfeitas. Sendo que existem diferentes tipos de malwares, cada um dispõem de sua própria carga útil, deste modo podemos ter cargas úteis distintas. Podemos citar por exemplo a carga útil relacionada, essa carga quando ativada apresenta mensagens ou conteúdos indesejados aos usuários dos sistemas. Contudo, existem outras variantes de cargas úteis que são bastante perigosas que acarretam danos ao sistema no mundo real.

Destaca-se que grande parte das ações realizadas pelos malware visam a integridade de software ou hardware do sistema computacional, bem como os dados dos usuários. Normalmente as mudanças não ocorrem de forma imediata, em geral são executadas quando determinadas condições acabam sendo satisfeitas em código malicioso (código correspondente a bomba lógica).

Existem malware que foram intencionalmente projetados para destruir dados, conforme mencionado anteriormente, existe um tipo de malware que cifra os dados do usuário e solicitam pagamento para que a chave criptográfica necessária para recuperar os dados seja fornecida, os malware conhecidos como ransomware. Esse tipo de malware possui uma carga útil bastante nociva, o que gera uma grande preocupação para os profissionais que atuam na área de segurança da informação.

Ainda, outra variante de cargas úteis que gera grande preocupação são aquelas cargas que foram projetadas para corromper o sistema, causando até mesmo danos ao equipamento físico. Para o atacante um sistema infectado é sem dúvida um dispositivo mais fácil de invadir. Existem determinado vírus, conhecido como Chernobyl que além de corromper os dados, ele ainda consegue reescrever o código do SETUP, também conhecido como BIOS, programa utilizado para inicializar um computador. Este ataque quando bem-sucedido prejudica o processo de inicialização (boot) do computador, o sistema falha na inicialização, onde para correção do problema é necessário reprogramar o chip da BIOS (gravar o chip novamente) ou substituí-lo fisicamente.

Ressalta-se que o componente fundamental do malware de corrupção de dados é a bomba lógica. A bomba lógica é caracterizada como código malicioso que em determinadas condições é ajustado para "explodir", ou seja, realizar a ação maliciosa a qual foi projetado. Entre alguns exemplos de condições que podem ser utilizadas para ativar uma bomba lógica: a presença ou ausência de um determinado arquivo ou dispositivo no sistema; um dia específico da semana ou certa data; a versão ou configuração em particular de um programa; a execução de uma aplicação por um usuário específico. Então, uma vez que a bomba lógica seja ativada ela poderá alterar ou excluir um conjunto de dados ou arquivos inteiros, causar dados ao sistema operacional a fim de que o computador trave ou causar um outro tipo de dano.

## **Denial of Service (DoS)**

Ataque de negação, ou termo em inglês DoS (Denial of Service), consiste e um técnica utilizada pelo atacante para indisponibilizar um serviço, servidor ou rede conectada na internet. Em geral, neste ataque o adversário realiza diversas requisições ao seu alvo a fim de sobrecarregá-lo, deste modo os recursos do sistema ficam indisponíveis para seus usuários. Existem uma versão deste ataque que é realizado de forma coordenada e distribuída, onde um conjunto de computadores é utilizado para realizar o ataque, esse tipo é denominado como ataque de negação de serviço distribuído, ou o termo inglês DDoS (Distributed Denial of Service).

![[UE8_img10.jpeg]]

Fonte: ©Stuart Miles/Adobe Stock

Com um objetivo diferente estes ataques não têm a intenção de invadir e nem coletar informações do usuário ou sistema, seu propósito na verdade é consumir todo recurso do seu alvo para causar indisponibilidade do serviço. Consequentemente, quando isto ocorre, todos os usuários que utilizam este sistema serão afetados, pois ficarão sem ter acesso a tais recursos, ficando impossibilitados de realizar as operações pretendidas.

Em geral, nos casos reportados os alvos que foram vítimas deste tipo de ataque, ficaram impedidos de fornecer o serviço naquele período que foram "objeto" do ataque, porém, após o incidente conseguiram voltaram a operar normalmente, na maioria dos casos não foi reportado vazamento de informação ou comprometimento dos servidores ou sistema.

Apesar de existir alguns indivíduos cedem por si próprio seu computador para que seja utilizado nos ataques, em geral executando ferramentas para este fim. Ressalta-se que a grande maioria dos computadores que estão sendo utilizados para realizar este tipo de ataque, os donos desses recursos (em geral computadores), em geral não têm conhecimento que seu computador foi infectado e está fazendo parte de uma botnet. Os Ataques de negação de serviço, seja realizado de forma distribuída ou não, podem ser realizados de diferentes formas, as mais comumente utilizadas são:

- Realizando o envio de uma grande quantidade de requisição para um serviço específico, deste modo, consumindo todos os recursos do sistema (processamento, memória, espaço em disco, rede) e impedindo assim que requisições legitimas dos seus usuários sejam atendidas;
- Efetuado pela exploração de vulnerabilidades existentes no sistema operacional ou ainda em programas instalados que podem fazer que um determinado serviço fique indisponível;
- Gerando um extenso volumo de tráfego de dados em uma rede, desta forma ocupando toda banda de rede disponível e indisponibilizando o acesso de qualquer computador ou serviço que tente utilizar aquela rede.

Relacionado ao assunto, existe um outro aspecto que também deve ser considerado, situações em que o serviço disponibilizado não foi corretamente dimensionado, desta forma é possível que haja uma saturação dos recursos. Consequentemente, o serviço poderá ficar inoperante ao tentar atender solicitações que sejam legítimas. Por exemplo, um site de comércio eletrônico que realiza promoções de produtos em uma "Black Friday", caso uma grande quantidade de clientes tente acessar o site simultaneamente se os recursos computacionais não forem estimados corretamente pode haver indisponibilidade do serviço ou o servidor não conseguir gerir todas as solicitações dos clientes.

## **Contramedidas Contra Malwares**

A execução de rotinas de softwares maliciosos insere inúmeros riscos à segurança da informação. Devemos estar cientes da existência de tais riscos, saber detectar as ameaças e principalmente aprender a se proteger. Visando garantir a segurança da informação, alguns cuidados que devem ser tomados, tanto no uso adequado dos computadores como da internet. Para isto, esta secção fornece um conjunto de boas práticas e mecanismos de segurança que podem ser utilizados para se proteger, entre alguns requisitos básicos de segurança, nos deparamos com os pilares da segurança:

- **Identificação****:** permitir que uma entidade se identifique no sistema, "dizer quem ela é".
- **Autenticação**: verificar se a entidade é realmente quem ela diz ser.
- **Autorização**: determinar quais as ações uma entidade pode realizar.
- **Integridade**: proteger a informação contra alterações não autorizada.
- **Confidencialidade**: proteger uma informação contra um acesso não autorizado.
- **Não repúdio ou irretratabilidade****:** evitar que uma entidade negue a autoria de uma determinada ação.
- **Disponibilidade****:** garantir que o recurso esteja disponível sempre que for necessário.

Para fornecer e garantir estes requisitos, foram desenvolvidos os mecanismos de segurança, quando devidamente configurados e utilizados, podem auxiliar o usuário a se proteger contra os riscos e segurança da informação. Primeiramente, vamos citar alguns dos cuidados necessários envolvendo o uso seguro da Internet, conforme orientados pelo CERT [Cert,2021]:

- **Mantenha seus equipamentos atualizados****: ** Utilize apenas programas originais. Tenha sempre as versões mais recentes dos programas instalados. Instale todas as atualizações disponíveis, principalmente atualizações referentes a segurança. Crie um disco de recuperação e tenha-o por perto no caso de emergências;
- **Instale um antivírus:** Mantenha sua solução de antivírus sempre atualizada, procedimento que deve incluir os arquivos de assinaturas, atualize o arquivo de assinaturas pela rede, o ideal que este processo seja realizado de preferência diariamente. Configure o antivírus para verificar automaticamente toda e qualquer extensão de arquivo, arquivos anexados aos e-mails, obtidos pela Internet, discos rígidos e as unidades removíveis. O ideal é sempre verificar os arquivos recebidos, antes de abri-los ou executá-los. Evite executar simultaneamente diferentes soluções de antivírus, eles podem entrar em conflito, afetar uns aos outros e ainda o desempenho do equipamento e interferir na capacidade de detecção. Você poderá criar um disco de emergência (mídia de emergência, pode ser criado em um pendrive) da sua solução de antivírus, caso você suspeite que o antivírus instalado está desabilitado ou foi comprometido, ou ainda o seu equipamento tem apresentado um comportamento estranho você poderá recorrer a este disco de emergência.
- **Utilize um firewall****: **Certifique-se de ter um firewall pessoal instalado e habilitado. Tenha o hábito de verificar os logs do firewall para verificar se não houve nenhuma tentativa de acesso malicioso pelos programas ou por um adversário.
- **Instalação de aplicativos:** Efetue download dos programas e aplicativos apenas de fontes confiáveis. Certifique-se que as permissões de instalação e execução estão coerentes. Selecione aplicativos que sejam bem avaliados e possua uma com grande quantidade de usuários.
- **Efetue Backup****:** Proteja seus arquivos e programas fazendo backups regularmente. Você deve garantir que seus backups estejam armazenados em um lugar seguro, mantenha os backups desconectados do sistema. Não recupere um backup caso desconfiar que este contenha dados que não são confiáveis.
- **Cuidado ao clicar em links****:** Atenção ao clicar em qualquer tipo de link, inclusive mensagens vindas de contatos conhecidos, nem todas as mensagens vindas de conhecidos são sempre confiáveis. O adversário pode alterar o campo do remetente do e-mail, falsificando sua origem, o e-mail pode ter sido enviado de contas falsas ou contas que foram invadidas. Antes de acessar um link curto procure utilizar complementos que permitam visualizar a url de destino.
- **Execução de arquivos****:** Utilize a conta de administrador apenas quando for realmente necessário. Tenha cuidado com extensões ocultas, alguns sistemas operacionais possuem a opção de configuração padrão para ocultar a extensão dos tipos de arquivos conhecidos. Desabilite a auto-execução de mídias removíveis e de arquivos anexados.

## **Explorando os mecanismos de segurança para prevenção de ataques de malware**

Este vídeo vai fornecer uma visão mais ampla sobre os mecanismos de segurança para proteção contra malwares, vamos apresentar como funciona tais ferramentas, quais as vantagens e desvantagens de utilizar estas abordagens, dicas e boas práticas para implementação destes mecanismos de segurança.

## **EXERCÍCIO**

**Exercícios de Fixação**

O que é um malware?

Cite três formas que o malware utiliza para infectar um dispositivo.

O que é um Vírus?

O que é um Hoax?

O que é um Worm?

Descreva o ciclo de progagação de um worm.

Descreva o que é um Bot e uma Botnet.

Quais são os tipos de Spyware? Descreva como funciona cada um deles.

O que é um Trojan?

Cite três mecanismos de segurança da informação. Descreva o que se trata cada um deles.

O que é um Ransomware?

O que é um Phishing?

Quais os componentes estruturais de malware?

O que é uma técnica de engenharia social?

Qual a diferença entre um ataque DoS e DDoS?

## **Conclusão**

Esta unidade abordou os conceitos relacionados a software malicioso, descobrimos o que é um malware, quais suas ações e como ele atua sobre o sistema para infectar e se disseminar. Discutimos quais são as principais motivações que levam o adversário a desenvolver e a propagar rotinas de código malicioso. Ainda, apresentamos os principais termos utilizados para categorizar os tipos de malware. Discutimos também que não existe um consenso universal para classificação, pois alguns tipos de malware se sobrepõem, estão dentro de mais de uma família.

Por conseguinte, apresentamos cada um dos tipos. Abordamos o processo de infecção pelo vírus de computador, como ele atua e infecta uma máquina hospedeira e ainda como se reproduz. Discutimos também, sobre a capacidade de um worm se propagar automaticamente pelas redes, enviando cópias de si próprio para outros computadores na rede, bem como a carga útil que eles carregam.

Posteriormente, foi apresentado como funciona uma botnet e as principais ações maliciosas que são realizadas, entre as principais os ataques de DDoS. Conhecemos também os diferentes tipos de spyware e como os adversários utilizam este malware para espionar suas vítimas.

Exploramos também o programa backdoor, foi discutido como este programa permite que um intruso consiga retornar a um computador que foi comprometido. Ainda, mostramos os diferentes tipos de Trojan, e quais as ações maliciosas que executam no computador após infectá-lo. Adicionalmente, abordamos o ransomware um dos mais nocivos tipos de malware, discutimos porque este tipo de malware é tão perigoso e cuidados que devem ser tomados para se precaver contra esta ameaça.

Ainda, foi apresentado algumas abordagens difundidas para classificação de malware, e porque atualmente tem sido classificado os malwares pelas funcionalidades no código fonte e através das semelhanças estruturais. Demostramos também, como os mecanismos de propagação atuam em uma infecção, quais as formas utilizadas para disseminar outros computadores e sistemas. Destacamos, os componentes elementares dos malware, o mecanismo de infecção, a carga útil e o mecanismo de ativação.

Por fim, discutimos sobre vulnerabilidades dos sistemas operacionais e programas instalados. Enfatizamos como os adversários exploram as vulnerabilidades e bugs no sistema por meio dos códigos maliciosos. Discutimos que o adversário para ter maior êxito em seus ataques utiliza técnicas de engenharia social associado ao uso de códigos maliciosos. Ainda, destacamos que existe uma grande preocupação com malware que foram projetados para corromper o sistema. Por último, discutimos sobre os desafios do profissional de segurança da informação para proteger os sistemas, apresentamos as contramedidas que devem ser adotadas para lidar com tais ameaças, cuidados necessários para proteger os sistemas computacionais e ativos da informação.