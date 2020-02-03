---
title: "如何使用gitee作为免费图床"
date: 2018-04-04T21:25:07+08:00
draft: false
tags: 
   - GIT
categories:
  - 技术
  - 归档
---

[TOC]

本篇文章是一个启发，介绍如何使用gitee作为免费图床。
没有使用github的原因是github国内访问有些慢。
另外，还有其他优秀的云存储，例如7niu，朋友们也可以试一下。

<!--more-->

## Use Gitee as public pictures storage.

### Step 1

- Create a project as your picture storage
- Submit your pictures

![png](https://gitee.com/gdhu/prvpic/raw/master/Image_002.png)


### Step 2

How to use it? 

Here is an example:

- change **blob** in this link into **raw**!

	https://gitee.com/gdhu/prvpic/*blob*/master/Image_001.png

- Into:

	https://gitee.com/gdhu/prvpic/*raw*/master/Image_001.png

**example**: this picture below is from gitee.

![png](https://gitee.com/gdhu/prvpic/raw/master/Image_001.png)

### Step 3, tips about Git usage:

```
git init 
git add origin xxx
git add --all
git commit -m "commit"
git push -f origin master
```

### Step 4, 使用Python自动生成图片链接

code as follows:

```
import os

# windows下命令之间使用&连接。
# 如cd C:\&dir

# 执行提交代码到git操作
cmd = 'E:&cd E:\gitpic&git add --all&git commit -m "update"&git push -f origin master'
# cmd = 'ipconfig'
result = os.popen(cmd)
print(result.read())

# 遍历目录，生成引用的图片链接
file_dir = 'E:\gitpic'
file_list = os.listdir(file_dir)

# 按照修改時間倒序排列

# st_mtime
#
#     Time of most recent content modification expressed in seconds.
#
# st_ctime
#
#     Platform dependent:
#
#         the time of most recent metadata change on Unix,
#         the time of creation on Windows, expressed in seconds

file_list.sort(key=lambda x: os.stat(file_dir + "/" + x).st_mtime,reverse=True)
images = []

# 最近的20张图片
for f in file_list[:20]:
    if f.endswith('.png'):
        img = "![" + f.split('.')[0] +"](https://gitee.com/gdhu/prvpic/raw/master/" + f +")\n";
        print(img)
        images.append(img)

# 写文件
with open('C:/Users/x1c/Desktop/图片地址.txt', 'w') as f:
    f.writelines(images)

```

### Step 5, 生成链接后的文档直接拿来复制使用
