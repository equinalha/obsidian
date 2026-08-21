---
base: "[[Tweets.base]]"
Type: Thread
Created: 2023-01-07T08:12:00
Author: TRÄW🤟
Tags:
  - Linux
Tweet Link: https://twitter.com/xtremepentest/status/1611353708692131846
---
> [!note] 📌
> **TRÄW🤟 **[***@xtremepentest:***](https://www.twitter.com/xtremepentest)
Modern Linux boot process explained 🐧↓

> [!note] 📌
> **TRÄW🤟 **[***@xtremepentest:***](https://www.twitter.com/xtremepentest)
When you turn on your Linux computer, it goes through a series of phases before presenting a login screen that prompts you for your username or password.

Every Linux distribution goes through four distinct stages during the boot-up process.

> [!note] 📌
> **TRÄW🤟 **[***@xtremepentest:***](https://www.twitter.com/xtremepentest)
The booting process consists of four steps, which we will go over in this thread:

• BIOS and UEFI Integrity check (POST)
• Loading of the Boot loader (GRUB2)
• Kernel initialization
• Starting systemd, the parent of all processes

> [!note] 📌
> **TRÄW🤟 **[***@xtremepentest:***](https://www.twitter.com/xtremepentest)
1. BIOS and UEFI Integrity check (POST)

First, when the system boots, the BIOS (Basic Input/Output System) or UEFI (Unified Extensible Firmware Interface) program launches and performs a Power On Self Test (POST).

This is an integrity check that runs a slew of diagnostic tests.

> [!note] 📌
> **TRÄW🤟 **[***@xtremepentest:***](https://www.twitter.com/xtremepentest)
The POST process validates the hardware components and peripherals such as the HDD or SSD, keyboard, RAM, USB ports, and any other hardware. It also runs tests to ensure that the computer is in good condition.

> [!note] 📌
> **TRÄW🤟 **[***@xtremepentest:***](https://www.twitter.com/xtremepentest)
Furthermore, if this test detects an error, it will typically display an error message on the screen, requesting your intervention.

> [!note] 📌
> **TRÄW🤟 **[***@xtremepentest:***](https://www.twitter.com/xtremepentest)
If the test fails to detect the RAM, POST produces a beeping sound; otherwise, if the expected hardware is present and functioning properly, the booting process advances to the next stage.

> [!note] 📌
> **TRÄW🤟 **[***@xtremepentest:***](https://www.twitter.com/xtremepentest)
BIOS and UEFI are firmware interfaces used by computers to start the operating system (OS). However, the two programs differ in their approach to storing metadata on and about the drive:

• BIOS uses the Master Boot Record (MBR)
• UEFI uses the GUID Partition Table (GPT)

> [!note] 📌
> **TRÄW🤟 **[***@xtremepentest:***](https://www.twitter.com/xtremepentest)
[2] Loading of the Boot loader (GRUB2)

The BIOS or UEFI has now run the POST to check the machine's status. The BIOS then searches the MBR (Master Boot Record) for information about the bootloader and disk partitioning.

> [!note] 📌
> **TRÄW🤟 **[***@xtremepentest:***](https://www.twitter.com/xtremepentest)
The boot loader in a BIOS system is located in the first sector of the boot device; this is the MBR.

It occupies the first 512 bytes of disk space which is typically /dev/sda or /dev/hda depending on the architecture of your drive.

> [!note] 📌
> **TRÄW🤟 **[***@xtremepentest:***](https://www.twitter.com/xtremepentest)
A UEFI system, on the other hand, stores all startup data in an.efi file. The file is located on the EFI System Partition, which also houses the boot loader.

It should be noted, however, that the MBR can sometimes be found on a Live USB or DVD installation of Linux.

> [!note] 📌
> **TRÄW🤟 **[***@xtremepentest:***](https://www.twitter.com/xtremepentest)
The boot loader, in particular, is a small program that loads the operating system. The boot loader's primary function is to locate the kernel on the disk, insert it into memory, and execute it with the supplied options.

> [!note] 📌
> **TRÄW🤟 **[***@xtremepentest:***](https://www.twitter.com/xtremepentest)
In Linux, there are four main types of bootloaders: LILO, SYSLINUX, GRUB, and GRUB2.

> [!note] 📌
> **TRÄW🤟 **[***@xtremepentest:***](https://www.twitter.com/xtremepentest)
[+] LILO

LILO (Linux Loader) was once one of the most popular Linux boot loaders. However, it has fallen out of favor due to its lack of support for multi-boot environments and UEFI.

> [!note] 📌
> **TRÄW🤟 **[***@xtremepentest:***](https://www.twitter.com/xtremepentest)
It also provides limited support for new filesystems.

LILO's developers officially ceased development and support in December 2015. As a result, the Linux Loader is outdated.

> [!note] 📌
> **TRÄW🤟 **[***@xtremepentest:***](https://www.twitter.com/xtremepentest)
[+] SYSLINUX

Similarly, SYSLINUX is a boot loader for the Linux operating system that runs on a FAT filesystem, similar to that of a Windows system. In a nutshell, its goal is to make the process of installing Linux for the first time as simple as possible.

> [!note] 📌
> **TRÄW🤟 **[***@xtremepentest:***](https://www.twitter.com/xtremepentest)
Furthermore, SYSLINUX supports the following major filesystems:
• ext2
• ext3
• ext4
• FAT

With some limitations, SYSLINUX can also support the Btrfs and XFS filesystems.

> [!note] 📌
> **TRÄW🤟 **[***@xtremepentest:***](https://www.twitter.com/xtremepentest)
[+] GRUB2

GRUB2 stands for GRand Unified Bootloader version 2, it is the most recent and primary bootloader in modern Linux distributions.

> [!note] 📌
> **TRÄW🤟 **[***@xtremepentest:***](https://www.twitter.com/xtremepentest)
GRUB2 is a choice for many modern Linux distributions because of:

• the ability to boot several operating systems
• network-based diskless

> [!note] 📌
> **TRÄW🤟 **[***@xtremepentest:***](https://www.twitter.com/xtremepentest)
• allows ease of use over a serial cable
• powerful command line interface for interactive configuration
• booting both a graphical and a text-based interface

GRUB2 has now replaced its predecessor (GRUB), which is now known as GRUB Legacy.

> [!note] 📌
> **TRÄW🤟 **[***@xtremepentest:***](https://www.twitter.com/xtremepentest)
When the BIOS finds the grub2 bootloader, it executes it and loads it into main memory (RAM).

You can do a few things with the grub2 menu. It lets you choose the Linux kernel version you want to use.

> [!note] 📌
> **TRÄW🤟 **[***@xtremepentest:***](https://www.twitter.com/xtremepentest)
If you've upgraded your system a few times, you might notice that different kernel versions are listed.

It also allows you to edit some kernel parameters by pressing a combination of keyboard keys.

> [!note] 📌
> **TRÄW🤟 **[***@xtremepentest:***](https://www.twitter.com/xtremepentest)
In addition, in a dual-boot setup with multiple OS installations, the grub menu allows you to choose which OS to boot into. The grub2 configuration file is located in /boot/grub2/grub2.cfg.

The primary goal of GRUB is to load the Linux kernel into main memory.

> [!note] 📌
> **TRÄW🤟 **[***@xtremepentest:***](https://www.twitter.com/xtremepentest)
[3] Kernel Initialization

The operating system now controls access to our computer resources after passing through BIOS or UEFI, POST, and using a boot loader to start the kernel.

> [!note] 📌
> **TRÄW🤟 **[***@xtremepentest:***](https://www.twitter.com/xtremepentest)
The Linux kernel follows a set procedure in this case:

• decompress itself from its compressed version before           undertaking any task
• perform hardware checks
• gain access to vital peripheral hardware
• initializes the /sbin/init program, also known as init.

> [!note] 📌
> **TRÄW🤟 **[***@xtremepentest:***](https://www.twitter.com/xtremepentest)
Init is always the first program to be executed and is assigned the process ID or PID of 1. It’s the init process that spawns various daemons & mounts all partitions that are specified in the /etc/fstab file.

> [!note] 📌
> **TRÄW🤟 **[***@xtremepentest:***](https://www.twitter.com/xtremepentest)
The kernel then mounts the initial RAM disk (initrd) which is a temporary root filesystem until the real root filesystem is mounted. All kernels are located in the `/boot` directory together with the initial RAM disk image.

> [!note] 📌
> **TRÄW🤟 **[***@xtremepentest:***](https://www.twitter.com/xtremepentest)
[4] Starting Systemd

Finally, the kernel loads Systemd, which replaces the old SysV init. Systemd is the mother of all Linux processes, managing tasks such as mounting file systems and starting and stopping services, to name a few.

> [!note] 📌
> **TRÄW🤟 **[***@xtremepentest:***](https://www.twitter.com/xtremepentest)
The /etc/systemd/system/default.target file is used by Systemd to determine the state or target into which the Linux system should boot.

> [!note] 📌
> 

> [!note] 📌
> **TRÄW🤟 **[***@xtremepentest:***](https://www.twitter.com/xtremepentest)
The systemd targets are broken down as follows:

• [**poweroff.target**](http://poweroff.target/) (runlevel 0) - Poweroff or Shutdown the system.
• [**rescue.target**](http://rescue.target/) (runlevel 1) - launches a rescue shell session.

> [!note] 📌
> **TRÄW🤟 **[***@xtremepentest:***](https://www.twitter.com/xtremepentest)
• [**multi-user.target**](http://multi-user.target/) (runlevel 2,3,4) -  Configures the system to a non-graphical (console) multi-user system.

> [!note] 📌
> **TRÄW🤟 **[***@xtremepentest:***](https://www.twitter.com/xtremepentest)
• [**graphical.target**](http://graphical.target/) (runlevel 5) - Configure the system to use a graphical multi-user interface to access network services.
• [**reboot.target**](http://reboot.target/) (runlevel 6)- reboots the system.

> [!note] 📌
> **TRÄW🤟 **[***@xtremepentest:***](https://www.twitter.com/xtremepentest)
Run the following command to determine the current target on your system:

$ systemctl get-default

You can change targets by entering the following command into the terminal:

$ init runlevel-value

Init 3, for example, configures the system to be non-graphical.

> [!note] 📌
> **TRÄW🤟 **[***@xtremepentest:***](https://www.twitter.com/xtremepentest)
The init 6 command reboots your system, while init 0 turns it off. When switching between these two targets, make sure to use the sudo command.

> [!note] 📌
> **TRÄW🤟 **[***@xtremepentest:***](https://www.twitter.com/xtremepentest)
The boot process is complete when systemd loads all daemons and sets the target or run level value. At this point, you will be prompted for your username and password, after which you will gain access to your Linux system.

> [!note] 📌
> **TRÄW🤟 **[***@xtremepentest:***](https://www.twitter.com/xtremepentest)
This information should be sufficient to help you understand the Linux booting process.

That's all! Thank you for getting this far. I hope you find this thread useful.

> [!note] 📌
> **TRÄW🤟 **[***@xtremepentest:***](https://www.twitter.com/xtremepentest)
If you found this thread valuable:

1. Toss us a follow for more daily threads on Linux, sysadmin and devops →  [**@xtremepentest**](https://www.twitter.com/xtremepentest)

2. Like and RT the first tweet so other Linux folks can find it too.

> [!note] 📌
> **TRÄW🤟 **[***@xtremepentest:***](https://www.twitter.com/xtremepentest)
• The default target value for a desktop workstation (with a graphical user interface) is 5, which corresponds to run level 5 in the old SystemV init.

• The default target for a server is [**multi-user.target**](http://multi-user.target/), which corresponds to run level 3 in SysV init.