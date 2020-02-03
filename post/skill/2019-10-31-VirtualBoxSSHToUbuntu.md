---
title: "window file transfer between host and virtualbox linux"
date: 2019-10-31T08:14:40+08:00
draft: false
tags: 
   - TECH
categories:
  - 技术
  - 归档
---

[TOC]

Window10与虚拟机linux利用端口转发(port forwarding)使用WinSCP传输文件.

<!--more-->

# win10, virtualbox, linux, winCSP, port forwarding

## WinCSP

场景：virtualbox中的虚拟机linux需要和host共享文件，可以双向传输。

最简单的方法是建立共享文件夹。但我觉得使用专用的软件更合适。我使用了WinSCP。

>WinSCP is an open source free SFTP client, FTP client, WebDAV client, S3 client and SCP client for Windows. Its main function is file transfer between a local and a remote computer. Beyond this, WinSCP offers scripting and basic file manager functionality.

下载安装后，我需要连接到虚拟机上，这时发现无法连接。

解决的办法参考这篇博客[access-nat-guest-from-host-virtualbox](http://ask.xmodulo.com/access-nat-guest-from-host-virtualbox.html)

## 如何设置端口转发


![2019-10-31-002](https://gitee.com/gdhu/prvpic/raw/master/2019-10-31-002.jpg)

![2019-10-31-003](https://gitee.com/gdhu/prvpic/raw/master/2019-10-31-003.jpg)

![2019-10-31-001](https://gitee.com/gdhu/prvpic/raw/master/2019-10-31-001.jpg)