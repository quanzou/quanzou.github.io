---
layout: post
title: "install Debian on Intel Mac Mini"
toc: true
categories:
  - Tech
tags:
  - software
  - hardware
  - linux
date:   2011-08-08 12:03 PM
---

This note shows how to single boot Linux without delay on Macmini and it 
was written on August 08 2011. Mac Mini systems shipped since February **2006**
contain Intel "**Core Duo**" processors and an Intel **945GM**+ICH7M chipset. In 
other words they are regular PCs using Intel's Centrino platform, modulo 
some fancy firmware, and with a little persuasion can run common or garden 
i386 Linux.

![mac_mini]({{ site.url }}{{ site.baseurl }}/assets/images/debian-mac-mini/mac-mini-2006-240.png){: width="236" height="108"}

**Mac mini (Late 2006)**

## Definitions
The Extensible Firmware Interface (EFI)
: A specification that defines 
a software interface between an operating system and platform firmware. 
EFI is a replacement for the older BIOS firmware interface present in 
all IBM PC-compatible personal computers.

The Master Boot Record (MBR)
: A type of boot sector popularized by
the IBM Personal Computer. It consists of a sequence of 512 bytes
located at the first sector of a data storage device such as a hard
disk. MBRs are usually placed on storage devices intended for use
with IBM PC-compatible systems.

The GUID Partition Table (GPT)
: A standard for the layout of the partition
table on a physical hard disk. Although it forms a part of the Extensible
Firmware Interface (EFI) standard, it is also used on some BIOS systems
because of the limitations of MBR partition tables, which restrict a disk
partition's size to a maximum of 2.19TB. GPT allows for a maximum disk and
partition size of 9.4 ZB. As of 2010, most current operating systems support 
GPT, although some (including Mac OS X and Windows) only support booting to 
GPT partitions on systems with EFI firmware.

## Firmware Version Checkup
The Mac's EFI Boot ROM and SMC firmware versions could be found at the 
Hardware section of the *System Information* under OSX, if Mac mini has 
OSX installed. If Mac mini doesn't have OSX installed, you will need an 
OSX disc, and boot from it. You actually don't need to install it, before 
you install the OSX, you can find out the hardware information from 
installer menu. Another way to find out the firmware version is to look 
up the SN# of the Mac mini: **G87193SXW0D**.

**EFI and SMC firmware for Intel-based Mac computers**

| Computer | Identifier | EFI Boot ROM version | SMC version |
| -------- | ---------- | -------------------- | ----------- |
| Mac mini Server (Mid 2010) |Macmini4,1  | MM41.0042.B03 (EFI 1.5) |
| Mac mini (Mid 2010) 	| Macmini4,1 | MM41.0042.B03 (EFI 1.5) |
| Mac mini (Early 2009) | Macmini3,1 | MM31.0081.B06 (EFI 1.2) |
| Mac mini (Late 2006)  | Macmini1,1 | MM11.0055.B08 (EFI 1.1) | 1.3f4 (SMC 1.0)
| Mac mini (Early 2006) | Macmini1,1 | MM11.0055.B08 (EFI 1.1) | 1.3f4 (SMC 1.0)

## Preparation

disk images needed: 
+ Download **gparted**, burn the disc. This is not necessary, but I found neither
the partition of OSX installer, nor Debian partion tool is accurate. OSX 
partition tool will reserve 200 MB hidden partion for EFI. You won't need this,
if you install linux only.
+ To prepare USB OSX, you will need a program called "Transmac": 
[https://www.acutesystems.com/scrtm.htm](https://www.acutesystems.com/scrtm.htm){:target="_blank"} 
(this program is no longer free). Then, backup the USB, Right click the USB 
through Transmac, choose Format disk --> Format with Disk Image. 
Finally choose the OSX dmg file you have on your harddisk. 
+ Burn the rEFIt bootable disk. Download the rEFIt disk image at:
[http://refit.sourceforge.net/#download](http://refit.sourceforge.net/#download){:target="_blank"} 
(By 2013-03-29, **rEFIt Project** is no longer actively maintained. A fork rEFInd is 
maintaned and under active development at 
[https://www.rodsbooks.com/refind/getting.html](https://www.rodsbooks.com/refind/getting.html){:target="_blank"}). 
Again, if you have multiple boot, then you will proabably want to intall refit 
either on a hiden partition. Since we only install linux, we don't have to do 
this. Open the disk image from **transmac**, right click the image from the 
list, and burn it on CD.
+  Debian i386 disc is needed for Mac mini (late 2006) model. Download it,
and burn it to CD. 

## Installation

### Debian
Boot Debian installation disc and remove ALL partitions, partition as
you like for your Linux installation. Install Debian, restart. You can
use gparted, if you don't like the partition tool from Debian disc.

This is my scheme for manually partitioning a 80 GB disc:

~~~bash
/boot 128 MB
/swap 4 GB
/     70 GB
~~~

Total size will sum up to 75 GB. 

>NOTE: To boot from CD, you will need to hold down **C** at startup. 
To eject, you will need to hold down Left button of the mouse at startup.

### rEFIt

Put in **rEFIt** CD and holding down **Alt** key, boot **rEFIT** cd. Synchronize
GUID and MBR. Restart.

**rEFIt**'s partition map tool will copy the **GPT** partition map into the **MBR**.
The new **GPT** partition format can handle very large disks and contains
the canonical partition map; the old **MBR** partition map should contain a
shadow of this information and is used here primarily by the **GRUB** bootloader.

The reason appears to be that the linux partition editor rewrote the **GPT**
partition map but did not shadow this this information into the **MBR** partition
map (presumably it assumes all GPT systems are **GPT-only**). Therefore, every
time, you change the partition table, you will need synchronize **GPT** and **MBR**
with **rEFIt**.

### OSX 
Insert OSX disc, boot from it, open terminal and enter following:

~~~bash
$ bless --device /dev/disk0s1 --setBoot --legacy --verbose
~~~

where **/dev/disk0s1** is the partition that I installed grub (do '**diskutil list**' 
to find out correct partition). Bless is only available at OSX installer's 
terminal too. Of course, '--verbose' is optional. This makes macmini EFI 
firmware boot your Linux installation in legacy mode without long delay 
(20s vs 3s). This is especially useful, if you want remotely reboot the machine.

## Completion 

Restart your Macmini (don't forget to remove OSX disc). And boot directly to Linux!

## Reference

+ The rEFInd Boot Manager, by Roderick W. Smith, 2012. [https://www.rodsbooks.com/refind/](https://www.rodsbooks.com/refind/){: target="_blank"}.
+ The rEFIt project, 2013. [http://refit.sourceforge.net](http://refit.sourceforge.net){:target="_blank"}{: target="_blank"}.
+ Installing Debian On Apple, Debian Wiki documentation, 2025. [https://wiki.debian.org/InstallingDebianOn/Apple](https://wiki.debian.org/InstallingDebianOn/Apple){:target="_blank"}{: target="_blank"}. Accessed January 7, 2007.