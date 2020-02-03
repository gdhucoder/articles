---
title: "写博客缩略图实时预览与上传"
date: 2019-03-12T10:50:18+08:00
draft: false
tags: 
   - TECH
categories:
  - 技术
  - 归档
---

[TOC]

最近一个问题一直困扰我：写博客时的截图生成图片链接的脚本不好用，没有实时性。

![我爱思考](https://gitee.com/gdhu/prvpic/raw/master/2019-03-12-001.jpg)


每次都需要我重新关闭打开一下。

思路是

a.每次新截图，保存到指定文件夹

b.上传到git

c.显示缩略图

<font color="Darkorange">**d.下次再截图，或者对图片有修改的时候。就需要我重新打开脚本文件。**</font>

这个问题一直没解决

<!--more-->

# 文件修改实时监测

解决这个问题的的方法是使用python3 的 <font color="green">**watchdog**</font>

每次对图片有修改或者新建图片时，重新执行 a b c 三步的那个脚本就可以了。

以上代码适用于检测文件修改，然后执行另一个操作。

在一个py程序中调用另一个cmd 

```code
process = subprocess.Popen(command, stdin=sys.stdin, stdout=sys.stdout, stderr=sys.stderr)
```


## 又一个坑

图片的大小影响网页的加载速度。

png的格式的文件要更大。使用jpg格式的文件，降低图片质量，整体不影响效果的前提下，使用jpg文件。

<font color="Darkorange">**picpick**</font>使用jpg保存截图，将截图的质量调到30%。

这样一张图只有几十kb。

![这个图片就很小](https://gitee.com/gdhu/prvpic/raw/master/2019-03-12-003.jpg)

## 效果

![2019-03-12-004](https://gitee.com/gdhu/prvpic/raw/master/2019-03-12-004.png)

```python
#!/usr/bin/env python3
# -*- coding: utf-8 -*
# @FileName: PngMonitor
# @Date: 2019-03-12 10:14
# @Author: HuGuodong gdong.hu[at]gmail.com

import os, sys, time, subprocess

from watchdog.observers import Observer
from watchdog.events import FileSystemEventHandler


def log(s):
    print('[Monitor] %s' % s)


class MyFileSystemEventHander(FileSystemEventHandler):
    def __init__(self, fn):
        super(MyFileSystemEventHander, self).__init__()
        self.restart = fn

    def on_any_event(self, event):
        if event.src_path.endswith('.png'):
            log('file changed: %s' % event.src_path)
            self.restart()


command = ['echo', 'ok']
process = None


def kill_process():
    global process
    if process:
        log('Kill process [%s]...' % process.pid)
        process.kill()
        process.wait()
        log('Process ended with code %s.' % process.returncode)
        process = None


def start_process():
    global process, command
    log('Start process %s...' % ''.join(command))
    process = subprocess.Popen(command, stdin=sys.stdin, stdout=sys.stdout, stderr=sys.stderr)


def restart_process():
    kill_process()
    start_process()


def start_watch(path, callback):
    observer = Observer()
    observer.schedule(MyFileSystemEventHander(restart_process), path, recursive=False)
    observer.start()
    log('Watching directory %s...' % path)
    start_process()
    try:
        while True:
            time.sleep(10)
    except KeyboardInterrupt:
        observer.stop()
    observer.join()


if __name__ == '__main__':
    print(sys.argv)
    command = 'D:\ProgramData\Anaconda2\envs\py36\python.exe E:/gitspace/x1c/PythonProjects/PP4E/Examples/PP4ELearn/GUI/PIL/MyPhoto.py'
    path = 'E:\gitpic'
    start_watch(path, None)

```


## 参考

[廖大神](https://www.liaoxuefeng.com/wiki/0014316089557264a6b348958f449949df42a6d3a2e542c000/001432339228196a8eb6fb8832b48b5aa0d740346536ead000)

[watchdog github](https://github.com/gorakhargosh/watchdog)