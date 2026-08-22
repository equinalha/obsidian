---
base: "[[Simulados.base]]"
Desempenho: 0.66
Banca: CEBRASPE
Obs: ""
Tipo: Certo/Errado
Obj: TSE
"% Colocação": -100
Status: Done
Data: 2024-10-25
---
**52 - A validação de entrada de dados, quando eles são inseridos na base de dados por fontes e usuários desconhecidos, é uma prática que atende ao conceito de integridade.**

> Certo.

1- A validação dos dados ajuda a preservar a integridade do ponto de vista de formato e padrão dos dados
2- Também ajuda a evitar a inserção de dados maliciosos, como SQL Injection

**54 - Segundo a NBR ISO/IEC 27002:2022, são dois os tipos de controle nas políticas de segurança da informação: #Preventivo e #Corretivo. **

> Errado

#Preventivo - Evitar a ocorrência
#Detectivo - O controle age na ocorrência
#Corretivo - O controle age após a ocorrência

**55 - Na NBR ISO/IEC 27002:2022, no atributo propriedades de segurança da informação incluem-se as visões de controle #Confidencialidade, #Integridade, #Disponibilidade e #Autenticidade.**

> Errado

Somente #Confidencialidade, #Integridade, #Disponibilidade

57 - Nos controles CIS, empresas que geralmente armazenam e processam informações confidenciais de clientes são classificadas como IG2 ou IG3. 

> 

74 - O uso de SSL/TLS ajuda a prevenir ataques de negação de serviço. 

> Errado

DDoS ocorre nas camadas 3 e 4. SSL/TLS atua na camada de aplicação

**80 - O *****port scanning***** não pode ser prevenido, sendo possível apenas a sua detecção, pois é uma técnica muito comum e não há forma de interrompê-la. **

> Errado


> **Firewalls **e sistemas de detecção de intrusão (**IDS/IPS**) podem ser configurados para bloquear ou limitar o número de solicitações de varredura de portas, detectando padrões suspeitos de tráfego de rede.
> 
> Só aí já damos ERRADO para questão, já que isso por si já é uma "prevenção".
> 
> É possível impedir totalmente o port scanning? NÃO
> 
> É possível prevenir? SIM

100 - Conforme o padrão IEEE 802.11ax, é irrelevante o uso de MFP (*Management Frame Protection*) para manter a resiliência de redes de missão crítica, já que o MFP usa tecnologia insegura.

> Errado

> O **MFP (Management Frame Protection)** é uma funcionalidade do padrão **IEEE 802.11ax** que visa aumentar a segurança das redes sem fio ao proteger os quadros de gerenciamento contra ataques, como o spoofing e o de desautenticação.

102 - Um roteador e um *switch *podem fazer uso da funcionalidade do Engine ID Identifier no SNMPv3, que agrega uma dupla identidade a um pacote SNMPv3 para fins de redução do tamanho do fluxo de dados entre elemento controlador e elemento controlado.

> Errado

> - O **Engine ID** no SNMPv3 (Simple Network Management Protocol versão 3) é um identificador único que identifica de forma exclusiva cada dispositivo gerenciado (também conhecido como **SNMP Engine**). 
> - Cada dispositivo gerenciado, como um roteador ou switch, possui seu próprio Engine ID, que é usado para autenticar e estabelecer comunicação segura com o gerenciador SNMP.
> - O **Engine ID** não agrega uma "dupla identidade" a um pacote, tampouco tem o objetivo de reduzir o tamanho do fluxo de dados entre o elemento controlador (gerenciador) e o elemento controlado (dispositivo SNMP). 
> - Ele não tem a função de compactar dados ou reduzir o tráfego de rede, mas sim de garantir que cada dispositivo seja identificado de forma única, facilitando a segurança e integridade da comunicação.
> - A comunicação entre o gerenciador e o dispositivo ainda envolve autenticação e criptografia conforme o perfil de segurança, mas não há função específica para reduzir o volume de dados.

105 - Três elementos devem ser considerados em um plano de recuperação de desastres de um sistema de TI: a prevenção, a detecção e a recuperação. 

> Correto

Um **plano de recuperação de desastres** (DRP - Disaster Recovery Plan) é uma parte essencial de um plano de continuidade de negócios, especialmente para sistemas de TI. Ele visa restaurar operações após um evento disruptivo, e três elementos principais são normalmente considerados:
> 1. **Prevenção**: Envolve medidas para minimizar a probabilidade de desastres, incluindo práticas como backups regulares, redundância, segurança física e controles de acesso.
> 2. **Detecção**: A implementação de sistemas que possam detectar rapidamente incidentes ou falhas. Isso pode incluir monitoramento contínuo, alertas em tempo real e auditorias para identificar ameaças emergentes.
> 3. **Recuperação**: Foca em ações para restaurar serviços e dados rapidamente após um incidente. Isso envolve a execução de procedimentos de backup, recuperação de sistemas e ativação de sites de recuperação, além de testes regulares do plano.

113 - A adoção de um plano de gestão de incidentes de segurança da informação não reduz a probabilidade de ocorrência de desastres, mas ajuda na solução do problema quando da sua ocorrência.

> Errado (Interpretação da CEBRASPE)

Dentro de um processo de gestão de riscos de segurança da informação temos a etapa do Processo de avaliação de riscos de segurança da informação. Dentro dessa etapa, uma subetapa é a identificação dos riscos, ameaças, controle, vulnerabilidades. Quando se faz essa análise preliminar a probabilidade de ocorrência de incidentes e desastres reduz, afinal após a finalização de todo o processo serão tomadas medidas preventivas.