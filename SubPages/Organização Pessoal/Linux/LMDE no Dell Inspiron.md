---

---
# Vídeo

Este notebook possui uma configuração conhecida como Optimus, na qual existem dois adaptadores de vídeo: Um acelerador 3d e um comum para economia de bateria

[http://wiki.debian.org/NvidiaGraphicsDrivers](http://wiki.debian.org/NvidiaGraphicsDrivers)

[https://wiki.debian.org/NVIDIA%20Optimus](https://wiki.debian.org/NVIDIA%20Optimus)

```javascript
$ lspci -nn | egrep -i "3d|display|vga"
0000:00:02.0 VGA compatible controller [0300]: Intel Corporation TigerLake GT2 [Iris Xe Graphics] [8086:9a49] (rev 03)
0000:01:00.0 3D controller [0302]: NVIDIA Corporation TU117M [GeForce MX450] [10de:1f97] (rev a1)
```

```javascript
$ nvidia-detect 
Detected NVIDIA GPUs:
0000:01:00.0 3D controller [0302]: NVIDIA Corporation TU117M [GeForce MX450] [10de:1f97] (rev a1)

Checking card: 00.0 3D controller
Your card is supported by the default drivers.
Your card is also supported by the Tesla 460 drivers series.
Your card is also supported by the Tesla 450 drivers series.
It is recommended to install the
    nvidia-driver
package.
```

A versão dos drivers a serem instalados é ***Version 470.103.01***

[https://us.download.nvidia.com/XFree86/Linux-x86_64/470.103.01/README/supportedchips.html](https://us.download.nvidia.com/XFree86/Linux-x86_64/470.103.01/README/supportedchips.html)

Passos

Blacklist nouveau:

```shell
sudo bash -c "echo blacklist nouveau > /etc/modprobe.d/blacklist-nvidia-nouveau.conf"
sudo bash -c "echo options nouveau modeset=0 >> /etc/modprobe.d/blacklist-nvidia-nouveau.conf"

sudo update-initramfs -u
```

```shell
apt install linux-headers-amd64
```

Adicionar os repositórios em **/etc/apt/sources.list**

```shell
# Debian Bullseye
deb http://deb.debian.org/debian/ bullseye main contrib non-free
# bullseye-backports
deb http://deb.debian.org/debian bullseye-backports main contrib non-free
```

Instalar os drivers

```shell
apt update
apt install -t bullseye-backports nvidia-driver firmware-misc-nonfree
apt install x11-xserver-utils
apt install nvidia-settings
```

Criar/editar o arquivo **/etc/X11/xorg.conf**

```shell
Section "ServerLayout"
    Identifier "layout"
    Screen 0 "nvidia"
    Inactive "intel"
EndSection

Section "Device"
    Identifier "nvidia"
    Driver "nvidia"
    BusID "<BusID for NVIDIA device here>" # e.g. PCI:1:0:0
EndSection

Section "Screen"
    Identifier "nvidia"
    Device "nvidia"
    Option "AllowEmptyInitialConfiguration"
EndSection

Section "Device"
    Identifier "intel"
    Driver "modesetting"
    BusID "<BusID for Intel device here>" # e.g. PCI:0:2:0
    #Option "AccelMethod" "none"
EndSection

Section "Screen"
    Identifier "intel"
    Device "intel"
EndSection
```

Criar/editar o arquivo **~/.xsessionrc**

```shell
xrandr --setprovideroutputsource modesetting NVIDIA-0
xrandr --auto
xrandr --dpi 96
```

Obs: O arquivo deve ser executável

## Configurar o Lightdm (se for o caso)

Criar o script de configuração: **/etc/lightdm/display_setup.sh**

```shell
xrandr --setprovideroutputsource modesetting NVIDIA-0
xrandr --auto
xrandr --dpi 96
```

Obs: O arquivo deve ser executável

Adicionar na configuração do arquivo **/etc/lightdm/lightdm.conf.d/70-linuxmint.conf**

```shell
[Seat:*]
user-session=cinnamon
display-setup-script=/etc/lightdm/display_setup.sh
```

# Som

```shell
apt install firmware-sof-signed
```

# Ícones

```shell
/usr/share/icons/hicolor/256x256
```

# Atalhos

```shell
/usr/share/applications
```

# Vídeos no Opera

```shell
sudo apt install chromium-codecs-ffmpeg-extra
cd /usr/lib/x86_64-linux-gnu/opera
sudo mv libffmpeg.so libffmpeg.so.old
sudo ln -s /usr/lib/chromium/libffmpeg.so ./libffmpeg.so
```

# Instalar o discord

```shell
sudo apt install libayatana-appindicator3-1
dpkg -b unpack/ discord-fixed.deb
dpkg-deb --control discord-0.0.17.deb
mv DEBIAN/ unpack/
vim ./unpack/DEBIAN/control
```

Substituir libappindicator1 por libayatana-appindicator3-1

```shell
dpkg -b unpack/ discord-fixed.deb
sudo dpkg -i discord-fixed.deb
```

# Montar a partição do Windows 11

Criar as pastas /media/bitlocker e /media/windows

Instalar o dislocker

```shell
apt install dislocker
```

configurar o fstab

```shell
#### Static Filesystem Table File
proc	/proc	proc	defaults	0	0
# /dev/nvme0n1p1
UUID=4C9D-A814	/boot/efi	vfat	defaults	0	1
# /dev/nvme0n1p7
UUID=6f521946-0ad2-4e8c-ae63-62e121781641	/	ext4	rw,errors=remount-ro	0	1
/dev/nvme0n1p3 /media/bitlocker fuse.dislocker recovery-password=039336-019195-138028-063558-250745-220726-224345-378543,nofail,x-gvfs-hide 0 0
/media/bitlocker/dislocker-file /media/windows ntfs-3g auto,uid=1000,gid=1000,dmask=0022,fmask=0133,nofail,x-gvfs-show,x-gvfs-name=C: 0 0
/dev/disk/by-uuid/3EB0A2BEB0A27BD1 /mnt/3EB0A2BEB0A27BD1 auto nosuid,nodev,nofail,noauto 0 0
```

# Se a partição windows não montar como RW

É necessário desabilitar o **Fast Boot** no windows: Painel de controle → Opções de Energia → Inicialização rápida

# Problemas na instalação do Docker no LMDE5

[https://medium.com/@dasguptabhargav/installing-docker-on-lmde-5-elsie-a-problem-and-a-solution-d89c2f030b86](https://medium.com/@dasguptabhargav/installing-docker-on-lmde-5-elsie-a-problem-and-a-solution-d89c2f030b86)

# Usando outro notebook como monitor

```java
sudo apt install barrier
```

# Pacotes

```bash
discord
dislocker
draw.io
drawing
eclipse
inkscape
gimp
gparted
librecad
linphone
mongo-tools
mongodb-compass
nvidia-compute-utils-510
nvidia-driver-510
nvidia-kernel-common-510
nvidia-kernel-source-510
nvidia-prime
nvidia-settings
nvidia-utils-510
obs-studio
openjdk-11-jdk-headless
openjdk-11-jdk
openjdk-11-jre-headless
openjdk-11-jre
postman
python3
qemu-kvm
soundconverter
sublimeText
virt-viewer
vscode
wps-office

http://listen.181fm.com/181-hardrock_128k.mp3
```

# Atualização do Kernel

## 1 - Instalar o Kernel a partir do repo *bullseye-backports*

[https://forums.linuxmint.com/viewtopic.php?t=371253](https://forums.linuxmint.com/viewtopic.php?t=371253)

[https://forums.linuxmint.com/viewtopic.php?f=250&t=369948](https://forums.linuxmint.com/viewtopic.php?f=250&t=369948)

```bash
apt install -t bullseye-backports linux-image-amd64 linux-headers-amd64
```

## 2 - Instalar os drivers da NVidia

```bash
sudo apt install linux-headers-$(uname -r) build-essential libglvnd-dev pkg-config dkms -y

sudo nano /etc/modprobe.d/blacklist-nouveau.conf
	blacklist nouveau
	options nouveau modeset=0

sudo update-initramfs -u

sudo apt install -t bullseye-backports firmware-misc-nonfree nvidia-kernel-dkms nvidia-driver nvidia-cuda-toolkit nvidia-cuda-dev nvidia-settings nvidia-smi nvidia-xconfig nvidia-opencl-icd nvidia-opencl-common nvidia-detect -y
```

# Acentuação no WPS Office

# **The solution to the failure of fcitx input method in WPS and wineqq**

Recently, it has been transferred from mint to open SUSE, with a variety of twists and turns.

Seeing that it’s almost over, I have another problem today:

Under wineqq and WPS, fcitx input method can’t be opened and can’t input Chinese.

This is very pitiful. These two software can’t input Chinese, which is basically equivalent to no installation. So it’s all about checking on the Internet. Most of the tutorials found on the Internet are due to the fact that several [environment variable](https://developpaper.com/tag/environment-variable/)s are not configured correctly. According to the method on the Internet, the following [code](https://developpaper.com/tag/code/)s are added to the file ~ /. Bashrc ~ /. Xprofile / etc / Profile:

```plain text
export XIM="fcitx"
		export XIM_PROGRAM="fcitx"
		export XMODIFIERS="@im=fcitx"
		export GTK_IM_MODULE="fcitx"
		export QT_IM_MODULE="fcitx"
```

Restart. It’s still hard to find out.

By chance, if you run commands like WPS on the command line, fcitx is easy to use. The initial suspicion is that the environment variable configured above does not take effect when double clicking to run.

Write a script and test it. The code is as follows:

```plain text
#!/usr/bin/sh
		export XMODIFIERS="@im=fcitx"
		export GTK_IM_MODULE="fcitx"
		export QT_IM_MODULE="fcitx"
		/usr/bin/wpp
```

Save it as wpp.sh, change the wps-office-wpp.desktop target address on the desktop to this script, and then run it. OK.It’s definitely about environment variables.

Next, you can make a small change to WPS and wineqq.

**WPS**

For WPS, double-click the desktop icon to run / usr / bin / WPS (WPP, ET), so you need to use a script to configure the environment variables before executing the program. There is a little difference between the actual script and the above test script:

```plain text
#!/usr/bin/sh
		export XMODIFIERS="@im=fcitx"
		export GTK_IM_MODULE="fcitx"
		export QT_IM_MODULE="fcitx"
		/usr/bin/wpp "$1"   //modify:13-12-18
```

The reason for adding a [parameter](https://developpaper.com/tag/parameter/) to the executable is that when the. Desktop file calls the executable, it will pass a% f parameter to the executable. Now let’s pass it to our script, and then our script calls it

Write the scripts that call WPS, WPP and ET, put them into / opt / Kingsoft / WPS office / office6 / directory, and modify wps-office-wps.desktop wps-office-wpp.desktop wps-office-et.desktop in / usr / share / applications / directory respectively as follows (take WPP for example, the rest is similar):

```plain text
#!/usr/bin/env xdg-open
		[Desktop Entry]
		Comment=Use Kingsoft Presentation to edit and play presentations.
		Comment [zh cn] = use WPS presentation to edit and play the presentation
		#Exec=/usr/bin/wpp %f
		Exec=/opt/kingsoft/wps-office/office6/wpp.sh %f
		####Comment out the previous line and add the line
		GenericName=Kingsoft Presentation
		GenericName [zh cn] = WPS demo
		MimeType=application/wps-office.dps;application/wps-office.dpt;application/wps-office.ppt;application/wps-office.pot;application/vnd.ms-powerpoint;application/vnd.mspowerpoint;application/mspowerpoint;application/powerpoint;application/x-mspowerpoint;application/wps-office.pptx;application/wps-office.potx;
		Name=Kingsoft Presentation
		Name [zh cn] = WPS demo
		StartupNotify=false
		Terminal=false
		Type=Application
		Categories=Office;Presentation;Qt;
		X-DBUS-ServiceName=
		X-DBUS-StartupType=
		X-KDE-SubstituteUID=false
		X-KDE-Username=
		Icon=wps-office-wppmain
		InitialPreference=3
```

Running WPS, successful

---

Although the problem has been solved, there are still several problems. Ask experts for advice:

1. What does the% f parameter mean in a. Desktop script

## **2. Why is the environment variable configured in the corresponding file difficult to use outside the terminal?**

*2013/12/18*

2. Fix bug: last line in script should be changed to / usr / bin / WPP “$1”
3. %Official Handbook of F’s role

> %f A single file name, even if multiple files are selected. The system reading the desktop entry should recognize that the program in question cannot handle multiple file arguments, and it should should probably spawn and execute multiple copies of a program for each selected file if the program is not able to handle additional file arguments. If files are not on the local file system (i.e. are on HTTP or FTP locations), the files will be copied to the local file system and %f will be expanded to point at the temporary file. Used for programs that do not understand the URL syntax.

## Atualizando para a abertura a partir dos arquivos

```bash
sudo desktop-file-install wps-office-prometheus.desktop
sudo update-desktop-database
```

# Headset

[https://askubuntu.com/questions/831331/failed-to-change-profile-to-headset-head-unit](https://askubuntu.com/questions/831331/failed-to-change-profile-to-headset-head-unit)

# Audio sumiu

```bash
rm /home/quinalha/.config/pulse/*
pulseaudio -k
```
