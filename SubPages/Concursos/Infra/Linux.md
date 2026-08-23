---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2024-11-17T18:33:00
Owner:
  - Eduardo Quinalha
---
# Introdução

- Segue o padrão POSIX, o mesmo utilizado pelo Unix
- Suporte nativo a virtualização
- Shell → Envolve o kernel (como uma casca) a fim de permitir que seja operável para o usuário final
	- É a principal ligação entre o usuário, os programas e o kernel
	- Usuário Root: #
	- Usuário comum: $

# Shell

## Histórico de Comandos

![[Untitled 525.png]]

# LVM

- Camada de software acima dos discos
- Permite RAID
- Composto por 3 camadas:
	- PV (Physical Volume)
		- Corresponde ao dispositivo de bloco adicionado ao LVM
	- VG (Volume Group)
		- Volumes físicos que fazem parte do LVM
		- A partir do VG são alocados os espaços para criação dos volumes lógicos
	- LV (Logical Volume)
		- Partição lógica criada pelo LVM

![[Untitled 526.png]]

# Sistema de Arquivos

## EXT3

- Introduziu o conceito de Journal
- Suporta até **16TB** no sistema de arquivos
- Até **2TB** de tamanho para cada arquivo
- No máximo **32000** subdiretórios para cada diretório

## EXT4

- Até **1EB** para o sistema de arquivos
- Até **16TB** por arquivo
- Número **ilimitado** de subdiretórios

## JFS

- Alternativa ao EXT4, desenvolvido pela IBM
- 64 bits

## XFS

- Usado como **padrão na distro RHEL** e suas derivações.
- Sistema de arquivos desenvolvido em **64 bits**, **compatível** com sistemas de **32 bits**
- Até **16EB** para o sistema de arquivos
- Até **8EB** por arquivo
- Considerado de **alto desempenho**
- **Permite aumentar a capacidade do volume de forma online (não precisa desmontar)**
	- A capacidade é aumentada através do comando ressze e2fs.
- Possui **backup e restore nativo e online.**

## ReiserFS

- Muito **rápido** para sistemas de arquivos que armazenam** arquivos pequenos** (cache, e-mails etc.)
- Primeiro sistema de arquivos baseado em journaling incluído no kernel padrão do Linux
- **Permite aumentar ou diminuir a partição sem perda dos dados.**

# Processo de Boot

- Em resumo, o processo de boot é o seguinte:
	- BIOS/UEFI executa POST e carrega o primeiro estágio do bootloader do MBR ou GPT.
	- O primeiro estágio do bootloader carrega o segundo estágio do bootloader.
	- O segundo estágio do bootloader apresenta um menu de seleção e carrega o kernel e o `initrd` na memória.
	- O kernel é inicializado e monta o `initrd` como sistema de arquivos raiz temporário.
	- O `initrd` executa scripts para carregar drivers e preparar o ambiente.
	- O `initrd` monta o sistema de arquivos raiz permanente e transfere o controle.
	- O `initrd` é desmontado e o sistema continua a inicialização a partir do sistema de arquivos raiz permanente.

## Bootloader

- **Primeiro Estágio do Bootloader**:
	- O BIOS/UEFI carrega o primeiro estágio do bootloader a partir do MBR (Master Boot Record) ou GPT (GUID Partition Table) do disco de boot.
	- O primeiro estágio do bootloader é geralmente **muito pequeno** e tem como principal tarefa localizar e carregar o segundo estágio do bootloader.
- **Segundo Estágio do Bootloader**:
	- O segundo estágio do bootloader é mais complexo e **reside em uma partição do disco.**
	- Ele carrega a configuração do bootloader, geralmente armazenada em um arquivo como `/boot/grub/grub.cfg`.
	- Apresenta um menu de boot ao usuário, permitindo a seleção entre diferentes sistemas operacionais ou diferentes versões do kernel.
- **Carregamento do Kernel e initrd**:
	- Após a seleção, o bootloader carrega o kernel do Linux e o `initrd` (ou `initramfs`) na memória.
	- O kernel é geralmente armazenado em `/boot/vmlinuz-<versão>` e o `initrd` em `/boot/initrd.img-<versão>`.

## Initrd (Initial RAM Disk)

O `initrd` (ou `initramfs`) é uma imagem de disco que contém um sistema de arquivos temporário. Ele é usado durante o processo de boot para carregar drivers e preparar o ambiente necessário para montar o sistema de arquivos raiz (root filesystem). Aqui está o detalhamento do `initrd` e suas etapas:

1. **Carregamento na Memória**:
	- O bootloader carrega o `initrd` na memória logo após carregar o kernel.
	- O `initrd` contém drivers e scripts necessários para a inicialização do sistema.
2. **Montagem do Sistema de Arquivos Temporário**:
	- O kernel monta o `initrd` como o sistema de arquivos raiz temporário.
	- No caso do `initramfs`, ele é montado como um `tmpfs`, que é um sistema de arquivos na memória.
3. **Execução de Scripts de Inicialização**:
	- O `initrd` contém scripts de inicialização, que são executados para carregar drivers e módulos necessários para acessar o sistema de arquivos raiz permanente.
	- Esses scripts podem incluir a montagem de sistemas de arquivos adicionais, configuração de rede básica, etc.
4. **Transição para o Sistema de Arquivos Raiz Permanente**:
	- Uma vez que todos os drivers e módulos necessários estão carregados, o `initrd` monta o sistema de arquivos raiz permanente especificado no parâmetro de inicialização (`root=...`).
	- O controle é então passado do `initrd` para o sistema de arquivos raiz permanente.
5. **Desmontagem do Initrd**:
	- O `initrd` é desmontado, e o sistema de arquivos raiz permanente assume o controle.
	- O processo de inicialização continua com o sistema de arquivos raiz permanente.

## Init System

- O init system é o **primeiro processo iniciado pelo kernel** e é o processo **pai de todos** os outros processos no sistema. 
- Ele é responsável por inicializar e gerenciar os serviços do sistema, montar sistemas de arquivos adicionais, e gerenciar o shutdown e o reboot do sistema.

### SysVinit

- **SysVinit** é um sistema de inicialização tradicional usado em muitas distribuições Linux mais antigas. 
- Ele é baseado no sistema de inicialização System V usado em Unix. 
- As principais características e etapas do SysVinit incluem:
6. **Script **`**/etc/inittab**`:
	- O arquivo `/etc/inittab` define os níveis de execução (runlevels) e os scripts que devem ser executados em cada nível.
7. **Níveis de Execução (Runlevels)**:
	- SysVinit usa níveis de execução para definir o estado do sistema. Cada nível de execução tem uma série de scripts associados que são executados quando o sistema entra naquele nível.
	- Os níveis de execução comuns incluem:
		- `0`: Desligar o sistema
		- `1`: Modo de usuário único (resgate)
		- `2-5`: Níveis de multiusuário (distribuições podem variar)
		- `6`: Reiniciar o sistema
8. **Scripts de Inicialização**:
	- Os scripts de inicialização são armazenados em diretórios como `/etc/rc.d/` ou `/etc/init.d/`.
	- Cada nível de execução tem seus próprios diretórios (`/etc/rc[0-6].d/`) contendo links simbólicos para scripts de inicialização.
	- Os scripts são executados em ordem alfabética dentro desses diretórios.

### Systemd

- **Systemd** é um sistema de inicialização mais moderno que visa superar as limitações do SysVinit. 
- Ele introduz várias melhorias e novas funcionalidades. 
- As principais características e etapas do systemd incluem:
9. **Unidades (Units)**:
	- Systemd usa unidades (`units`) para definir e gerenciar serviços, montagens, dispositivos, e outros recursos do sistema.
	- Tipos de unidades incluem `service`, `mount`, `device`, `target`, e muitos outros.
		- `service` (serviço): essa unidade corresponde a um **daemon** que pode ser iniciado (start), parado (stop), reiniciado (restart) e recarregado (reload);
		- `socket`: essa unidade encapsula um socket no sistema de arquivos ou na Internet. **Cada unidade socket tem uma unidade service equivalente**;
		- `device`: essa unidade encapsula um dispositivo. O device fica no diretório /dev
		- `target` (alvo): essa unidade é usada para **agrupamento lógico de unidades de service**, **socket e device**. Os targets **correspondem ao runlevels** (níveis de execução) do SysVinit, eles definem os serviços que devem estar presentes para que o sistema seja executado e esteja ativo nesse estado;
	- Para verificar o nível de execução usado no SystemD, utilize o comando: `systemctl get-default`;
	- As unidades são configuradas usando arquivos `.service`, `.mount`, etc., localizados em `/etc/systemd/system/` e `/usr/lib/systemd/system/`.
	- Para reinicializar o sistema, digite: `systemctl reboot`;
	- Para parar o sistema, basta entrar com: `systemctl shutdown`.
10. **Dependências e Paralelismo**:
	- Systemd **permite definir dependências entre unidades,** o que** ajuda a garantir que os serviços sejam iniciados na ordem correta.**
	- Suporta **inicialização paralela**, permitindo que vários serviços sejam iniciados simultaneamente, resultando em tempos de inicialização mais rápidos.
11. **Targets**:
	- Substitui os níveis de execução do SysVinit com `targets`, que são agrupamentos de unidades. 
	- Exemplos incluem `multi-user.target`, `graphical.target`, e `rescue.target`.
	- Targets permitem configurar estados do sistema de maneira mais flexível.
12. **Journald**:
	- Systemd inclui um sistema de registro centralizado chamado `journald`, que coleta e armazena logs de sistema e de serviços.
	- Logs podem ser acessados usando o comando `journalctl`.
13. **Gerenciamento de Serviços**:
	- Serviços podem ser gerenciados usando comandos como `systemctl start`, `systemctl stop`, `systemctl restart`, e `systemctl status`.
	- `reload`: Atualiza a configuração do serviço. Caso ele não permita a reconfiguração de forma online, não terá efeito. Exemplo: `systemctl reload nfs-server.service`

### Diferenças Principais entre SysVinit e Systemd

| Característica | SysVinit | Systemd |
| --- | --- | --- |
| **Modelo de Inicialização** | Baseado em níveis de execução (runlevels) | Baseado em unidades (units) e targets |
| **Configuração** | Arquivo `/etc/inittab` e scripts em `/etc/rc.d/` | Arquivos de unidade em `/etc/systemd/system/` |
| **Paralelismo** | Inicialização sequencial | Inicialização paralela |
| **Dependências** | Limitadas, baseada na ordem dos scripts | Suporte completo a dependências entre unidades |
| **Registro de Logs** | Syslog | Journald |
| **Flexibilidade e Modularidade** | Menos flexível e modular | Alta flexibilidade e modularidade |
| **Tempos de Inicialização** | Mais lento | Mais rápido devido ao paralelismo |

# Gerenciamento de Processos

## Fork Off and Die

- Quando o pai de um processo morre, o comportamento padrão do filho é ser adotado pelo processo init
- Além disso, como um processo herda o terminal do processo pai, ao ser adotado pelo init, o processo filho irá herdar o terminal do init (no caso, como o init não tem terminal, o processo filho irá ficar sem terminal).
- Exemplo:
	- O processo pai poderia ser, por exemplo, um “service sshd start”. 
	- Esse processo será criado, executado e finalizado, ele não precisa ficar em execução eternamente em segundo plano. 
	- Ele gerará, porém, um sshd vinculado ao init que ficará em constante execução aguardando solicitações de acesso remoto. 
	- Desse modo, esse sshd é um processo filho que será adotado pelo init, enquanto o “servisse sshd start” é finalizado.

## Fork

- Cria um processo filho, que se diferencia a partir do processo-pai somente em suas identificações (**PID** e **PPID**)
- O fork consome tempo e memória requerida para **duplicar as tabelas do processo-pai.**

## Kill

- O comando kill é utilizado para controlar processos por sinais
- É preciso ser o dono do processo ou o usuário root para terminar ou destruir o processo
- Sua principal função é, de fato, interromper processos, mas ele não serve apenas para isso.
- Sinais
| HUP | 1 | Este sinal é enviado automaticamente quando se desconecta a sessão ou se fecha o terminal. Usado também para resetar processos.  |
| --- | --- | --- |
| INIT | 2 | Interrompe o processo |
| KILL | 9 | Termina incondicionalmente e de forma drástica. Pode corromper dados |
| TERM | 15 | Encerra o processo de foma elegante, possibilita que os arquivos sejam fechados |
| TSTP | 20 | Termina para continuar depois. Corresponde a Ctrl + Z ou FG |

## Jobs

- O comando jobs mostra os processos que estão parados ou rodando em segundo plano.
- Processos em segundo plano são iniciados usando o símbolo “&” no final da linha de comando ou através do comando bg.
- É útil para ser utilizado junto com os comandos `fg ` e `bg`
	- FG: Coloca um processo anteriormente interrompido em primeiro plano
	- BG: Coloca em segundo plano

## Outros comandos relacionados a gerenciamento de processos

- **nohup:** Inicia a execução de um processo e impede que seja interrompido
- **fuser:** Exibe os processos e usuários que estão utilizando um arquivo, diretório ou socket
- **vmstat: **Relata informações sobre processos, memória, paginação, E/S, traps e atividades de CPU
- **nice:** Inicia um processo com a prioridade especificada (120 padrão)
	- A definição da prioridade de um processo é feita automaticamente e dinamicamente pelo kernel. Nice é um atributo que influencia nesta prioridade
	- Enquanto a prioridade varia entre 100 a 139, o nice varia de -20 a +19 (para root) ou de 1 a 19 para os demais usuários
	- O valor 10 é o padrão de execução
- **renice: **Recalcula o nice de um processo em execução
- **ionice:** Define o nice de um processo de I/O

# Filtros e Processamento de Texto

- `tac`
	- Cat invertido
- `nl`
	- Mostra o conteúdo junto ao número da linha
- `less`
	- Similar ao `more`
- `split`
	- Divide o arquivo em vários menores
- `join`
	- Faz a união de dois arquivos distintos
- `diff`
	- Compara dois arquivos
	- O formato de saída é compatível com o comando `patch`

# ACL’s

Os três últimos bits são utilizados para definir permissões adicionais para os arquivos e diretórios. Os três modelos especiais para controle de acesso são denominados Set User ID (SUID), Set Group ID (SGID) e Sticky Bit (Sticky).

![[Untitled 527.png]]

As permissões especiais alteram o comportamento padrão do sistema operacional na manipulação dos arquivos que possuem tais permissões.  Então, vejamos qual o funcionamento do sistema operacional para cada uma dessas permissões.

A propriedade SUID permite ajustar o ID do usuário (SetUID), é aplicada apenas para arquivos executáveis não tendo qualquer efeito sob diretórios. Quando um arquivo executável com a propriedade SUID aplicada, entrar em execução, o programa deverá rodar com o ID do proprietário do arquivo, não com o ID do usuário que o executou. Em outras palavras, o processo do arquivo executável utilizando o acesso SUID será executado como se estivesse sido iniciado pelo dono do arquivo. Esta permissão de acesso só pode ser definida no campo de execução do proprietário do arquivo, atribuição realizada com a letra “s”. Tal funcionalidade proporciona a criação e utilização de programas privilegiados que podem usar arquivos que são normalmente inacessíveis a outros usuários.

![[Untitled 528.png]]

Alternativamente, a propriedade SGID é utilizada para ajustar o ID do grupo. Esta propriedade tem uma função bastante semelhante a propriedade SUID para arquivos executáveis, contudo esta propriedade tem um efeito especial quando aplicado sob diretórios. Quando esta permissão é aplicada em um diretório, os novos arquivos que serão criados dentro deste diretório assumem o mesmo ID de grupo do diretório com a propriedade SGID aplicada. Esta permissão de acesso especial só pode ser definida no campo que habilita a execução para o grupo, atribuição realizada com a letra “s”.

![[Untitled 529.png]]

Por último, o bit de permissão *Sticky*, em português o termo mais adequado seria “Aderente”. Esta propriedade quando habilitada em arquivos executáveis faz com que o sistema mantenha uma imagem do programa em memória depois que o programa finalizar. Deste modo, é possível aumentar o desempenho, pois isto permite realizar um cache do programa para a memória, a próxima vez que este arquivo for executado, ele será carregado mais rápido.

Adicionalmente, a propriedade *Sticky* pode ser utilizada para aumentar a segurança, pois quando aplicada sobre os diretórios, impede que outros usuários excluam ou renomeiem os arquivos nos quais não são donos. Assim, este diretório estará em modo *append-only* (somente incremento), apenas o proprietário do arquivo pode excluir e renomear esses arquivos. Esta propriedade é útil para gerenciar arquivos em diretórios temporários. Esta permissão de acesso especial é definida no campo que habilita a execução para outros usuários, atribuição realizada com a letra “t”.

![[Untitled 530.png]]

## **Listas de controle de acesso no Linux**

A maioria dos sistemas operacionais baseados no Unix suportam as listas de controle de acesso. No Linux denominada como lista de controle de acesso estendida.

No Linux é possível conceder uma lista de ID´s de usuários e grupos a um arquivo ou diretório, para isto é utilizado o comando setfacl. Este comando permite associar qualquer número de usuário ou grupo a um determinado tipo de objeto (arquivo ou diretório), fornecendo as permissões de leitura, escrita e execução de forma individual.

Esta abordagem fornece uma flexibilidade maior na hora de atribuir as permissões de acesso. Neste sentido, um arquivo além ser protegido pelo mecanismo de acesso a arquivos tradicional, adicionalmente pode dispor de uma ACL estendida. Os arquivos Linux fornecem um bit de proteção adicional para indicar se este arquivo possui uma ACL estendida ou não, este bit é representado por um sinal de adição (+).

![[Untitled 531.png]]

O proprietário do arquivo “arquivo1.txt” é o usuário “aluno”, por sua vez o grupo proprietário é “equipe1”. Podemos utilizar o comando getfacl para visualizar as permissões na ACL estendida. Observe que adicionalmente, foram concedidas duas outras permissões na ACL estendida, conforme disposto na imagem abaixo existem dois usuários nomeados, usuários aluno2 e aluno3, ambos com permissão de leitura e escrita.

![[Untitled 532.png]]

1. As permissões das classes proprietário e outros, estabelecido pelos 9 bits de proteção do modelo de controle de acesso tradicional são correspondente as ACLs estendidas.

1. A permissões da classe grupo representam as permissões máximas que podem ser atribuídas aos usuários ou grupos nomeados, com exceção do proprietário do arquivo. Neste último, a permissão funciona como uma máscara.

1. Todos os usuários e grupos definidos na ACLs estendidas que estão associados a um arquivo, definem sua permissão na ACL estendida utilizando um campo de permissão de 3 bits (leitura, escrita e execução). As permissões listadas para um usuário ou grupo nomeado são verificadas no campo referente a máscara. Qualquer permissão que não esteja presente neste campo deve ser automaticamente desabilitada.

# Red Hat Enterprise Linux

## SSSD

- System Security Services Daemon
- Fornece acesso a diferentes fontes de identidade e autenticação
- Integra com o LDAP, Kerberos, Active Directory e outros
- Faz cache permitindo login mesmo com o servidor de domínio fora do ar
- Reduz a complexidade dos serviços PAM e NSS

## Red Hat Satellite

- Fornece um conjunto abrangente de ferramentas para a administração de infraestruturas de TI, facilitando a implementação, configuração, atualização, e manutenção de servidores em larga escala
- Com o Satellite é possível gerenciar um grupo de servidores de forma centralizada
- Funcionalidades
	- Aplicação de patches e atualizações
	- Provisionamento de sistemas (bare-metal, virtualização e cloud)
	- Utiliza ferramentas como puppet e Ansible
	- Monitoramento, saúde e desempenho
- Estrutura
	- Satellite Server: Serviço central
	- Capsule Server: Servidores intermediários, ajudam a distribuir carga e fornecer serviços de gerenciamento
	- Hammer CLI: CLI para interagir com o serviço Satellite
	- Foreman: Interface web

## NFtables

- Framework de filtragem de pacotes no kernel Linux
- Destinado a substituir o iptables
- Funciona de forma tanto stateful quanto stateless

## Network Manager

- `/etc/sysconfig/network` não é mais utilizado para configurar interfaces de rede
- Atualmente as configurações de rede são gerenciadas principalmente através do **NetworkManager**
- O NetworkManager utiliza arquivos de configuração localizados no diretório `/etc/NetworkManager/` e suas subpastas, como `/etc/NetworkManager/system-connections/`, onde são armazenadas as configurações de rede específicas.
- Para configurar a rede no RHEL 8, geralmente usamos ferramentas como `**nmtui**` (Network Manager Text User Interface) ou `**nmcli**` (Network Manager Command Line Interface)
- **Exemplo de comando com nmcli: **`nmcli con add type ethernet ifname eth0 ip4 192.168.1.100/24 gw4 192.168.1.1`

## Firewalld

- **Firewalld** é um serviço de gerenciamento de firewall para sistemas Linux que fornece uma interface dinâmica para gerenciar regras de firewall. 
- Ele é projetado para ser mais fácil de usar e mais flexível do que as abordagens tradicionais de firewall, como iptables. 

### Principais Características do Firewalld

14. **Zonas de Firewall**:
	- As zonas permitem a definição de políticas de segurança específicas para diferentes áreas da rede (por exemplo, home, work, public). 
	- Cada zona possui suas próprias regras de firewall e configurações.
15. **Configuração Dinâmica**:
	- As regras de firewall podem ser adicionadas, modificadas ou removidas em tempo real sem precisar reiniciar o serviço, permitindo ajustes sem interrupções na conectividade de rede.
16. **Suporte a IPv4, IPv6, Ethernet Bridges e Firewall Zones**:
	- Firewalld pode gerenciar regras para IPv4, IPv6, pontes Ethernet e zonas de firewall.
17. **Interação com Serviços e Aplicativos**:
	- Integração com serviços e aplicativos para configurar automaticamente regras de firewall necessárias para a operação desses serviços.
18. **Interface Gráfica e de Linha de Comando**:
	- Firewalld fornece tanto uma interface gráfica (firewall-config) quanto uma interface de linha de comando (firewall-cmd) para gerenciamento.

### Comandos Básicos do Firewalld

- **Verificar o Status do Firewalld**: `firewall-cmd --state`
- **Listar Zonas Ativas**: `firewall-cmd --get-active-zones`
- **Adicionar uma Regra Permanente para Permitir SSH**: `firewall-cmd --zone=public --add-service=ssh --permanent`
- **Remover uma Regra Permanente para Permitir SSH**: `firewall-cmd --zone=public --remove-service=ssh --permanent`
- **Recarregar as Configurações do Firewalld**: `firewall-cmd --reload`
- **Listar Todas as Regras em uma Zona**: `firewall-cmd --zone=public --list-all`

### Relacionamento com NFTables

- Firewalld pode usar diferentes backends para aplicar suas regras de firewall. 
- Tradicionalmente, ele usava `iptables` como backend, mas com o advento do `nftables`, o suporte para `nftables` como backend foi adicionado.
- **NFTables como Backend**:
	- Em sistemas que usam `nftables`, Firewalld pode ser configurado para usar `nftables` em vez de `iptables` para aplicar as regras de firewall.
	- Usar `nftables` como backend pode trazer benefícios como melhor desempenho e uma sintaxe mais limpa e moderna para a aplicação de regras.
- **Configuração para usar NFTables**:
	- A configuração do Firewalld para usar `nftables` pode ser feita ajustando o backend no arquivo de configuração do Firewalld.

### Exemplo de Configuração

- Para configurar Firewalld para usar `nftables` como backend, edite o arquivo de configuração `/etc/firewalld/firewalld.conf` e ajuste a seguinte linha: `FirewallBackend=nftables`
- Após editar o arquivo de configuração, reinicie o serviço Firewalld para aplicar as mudanças:  `systemctl restart firewalld`

## SELinux

- **SELinux (Security-Enhanced Linux)** é uma implementação de controle de acesso obrigatório (MAC) integrada ao kernel Linux. 
- Ele foi originalmente desenvolvido pela NSA (National Security Agency) dos Estados Unidos para aumentar a segurança dos sistemas Linux, fornecendo um mecanismo robusto para definir e aplicar políticas de segurança que controlam a forma como os processos e usuários podem acessar recursos no sistema.

### Principais Características do SELinux

19. **Controle de Acesso Obrigatório (MAC)**:
	- SELinux usa MAC, o que significa que as políticas de segurança são impostas pelo sistema e não podem ser alteradas pelos usuários finais.
	- Diferente do Controle de Acesso Discricionário (DAC), onde os proprietários de arquivos têm controle sobre os direitos de acesso, MAC impõe políticas de segurança rígidas que não podem ser facilmente ignoradas.
20. **Políticas de Segurança**:
	- As políticas de SELinux definem quais ações são permitidas para cada usuário, processo e recurso no sistema.
	- As políticas são compostas por regras que especificam permissões detalhadas.
21. **Modos de Operação**:
	- **Enforcing**: O SELinux aplica e reforça as políticas de segurança, bloqueando ações não autorizadas e registrando eventos.
	- **Permissive**: O SELinux não bloqueia ações não autorizadas, mas registra eventos que violariam as políticas de segurança. 
		- Esse modo é útil para debug e desenvolvimento de políticas.
	- **Disabled**: O SELinux está desativado e não aplica nenhuma política de segurança.
22. **Contextos de Segurança**:
	- SELinux associa um contexto de segurança a cada arquivo, diretório, processo e recurso do sistema, que consiste em atributos como usuário, papel, tipo e nível de segurança.

### Componentes do SELinux

23. **Políticas**:
	- As políticas são coleções de regras que definem as permissões para todos os objetos do sistema. 
	- Existem políticas predefinidas (como a política de destino) e políticas personalizadas.
24. **Contextos de Segurança**:
	- Cada objeto no sistema (arquivos, processos, etc.) tem um contexto de segurança que define suas permissões de acesso.
25. **Utilitários de Linha de Comando**:
	- **getenforce**: Exibe o modo atual do SELinux.
	- **setenforce**: Altera o modo de operação do SELinux (enforcing ou permissive).
	- **semanage**: Gerencia definições de políticas e contextos de segurança.
	- **restorecon**: Restaura contextos de segurança para arquivos e diretórios.
26. **Logs de Auditoria**:
	- SELinux registra eventos de segurança em logs, que podem ser revisados para auditoria e debug.

### Exemplo de Uso e Configuração

- Verificando o Modo Atual do SELinux `getenforce`
- Alterando o Modo do SELinux para Permissive `sudo setenforce 0`
- Alterando o Modo do SELinux para Enforcing `sudo setenforce 1`

### Verificando Contextos de Segurança

- Para listar os contextos de segurança de arquivos e diretórios, use o comando `ls -Z`: `ls -Z /etc/passwd`
- A saída incluirá o contexto de segurança associado ao arquivo.

### Restaurando Contextos de Segurança

- Se os contextos de segurança forem alterados incorretamente, você pode restaurá-los usando `restorecon`: `sudo restorecon -Rv /path/to/directory`

### Perfis

- Usuários do sistema podem ser mapeados em perfis padrões existentes dentro do SELinux:
	- **xguest_u :** este usuário tem acesso às ferramentas GUI e a rede está disponível através do navegador Firefox.
	- **user_u : **este usuário tem mais acesso do que as contas de convidado (GUI e rede), mas não pode alternar entre usuários executando su ou sudo.
	- **system_u : **este usuário destina-se a executar serviços do sistema e não deve ser mapeado para contas de usuário regulares.
	- **staff_u : **mesmos direitos que user_u, exceto que pode executar o comando sudo para ter privilégios de root.

# PAM

- Pluggable Authentication Module
- O PAM é um **conjunto de bibliotecas** que permite aos administradores configurar como as aplicações **autenticam** os usuários.
- Ele fornece uma **camada de abstração** entre os serviços do sistema e os mecanismos de autenticação.
- As configurações do PAM são geralmente encontradas em arquivos no diretório `/etc/pam.d/`
- O PAM permite implementar **políticas de autenticação** complexas e em camadas, aumentando significativamente a segurança do sistema.
- Administradores podem facilmente ajustar as políticas de autenticação sem modificar as aplicações individuais.
- O PAM pode ser integrado com outros sistemas de autenticação, como **LDAP**, **Kerberos**, ou** autenticação biométrica**, tornando-o uma ferramenta versátil para hardening.

## Interfaces PAM

- **Auth**
	- Valida a identidade do usuário, frequentemente solicitando uma senha
- **Account**
	- Lida com a verificação da conta, verificando condições como pertencimento a grupos ou restrições de horário
- **Session**
	- Gerencia atualizações de senha, incluindo verificações de complexidade ou prevenção de ataques de dicionário
- **Password**
	- Gerencia ações durante o início ou fim de uma sessão de serviço, como montagem de diretórios ou definição de limites de recursos
