---
base: "[[Simulados.base]]"
Desempenho: 0.53
Banca: CEBRASPE
Obs: Apenas específica
Tipo: Certo/Errado
Obj: TSE
"% Colocação": -100
Status: Done
Data: 2024-03-10
---
> [!note] 💥
> Análise Geral:
- Necessidade de aprofundamento em SNMP, MIB e RMON
- Necessidade de revisão e aprofundamento em algoritmos criptograficos: AES, Blowfish
- Necessidade de revisão de ISO 27005 e Gerenciamento de Riscos
- Cuidado com afirmações do tipo “Prevê metodologia **específica**” Geralmente estas coisas são mais genéricas
- Estudar LGPD
- Buscar o que é BAS (Breach Attack Simulation)
- Revisar e aprofundar sobre firewall. Quais tecnologias são consideradas firewall (Proxy, NAT, filtros, etc.)
- Revisar e aprofundar sobre proxy
- Revisar e aprofundar sobre STRIDE
- Revisar IEEE 802.3 (especifica também a camada física?)
- Estudar PMBOK 7
- Estudar COBIT 2019

Análise estratégica
- Algumas questões dão muito na cara. Estas vale chutar conscientemente
- Ainda é preferível deixar em branco do que arriscar chutar errado

52 No SNMPv1, as comunidades estão restritas a dois tipos apenas, leitura e leitura e escrita.

> [!note] 🔥
> ***Tipos de comunidades no SNMPv1:***
> - ***Comunidade pública:**** Permite apenas leitura de informações básicas do dispositivo.*
> - ***Comunidade privada:**** Permite leitura e modificação de informações do dispositivo.*
> - ***Comunidades específicas:**** Comunidades personalizadas com permissões de acesso específicas para grupos de dispositivos ou funcionalidades.*

56 Diferentemente do SNMPv1 e do SNMPv2, o SNMPv3 fornece serviços de autenticação e privacidade.

> [!note] 🔥
> *Correto

Os serviços de autenticação e privacidade só foram introduzidos na versão 3.

Obs: Existe uma subversão do 2, SNMPv2u que oferece algum suporte a criptografia*

57 A MIB RMON apresenta mecanismos para um gerente configurar e controlar um monitor remoto, mas não consegue coletar seus dados nem receber seus alarmes.

> [!note] 🔥
> *Errado.

Pode ser utilizada para coletar dados e receber alarmes*

58 Uma das características da MIB-II é que o gerenciamento é realizado em cada dispositivo individualmente, ou seja, cada dispositivo deve ter sua MIB e seu agente.

> [!note] 🔥
> *Cada dispositivo de rede gerenciado precisa ter sua própria MIB, que define os objetos de gerenciamento que podem ser acessados e manipulados por um gerente de rede.*
> *Cada dispositivo precisa ter um agente SNMP (Simple Network Management Protocol) que implementa a MIB e fornece acesso aos seus dados para o gerente de rede.*

59 A versão RMON1 define vinte e dois grupos de MIB para o monitoramento básico de rede.

> [!note] 🔥
> *São 20 grupos, sendo os 10 primeiros responsáveis pelas camadas 1 e 2 do modelo OSI e os outros 10 pelas camadas 3 a 7.*

60  Existem duas versões do RMON, conhecidas por RMON1 ou RMONv1, e RMON2 ou RMONv2.

> [!note] 🔥
> *Correto.

Como RMON é a extensão da MIB, é correto associá-las a versão.*

63 Blowfish é uma cifra simétrica de blocos que utiliza chave com tamanho variável de 32 bits a 448 bits e que foi criada como alternativa gratuita e rápida aos algoritmos criptográficos existentes.

> [!note] 🔥
> *Correto. Exatamente a descrição do algoritmo presente nas literaturas*

### IEC 27005

70 Gerenciamento de riscos é um processo contínuo que se aplica a todas as fases operacionais em que consequências de um risco específico são aceitas.

> [!note] 🔥
> 

72  A ABNT NBR ISO/IEC 27005 provê metodologia específica para o gerenciamento de riscos em segurança da informação.

> [!note] 🔥
> 

74 Na avaliação de desempenho, em desempenho deficitário, não devem ser incluídos não conformidades, quase acidentes e alarmes falsos.

> [!note] 🔥
> 

### LGPD

76 Aplica-se a LGPD na coleta e no tratamento de dados pessoais para fins particulares, jornalísticos, artísticos, de segurança pública e de defesa nacional.

> [!note] 🔥
> 

79 A LGPD indica princípios de boa-fé que devem ser levados em consideração no tratamento de dados pessoais, como a transparência, que garante ao titular consulta facilitada e gratuita da integralidade dos seus dados pessoais.

> [!note] 🔥
> 

### Segurança Cibernética

82 A técnica BAS (breach attack simulation) é utilizada para proteger sistemas de TI contra ameaças de segurança, com acesso a meios centralizados de consultas e compartilhamento de informações sobre ameaças.

> [!note] 🔥
> *Errado. BAS é utilizado para simular ataques conhecidos e identificar vulnerabilidades presentes, a eficácia dos sistemas de proteção (firewall, IDS, IPS) e treinar especialistas.*

### Firewall

87 Um proxy pode atuar no nível de aplicação, em que haverá um proxy diferente para cada aplicação, ou ainda no nível de transporte, em que haverá um proxy genérico para conexões TCP e UDP.

> [!note] 🔥
> *Um proxy pode, de fato, operar tanto no nível de aplicação quanto no nível de transporte.*
> *No ****nível de aplicação****, um proxy específico é usado para cada aplicação. Este tipo de proxy é ****capaz de ler e interpretar o conteúdo das mensagens trocadas entre cliente e servidor****, permitindo um controle mais granular do tráfego de rede.*
> 
> *Exemplos comuns incluem proxies HTTP, FTP e SMTP.*
> 
> *No nível de transporte, ****um proxy genérico pode ser usado para conexões TCP e UDP****.*
> 
> *Este tipo de proxy, também conhecido como**** proxy de circuito****, estabelece uma conexão entre cliente e servidor e repassa os pacotes entre eles *<u>***sem inspecionar o conteúdo das mensagens***</u>*.*

### Modelagem de Ameaças

91 STRIDE é uma metodologia de identificação de ameaças à segurança baseada em um processo de sete etapas para identificar, enumerar e classificar as ameaças.

> [!note] 🔥
> *Errado

STRIDE é um modelo de ameaças para classificá-las em 6 grupos:
Spoofing, Tampering, Repudiation, Information Disclosure, Denial of Service, Elevation of Privilege

Não existem etapas e nem são 7*

106 O IEEE 802.3 define como deve ser o controle de acesso da camada física e da camada de enlace de dados do padrão Ethernet com fio.

> [!note] 🔥
> *Certo. Pensei demais*
