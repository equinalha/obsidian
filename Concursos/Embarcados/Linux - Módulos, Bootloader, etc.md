---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2025-04-29T14:41:00
Owner:
  - Eduardo Quinalha
---
[https://sergioprado.blog/page/2/](https://sergioprado.blog/page/2/)

[https://www.youtube.com/watch?v=ohJzUe5CJ94](https://www.youtube.com/watch?v=ohJzUe5CJ94)

# Compilação do Kernel e Módulos

- Após a compilação do kernel é necessário a instalação dos módulos

```bash
sudo make modules_install
```

## Trabalhando com módulos

- Módulos podem ser carregados e descarregados em tempo de execução, sem necessidade de reboot
- Ferramentas:
	- `modprobe`
		- Forma mais recomendada de carregamento de um módulo
		- Lida com dependências automaticamente
		- `sudo modprobe <nome_do_módulo>`
		- Pode ser usado para remover módulos
		- `sudo modprobe -r <nome_do_módulo>`
	- `insmod`
		- Carrega o módulo diretamente a partir de um arquivo
		- Não lida com dependências
		- Deve ser fornecido o caminho completo para o módulo
		- `sudo insmod /caminho/para/modulo.ko`
	- `lsmod`
		- Lista os módulos atualmente carregados no kernel
		- Exibe informações como o uso de memória de cada um
	- `rmmod`
		- Descarrega o módulo
		- Não lida com dependências
		- Ele não pode estar em uso
		- Caso esteja em uso e ainda assim deseje forçar a remoção:
			- `sudo rmmod -f <nome_do_módulo>`
	- `modinfo`
		- Exibe informações detalhadas sobre o módulo sem carregá-lo
- Carregamento automático
	- Os módulos a serem carregados automaticamente durante o boot devem ser listados no arquivo:
		- `/etc/modules`

## Desenvolvimento de módulos

- Para o desenvolvimento de módulos do kernel, é necessário o código fonte ou os headers deste
- Módulos são normalmente desenvolvidos em C
- Estrutura básica de um módulo

```c
#include <linux/init.h>     // Necessário para as macros de inicialização e finalização
#include <linux/module.h>   // Necessário para todos os módulos do kernel

MODULE_LICENSE("GPL");      // Define a licença do módulo
MODULE_AUTHOR("Seu Nome");  // Define o autor
MODULE_DESCRIPTION("Exemplo simples de módulo do kernel");  // Descrição do módulo

// Função que é chamada quando o módulo é carregado
static int __init hello_init(void) {
    printk(KERN_INFO "Hello, World! Módulo carregado.\n");
    return 0;  // Retorna 0 se o módulo for carregado com sucesso
}

// Função que é chamada quando o módulo é descarregado
static void __exit hello_exit(void) {
    printk(KERN_INFO "Goodbye, World! Módulo descarregado.\n");
}

// Macros que indicam as funções de inicialização e finalização
module_init(hello_init);
module_exit(hello_exit);
```

- `**printk**`: Similar ao `printf` em programas de usuário, `printk` é usado para imprimir mensagens no nível do kernel. O argumento `KERN_INFO` define o nível de log (informativo neste caso).
- `**module_init()**`** e **`**module_exit()**`: Estas macros indicam ao kernel quais funções executar quando o módulo for carregado ou descarregado.

# Boot do Linux

## Bootloader

### Lilo

- Descontinuado
- Sem suporte a novos sistremas de arquivo

### SYSLINUX

- Bootloader para partições FAT32
- Utilizado para instaladores do linux
- Principal bootloader utilizado para sistemas embarcados
- permite adicionar temas gráficos simples, menus interativos, animações e até suporte a resolução gráfica personalizada, o que é útil para criar imagens "live" atraentes.
- é capaz de carregar imagens de kernel, initrd e outros arquivos necessários diretamente da mídia removível.
- Configuração:
	- Feita através do arquivo syslinux.cfg
```bash
DEFAULT linux
LABEL linux
  KERNEL /vmlinuz
  APPEND initrd=/initrd.img root=/dev/sda1
TIMEOUT 50
PROMPT 1
```
	- Para instalar no dispositivo utiliza-se: `syslinux -i /dev/sdX1`

### GRUB2

- Padrão atual
- Assume após o BIOS ou UEFI
- Insere o kernel na memória e entrega o controle a este
- Configurações
	- localizado em `/boot/grub/grub.cfg`

## RootFS

- sistema de arquivos raiz usado pelo kernel do Linux
- Ponto de partida de toda a estrutura de diretórios do sistema Linux e contém os arquivos e diretórios essenciais necessários para que o sistema operacional funcione, como `/bin`, `/sbin`, `/lib`, `/etc`, e outros
- Refere especificamente ao sistema de arquivos que o kernel monta como o sistema de arquivos raiz no **momento da inicialização**
- Existem três abordagens comuns para** fornecer o RootFS durante a inicialização**:
	- Sistema de arquivos embutido no kernel
		- Normalmente nos formatos CPIO ou initramfs
		- Comum em dispositivos limitados
		- O SO é carregado na memória e nunca é desmontando ou trocado
	- Initramfs
		- Técnica usada nas distros moderndas
		- Imagem compactada que contém um sistema de arquivos básico
	- Sistema de arquivos a partir de dispositivos de armazenamento
		- Neste caso o RootFS normalmente está localizado em uma partição do disco
- Exemplo: 

```shell
mkinitcpio -g /boot/initramfs-linux.img
```

## Processo de Boot

### Em sistemas domésticos

- O **bootloader** é responsável por **carregar o kernel na memória** e passar para ele algumas informações importantes.
- Kernel monta o initramfs como RootFS inicial.
- Kernel executa `/init` ou script similar dentro do initramfs.
- O script `/init` localiza o RootFS definitivo (por exemplo, `/dev/sda1`).
- O comando `pivot_root` é usado para montar o RootFS definitivo em `/`.
- O sistema de arquivos initramfs é desmontado, e o sistema continua a inicialização a partir do RootFS definitivo.

### Em sistemas embarcados

- O bootloader passa diretamente o parâmetro de qual dispositivo contém o sistema de arquivos raiz (geralmente algo como `root=/dev/sda1`) na linha de comando do kernel. 
- O kernel então usa essa informação para montar diretamente o **RootFS real**.
- O kernel, ao receber essa informação do bootloader, utiliza os drivers necessários (inicialmente embutidos no próprio kernel ou carregados via initramfs, se presente) para montar o sistema de arquivos diretamente a partir do dispositivo de armazenamento. 
- O RootFS real é então montado como o sistema de arquivos raiz em `/`.
- Após montar o RootFS diretamente do disco, o kernel localiza e executa o processo de inicialização padrão, que geralmente é `/sbin/init`. 
- Esse processo inicializa todos os outros serviços do sistema (daí o nome init, abreviação de "initialization"). 
- Em sistemas modernos, o init pode ser substituído por outros sistemas de gerenciamento, como o **systemd** ou o **Upstart**.

# Montando uma Distribuição Básica

## 1. Kernel

- Baixar e compilar o kernel linux, usando apenas funcionalidades básicas

```shell
tar -xvf linux-x.x.x.tar.xz
cd linux-x.x.x
make menuconfig
make -j$(nproc)
sudo make modules_install
sudo make install
```

## 2. Criação do RootFS

- Estrutura mínima

```shell
mkdir -p rootfs/{bin,sbin,etc,proc,sys,dev,tmp,usr/lib}
```

- Populando o RootFS
	- Uma maneira comum de criar binários básicos é usar o **BusyBox**, que fornece implementações mínimas de várias ferramentas Unix em um único binário.

```shell
cp /usr/local/bin/busybox rootfs/bin
ln -s busybox rootfs/bin/sh  # BusyBox vai atuar como shell
```

- Criando arquivos de Dispositivos
	- Alguns nós básicos são necessários em `/dev` para o funcionamento inicial:
		- `console`, `null`, `tty`, etc
	- O comando `mknod `permite a criação destes nós
```shell
mknod -m 600 rootfs/dev/console c 5 1
mknod -m 666 rootfs/dev/null c 1 3
```

## 3. Criação do Initramfs (Opcional)

- Para gerar a imagem do initramfs, crie um arquivo CPIO compactado com a estrutura do seu RootFS:
```shell
bash
Copiar código
cd rootfs
find . | cpio -o --format=newc | gzip > ../initramfs.img
```
- Durante a configuração do kernel, você pode embutir o initramfs diretamente, configurando-o durante o processo de compilação, em:
```shell
General setup → Initial RAM filesystem and RAM disk (initramfs/initrd) support → initramf
```

## 4. Configuração do bootloader

# Desenvolvimento

## Aplicações

- As aplicações em um sistema Linux geralmente são executadas no **espaço do usuário, **o que significa que elas não têm acesso direto ao hardware, sendo mediadas pelo **kernel** através de chamadas de sistema (syscalls)
- Considerações de Segurança:
	- **Privilégios Mínimos**: Sempre execute serviços com o mínimo de privilégios necessários (por exemplo, evitar execução como root, usar `setuid` e `setgid`).
		- O **bit setuid** (Set User ID) permite que um arquivo executável seja executado com as permissões **do proprietário do arquivo**, em vez das permissões do usuário que o executa. 
		- Isso significa que, quando um programa com o bit setuid definido é executado, ele assume os privilégios do **dono do arquivo**, não do usuário que está executando o programa.
		- Pode ser definido da seguinte maneira:
```shell
$ chmod u+s /path/to/executable
$ ls -l /path/to/executable

-rwsr-xr-x 1 root root 12345 Oct 14 10:30 /path/to/executable

# O s no lugar de x nas permissões de usuário (rws) indica que o bit setuid está ativado.
```
	- **Sandboxing**: Utilize mecanismos como `seccomp`, `cgroups` ou **containers** para limitar o acesso de aplicações e processos ao sistema.
	- **Capacidades do Kernel**: Em vez de fornecer ao processo direitos de superusuário completos, considere usar as **capacidades do kernel** (`capabilities`) para conceder permissões específicas.
		- As **Linux Capabilities** são uma forma de dividir os privilégios tradicionais de **root** (usuário administrador) em diferentes unidades menores e mais controladas, chamadas de **capabilities**.
		- As **capabilities** quebram o poder total do root em permissões individuais.
		- Com as **capabilities**, é possível restringir as permissões de um processo, mesmo que ele seja executado como root, para limitar o impacto de possíveis falhas de segurança.
		- Para verificar quais capabilities estão associadas a um processo, você pode usar a ferramenta `**pscap**` ou o comando `**getcap**`.
		- Para definir capabilities em um arquivo executável, você pode usar o comando `**setcap**`.
```shell
setcap cap_net_bind_service=+ep /usr/bin/my_program
```
		- O `+ep` indica que a capability é efetiva (`e`) e permitida (`p`).
			- As capabilities estão divididas em três conjuntos para cada processo:
			1. **Permitted (P)**: Capabilities que o processo tem permissão de ativar.
			2. **Inheritable (I)**: Capabilities que podem ser herdadas por processos filhos.
			3. **Effective (E)**: Capabilities ativas, ou seja, aquelas que o processo realmente pode usar.
	- **Controle de Acesso Mandatório (MAC)**: Ferramentas como SELinux ou AppArmor podem ser utilizadas para aplicar políticas de segurança rígidas a serviços e aplicações.

## Serviços

- Processos de longa execução
- Gerenciados pelo sistema
- Executados em segundo plano (`Daemons`)
- O desenvolvimento de serviços no Linux envolve tanto a criação do código do serviço quanto a integração e gerenciamento desse serviço pelo sistema, utilizando ferramentas como **systemd**.
- Integração com o `SystemD`
	- É necessário criar um arquivo de unidade do systemd: `/etc/systemd/system/meu-servico.service`
```shell
[Unit]
Description=Meu Serviço Exemplo
After=network.target

[Service]
ExecStart=/usr/bin/python3 /path/to/meu_servico.py
Restart=always

[Install]
WantedBy=multi-user.target
```
	- Ativar e iniciar o serviço: 
```shell
sudo systemctl enable meu-servico
sudo systemctl start meu-servico
```

## Syscalls

- Permitem que o software em **user space** solicite serviços ao **kernel**.
- Principais `**syscalls**`** **utilizadas em aplicações:
	- `**open()**`**, **`**read()**`**,**`** write()**`: Para trabalhar com arquivos.
	- `**socket()**`**, **`**bind()**`**, **`**listen()**`**, **`**accept()**`: Para comunicação de rede.
	- `**fork()**`**, **`**exec()**`**, **`**wait()**`: Para criação e gerenciamento de processos.
	- `**ioctl()**`: Para realizar operações de I/O em dispositivos especiais.

## Aplicações Multithread e Multiprocessos

- O Linux oferece suporte a **POSIX threads (pthreads)**, que são amplamente utilizados em aplicações C/C++

```c
#include <pthread.h>
#include <stdio.h>

// Função Callback que será chamada pela Thread
void* myThread(void* arg) {
    printf("Thread está executando!\n");
    return NULL;
}

int main() {
    pthread_t thread;
    pthread_create(&thread, NULL, myThread, NULL); // Criação da thread
    pthread_join(thread, NULL); // Espera a thread terminar
    return 0;
}
```

- A função `**pthread_create**`é usada para criar uma nova thread.
	- O **primeiro argumento** é o endereço da variável `thread`, que receberá o identificador da thread criada.
	- O **segundo argumento** (`NULL` neste caso) permite definir atributos da thread, como prioridade ou pilha de execução. Se passado como `NULL`, usa os atributos padrão.
	- O **terceiro argumento** é a função que será executada pela thread, no caso, a função `myThread`.
	- O **quarto argumento** é o parâmetro que será passado para a função `myThread`. Neste exemplo, `NULL` é passado, já que a função não utiliza nenhum argumento.
- `**pthread_join**`é uma chamada que bloqueia a execução do **main thread **até que a thread criada termine sua execução.
	- O **primeiro argumento** é o identificador da thread que queremos esperar.
	- O **segundo argumento** é um ponteiro para o valor de retorno da thread. 
	- Neste caso, estamos passando `NULL`, pois não nos interessa o valor de retorno.
	- O`**pthread_join**`é importante para garantir que o programa principal (ou outras threads) espere até que uma thread específica termine. 
	- Caso contrário, o programa poderia encerrar antes que a nova thread tivesse a chance de executar.

## Comunicação Entre Processos (IPC)

- Tipos de IPC:
	- **Sinais**: Para enviar notificações entre processos (usando `kill` ou `signal`).
	- **Pipes** e **Named Pipes (FIFOs)**: Para comunicação de dados entre processos pai e filho.
	- **Sockets**: Para comunicação entre processos locais ou em redes.
	- **Shared Memory**: Para permitir que processos diferentes compartilhem a mesma região de memória, otimizando a comunicação.
	- **Semáforos**: Para controlar o acesso a recursos compartilhados.

# Drivers

- Com exceção de drivers de rede, os driver linux funcionam através de uma **abstração por arquivos**
- Por exemplo, considere o arquivo `/dev/ttys0`
	- PS: Os arquivos de device driver são criados pelo comando `mknod`
- Um driver é escrito de forma a implementar algumas funções básicas: `open`, `close`, `read`, `write`, `ioctl`
- Estas funções **são callbacks**. Quando o usuário abrir o arquivo `/dev/ttys0`, o kernel irá chamar o driver correspondente e acionar a função `open`
- O Kernel reconhece o driver correspondente a cada arquivo do **virtual filesystem** através de dois números: `major` / `minor`
	- Estes números são alocados pelo Kernel quando o módulo for carregado com o uso do comando `modprobe`
- Os dispositivos podem ser de dois tipos
	- caractere
	- bloco

## Unified Device Model

![[Concursos/images/image 3.png]]

- Disponível a partir da versão 2.6 do Kernel
- Tem por objetivo criar **camadas de abstrações** que tornam o driver **portável**
- Tem 2 componentes
	- Frameworks → Padronização da interface exportada pelo driver
		- Padroniza o protocolo (linguagem utilizada)
	- Infraestrutura de barramento → Separação entre o driver e a descrição do dispositivo de hardware

### Framework

![[Concursos/images/image 4.png]]

- Alguns frameworks
	- TTY
		- Dispositivos seriais
	- INPUT
		- Dispositivos de entrada do usuário
		- mouse, teclado, touchscreen, joystick
	- FRAMEBUFFER
		- Saída de vídeo
	- ALSA
		- Dispositivos de som
	- LEDS
		- Usado em dispositivos com GPIO

### Infraestrutura de Barramento

![[Concursos/images/image 5.png]]

- Abstrai o driver da descrição do dispositivo do hardware (DMA, interrupção, etc..)
- Centraliza o acesso ao barramento de dispositivos
- Possibilita identificar hierarquicamente todos os dispositivos
- Permite o gerenciamento de energia
![[Concursos/images/image 6.png]]

### Device Tree

- Estrutura de dados que descreve o hardware
- Abstrai a descrição do hardware, separando-o do driver
- Identifica a topologia de hardware
- Muito utilizado em plataformas embarcadas
