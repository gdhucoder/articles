---
title: "linux查看硬件信息"
date: 2020-04-25T05:51:17+08:00
draft: false
tags: 
   - TECH
categories:
  - 思考
  - 归档
---

[TOC]

硬件信息。

<!--more-->

lshw - List Hardware

A general purpose utility, that reports detailed and brief information about multiple different hardware units such as cpu, memory, disk, usb controllers, network adapters etc. Lshw extracts the information from different /proc files.

```bash
$ sudo lshw -short

H/W path        Device      Class       Description
===================================================
                            system      ()
/0                          bus         DG35EC
/0/0                        processor   Intel(R) Core(TM)2 Quad CPU    Q8400  @ 2.66GHz
/0/0/1                      memory      2MiB L2 cache
/0/0/3                      memory      32KiB L1 cache
/0/2                        memory      32KiB L1 cache
/0/4                        memory      64KiB BIOS
/0/14                       memory      8GiB System Memory
/0/14/0                     memory      2GiB DIMM DDR2 Synchronous 667 MHz (1.5 ns)
/0/14/1                     memory      2GiB DIMM DDR2 Synchronous 667 MHz (1.5 ns)
/0/14/2                     memory      2GiB DIMM DDR2 Synchronous 667 MHz (1.5 ns)
/0/14/3                     memory      2GiB DIMM DDR2 Synchronous 667 MHz (1.5 ns)
/0/100                      bridge      82G35 Express DRAM Controller
/0/100/2                    display     82G35 Express Integrated Graphics Controller
/0/100/2.1                  display     82G35 Express Integrated Graphics Controller
/0/100/19       eth0        network     82566DC Gigabit Network Connection
/0/100/1a                   bus         82801H (ICH8 Family) USB UHCI Controller #4
/0/100/1a.1                 bus         82801H (ICH8 Family) USB UHCI Controller #5
/0/100/1a.7                 bus         82801H (ICH8 Family) USB2 EHCI Controller #2
/0/100/1b                   multimedia  82801H (ICH8 Family) HD Audio Controller
/0/100/1c                   bridge      82801H (ICH8 Family) PCI Express Port 1
/0/100/1c.1                 bridge      82801H (ICH8 Family) PCI Express Port 2
/0/100/1c.2                 bridge      82801H (ICH8 Family) PCI Express Port 3
/0/100/1c.2/0               storage     JMB368 IDE controller
/0/100/1d                   bus         82801H (ICH8 Family) USB UHCI Controller #1
/0/100/1d.1                 bus         82801H (ICH8 Family) USB UHCI Controller #2
/0/100/1d.2                 bus         82801H (ICH8 Family) USB UHCI Controller #3
/0/100/1d.7                 bus         82801H (ICH8 Family) USB2 EHCI Controller #1
/0/100/1e                   bridge      82801 PCI Bridge
/0/100/1e/5                 bus         FW322/323 [TrueFire] 1394a Controller
/0/100/1f                   bridge      82801HB/HR (ICH8/R) LPC Interface Controller
/0/100/1f.2                 storage     82801H (ICH8 Family) 4 port SATA Controller [IDE mode]
/0/100/1f.3                 bus         82801H (ICH8 Family) SMBus Controller
/0/100/1f.5                 storage     82801HR/HO/HH (ICH8R/DO/DH) 2 port SATA Controller [IDE m
/0/1            scsi3       storage     
/0/1/0.0.0      /dev/sda    disk        500GB ST3500418AS
/0/1/0.0.0/1    /dev/sda1   volume      70GiB Windows NTFS volume
/0/1/0.0.0/2    /dev/sda2   volume      395GiB Extended partition
/0/1/0.0.0/2/5  /dev/sda5   volume      97GiB HPFS/NTFS partition
/0/1/0.0.0/2/6  /dev/sda6   volume      97GiB Linux filesystem partition
/0/1/0.0.0/2/7  /dev/sda7   volume      1952MiB Linux swap / Solaris partition
/0/1/0.0.0/2/8  /dev/sda8   volume      198GiB Linux filesystem partition
/0/3            scsi4       storage     
/0/3/0.0.0      /dev/cdrom  disk        DVD RW DRU-190A
```