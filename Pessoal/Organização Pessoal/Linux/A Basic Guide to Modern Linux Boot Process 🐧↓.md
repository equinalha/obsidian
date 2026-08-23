---

---
> [!note] 📌
> **Linuxopsys **[***@linuxopsys:***](https://www.twitter.com/linuxopsys)
A Basic Guide to Modern Linux Boot Process 🐧↓

> [!note] 📌
> **Linuxopsys **[***@linuxopsys:***](https://www.twitter.com/linuxopsys)
When you turn on your Linux computer, it goes through a series of phases before presenting a login screen that prompts you for your username or password.

Every Linux distribution goes through four distinct stages during the boot-up process.

> [!note] 📌
> **Linuxopsys **[***@linuxopsys:***](https://www.twitter.com/linuxopsys)
The booting process consists of four steps, which we will go over in this thread:

• BIOS and UEFI Integrity check (POST)
• Loading of the Boot loader (GRUB2)
• Kernel initialization
• Starting systemd, the parent of all processes

> [!note] 📌
> **Linuxopsys **[***@linuxopsys:***](https://www.twitter.com/linuxopsys)
1. BIOS and UEFI Integrity check (POST)

First, when the system boots, the BIOS (Basic Input/Output System) or UEFI (Unified Extensible Firmware Interface) program launches and performs a Power On Self Test (POST).

This is an integrity check that runs a slew of diagnostic tests.

> [!note] 📌
> **Linuxopsys **[***@linuxopsys:***](https://www.twitter.com/linuxopsys)
The POST process validates the hardware components and peripherals such as the HDD or SSD, keyboard, RAM, USB ports, and any other hardware. It also runs tests to ensure that the computer is in good condition.

> [!note] 📌
> **Linuxopsys **[***@linuxopsys:***](https://www.twitter.com/linuxopsys)
Furthermore, if this test detects an error, it will typically display an error message on the screen, requesting your intervention.

> [!note] 📌
> **Linuxopsys **[***@linuxopsys:***](https://www.twitter.com/linuxopsys)
If the test fails to detect the RAM, POST produces a beeping sound; otherwise, if the expected hardware is present and functioning properly, the booting process advances to the next stage.

> [!note] 📌
> **Linuxopsys **[***@linuxopsys:***](https://www.twitter.com/linuxopsys)
BIOS and UEFI are firmware interfaces used by computers to start the operating system (OS). However, the two programs differ in their approach to storing metadata on and about the drive:

• BIOS uses the Master Boot Record (MBR)
• UEFI uses the GUID Partition Table (GPT)

> [!note] 📌
> **Linuxopsys **[***@linuxopsys:***](https://www.twitter.com/linuxopsys)
[2] Loading of the Boot loader (GRUB2)

The BIOS or UEFI has now run the POST to check the machine's status. The BIOS then searches the MBR (Master Boot Record) for information about the bootloader and disk partitioning.

> [!note] 📌
> **Linuxopsys **[***@linuxopsys:***](https://www.twitter.com/linuxopsys)
The boot loader in a BIOS system is located in the first sector of the boot device; this is the MBR.

It occupies the first 512 bytes of disk space which is typically /dev/sda or /dev/hda depending on the architecture of your drive.

> [!note] 📌
> **Linuxopsys **[***@linuxopsys:***](https://www.twitter.com/linuxopsys)
A UEFI system, on the other hand, stores all startup data in an.efi file. The file is located on the EFI System Partition, which also houses the boot loader.

It should be noted, however, that the MBR can sometimes be found on a Live USB or DVD installation of Linux.

> [!note] 📌
> **Linuxopsys **[***@linuxopsys:***](https://www.twitter.com/linuxopsys)
The boot loader, in particular, is a small program that loads the operating system. The boot loader's primary function is to locate the kernel on the disk, insert it into memory, and execute it with the supplied options.

> [!note] 📌
> **Linuxopsys **[***@linuxopsys:***](https://www.twitter.com/linuxopsys)
In Linux, there are four main types of bootloaders: LILO, SYSLINUX, GRUB, and GRUB2.

> [!note] 📌
> **Linuxopsys **[***@linuxopsys:***](https://www.twitter.com/linuxopsys)
[+] LILO

LILO (Linux Loader) was once one of the most popular Linux boot loaders. However, it has fallen out of favor due to its lack of support for multi-boot environments and UEFI.

> [!note] 📌
> **Linuxopsys **[***@linuxopsys:***](https://www.twitter.com/linuxopsys)
It also provides limited support for new filesystems.

LILO's developers officially ceased development and support in December 2015. As a result, the Linux Loader is outdated.

> [!note] 📌
> **Linuxopsys **[***@linuxopsys:***](https://www.twitter.com/linuxopsys)
[+] SYSLINUX

Similarly, SYSLINUX is a boot loader for the Linux operating system that runs on a FAT filesystem, similar to that of a Windows system. In a nutshell, its goal is to make the process of installing Linux for the first time as simple as possible.

> [!note] 📌
> **Linuxopsys **[***@linuxopsys:***](https://www.twitter.com/linuxopsys)
Furthermore, SYSLINUX supports the following major filesystems:
• ext2
• ext3
• ext4
• FAT

With some limitations, SYSLINUX can also support the Btrfs and XFS filesystems.

> [!note] 📌
> **Linuxopsys **[***@linuxopsys:***](https://www.twitter.com/linuxopsys)
[+] GRUB2

GRUB2 stands for GRand Unified Bootloader version 2, it is the most recent and primary bootloader in modern Linux distributions.

> [!note] 📌
> **Linuxopsys **[***@linuxopsys:***](https://www.twitter.com/linuxopsys)
GRUB2 is a choice for many modern Linux distributions because of:

• the ability to boot several operating systems
• network-based diskless

> [!note] 📌
> **Linuxopsys **[***@linuxopsys:***](https://www.twitter.com/linuxopsys)
• allows ease of use over a serial cable
• powerful command line interface for interactive configuration
• booting both a graphical and a text-based interface

GRUB2 has now replaced its predecessor (GRUB), which is now known as GRUB Legacy.

> [!note] 📌
> **Linuxopsys **[***@linuxopsys:***](https://www.twitter.com/linuxopsys)
When the BIOS finds the grub2 bootloader, it executes it and loads it into main memory (RAM).

You can do a few things with the grub2 menu. It lets you choose the Linux kernel version you want to use.

> [!note] 📌
> **Linuxopsys **[***@linuxopsys:***](https://www.twitter.com/linuxopsys)
If you've upgraded your system a few times, you might notice that different kernel versions are listed.

It also allows you to edit some kernel parameters by pressing a combination of keyboard keys.

> [!note] 📌
> **Linuxopsys **[***@linuxopsys:***](https://www.twitter.com/linuxopsys)
In addition, in a dual-boot setup with multiple OS installations, the grub menu allows you to choose which OS to boot into. The grub2 configuration file is located in /boot/grub2/grub2.cfg.

The primary goal of GRUB is to load the Linux kernel into main memory.

> [!note] 📌
> **Linuxopsys **[***@linuxopsys:***](https://www.twitter.com/linuxopsys)
[3] Kernel Initialization

The operating system now controls access to our computer resources after passing through BIOS or UEFI, POST, and using a boot loader to start the kernel.

> [!note] 📌
> **Linuxopsys **[***@linuxopsys:***](https://www.twitter.com/linuxopsys)
The Linux kernel follows a set procedure in this case:

• decompress itself from its compressed version before           undertaking any task
• perform hardware checks
• gain access to vital peripheral hardware
• initializes the /sbin/init program, also known as init.

> [!note] 📌
> **Linuxopsys **[***@linuxopsys:***](https://www.twitter.com/linuxopsys)
Init is always the first program to be executed and is assigned the process ID or PID of 1. It’s the init process that spawns various daemons & mounts all partitions that are specified in the /etc/fstab file.

> [!note] 📌
> **Linuxopsys **[***@linuxopsys:***](https://www.twitter.com/linuxopsys)
The kernel then mounts the initial RAM disk (initrd) which is a temporary root filesystem until the real root filesystem is mounted. All kernels are located in the `/boot` directory together with the initial RAM disk image.

> [!note] 📌
> **Linuxopsys **[***@linuxopsys:***](https://www.twitter.com/linuxopsys)
[4] Starting Systemd

Finally, the kernel loads Systemd, which replaces the old SysV init. Systemd is the mother of all Linux processes, managing tasks such as mounting file systems and starting and stopping services, to name a few.

> [!note] 📌
> **Linuxopsys **[***@linuxopsys:***](https://www.twitter.com/linuxopsys)
The /etc/systemd/system/default.target file is used by Systemd to determine the state or target into which the Linux system should boot.

> [!note] 📌
> **Linuxopsys **[***@linuxopsys:***](https://www.twitter.com/linuxopsys)
• The default target value for a desktop workstation (with a graphical user interface) is 5, which corresponds to run level 5 in the old SystemV init.

• The default target for a server is [**multi-user.target**](http://multi-user.target/), which corresponds to run level 3 in SysV init.

> [!note] 📌
> **Linuxopsys **[***@linuxopsys:***](https://www.twitter.com/linuxopsys)
The systemd targets are broken down as follows:

• [**poweroff.target**](http://poweroff.target/) (runlevel 0) - Poweroff or Shutdown the system.
• [**rescue.target**](http://rescue.target/) (runlevel 1) - launches a rescue shell session.

> [!note] 📌
> **Linuxopsys **[***@linuxopsys:***](https://www.twitter.com/linuxopsys)
• [**multi-user.target**](http://multi-user.target/) (runlevel 2,3,4) -  Configures the system to a non-graphical (console) multi-user system.

> [!note] 📌
> **Linuxopsys **[***@linuxopsys:***](https://www.twitter.com/linuxopsys)
• [**graphical.target**](http://graphical.target/) (runlevel 5) - Configure the system to use a graphical multi-user interface to access network services.
• [**reboot.target**](http://reboot.target/) (runlevel 6)- reboots the system.

> [!note] 📌
> **Linuxopsys **[***@linuxopsys:***](https://www.twitter.com/linuxopsys)
Note, the run level in Linux represents the current state of the operating system. Run levels specify which system services are active. SysVinit previously identified run levels by number.

In Systemd, however,.target files have replaced run levels.

> [!note] 📌
> **Linuxopsys **[***@linuxopsys:***](https://www.twitter.com/linuxopsys)
Run the following command to determine the current target on your system:

$ systemctl get-default

You can change targets by entering the following command into the terminal:

$ init runlevel-value

Init 3, for example, configures the system to be non-graphical.

> [!note] 📌
> **Linuxopsys **[***@linuxopsys:***](https://www.twitter.com/linuxopsys)
The init 6 command reboots your system, while init 0 turns it off. When switching between these two targets, make sure to use the sudo command.

> [!note] 📌
> **Linuxopsys **[***@linuxopsys:***](https://www.twitter.com/linuxopsys)
The boot process is complete when systemd loads all daemons and sets the target or run level value. At this point, you will be prompted for your username and password, after which you will gain access to your Linux system.

> [!note] 📌
> **Linuxopsys **[***@linuxopsys:***](https://www.twitter.com/linuxopsys)
This information should be sufficient to help you understand the Linux booting process.

That's all! Thank you for getting this far. I hope you find this thread useful.

> [!note] 📌
> **Linuxopsys **[***@linuxopsys:***](https://www.twitter.com/linuxopsys)
If you found this thread valuable:

1. Toss us a follow for more daily threads on Linux, sysadmin and devops → [**@linuxopsys**](https://www.twitter.com/linuxopsys)

2. Like and RT the first tweet so other Linux folks can find it too.