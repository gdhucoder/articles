---
title: "win10如何在Docer容器中运行IntelliJ？"
date: 2019-06-20T20:17:20+08:00
draft: false
tags: 
   - DOCKER
categories:
  - 技术
  - 归档
---

[TOC]

本文讲win10如何在Docer容器中运行IntelliJ

<!--more-->

# win10 intelliJ docker

## 只需要几个步骤

- 安装docker

- 注册docker hub id

- 执行

```
docker pull guodonghu/ideaj:v1.1
```

- windows10系统下载xming，并安装

- 启动container

```
docker run ... 
```

## Dockerfile

```sh
FROM adoptopenjdk/openjdk8

LABEL maintainer "Viktor Adam <rycus86@gmail.com>"

RUN  \
  apt-get update && apt-get install --no-install-recommends -y \
  gcc git openssh-client less \
  libxtst-dev libxext-dev libxrender-dev libfreetype6-dev \
  libfontconfig1 libgtk2.0-0 libxslt1.1 libxxf86vm1 \
  && rm -rf /var/lib/apt/lists/* \
  && useradd -ms /bin/bash developer

ARG idea_source=https://download.jetbrains.com/idea/ideaIC-192.5118.30.tar.gz
ARG idea_local_dir=.IdeaIC2019.2

WORKDIR /opt/idea

RUN curl -fsSL $idea_source -o /opt/idea/installer.tgz \
  && tar --strip-components=1 -xzf installer.tgz \
  && rm installer.tgz

USER developer
ENV HOME /home/developer

RUN mkdir /home/developer/.Idea \
  && ln -sf /home/developer/.Idea /home/developer/$idea_local_dir

CMD [ "/opt/idea/bin/idea.sh" ]
```

## docker run

```sh
docker run --rm -e DISPLAY=$DISPLAY -v e:GDUT/dockerdev/X11-unix:/tmp/.X11-unix -v e:/GDUT/dockerdev/Idea:/home/developer/.Idea -v e:/GDUT/dockerdev/java:/home/developer/.java -v e:/GDUT/dockerdev/maven:/home/developer/.m2 -v e:/GDUT/dockerdev/gradle:/home/developer/.gradle -v e:/GDUT/dockerdev/IdeaIC2019:/home/developer/.IdeaIC2019.2 -v e:/GDUT/dockerdev/share:/home/developer/.local/share/JetBrains -v e:/GDUT/dockerdev/Project:/home/developer/Project guodonghu/ideaj:v1.1
```

其中`-v 后面的是本地与container共享的文件目录`

## DockerHub

```sh
# 镜像
docker pull guodonghu/ideaj:v1.1

# 运行
docker run ...
```


## scala & spark

成功打开intellij后，选择插件，安装scala插件。

![2019-06-20-004](https://gitee.com/gdhu/prvpic/raw/master/2019-06-20-004.jpg)

在v1.1中，我下载好了scala2.11 和spark 2.4.3在镜像中。直接配置依赖即可。

![2019-06-20-005](https://gitee.com/gdhu/prvpic/raw/master/2019-06-20-005.jpg)

![2019-06-20-006](https://gitee.com/gdhu/prvpic/raw/master/2019-06-20-006.jpg)

![2019-06-20-007](https://gitee.com/gdhu/prvpic/raw/master/2019-06-20-007.jpg)

![2019-06-20-008](https://gitee.com/gdhu/prvpic/raw/master/2019-06-20-008.jpg)

## 试验一下开发环境

在powershell中输入：

```sh
set-variable -name DISPLAY -value 192.168.31.224:0.0
```

接着输入：

```sh
docker run...
```

![2019-06-20-016](https://gitee.com/gdhu/prvpic/raw/master/2019-06-20-016.jpg)

图形界面已经启动成功了。

![2019-06-20-017](https://gitee.com/gdhu/prvpic/raw/master/2019-06-20-017.jpg)

在IDE中运行样例代码也成功了。

![2019-06-20-018](https://gitee.com/gdhu/prvpic/raw/master/2019-06-20-018.jpg)
