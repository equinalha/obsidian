---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2024-09-23T18:31:00
Owner:
  - Eduardo Quinalha
---
# Arquitetura Zero Trust

- Desconsidera o conceito de rede interna
- Não pressupõe a confiança a depender da origem do acesso
- Na verdade, este modelo se adéqua à tendência de não mais existir rede interna, agora tudo é nuvem e tanto o usuário quanto o serviço estão ligados diretamente à internet
- A internet é a nova rede interna
- Baseia no princípio “nunca confie, sempre verifique”

## Princípios fundamentais

- **Autenticação e Autorização Contínuas:** 
	- Em uma arquitetura Zero Trust, todos os acessos são rigorosamente autenticados e autorizados, independentemente da localização do usuário ou do dispositivo. 
	- Isso inclui a autenticação multifatorial para verificar a identidade dos usuários e a aplicação de políticas de acesso granulares com base em papéis, contextos e comportamentos.
- **Micro-segmentação da Rede:**** **
	- A rede é dividida em segmentos menores e isolados, limitando o tráfego entre eles e restringindo o acesso apenas aos recursos necessários para cada usuário ou serviço. 
	- Isso reduz a superfície de ataque e minimiza o impacto de violações de segurança, pois dificulta a movimentação lateral.
- **Análise de Comportamento e Detecção de Anomalias: **
	- São implementados mecanismos de monitoramento em tempo real para detectar atividades suspeitas ou anômalas. 
	- Isso inclui a análise do comportamento do usuário, dispositivos e aplicativos, bem como a detecção de padrões de tráfego incomuns que possam indicar uma violação de segurança.
- **Controles de Acesso Baseados em Políticas:** 
	- O acesso a recursos e dados é concedido com base em políticas granulares que consideram fatores como identidade, contexto da solicitação, comportamento do usuário e risco associado. 
	- Isso permite uma aplicação consistente e flexível das políticas de segurança em toda a organização.
- **Segurança Pervasiva e Criptografia:** 
	- Todos os dados em trânsito e em repouso são criptografados para proteger contra interceptação e acesso não autorizado. 
	- Além disso, são implementadas medidas de segurança em todas as camadas da infraestrutura, incluindo endpoints, redes, aplicativos e serviços em nuvem.

![[Untitled 305.png]]

## Processo de Implantação

- **Identificação da Superfície de Proteção****,** que é composta pelos dados, ativos, aplicativos e serviços mais importantes da rede. 
	- Esta superfície é conhecida por DAAS, sigla em inglês.
- Entender como o é o tráfego de dados para dentro e para fora da superfície de proteção, identificando usuários, aplicações e a infraestrutura, estabelecendo um modelo de tráfego considerado normal.
- Cria-se então um microperímetro ao redor desta superfície, normalmente utilizando-se de **Gateways de Segmentação** ou **firewall de última geração**. 
- Com base no entendimento do tráfego na fronteira da superfície de proteção e da criticidade dos dados e serviços, deve-se elaborar uma **política de Zero Trust**, que estabeleça quais são os usuários que terão acesso ao microperímetro e a quais serviços. 
	- O firewall será o elemento responsável por controlar os acessos e garantir a aplicação da política estabelecida.
- Por fim, deverá ser feito o monitoramento contínuo do perímetro estabelecido, buscando por anomalias e por eventuais elementos que deverão ser incluídos na política. 

![[Untitled 306.png]]

# Zero Trust Network Access

- **É um método de acesso remoto**
- Solução de segurança com foco no **Acesso remoto, ****Diferente de VPN**
- Base em políticas bem definidas
- **concede acesso apenas a serviços ou aplicativos específicos, enquanto as VPNs concedem acesso a uma rede inteira.**
- O acesso a aplicativos ou recursos é concedido somente após a autenticação do usuário no ZTNA
- Após a autenticação, o ZTNA concede ao usuário acesso ao aplicativo ou serviço específico, por um túnel

## Benefícios

- Acesso detalhado, reconhecimento de contexto a aplicativos essenciais
- Elimina a concessão de confiança excessiva
- Impede que o usuário tenha visibilidade a outros serviços que não tenha permissão
- Protege contra ataques laterais
	- Mesmo que o atacante venha a ter acesso a determinado recurso, não poderá fazer varredura em busca de outros serviços
- Permite monitoramento pós-conexão para evitar vazamento de dados, ações mal intencionadas ou comprometimento de credenciais
- **Endereços de IP ocultos:** o ZTNA não expõe endereços de IP à rede. O resto da rede permanece invisível para os dispositivos conectados, exceto para o aplicativo ou serviço ao qual eles estão conectados.

## Formas de implementação

- Iniciando no Endpoint
	- Um agente instalado no dispositivo se comunica com o controlador de ZTNA, que fornece autenticação e se conecta ao serviço desejado.
- Iniciando no Serviço
	- a conexão é iniciada por um intermediário entre o aplicativo e o usuário
	- requer que um conector de ZTNA leve seja instalado na frente dos aplicativos
	- Isola os aplicativos do acesso direto por meio de um proxy
	- não é necessário nenhum agente nos dispositivos de usuários finais
		- Favorece BYOD

## Modelos de Fornecimento

- ZTNA Independente
	- A própria organização implanta e gerencia todos os elementos ZTNA
- ZTNA Como serviço
	- Oferecido por provedor de nuvem
	- A Organização só precisa implantar os conectores na frente dos aplicativos protegidos

## ZTAA

- Segurança de aplicativos
- Mesmos princípios do ZTNA ao acesso de aplicativos mas não ao acesso à rede
- Cada solicitação de acesso a um aplicativo é tratada individualmente

# SDP

- Software Dfined Perimeter
- Oculta a infraestrutura de pessoas externas ou invasores
- Perímetro da rede é baseado num software e não em hardware
- Autentica dispositivos e identidade de usuários
- Após a autenticação do usuário, uma conexão de rede individual entre este usuário e o servidor que ele deseja acessar, é configurada

# PAM

- Privileged Access Management
- Monitora, detecta e impede acesso privilegiado não autorizado
- Localiza, monitora e gerencia contas de usuário e privilégios, detectando anomalias. Por exemplo, uma conta de funcionário do RH que tenha privilégio DBA
- Oferece visibilidade sobre quem está usando contas privilegiadas e o que está fazendo com elas
- Gerar relatórios para identificar e investigar anomalias.
- Princípio do menor privilégio
- Acesso privilegiado é concedido apenas quando necessário e por tempo limitado
- Ferramentas
	- Descoberta de contas com privilégio
	- Gerenciamento de senhas
	- Gravação de sessões
	- Análise de sessões privilegiadas

## PIM

- Privileged Identity Management
- Gerenciamento e controle de identidades que tenham privilégios em sistemas ou outros recursos
- Contas de administração de sistemas, DBA de banco, etc..
- Impõe controles rígidos nestas contas
- O objetivo é estabelecer controles fortes e processos de gerenciamento de identidades privilegiadas
- PIM controla administradores e super usuários com acesso com limite de tempo e protege essas contas privilegiadas.

## IAM

- Permite o gerenciamento de identidades e privilégios de acesso
- Possibilita a configuração de funções de usuário
- Rastreamento de atividade
- Estabelecimento de políticas corporativas
- IAM pode ser composto de diversas ferramentas
- SSO, MFA, RBAC e privilégios mínimos são métodos de IAM
- **Identity Management**
	- Diretório se comunica com um ou mais sistemas de RH
	- Sincroniza informações com LDAP, sistemas ERP e aplicações corporativas
	- Realiza o provisionamento e desprovisionamento
	- Ciclo de vida da identidade:
		- Joiner - onboarding
		- Mover - Promoção
		- Leaver - offboarding
		- Access Request - workflows, forms
		- SoD - Seggregation of Duties
		- Password Self-service
![[Untitled 307.png]]
- **Access Management**
	- Adaptative Access
		- Captura diversas informações sobre o usuário que está tentando se autenticar:
			- Geolocalização
			- Informações sobre o dispositivo
			- IP
			- Histórico
			- Análise do comportamento
		- Com estas informações é criado um escore
		- Um bom escore, garante acesso aos sistemas
		- Um escore médio pode requerer uma etapa adicional de autenticação
		- Um escore ruim, bloqueia o acesso

# EDR (Endpoint Detection and Response)

- Focado no endpoint
- Coleta e analisa dados das atividades nos endpoints
- Depende de:
	- Monitoramento contínuo
	- Análise comportamental
	- Resposta automatizada
	- Visibilidade

# XDR (Extended Detection and Response)

- Evolução do EDR que amplia a detecção para além dos endpoints
- Integra dados de múltiplas fontes
- Permite uma resposta coordenada e visibilidade unificada
