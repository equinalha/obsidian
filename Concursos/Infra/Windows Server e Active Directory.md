---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2024-12-01T10:59:00
Owner:
  - Eduardo Quinalha
---
# LDAP

- Porta 389/TCP
- Acesso a diretório (catálogo)
- Função: Organizar os recursos de rede de forma **hierárquica**, como uma **árvore** de diretório
	- Computadores
	- Impressoras
	- Contas de usuário, etc.
- Baseado em um padrão aberto
- API’s bem definidas
- Maior velocidade de consulta que um BD relacional
- Replicável e distribuível
- **Facilita a localização de informações (pesquisa pelo nome)**
- Schema
	- Conjunto de objetos e atributos
	- Padrão **X.500**
- **Escalável**

## Funcionamento

- Cada entrada possui um identificador único: **DN** (Distinguished Name)
	- Composto de um **RDN** (Relative …)
	- Construído de alguns atributos, seguido pelo **DN da entrada pai**
- Atributos
	- **CN**: Common Name
	- **SN**: Surname
	- **OU**: Unidade Organizacional
	- **DC**: Componente de domínio
	- **O**: Nome da organização
	- **C**: Country (Pouco utilizado)
```plain text
Exemplo:

dn: cn=Eduardo Quinalha,dc=tre-pr,dc=jus,dc=br
givenName: Eduardo
sn: Quinalha
mail: eduardo.quinalha@tre-pr.jus.br
```
- Comandos
	- **Bind**: **Autentica e especifica a versão do protocolo LDAP**
	- **Search**: Procura/recupera entradas
	- **Compare**: compara uma entrada com valor dado
	- **Add**: adiciona nova entrada
	- **Delete**: Exclui entrada
	- **Modify**: Modifica uma entrada
	- **Modify DN: Move ou renomeia**
	- **Abandon**: Aborta uma requisição
	- **Unbind**: Fecha conexão
	- **Extended Operation:** Operação genérica para deifnir outras operações
	- **StartTLS: Protege a conexão com TLS (A partir da versão 3 do protocolo)**
- DIT (Directory Information Tree)
	- Representação dos dados em uma estrutura hierárquica de forma de árvore
	- No AD, por exemplo, temos o NTDS.DIT
	- O LDAP usa o DIT como estrutura de armazenamento de dados
![[Concursos/images/Untitled 15.png]]

## Response Codes

0 LDAP_SUCCESS

2 LDAP_PROTOCOL_ERROR (BAD REQUEST)

3 LDAP_TIM3LIMIT_EXC33D3D

5 LDAP_COMPARE_FALSE

6 LDAP_COMPARE_TRUE

# Active Directory

## Conceitos

- **Workgroup**
	- Cenário em que cada servidor é independente do outro
	- Pequenas redes
	- Poucos usuários
	- Não há unificação de autenticação
	- Componentes espalhados pela rede
- **Diretórios**
	- Base de dados única, centralizada, escalável
- **Active Directory**
	- Serviço de diretórios do Windows
	- Deve ser utilizado com NTFS
- **Domínios**
	- Agrupamento lógico de contas e recursos
- **Controlador de Domínio**
	- Autentica o usuário e gera um token
	- O token é utilizado para que o usuário não tenha que digitar a senha novamente
- **Árvores e Florestas**

![[Concursos/images/image 12.png]]

- **Catálogo Global**
	- Controlador de domínio que armazena uma cópia de todos os objetos do AD em uma floresta
	- Armazena uma cópia completa de todos os objetos no diretório para seu domínio e cópia parcial de todos os objetos para todos os outros domínios na floresta.

## Principais Serviços

### AD CS

- Certificate Services
- Criação e gerenciamento de certificados de chaves públicas

### AD DS

- Domain Services
- Componente principal
- Armazena informações sobre usuários, computadores, dispositivos, etc.

### AD FS

- Federation Services
- Identidades de acesso que operam através de múltiplas plataformas (Windows ou não)
- Pode fornecer SSO

### AD LDS

- Lightweight Directiory Services
- Versão mais leve do AD
- Provê praticamente as mesmas funcionalidades do AD DS
- Não requer o desenvolvimento de domínios

### AD RMS

- Rights Management Services
- Gerenciamento de identidades

## Arquivos

- NTDS.dit
	- armazena a árvore de diretório
- edb.chk
	- Checkpoint
	- Usado para recuperação de estado
- edb.log
	- log de transações

# Windows Server 2012

- Utiliza sistema de arquivos ReFS
	- Verificação automática de integridade e limpeza de dados
	- Proteção contra degradação de dados
	- Integração com RAID
	- Permite caminhos e nomes de arquivos muito longos
- O Windows Server 2012 possui duas principais opções de instalação: a **Instalação Server Core** e a **Instalação com Interface Gráfica do Usuário (GUI)**.
- A **Instalação Server Core** é a opção padrão no processo de instalação do Windows Server 2012.

# Windows Server 2016

## BranchCache

-  visa otimizar a utilização da largura de banda de rede em ambientes onde há escritórios remotos ou sucursais
- Permite que conteúdos frequentemente acessados de servidores remotos sejam armazenados localmente
	- Quando um computador em uma rede local (como um escritório) solicita dados de um servidor remoto (como o Windows Server Essentials hospedado no Azure), o conteúdo pode ser armazenado localmente
	- Com o conteúdo armazenado em cache, outros computadores na mesma rede local podem acessar esses dados diretamente, sem precisar fazer novas solicitações através da WAN (Wide Area Network) para o servidor remoto.
- Formas de configuração
	- **Distributed Cache Mode**: 
		- O cache é armazenado nos próprios computadores clientes da rede local. 
		- Quando um cliente solicita dados de um servidor remoto, ele os armazena e compartilha com outros clientes no escritório local.
	- **Hosted Cache Mode**: 
		- Um servidor local é dedicado e armazena o cache, centralizando o conteúdo em um ponto de acesso comum para outros clientes da rede.

## Device Guard

- Combinação de recursos de hardware e software que, juntos, criam uma forte linha de defesa contra malwares.
- Pode usar a** virtualização baseada em hardware** para **isolar partes do sistema operacional** e impedir que ataques comprometam o núcleo do sistema, ou seja, o **modo kernel**.
- Permite que apenas aplicativos confiáveis sejam executados no servidor.
- Utiliza uma tecnologia chamada **Configurable Code Integrity (CCI)**, que assegura que apenas código confiável é executado no sistema

## Nano Server

- **Versão leve do Windows Server**, voltada para execução de aplicações modernas, como** containers e microserviços.**
- É uma instalação com menos componentes, ideal para reduzir a superfície de ataque e o uso de recursos. 
- Não tem interface gráfica (GUI) **nem interface local**, o que significa que ele é **completamente gerenciado remotamente**.
- Isso inclui gerenciamento via **PowerShell Remoto**, **Windows Remote Management (WinRM)**, **SSH**, **System Center** ou ferramentas específicas para gerenciamento de servidores headless. 
- Não possui nenhum suporte a login local direto.
- **Não suporta **muitas das funções do Windows Server tradicional, como **Active Directory** Domain Services (AD DS), DNS, ou DHCP. 
- Ele é voltado para cenários específicos, como:
	- **Host de containers**
	- **Serviços de computação em nuvem**
	- **Servidores Web e aplicações distribuídas**

## Containers

- Introduz suporte nativo a **Windows Containers e Hyper-V Containers**
- Os containers são uma forma de isolar aplicações e seus ambientes em um único sistema, com menor sobrecarga em relação a máquinas virtuais.
- **Windows Containers** compartilham o kernel do sistema operacional host.
- São projetados para rodar aplicativos **nativos do Windows**, como serviços Windows, .NET Framework, IIS, ou qualquer aplicativo que seja dependente de APIs do Windows.
- **Windows Containers** compartilham o kernel do host Windows com um isolamento leve.
- **Hyper-V Containers** são executados em um nível de isolamento mais alto, cada container é executado dentro de uma mini máquina virtual Hyper-V, garantindo um isolamento mais seguro, semelhante ao de VMs.
- Containers Windows podem ser gerenciados pelas** mesmas ferramentas** amplamente usadas no ecossistema de containers, como **Docker** e **Kubernetes**.
- O **Docker para Windows** tem suporte para containers Windows e permite a execução e gerenciamento de containers diretamente no Windows Server ou Windows 10 (com suporte a containers Hyper-V).

## Storage Spaces Direct (S2D)

- Tecnologia que facilita a criação de sistemas de armazenamento **hiperconvergente**, utilizando servidores padrão e discos locais. 
- Permite a criação de **clusters hiperconvergentes**, integrando armazenamento e processamento em um único ambiente gerenciado
- Permite criar sistemas de armazenamento altamente disponíveis utilizando discos locais em servidores em cluster
- Ele permite que você construa **pools de armazenamento distribuído**, sem a necessidade de **SANs** caras.
- Possibilita dois modelos de implantação:
	1. **Modelo hiperconvergente:** Neste modelo, os recursos de computação e armazenamento estão localizados <u>nos mesmos nós do cluster</u>. Ao adicionar hosts a este modelo, você está essencialmente adicionando tanto recursos de armazenamento quanto de computação, pois eles estão acoplados
	2. **Modelo convergente (ou desagregado): **Neste modelo, um cluster é usado para recursos de computação e outro cluster é usado para recursos de armazenamento

## Shielded Virtual Machines (Máquinas Virtuais Blindadas)

- As **Shielded VMs** são máquinas virtuais protegidas contra acessos não autorizados, tanto de **administradores** do host quanto de **usuários maliciosos. **
- Utilizam criptografia de dados e integram com o **Host Guardian Service (HGS)** para garantir que apenas hosts confiáveis possam executar essas VMs.

## **Just Enough Administration (JEA)**

- Permite fornecer permissões mínimas para que administradores possam realizar tarefas específicas sem obter controle total sobre o sistema. 
- Essa abordagem de "least privilege" aumenta a segurança e reduz o risco de ataques baseados em credenciais.

## **PowerShell Direct**

- **P**ermite gerenciar máquinas virtuais diretamente do host físico via **PowerShell**, 
- Sem necessidade de configurar a rede ou credenciais adicionais

## **Host Guardian Service (HGS)**

- Usado para proteger máquinas virtuais com criptografia e garantir que **apenas hosts confiáveis** possam executar essas VMs. 
- Ele é fundamental para a implementação de **Shielded VMs**.

## **Storage Replica**

- **Storage Replica** é um recurso que permite a replicação síncrona e assíncrona de volumes entre servidores ou clusters, garantindo a continuidade de negócios e recuperação de desastres com zero perda de dados (RPO).

## **Soft Restart**

- Possibilita reinicializar o Windows Server** sem reinicializar todo o hardware**. 
- Isso reduz o tempo de inatividade em atualizações e manutenção.

## **Cluster Operating System Rolling Upgrade**

- Permite que clusters de alta disponibilidade sejam atualizados para uma nova versão do sistema operacional sem interrupções, migrando os nós para o novo SO sem downtime.

## **Network Controller**

- Solução de gerenciamento centralizado para **redes definidas por software (SDN). **
- Ele permite automatizar a configuração, monitoramento e gerenciamento de redes virtuais e físicas.

## Monitor de Referência

- **Monitor de Referência de Segurança do Windows Kernel-Mode**
- Avalia as listas de permissões (ACL) a fim de permitir o acesso ou não ao um determinado driver de dispositivo

# VDI - Virtual Desktop Infrastructure

- tecnologia para prover e gerenciar desktops virtuais
- Os desktops virtualizados são criados por uma máquina virtual (VM) controlada por um hypervisor

# **Windows Server Essentials**

O **Windows Server Essentials** é uma versão simplificada do sistema operacional Windows Server, projetada para pequenas empresas, geralmente com até 25 usuários e 50 dispositivos. Essa versão oferece funcionalidades essenciais, como:

- Compartilhamento de arquivos.
- Gerenciamento de usuários e dispositivos.
- Backup automático de clientes e servidores.
- Integração com serviços de nuvem, como o Microsoft Azure e o Office 365.
- Funcionalidades básicas de servidor de diretório e autenticação via Active Directory.

Por ser uma solução mais leve e fácil de gerenciar, o Windows Server Essentials é ideal para empresas menores que não precisam de todos os recursos robustos presentes em outras edições do Windows Server, como a Standard ou a Datacenter.

# PowerShell

- Compilado sobre o CLR (Common Language Runtime) do .NET Framework
- introduz o conceito de cmdlet (pronuncia-se “command-let”), uma ferramenta de linha de comando simples, de função única e compilada no shell.
- cmdlets geralmente seguem o formato **verbo-substantivo**, ex.: “Stop-process” (parar o processo)
- **cmdlets são instâncias de classes do framework .NET;**
- Principais:

![[Concursos/images/image 13.png]]

**WinRM (Windows Remote Management)** é uma ferramenta usada principalmente para gerenciar máquinas Windows remotamente

# Windows Admin Center

- Ferramenta gratuita, baseada em web (navegador), para gerenciamento remoto de servidores windows, clusters, PC e infraestrutura de nuvem
- Reúne várias ferramentas de gerenciamento em um único painel
- Permite integração com Azure
- É voltada à administração de servidores e clusters únicos, não suporta administração em grande escala, como datacenters
- Suporte para gerenciamento de **Clusters de Failover** e **Hyper-Converged Infrastructure** (HCI), com monitoramento e relatórios de desempenho para ambientes virtualizados.
- Oferece ferramentas para a configuração e operação de **clusters HCI**, suportando storage spaces, redes definidas por software (**SDN**) e alta disponibilidade.
- Facilita o gerenciamento de **Hyper-V**, permitindo que os administradores criem, excluam e configurem máquinas virtuais.
- Suporta o **Cluster Aware Updating (CAU)** para gerenciar atualizações em clusters de failover, reduzindo o downtime.