---
title: "Windows 10 Docker & GUI"
date: 2019-06-20T20:04:38+08:00
draft: false
tags: 
   - TAG
categories:
  - 技术
  - 归档
---

[TOC]

win10安装docker启动容器调用图形界面报错。

<!--more-->

# Windows 10 Docker & GUI

## 下载安装xming

[xming download](https://sourceforge.net/projects/xming/)

![2019-06-20-010](https://gitee.com/gdhu/prvpic/raw/master/2019-06-20-010.jpg)

修改xming安装目录中的X0.hosts 。

配置xming，新增本地ip，并保存。

```
localhost
192.168.31.224
```
启动XLaunch.ext

![2019-06-20-011](https://gitee.com/gdhu/prvpic/raw/master/2019-06-20-011.jpg)

按如下配置：

![2019-06-20-011](https://gitee.com/gdhu/prvpic/raw/master/2019-06-20-011.jpg)

![2019-06-20-012](https://gitee.com/gdhu/prvpic/raw/master/2019-06-20-012.jpg)

![2019-06-20-013](https://gitee.com/gdhu/prvpic/raw/master/2019-06-20-013.jpg)

![2019-06-20-014](https://gitee.com/gdhu/prvpic/raw/master/2019-06-20-014.jpg)

![2019-06-20-015](https://gitee.com/gdhu/prvpic/raw/master/2019-06-20-015.jpg)

保存配置到，%appdata%目录，例如我的C:\Users\x1c\AppData\Roaming

## 启动powershell

PowerShell设定本地ip，
set-variable -name DISPLAY -value 192.168.31.224:0.0

## 运行docker

```
docker run --rm -e DISPLAY=$DISPLAY ...
```

## 参考

[ref-1](https://dev.to/darksmile92/run-gui-app-in-linux-docker-container-on-windows-host-4kde)

[ref-2](https://blogs.msdn.microsoft.com/jamiedalton/2018/05/17/windows-10-docker-gui/)